# 📚 DevOps - سوالات متداول مصاحبه

## 📖 Table of Contents

- [🔧 Jenkins](#-jenkins)
- [🦊 GitLab CI](#-gitlab-ci)
- [⚡ GitHub Action](#-github-action)
- [📊 Prometheus](#-prometheus)
- [📈 Grafana](#-grafana)
- [🧩 ELK Stack](#-elk-stack)
- [🪵 Loki](#-loki)
- [🔍 Splunk](#-splunk)
- [☁️ AWS](#-aws)
- [☁️ Azure](#-azure)
- [☁️ GCP](#-gcp)
- [☸️ Kubernetes](#-kubernetes)
- [🐳 Docker](#-docker)
- [🐙 Docker Compose](#-docker-compose)
- [⚙️ Ansible](#-ansible)
- [🏗️ Terraform](#-terraform)
- [🌐 Nginx / LB / Traefik](#-nginx--lb--reverse-proxy--traefik)
- [🔀 Istio](#-istio)
- [🧪 Testing](#-تست-functional--non-functional--selenium--jmeter--k6--sonarqube)
- [💾 Ceph / MinIO](#-ceph--minio)
- [🚀 DevOps / GitOps / MLOps](#-devops--gitops--devsecops--llmops--mlops)
- [🐚 Bash / Python / Linux / Git](#-bash--python--linux--git)
- [📋 Scrum / Agile](#-scrum--agile)
- [📨 RabbitMQ / Kafka](#-rabbitmq--kafka)
- [🏛️ معماری & پروتکل‌ها](#-معماری--پروتکلها)

---

## 🔧 Jenkins

**Jenkins چیه؟**  
یک سرور اتوماسیون متن‌باز برای **CI/CD** که به شما کمک می‌کنه Build، Test و Deploy رو خودکار کنید.  
*(سطح: جونیور)*

**تفاوت Pipeline و Freestyle؟**  
**Freestyle:** پروژه‌های ساده با مراحل محدود. **Pipeline:** به‌صورت کد (Jenkinsfile) با قابلیت مراحل شرطی، موازی و مدیریت نسخه.  
*(سطح: میدلول)*

**انواع Pipeline؟**  
- **Declarative:** ساده‌تر، ساختار مشخص، مناسب بیشتر موارد.  
- **Scripted:** انعطاف‌پذیرتر با سینتکس Groovy.  
*(سطح: میدلول)*

**مراحل اصلی یه Jenkinsfile؟**  
`pipeline { agent any stages { stage('Build'){} stage('Test'){} stage('Deploy'){} } }`  
*(سطح: میدلول)*

**تفاوت Master و Agent در Jenkins؟**  
**Master:** مدیریت و زمان‌بندی. **Agent:** اجرای واقعی Jobها (می‌تونه روی ماشین‌های مختلف باشه).  
*(سطح: میدلول)*

**چطور Jenkins رو با Kubernetes یکپارچه کنم؟**  
با پلاگین **Kubernetes**، می‌تونید Agentهای ephemeral (موقتی) داخل کلاستر ایجاد کنید که بعد از Job حذف بشن.  
*(سطح: سینیور)*

**چطور Secrets رو مدیریت کنم؟**  
از **Credentials** داخلی Jenkins یا **HashiCorp Vault** استفاده کنید و در Pipeline با `withCredentials` بهش دسترسی داشته باشید.  
*(سطح: میدلول)*

**تفاوت Multibranch Pipeline با Pipeline معمولی؟**  
Multibranch به‌ازای هر شاخه (Branch) در Git، به‌صورت خودکار یه Pipeline مجزا ایجاد می‌کنه و Jenkinsfile اون شاخه رو اجرا می‌کنه.  
*(سطح: سینیور)*

**چطور Build رو موازی اجرا کنم؟**  
با `parallel` در Declarative Pipeline: `parallel { stage('A'){...} stage('B'){...} }`  
*(سطح: سینیور)*

**چطور Jenkins رو با GitLab یا GitHub ادغام کنم؟**  
از Webhookها و پلاگین‌های مربوطه استفاده کنید تا به‌ازای هر Push یا PR، Pipeline به‌صورت خودکار اجرا بشه.  
*(سطح: میدلول)*

---

## 🦊 GitLab CI

**GitLab CI چیه؟**  
ابزار CI/CD یکپارچه در GitLab که با فایل `.gitlab-ci.yml` تنظیم میشه و Pipeline رو اجرا می‌کنه.  
*(سطح: جونیور)*

**مراحل اصلی در GitLab CI؟**  
`stages: [build, test, deploy]` و هر Job زیر یکی از این stages تعریف میشه.  
*(سطح: جونیور)*

**تفاوت Job و Stage؟**  
**Stage:** مرحله‌ی منطقی (مثل Build). **Job:** کاری که در اون مرحله انجام میشه (چند Job می‌تونن موازی اجرا بشن).  
*(سطح: میدلول)*

**چطور Cache و Artifact تعریف کنم؟**  
`cache:` برای وابستگی‌های بین Jobها (مثل `node_modules`). `artifacts:` برای خروجی که بین stages منتقل میشه.  
*(سطح: میدلول)*

**چطور از GitLab CI با Kubernetes استفاده کنم؟**  
با استفاده از **GitLab Agent for Kubernetes** (مدیریت کلاستر) یا `kubectl` در Jobها با تنظیم KUBECONFIG.  
*(سطح: سینیور)*

**تفاوت Rules و Only/Except؟**  
`only/except` قدیمی‌تر و ساده‌تر. `rules` جدیدتر و انعطاف‌پذیرتر با قابلیت شرط‌های پیچیده و متغیرها.  
*(سطح: سینیور)*

**چطور Pipeline رو برای محیط‌های مختلف (Dev/Prod) مدیریت کنم؟**  
از **Environment** و **Deployment** در GitLab استفاده کنید و با Rules شرطی (مثل `if: $CI_COMMIT_BRANCH == "main"`) کنترل کنید.  
*(سطح: میدلول)*

**GitLab CI vs Jenkins؟**  
GitLab CI یکپارچه با GitLab، ساده‌تر، بدون نیاز به سرور جدا. Jenkins انعطاف‌پذیرتر با پلاگین‌های بیشتر ولی نیاز به مدیریت سرور.  
*(سطح: سینیور)*

---

## ⚡ GitHub Action

**GitHub Action چیه؟**  
ابزار CI/CD یکپارچه در GitHub که با فایل `.github/workflows/*.yml` تعریف میشه.  
*(سطح: جونیور)*

**تفاوت Action و Workflow؟**  
**Workflow:** کل فرآیند اتوماسیون (یک فایل YAML). **Action:** یک کار خاص (مثل Checkout کد یا Deploy به S3) که داخل Workflow استفاده میشه.  
*(سطح: میدلول)*

**چطور Secrets رو مدیریت کنم؟**  
از **Secrets** در Settings مخزن استفاده کنید و با `${{ secrets.MY_SECRET }}` در Workflow بهش دسترسی داشته باشید.  
*(سطح: میدلول)*

**چطور Matrix Strategy کار می‌کنه؟**  
به شما اجازه میده یه Job رو با چندین ترکیب (مثل نسخه‌های مختلف Node.js و OS) به‌صورت موازی اجرا کنید: `strategy: matrix: node-version: [16, 18]`  
*(سطح: سینیور)*

**تفاوت push و pull_request در trigger؟**  
`push` با هر کامیت اجرا میشه. `pull_request` موقع ایجاد یا آپدیت PR اجرا میشه (مناسب تست قبل از Merge).  
*(سطح: میدلول)*

**چطور از GitHub Action برای Deploy به Kubernetes استفاده کنم؟**  
با اکشن‌های رسمی مثل `azure/k8s-deploy` یا `actions-hub/kubectl` و تنظیم KUBECONFIG یا استفاده از Service Account.  
*(سطح: سینیور)*

**GitHub Action vs GitLab CI؟**  
هر دو قدرتمند. GitHub Action اکوسیستم وسیع‌تری از اکشن‌های آماده داره و با GitHub یکپارچه‌ست. GitLab CI امکانات پیشرفته‌تری برای مدیریت محیط‌ها و Deployments داره.  
*(سطح: سینیور)*

---

## 📊 Prometheus

**Prometheus چیه؟**  
سیستم مانیتورینگ و هشدار متن‌باز که متریک‌ها رو به‌صورت Pull (Scrape) از اپلیکیشن‌ها جمع‌آوری می‌کنه.  
*(سطح: جونیور)*

**تفاوت Pull vs Push در مانیتورینگ؟**  
**Pull (Prometheus):** خود سرور متریک‌ها رو از اپلیکیشن می‌گیره (کشف سرویس خودکار). **Push:** اپلیکیشن متریک‌ها رو به سرور می‌فرسته (مثل Graphite).  
*(سطح: میدلول)*

**چطور یه متریک سفارشی در Prometheus تعریف کنم؟**  
با کتابخانه‌های کلاینت (مثل `prometheus_client` در Python) و تعریف Metric Typeهایی مثل Counter, Gauge, Histogram.  
*(سطح: میدلول)*

**تفاوت Counter و Gauge؟**  
**Counter:** فقط افزایشی (مثل تعداد درخواست‌ها). **Gauge:** می‌تونه افزایش یا کاهش پیدا کنه (مثل مصرف CPU).  
*(سطح: میدلول)*

**چطور Alertmanager کار می‌کنه؟**  
هشدارهای Prometheus رو دریافت می‌کنه، گروه‌بندی (Grouping)، خاموشی (Inhibition) و مسیریابی (Routing) به مقصدهایی مثل Slack، Email یا PagerDuty رو انجام میده.  
*(سطح: سینیور)*

**چطور Prometheus رو با Kubernetes یکپارچه کنم؟**  
با **Prometheus Operator** یا **kube-prometheus-stack** که شامل ServiceMonitor برای کشف خودکار سرویس‌ها و جمع‌آوری متریک‌های K8s هست.  
*(سطح: سینیور)*

---

## 📈 Grafana

**Grafana چیه؟**  
ابزار بصری‌سازی (Visualization) و داشبورد برای داده‌های مانیتورینگ که از منابعی مثل Prometheus, Loki, Elasticsearch داده می‌گیره.  
*(سطح: جونیور)*

**تفاوت Data Source و Panel؟**  
**Data Source:** منبع داده (مثل Prometheus). **Panel:** ویجت نمایش داده روی داشبورد (نمودار، جدول، و...).  
*(سطح: میدلول)*

**چطور یه Alert در Grafana تعریف کنم؟**  
در تنظیمات Panel، تب Alert رو فعال کنید و شرط (مثل `when avg() > 80`) و کانال ارسال (Slack, Email) رو تنظیم کنید.  
*(سطح: میدلول)*

**Grafana vs Kibana؟**  
Grafana قوی‌تر در متریک‌های عددی (Prometheus) و داشبوردهای پیشرفته. Kibana بخشی از ELK و قوی‌تر در لاگ‌ها و جستجوی متنی.  
*(سطح: سینیور)*

**چطور Grafana رو با Loki یکپارچه کنم؟**  
Loki رو به‌عنوان Data Source اضافه کنید و با **LogQL** (زبان جستجوی لاگ Loki) لاگ‌ها رو در Grafana مشاهده کنید.  
*(سطح: میدلول)*

---

## 🧩 ELK Stack

**ELK مخفف چیه؟**  
**Elasticsearch** (ذخیره و جستجو) + **Logstash** (پردازش و انتقال) + **Kibana** (نمایش و داشبورد).  
*(سطح: جونیور)*

**نقش Logstash در ELK؟**  
داده‌ها رو از منابع مختلف (فایل, TCP, Kafka) دریافت، تبدیل (Filter) و به Elasticsearch ارسال می‌کنه.  
*(سطح: میدلول)*

**تفاوت Index و Document در Elasticsearch؟**  
**Index:** مانند دیتابیس. **Document:** مانند رکورد (JSON) که در Index ذخیره میشه.  
*(سطح: میدلول)*

**چطور لاگ‌های Kubernetes رو به ELK بفرستم؟**  
با **Filebeat** به‌عنوان DaemonSet روی Nodeها که لاگ‌های کانتینرها رو جمع‌آوری و به Logstash یا مستقیم به Elasticsearch می‌فرسته.  
*(سطح: سینیور)*

**تفاوت ELK و EFK؟**  
در EFK به‌جای Logstash از **Fluentd** استفاده میشه که سبک‌تر است و منابع کمتری مصرف می‌کنه.  
*(سطح: میدلول)*

**چطور از Kibana برای تحلیل لاگ استفاده کنم؟**  
با استفاده از **Discover** برای جستجو، **Visualize** برای نمودار و **Dashboard** برای ترکیب اطلاعات.  
*(سطح: میدلول)*

---

## 🪵 Loki

**Loki چیه؟**  
سیستم جمع‌آوری لاگ از Grafana Labs، که به‌جای ایندکس کردن محتوای لاگ، فقط برچسب‌ها (Labels) رو ایندکس می‌کنه و بسیار سبک‌تر از Elasticsearch است.  
*(سطح: میدلول)*

**تفاوت Loki و Elasticsearch؟**  
**Loki:** فقط Labels رو ایندکس می‌کنه، ذخیره‌سازی ارزان‌تر و سریع‌تر ولی جستجوی متنی محدودتر. **Elasticsearch:** جستجوی متنی کامل ولی سنگین‌تر و پرهزینه‌تر.  
*(سطح: سینیور)*

**چطور لاگ‌ها رو به Loki بفرستم؟**  
با **Promtail** (مشابه Filebeat) یا **Grafana Agent** که لاگ‌ها رو Scrape می‌کنه و با برچسب به Loki ارسال می‌کنه.  
*(سطح: میدلول)*

**چطور در Loki جستجو کنم؟**  
با زبان **LogQL** مشابه PromQL: `{namespace="prod"} |= "error"` برای پیدا کردن خطا در namespace prod.  
*(سطح: میدلول)*

---

## 🔍 Splunk

**Splunk چیه؟**  
پلتفرم تجاری برای جمع‌آوری، ایندکس کردن و تحلیل داده‌های لاگ و متریک با قابلیت جستجوی قدرتمند و داشبوردهای پیشرفته.  
*(سطح: میدلول)*

**تفاوت Splunk و ELK؟**  
Splunk تجاری، پشتیبانی حرفه‌ای، UI بهتر و قابلیت‌های پیشرفته‌تر. ELK متن‌باز، رایگان، نیاز به تنظیمات بیشتر ولی انعطاف‌پذیرتر.  
*(سطح: سینیور)*

**چطور داده‌ها رو به Splunk بفرستم؟**  
با **Universal Forwarder** (برای فایل‌ها) یا **HTTP Event Collector (HEC)** (برای ارسال HTTP) یا **Splunk Connect for Kubernetes**.  
*(سطح: میدلول)*

**SPL (Search Processing Language) چیه؟**  
زبان جستجوی اختصاصی Splunk برای فیلتر، تبدیل و تحلیل داده‌ها: `index=main error | stats count by host`  
*(سطح: سینیور)*

---

## ☁️ AWS

**EC2 چیه؟**  
سرویس ماشین‌های مجازی در ابر (IaaS) که می‌تونید انواع Instance با سیستمعامل‌های مختلف ایجاد کنید.  
*(سطح: جونیور)*

**تفاوت S3 و EBS؟**  
**S3:** Object Storage (فایل‌های استاتیک، بکاپ). **EBS:** Block Storage (مثل هارد دیسک برای EC2، مناسب دیتابیس).  
*(سطح: میدلول)*

**IAM چیه و چطور کار می‌کنه؟**  
مدیریت دسترسی (Identity & Access Management). شامل User, Group, Role و Policy برای کنترل دقیق دسترسی به منابع.  
*(سطح: میدلول)*

**تفاوت Security Group و NACL؟**  
**Security Group:** فایروال سطح Instance (Stateful). **NACL:** فایروال سطح Subnet (Stateless).  
*(سطح: سینیور)*

**چطور Load Balancer در AWS کار می‌کنه؟**  
ترافیک رو بین چندین Target (EC2 یا IP) توزیع می‌کنه. انواع: ALB (لایه ۷)، NLB (لایه ۴)، CLB (قدیمی).  
*(سطح: میدلول)*

**Auto Scaling چیست؟**  
به‌صورت خودکار تعداد Instanceها رو بر اساس سیاست‌های مشخص (مثل CPU) افزایش یا کاهش میده تا کارایی و هزینه بهینه بشه.  
*(سطح: میدلول)*

**VPC چیست؟**  
شبکه مجازی اختصاصی در AWS که می‌تونید Subnetها، Route Tableها و Internet Gateway رو خودتون مدیریت کنید.  
*(سطح: میدلول)*

**تفاوت RDS و DynamoDB؟**  
**RDS:** دیتابیس رابطه‌ای (SQL) مثل PostgreSQL, MySQL. **DynamoDB:** دیتابیس NoSQL کلید-مقدار (Key-Value) با مقیاس‌پذیری بالا.  
*(سطح: سینیور)*

**چطور Secrets رو در AWS مدیریت کنم؟**  
با **AWS Secrets Manager** یا **Parameter Store** (در Systems Manager) که رمزها رو ذخیره و به‌صورت امن به اپلیکیشن‌ها تزریق می‌کنه.  
*(سطح: سینیور)*

**CloudFormation چیست؟**  
ابزار IaC (زیرساخت به‌عنوان کد) در AWS که با فایل‌های JSON/YAML زیرساخت رو تعریف و مدیریت می‌کنه.  
*(سطح: سینیور)*

---

## ☁️ Azure

**Azure VM چیست؟**  
معادل EC2 در AWS، ماشین‌های مجازی با سیستمعامل‌های مختلف در ابر مایکروسافت.  
*(سطح: جونیور)*

**تفاوت Azure Blob و Azure Disk؟**  
**Blob:** Object Storage (مشابه S3). **Disk:** Block Storage (مشابه EBS).  
*(سطح: میدلول)*

**Azure DevOps چیست؟**  
پلتفرم یکپارچه برای CI/CD (Pipelines)، مدیریت کد (Repos)، بورد (Boards) و تست (Test Plans) از مایکروسافت.  
*(سطح: میدلول)*

**تفاوت AKS و Service Fabric؟**  
**AKS:** Kubernetes مدیریت‌شده در Azure. **Service Fabric:** پلتفرم اختصاصی مایکروسافت برای میکروسرویس‌ها (قدیمی‌تر).  
*(سطح: سینیور)*

**Azure Functions چیست؟**  
سرویس Serverless برای اجرای کد به‌صورت رویدادمحور (Event-Driven) بدون مدیریت سرور (مشابه AWS Lambda).  
*(سطح: میدلول)*

**Azure Active Directory (AAD) چیست؟**  
سرویس مدیریت هویت و دسترسی (IAM) در Azure برای احراز هویت کاربران و برنامه‌ها.  
*(سطح: میدلول)*

---

## ☁️ GCP

**GCP Compute Engine چیست؟**  
معادل EC2 در AWS، سرویس ماشین‌های مجازی در گوگل.  
*(سطح: جونیور)*

**تفاوت GCS و Persistent Disk؟**  
**GCS (Google Cloud Storage):** Object Storage (مشابه S3). **Persistent Disk:** Block Storage (مشابه EBS).  
*(سطح: میدلول)*

**GKE چیست؟**  
Google Kubernetes Engine، سرویس مدیریت‌شده Kubernetes در GCP که یکی از بهترین‌های بازار محسوب میشه.  
*(سطح: میدلول)*

**Cloud Functions چیست؟**  
سرویس Serverless در GCP (مشابه AWS Lambda) برای اجرای کد به‌صورت رویدادمحور.  
*(سطح: میدلول)*

**BigQuery چیست؟**  
سرویس Data Warehouse (انبار داده) بدون سرور در GCP برای تحلیل داده‌های حجیم با SQL.  
*(سطح: سینیور)*

**IAM در GCP چگونه کار می‌کند؟**  
مشابه AWS IAM، با Member (User/Service Account)، Role (مجوزها) و Resource (منابع) برای کنترل دسترسی.  
*(سطح: میدلول)*

---

## ☸️ Kubernetes

**Kubernetes چیست؟**  
سیستم متن‌باز برای مدیریت (ارکستراسیون) کانتینرها در مقیاس بزرگ.  
*(سطح: جونیور)*

**تفاوت Pod و Container؟**  
**Pod:** کوچک‌ترین واحد در K8s، شامل یک یا چند Container که منابع (شبکه و استوریج) مشترک دارند.  
*(سطح: جونیور)*

**اجزای Control Plane؟**  
- **API Server:** ورودی تمام درخواست‌ها.  
- **Scheduler:** تخصیص Pod به Nodeها.  
- **Controller Manager:** مدیریت کنترلرها.  
- **etcd:** ذخیره‌سازی کلید-مقدار کلاستر.  
*(سطح: میدلول)*

**تفاوت Deployment و StatefulSet؟**  
**Deployment:** برای اپ‌های بی‌حالت (Stateless). **StatefulSet:** برای اپ‌های حالت‌دار با هویت ثابت (مثل دیتابیس).  
*(سطح: میدلول)*

**DaemonSet چیست؟**  
روی هر Node دقیقاً یک Pod اجرا می‌کنه (مثل جمع‌آوری لاگ یا مانیتورینگ).  
*(سطح: میدلول)*

**چطور یک سرویس رو در K8s Expose کنم؟**  
با **Service** از نوع ClusterIP (داخلی)، NodePort (خارجی روی پورت Node) یا LoadBalancer (ابر) و **Ingress** برای مسیریابی مبتنی بر Host/Path.  
*(سطح: میدلول)*

**PersistentVolume و PersistentVolumeClaim چیه؟**  
**PV:** منبع ذخیره‌سازی در کلاستر (مثل NFS, EBS). **PVC:** درخواست استفاده از PV توسط Pod.  
*(سطح: سینیور)*

**تفاوت Ingress و LoadBalancer؟**  
**LoadBalancer:** تخصیص IP عمومی به هر سرویس (هزینه بالا). **Ingress:** یه نقطه ورودی واحد با مسیریابی بر اساس Host/Path (هزینه کمتر، انعطاف بیشتر).  
*(سطح: سینیور)*

**HPA چیست؟**  
Horizontal Pod Autoscaler: به‌صورت خودکار تعداد Podها رو بر اساس متریک‌های (مثل CPU) افزایش/کاهش میده.  
*(سطح: سینیور)*

**چطور یک Pod رو عیب‌یابی کنم؟**  
با `kubectl describe pod`، `kubectl logs` و `kubectl exec -it` برای ورود به Pod.  
*(سطح: میدلول)*

**تفاوت ClusterIP و NodePort؟**  
**ClusterIP:** فقط داخل کلاستر قابل دسترس. **NodePort:** روی پورتی بین ۳۰۰۰۰-۳۲۷۶۷ روی هر Node قابل دسترس از خارج.  
*(سطح: میدلول)*

**چطور از K8s با CI/CD یکپارچه کنم؟**  
با ابزارهایی مثل **ArgoCD** (GitOps) یا در Pipeline با `kubectl apply` یا Helm. همچنین می‌تونید از **GitLab Agent** یا **GitHub Action** استفاده کنید.  
*(سطح: سینیور)*

---

## 🐳 Docker

**Docker چیست؟**  
پلتفرم برای ساخت، ارسال و اجرای اپلیکیشن‌ها در کانتینرها (محیط‌های سبک و قابل حمل).  
*(سطح: جونیور)*

**تفاوت Image و Container؟**  
**Image:** قالب فقط‌خواندنی (Read-Only) شامل کد و وابستگی‌ها. **Container:** نمونه‌ی در حال اجرا از Image.  
*(سطح: جونیور)*

**Dockerfile چیست؟**  
فایل متنی شامل دستورات ساخت Image (مثل `FROM, RUN, COPY, CMD`).  
*(سطح: جونیور)*

**چطور یه Image رو بهینه‌سازی کنم؟**  
- از **Multi-stage Build** استفاده کنید.  
- از Base Image سبک مثل `alpine`.  
- دستورات `RUN` رو ترکیب کنید تا لایه‌های کمتری ایجاد بشه.  
- فایل‌های غیرضروری رو با `.dockerignore` حذف کنید.  
*(سطح: میدلول)*

**تفاوت CMD و ENTRYPOINT؟**  
**CMD:** آرگومان‌های پیش‌فرض که قابل بازنویسی هستن. **ENTRYPOINT:** دستور اصلی که نمی‌شه بازنویسی کرد (فقط آرگومان‌ها قابل تغییرن).  
*(سطح: میدلول)*

**Docker Network چیست؟**  
شبکه‌های مجازی برای ارتباط کانتینرها: **bridge** (پیش‌فرض)، **host** (مستقیم روی شبکه میزبان)، **overlay** (ارتباط بین چندین Docker Daemon در Swarm).  
*(سطح: میدلول)*

**چطور حجم داده (Volume) رو مدیریت کنم؟**  
با `docker volume create` یا `-v` در `docker run`. Volumeها روی میزبان ذخیره می‌شن و حتی بعد از حذف کانتینر باقی می‌مونن.  
*(سطح: میدلول)*

**تفاوت Docker و VM؟**  
**Docker:** سبک‌تر، از هسته‌ی میزبان استفاده می‌کنه، سریع‌تر. **VM:** سنگین‌تر، شامل هسته‌ی مجزا، کندتر.  
*(سطح: جونیور)*

---

## 🐙 Docker Compose

**Docker Compose چیست؟**  
ابزاری برای تعریف و اجرای چندین کانتینر Docker با یک فایل `docker-compose.yml` روی یک ماشین.  
*(سطح: جونیور)*

**تفاوت Compose و Kubernetes؟**  
**Compose:** تک‌ماشین، مناسب توسعه محلی. **Kubernetes:** کلاستر چند ماشین، مناسب Production.  
*(سطح: میدلول)*

**چطور سرویس‌ها رو در Compose به هم متصل کنم؟**  
با **network** یا **links** (قدیمی). در Compose، سرویس‌ها با نام خودشون به‌عنوان Hostname قابل شناسایی هستن.  
*(سطح: میدلول)*

**چطور متغیرهای محیطی رو در Compose مدیریت کنم؟**  
با `environment` یا `env_file` در فایل Compose. همچنین می‌تونید از `${VAR}` برای ارجاع به متغیرهای Shell استفاده کنید.  
*(سطح: میدلول)*

**چطور Compose رو به Kubernetes تبدیل کنم؟**  
با ابزار **Kompose** که فایل Compose رو به Manifestهای K8s تبدیل می‌کنه (البته ممکنه نیاز به تنظیمات دستی داشته باشه).  
*(سطح: سینیور)*

---

## ⚙️ Ansible

**Ansible چیست؟**  
ابزار اتوماسیون IT برای مدیریت پیکربندی (Configuration Management)، Provisioning و Deployment که بدون Agent کار می‌کنه.  
*(سطح: جونیور)*

**تفاوت Playbook و Role؟**  
**Playbook:** فایل YAML شامل لیستی از Taskها. **Role:** مجموعه‌ای از Playbookها، متغیرها، فایل‌ها و Handlerها که قابل استفاده‌ی مجدد هست.  
*(سطح: میدلول)*

**Inventory در Ansible چیست؟**  
لیست سرورهایی که Ansible باهاشون کار می‌کنه (مشخصات IP، گروه‌ها و متغیرها).  
*(سطح: میدلول)*

**تفاوت Ansible و Terraform؟**  
**Terraform:** Provisioning (ساخت زیرساخت). **Ansible:** Configuration Management (تنظیمات نرم‌افزار). مکمل هم هستند.  
*(سطح: سینیور)*

**چطور Secrets رو در Ansible مدیریت کنم؟**  
با **Ansible Vault** که فایل‌ها یا متغیرها رو رمزگذاری می‌کنه و با Password در زمان اجرا Decrypt می‌کنه.  
*(سطح: میدلول)*

**Module چیست؟**  
واحدهای آماده در Ansible برای انجام کارهای خاص (مثل `apt` برای نصب بسته، `copy` برای کپی فایل، `service` برای مدیریت سرویس).  
*(سطح: جونیور)*

---

## 🏗️ Terraform

**Terraform چیست؟**  
ابزار IaC (زیرساخت به‌عنوان کد) برای ساخت، تغییر و مدیریت زیرساخت با فایل‌های کانفیگ (HCL).  
*(سطح: جونیور)*

**تفاوت Plan و Apply؟**  
`terraform plan` تغییرات رو پیش‌نمایش میده (بدون اجرا). `terraform apply` تغییرات رو اعمال می‌کنه.  
*(سطح: میدلول)*

**State در Terraform چیست؟**  
فایل (`terraform.tfstate`) که وضعیت فعلی زیرساخت رو ذخیره می‌کنه تا Terraform بتونه تغییرات رو مدیریت کنه. بهتره روی Remote Backend (مثل S3) ذخیره بشه.  
*(سطح: میدلول)*

**چطور از Terraform با AWS استفاده کنم؟**  
با **Provider** `aws` و تنظیم Credentials (Access Key) و تعریف منابع مثل `aws_instance`, `aws_s3_bucket`.  
*(سطح: میدلول)*

**تفاوت Data Source و Resource؟**  
**Resource:** منبعی که ایجاد/مدیریت می‌کنید (مثل EC2). **Data Source:** منبعی که فقط می‌خونید (مثل لیست AMIها).  
*(سطح: سینیور)*

**چطور State رو به اشتراک بگذارم؟**  
با **Remote Backend** مثل S3 + DynamoDB (برای قفل‌گذاری) یا Terraform Cloud.  
*(سطح: سینیور)*

**Module چیست؟**  
مجموعه‌ای از منابع Terraform که به‌صورت یک بسته قابل استفاده‌ی مجدد (Reusable) تعریف میشن.  
*(سطح: میدلول)*

---

## 🌐 Nginx / LB / Reverse Proxy / Traefik

**Nginx چیست؟**  
وب‌سرور و Reverse Proxy پرسرعت و سبک که برای Load Balancing، Cache و SSL Termination استفاده میشه.  
*(سطح: جونیور)*

**Reverse Proxy چیست؟**  
سرور واسطه که درخواست‌های کلاینت رو دریافت و به سرورهای پشتیبان (Backend) هدایت می‌کنه. مزایا: Load Balancing، افزایش امنیت، Cache.  
*(سطح: میدلول)*

**تفاوت Reverse Proxy و Forward Proxy؟**  
**Forward Proxy:** نماینده‌ی کلاینت (مثل VPN). **Reverse Proxy:** نماینده‌ی سرور (مثل Nginx برای Load Balancing).  
*(سطح: میدلول)*

**چطور Nginx رو برای Load Balancing تنظیم کنم؟**  
با `upstream` و تعریف Backendها و سپس `proxy_pass` در `location`. همچنین متدهای `round-robin`, `least_conn`, `ip_hash`.  
*(سطح: میدلول)*

**تفاوت Nginx و Apache؟**  
Nginx رویدادمحور (Event-Driven) و غیرهمزمان (Async) → مصرف منابع کمتر، مناسب ترافیک بالا. Apache پروسس/ترد محور → سنگین‌تر ولی پشتیبانی از ماژول‌های بیشتر.  
*(سطح: سینیور)*

**Traefik چیست؟**  
Ingress Controller و Reverse Proxy مدرن برای Kubernetes و Docker که به‌صورت خودکار سرویس‌ها رو کشف (Service Discovery) و Route می‌کنه.  
*(سطح: میدلول)*

**تفاوت Traefik و Nginx Ingress؟**  
Traefik کشف خودکار سرویس‌ها رو بهتر انجام میده و با Let's Encrypt یکپارچه‌ست. Nginx Ingress پایدارتر و پرکاربردتره، ولی تنظیمات دستی بیشتری نیاز داره.  
*(سطح: سینیور)*

**چطور Nginx رو برای SSL تنظیم کنم؟**  
با **Let's Encrypt** و Certbot یا تنظیم دستی گواهی در `ssl_certificate` و `ssl_certificate_key` و `listen 443 ssl`.  
*(سطح: میدلول)*

---

## 🔀 Istio

**Istio چیست؟**  
Service Mesh متن‌باز برای مدیریت ارتباطات، امنیت و مشاهده‌پذیری میکروسرویس‌ها در Kubernetes.  
*(سطح: سینیور)*

**اجزای اصلی Istio؟**  
- **Envoy Proxy:** Sidecar در کنار هر Pod.  
- **Pilot:** مدیریت ترافیک و قوانین.  
- **Mixer:** جمع‌آوری متریک و لاگ (در نسخه‌های جدید حذف شده).  
- **Citadel:** مدیریت امنیت و گواهی‌ها (mTLS).  
*(سطح: سینیور)*

**چطور از Istio برای Canary Deployment استفاده کنم؟**  
با **VirtualService** و **DestinationRule** ترافیک رو بین نسخه‌های مختلف (subset) تقسیم کنید: `weight: 90` برای v1 و `weight: 10` برای v2.  
*(سطح: سینیور)*

**تفاوت Istio و Linkerd؟**  
Istio قدرتمندتر با قابلیت‌های بیشتر (مثل مدیریت ترافیک پیشرفته)، ولی سنگین‌تر. Linkerd سبک‌تر و ساده‌تر با تمرکز بر امنیت و مشاهده‌پذیری.  
*(سطح: سینیور)*

---

## 🧪 تست (Functional / Non-Functional / Selenium / JMeter / K6 / SonarQube)

**تفاوت تست Functional و Non-Functional؟**  
**Functional:** بررسی «چه کاری» سیستم انجام میده (Unit, Integration, System). **Non-Functional:** بررسی «چقدر خوب» انجام میده (Performance, Security, Usability).  
*(سطح: جونیور)*

**Unit Test چیست؟**  
تست کوچک‌ترین واحد کد (معمولاً تابع یا متد) به‌صورت مجزا (ابزارها: JUnit, PyTest, NUnit).  
*(سطح: جونیور)*

**Integration Test چیست؟**  
تست تعامل بین چندین ماژول یا سرویس (مثل ارتباط API با دیتابیس).  
*(سطح: میدلول)*

**Selenium چیست؟**  
ابزار اتوماسیون تست مرورگر برای تست‌های End-to-End و Functional وب‌اپلیکیشن‌ها.  
*(سطح: میدلول)*

**تفاوت JMeter و K6؟**  
**JMeter:** قدیمی‌تر، UI محور، سنگین، مناسب تست‌های پیچیده. **K6:** مدرن، مبتنی بر کد (JavaScript)، سبک، مناسب CI/CD و تست‌های Performance خودکار.  
*(سطح: سینیور)*

**چطور تست Performance رو در CI/CD یکپارچه کنم؟**  
با ابزارهایی مثل K6 که به‌صورت CLI اجرا میشن، می‌تونید در Pipeline اجراشون کنید و در صورت شکست (مثلاً زمان پاسخ > ۲ ثانیه)، Pipeline رو Fail کنید.  
*(سطح: سینیور)*

**Smoke Testing چیست؟**  
تست سریع برای اطمینان از اینکه قابلیت‌های حیاتی سیستم بعد از هر دیپلوی کار می‌کنن.  
*(سطح: میدلول)*

**Regression Testing چیست؟**  
مطمئن میشه که تغییرات جدید، قابلیت‌های قبلی رو خراب نکردن (معمولاً با اجرای مجدد تست‌های قدیمی).  
*(سطح: میدلول)*

**SonarQube چیست؟**  
ابزار تحلیل کد استاتیک (Static Code Analysis) برای پیدا کردن باگ‌ها، آسیب‌پذیری‌های امنیتی و بوی بد کد (Code Smell).  
*(سطح: میدلول)*

**چطور SonarQube رو با CI/CD یکپارچه کنم؟**  
با افزودن مرحله‌ی اسکن در Pipeline (مثلاً با `sonar-scanner`) و تعریف Quality Gate که در صورت شکست، Pipeline رو متوقف کنه.  
*(سطح: سینیور)*

**تفاوت Load و Stress Testing؟**  
**Load:** تست با بار عادی (مثلاً ۱۰۰۰ کاربر همزمان). **Stress:** تست با بار فراتر از حد معمول برای پیدا کردن نقطه‌ی شکست.  
*(سطح: میدلول)*

**Endurance Testing چیست؟**  
تست عملکرد سیستم تحت بار طولانی‌مدت (مثلاً ۷۲ ساعت) برای پیدا کردن نشتی حافظه (Memory Leak) یا مشکلات تدریجی.  
*(سطح: سینیور)*

---

## 💾 Ceph · MinIO

**Ceph چیست؟**  
سیستم ذخیره‌سازی توزیع‌شده (Distributed Storage) که شامل Object Storage (RADOSGW)، Block Storage (RBD) و File System (CephFS) هست.  
*(سطح: سینیور)*

**MinIO چیست؟**  
سرور Object Storage متن‌باز و سازگار با S3 API که سبک و مناسب برای محیط‌های Kubernetes و ابرهای خصوصی هست.  
*(سطح: میدلول)*

**تفاوت Ceph و MinIO؟**  
**Ceph:** کامل‌تر (پشتیبانی از Block و File System)، سنگین‌تر، مناسب محیط‌های بزرگ. **MinIO:** فقط Object Storage، سبک، ساده‌تر، مناسب کانتینرها.  
*(سطح: سینیور)*

**چطور از MinIO در Kubernetes استفاده کنم؟**  
با **MinIO Operator** یا Helm Chart، می‌تونید MinIO رو روی K8s نصب کنید و از PVC برای ذخیره‌سازی داده‌ها استفاده کنید.  
*(سطح: میدلول)*

---

## 🚀 DevOps · GitOps · DevSecOps · LLMOps · MLOps

**DevOps چیست؟**  
فرهنگ و روش‌کاری برای ادغام Dev و Ops به‌منظور افزایش سرعت تحویل، کیفیت و کاهش اصطکاک.  
*(سطح: جونیور)*

**GitOps چیست؟**  
روش‌کاری که Git رو به‌عنوان **منبع حقیقت (Single Source of Truth)** برای زیرساخت و اپلیکیشن در نظر می‌گیره و تغییرات با Pull Request و Apply خودکار (مثل ArgoCD) انجام میشن.  
*(سطح: میدلول)*

**تفاوت DevOps و GitOps؟**  
DevOps فلسفه‌ست، GitOps یه پیاده‌سازی خاص از DevOps که بر **Git** به‌عنوان مرکز کنترل تأکید داره و معمولاً با Kubernetes و ArgoCD/Flux پیاده میشه.  
*(سطح: سینیور)*

**DevSecOps چیست؟**  
DevOps + Security از ابتدای چرخه (Shift-Left) با اسکن امنیتی در CI/CD و استفاده از ابزارهایی مثل Trivy, Snyk, OPA.  
*(سطح: میدلول)*

**MLOps چیست؟**  
ترکیب DevOps با Machine Learning برای مدیریت چرخه‌ی حیات مدل‌ها (آموزش، نسخه‌بندی، Deploy و مانیتورینگ). ابزارها: Kubeflow, MLflow.  
*(سطح: سینیور)*

**LLMOps چیست؟**  
نسخه‌ی تخصصی MLOps برای مدل‌های بزرگ زبانی (Large Language Models) که شامل Fine-tuning, Prompt Engineering و مدیریت هزینه‌ها و داده‌های حجیم هست.  
*(سطح: سینیور)*

**تفاوت MLOps و DevOps؟**  
MLOps علاوه بر CI/CD، شامل **مدل‌های داده**، نسخه‌بندی داده‌ها (Data Versioning)، مانیتورینگ دrift مدل (Model Drift) و چالش‌های خاص ML مثل عدم قطعیت (Stochastic) هست.  
*(سطح: سینیور)*

**ArgoCD چیست؟**  
ابزار GitOps برای Kubernetes که به‌صورت خودکار تغییرات موجود در Git رو به کلاستر Apply می‌کنه و وضعیت (Sync) رو مانیتور می‌کنه.  
*(سطح: میدلول)*

**تفاوت ArgoCD و FluxCD؟**  
ArgoCD امکانات UI و مدیریت پیشرفته‌تر داره. FluxCD سبک‌تر و ساده‌تر، با رویکرد سورس‌محور (Source-controller). هر دو GitOps هستند.  
*(سطح: سینیور)*

**چطور DevSecOps رو در CI/CD پیاده کنم؟**  
با اضافه کردن مراحل اسکن امنیتی (SAST با SonarQube، اسکن وابستگی‌ها با Snyk، اسکن ایمیج با Trivy، اسکن زیرساخت با Checkov) و Quality Gate برای جلوگیری از انتشار کد ناامن.  
*(سطح: سینیور)*

---

## 🐚 Bash · Python · Linux · Git

**تفاوت Bash و Shell؟**  
**Shell:** رابط خط فرمان (مثل sh, zsh). **Bash:** نوعی از Shell (Bourne Again SHell) که محبوب‌ترین در لینوکس است.  
*(سطح: جونیور)*

**چطور یک فایل لاگ رو به‌صورت زنده (Real-time) ببینم؟**  
با `tail -f /path/to/log` (دنبال کردن زنده).  
*(سطح: جونیور)*

**چطور تمام فرآیندهای در حال اجرا رو ببینم؟**  
`ps aux` یا `top` یا `htop`.  
*(سطح: جونیور)*

**چطور یک دایرکتوری رو به‌صورت بازگشتی (Recursive) حذف کنم؟**  
`rm -rf /path/to/dir` (بسیار با احتیاط!).  
*(سطح: جونیور)*

**Python در DevOps چه کاربردی داره؟**  
نوشتن اسکریپت‌های اتوماسیون، مدیریت APIهای ابری، ساخت ابزارهای سفارشی، تحلیل داده و لاگ، و استفاده با ابزارهایی مثل Ansible (که با Python نوشته شده).  
*(سطح: میدلول)*

**Git مخفف چیه و چطور کار می‌کنه؟**  
سیستم کنترل نسخه (VCS) توزیع‌شده که تغییرات کد رو مدیریت می‌کنه و امکان همزمانی تیم‌ها رو فراهم می‌کنه.  
*(سطح: جونیور)*

**تفاوت `git pull` و `git fetch`؟**  
`git fetch` فقط تغییرات رو از remote دریافت می‌کنه (بدون Merge). `git pull` = `git fetch` + `git merge`.  
*(سطح: میدلول)*

**چطور یک Conflict در Git رو حل کنم؟**  
فایل‌های Conflict رو باز کنید، قسمت‌های مشخص‌شده با `<<<<<<<` و `>>>>>>>` رو ویرایش کنید، سپس `git add` و `git commit` کنید.  
*(سطح: میدلول)*

**تفاوت `git reset` و `git revert`؟**  
`git revert` یک کامیت جدید برای خنثی‌سازی ایجاد می‌کنه (ایمن برای شاخه‌های عمومی). `git reset` تاریخچه رو بازنویسی می‌کنه (فقط برای شاخه‌های شخصی).  
*(سطح: سینیور)*

**چطور یک Branch جدید ایجاد کنم و بهش سوئیچ کنم؟**  
`git checkout -b new-branch` یا `git branch new-branch` و سپس `git checkout new-branch`.  
*(سطح: جونیور)*

---

## 📋 Scrum · Agile

**Agile چیست؟**  
روش‌شناسی توسعه نرم‌افزار با رویکرد چابک، مبتنی بر تکرارهای کوتاه (Sprint) و بازخورد مداوم.  
*(سطح: جونیور)*

**Scrum چیست؟**  
چارچوبی از Agile شامل نقش‌های (Product Owner, Scrum Master, Team)، مراسم‌ها (Sprint Planning, Daily Standup, Review, Retrospective) و مصنوعات (Product Backlog, Sprint Backlog).  
*(سطح: میدلول)*

**تفاوت Scrum و Kanban؟**  
**Scrum:** مبتنی بر Sprintهای زمان‌بندی‌شده (Fixed Length). **Kanban:** مبتنی بر جریان مداوم (Continuous Flow) با محدودیت Work In Progress (WIP).  
*(سطح: سینیور)*

**DevOps و Agile چه ارتباطی دارند؟**  
Agile روی **توسعه** (Dev) تمرکز داره، DevOps این چابکی رو به **عملیات** (Ops) و **تحویل** (Delivery) هم گسترش میده تا کل چرخه‌ی حیات نرم‌افزار چابک بشه.  
*(سطح: سینیور)*

---

## 📨 RabbitMQ · Kafka

**RabbitMQ چیست؟**  
Message Broker (واسط پیام‌رسانی) مبتنی بر پروتکل AMQP که برای ارتباط ناهمگام (Asynchronous) بین سرویس‌ها استفاده میشه.  
*(سطح: میدلول)*

**Kafka چیست؟**  
پلتفرم استریمینگ (Streaming) توزیع‌شده برای پردازش داده‌های بلادرنگ (Real-time) با قابلیت ذخیره‌سازی طولانی‌مدت (Log-based).  
*(سطح: میدلول)*

**تفاوت RabbitMQ و Kafka؟**  
**RabbitMQ:** مبتنی بر Queue، پیام‌ها بعد از مصرف حذف میشن، مناسب کارهای سبک و درخواست‌های فوری. **Kafka:** مبتنی بر Topic و Log، پیام‌ها برای مدت طولانی نگهداری میشن، مناسب پردازش داده‌های حجیم و Event Sourcing.  
*(سطح: سینیور)*

**چطور Kafka رو در Kubernetes اجرا کنم؟**  
با **Strimzi** (Operator) یا **Confluent for Kubernetes** که مدیریت Kafka روی K8s رو ساده می‌کنن.  
*(سطح: سینیور)*

**چطور از RabbitMQ در میکروسرویس‌ها استفاده کنم؟**  
با تعریف **Producer** (فرستنده) و **Consumer** (گیرنده) و استفاده از **Exchange** و **Queue** برای مسیریابی پیام‌ها.  
*(سطح: سینیور)*

**تفاوت Topic و Queue در messaging؟**  
**Queue:** پیام به یک Consumer تحویل داده میشه (Point-to-Point). **Topic:** پیام به چندین Consumer تحویل داده میشه (Publish-Subscribe).  
*(سطح: سینیور)*

---

## 🏛️ معماری · پروتکل‌ها

**تفاوت Monolithic و Microservices؟**  
**Monolithic:** همه‌ی اجزا در یک اپلیکیشن واحد (ساده، دیپلوی آسان، مقیاس‌پذیری سخت). **Microservices:** هر سرویس به‌صورت مستقل (مقیاس‌پذیری بالا، پیچیدگی شبکه).  
*(سطح: میدلول)*

**RESTful چیست؟**  
معماری API مبتنی بر HTTP و متدهای (GET, POST, PUT, DELETE) با داده‌های JSON/XML و Stateless.  
*(سطح: جونیور)*

**GraphQL چیست؟**  
زبان پرسش (Query Language) برای APIها که به کلاینت اجازه میده دقیقاً داده‌های موردنیاز رو درخواست کنه (بدون Over-fetching).  
*(سطح: میدلول)*

**تفاوت REST و GraphQL؟**  
**REST:** چندین Endpoint با داده‌های ثابت. **GraphQL:** یک Endpoint با Queryهای سفارشی (انعطاف بیشتر، کاهش تعداد درخواست‌ها).  
*(سطح: سینیور)*

**gRPC چیست؟**  
فریم‌ورک RPC پرسرعت از گوگل که از Protocol Buffer (باینری) و HTTP/2 استفاده می‌کنه. مناسب ارتباط داخلی میکروسرویس‌ها.  
*(سطح: میدلول)*

**تفاوت HTTP/1.1 و HTTP/2؟**  
**HTTP/2:** مولتی‌پلکسینگ (چندین درخواست همزمان روی یک کانال)، فشرده‌سازی هدر، Server Push، سرعت بالاتر.  
*(سطح: سینیور)*

**WebSocket چیست؟**  
پروتکل ارتباط دوطرفه (Full-Duplex) روی یک کانال TCP که برای اپلیکیشن‌های بلادرنگ (مثل چت، بازی) استفاده میشه.  
*(سطح: میدلول)*

**تفاوت WebSocket و HTTP؟**  
HTTP درخواست-پاسخ (Request-Response) و Stateless. WebSocket ارتباط دائمی (Persistent) و دوطرفه با تاخیر کم (Low Latency).  
*(سطح: سینیور)*

**Webhook چیست؟**  
مکانیزمی که یک اپلیکیشن به‌صورت خودکار به اپلیکیشن دیگه در پاسخ به یه رویداد (Event) درخواست HTTP می‌فرسته (مثل تریگر Pipeline با Push به Git).  
*(سطح: میدلول)*

**تفاوت Webhook و API؟**  
API یک رابط (Interface) برای درخواست‌های کلاینت به سرور هست. Webhook یک Callback HTTP هست که سرور به‌صورت خودکار به کلاینت اطلاع میده (معکوس API).  
*(سطح: سینیور)*
