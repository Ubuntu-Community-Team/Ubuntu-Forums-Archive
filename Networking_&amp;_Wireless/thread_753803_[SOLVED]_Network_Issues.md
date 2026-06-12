---
title: "[SOLVED] Network Issues"
date: 2008-04-13
forum: Networking &amp; Wireless
---

### Post by eeboy on 2008-04-13
I've got ubuntu running from the CD on a IBM Thinkpad. I have established connectivity via a wired network. I can ping other computers in my local network, I can ping external networks via IP and URL (ex: [www.google.com](www.google.com)). All the other computers in my local network can access the web with no issues. However, the ubuntu laptop can not access 99% of the web pages I attempt to get at. The only pages I've had success with are google and ubuntu.

Any suggestions as to what could be the cause of this?

---

### Post by wormser on 2008-04-13
It sounds like it could be a DNS issue.  A good test for this is pinging by name and IP address.  If you can ping my IP and not the name then it is a DNS issue.

```
ping ubuntuforums.org
``````
ping 91.189.94.186
```I recommend using the [OpenDNS]("https://www.opendns.com/start/ubuntu.php") servers.

---

### Post by eeboy on 2008-04-13
No problems with that. I get 100% response to all my pings (by name or IP).

It's not just web pages that aren't loading either. I just tried to get up and running on Pidgen (IRC) and that fails as well. It's very strange.

---

### Post by eeboy on 2008-04-13
Also, I don't know if this means anything... but If I do a trace route on different sites (google, yahoo, etc) some of them take several hops (7-8)and then it seems to fail (no reply). The host prior to the failure isn't consistent.

---

### Post by wormser on 2008-04-13
Try setting up [OpenDNS]("https://www.opendns.com/start/ubuntu.php") to rule out any DNS issues.  Then we can go from there.

---

### Post by eeboy on 2008-04-13
Thanks wormser!

I overlooked that in your first post. That worked. But why? I was resolving names prior using my ISPs DNS. Any thoughts?

---

### Post by wormser on 2008-04-13
I am no expert with DNS.  I just understand the symptoms.  Click the star icon in the lower right hand corner of the post that helped.  It gives thanks and helps the next person viewing the thread find the solution.  Also, mark the thread as Solved.

---

