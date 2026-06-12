---
title: "WPN111 hangs after 1 to 5 min"
date: 2008-02-07
forum: Networking &amp; Wireless
---

### Post by aos on 2008-02-07
Hi

I followed the post [http://ubuntuforums.org/showthread.php?t=652910](http://ubuntuforums.org/showthread.php?t=652910)  on HowTo ndiswrapper WPN111  and it worked quite well.

but after rebooting the PC with the usb card pluged. It works during 5 minutes and then the signal disapears.  

I run sudo ifdown wlan0, then sudo ifup wlan0. But then it never gets back up again.

Does anybody got the same problem?
I am running Ubuntu 7.10 updated.  The ndiswrapper I have installed is the one provided by the Ubuntu repositories.

Cheers
Alfonso

---

### Post by aos on 2008-02-07
I forgot to comment that if I reboot the PC, it works again, but the same problem appears.

---

### Post by Erwin Criddle on 2008-03-05
This is a common problem with ndiswrapper. Instead of restarting Ubuntu, shutdown the system instead.

---

