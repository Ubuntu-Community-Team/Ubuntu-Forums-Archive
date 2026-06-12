---
title: "SiS900 Fast Ethernet in Ubuntu on Clevo 2700c 'Speed'-laptop ?"
date: 2006-09-23
forum: Networking &amp; Wireless
---

### Post by timvets on 2006-09-23
the machine is this:

[http://www.clevo.com.tw/products/2200c.asp#](http://www.clevo.com.tw/products/2200c.asp#)
(-> 2700c )

lspci lists this ethernet card as
Ethernet Controller: Silicon Integrated Systems (SiS) SiS900 Fast Ethernet (rev 82)
under windows it always worked, now installed Ubuntu (latest version today) and internet or network doesn't work.
I'm rather newbie, any help please ?

thanks!
Tim

---

### Post by spd106 on 2006-09-24
This device should work fine using the sis900 driver. Does it show up in **ifconfig**? If not, could you see if the driver is being loaded, **lsmod | grep sis**?
Looking through the output of **dmesg** may also turn up some info.

---

### Post by timvets on 2006-09-28
>Does it show up in ifconfig? 

ifconfig gives something similar to what it says on this computer (with which I can acces internet)

>If not, could you see if the driver is being loaded, lsmod | grep sis?

it shows up 

mii 5888 1 sis900

>Looking through the output of dmesg may also turn up some info.

dmsg shows 2 entries of sis 900

one with just the version and date
the other:
eth0: SiS 900 PCI Fast Ethernet at 0x3200, IRQ 10, 0:90:f5:0a:00ea 

thanks 
tim

---

### Post by timvets on 2006-09-28
(just doing some guessing)

the last line in dmesg is:
'no IPv6 routers present'

---

### Post by spd106 on 2006-09-29
That last line about ipv6 shouldn't be an issue, everyone gets that.

According to the info you've supplied the card should be working. Does it show up in the System > Administration > Networking applet? It should be called eth0 and say that it is active. Do you have a DHCP server or do you need to give it a static IP address?

---

