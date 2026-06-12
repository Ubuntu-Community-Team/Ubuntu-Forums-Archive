---
title: "Obtaining external IP from behind a router"
date: 2007-07-26
forum: Networking &amp; Wireless
---

### Post by richard4339 on 2007-07-26
Ok, so, I'll note that while I've delved into Linux Administration in the past, this is my first real foray into this topic where I haven't managed to make the box fail to respond within a few minutes, so I feel like I'm doing good so far (I've got Apache/PHP through LAMP running, Samba, SSH, FTP, etc).

Here's my problem/issue, and I haven't been able to find much on this. I've got a Linksys WRT54G router which my server is behind. I've told the Ubuntu server via its hosts file to take the static IP 192.168.1.12, and this works great thus far. I've turned on port forwarding for the appropriate ports I need accessible externally (so far, ports 21 and 22 for FTP and SSH, and port 80 for Apache). The thing is, I'm on a dynamic IP. I know I could use a dynamic IP service to update the IP, but I'm using a third-party DNS service overall to control other servers on the domain I use. So, I've written a PHP script that interfaces with the DNS service to update, but my $_SERVER['SERVER_ADDR'] variable is giving the internal IP address of 192.168.1.12. The thing is, I'm not sure if this is because I have PHP configured incorrectly somewhere, or because I have the networking files, specifically /etc/hosts configured incorrectly.

How can I get the server, overall, to see the external IP address automatically, if that is possible at all? If I have to manually update the /etc/hosts file every time the IP changes, it defeats the purpose of trying to use these type scripts and service, and obviously if they have clients for Linux, there has to be a way to do this.

---

### Post by kidders on 2007-07-27
Hi there,

When it comes to setting your IP address, /etc/hosts is irrelevant ... it's just used to short-circuit DNS queries. If you add a line to /etc/hosts specifying 1.2.3.4 as your IP address, that won't change the fact that your address is 192.168.1.12.

Apache doesn't normally care what its IP address is ... $_SERVER['SERVER_ADDR'] will simply return whatever the end user tells it to contain. For instance, by accessing your web server on a network interface with the IP 192.168.1.12, you are effectively instructing it to report that as it's address.

I'm not sure how helpful that is. Unfortunately, your question is a little confusing. It's not clear what you mean when you say you want your web server to "see" it's external IP address. I'm also struggling to think of a reason why you would even *want* your server to know what it's addresses are, so it's difficult to put together a good solution for you.

---

### Post by dmizer on 2007-07-30
you should be able to configure the wrt54g router to update your dyndns account automatically.

under the "setup" tab, select "ddns" and fill in the settings.

if that doesn't work, install ddclient on your server and configure it to update your dyndns account every 10 minutes or so by adding this line to the default conf file:
```
daemon=600
```

---

### Post by kevdog on 2007-07-30
If you want to see your external IP address you can take the following and type it at the command line, this could easily be turned into a shell script:

/usr/bin/lynx -source [http://www.showmyip.com](http://www.showmyip.com) | grep "<HTML><HEAD><TITLE>IP Address properties of your Internet Connection" | awk '{ print $8 }'

---

### Post by dmizer on 2007-07-30
best bet is to use the router configuration because the router will automatically update the dynamic service the same instant the wan ip changes.

the best you can do with a script is to have it check periodically via cron which could put you out of service for as long as 10 minutes.

---

