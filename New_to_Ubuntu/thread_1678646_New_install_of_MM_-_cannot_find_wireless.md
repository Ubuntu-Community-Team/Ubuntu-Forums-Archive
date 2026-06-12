---
title: "New install of MM - cannot find wireless"
date: 2011-01-30
forum: New to Ubuntu
---

### Post by eeprom on 2011-01-30
Hello,
I just installed ubuntu 10.10 onto a Compaq laptop.  The OS doesn't seem to recognize the wireless card.  Can someone please tell me how to find the wireless card?  
thanks.EE

---

### Post by sandyd on 2011-01-30
> **eeprom said:**
> Hello,
I just installed ubuntu 10.10 onto a Compaq laptop.  The OS doesn't seem to recognize the wireless card.  Can someone please tell me how to find the wireless card?  
thanks.EE
a) Go to System -> Administration -> Hardware Drivers and check for anything to do with wireless

b) if it doesnt, 
Go to Applications -> Accessories -> Terminal and
post output of
```

lspci
```cute cockatiel btw ;)

---

### Post by eeprom on 2011-01-30
The bird is Reggie.  Sorry to say he recently passed away.  

So, I don't have the Hardware menu, as I had hoped.   I went to a terminal and entered lspci.  I suppose this is a readout of the hardware devices. This is some of what I came up on the terminal...

06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

It appears that the wireless card is visible to the system.  Do you know what I need to do to activate it?

thanks,
EE

---

### Post by sandyd on 2011-01-30
> **eeprom said:**
> The bird is Reggie.  Sorry to say he recently passed away.  

So, I don't have the Hardware menu, as I had hoped.   I went to a terminal and entered lspci.  I suppose this is a readout of the hardware devices. This is some of what I came up on the terminal...

06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

It appears that the wireless card is visible to the system.  Do you know what I need to do to activate it?

thanks,
EE
Im sorry to hear that :(

Theirs a bug in ubuntu 10.10 right now, the wrong firmware gets installed. check out [http://art.ubuntuforums.org/showpost.php?p=10020899&postcount=3](http://art.ubuntuforums.org/showpost.php?p=10020899&postcount=3)

---

### Post by eeprom on 2011-01-30
Thanks for your help.  The wireless is functioning.  I went to System >>  Additional drivers, and then did the update of drivers.  I actually don't know why that worked, but it did.

EE

---

