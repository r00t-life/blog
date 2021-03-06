## 分析


当我们在登陆界面输入 `\ ( ) *`这些字符登录时候，如果出现错误，那么就有可能是 `LDAP` 注入
对于 `LDAP` 注入，可以用 `*` 来进行查询

在这道题中，当用户名和密码均为 `*` 的时候，明显是可以成功登录的。

假设系统的查询语法如下：

```
(&(username=*)(password=*))
```

很明显这里会查询所有的字段

这时候我们可以配合通配符 `*` 来做一些暴力破解

当用户名为`a*`，密码为 `*` 的时候，如果登录成功，那么说明用户名的第一个字符为 `a`，以此类推，就能够暴力跑出用户名和密码

# 参考链接
[https://xz.aliyun.com/t/5689](https://xz.aliyun.com/t/5689)

[https://wooyun.js.org/drops/LDAP%E6%B3%A8%E5%85%A5%E4%B8%8E%E9%98%B2%E5%BE%A1%E5%89%96%E6%9E%90.html](https://wooyun.js.org/drops/LDAP%E6%B3%A8%E5%85%A5%E4%B8%8E%E9%98%B2%E5%BE%A1%E5%89%96%E6%9E%90.html)