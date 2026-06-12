---
title: "apache2 ip address"
date: 2007-08-06
forum: Networking &amp; Wireless
---

### Post by gishaust on 2007-08-06
Hi everyone 


I have an internal lan that has apache2 webserver. My problem is that when it crashes it says that the it cannot resolve host name ignore! I have change it in the apache2.conf three times and It keeps doing the 
same thing. I have a fake name with [www.qwer.com](www.qwer.com) on the lan if I type that into the browser it does not work. but I can ping the server it through the browser. but I cannot ping it with port 80. 

Now for the strange things, I looked at the error logs and it says the following 

error client 192.168.1.2 file does not exist .( The machine in the trial period had a static ip with that but it has been a dynamic box for three weeks.  I change the inet (I think) so that it was only dynamic and delete the static info)

The second error is 
"caught sigterm shutting down" (which I can't find a lot of information on)

The access log says that 
192.168.1.2 (which is another machine now) http/1/"200" 734"_""moz"
which I believe to be another machines ip 

All I am trying to do is get it to serve up in the lan  by using the browser with [www.qwer.com](www.qwer.com)

any help would be great thanks

gishaust

---

### Post by misconfiguration on 2007-08-06
Well first things first.. If you're troubleshooting apache you need not see the access.log

```
/var/log/httpd/error_log
``` 

Second of all, if you're wanting to redirect local traffic of [www.qwer.com](www.qwer.com) for all of your LAN machines to access the LAN box that's hosting this web-service I would make sure you've edited /etc/hosts properly

cat /etc/hosts
# Do not remove the following line, or various programs
# that require network functionality will fail.
127.0.0.1         localhost.localdomain  localhost
<ip_of_box_that_hosts_apache>          qwer.com

***Do this on the server AND your local machine***

Now when you query [www.qwer.com](www.qwer.com) you'll automagically be re-directed to the local box. 

You can always type http://<ip_of_box> in your browser to see if apache is running correctly.

---

### Post by gishaust on 2007-08-06
misconfiguration


Thankyou for your help it was a host issue it works great.

gishaust

---

### Post by misconfiguration on 2007-08-06
Anytime, friend.

I'm glad to help!

---

