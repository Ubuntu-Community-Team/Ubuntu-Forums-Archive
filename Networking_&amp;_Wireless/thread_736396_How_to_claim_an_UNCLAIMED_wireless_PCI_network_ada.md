---
title: "How to claim an UNCLAIMED wireless PCI network adapter RTL8085"
date: 2008-03-26
forum: Networking &amp; Wireless
---

### Post by blokkendoos on 2008-03-26
Dear groupers,

The topic header states rtl8085 but in fact it is all about a RTL8185. Sorry

The output of  lshw -C network on my GG 7.10 installation tells me the rtl8185 chipset on my wireless adapter is UNCLAIMED. 
It used to be Disabled. 
Then I started out to get it to work following KevDogs ndiswrapper how to.
The card is no longer listed in dmesg, but the device manager shows it is there.
The question seems to be: how to claim an unclaimed network adapter.

tia

pablo k

---

### Post by blokkendoos on 2008-03-27
Dear groupers,

It seems the way to claim an unclaimed wlan nic is to use the right driver file. On my rtl8185 nic I used the latest XPdrivers from the manufacturer SMC with ndiswrapper. Not the right ones.
I tried the old ones on the CD-ROM shipped with the card and my nic became unclaimed.
Used drivers: net8185

thanks,

pablo k

---

