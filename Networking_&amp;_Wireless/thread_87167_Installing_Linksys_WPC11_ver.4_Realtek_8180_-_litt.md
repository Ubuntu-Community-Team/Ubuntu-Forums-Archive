---
title: "Installing Linksys WPC11 ver.4/ Realtek 8180 - little help?"
date: 2005-11-07
forum: Networking &amp; Wireless
---

### Post by monomaniacpat on 2005-11-07
Hi there,

I'm trying to install a linksys WPC11 ver. 11 (rt8180 chipset) and having installed ndiswrapper and the relevant driver, linux fails to recognise the card (hardware present? NO.)

I've also used [http://linux-wless.passys.nl/query_part.php?brandname=Linksys&zoek=brandname](http://linux-wless.passys.nl/query_part.php?brandname=Linksys&zoek=brandname), which led me to [http://rtl8180-sa2400.sourceforge.net/](http://rtl8180-sa2400.sourceforge.net/). From there, I d/l rtl8180-sa2400. Once that was downloaded and unpacked, I followed the INSTALL instructions. It told me to MAKE - which gets the following response...

monomaniacpat@ubuntu:~/Desktop/rtl8180-0.21$ make
Makefile:8: /lib/modules/2.6.12-9-386/build/.config: No such file or directory
make: *** No rule to make target `/lib/modules/2.6.12-9-386/build/.config'.  Stop.
 
Ignoring that and continuing I go to ./module_load. This results in the programme not finding the relevant files. Checking the directory I discover that no .ko files exist, so I change the files ending .c to end .ko and try again, which results in:

monomaniacpat@ubuntu:~/Desktop/rtl8180-0.21$ sudo ./module_load
insmod: error inserting 'ieee80211_crypt-r8180.ko': -1 Invalid module format
insmod: error inserting 'ieee80211_crypt_wep-r8180.ko': -1 Invalid module format
insmod: error inserting 'ieee80211-r8180.ko': -1 Invalid module format
insmod: error inserting 'r8180.ko': -1 Invalid module format

What should I do to either get ndiswrapper/ linux to recognise the hardware or make them into VALID module formats?

Thanks in advance,

Mono.

---

### Post by mips on 2005-11-07
From, [http://ubuntuforums.org/showthread.php?p=473858#post473858](http://ubuntuforums.org/showthread.php?p=473858#post473858)

Have a look at [http://ubuntuforums.org/showthread.p...ighlight=WPC11](http://ubuntuforums.org/showthread.p...ighlight=WPC11)
and post5 in this thread [http://ubuntuforums.org/showthread.p...ighlight=WPC11](http://ubuntuforums.org/showthread.p...ighlight=WPC11)

---

### Post by monomaniacpat on 2005-11-07
The last two links are broken... thanks for the first!

---

### Post by monomaniacpat on 2005-11-08
Unfortunately, those didn't help me as Linux is currently unable to detect the card - can anyone tell me why this may be the case?

---

### Post by mips on 2005-11-08
[http://www.ubuntuforums.org/showthread.php?t=71372&highlight=WPC11](http://www.ubuntuforums.org/showthread.php?t=71372&highlight=WPC11)

Acording to this post it might not be in the kernel modules by default. Individual got it to work via ndiswrapper though.

---

### Post by monomaniacpat on 2005-11-09
Thanks for that - the link looks rather promising, but I don't understand what the user did to get his card working - could you tell me?

---

