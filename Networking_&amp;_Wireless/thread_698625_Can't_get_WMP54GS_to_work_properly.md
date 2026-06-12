---
title: "Can't get WMP54GS to work properly"
date: 2008-02-16
forum: Networking &amp; Wireless
---

### Post by MrDavinator on 2008-02-16
I am an absolute ubuntu beginner.  I installed it earlier today, and cannot get any internet working.  I have installed the AMD 64 bit version of Ubuntu.

I am trying to get my Linksys WMP54GS working correctly.  I have installed the driver using ndisgtk to convert the BCMWL5.inf file from my windows install disk, and the Wireless Network Drivers window says that the hardware is present.  I can't see any wireless networks though.

I have searched these forums and googled for hours, and I am still not able to get this working.  Please, any help would be appreciated!!

---

### Post by Hightide on 2008-02-17
Hi Mr Davinator

please can you post the output from 

```
sudo lshw -C network
```


```
sudo iwconfig
```

regards

:)

---

