---
title: "www-data or daemon"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by new_kubunto on 2009-04-30
Hello, I installed apache2 server and on the httpd.conf file the user configured is daemon. When I look on the log system files seams that execure/write/read webserver application is the www-data. who is www-data ? why is not daemon that request the file access for web application ?

---

### Post by kpkeerthi on 2009-04-30
Why so many dup posts?

---

### Post by spiderbatdad on 2009-04-30
On apache2, installed from the ubuntu repositories, you should find httpd.conf to be empty. Apache2.conf comes with default configuration settings and you can make changes in httpd.conf that will overrride the default settings.
www-data is the user apache2 runs as. This user has limited privileges. This is set in apache2.conf: ```
# These need to be set in /etc/apache2/envvars
User ${APACHE_RUN_USER}
Group ${APACHE_RUN_GROUP}

```
Looking in envars, you should see:
```
export APACHE_RUN_USER=www-data
export APACHE_RUN_GROUP=www-data
```

Hope this helps you.

---

