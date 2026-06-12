---
title: "Gutsy Gibbon and Dell 1450 USB"
date: 2007-11-21
forum: Networking &amp; Wireless
---

### Post by masterplumber on 2007-11-21
Managed to take ownership of an old Dell Latitude laptop which has a 1450 usb adaptor.  After some fun and games trying to get a working ISO image on CD, I finally got Gutsy Gibbon installed late last night.  

I plugged in the 1450 and clicked on the Network icon at the top right hand corner of the screen.  I was amazed to see that my wireless network was recognised.  Also amazed when I clicked on it, entered my WEP key etc. and found I was connected to the Internet right away.

My joy quite quickly turned to frusdtration though as the connection keeps dropping.

So what I really would like to know is whether I can stick with this out of the box functionality e.g. is there some tweak I need to do to stabilise the connection as it stands or should  I go with an ndiswrapper install instead?

Also, if I go with ndiswrapper will I still get the 'roaming' capabilities that seem to be a nerw feature of Gutsy Gibbon?  I would really like to take my laptop out and about to spread the non-windows word, so to speak

---

### Post by masterplumber on 2007-11-21
have done some more investigation and here's what I've found.

By doing nothing i.e. just leaving roaming mode on and using the prism54usb driver that seemed to be activated automatically, I can connect to my wireless network no problem.  I can use synaptic etc. and everything is ok.

Problem arises when I use Firefox.  Connection lasts < 1 minute and then drops out.  Anyone have any ideas?  Is this an ndiswrapper job?

I noticed that there is a Linux directory on the Dell driver CD that came with the 1450 USB adapter and it has a file in it called

Prism-3.03.2-1.noarch.rpm

I tried opening it but got a message saying 'Archive type not supported'.  Would it be worht using alien to change this to a deb and trying to install it?

---

### Post by masterplumber on 2007-11-24
Used ndiswrapper and dellnic driver from the CD.

Had to blacklist the pr54usb module first.

Everything looked ok for about half an hour and then the connection dropped.  Tried my ubuntu desktop in the bedroom which also has a wireless PCI card (Edimax) and found it was dropping its wireless connection after 45 min.

A bit of digging found that my BT home Hub had been upgraded overnight - I didn't realise - and that my custom DHCP settings had disappeared.  Fixed that and everything now working.

So the Dell 1450 USB adapter works ok with ndiswrapper on Gutsy.

---

