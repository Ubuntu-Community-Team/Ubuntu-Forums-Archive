---
title: "Debian equivalent of /boot/grub/menu.lst????"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by kansasnoob on 2009-02-15
Brief explanation. I'm preparing to install Debian Lenny for a friend in a dual boot with Ubuntu 8.04.2 LTS. I've tried the Lenny live CD on his machine and have burned and tested the net-install CD, and have his machine hooked up to my DSL (no router, so I can only run his machine or mine - no biggy!)

Anyway I have the drive partitioned to use the manual install option installing Debian Lenny, but I don't know what to expect from Debian's GRUB. It may (or may not) detect the Ubuntu install and "auto-magically" add Ubuntu to Debian's GRUB. I dunno.

I just know that preparation is always a good thing. For instance I've sometimes found Linux Mint 6's gfxgrub to screw up detecting all OS's in a multi-boot so I'll just revert to Ubuntu's GRUB and add the new Mint entry to that menu list.

So here's the question: In Ubuntu or Mint I run:

```
cat /boot/grub/menu.lst
```

To read the menu list, and of course I'd use "sudo gedit" instead of "cat" if I were going to edit the menu list. Debian seems only slightly different regarding commands - ie: su makes you root and then you run most commands in a similar manner as Ubuntu - actually more like Mepis.

Anyway, if the Debian install results in a nice dual-boot GRUB screen that's great! I'm done! I have no intention of doing anymore with Lenny! The owner knows that's in his hands!

OTOH, if Lenny does **not** recognize the existing Ubuntu OS I plan on restoring GRUB to Ubuntu and simply adding Lenny to Ubuntu's menu list. I just want to know how to access and/or edit Debian's menu list.

As an example, I recently installed Mint 6 on a machine w/Ubuntu. Mint's gfxboot did not "auto-detect" the previous OS's which were win XP, Ubuntu 8.04, and Ubuntu 8.10. It only recognized XP! (Ubuntu seems to be the best at "auto-magically" detecting ALL OS's)

Since Ubuntu 8.10 was the last previous OS installed I simply copied the Mint 6 boot lines:

> title        Linux Mint 6, kernel 2.6.27-7-generic
root        (hd0,7)
kernel        /boot/vmlinuz-2.6.27-7-generic root=/dev/sda8 ro quiet splash
initrd        /boot/initrd.img-2.6.27-7-generic

title        Linux Mint 6, kernel 2.6.27-7-generic (recovery mode)
root        (hd0,7)
kernel        /boot/vmlinuz-2.6.27-7-generic root=/dev/sda8 ro single
initrd        /boot/initrd.img-2.6.27-7-generic


To the very end of Ubuntu 8.10's menu list after restoring grub's "stage1" to 8.10. (I did add "#manually edited" to the front of each just so I'd know months from now what I did.) 

I hope to be able to do the same with Lenny if needed but just want to know how to access Lenny's menu list??????????????

Sorry if I made this too confusing:)

I've spent a couple of dizzying hours of searching Debian's man pages and I decided to just ask here! Best to be prepared, eh?

---

### Post by ajgreeny on 2009-02-15
As far as I'm aware debian still has the same /boot/grub/menu.lst file as ubuntu, so you should be able to add the stanzas for debian in that, to the ubuntu menu.lst and boot debian from that.  Be warned, however, that it may not work directly the other way round, as ubuntu 8.10 has a new version of grub, and the second line of the ubuntu stanzas no longer says **root        (hd0,7)** or similar, but has a new format which I can't now remember, but which certainly is not acceptable to older grub versions, even that in ubuntu 8.04.  I had to change the format of that line back to the old style, when I copied it, in order to be able to boot 8.10 from the 8.04 grub.

I hope that makes sense to you, and you find it helpful.  The main point is simply that debian appears to use a /boot/grub/menu.lst file just like ubuntu.

---

### Post by kansasnoob on 2009-02-15
> **ajgreeny said:**
> As far as I'm aware debian still has the same /boot/grub/menu.lst file as ubuntu, so you should be able to add the stanzas for debian in that, to the ubuntu menu.lst and boot debian from that.  Be warned, however, that it may not work directly the other way round, as ubuntu 8.10 has a new version of grub, and the second line of the ubuntu stanzas no longer says **root        (hd0,7)** or similar, but has a new format which I can't now remember, but which certainly is not acceptable to older grub versions, even that in ubuntu 8.04.  I had to change the format of that line back to the old style, when I copied it, in order to be able to boot 8.10 from the 8.04 grub.

I hope that makes sense to you, and you find it helpful.  The main point is simply that debian appears to use a /boot/grub/menu.lst file just like ubuntu.

Thank you, as soon as I shower I'm just going to go for it and see what happens. Another venture into the unknown!

I always create a full back-up on an external drive using Partimage anyway so the worst thing that will happen is I'll hand the box back as it was!

Just FYI, this is one of my son's friends and they wanted to borrow one of my USB hard drives to try this themselves.

That is always a NO! No one uses my drives but me! To me that's as bad as asking to borrow a gun!

---

### Post by gn2 on 2009-02-15
> **kansasnoob said:**
> ~ and of course I'd use "sudo gedit" instead of "cat" if I were going to edit the menu list. ~

Better make that "gksudo gedit" as gedit is a graphical app. ;)

[https://help.ubuntu.com/community/RootSudo#Graphical%20sudo](https://help.ubuntu.com/community/RootSudo#Graphical%20sudo)

---

