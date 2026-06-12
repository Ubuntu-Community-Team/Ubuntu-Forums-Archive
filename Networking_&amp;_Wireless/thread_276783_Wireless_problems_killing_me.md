---
title: "Wireless problems killing me"
date: 2006-10-13
forum: Networking &amp; Wireless
---

### Post by bensr20det on 2006-10-13
*Linux newbie here*

I just installed Ubuntu 6.06. I have been reading alot of threads about the card that I am using, a Linksys WMP54G. Everywhere I look it says that I need to have the rt2500 driver. For some reason mine has installed a Broadcom Corp. BCM4306. The computer is not hardwired to the router so I cant download the ndiswrapper. is there anything I can do?

---

### Post by fouadz on 2006-10-13
Use another computer (like friend computer or job computer) and burn the file on a CD.
 :mrgreen: 


Take care!

---

### Post by bensr20det on 2006-10-13
Ok when I look on the CD that came with the wireless card in the Drivers folder it has BCM43xx so i assume the driver is correct and I dont need ndiswrapper. where should I go from here?

---

### Post by dto on 2006-10-13
The driver you have is a Windows driver -- you still need ndiswrapper to use it with Linux. I only looked briefly, but according to the [NdisWrapper wiki page](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List) this card appears to work well with NdisWrapper.

Just looking over my Ubuntu 6.10 CD from my Windows PC at work, it appears that NdisWrapper is on it. You should be able to start Synaptic, search for NdisWrapper and install it from the Ubuntu CD. Once it is installed, you can use 'ndiswrapper -i your_driver.inf' to install the driver you have.

---

### Post by bensr20det on 2006-10-13
I have put ndiswrapper on a CD and tried to install it. I followed the install doc with the file but it tells me to run a few commands "make install" and a few others. when I try to run these commands it says that there is no 'make' command. is it easier to install it from the ubuntu 6.06 install cd?

---

### Post by gvgerman on 2006-10-13
I have a wireless internal device with a Broadcom Corporation BCM4306 chipset and this worked for me:  [How to: Broadcom Wireless cards]("http://www.ubuntuforums.org/showpost.php?p=1071920&postcount=1")

---

### Post by bensr20det on 2006-10-13
Thanks for the guide but it requires the computer to be online and this computer is someplace that I can't hardwire it to the router. If it must be done I can do it that way but I wouldn't mind knowing how to use ndiswrapper. If someone could tell me how to install it from the ubuntu install CD that would be fantastic. thanks.

---

### Post by bensr20det on 2006-10-14
Well I was able to get the box hardwired to the router, followed the guide posted above and everything is working great. thanks everyone

---

