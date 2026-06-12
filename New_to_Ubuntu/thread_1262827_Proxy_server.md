---
title: "Proxy server"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by mosquetero on 2009-09-10
Hi everyone!

I have 3 computers at home (one laptop and two "home" computers). One of these home computers connects to the internet through the other one using a proxy. Specifically, I use the software analogx proxy which unfortunately is only available for Windows. 
I want to install Ubuntu in the computer that provides the internet to the other one (the proxy server) and I wanted to know if it exists a proxy application in Ubuntu that allows other computers to connect to the internet through it. In other words, is it an analogx proxy application for Ubuntu???

Thanks :D

---

### Post by Mighty_Joe on 2009-09-10
The ability to share an internet connection is built-in to the Linux kernel as part of the iptables functionality.  [See here]("http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html") (note there's a [gui available]("http://www.fs-security.com/")).
Personally, I use a [router device]("http://en.wikipedia.org/wiki/Linksys_WRT54G_series").  Easier to configure and if someone 'sploits it, they haven't cracked any of your computers.

---

### Post by mosquetero on 2009-09-10
I found it! Its name is Squid, but thanks anyway

---

### Post by bodhi.zazen on 2009-09-10
If you like squid, take a look at bfilter. It is lighter weight and can perform adblocking as well.

[http://blog.bodhizazen.net/linux/adblock-with-bfilter/](http://blog.bodhizazen.net/linux/adblock-with-bfilter/)

Just be sure to firewall bfilter so it accepts connections only from your local computers.

---

### Post by mosquetero on 2009-09-12
Thank you bodyzazen, bfilter is a really good alternative:)

---

### Post by Gone fishing on 2009-09-12
I use squid (and run the Internet to about 60 PCs through it) I don't think it too difficult and very stable, although I recommend Webmin to help configure it.

---

### Post by bodhi.zazen on 2009-09-12
> **Gone fishing said:**
> I use squid (and run the Internet to about 60 PCs through it) I don't think it too difficult and very stable, although I recommend Webmin to help configure it.

Squid works well as a proxy,but the configuration file is huge and documentation is very poor and out of date. So if you need to make some customizations it is a pain.

---

### Post by Gone fishing on 2009-09-12
Which is why I'd Webmin to help configure it. It makes setting up ACLs proxy ports etc easy

[ATTACH]128325[/ATTACH]
[ATTACH]128326[/ATTACH]
[ATTACH]128327[/ATTACH]

Edit just added a couple more screen shots

---

### Post by Gone fishing on 2009-09-12
However, Squid is probably over the top for sharing the Internet to a couple of PCs

---

### Post by zman58 on 2009-09-12
I set up squid on my home server. It was very easy. I didn't have to make many changes at all. In the diff output below, the lines with "<" were added while the lines with ">" were removed. Here is diff output comparing my current squid.conf with the original that was installed on Ubuntu from the main repository (using Synaptic).

zadmin@gatekeeper:/etc/squid$ sudo diff squid.conf squid.conf.original_2008-11-10 
[sudo] password for zadmin: 
634c634
< http_access deny to_localhost
---
> #http_access deny to_localhost
644,646d643
< # -kwz- 2008-11-10 added to allow local subnet access to http
< acl zgroup_network src 192.168.1.0/24
< http_access allow zgroup_network
925,926c922
< http_port 3128 transparent
< always_direct allow all
---
> http_port 3128
1839,1840d1834
< # -kwz- 2008-11-10 provide 1000MB cache...
< cache_dir ufs /var/spool/squid 1000 16 256
3055d3048
< visible_hostname gatekeeper

So, as you can see, only a few lines needed to be changed. If you want to take a look at how I am using it you can refer to my website where I have documented and provide all configuration for my Ubuntu home server, gatekeeper.

Feel free to download the server configuration .tar file and extract the squid configuration file (/etc/squid/squid.conf) for reference or use on your system.
[http://home.roadrunner.com/~zahorec/gatekeeper.html](http://home.roadrunner.com/~zahorec/gatekeeper.html)
Here is the server configuration .tar file from that page:
[http://home.roadrunner.com/~zahorec/downloads/gatekeeper_Ubuntu_8.04_server_config_2009-03-06.tar](http://home.roadrunner.com/~zahorec/downloads/gatekeeper_Ubuntu_8.04_server_config_2009-03-06.tar)

You don't really need something as powerful as squid to share a few connections on a PC. You can use iptables to accomplish that. All you need is a script to set it up. I have been using Arno's firewall script.
[http://rocky.eld.leidenuniv.nl/](http://rocky.eld.leidenuniv.nl/)
...You can get that also from my server .tar file above along with the configuration files I am using with it. I have been running it for several years. The solution I have has been thoroughly tested and it is very effective. It provides a full stealthy firewall connection to the internet and allows you to use one system to share the connection with many others.

---

