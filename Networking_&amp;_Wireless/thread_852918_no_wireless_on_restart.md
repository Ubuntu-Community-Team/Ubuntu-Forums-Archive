---
title: "no wireless on restart"
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by bonfire89 on 2008-07-08
hello,

Every time I restart I lose my wireless connection. After 10 minutes of fiddling around, clicking on the network, clicking connect to other network and lots of literally fiddling around I get it to work again.

Further more, occasionally it drops off and I have to do the same fiddling around.

It seems like perhaps it is not set up to connect by default?

thank you

---

### Post by superprash2003 on 2008-07-08
are you using ndiswrapper drivers?

---

### Post by bonfire89 on 2008-07-08
unless those are installed automatically, definitely not. I assume those are good? I will do some research on those.

Thanks.

---

### Post by bonfire89 on 2008-07-09
I believe the wireless card is a


Intel ipw2100


are there any specific installation procedures recommended for this card?

---

### Post by chalewa on 2008-07-09
can you give us the output of 

```
lspci
``` and ```
lsusb
```

then maybe we can figure out the situation..

---

### Post by bonfire89 on 2008-07-09
```
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
01:0a.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
01:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
01:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
01:0d.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 03)

```


```
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

---

### Post by bonfire89 on 2008-07-09
I have had the computer in question in an area that doesn't pick up on the neighbors wifi and it hasn't seemed to drop...

not sure if that makes a difference.


It is a bit of a mystery for sure.






furthermore,

somtimes I have trouble starting xubuntu where the bar freezes like a 5th of the way. Usually I force a shutdown and try again. This time I let sit there and now I'm getting

```
[27200.[seemingly random numbers]] ipw2100: eth1: Failed to start the card. 
```

---

