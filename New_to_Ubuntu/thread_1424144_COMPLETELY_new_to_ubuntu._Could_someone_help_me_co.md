---
title: "COMPLETELY new to ubuntu. Could someone help me configure boot.ini?"
date: 2010-03-07
forum: New to Ubuntu
---

### Post by mikeeey on 2010-03-07
Hello everyone, I hate ask for answers like this, searching did me no good if I couldn't understand what anything even meant.

I'm completely new to ubuntu, and completely new to dual booting.

Here's where I'm at so far:

Last night I started to free up a 10GB portion.. I was very tired but excited to try out ubuntu. Well.. I got the portion free, but next thing you know I'm asleep :redface:

so I started where I left off this morning, I installed Ubuntu 9.10 to that free portion, then at the end of the setup it asked me to remove the CD and close the tray so it could restart. When it restarted it booted right back into windows XP, and this is where I'm stuck.

I'm unsure how to add ubuntu to boot.ini, I'm unsure what gnome or grub or grub2 is. **I'm just trying to figure out how to boot into ubuntu lol.**

If anyone could help me with this I'd really appreciete it.

Thanks!


**edit:** if it helps, here's what my boot.ini looks like. I'm just confused why it wasn't automatically added when I installed ubuntu to the other partition:

```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

```

---

### Post by nothingspecial on 2010-03-07
Are you sure you installed Ubuntu.

Boot up the live cd, in the menu, go, applications > accessories > terminal and type ```
sudo fdisk -l
```

Then copy and paste the output to a new post here.

---

### Post by skymera on 2010-03-07
Do you have more than one hard drive?

I'm thinking that GRUB is installed to the primary drive, whilst Ubuntu is on another, though this doesn't really explain why GRUB doesn't load and XP just boots.

+1 to answer above.

---

### Post by Method X on 2010-03-07
Ok.
Boot.ini can't take you into ubuntu, because Windows system doesn't support other OS.

Well, thats strange, but ubuntu always install GRUB. Ok, try to remember, maybe you cancelled grub installing,  or maybe you installed it on another partition?
Anyway, don't give up.

Try this one:
1.boot up from ubuntu Live CD.
2.open terminal
3. Then use these commands:

```
sudo fdisk -l
```

You will see something like:

>    Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        9253    74218496    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3            9253       29126   159629400    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sda4           29127       30402    10240000    7  HPFS/NTFS
Partition 4 does not end on cylinder boundary.
/dev/sda5            9253       28923   157996408+  83  Linux
/dev/sda6           28923       29126     1632928+  82  Linux swap / Solaris

that was mine filesystem, so, as you can see mine ubuntu installed on /dev/sda5

Get last number of your linux-sda.

after that try these commands:

```

sudo mount /dev/sdaX /mnt    (X is your sda number)
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt
grub-install /dev/sda                (without number of sda)

```

If you get an error with last command try that one:
```
grub-install --recheck /dev/sda
```

And  after that just exit with these commands:
```

exit
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt
sudo reboot

```

Hope, this will help.

---

### Post by candtalan on 2010-03-07
win.ini is only any use if you installed ubuntu using the Windows Ubuntu Installer (wubi). In this case the ubuntu is installed into a windows 'folder', and win.ini is used by the windows boot loader to offer an initial choice of Windows or ubuntu, with Windows being the default choice.

However, if you resized windows to create an unused space of 10GB on the disc, and then used the ubuntu CD to boot up, and install from the initial CD booted menu, then chose the installer options of install into largest unused space on the disc, then it should be ok and working. In which case the boot loader will be grub not windows.

---

### Post by mikeeey on 2010-03-07
thanks for the replies everyone!

