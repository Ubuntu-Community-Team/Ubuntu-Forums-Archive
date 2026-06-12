---
title: "New install : network and drivers issues"
date: 2016-07-18
forum: Networking &amp; Wireless
---

### Post by eitanedi on 2016-07-18
hello,
Green as they come in Ubuntu.
Got a new PC and went for Linux. AMD 8350 , GA990XA , Asus GT710 ( nvidia ). Ubuntu mate 16.04
Questions :
1. Started with TPLink WN725N , worked at about 1/10 the speed I get in my laptop ( 2 mbps vs 20 ).
Tried various fixes from forums, gave it up, got Edimax EW7711USn. Now working at half speed of my laptop ( 10 vs 20 ).
Bit Rate=81 Mb/s  Tx-Power=20 dBm
... Power Management : off  Link Quality=37/70  Signal level=-73 dBm
... Tx excessive retries:354  Invalid misc:82
Is this the best the hardware can do, or am I doing something wrong ?
It worked OOTB, didn't install the Edimax driver, downloaded bot couldn't find how to, and I have no CDRom.

2. On my first Ubuntu-mate 16.04 install a few days ago,
Ubuntu prompted and downloaded 2 proprietary drivers : one for AMD and one for the GPU.
Since then did several re-installs because of network tinkering.
Now 'additional drivers' says no propietary drivers in use and no additional drivers available.
How can I get the proprietary drivers ?

Thanks and sorry if I mixed issues, tell me if I should split questions by forums.

---

### Post by mastablasta on 2016-07-18
> **eitanedi said:**
> hello,
Green as they come in Ubuntu.
Got a new PC and went for Linux. AMD 8350 , GA990XA , Asus GT710 ( nvidia ). Ubuntu mate 16.04
Questions :
1. Started with TPLink WN725N , worked at about 1/10 the speed I get in my laptop ( 2 mbps vs 20 ).
Tried various fixes from forums, gave it up, got Edimax EW7711USn. Now working at half speed of my laptop ( 10 vs 20 ).
Bit Rate=81 Mb/s  Tx-Power=20 dBm
... Power Management : off  Link Quality=37/70  Signal level=-73 dBm
... Tx excessive retries:354  Invalid misc:82
Is this the best the hardware can do, or am I doing something wrong ?
It worked OOTB, didn't install the Edimax driver, downloaded bot couldn't find how to, and I have no CDRom.

what chip is it? does it have official linux driver? is the correct driver loaded on boot?

> 
2. On my first Ubuntu-mate 16.04 install a few days ago,
Ubuntu prompted and downloaded 2 proprietary drivers : one for AMD and one for the GPU.
Since then did several re-installs because of network tinkering.
Now 'additional drivers' says no propietary drivers in use and no additional drivers available.
How can I get the proprietary drivers ?


we do not know what "tinkering" you did in order to undo it. you can however always install nvidia drivers manually or add a PPA for them and install thoguh PPA. but you can first try to install them via command line and see if any errors are reported. 
[/QUOTE]
Thanks and sorry if I mixed issues, tell me if I should split questions by forums.[/QUOTE]

yes, it would be better to split them. one of these goes into networking area of the forums the other one into hardware/general help.

you posted in new to Ubutnu. people new to ubuntu shouldn't tinker too much and blindly follow various tutorials :P

---

### Post by grahammechanical on 2016-07-18
> Now 'additional drivers' says no proprietary drivers in use and no additional drivers available.

The machine needs to be connected to the internet otherwise Additional Drivers will not be able to find proprietary drivers. It could also be the reason that the utility is not reporting any proprietary video drivers in use when you know a proprietary video driver is being used.

Regards

---

### Post by jeremy31 on 2016-07-18
Moved to networking
Please visit the wireless script link in my signature and post results

---

### Post by eitanedi on 2016-07-18
Connection looks good now *fingers crossed*. Consistent at 20 Mbps, same as my laptop. Maybe another pc was downloading.
I'll see how it goes in the coming days. If all ok, I'll note it here so anyone who searches for a good wifi linux bet can see. 
The chip is rt3070. It does come with proprietary driver ( from 2008 ) but I didnt install it.

Anyway, there was constant connection, just with varying speeds, so this is not the issue with the drivers.
Still no proprietary drivers installed and no additional drivers available.
How do I install manually ? Is there anything parallel to 'device manager' in windows ? 
How do I know if my hardware is running optimally ?

---

### Post by jeremy31 on 2016-07-18
If it causes problems in the future just post the wireless script results or do some searching for info based on what the wifi card shows up in ```
lsusb
```
Sometimes you can find solutions that are recent enough to be useful

---

