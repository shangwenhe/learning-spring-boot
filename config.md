

### HelloController
```java
package com.shangwenhe.demo_java;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestMethod;
import org.springframework.web.bind.annotation.RestController;


@RestController
class HelloController {

    @Autowired
    private AuthorProperties authorProperties;

    @RequestMapping(value = "/hello", method = RequestMethod.GET)
    public String say(){
        return  "shangwenhe" + authorProperties.getAge();
    }
}
```



### AuthorProperties
```java
package com.shangwenhe.demo_java;

import org.springframework.boot.context.properties.ConfigurationProperties;
import org.springframework.stereotype.Component;

@Component
@ConfigurationProperties(prefix = "author")
public class AuthorProperties {

    private Integer age;

    public Integer getAge(){
        return age;
    }
    public void setAge(Integer age){
        this.age = age;
    }

}
```

```yaml
spring:
  profiles:
    active: prod
```


