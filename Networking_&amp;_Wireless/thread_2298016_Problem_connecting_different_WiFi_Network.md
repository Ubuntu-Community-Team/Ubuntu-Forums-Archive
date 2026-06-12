---
title: "Problem connecting different WiFi Network"
date: 2015-10-08
forum: Networking &amp; Wireless
---

### Post by Boris786 on 2015-10-08
Hello,
I have recently installed Ubuntu 14.04 LTS. I have three WiFi networks showing in my network connections: Netgear68,Netgear68-5G & Netgear68_Ext. 
I can select either Netgear6 or Netgear68-5G but cannot connect to Netgear68_Ext. If I do so there is a temporary disconnection and then Netgear68-5G connects. 
Netgear68_Ext is unsuprisingly an extender and has the right password assigned. The signal strength is substantially better than the other two networks.
Any ideas?

---

### Post by Boris786 on 2015-10-13
I am thinking that no one has an answer to this. I am now looking at the hardware side of the house.

---

### Post by Hadaka on 2015-10-13
Hi, your problem is most likely to be with the extender. When you set up the extender
you told it to broadcast Netgear68_Ext as its essid (extended ssid) and that is exactly
what it is doing.It doesnt care if the originating (real) Netgear68_Ext is working or not
it is powered on and broadcasting as instructed.
Disconnect the repeater/extender and see if you can attach to Netgear68_Ext.
if you can, then reconnect or configure your extender/repeter via its ip.
I have a working netgear repeater/extender so i know that it needs to rebroadcast the
ssid of the ap you are extending, if you are not doing that, it wont work.
good luck

---

### Post by Boris786 on 2016-03-29
Thanks. Sorry for super slow response - the day after posting it just upped and started working. No idea why or  how.

---

### Post by Hadaka on 2016-03-30
I am so glad to know it is now working, all the sleepless nights
not knowing ...;)
Please take the time to mark this thread solved by going  to your
first post of this thread, click Thread Tools and then choose..mark
this thread Solved.
thanks.

---

