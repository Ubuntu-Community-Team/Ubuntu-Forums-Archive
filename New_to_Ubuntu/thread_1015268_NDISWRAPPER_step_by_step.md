---
title: "NDISWRAPPER step by step?"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by cautiouschris on 2008-12-18
Got Ubuntu loading off thumb drive beautifully. Now comes the challenge of configuring the dreaded Broadcom Wlan. Is there a step by step guide to installing ndiswrapper and/or wine?

Kindest Regards,
Cc

---

### Post by bobnutfield on 2008-12-18
Hello, 

Welcome to Ubuntu.  Which version are you running?  The 2.6.27 kernel used in Intrepid has much greater support for wireless chipsets than previous kernels.  However, if you would like a link to a solved thread for getting broadcom cards working:

[http://ubuntuforums.org/showthread.php?t=766560]("http://ubuntuforums.org/showthread.php?t=766560")

---

### Post by Michael.Godawski on 2008-12-18
good luck :p

[LIST]
[*][https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper))
[/LIST]
Feel free to cry for help...I had once a Broadcom too. I emphasize "had"... 

Have you checked if there are any drivers inactive in 
System > Administration > Hardware Drivers?

---

### Post by cautiouschris on 2008-12-18
yeah, that might help...Ubuntu 8.10. Not sure about the kernel though...

---

### Post by bobnutfield on 2008-12-18
If you have 8.10, then you are using the latest 2.6.27 kernel.  As mentioned, check in System>Administration>Hardware Drivers and see if anything for your wireless is there before trying NDISWRAPPER.

---

### Post by stchman on 2008-12-18
I believe you can use the ndisgtk and use a graphical front end to install Windows wireless drivers.

---

### Post by cautiouschris on 2008-12-19
Thanks to all. I will follow these suggestions and con't my research.

Cheers,
Cc

---

