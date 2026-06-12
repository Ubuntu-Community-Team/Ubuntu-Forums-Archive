---
title: "Dual Boot"
date: 2010-07-07
forum: New to Ubuntu
---

### Post by berdar on 2010-07-07
I've got two hard drives for my laptop.  One of them has ubuntu on it and the other has windows 7.   I'm guessing that  editing grub will allow me to dual boot.

The problem is I have no idea how to do it.  I've searched here and on google but can't figure it out.

Can anyone help?

Thanks in advance.

---

### Post by jtarin on 2010-07-07
Do you have Grub (which version?) installed to the MBR of the First drive (should be Win7) or or to the / of the second drive (should be Ubuntu).

---

### Post by berdar on 2010-07-07
> **jtarin said:**
> Do you have Grub installed to the MBR of the First drive (should be Win7) or or to the / of the second drive (should be Ubuntu).

grub is on the #1 drive which is Ubuntu



Edit,

what i'm working with is two drives which have the OS installed separately.  I had W7 and decided to try Ubuntu on a second drive, that way I could just change Drives to go back to Windows if i wanted.   The Ubuntu drive is in the #1 drive slot and W7 in the #2.

---

### Post by jtarin on 2010-07-07
If you change drives and make Win 7 number #1 will it boot? Then your Grub/Ubuntu drive is not seen correct?

---

### Post by berdar on 2010-07-07
> **jtarin said:**
> If you change drives and make Win 7 number #1 will it boot? Then your Grub/Ubuntu drive is not seen correct?
That is correct.

---

### Post by jtarin on 2010-07-07
I've dual booted for years and have never liked anything on my MBR of Win drive because it can be problematic. I have always been able to boot Linux with a Live CD etc. One of the best ways I have found to dual boot my Win 7 and any version of Linux,BSD or PowerPC is "[EasyBCD]("http://neosmart.net/forums/showthread.php?t=642")" it's foolproof.Install on your Win 7 , configure it to boot Grub 2 on a Linux partition/drive then make Win 7 your primary drive.
[Case example]("http://neosmart.net/forums/showthread.php?t=6655&highlight=linux+drive")
Use the latest build.....works flawlessly.

---

### Post by oldfred on 2010-07-08
If you have grub2, plug in both drives, set BIOS to boot from Ubuntu drive.

Once in Ubuntu
sudo update-grub

that should find the windows install and on next reboot let you boot windows.

---

### Post by berdar on 2010-07-08
> **oldfred said:**
> If you have grub2, plug in both drives, set BIOS to boot from Ubuntu drive.

Once in Ubuntu
sudo update-grub

that should find the windows install and on next reboot let you boot windows.

Worked Perfectly, Thank you.

---

