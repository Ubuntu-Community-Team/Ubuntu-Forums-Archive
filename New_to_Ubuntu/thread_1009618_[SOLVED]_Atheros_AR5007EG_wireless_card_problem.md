---
title: "[SOLVED] Atheros AR5007EG wireless card problem"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by jfloydb on 2008-12-12
Acer Aspire One
Model number: ZG5

Intell(R) Atom(TM)
CPU N270 @ 1.60GHz
1.60 GHz, 0.98 GB of RAM

Atheros AR5007EG Wireless Network Adapter

MS Windows XP
Home Edition
Version 2002
Service Pack 3

Above are the specs for my new computer. I want to run UBUNTU
as a WUBI or as a dual boot, AND I WANT WIRELESS INTERNET 
ACCESS.  I did try Hardy Heron, but, of course, my wireless
network adaptor card never showed up. I tried several things,
but no luck. (The Eithernet Cable works, however.)

Does anybody else on this forum own this computer?  Has 
anybody figured out exactly how to gain wifi access with this
particular computer?  Would UBUNTU 8.10 do any better than 
8.04?  I need some instruction that an Absolute Beginner can
understand and apply...

Thanks in advance

---

### Post by nhasian on 2008-12-12
yes use Ubuntu 8.10 and follow my instructions here for wifi:

[http://ubuntuforums.org/showpost.php?p=6059353&postcount=15](http://ubuntuforums.org/showpost.php?p=6059353&postcount=15)

---

### Post by rlogan on 2008-12-13
Yeah I have the same issue with our laptop with the 5007/242x chipset. Its a pain but we have got around it with the following link :-

[http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/)

I found this link via the Unofficial Ubuntu Guide at :-

[http://ubuntuguide.org/wiki/Ubuntu:Intrepid](http://ubuntuguide.org/wiki/Ubuntu:Intrepid)

The main hassle with this is that each time there is a kernal update you need to redo the whole process.

Hope this helps

Cheers

Richard

---

### Post by Hellno on 2008-12-15
Hi

I couldn't help to ask, i've done every step posted here and in another threats where they advised me to blacklist something, but my wifi is still not working.. plus, when i install the linux-backports-modules-intrepid or any other new application, generally, it returns an error in the command line...

Errors were encountered while processing:
 linux-image-2.6.27-7-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

can somebody help me to get some rest tonight?:S

---

### Post by rlogan on 2008-12-16
Thats strange, sounds like something hasn't installed quite right.

Try this :-

sudo apt-get -f install

sudo apt-get update

see if that fixes the update issue.

The procedure I linked too before worked perfectly for me and it also says that when he blacklisted the driver it didn't work. 

Heres the link:- 

[http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/)


Hope it helps

Cheers

Richard

---

### Post by jfloydb on 2009-04-26
The answer is: upgrade to 9.04 for the acer Aspire One... Thanks everyone...

---

### Post by rlogan on 2009-04-27
I 2nd that !!!

Upgrade to Jaunty and it works out of the box !!!!

Likewise the last upgrade to I think it was 2.6.27-11 on Intrepid it also worked !!!

Wonderful no more recompiling !!!!

Cheers all

Richard

---

### Post by cmcanulty on 2009-09-26
I have exact same machine running Ubuntu 9.04, but fix didn't work at all. It connects OK in windows, help please

---

