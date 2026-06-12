---
title: "Installation Within Windows"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by coover on 2009-04-23
I had 9.04 RC installed "within Windows" on my laptop running Vista SP1. After uninstalling it, I installed 9.04. Installation went well and then the reboot. Vista came up. I was not given a dual-boot choice to boot into Ubuntu. I checked the hard drive and found a 17.2 GB Ubuntu directory so I know the files are there. 

What happened, and how do I get it to dual-boot?

---

### Post by aaronp on 2009-04-23
How did you do the first install, was it inside some sort of virtulisation application or with Wubi?

Was this one a proper install (i.e. boot from the live CD and create a new partition to install it) or a Wubi install? (i.e. put the CD in whilst in Windows and install from there)

---

### Post by coover on 2009-04-23
It was not a virtual installation. It was "within" windows, itself (the 2nd or middle installation choice). No partitioning was done.

---

### Post by Paqman on 2009-04-23
> **coover said:**
> It was not a virtual installation. It was "within" windows, itself (the 2nd or middle installation choice). No partitioning was done.

That's the "Wubi" installer. So to get this straight:
[LIST=1]
[*]You installed 9.04 with Wubi
[*]You uninstalled this. Through the Windows add/remove?
[*]You then reinstalled 9.04. Through Wubi? Or not?
[/LIST]

---

### Post by coover on 2009-04-24
Yes, it was Wubi.exe that I used to install. Installation took about 10 minutes. A reboot was requested and done. There was no dual-boot choice. It booted straight to Vista.

---

### Post by coover on 2009-04-24
I just checked the Vista "Programs and Features" (the equivalent of XPs "Add/Remove") and found a listing for "Ubuntu"

---

### Post by steve101101 on 2009-04-24
it should automatically be added with a wubi install. if you haven't used the ubuntu install i would remove the old one and try to reinstall.

---

### Post by aaronp on 2009-04-24
> **coover said:**
> Yes, it was Wubi.exe that I used to install. Installation took about 10 minutes. A reboot was requested and done. There was no dual-boot choice. It booted straight to Vista.

I'd say uninstall and reinstall and see if you get the boot menu this time. If not, report back and we can start to try to figure out where the boot menu is for you...

---

### Post by coover on 2009-04-24
The old uninstall - reinstall works again. 9.04 is now installed and now is the time to configure, update and make the operating system look like I want it to look. Thanks guys for the advice and the encouragement. It was and is appreciated.:)

---

### Post by aaronp on 2009-04-24
> **coover said:**
> The old uninstall - reinstall works again. 9.04 is now installed and now is the time to configure, update and make the operating system look like I want it to look. Thanks guys for the advice and the encouragement. It was and is appreciated.:)

Awesome, have fun with Jaunty!

---

