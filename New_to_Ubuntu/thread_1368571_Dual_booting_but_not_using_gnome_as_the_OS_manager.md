---
title: "Dual booting but not using gnome as the OS manager?"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by Pascal11110 on 2009-12-30
Is it possible to dual-boot Vista and Ubuntu but not use gnome as the OS manager on startup? Or as an alternative, can I change the default OS boot list and time it displays? I just hate having it automatically boot to linux after like 10 seconds because if I need to get into windows I always accidentally boot to Linux at least once because I am not paying attention. I am a gamer so I use my windows partition more than my Ubuntu partition (it just takes less time/screwing around) so it would just be nice if it just sat at the the OS options list indefinitely or I could set Windows as the default.

---

### Post by Merk42 on 2009-12-30
You mean GRUB not GNOME, but yes.
You can set it up to use the Windows bootloader or change the options in GRUB (this is the easier option).

How you can GRUB depends on what version of Ubuntu you're running.  As of 9.10 they switched to GRUB 2 which is configured far differently than legacy GRUB.

---

### Post by Pascal11110 on 2009-12-30
Lol, ya I did mean grub. Well I'm probably going to be using 9.1, and I'll probably switch to the new version in february (which I assume is going to use grub 2) Could you direct me to a thread on configuring to the boot options for grub 2? I'll check through the forums myself but if you know a good one I'd be grateful.

---

### Post by Pascal11110 on 2009-12-30
And I am quite a bit more versed with Windows than Ubuntu so using the Windows boot manager might be an option for me, I just thought that the windows boot manager would throw up if I tried to make Ubuntu one of its boot options. I'll check around for that as well.

---

### Post by Merk42 on 2009-12-30
February? The next version of Ubuntu, Lucid Lynx, is the end of April.
There's this right now for GRUB2, I know there's a nice long thread in Ubuntu forums about it too
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

EDIT: Here [GRUB 2 Guide](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by Geoff918 on 2009-12-30
Use Wubi.

[http://wubi-installer.org/](http://wubi-installer.org/)

**EDIT**

By the way, changing boot menus in Vista is not as easy as prior versions of Windows. There are guides around if that's the version you're running. It can, of course, be done. GRUB is pretty easy once you're used to it. GRUB2, I'm still working on figuring out myself. It's less than intuitive. You have to make more non-standard-seeming changes to it.

---

### Post by Merk42 on 2009-12-31
WUBI? Jeez then if Pascall1110 wanted sole Ubuntu he/she would have to reinstall both!

Just use the second link I posted, pretty thorough guide.
Actually if you have no experience in GRUB1, then better, then you don't have to 'unlearn' stuff for GRUB2

---

### Post by SkyNet2029 on 2009-12-31
You just need to edit the grub configuration.
this is located in /boot/grub/menu.list
 
so,,,
 
```
sudo gedit /boot/grub/menu.list
```
 
change the line that says (timeout)
 
to the number of seconds you want it to wait before booting automaticallt into linux.
 
While you CAN use the windows bootloader, grub is the preferred method. Both grub (legacy) and Grub2 will create an entry for your windows installation.
 
Install windows, then the linux.

---

### Post by Merk42 on 2009-12-31
> **SkyNet2029 said:**
> You just need to edit the grub configuration.
this is located in /boot/grub/menu.list
 
so,,,
 
```
sudo gedit /boot/grub/menu.list
```
 
change the line that says (timeout)
 
to the number of seconds you want it to wait before booting automaticallt into linux.
 
While you CAN use the windows bootloader, grub is the preferred method. Both grub (legacy) and Grub2 will create an entry for your windows installation.
 
Install windows, then the linux.
EXCEPT the whole editing of menu.list is not what GRUB2 uses...
So a clean installation of 9.10 won't have /boot/grub/menu.list

---

### Post by Pascal11110 on 2009-12-31
Ya, I read that in the link that you provided, which was very helpful. Just for the record though, I have dual booted several computers so I do know the basics, but I definitely don't know enough to hurt my learning curve with grub 2. I'll have to experiment a bit on my test machine before I try it out on my laptop.

---

### Post by Paqman on 2009-12-31
You can install startupmanager. It'll give you a nice easy way to switch the default OS in Grub2. It's not 100% compatible with Grub2 yet, but it can handle this simple job ok.

---

### Post by Pascal11110 on 2009-12-31
And if anyone else checks out this thread I found a great thread on grub 2: [http://ubuntuforums.org/showthread.php?p=8191211]("http://ubuntuforums.org/showthread.php?p=8191211")

---

