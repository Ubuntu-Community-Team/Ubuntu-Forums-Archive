---
title: "trouble with s"
date: 2011-08-23
forum: New to Ubuntu
---

### Post by wellie on 2011-08-23
**Re: windows crashed, want to dual install ubuntu but...........** 			
 			 			 		   		 		 		well i downloaded the [ubuntu-11.04-desktop-i386.iso]("http://se.releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.iso")  on another laptop, burned it to a dvd, putted into my broken medion laptop and it cant read the cd/dvd,
 the same warnings came up as before

it cant read because the system32 is missing and/or destroyed and its asking for a installation disc which i dont have

shall i download the alternative iso ?


best reguards:wink:

---

### Post by raja.genupula on 2011-08-23
try to install from USB start up disk , seems like system problem but i am not sure .. to check errors for ISO go to MD5SUM verification , it will declare if any errors are there in ISO

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by dave01945 on 2011-08-23
are you trying to open the disk in windows or boot from it

if windows doesn't work and you want to get rid of it just boot from the cd

put the cd in drive reboot computer then it should boot from the disc if not just change your bios options to boot from cd/dvd before it boots hdd

---

### Post by raja.genupula on 2011-08-23
> **dave01945 said:**
> are you trying to open the disk in windows or boot from it

if windows doesn't work and you want to get rid of it just boot from the cd

put the cd in drive reboot computer then it should boot from the disc if not just change your bios options to boot from cd/dvd before it boots hdd

man i have faced that in my lappy too . its a input/output error . finally i had installed ubuntu with wubi from   windows 2000 os . its not going to allow to install from cd/dvd .

---

### Post by seawolf167 on 2011-08-23
> **wellie said:**
> the same warnings came up as before

it cant read because the system32 is missing and/or destroyed and its asking for a installation disc which i dont have

This is Windows error and is indicating that you are not attempting to boot off the cd, but instead off the Windows partition. It sounds like you will need to either add, or change the order of your boot devices in BIOS.

To do so, hit the required keystroke to enter your BIOS (usually [F2]), then when in there, ensure that booting off your cd/dvd drive is enabled and has a higher priority than your hard drive. Once set, save and exit BIOS and re-attempt to boot off your Ubuntu installation cd.

Optionally, you can hit the required keystroke to give you a boot menu during POST (usually [F11]).

---

### Post by SoFl W on 2011-08-23
Make sure it is booting from the CD, if you get the Windows error it sounds like it is still trying to boot from the hard drive.

---

