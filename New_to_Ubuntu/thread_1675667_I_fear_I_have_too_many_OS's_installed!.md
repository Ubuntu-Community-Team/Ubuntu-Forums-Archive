---
title: "I fear I have too many OS's installed!"
date: 2011-01-25
forum: New to Ubuntu
---

### Post by Ranger_Joe on 2011-01-25
Hello All,
I have too many operating systems installed and I only need one. I am currently running Ubuntu 10.10. My computer still has Windows 7 and I have one or two more versions of Ubuntu installed. 

I'm pretty sure all of these have their own partition. Attached is a picture of my GRUB at startup. I'm pretty sure I need to delete everything except the highlighted OS.

Please help me do this. Thanks!

---

### Post by Quackers on 2011-01-25
Your first 6 grub menu entries are for the same operating system (just different kernels).
You can do everything you want to do from gparted in the live cd desktop by deleting partitions. Obviously not the one for your current 10.10!
Please be aware that you may also delete the Windows recovery partition, and unless you have already made the recovery dvd's you will have no way to go back to Windows! You should also make a Windows repair disc before you delete Windows.

---

### Post by Ranger_Joe on 2011-05-03
I'm getting ready to install 11.04 tonight. Can I just delete all these partitions with that disk by doing a clean install?

Also, I have absolutely no desire to ever use Windows again... ever. So... I'm good.

---

### Post by spiky001 on 2011-05-03
You can install ubuntu as an only os if you want it will clear all the kernels It will wipe both windows as well. Why not install with a seperate home patition as well

---

### Post by Ranger_Joe on 2011-05-03
What do you mean? Dual boot with windows?

---

### Post by Bigbluecat on 2011-05-03
They are not partitions - just kernel images as updates come in (files if you like). No need for GParted.

You can find a way to make grub only show 1 or 2. I used to know how to do this with Grub 1 but I would need to research Grub 2. 

I used to have Grub set to show 2 entries. That way if an upgrade caused problems I would always have the previous version available from the Grub menu.

Don't worry too much about them. They are not taking up much space. Have a search for Grub 2 configuration and see if you can find a way to limit it to two entries. Sorry I don't have this knowledge at my fingertips at the moment.

---

### Post by Ranger_Joe on 2011-05-03
So basically it's purely aesthetic? You can just somehow get GRUB to show like 2 list items?

I'll research it but does anybody else know how to do this?

---

### Post by Dondermans on 2011-05-03
I think this thread contains the information you are looking for:

[http://ubuntuforums.org/showthread.php?p=10340183#post10340183](http://ubuntuforums.org/showthread.php?p=10340183#post10340183)

---

### Post by Anonymous is Incognito on 2011-05-03
There are *two* different things happening here.

[LIST]
[*]You see all of the Ubuntu entries? Those are entries for older kernels. When you update your system new kernels may get installed. The old ones remain in place, in case something goes wrong you can use your older kernel.

These are not seperate OSs, see them like a revert option.

See [this HTG post]("http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/") for more information.


[*]To remove Windows (like you wanted), you'll need to remove the Windows partitions. You can using a tool like [FONT="Courier New"]GParted, fdisk[/FONT] etc.

Just make sure you have backed up anything you want to back up. Removing these partitions will cause you to loose the data on it.
[/LIST]

---

### Post by Retlol on 2011-05-03
> **Ranger_Joe said:**
> So basically it's purely aesthetic? You can just somehow get GRUB to show like 2 list items?

I'll research it but does anybody else know how to do this?

Instead of hiding them, remove them. They won't show up in grub and you'll get rid of unneeded kernels/disk space.

---

