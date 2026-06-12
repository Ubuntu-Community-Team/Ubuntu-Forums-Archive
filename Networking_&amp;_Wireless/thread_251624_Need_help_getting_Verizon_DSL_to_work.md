---
title: "Need help getting Verizon DSL to work"
date: 2006-09-05
forum: Networking &amp; Wireless
---

### Post by catzoo on 2006-09-05
I just installed Ubuntu on my old Dell Latitude CPt (bought new in 2001, has a 650 Celeron chip), everything set up well but can't get the Verizon DSL to work. I connect to the DSL modem (Westell) through my USB port, rather than ethernet (my computer doesn't have an ethernet card). Could this be causing the problem?  As I understand it, Ubuntu is supposed to recognize DSL automatically and set itself up.  I am not a technical person, can anyone offer help?

---

### Post by whizbaby on 2006-09-05
There's two possibilities:
either you have a router which has the ability to store username and password and connects itself to the provider. Then you only would have to get the connection between your modem and your computer right.(this could be done with the command 'dhclient', see 'man dhclient' for useage)
Or you send authentication information at the beginning of each session, in this case you would use 'pppoeconf' (again see manual).
The thing I just don't know is what your device's name in /dev is. (/dev/modem maybe? doesn't have to, this usb always fools me...)

---

### Post by catzoo on 2006-09-06
I read last night that modems that connect to the laptop through a USB port are very difficult to set up with Ubuntu. Again, this is an old computer, so I didn't have an ethernet connection built in. 

What would happen if I install a ethernet connector into my pcmcia slot, thereby bypassing the USB?  Would this be easier?  If I do this, would ubuntu recognize my verizon dsl connection automatically, or would I have to do some setting up.  Again, I am not a technical person

---

### Post by skymt on 2006-09-06
Yes, the USB connection is the problem. An ethernet PCMCIA card would fix it. Once you get one, see [this HOWTO](https://help.ubuntu.com/community/ADSLPPPoE) for.. well... how to!

---

### Post by catzoo on 2006-09-06
Thanks very much - I'll try the pcmcia and see if it sorts out

---

### Post by catzoo on 2006-09-07
I got it fixed. Last night I went to Circuit City and bought Ethernet PCMCIA card to plug into my laptop, cost $22 (the cheapie Circuit City brand).  No longer have to worry about USB issues.  I booted the computer and immediately had verizon dsl connection working. Simple as that. :D

---

