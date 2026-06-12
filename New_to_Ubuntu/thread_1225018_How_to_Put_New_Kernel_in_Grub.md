---
title: "How to Put New Kernel in Grub"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by Hoom@n on 2009-07-28
Hi,
I updated my Ubuntu and a new kernel installed; but, when it asked me too what to do with "menu.lst" accidentally I kept the current menu.lst which I didn't want! Now, how can I change the kernel in grub whith this newer one?
Thanks.

---

### Post by Elfy on 2009-07-28
Try ```
sudo update-grub
```

---

### Post by Hoom@n on 2009-07-28
> **forestpixie said:**
> Try ```
sudo update-grub
```
I used "sudo update-grub" and I got this:
```
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.28-13-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done
```
But after restarting, there was still the old version (2.6.28-11) in list without adding any new thing.
What to do?

---

### Post by Elfy on 2009-07-28
Can you run this and post the results please.

```
ls /boot
```

---

### Post by Hoom@n on 2009-07-29
I updated Ubuntu again, and a new kernel installed again; this time I chose "maintainer version" (or probably it was something similar to it). Windows removed from my menu.lst and two new kernels(one gotten today and the other yesterday!) added. I added windows manually(from a backup from the fist menu.lst) and put # before two old kernels and changed the place of Windows and Linux kernel. Now everything is OK!
But here you are:
```
hooman@hooman-laptop:~$ ls /boot
abi-2.6.28-11-generic         memtest86+.bin
abi-2.6.28-13-generic         System.map-2.6.28-11-generic
abi-2.6.28-14-generic         System.map-2.6.28-13-generic
config-2.6.28-11-generic      System.map-2.6.28-14-generic
config-2.6.28-13-generic      vmcoreinfo-2.6.28-11-generic
config-2.6.28-14-generic      vmcoreinfo-2.6.28-13-generic
grub                          vmcoreinfo-2.6.28-14-generic
initrd.img-2.6.28-11-generic  vmlinuz-2.6.28-11-generic
initrd.img-2.6.28-13-generic  vmlinuz-2.6.28-13-generic
initrd.img-2.6.28-14-generic  vmlinuz-2.6.28-14-generic
```

---

### Post by MattM11 on 2009-07-29
I'm having the same problem!

I'm running Ubuntu 9.04. This morning Update Manager apparently installed a new Kernel (2.6.28-14). When an option came up I simply went with the default. (I was in a rush, so didn't have time to properly look at it). I then restarted when prompted. 

However it's apparently still using 2.6.28-13. 

When I run sudo update-grub I get:

> Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.28-14-generic
Found kernel: /boot/vmlinuz-2.6.28-13-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

When I run ls /boot I get:

> abi-2.6.28-11-generic         memtest86+.bin
abi-2.6.28-13-generic         System.map-2.6.28-11-generic
abi-2.6.28-14-generic         System.map-2.6.28-13-generic
config-2.6.28-11-generic      System.map-2.6.28-14-generic
config-2.6.28-13-generic      vmcoreinfo-2.6.28-11-generic
config-2.6.28-14-generic      vmcoreinfo-2.6.28-13-generic
grub                          vmcoreinfo-2.6.28-14-generic
initrd.img-2.6.28-11-generic  vmlinuz-2.6.28-11-generic
initrd.img-2.6.28-13-generic  vmlinuz-2.6.28-13-generic
initrd.img-2.6.28-14-generic  vmlinuz-2.6.28-14-generic

I'm still a bit of a novice when it comes to Ubuntu. :(

---

### Post by ranch hand on 2009-07-29
When you boot up go to terminal and;
```

gksudo gedit /boot/grub/menu.lst

```
when that comes up edit this section so that it looks like this
```

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

```
This is near the top of the page and will have you seeing the grub menu when you boot your box.

Reboot and when the menu comes up hit the letter "e".  This will allow you to edit (for that boot only) the menu.  Change all lines refering to 2.6.31-3 to 2.6.31-4 and then hit the letter "b" and the bugger will boot up.

This will make it possible to see if it is booting to the new kernal.  If so you can go back to your /boot/grub/menu.lst and simply remove all the entries that are not for the new kernal (leave the memtest entry too).  Then it will have no choice but to boot to the new kernal and you won't have all of them listed on the menu.

It would be good to remove at least one of those kernals from your drive.  You can check synaptic in "status" (bottom left corner) and look for "installed (auto removable)".  Some folks like to keep an old kernal around for a while in case the new one is flaky but except for being able to boot to the old kernal on a whim they are just taking up space on your drive, mark them for "complete removal".

---

### Post by MattM11 on 2009-07-29
ranch hand,

Thanks.

I followed your advice. Then, once I was sure it would boot to the new kernel, I changed the references from the old one (13) to the new one (14) in menu.lst. This seems to have done the trick. Both the grub menu and System Monitor refer to the newer kernel.

Next time, I'll pay more attention when I'm updating. :)

---

### Post by ranch hand on 2009-07-29
That is GREAT.

I love grub-legacy but I think that grub2 is going to be even better when it gets the kinks worked out and we learn how to run it.

