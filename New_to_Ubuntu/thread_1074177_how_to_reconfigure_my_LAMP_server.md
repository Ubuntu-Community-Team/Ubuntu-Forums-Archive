---
title: "how to reconfigure my LAMP server?"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by mash.ky on 2009-02-18
i am using Ubuntu 8.10 (intrepid) and configuered it into LAMP server. previously i was using php6 . later i uninstalled php6 and installed php5 but when i run [http://localhost:8080](http://localhost:8080) it gives

*****************************************************************************

It works !

If you're seeing this page via a web browser, it means you've setup Tomcat successfully. Congratulations!

This is the default Tomcat home page. It can be found on the local filesystem at: /var/lib/tomcat6/webapps/ROOT/index.html


*****************************************************************************
i need to run this on php5. pls help me! :(

---

### Post by yoyoned on 2009-02-19
try localhost without the :8080

---

### Post by cb951303 on 2009-02-19
There is a solution that works always when you're in trouble with LAMP:
**Purge** remove every lamp related package then reinstall it with this
```

sudo tasksel install lamp-server

```

---

