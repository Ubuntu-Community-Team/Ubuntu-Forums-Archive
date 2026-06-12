---
title: "Monitoring &amp; Troubleshooting Tools"
date: 2020-01-24
forum: Networking &amp; Wireless
---

### Post by abbasali31 on 2020-01-24
Hello,

Can any recommend a few open monitoring and troubleshooting tools mainly for Ubuntu Server or others such as Cent-OS?

I am having issues with my network traffic originating from a server and would like to monitor traffic pattern such as packets in/out traffic, buffering issues etc.

Thank You!

---

### Post by TheFu on 2020-01-26
```
man -k network
man -k monitor
```

Use the system to find answers.  If you are running Unix servers, this is a basic skill.  Anyway, you'll see more tools than you'll want to use.  **netstat** is normally used, but for some specific needs, **lsof** is handy.  If the firewall is involved, there's a bunch information gathering/showing options for most firewalls.

When it comes to buffering, you'll probably want/need to read a few deep articles, since network buffering is a complex topic where larger isn't usually better.

---

