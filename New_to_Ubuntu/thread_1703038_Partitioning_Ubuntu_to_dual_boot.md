---
title: "Partitioning Ubuntu to dual boot"
date: 2011-03-08
forum: New to Ubuntu
---

### Post by MDW6 on 2011-03-08
Ubuntu is my main operating system.  I need to install Windows.  I would like to dual boot rather than use Virtual Box.  Can I do this?  How?

---

### Post by maqtanim on 2011-03-08
You can do that with Gparted of live disk. 

By the way Welcome to the forum!! :D

---

### Post by ikt on 2011-03-08
> **MDW6 said:**
> Ubuntu is my main operating system.  I need to install Windows.  I would like to dual boot rather than use Virtual Box.  Can I do this?  How?

There is a good guide here:

[https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu](https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu)

Make sure you backup everything first!

---

### Post by oldfred on 2011-03-08
You need to have a primary partition formated to NTFS with the boot flag for the windows installer to see it. Otherwise you have to have a blank disk. Windows does not see the Linux partitions and gets confused otherwise.

---

### Post by teward on 2011-03-08
Note that when you install Windows now (since you've already got Linux installed), it'll overwrite the bootloader, so you'll need to restore GRUB afterwards.

---

### Post by MDW6 on 2011-03-08
I appreciate all the responses that came so quickly.  I wish I could understand what you are talking about.  I don't know what a live disc is, and the tutorials assume far too much knowledge on my part.  This is a little frustrating to say the least.

Can I reformat the disc and start from scratch?  If so, with which OS should I begin?  

Maybe I should explain why I want to dual boot instead of using Virtual Box.  In VB, I could not use the usb ports, and the Windows I was using inside VB would not fill the monitor even though it was in full-screen mode.  If that problem could be solved, then dual booting can be avoided.

---

### Post by Hakunka-Matata on 2011-03-08
> **MDW6 said:**
> I appreciate all the responses that came so quickly.  I wish I could understand what you are talking about.  I don't know what a [COLOR="Red"]live disc[/COLOR] is, and the tutorials assume far too much knowledge on my part.  This is a little frustrating to say the least.

Can I reformat the disc and start from scratch?  If so, with which OS should I begin?  

Maybe I should explain why I want to dual boot instead of using Virtual Box.  In VB, I could not use the usb ports, and the Windows I was using inside VB would not fill the monitor even though it was in full-screen mode.  If that problem could be solved, then dual booting can be avoided.

The live disc, or LiveCD is the Ubuntu Install CD.  It's what you boot with to get started.  You can also use it to boot with and fix problems on your hard drive, if the hard drive has problems and won't boot.

Yes, you can reformat your disc first.  And partition it as well before you start your installs.  Boot with the LiveCD, and use GParted disc partitioner to prepare the disc.  Installing Windows first is easiest, as Ubuntu will install Grub2 when you install it, which provides you with the dual-boot menu.

---

### Post by Hakunka-Matata on 2011-03-08
> **oldfred said:**
> [COLOR="Red"]You need to have a primary partition formated to NTFS with the boot flag for the windows installer to see it.[/COLOR] Otherwise you have to have a blank disk. Windows does not see the Linux partitions and gets confused otherwise.

If you choose to install Windows first, and you prepare the disc beforehand, remember what oldfred says in the quoted post.

---

### Post by bk60544 on 2011-03-09
so **how** do you "restore GRUB"?

---

### Post by beew on 2011-03-09
Check out post #7.
[URL="http://ubuntuforums.org/showthread.php?t=1699552"]http://ubuntuforums.org/showthread.php?t=1699552
[/URL]

---

### Post by oldfred on 2011-03-09
A couple of more links in case one makes more sense to you.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by MDW6 on 2011-03-11
> **oldfred said:**
> A couple of more links in case one makes more sense to you.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Thank you all for your help.  We installed Windows first and made a partition in which we could install Ubuntu.  I have a cd with Ubuntu and it automatically made itself the default OS.  Now I can have the best of both worlds!

---

### Post by Hakunka-Matata on 2011-03-11
What a short sweet trip that was.  Thanks for reporting how it went!

---

