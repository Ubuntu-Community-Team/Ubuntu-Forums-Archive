---
title: "Problem with wireless card--broadcom bcm94318"
date: 2010-07-08
forum: New to Ubuntu
---

### Post by T2manner on 2010-07-08
I installed Ubuntu 10.04 on our Dell Inspiron 530, and couldn't get my wireless card to work.   I read multiple threads about this same problem, but all the different techniques didn't work for me.
I went to the device driver thing and tried to activate the driver, but it didn't work. Some error message came up.  I tried to install b43-fwcutter by addnig the Ubuntu CD to the list of repositories, but another error message came up.  So then I downloaded a .deb b43-fwcutter file on my laptop to install on my desktop, and it installed fine, but when I restarted my computer, wireless still didn't work.
Help please.

I also tried installing the newest linux kernel 2.x.34 or something.  It also didn't work.

I don't have access to the internet at all on the desktop (router is too far away to use Ethernet cable), so any files I install will have to come from my laptop via usb.

ALSO, this wireless card works right out of the box in Fedora 13.  I'm not sure why I'm having so much trouble with Ubuntu :\

---

### Post by sandyd on 2010-07-08
you cant activate the drivers, because you don't have internet to download them.
However, I will point you to the drivers, so that you can get some internet...
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

after installing the driver, and when your internet works, install the one from hardware drivers, because you will have to reinstall this version of the driver each time you grab a new kernel

---

### Post by T2manner on 2010-07-08
The driver is on the Ubuntu 10.04 CD. You have to activate it though.  That's why I added the CD to the repositories and tried to activate it.

---

### Post by Nick_Jinn on 2010-07-08
I tried installing the broadcom driver on an older PC just now, and it DID install because it did recognize a USB wireless card I was using (I am trying to activate the internal wireless card), but not only did that driver not work to activate the internet, but it also disabled my wireless connections and I cant figure out how to undue it. Its not allowing me to reactivate it. The option is dim and wont let me click on it. I also cannot connect with the other wireless card that was just working, so the driver not only doesnt work but its making things worse.

Is there a work around for this? I dont remember this being that difficult. Has something changed with the broadcom drivers? Some kind of update in the download? Whatever it is, its not working out.

---

### Post by T2manner on 2010-07-08
I found the answer here. 
[http://ubuntuforums.org/showthread.php?p=5469730](http://ubuntuforums.org/showthread.php?p=5469730)
It's really easy, and it works!
Hopefully this will help future beginners. Thanks :D

---

