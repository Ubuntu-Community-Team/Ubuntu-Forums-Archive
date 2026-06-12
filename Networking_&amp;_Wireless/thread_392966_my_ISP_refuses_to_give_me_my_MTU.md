---
title: "my ISP refuses to give me my MTU"
date: 2007-03-25
forum: Networking &amp; Wireless
---

### Post by raffytaffy on 2007-03-25
i am trying to properly set up my vpn firewall / router. my ISP is time warner cable new york. i called them to find out my MTU and they refuse to give it to me. what can i do? my router is set to 1500 MTU default

my router is netgear fvs114

---

### Post by chewearn on 2007-03-25
Here is a guide using DOS ping (for reference):
[http://www.speedguide.net/read_articles.php?id=156](http://www.speedguide.net/read_articles.php?id=156)

First, find the IP address of  your ISP's server that you are connected to.  You can see this IP in your router status.

Then ping the server, varying the packet size as described in the article, e.g.:

```
ping -s1472 xxx.xxx.xxx.xxx
```


Use decreasing packet size: -s1472, -s1468, -s 1464, -s1460 and so on.  At a certain value, you will start to get replies.  Add 28 to this value and you got the MTU.

---

### Post by raffytaffy on 2007-03-25
> **AstalaVista said:**
> Here is a guide using DOS ping (for reference):
[http://www.speedguide.net/read_articles.php?id=156](http://www.speedguide.net/read_articles.php?id=156)

First, find the IP address of  your ISP's server that you are connected to.  You can see this IP in your router status.

Then ping the server, varying the packet size as described in the article, e.g.:

```
ping -s1472 xxx.xxx.xxx.xxx
```


Use decreasing packet size: -s1472, -s1468, -s 1464, -s1460 and so on.  At a certain value, you will start to get replies.  Add 28 to this value and you got the MTU.

ok i try with 1500 and i get response

---