I have finally gotten pretty good at grub and now the buggers change it, this is fun.

Now if I could only figureout why 2.6.28-14 won't update on most of my 9.04 variations.  Must have to do with my box as i see nothing in the forums about it.  Some took it, others did not.  I think I have some investigating to do.

---

### Post by p_squared on 2009-07-29
Another option is to delete menu.lst and then run update-grub (remember to backup the original file first!).  I just tried this and the latest kernel was added to the list.

---

### Post by ranch hand on 2009-07-29
The problem I have with scripts in grub-legacy is that they are add on and are not real dependable.  They work most of the time but when they don't they really fry your boot.

I take a little longer and edit my files.  The worst I have ever had grub-legacy screwed was by using Super Grub Disk.  Editing is a sure thing.

Grub2 is built on such scripts and it is going to be more flexible and able to deal with new file systems that the old.

I grew up working horses and tractors pulling horse drawn equipment.  Grub-legacy is kind of like that.  It works great.  The guy running it better know what he is doing.

Grub2 is more like a lot of modern ag equipment.  It knows what it is doing so the operator does not have to.  The only problem comes when something goes wrong and the guy running it can't fix it.  With patience and a little practice and experience grub2 is going to be grreat for ignert folks as well as people that know what is inside it.

Great fun.

---

### Post by klausner on 2009-07-30
> **p_squared said:**
> Another option is to delete menu.lst and then run update-grub (remember to backup the original file first!).  I just tried this and the latest kernel was added to the list.

I couldn't get update-grub to add 2.6.27-14 my old menu.lst in Intrepid either. But your suggestion was great! Worked like a charm. 

Must be something weird about 2.6.27-14, because I haven't had this problem before.

Thanks. :D

---

### Post by Hoom@n on 2009-07-31
> **klausner said:**
> I couldn't get update-grub to add 2.6.27-14 my old menu.lst in Intrepid either. But your suggestion was great! Worked like a charm. 

Must be something weird about 2.6.27-14, because I haven't had this problem before.

Thanks. :D
I think this problem just occurs when you changed your menu.lst file.

---

### Post by dhirendra1 on 2009-10-16
I am running Karmic with grub2 and dual boot it alongwith windows. I found that Grub2 was not adding new kernals (2.6.31-13 & 14) in the list. It was showing earlier versions 11 and 12 only. I removed these earlier versions through Synaptic and recreated menu.lst afresh through update-grub.  It now shows the latest kernels (13 and 14).  At the time of booting, however, the grub menu still shows the earlier kernels (11 and 12) and does not show the newer ones.  I removed (as root) the menu.lst and recreated it again....still old menu persists.  The output of ls /boot is as below:

dhiruravi@dhiruravi-laptop:~$ ls /boot
abi-2.6.31-13-generic         memtest86+.bin
abi-2.6.31-14-generic         System.map-2.6.31-13-generic
config-2.6.31-13-generic      System.map-2.6.31-14-generic
config-2.6.31-14-generic      vmcoreinfo-2.6.31-13-generic
grub                          vmcoreinfo-2.6.31-14-generic
initrd.img-2.6.31-13-generic  vmlinuz-2.6.31-13-generic
initrd.img-2.6.31-14-generic  vmlinuz-2.6.31-14-generic
dhiruravi@dhiruravi-laptop:~$ 

The output of update-grub is this:

dhiruravi@dhiruravi-laptop:~$ sudo update-grub
[sudo] password for dhiruravi: 
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31-14-generic
Found kernel: /boot/vmlinuz-2.6.31-13-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

dhiruravi@dhiruravi-laptop:~$ 

The startup-manager also shows the earlier kernels (11 & 12) in its list and does not update its list with the newer kernels.

Presently, I can boot into kernel 13 or 14 only by using "e" command at the time of boot by changing the kernel numbers.  Ubuntu, otherwise runs fine.  Could someone guide me as to how to amend the display list of grub at the time of booting to enable it to show the latest kernels???

---

### Post by dhirendra1 on 2009-10-17
It has been sorted out by editing the menu.cfg file by running following two commands:

sudo chmod +w /boot/grub/grub.cfg
gksudo gedit /boot/grub/grub.cfg

update-grub command thereafter brought back the read-only status for this file.

---

### Post by ranch hand on 2009-10-17
> **dhirendra1 said:**
> It has been sorted out by editing the menu.cfg file by running following two commands:

sudo chmod +w /boot/grub/grub.cfg
gksudo gedit /boot/grub/grub.cfg

update-grub command thereafter brought back the read-only status for this file.
This is what it is supposed to do.  You do not edit /boot /grub/grub.cfg directly.

Go to;

[http://ubuntuforums.org/showthread.php?t=1285897](http://ubuntuforums.org/showthread.php?t=1285897)

and read it.  Follow the links to more detailed information (some really good info from really great forum members).  Mine is just to get you started.  If you use the symbolic or "generic" menuentry for Ubuntu 9.10 in a custom entry, it will NEVER  need edited for the kernel, it will ALWAYS boot to the newest.

---

