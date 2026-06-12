---
title: "Intrepid: Can't connect to encrypted (WPA or WEP) networks"
date: 2008-11-02
forum: Networking &amp; Wireless
---

### Post by thread_au on 2008-11-02
Hi all, starting at the bottom of a new forum for me (gentoo user who now has xubuntu on his netbook).

Summary:
Asus eeepc901 with array.org kernel can't connect to protected networks (WPA or WEP). Hidden, unprotected network is fine.

Scenario:
I have an eeepc 901 from Asus. All was well with 8.04.  Aside from the upgrader uninstalling nearly allll my packages (no network drivers, no xfce, no nothing), I finally got to 8.10 (clean install).  I very much appreciated having native ethernet drivers to get started.

I installed the array.org kernel to get wireless. However, whenever I (attempt to) connect a protected network (either WEP or WPA) the password is always rejected. I simply get asked again and again by the network manager for the password.  I know the passwords are correct because a: it worked when I installed 8.04 a month ago, b: i changed it to a really simple one for testing.  I can connect fine to the (hidden) unprotected network.

The problem could be anywhere between ubuntu (and maybe the keyring?) and the array.org kernel (I'll post over there as well).  However, I noticed that someone on the forums here had a similar problem with the Acer Aspire.

Any hints? :)

---

### Post by Tsar on 2008-11-02
Hints none

As i have the same problem

---

### Post by hanzomon4 on 2008-11-02
Try setting NM to automatically connect to the protected network then reboot. I can't connect to any network unless it connects automatically at login.

---

### Post by hln on 2008-11-02
hanzomon4,

I'm experiencing the same problem in 8.10 either upgrafing from 8.04 or clean install--it worked in 8.04.  Can you detail your solution please.  I'm using TRENDNET Wireless router (TEW452BRP) and it seems to me that setting the router to authenticate using WPA2 seems to work.  However, this setting also thwart out my laptop as the W- (built-in) card doesn't seem to support WPA2 :-(

Can someone shed some light?  For NM developper: please add back the codes from the old NM to support WPA.

Thanks.

---

### Post by thread_au on 2008-11-03
Just to clarify... are you guys using a cusom kernel or the standard intrepid kernel?

---

### Post by TomDoe on 2008-11-03
Im on Acer Aspire One A150 with Ubuntu 8.10, I cant connect to WEP(WPA networks either. Works fine with no scurity.

---

### Post by hln on 2008-11-03
I'm using the default kernel came with the CD; I have not compiled or load any custom kernel.  However, I did update the kernet right after the install (via the standard Update Manager over wired eth0 I/F).

---

### Post by Nuetouch on 2008-11-03
Just browsing the threads, but my intrepid 8.10 with a belkin usb wireless adapter connected just fine on my wep network,I had to initiate the key and it works just fine, remember, it is beta, so give your feed back to the developers...

---

### Post by thread_au on 2008-11-12
Has anyone here had any resolution yet?

I guess I can file a bug report, but I'm not sure which package(s) to file it against.

regards

---

### Post by thread_au on 2008-11-13
well, looks like this other thread caught on more... we'll see how that one develops:

[http://ubuntuforums.org/showthread.php?t=963379](http://ubuntuforums.org/showthread.php?t=963379)

Meanwhile, I updated a few packages and now it completely hangs (as in, not even mouse movement) when I try to connect to wireless at all :-/

---

