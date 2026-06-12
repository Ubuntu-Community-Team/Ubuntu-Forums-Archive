---
title: "Wifi issue, broadcom 4313 network adapter ubuntu 13.10 64 bit"
date: 2015-01-11
forum: Networking &amp; Wireless
---

### Post by dinesh14 on 2015-01-11
I m new to ubuntu , and successfully dual booted it with windows 8.1 using ubuntu usb. I m using lenovo ideapad z580 laptop with core i5, and 4 gb ram. After installing ubuntu i got a grub v2, boot manager from where i selected ubuntu. But it ended up with a purple screen. After waiting for some, again i started the laptop, and this time it ended up with black screen with a blinking cursor where i can type texts. Then i forcefully shut down it by holding power key and again started, however this time it booted successfully. But now i m facing problem of wifi connection as i m not able to see available wifi network which other device can see. But ethernet is working fine. I connected my phone using cable and its just working fine but wifi is not working. After sometime it shows some networks but with 0 stregth. I m very new to ubuntu and require ur urgent help regarding this. I tried several methods from here but i cant able to get them. So plz solve my issue as simple as possible...

---

### Post by Impavidus on 2015-01-11
You need some broadcom drivers for your wifi. Broadcom is often problematic. The additional drivers utility is designed for that, so if you run it, it will search the repositories for drivers for your wifi card, using your wired connection. But not on 13.10. Ubuntu 13.10 is end of life and the repositories have been removed. Try installing Ubuntu 14.04.

---

### Post by coldraven on 2015-01-11
+1 for installing 14.04

---

### Post by Rob Sayer on 2015-01-11
The drivers you get from Additional Drivers do NOT always work.  I found this out the hard way.  More than once.  I never install them now without checking first.

Ditto on installing 14.04.

One thing about broadcom is that they release different actual adapters under one model name.  LIke the 4313.  You need to know the difference, ie the PCI ID.  See:

[http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)

You don't want the proprietary driver for the bcm4313 in 14.04.  Another guide:

[http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers)

My netbook has a 4313 with PCI ID 14e4:4727 (the number after 14e4: is the real model number really).  I did the step in the last link a couple of days ago involving installing firmware-b43-installer.

I did this with some nervousness because it seems at odds with other stuff I've found from very knowledgeable sources.  So far it seems to be working well, but I only use this netbook outside at wifi hotspots.  It's difficult to test so I'm not 100% sure I'd recommend it to someone else yet.

One thing I'd also point out is that whatever you find out there, don't do it unless it:

... says it's for your ubuntu release version and
... you have an idea how to undo changes if they don't work.  Unfortunately there are a lot of blogs that never tell you how to undo them.

---

### Post by Sef on 2015-01-11
[COLOR=#000000]```
... you have an idea how to undo changes if they don't work. Unfortunately there are a lot of blogs that never tell you how to undo them
```

That's why it is best to back your OS.  To do so, use [clonezilla]("http://clonezilla.org/").[/COLOR]

---

### Post by Rob Sayer on 2015-01-16
Just thought I'd mention:  as mentioned in my previous post here I installed firmware-b43-installer 4 or 5 days ago but was unwilling then to comment because it was too new.  I don't use this netbook at home much.

But after using it out a bunch of times, I do think it's working better since I installed it.

---

