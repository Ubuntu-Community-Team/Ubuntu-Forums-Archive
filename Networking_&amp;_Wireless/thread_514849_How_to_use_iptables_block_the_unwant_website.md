---
title: "How to use iptables block the unwant website?"
date: 2007-08-01
forum: Networking &amp; Wireless
---

### Post by xiehuipiaofeng on 2007-08-01
Hi,
I want to block the unwant website using iptables(ubuntu server 7.04, iptables 1.3.6) without any patchs. In some sugguestion, they let me try to use the ** -m string --string "sex"** to do it. But when i run the script, it tells me that i also need install many .so libs. So i want to know whether i can block website or download link,just like "http://www.abc.com/abc.mp3", using the iptables' rule directly.

Thank you!

---

### Post by frodon on 2007-08-01
You can easily deny the IP of the site with iptables, now for web filtering what you need is dansguardian and squid, here is a small dansguardian and squid guide :
[http://software.newsforge.com/software/04/06/23/1521209.shtml](http://software.newsforge.com/software/04/06/23/1521209.shtml)

---

### Post by xiehuipiaofeng on 2007-08-01
> **frodon said:**
> You can easily deny the IP of the site with iptables, now for web filtering what you need is dansguardian and squid, here is a small dansguardian and squid guide :
[http://software.newsforge.com/software/04/06/23/1521209.shtml](http://software.newsforge.com/software/04/06/23/1521209.shtml)

Thank you. But i just want to use the iptables without install any others. And how to do it? it's can be done just by iptables itself?

---

### Post by frodon on 2007-08-01
To deny a site i would add  rules like that :
```
iptables -A INPUT -s abc.com -j DROP
iptables -A OUTPUT -d abc.com -j DROP
```

If it can help you here is a small guide i wrote about iptables :
[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)

---

### Post by xiehuipiaofeng on 2007-08-01
Thank you for your guide and reply. It's maybe i express ambiguously. In fact, I want to block the download links of the music, video, or else. I want to prohibit the users from downloading any format music like .mp3,wma, etc. I can do it with the expression like "*.mp3" or "mp3$" ?

---

### Post by frodon on 2007-08-02
you definitely need a dansguardian setup :
[http://dansguardian.org/?page=introduction](http://dansguardian.org/?page=introduction)

Dansguardian allows file extension filtering but not iptables unfortunately.

With the 2 links below you should be able to install your squid + dansguardian setup easily :
[https://help.ubuntu.com/community/SquidGuard](https://help.ubuntu.com/community/SquidGuard)
[http://software.newsforge.com/software/04/06/23/1521209.shtml](http://software.newsforge.com/software/04/06/23/1521209.shtml)

---

