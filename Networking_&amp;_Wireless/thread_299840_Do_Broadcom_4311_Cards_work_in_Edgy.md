---
title: "Do Broadcom 4311 Cards work in Edgy?"
date: 2006-11-14
forum: Networking &amp; Wireless
---

### Post by unbuntu kid on 2006-11-14
I have drapper (6.06.1) installed on my laptop, and have to use Linuxant's windows driver support to use my Broadcom 4311 wifi.  I was wondering if Edgy (6.10) supported the broadcom 4311 device without Linuxant.

This is because Linuxant 's free licence expires in 30 days, and ndiswrapper doesn't like me at all.

---

### Post by funky_munky on 2006-11-24
I had a hard time finding what would work but it does in fact work.  I am using Kubuntu edgy with ndiswrapper 1.28 compiled and used the driver off of Dell's website.  I am connected right now using knetworkmanager to connect to a wpa2 psk aes network.

if I can find the link to he thread that helped me I will post it here but the key was using the latest stable ndiswrapper.

ah hah I found the thread.

[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

this should work regardless of dapper or edgy

---

### Post by FrodoB on 2006-11-24
Ndiswrapper works for me.  Here is the procedure that I followed:

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show)

I am not normally a big fan of using NDIS drivers, but in this case ndiswrapper is quite solid so far.

---