(everything below I'm running off the CD)
Here's what the terminal displayed:
```
ubuntu@ubuntu:~$ sudo fdisk -l



Disk /dev/sda: 80.1 GB, 80060424192 bytes

255 heads, 63 sectors/track, 9733 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x3ccb16c8



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1        9733    78180291    7  HPFS/NTFS



Disk /dev/sdb: 160.0 GB, 160041885696 bytes

255 heads, 63 sectors/track, 19457 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0xd3e0d3e0



   Device Boot      Start         End      Blocks   Id  System

/dev/sdb1   *           1       18242   146528833+   7  HPFS/NTFS

/dev/sdb2           18243       19457     9759487+   5  Extended

/dev/sdb5           18243       19399     9293571   83  Linux

/dev/sdb6           19400       19457      465853+  82  Linux swap / Solaris

```


and here's some screenshots I took. You can see my 9.5GB partition is there, with ubuntu installed on it. I even found the grub folder in there.
I just have no idea how to boot into ubuntu. Is there another OS manager I need to install?

[IMG]http://img716.imageshack.us/img716/4210/screenshotyd.png[/IMG]
[IMG]http://img9.imageshack.us/img9/2783/screenshot1de.png[/IMG]



> **skymera said:**
> Do you have more than one hard drive?

I'm thinking that GRUB is installed to the primary drive, whilst Ubuntu is on another, though this doesn't really explain why GRUB doesn't load and XP just boots.

+1 to answer above.

Yes, I also have an 80GB HDD in my computer, but it's remained completely empty, and still has the same ammount of empty space as it did before I installed Ubuntu. In the screenshots above I found that ubuntu is quite infact on my 9.5GB partition. I also found the grub folder in this partition (not shown in the screenshots tho)


> **candtalan said:**
> 
However, if you resized windows to create an unused space of 10GB on the disc, and then used the ubuntu CD to boot up, and install from the initial CD booted menu, then chose the installer options of install into largest unused space on the disc, then it should be ok and working. In which case the boot loader will be grub not windows.

This is exactly what I did. I followed the "6 steps" to install ubuntu, and when it got to the partition step I cleared a <10GB partition and installed Ubuntu to the largest unused space on my primary HDD (which was the remaining 9.5GB)

Are there any other ways to install GRUB? Does the fact that grub is installed on the 2nd partition with Ubuntu explain why it's not showing up when I boot my computer?

---

### Post by linuxman94 on 2010-03-07
You need to do these commands, as Method X said.

```
sudo mount /dev/sdb5 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt
grub-install /dev/sdb
```

Then exit with these commands.

```
exit
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt
sudo reboot
```

---

### Post by asmoore82 on 2010-03-07
-OR- just set your BIOS to boot the other drive - no risk.

---

### Post by mikeeey on 2010-03-08
> **linuxman94 said:**
> You need to do these commands, as Method X said.

```
sudo mount /dev/sdb5 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt
grub-install /dev/sdb
```

Then exit with these commands.

```
exit
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt
sudo reboot
```

Thanks! those codes did the trick!
now I'm just figuring out how to change the default booting OS back to windows, as well as getting my airlink101 wireless USB card to work.

Thank again everyone, time to start exploring ubuntu!

---

### Post by Method X on 2010-03-08
> **mikeeey said:**
> Thanks! those codes did the trick!
now I'm just figuring out how to change the default booting OS back to windows, as well as getting my airlink101 wireless USB card to work.

Thank again everyone, time to start exploring ubuntu!

Nice to hear that.
About default booting OS:

```
sudo gedit /boot/grub/grub.cfg
```
locate for:
set default="0"
and change 0 to 4.

If you don't have grub.cfg than it must be menu.lst.

And about wireless, i think these links will help you:

[http://ubuntuforums.org/showthread.php?t=1342593&highlight=peepingtom]("http://ubuntuforums.org/showthread.php?t=1342593&highlight=peepingtom")
[http://www.linuxquestions.org/questions/linux-hardware-18/airlink-101-usb-wireless-on-ubuntu-9.10-785127/]("http://www.linuxquestions.org/questions/linux-hardware-18/airlink-101-usb-wireless-on-ubuntu-9.10-785127/")

Never give up on linux ;)

---

### Post by mikeeey on 2010-03-08
> **Method X said:**
> Nice to hear that.
About default booting OS:

```
sudo gedit /boot/grub/grub.cfg
```
locate for:
set default="0"
and change 0 to 4.

If you don't have grub.cfg than it must be menu.lst.

And about wireless, i think these links will help you:

[http://ubuntuforums.org/showthread.php?t=1342593&highlight=peepingtom]("http://ubuntuforums.org/showthread.php?t=1342593&highlight=peepingtom")
[http://www.linuxquestions.org/questions/linux-hardware-18/airlink-101-usb-wireless-on-ubuntu-9.10-785127/]("http://www.linuxquestions.org/questions/linux-hardware-18/airlink-101-usb-wireless-on-ubuntu-9.10-785127/")

Never give up on linux ;)

Thanks Method X! I'll try the default boot thing later when I get back from work.

Upon doing some google searches I found that the drivers I need for my AWLL4030 Wireless USB adapter are madwifi. I downloaded the madwifi files and was confused when I didn't find a setup file (LOL yes, coming from a windows user).
I've started another topic regarding the issue:
[http://ubuntuforums.org/showthread.php?p=8937025#post8937025](http://ubuntuforums.org/showthread.php?p=8937025#post8937025)


I'll take another look at those 2 topics you sent me, but from what I scanned over just now it looked like something that really confused me.

Is there a type of setup file format for linux? For example windows uses .exe, mac uses .dmg. Does linux have one?

---

### Post by harrisonk on 2010-03-08
[SIZE=2]It's a .deb for Ubuntu, a .yum for fedora, a .rpm for Red Hat Linux it's a .tar.gz for Slackware Linux so it depends on which Linux distro you use (in this case Ubuntu) so the equivalent of a .exe in Ubuntu is .deb  .

If this is confusing let me know and I will try and explain it better.

Harrison[/SIZE]

---

### Post by mikeeey on 2010-03-09
> **Method X said:**
> Nice to hear that.
About default booting OS:

```
sudo gedit /boot/grub/grub.cfg
```
locate for:
set default="0"
and change 0 to 4.

If you don't have grub.cfg than it must be menu.lst.

And about wireless, i think these links will help you:

[http://ubuntuforums.org/showthread.php?t=1342593&highlight=peepingtom]("http://ubuntuforums.org/showthread.php?t=1342593&highlight=peepingtom")
[http://www.linuxquestions.org/questions/linux-hardware-18/airlink-101-usb-wireless-on-ubuntu-9.10-785127/]("http://www.linuxquestions.org/questions/linux-hardware-18/airlink-101-usb-wireless-on-ubuntu-9.10-785127/")

Never give up on linux ;)

I tried changing the value, and when I saved it it didn't let me cause it was read only. lol how can I fix this?

---

### Post by Method X on 2010-03-09
> **mikeeey said:**
> I tried changing the value, and when I saved it it didn't let me cause it was read only. lol how can I fix this?

looks like you opened it without root priveleges.

again, open it with command:

gksudo gedit /boot/grub/grub.cfg

---

### Post by undecim on 2010-03-09
@Method X, mikeeey: grub.cfg is not meant to be edited directly.

If you want to change something about grub, you need to change it in /etc/default/grub, otherwise when you update your kernel, your changes will be overwritten.

To change the default option like you want, you need to edit /etc/default/grub by pressing Alt+F2 and typing "gksu gedit /etc/default/grub". Then change the line "GRUB_DEFAULT=0" to "GRUB_DEFAULT=4", and the run "sudo update-grub" from a terminal.

---

### Post by Method X on 2010-03-09
> **undecim said:**
> @Method X, mikeeey: grub.cfg is not meant to be edited directly.

If you want to change something about grub, you need to change it in /etc/default/grub, otherwise when you update your kernel, your changes will be overwritten.

To change the default option like you want, you need to edit /etc/default/grub by pressing Alt+F2 and typing "gksu gedit /etc/default/grub". Then change the line "GRUB_DEFAULT=0" to "GRUB_DEFAULT=4", and the run "sudo update-grub" from a terminal.

thanks.
Will note that for future.

---

### Post by andrew.46 on 2010-03-09
Hi harrisonk,

> **harrisonk said:**
> it's a .tar.gz for Slackware Linux

To be perfectly correct for Slackware it is actually a .tgz, or .txz for newer versions...

Andrew

---

### Post by mikeeey on 2010-03-09
> **undecim said:**
> @Method X, mikeeey: grub.cfg is not meant to be edited directly.

If you want to change something about grub, you need to change it in /etc/default/grub, otherwise when you update your kernel, your changes will be overwritten.

To change the default option like you want, you need to edit /etc/default/grub by pressing Alt+F2 and typing "gksu gedit /etc/default/grub". Then change the line "GRUB_DEFAULT=0" to "GRUB_DEFAULT=4", and the run "sudo update-grub" from a terminal.
Thank you undecim! I've got it working now, and I even got my wireless drivers working on Ubuntu as well! I'm on the Internet for the first time on Ubuntu typing this!

---

