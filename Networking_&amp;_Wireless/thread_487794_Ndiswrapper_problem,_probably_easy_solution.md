---
title: "Ndiswrapper problem, probably easy solution"
date: 2007-06-29
forum: Networking &amp; Wireless
---

### Post by number3pencil on 2007-06-29
I'm trying to setup ubuntu on my brothers PC and I'm running into a problem getting ndiswrapper to work.  Were using a trendnet 424 usb adapter and ubuntu fiesty.  I checked the wiki and his card should work.  Here's the steps I've taken:

1) Installed ndiswrapper
2) Installed driver
3) ndiswrapper -l returns "driver present, hardware present"
4) depmod returns no errors
5) modprobe ndiswrapper

now what? NetworkManager doesn't pick up anything and neither does iwconfig. I must be missing something.  Any help is greatly appreciated.

---

### Post by t4thfavor on 2007-06-29
Try this 
[http://sourceforge.net/projects/zd1211/](http://sourceforge.net/projects/zd1211/) 

I guess the card is not on the compat list for ndiswrapper

Source:
[http://murga-linux.com/puppy/viewtopic.php?p=21991&sid=79e3724d6857cc279d3f16e4e3e9fbf3](http://murga-linux.com/puppy/viewtopic.php?p=21991&sid=79e3724d6857cc279d3f16e4e3e9fbf3)

---

