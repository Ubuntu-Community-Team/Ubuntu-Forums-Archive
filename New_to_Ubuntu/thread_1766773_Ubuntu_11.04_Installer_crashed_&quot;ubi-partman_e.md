---
title: "Ubuntu 11.04 Installer crashed &quot;ubi-partman exit code 10&quot;"
date: 2011-05-24
forum: New to Ubuntu
---

### Post by swarup on 2011-05-24
Hello, 
I am trying to install Ubuntu 11.04 on a friend's computer-- a Dell Dimension E520 Desktop. I am using 11.04 386 desktop version. The first time I tried to install, it booted up to the Ubuntu desktop and then gave the error report that "Ubiquity failed". And the second and subsequent times I have tried, it actually starts installing, copying files etc, but then gives the error "ubi-partman failed with exit code 10". 

So what do I need to do to get this 11.04 to install properly?

Thank you

---

### Post by swarup on 2011-05-24
Well, I've tried to install it around six or seven times. It is no longer giving the "ubi-partman" error message. It just says there was an error in downloading the files from the cd into the harddrive, and suggests that the cd/DVD drive may be bad or the cd may be bad. I know the drive is perfectly fine. Guess I'll try downloading another copy of the software. But googling around, it seems like ALOT of people are having trouble getting 11.04 installed. And that is surprising, given that this was supposed to be THE user friendly version, made especially for attracting new users.

---

### Post by wildmanne39 on 2011-05-25
> **swarup said:**
> Well, I've tried to install it around six or seven times. It is no longer giving the "ubi-partman" error message. It just says there was an error in downloading the files from the cd into the harddrive, and suggests that the cd/DVD drive may be bad or the cd may be bad. I know the drive is perfectly fine. Guess I'll try downloading another copy of the software. But googling around, it seems like ALOT of people are having trouble getting 11.04 installed. And that is surprising, given that this was supposed to be THE user friendly version, made especially for attracting new users.
Hi, I had that problem trying to upgrade, I had to do a clean install.

---

### Post by swarup on 2011-05-25
I am doing a clean install. I have not tried even once to do it via upgrade. I deleted all the linux partitions, and have simple unallocated space where I want 11.04 to be installed. I have again this morning downloaded the iso, burned it, and tried to install. Again, after selecting to install "side-by-side the current OS" (Windows is also on this computer), it starts installing and after a couple minutes gives the same error I have gotten ten times by now: The installer encountered an error copying files to the hard disk". The message goes on to suggest the cd/dvd drive may be bad, or the disk may be bad. But I know neither is the case. If anyone has any suggestions, please let me know soon. Otherwise I'll just have to install 10.10.

---

### Post by verymadpip on 2011-05-25
Has anyone checked the MD5 sum of the ISOs to make sure the downloaded file's not been corrupted?

I had a similar error installing Lubuntu on an older machine which I resolved by using the alternate (text based) installer.

I know that's not much help, it's all I've got for now I'm afraid.

---

### Post by swarup on 2011-05-25
Still, that's a good suggestion. In the future, I'll try and remember to try that if I get stuck on an install. For now, I've gone ahead and installed 10.10-- which was itself not without various problems. I eventually got it installed with help from the support forum, but it seems that the new installer, Ubiquity, still has a lot of bugs. Personally, I liked the old installer-- worked great. I'll sacrifice the graphics any time, for something that works. "If it ain't broke, don't fix it". :)

---

### Post by axelsvag on 2011-06-01
I have had exactly the same problem with all 11.04 based distributions. At least when I use the usb method and make the "usb startdisk" tool inside the Ubuntu system/adm menu. What fixed everything for me was to increase the size used by the installation. There is a little bar at the bottom of the menu that default says 128Mb but when I increase this to e.g. 500 mb everything installs nicely.

---

### Post by nanonils on 2011-06-12
Worked for me only after updating the live OS after booting from the installation USB. Whatever bug the installer had in April 28 (that's the 11.04 64bit available right now) it seems to disappear after the update.

---

