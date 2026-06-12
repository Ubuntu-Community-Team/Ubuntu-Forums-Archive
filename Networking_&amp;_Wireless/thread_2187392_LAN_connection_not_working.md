---
title: "LAN connection not working"
date: 2013-11-11
forum: Networking &amp; Wireless
---

### Post by zach.toolson on 2013-11-11
Hello all!

I just installed ubuntu for the first time on an old desktop (at the suggestion of a good friend). The installation went well, but it didn't seem to detect my wired internet connection. This desktop has no wireless card currently, so wired had been my only option. I have tested the wired connection on a Windows 7 laptop and it works fine. Is there any way to get this to work??

-Zach

---

### Post by TheFu on 2013-11-12
What do the log files show? [http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files](http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files)
What hardware is inside your machine? [http://blog.jdpfu.com/2013/04/27/linux-troubleshooting-101-knowing-your-hardware](http://blog.jdpfu.com/2013/04/27/linux-troubleshooting-101-knowing-your-hardware)
Where is the networking failing? [http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking)

---

### Post by Bucky Ball on 2013-11-12
Please give the results of:

```
sudo lshw -C network
ifconfig
```

Thanks.

---

