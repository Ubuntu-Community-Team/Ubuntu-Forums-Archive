---
title: "apache + tomcat mod_jk"
date: 2009-07-31
forum: New to Ubuntu
---

### Post by 007casper on 2009-07-31
I have been trying to set mod_jk without any luck.  

I am getting ProxyPreserveHost invalid on the terminal when I restart apache. I have listed the steps to install mod_jk. I have installed libapache2-mod-jk for mod_jk. After I got an error, I figured installing
libapache2-mod-proxy-html will help... it still hicks up. ](*,)

[B]
Invalid command 'ProxyPreserveHost', perhaps misspelled or defined by a module not included in the server configuration[/B]

I used this link as [mod_jk]("http://ubuntuforums.org/showthread.php?t=219985&highlight=mod_jk") as a partial reference.

I set up my tomcat apache connect /etc/apache2/apache2.conf 
-
```

JkWorkersFile /etc/apache2/workers.properties
JkLogFile /var/log/apache2/mod_jk.log
JkLogLevel debug
JkLogStampFormat "[%a %b %d %H:%M:%S %Y] "
JkRequestLogFormat "%w %V %T"
JkOptions +ForwardKeySize +ForwardURICompat -ForwardDirectories
JkShmFile /var/log/apache2/jk-runtime-status
JkShmSize 256
```

and also got the worker.properties under /etc/apache2/workers.properties
-
```

workers.tomcat_home=/usr/share/tomcat6
workers.java_home=/usr/lib/jvm/java-6-sun #/usr/lib/jvm/java-1.5.0-sun
ps=/
worker.list=worker1
worker.worker1.port=8009
worker.worker1.host=localhost
worker.worker1.type=ajp13
#worker.worker1.lbfactor=1
worker.worker1.socket_keepalive=1
worker.worker1.socket_timeout=60
```

then I edited <*virtual host> over at /etc/apache2/sites-enabled/000-default
-
```

ProxyPreserveHost On

	RewriteEngine On
	RewriteRule ^/ext/(.*) http://localhost:8080/ext/$1 [P,L]
	RewriteRule ^/app/(.*) http://localhost:8080/app/$1 [P,L]

JKMount /* worker1
```

then stopped apache, stopped tomcat, started tomcat, and when I start apache, it gives me an error in the terminal 

$ /etc/init.d/apache2 restart
 * Restarting web server apache2                                                Syntax error on line 41 of /etc/apache2/sites-enabled/000-default:
Invalid command 'ProxyPreserveHost', perhaps misspelled or defined by a module not included in the server configuration

and mod_jk log gives me
[Thu Jul 30 15:40:48 2009] [5037:3074705184] [warn] map_uri_to_worker::jk_uri_worker_map.c (608 ): Uri * is invalid. Uri must start with /
:roll:

if I block the ProxyPreserveHost On, I can restart apache. However, I get a different error from mod_jk log
[Thu Jul 30 17:28:13 2009] [error] [client 127.0.0.1] attempt to make remote request from mod_rewrite without proxy enabled
[B]
how can I fix ProxyPreserveHost error?[/B]:confused:  

Thank you so much.:P

---

### Post by 007casper on 2009-08-01
bump

---

### Post by 007casper on 2009-08-03
nobody knows what is going on ???

---

### Post by 007casper on 2009-08-06
bump

---

