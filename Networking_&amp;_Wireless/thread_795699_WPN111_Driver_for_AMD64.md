---
title: "WPN111 Driver for AMD64"
date: 2008-05-15
forum: Networking &amp; Wireless
---

### Post by Richard_Au_2006 on 2008-05-15
After spending very many hours I finally found why my WPN111 USB adapter (V-2.0) does not work with Ubuntu on my AMD64 machine: because the native driver that came with this adapter is for 32 bit machine.  Although Netgear states that it does support Vista 64 bit you need to install that driver from the CD on a Vista 64 bit operating system.  Installing this driver on XP 32 machine simply installed the 32 bit driver.  The CD has ‘exe’ files which I could not expand under Linux.
My question: Is there any substitute driver that I can use with this adapter for AMD64 (chipset is AR5523).
I already tried [www.atheros.cz](www.atheros.cz) without success.  When I installed the driver from there (AR5005UG) ndiswrapper reported driver is present but hardware is not present.

Thanks,
Richard

---

### Post by Rips on 2010-12-19
Bump. Same problem. Have Windows 7 running wpn111 just fine. Ubuntu 10.10 64bit doesnt like it at all.

I have the files in win7 but have no idea which they are. Win7 reports the file its using as wpn111vx.sys but have no idea where the inf or other files are.

Any help would be appreciated. I miss my dual boot sys.

---

### Post by sepatel on 2011-08-06
Looks like the win7 drivers are 32 bit drivers. I haven't found a way to install the atheros drivers successfully yet but the problem with netgear is that there drivers are only 32bit.

---

