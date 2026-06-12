---
title: "How do You lock broadband connection to 3G/W-CDMA only????"
date: 2010-09-08
forum: New to Ubuntu
---

### Post by suomalainen on 2010-09-08
Ubunteros,

In Network Connection Manager there is no way to lock your wireless GSM broadband connection to 3G (WCDMA) only!!!

This means that if your stick  starts to bounce between 3G or GPRS (2G) then you are likely to be disconnected and needing to re-boot your machine. More so, when there isn't a seemless IP handoff within the network thus adding to complications.

Here's my question. Is there any recommended program I can use to establish my 3G GSM broadband connection and then remain locked onto 3G only????

Thanks for your support!!!

---

### Post by suomalainen on 2010-09-13
knock.... knock.......

---

### Post by suomalainen on 2010-09-19
Any suggestions?

---

### Post by waynefoutz on 2010-09-19
the only suggestion I can come up with is to install the windows utility that comes with the modem or from Sprint or Verizon, whichever it is you're using,on to a windows machine  and load the settings you want into the modem from there. Once they are loaded in, they stay the same until you change them back with the same application. For instance, I set mine up at home to not roam, and use only Sprint's towers. Those settings stay loaded in the modem, and as far as I know, there is no way of altering it with any version of Linux. AT&T and T-Mobile's GSM modems can be set with a communication terminal and some AT commands, but as far as I know, you can't do that with a CDMA modem.

---

### Post by suomalainen on 2010-09-19
waynefoutz,

We can think of W-CDMA as the broadband 3G GSM technology.

2G is the GPRS and slower technology.

The Saunalahti software does allow 3G only under windows XP. but that does not set the stick permanently with this setting. So in Linux it will always roam over to 2G and the connection disconnects and re-boot modem necessary.

---

### Post by waynefoutz on 2010-09-19
> **suomalainen said:**
> waynefoutz,

We can think of W-CDMA as the broadband 3G GSM technology.

2G is the GPRS and slower technology.

The Saunalahti software does allow 3G only under windows XP. but that does not set the stick permanently with this setting. So in Linux it will always roam over to 2G and the connection disconnects and re-boot modem necessary.

If your windows software can lock it to "EVDO only" it should stay with the stick after you pull it out. That's been my experience.

---

