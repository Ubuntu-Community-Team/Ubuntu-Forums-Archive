---
title: "[SOLVED] Request sent from external IP address is not getting forwarded to internal i"
date: 2008-02-20
forum: Networking &amp; Wireless
---

### Post by thoughtsga on 2008-02-20
Hello, 

I'm new to this concept of request being forwarded from an external to internal ip address. 

I've installed a web server (Tomcat) on a port 7070, and I'm trying to access a web application deployed on this Tomcat through an external IP addresss.


So I try [http://xxx.xxx.xxx.xxx:7070/page.jsp](http://xxx.xxx.xxx.xxx:7070/page.jsp) , I get a blank page. 

On the Ubuntu command line I type netstat -tupan , the output of netstat -tupan shows that a connection was received from the external ip address. I see a record like

Local Address
yyy.yyy.yyy.yyy:7070

Foreign Address
xxx.xxx.xxx.xxx:7070


But when I check the access log records for Tomcat, it shows that no request was received in the first place. 

I checked with Tomcat's mailing list and they said that there is no special configuration required in Tomcat to make it a standalone webserver. They said it might be something to do with a firewall. 

So I read this: [https://help.ubuntu.com/6.06/ubuntu/serverguide/C/firewall-configuration.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/firewall-configuration.html) 

I'm new to firewall configuration, but I just wanted to check with you about what should be configured so that the request from external ip address reaches to the internal ip address so that the request reaches Tomcat, and then the response from Tomcat is sent back to the external ip address.

I made sure that Tomcat receives the request when it is sent internally. That is if I locally try to access the web app like [http://localhost:7070](http://localhost:7070) or [http://127.0.0.1:7070](http://127.0.0.1:7070) or [http://yyy.yyy.yyy.yyy:9090](http://yyy.yyy.yyy.yyy:9090) (internal ip address) , Tomcat responds to the request and serves the web page. 

Any help with configuring the firewall is appreciated.

---

### Post by thoughtsga on 2008-02-20
Hello everyone, 

This is solved, I ran the iptables tool as per the instructions, I used a 32 bit mask instead of 16 and I change the interface device name to eth0 , and now i can access  the site externally woo hoo.

That article is great, thatnks to who ever wrote it.

---

