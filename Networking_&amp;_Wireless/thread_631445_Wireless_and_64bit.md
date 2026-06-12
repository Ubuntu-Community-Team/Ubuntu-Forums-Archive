---
title: "Wireless and 64bit"
date: 2007-12-04
forum: Networking &amp; Wireless
---

### Post by Cam1223 on 2007-12-04
There seems to be a problem with the driver in ubuntu 7.10 that handles ralink wireless cards. my connection is fine when i first boot up and then it will go out and i have to reboot to get it back. i have tried "/etc/init.d/networking restart" this rarely brings my connection back. 

when i type dmesg i see the driver rt2x00pci and it reports an error. something about Tx write in an unused space. 

i have tried to fix this using ndiswrapper but i get a bad magic error becuase i am 64bit and the windows driver im using is 32bit. i dont know if they have a 64bit or where to find it. iv looked.

i also tried compiling the rt61 driver for linux but when i try and load it using sudo modprobe rt61 it returns an error saying there is an unknown symbol in the module. 

does someone have a possible solution to this?

---

### Post by Cam1223 on 2007-12-04
come on guys anything..??? :confused:

---

### Post by rikis on 2007-12-04
I have a similar problem...

Using a dell inspiron 1501 with processor amd athlon 64. When booting, strenght is fine but after a little while I cannot use my wireless connection anymore.

I am goin to give it a try ndiswrapper...

Hope someone can help.

---

### Post by charwhee on 2007-12-05
Okay, I am also having problems getting my wifi up since the upgrade blew out my drivers but I'm guessing this is a fairly straightforward install/settings issue rather than a problem with the driver. It seems like there are enough mature linux drivers that you shouldn't have to do ndiswrapper unless that's your thing.

Here's another thread that seems to address this issue:
[http://ubuntuforums.org/showthread.php?t=627030&highlight=RT61](http://ubuntuforums.org/showthread.php?t=627030&highlight=RT61)

Here is the Ralink linux driver page.
[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

Also, one of things I had to remember to do was set the card up to get an IP address using DHCP after going through the setup process. Yeah, well, those "...for Dummies" books are written for guys like me.

---

### Post by kevdog on 2007-12-05
Did you try compiling from source the rt61 drivers from the serial monkey website??

---

### Post by Cam1223 on 2007-12-05
yes iv tried compiling the source rt61 drivers off serialmonkey but when i type sudo modprobe rt61 it tells me theres an unknown symbol. i blacklisted rt2x00pci and rebooted and then did sudo modprobe -r rt2x00pci and it says FATAL: Module rt2x00pci is in use. how is it in use after i blacklisted it??

---

