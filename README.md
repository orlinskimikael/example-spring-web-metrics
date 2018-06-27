# Przykład Spring Web Metrics

Przykład połączenia Spring Boot z Spring Micrometer i Prometheus.

## Pierwsze kroki

Pobranie aplikacji z github-a:

```
git clone https://github.com/orlinskimikael/example-spring-web-metrics.git
```

### Wymagania wstępne

Do pobrania i wygenerowania biblioteki wymagane są:

* GIT - https://git-scm.com/
* JAVA 8 (JDK i JRE) - http://www.oracle.com/technetwork/pt/java/javase/downloads/jdk8-downloads-2133151.html?printOnly=1
* MAVEN - https://maven.apache.org/
* Prometheus - https://prometheus.io

##### Konfiguracja środowiska

Należy również pamiętać o ustawieniu odpowiednich zmiennych środowiskowych *(przykładowe ścieżki)*:

```
JAVA_HOME = C:\Program Files\Java\jdk-10.0.1
JDK_HOME = %JAVA_HOME%
JRE_HOME = C:\Program Files\Java\jre-10.0.1
M2_HOME = C:\Program Files\Apache\apache-maven-3.5.3
MAVEN_HOME = C:\Program Files\Apache\apache-maven-3.5.3
PATH = $PATH;C:\Program Files\Java\jdk-10.0.1\bin;C:\Program Files\Java\jre-10.0.1\bin;C:\Program Files\Git\bin;
```

##### Konfiguracja Prometheus

Modyfikacja pliku prometheus.yml

```
scrape_configs:
  - job_name: 'example-spring-web-metrics'
    scrape_interval: 5s
    metrics_path: '/actuator/prometheus'
    static_configs:
    - targets: ['localhost:8080']
```

Uruchomienie:

```
prometheus.exe
```

### Budowanie i uruchomienie

Budowanie biblioteki należy wykonać za pomocą narzędzia MAVEN za pomocą polecenia *(polecenie wykonujemy z poziomu folderu w którym umieszczony jest plik pom.xml projektu)*:

```
mvn clean package
```

Po wykonaniu polecenia biblioteka zostanie umieszczona w lokalnym repozytorium maven-a oraz w folderze **target** projektu.

Uruchomienie:

```
java -jar target/example-spring-web-metrics-1.0.0.jar
```

Po uruchomieniu możemy śledzić metryki (np.: system\_cpu\_usage, jvm\_gc\_memory\_allocated\_bytes\_total) za pomocą linków:

http://localhost:8080/actuator/prometheus

oraz

http://localhost:9090

## Inne

https://igorski.co/java/spring-boot/spring-boot-metrics-prometheus/

## Autor

* **Michał Orliński**
* email: orlinski.michal.it@gmail.com