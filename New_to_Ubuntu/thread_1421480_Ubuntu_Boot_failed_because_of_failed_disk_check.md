---
title: "Ubuntu Boot failed because of failed disk check"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by seventhsamurai on 2010-03-04
Hi Guys

Had a boot issue with Ubuntu. Thought I'd share how I solved it just in case any other beginners like me have a similar issue.

Basically, due to some power and overheating issues, my laptop shut down improperly and restarted several times, until Ubuntu started a disk check on boot and the check kept failing around 90% mark consistently. There was no way for me to log in normally, because if I skipped the disk check, it would take me to a prompt.

How to fix:

Get out that Ubuntu Live CD that you installed Ubuntu from. If you don't have it, download the iso file of the Ubuntu LIVE CD. Burn it onto a CD.

Pop the CD into your computer and boot off the CD. Select the first option which allows you to run Ubuntu Live off the CD without making changes to your computer.

Ubuntu desktop will load, but its not your desktop, its the live desktop running off the CD. You can think of this as similar to Windows Safe Mode, except, its better and more powerful, and disconnected from your installed file system.

Go to System >> Administration and run Gpart. In Gpart, select your file system partition, mark it for check & repair, and run the utility. It's pretty self-explanatory. Gpart fixes the errors. Just reeboot normally, and you will be good to go.

---

### Post by steve-shinn on 2010-03-04
Doing the same but running "fsck" instaed of gparted would achieve the same effect.

---

### Post by 2uRcJQ34G1 on 2010-03-04
You could also try > sudo e2fsck -f.

---

### Post by philinux on 2010-03-04
I just run fsck from the recovery mode.

---

