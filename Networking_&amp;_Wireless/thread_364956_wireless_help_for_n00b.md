---
title: "wireless help for n00b"
date: 2007-02-18
forum: Networking &amp; Wireless
---

### Post by nonewmsgs on 2007-02-18
dlink 650 revP is a prism2 or a 3 depending on what site i looked at.   either way it requires the  linux-wlan-ng driver.  but i dont know if the linux wlan ng driver is new enough for any of the modern kernals.  other sites said that it is preinstalled and needs firmware.  i have a terrible headache and spent many hours and cannot conect wirelessly.  maybe i should have posted in the wireless/network forum, but iread most of those articles and i dont know if im up to that level and i dont want to doublepost.  i did look for ndiswrapper in add/remove and didnt see it.

someone please tell me what to do in english.  im very frustrated and i just want it to have internet access.

---

### Post by crispy_420 on 2007-02-19
How bout posting the exact model number?

(Such as DWL-650)

Maybe a link for us a dlink's home page?

---

### Post by nonewmsgs on 2007-02-19
[http://support.dlink.com/products/view.asp?productid=DWL%2D650%5FrevP](http://support.dlink.com/products/view.asp?productid=DWL%2D650%5FrevP)
dlink dwl 650 revision p pcmcia 802.11b

i have the cd for the drivers, and read a recent post on downloading, installing ndiswrapper (it was a wiki article and was straightforward not like the crytic knowledge googled sites were giving me)

here's what went down with that:
(first i had more difficulty with xubuntu than ubuntu with copying and pasting.  i kept getting directory read only errors.  i never got those with ubuntu)

$ sudo ndiswrapper-1.8 -i /home/prism.inf
installing prism
couldn't copy /home/prism.inf at /usr/sbin/ndiswrapper-1.8 line 144.
$ sudo ndiswrapper-1.8 -i /home/prism.inf
prism is already installed.  Use -e to remove it
$ sudo modprobe ndiswrapper 
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid arguement
$

thank you,
nonewmsgs

---

### Post by crispy_420 on 2007-02-20
Did you try installing linux-wlan-ng? I does say it supports prism chipset cards and I think that is what you have.

[dlink support for linux]("http://support.dlink.com/faq/view.asp?prod_id=357")

---

### Post by nonewmsgs on 2007-02-21
ok.  i downloaded the latest version for my card.  but im having some trouble installing it.  i extracted the tar (keeping directories intact) and ran the makefile as a program.  i think it made a pda.pl script.  i ran it but nothing seemed to happen.  did i not do something or do something wrong?  i checked in networking and it doesnt show the wireless card, but interestingly it is in the device manager.

but it has always been in the device manager.  teasing me.

---

### Post by nonewmsgs on 2007-02-23
well right now i still dont have it working, but i am not dismayed for i have another pcmcia wireless card i could use if it's easier!!!11

[http://www.netgear.com/Products/Adapters/RangeMaxAdapters/WPN511.aspx](http://www.netgear.com/Products/Adapters/RangeMaxAdapters/WPN511.aspx)

netgear wpn511
will that help?

---

### Post by nonewmsgs on 2007-02-25
well since i want to probably move the other laptop to ubuntu i decided it wouldnt make sense to just stop in the middle figure out the other one and then after i convert my other laptop to have this same trouble again, so i played around and figured out that i was installing the driver wrongly, but i did manage to figure it out.  there was a faq and a readme, but carefully following directions got me to a point where i at least have an easier error (most likely )to fix.

error: stdio.h: no such file or directory
error: stdlib.h:no such file or directory
error: string.h:no such ...
error: ctype.h:no such

i realize these are all basic C headerfile libraries so at first i was a bit surprised by this not being already installed, but then i said "im certain synaptic has my standard libraries!", and standard libraries galore, indeed, but i dont see/am not sure where are the libraries i need.  which ones do i need?

---

