---
title: "cant scan using Xsane"
date: 2010-01-25
forum: New to Ubuntu
---

### Post by manny43 on 2010-01-25
Hello friends

I'm running Ubuntu 8.04 LTS and everything works great except when running Xsane Image Scanner which prompts the following message:Failed to open device "v4l:/dev/video0 invalid argument"Any suggestion on how to resolve this issue?Thanks.
HP Photosmart C4680 Print-Scan-Copy.

---

### Post by phidia on 2010-01-26
Make sure you have HPLIP installed on your system-there is also a gui for that HP driver setup app. Once you have that and the gui try to configure the all-in-one with it.

---

### Post by manny43 on 2010-01-26
Yes HPLIP is installed and the weird thing is that i can print with no problems.

---

### Post by Psumi on 2010-01-26
> **manny43 said:**
> Yes HPLIP is installed and the weird thing is that i can print with no problems.

[http://localhost:631](http://localhost:631)

In the Admin area, under your printer, tell us what the Connection/URL for it is

Oh, and try using gksudo xsane from terminal, see if it works.

---

### Post by hyperhelium on 2010-01-26
I had a very similar problem with my scanner although it's of a different brand. I had to install and compile Sane completely since the one in the repos didn't seem to have the model of my scanner. I also had to work with the permissions etc.

But I found a very useful guide on how to install and compile Sane libraries up-to-date and how to modify permissions. I guess this could help. It did the trick for me.

[http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html](http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html)

I hope this helps.

Cheers.

---

### Post by manny43 on 2010-01-26
Device URL hp:/usb/Photosmart_C4600_series?serial=CN96

---

### Post by SoFl W on 2010-01-26
After I upgraded from 9.04 to 9.10 SANE would "crash"  Didn't matter what save option I used or if I previewed or not, after the scan as soon as the bulb returned to the start position on the scanner SANE would close (or crash).

---

### Post by manny43 on 2010-01-26
Heye guys this resolved the problem

HP C4400 SERIES 
SUPPORTED BY HPLIP(requires HPLIP version 2.8.5 or later
went to this site [http://hplip.sourceforge.net/downloads.html](http://hplip.sourceforge.net/downloads.html) and downloaded Automatic Installer
now everything works great.I can scan with no problems.Hope this helps someone else too.THANKS

---

### Post by SoFl W on 2010-01-30
Your answer did not work for my hpscanjet 3500 but it did lead me to find this:
[https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/428476](https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/428476)
which did work.   

Hopefully if someone else is having problems one of our answers will help.

---

