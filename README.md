# spring-cloud-eureka
### pox配置
```xml
<dependencies>
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter</artifactId>
</dependency>

<!--引入eureka-->
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-netflix-eureka-server</artifactId>
    <version>2.2.1.RELEASE</version>
</dependency>
</dependencies>


<!--eureka需要引入org.springframework.cloud-->
<dependencyManagement>
        <dependencies>
            <dependency>
                <groupId>org.springframework.cloud</groupId>
                <artifactId>spring-cloud-dependencies</artifactId>
                <version>Hoxton.SR1</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>
        </dependencies>
    </dependencyManagement>
```

### 配置说明
```properties
server.port=8888
eureka.instance.hostname=peer1
spring.application.name=spring-cloud-eureka
eureka.client.register-with-eureka=false #表示是否将自己注册到Eureka Server，默认为true
eureka.client.fetch-registry=false #表示是否从Eureka Server获取注册信息，默认为true。
eureka.client.serviceUrl.defaultZone=http://localhost:${server.port}/eureka/ #设置与Eureka Server交互的地址，查询服务和注册服务都需要依赖这个地址。默认是http://localhost:8761/eureka ；多个地址可使用 , 分隔
```

### 增加注解 @EnableEurekaServer