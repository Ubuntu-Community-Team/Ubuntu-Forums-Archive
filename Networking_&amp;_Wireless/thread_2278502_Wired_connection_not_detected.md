---
title: "Wired connection not detected"
date: 2015-05-17
forum: Networking &amp; Wireless
---

### Post by proxydev on 2015-05-17
I'm a Linux newbie and I don't know how to permanently fix a problem that I'm having. Please help me fix this AND find out the reason this is happening.

**My problem:**

Even though I have my ethernet cord connected to my desktop, I still can't connect to the internet. The only time I can connect to the internet is when I do the command: ```
sudo ethtool -s eth0 autoneg off speed 100 duplex full
```

I found that command on this site: [http://www.garron.me/en/linux/ubuntu-network-speed-duplex-lan.html](http://www.garron.me/en/linux/ubuntu-network-speed-duplex-lan.html)
The "permanent fix" listed at the bottom of the site actually ruined my network interface and caused it to not start.

Now, I've done web searching and have came across a ton of post that relates to my problem. Guess what? Every fix that helpers recommended did not work. Hopefully this time'll be different.

---

### Post by chili555 on 2015-05-17
Did you try dropping the command without sudo into /etc/rc.local?

---

### Post by proxydev on 2015-05-17
I managed to fix my problem. The problem was my Realtek drivers.

 I fixed the problem by following these guides:

[http://crunchbang.org/forums/viewtopic.php?pid=316644#p316644](http://crunchbang.org/forums/viewtopic.php?pid=316644#p316644) 
[https://unixblogger.wordpress.com/2011/10/18/the-pain-of-an-realtek-rtl8111rtl8168-ethernet-card/](https://unixblogger.wordpress.com/2011/10/18/the-pain-of-an-realtek-rtl8111rtl8168-ethernet-card/)

---

