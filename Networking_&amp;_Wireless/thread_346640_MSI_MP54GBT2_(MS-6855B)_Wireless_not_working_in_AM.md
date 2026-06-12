---
title: "MSI MP54GBT2 (MS-6855B) Wireless not working in AMD X64 Edgy"
date: 2007-01-26
forum: Networking &amp; Wireless
---

### Post by Zarky on 2007-01-26
Hi! First post here so be nice ;)

I have install Dapper and Edgy 64 bit on Wifes laptop ([MSI S270]("http://www.msicomputer.com/NB/product_spec.asp?model=S270") AMD Turion) and have installed most of the drivers and Ubuntu is mostly wife approved. :)

I did say most drivers, the Wireless doesn't work. It's an MSI [MP54GBT2]("http://www.msicomputer.com/product/p_spec.asp?model=MP54GBT2&class=com") and I have searched high and low for several months looking for a fix for this card. I've compiled drivers from [rt2x00.serialmonkey]("http://rt2x00.serialmonkey.com/") legacy and the rt2x00 Experimental. I've tried the source from [Ralink]("http://www.ralinktech.com.tw/"). The ones built into Ubuntu don't work either. The best I could get is it'll connect / disconnect and repeat this every second using RaConfig2500. h yeah, I've even tried NDISwrapper using various X64 windows drivers. nadda. locks up ubuntu during boot.

So, if anybody has this Wireless card and has gotten it to work with ubuntu X64, please let me know how ya did it!!??

Other info: Chipset is a Ralink rt2560f (opened it up and looked) has some sort of Bluetooth (works with BT Mouse btw)
Wireless Access point is WPA encrypted, but during testing, I have tried open and wep.
Would like it easy to use with multiple AP's (in other words, be Wife approved)
Card Reader doesn't work, but thats for another post ;)
Dual boot to Win XP Pro, smoked 1 install of Dapper trying to get Wireless to work (have since learnt about recovery option in grub ;)

Thank you

---

### Post by xcb on 2007-02-03
I've got a MS-1029 with the RT2560F chipset on my BT/Wifi card.

Instead of Raconfig, I installed RutilTv0.13

[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500)

and it worked like a charm. I, too, was having all sorts of silly issues - and they seem to have cleared up. 

YMMV, of course! Good luck!

---

