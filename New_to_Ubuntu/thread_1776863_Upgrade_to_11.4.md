---
title: "Upgrade to 11.4"
date: 2011-06-06
forum: New to Ubuntu
---

### Post by fallenangel3787 on 2011-06-06
Hello. So I have been running 10.10 for a while now and I decided to upgrade to 11.4. Since I upgraded it has been painfully laggy. As I type its having trouble keeping up with my typing. Switching between windows is a no no and trying to browse menu items is also useless. 100 times worse than trying to use windows before its fully booted.

HELP!!!!!

what could be causing this. What do you need to know about the laptop to be able to help me sort it ? PLEASE HELP!!!!

---

### Post by LowSky on 2011-06-06
Hi, Could you give your computer specs.

Are you using Unity or classic gnome?

Have you made any other changes, for example the use of compiz?

---

### Post by fallenangel3787 on 2011-06-06
Thanks man :D

Specs: i7-2630QM  2.00GHz, AMD Radeon HD 6570M 1GB, ****8GB DDR3.

Its a Lenovo Ideapad Y560p in case you need to look something else up.

Nothing else had changed. I kept my install of 10.10 pretty stock. Few applications installed and some drivers for the display. Thats about it. 

Using Classic, Tried Unity for a bit but it wasn't great :P no offense to them that like it but its AWFUL if you ask me haha. Maybe one day I'll get used to it :P 

Just rebooted and selected to boot "an older version" or whatever it is on GRUB and selected the only other version there (guessing what i used for 10.10) and its much smoother with it. so does that mean its something to do with that ?? 

System Monitor says 
"Ubuntu
 Release 11.04 (natty)
 Kernel Linux 2.6.35-28-generic-pae 
 GNOME 2.32.1"

Forgive my noobness when it comes to linux :( we all have to start some place ? right ?

---

### Post by fallenangel3787 on 2011-06-07
*bump*

---

### Post by wildmanne39 on 2011-06-07
> **fallenangel3787 said:**
> Thanks man :D

Specs: i7-2630QM  2.00GHz, AMD Radeon HD 6570M 1GB, ****8GB DDR3.

Its a Lenovo Ideapad Y560p in case you need to look something else up.

Nothing else had changed. I kept my install of 10.10 pretty stock. Few applications installed and some drivers for the display. Thats about it. 

Using Classic, Tried Unity for a bit but it wasn't great :P no offense to them that like it but its AWFUL if you ask me haha. Maybe one day I'll get used to it :P 

Just rebooted and selected to boot "an older version" or whatever it is on GRUB and selected the only other version there (guessing what i used for 10.10) and its much smoother with it. so does that mean its something to do with that ?? 

System Monitor says 
"Ubuntu
 Release 11.04 (natty)
 Kernel Linux 2.6.35-28-generic-pae 
 GNOME 2.32.1"

Forgive my noobness when it comes to linux :( we all have to start some place ? right ?Hi, have you installed your driver for your video card, most of the problems come from video cards with lagging I had that with the recommend driver with my nvidia card and I switched to the old driver and it works perfect now and as for 2 months.

---

### Post by fallenangel3787 on 2011-06-08
Hey. Thanks for the reply. I did have the proprietary drivers installed before I upgraded. (from the "Additional Drivers" under "System" menu).. They were still installed after the upgrade as well (I just checked) but I removed them and just reinstalled them to see if it will make a difference. Its asking me to restart my computer now so i will restart it and report back.

It does seem like it is something to do with display cos its lagging out and being slow to display things. Its not having problems processing things since the CPU usage isn't anywhere near maxing out.

Again Thanks for you help.

EDIT :- OK so I just restarted and it doesn't seem to have made much of a difference if any at all. I checked to make sure the drivers installed ok and that they are active which they are, everything is installed fine also. 

Anyone have any other ideas ? kind of frustrating since I need to use this laptop for work. 

Is there ab easy way to roll back to 10.10 ?

---

### Post by alphacrucis2 on 2011-06-08
> **fallenangel3787 said:**
> Hey. Thanks for the reply. I did have the proprietary drivers installed before I upgraded. (from the "Additional Drivers" under "System" menu).. They were still installed after the upgrade as well (I just checked) but I removed them and just reinstalled them to see if it will make a difference. Its asking me to restart my computer now so i will restart it and report back.

It does seem like it is something to do with display cos its lagging out and being slow to display things. Its not having problems processing things since the CPU usage isn't anywhere near maxing out.

Again Thanks for you help.

EDIT :- OK so I just restarted and it doesn't seem to have made much of a difference if any at all. I checked to make sure the drivers installed ok and that they are active which they are, everything is installed fine also. 

Anyone have any other ideas ? kind of frustrating since I need to use this laptop for work. 

Is there ab easy way to roll back to 10.10 ?

It might be worth trying the newer driver direct from AMD. I think the fglrx driver in the Natty repos is a pre release version. The official Cat 11.5 from AMD might fix a few issues. You can download the 32 or 64 bit Linux driver direct from the AMD website. Once you have it downloaded. First purge the existing fglrx, then install the new once via the buildpkg method as described in Ubuntu binary driver Howto/ATI doc.

---

### Post by fallenangel3787 on 2011-06-08
Thanks for your help. I will try that. I hadn't thought of that. Just hoped that the Additional Drivers bit on Ubuntu was the latest! Will let you know if it works

---

### Post by ppv on 2011-06-08
Only highlighting out but why are you using a pae kernel. Is it that you are using 32bit Ubuntu and since you have 8GB ram. The processor looks to be 64 bit so you could use 64 bit Ubuntu and non-pae kernel and still use all of your ram. Would not suggest doing any of the above things until you know that it is the issue and you have taken a backup of your files.

---

