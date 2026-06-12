---
title: "MD5 and 701 issues"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by KyleRickards on 2009-09-11
Hi all

Having issues putting any ubuntu variation onto my Asus 701 EEE. Have tried USB and disk approaches with no joy, can load into live environment but then get an i/o error when trying to permanently install. (I did use Gparted in Live to wipe my internal HDD and make one live partition of 3.7 gig ready for install - could this be an issue?)

That said!  I am downloading various ISOs off the net through either mirror or torrent and when I do an MD5 check, they all come up without matching codes? Surely this can't be right? Am I doing something wrong? I have already wasted several disks this week hence I thought I would check the MD5 code.

Thanks
Kyle

---

### Post by t0p on 2009-09-11
I'm puzzled by your problem, as I've installed ubuntu onto my 701 several times.  I've always used the "live usb" method.  I'm wondering if there's something wrong with your SSD (your "hard drive"), as you have no problem running ubuntu in a live session.  Have you tried installing an OS from an .iso/.img that you *know* is good? ie, reinstalling the OS that came with the EeePC?

To help us help you, please try again to install ubuntu (from a live usb that works fine in live session mode), and make a note of what happens - at what point of installation does it fail, and what is the exact error reported?

As for the MD5sum problem... more weirdness.  *Every* download has MD5 mismatch?

It all sounds to me like hardware problems.

---

### Post by KyleRickards on 2009-09-11
Hi

JUst tried with memory stick, very slow to install but did complete. Upon reboot, permanently reboots itself after Grub loads up. Am now trying with my CD of Ubuntu (which I *know* works!)  Will keep you posted, thanks for the assist on this one. Starting to think the SSD is fried somehow...

Kyle

---

### Post by LewRockwell on 2009-09-11
701:

[https://wiki.edubuntu.org/HardwareSupport/Machines/Netbooks](https://wiki.edubuntu.org/HardwareSupport/Machines/Netbooks)



MD5:

*nix Related:

[http://ubuntuforums.org/showthread.php?t=290339](http://ubuntuforums.org/showthread.php?t=290339)



Windows Related:

[http://download.cnet.com/MD5-SHA-1-Checksum-Utility/3000-2092_4-10911445.html](http://download.cnet.com/MD5-SHA-1-Checksum-Utility/3000-2092_4-10911445.html)

[http://support.microsoft.com/kb/841290](http://support.microsoft.com/kb/841290)



Mac Related:

[http://download.cnet.com/checkSum/3000-2248_4-42637.html](http://download.cnet.com/checkSum/3000-2248_4-42637.html)

[http://discussions.apple.com/message.jspa?messageID=7025577](http://discussions.apple.com/message.jspa?messageID=7025577)


.

---

### Post by LewRockwell on 2009-09-11
> **KyleRickards said:**
> Hi

JUst tried with memory stick, very slow to install but did complete. Upon reboot, permanently reboots itself after Grub loads up. Am now trying with my CD of Ubuntu (which I *know* works!)  Will keep you posted, thanks for the assist on this one. Starting to think the SSD is fried somehow...

Kyle

what happens when you revert to the original out-of-the-box configuration?

.

---

### Post by KyleRickards on 2009-09-11
Won't let me do that, only thing I can get working is Ubuntu so I will live with that for the moment I guess.

---

### Post by KyleRickards on 2009-09-11
Well finally used netbootin and a new downloaded iso on my XP lappy to get an install of eeebuntu working. However, I have no system tray when I am logged in as me, if I switch to guest account, it appears? Have connected using ethernet cable and got all the updates I can which installed. Everything seems to be fine now apart from the tray problem - any help appreciated?

Kyle

---

