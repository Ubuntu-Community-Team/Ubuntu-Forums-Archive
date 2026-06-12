---
title: "HELP!!!!! My Grub2 is broken!!!!!!!!!"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by LGN on 2009-12-19
I was using GParted on the Ubuntu Live CD to make my Ubuntu Paetition bigger, Noe grub2 won't work, and I can't get into Ubuntu 9.10 OR Windows XP MCE 2005

I installed Ubuntu 9.10 about two weeks ago, an MCE 2005 came with the computer (two years ago)

Ubuntu 9.10 is on /dev/sda5 (part f an extended partiion, /dev/sda4, along with the swap partition))

I need a guide that tells me EXACTLY what to do to recover my grub

I can use the Live CD, so I can use the termenal if I have to.

PLEASE HELP ME!!!!!!!!!!!!!!!!!!

---

### Post by drs305 on 2009-12-19
Take a look at the Grub 2 community doc:
[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode]("https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode")

The CLI and Rescue section includes help on editing an existing menu, booting from the Grub 2 command and rescue prompts, and reinstalling from the LiveCD (if necessary).

You might need to check the UUIDs (sudo blkid) and also ensure your boot partition hasn't changed (sda5).

---

### Post by LGN on 2009-12-19
Wow, I didn't expect a reply that fast!

I'll check that out, thanks.

What I did was resize a fat32 partition to make it smaller and made the extended partition bigger so I could make ubuntu (sda5) bigger so I could store more.

---

### Post by drs305 on 2009-12-19
> **LGN said:**
> Wow, I didn't expect a reply that fast!

Welcome to the Ubuntu forums. I didn't notice it was your first post.

Some of the instructions can be a bit overwhelming, so just take it step by step and post back if you have questions about the guide.

---

### Post by LGN on 2009-12-19
Yah, Im new, bu I have read many posts about multiple topics because I was interested.

Recovering grub via rescue mode has too many confusing steps, so I think I will reinstall from a live cd,

thanks for the support,
Zach

---

### Post by garyed on 2009-12-19
Try this:
Boot from the 9.10 live CD, open a terminal & do:
```
sudo fdisk -l
```
Find the Ubuntu 9.10 partition - ID # should be 83
Lets say it is /dev/sda5 - then do:
```
sudo mount /dev/sda5 /mnt
```
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

then reboot, take out the CD  & hopefully you'll get a grub menu to get you back into Ubuntu. Oce there get to a terminal & do:
```
sudo update-grub
```

Good luck

---

### Post by LGN on 2009-12-19
I'll try it.

Step by step
-started live cd
-splash screen
-I see mouse
-cool login noise
-desktop
-why doe ubuntu hate my screen resolution without drivers
-terminal
-"installation finished, No error reported.
This is the contents of the device map /mbr/ /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script 'grub-install'.

(hd0)    /dev/sda"
-rebooting
-and
-...
-GRUB2!!!!!

Thank you SOOOOOO much!!!!!!

And how do u change a post prefix to solved?

---

### Post by drs305 on 2009-12-19
> **LGN said:**
> 
And how do u change a post prefix to solved?


In the Thread Tools link at the top right of the first post. It's reversible as well.

---

