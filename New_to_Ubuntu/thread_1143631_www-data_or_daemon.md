---
title: "www-data or daemon"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by new_kubunto on 2009-04-30
Hello, I installed apache2 server and on httpd.conf is set User daemon and Group daemon. But when I look at the log files seams that is www-data user is executong/reading or writing files related to webserver application (php). Why www-data user is doing that, who is www-data ? Is a system user ?

---

### Post by nandemonai on 2009-04-30
What version of ubuntu are you using?

httpd.conf shouldn't be in use. It should be /etc/apache2/envvars

```
# envvars - default environment variables for apache2ctl

# Since there is no sane way to get the parsed apache2 config in scripts, some
# settings are defined via environment variables and then used in apache2ctl,
# /etc/init.d/apache2, /etc/logrotate.d/apache2, etc.
export APACHE_RUN_USER=www-data
export APACHE_RUN_GROUP=www-data
export APACHE_PID_FILE=/var/run/apache2.pid
```

And yes, www-data is system user, created by apache.

(I'm going off 8.04, I never use non LTS for servers).

---

### Post by new_kubunto on 2009-04-30
www-data or daemon
Hello, I installed apache2 server and on the httpd.conf file the user configured is daemon. When I look on the log system files seams that execure/write/read webserver application is the www-data. who is www-data ? why is not daemon that request the file access for web application ?

---

