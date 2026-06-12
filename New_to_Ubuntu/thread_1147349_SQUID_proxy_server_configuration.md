---
title: "SQUID proxy server configuration"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by akkad on 2009-05-03
i need a help in setting the configuration of SQUID proxy server where :

- i have a machine that has Squid and apache servers both on same machine, apache listens to port 80 where Squid listens to port 8000.
- another machine on the same network has IIS server listens to port 80.

am looking to configure Squid just to translate the incoming internet requests and then passes them to the specified http server without any extra features (caching, ...) only passing requests.

Squid website has configuration examples which i tired to follow but with no luck :( , so i came up with the following config:

cache_peer 10.1.1.1 parent 80 0 no-query originserver name=tomcat
cache_peer_domain tomcat tomcat.no-ip.com
cache_peer 10.1.1.2 parent 80 0 no-query originserver name=iis
cache_peer_domain iis iis.no-ip.com

where 10.1.1.1 is the apache & Squid server ip address, and 10.1.1.2 is the IIS ip address, as you can see am using no-ip.com on Squid&Apache server to update my public ip, for no-ip dont panic i configured every thing about port forwarding .... etc where my server is totally accessible over the internet, now when i request the Squid server (like tomcat.no-ip.com) over the internet i receive a response from Squid telling that "the requested URL could not be retrieved" followed by "access denied", so did configure Squid in the right way?

---

### Post by akkad on 2009-05-03
help plz ??

---

### Post by Gone fishing on 2009-05-03
I cheat and configure squid using webmin, however, you need an allow ACL that allows your local area network to connect to the net by default squid wont allow anything to connect  as an open proxy is a bad thing.

---

### Post by Gone fishing on 2009-05-03
The relevant lines in my squid.conf  look like

```
acl allowlocal src 192.168.1.1-192.168.1.255

http_access allow allowlocal
```

---

### Post by akkad on 2009-05-03
Gone fishing, no look with those settings too :(

---

### Post by Gone fishing on 2009-05-03
I assume you've changed 192.168.1.1-192.168.1.255 to your ip range?

my proxy is a caching proxy but my squid.conf is emailed to you. I hope tht helps.(I've commented our squidguard) and you'll note some of my ACL are interesting:)

Webmin does make thing easier

---

### Post by akkad on 2009-05-03
thanks man, the email is received, let me try the configurations you have and I'll feed back.

---

### Post by akkad on 2009-05-04
solved, this the configurations that works for me, add them at the top of the squid.conf file :

http_port 8000 accel vhost
cache_peer 127.0.0.1 parent 80 0 no-query originserver name=srvtomcat
cache_peer_domain srvtomcat subA.no-ip.com
cache_peer 10.1.1.10 parent 80 0 no-query originserver name=srviis
cache_peer_domain srviis subB.no-ip.com
http_access allow all

where 127.0.0.1 is the ip of the local machine that has both squid and apache, 10.1.1.10 is the IIS machine, subA.no-ip.com & subB.no-ip.com are hosts on no-ip.

---

### Post by sanbd on 2009-10-17
squid is not working properly.i configure it but this massage is show 5


1255773198.037      5 172.17.8.168 TCP_MISS/504 1637 GET [http://dungcoivb.googlepages.com:8000/ND.txt](http://dungcoivb.googlepages.com:8000/ND.txt) - NONE/- text/html
1255773204.133    258 172.17.8.217 TCP_MISS/504 1698 GET [http://attachments.weiphone.com:8000/temp7/bd/Melodica-v1.1.1-RRPhantom.ipa](http://attachments.weiphone.com:8000/temp7/bd/Melodica-v1.1.1-RRPhantom.ipa) - NONE/- text/html
1255773204.267    134 172.17.8.217 TCP_MISS/504 1698 GET [http://attachments.weiphone.com:8000/temp7/9f/Melodica-v1.1.1-RRPhantom.ipa](http://attachments.weiphone.com:8000/temp7/9f/Melodica-v1.1.1-RRPhantom.ipa) - NONE/- text/04 

and my ip is 172.0.0.0/8

and i am using mikrotik server...........

any one help me plzzz

---

### Post by Big_Croc7 on 2009-10-17
[deleted]

---

### Post by sanbd on 2009-10-18
any one help me???

---

