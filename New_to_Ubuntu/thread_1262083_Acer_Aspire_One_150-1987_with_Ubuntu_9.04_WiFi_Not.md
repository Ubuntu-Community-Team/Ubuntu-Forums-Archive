---
title: "Acer Aspire One 150-1987 with Ubuntu 9.04 WiFi Not Working"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by gccradioscience on 2009-09-09
After I installed Ubuntu 9.04 for the first time, the WiFi worked well.  After installing the so called security updates the WiFi dropped out.  All I have to get online is the Ethernet connection.   I have places to go and people to see and I want to take my netbook with me.  SInce I cannot get it to work,  I have to leave home 
all the time.  

More info about me and linux: Using and installing programs with Ubuntu seems that it requires computer science degree than it does with using  Windows XP or Mac.   I have used Windows since 1998, but did not know about Linux, but heard about it while browsing for software.  My friend introduced it to me and recommended me to get Debian, I was not well educated about it.  Back in 2008 I started linux with the Live CD called Knoppix. This  year I am using Ubuntu cause others are using it because of not having an OS 
on my netbook.  Still have Windows XP SP3 on my Compaq desktop though.      

Back to this:  Can someone help me with reactivinig my WiFi connection?  Or do I have to reinstall Ubuntu.  I know when I get Windows back I will keep Ubuntu handy.

---

### Post by nothingspecial on 2009-09-10
It could be a kernel update.

Restart and when you see the bit about grub loading press escape.

Boot into the pevious kernel.

And post your wireless card

```
sudo lshw -C network
```

---

