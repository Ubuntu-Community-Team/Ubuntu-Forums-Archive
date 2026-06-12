---
title: "Install to USB flash won't boot, &quot;No partition active&quot;"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by palmboy5 on 2008-12-18
I've installed Ubuntu 8.04 desktop version to a 4GB flash drive following this guide:
[http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/](http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/)

However, after the installation completes and reboots, all I get is "No partition active" and some stuff asking me to insert a bootable media.

I found this thread
[http://ubuntuforums.org/showthread.php?t=887895](http://ubuntuforums.org/showthread.php?t=887895)
and tried the suggested commands.

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 4043 MB, 4043308544 bytes
255 heads, 63 sectors/track, 491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe0100867

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         463     3719016   83  Linux
/dev/sda2             464         491      224910    5  Extended
/dev/sda5             464         491      224878+  82  Linux swap / Solaris
```

```
ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal Bash-like line editing --- (I'm typing this up manually so this is skipped) --- of a device/filename.]
grub> find /boot/grub/stage1
find /boot/grub/stage1

Error 15: File not found
```

To improvise I've tried within sudo grub:
```
root sda,1
root (sda,1)
root (sd1)
root (/dev/sda,1)
setup sda
setup (sda)
```

All of them got either Error 11 or Error 23.

What do I do?:confused:

This is my second try installing to the flash drive. The first try it WOULD boot but then error and fall back to shell. All I got was a command line.

---

### Post by falcon61102 on 2008-12-18
Try starting up gparted and looking at your USB drive.  Based on your fdsik results, it shows that none of your partitions are flagged as the boot partition.  You should be able to set this in gparted.

---

### Post by palmboy5 on 2008-12-18
I'm running the install CD as a liveCD, and I get the error message "Root privileges are required for running GParted".

---

### Post by falcon61102 on 2008-12-18
That's interesting.  Try opening up a terminal windows and type:
```
gksudo gparted
```

---

### Post by palmboy5 on 2008-12-18
That works! In GParted I right-clicked on /dev/sda1 and selected Manage Flags. Do I just check "boot", close, and reboot?

---

### Post by falcon61102 on 2008-12-18
Yeah, give that a try and if any problems come up, post back and we'll work throug them.

---

### Post by palmboy5 on 2008-12-18
Ok, rebooting gets me "No boot signature in partition". Bah. >_<

---

### Post by falcon61102 on 2008-12-18
If you run a fdisk -l, does the partition show up with a * next to it indicating that it is flagged as a boot partition?

Also, by the sounds of that error, it looks like your GRUB didn't install itself into the MBR of the USB drive.  When you first installed Ubuntu, did you select the option to install the GRUB?  Also, try running the GRUB setup again:
```
sudo grub
find /boot/grub/stage1
```
What does this produce?

---

### Post by palmboy5 on 2008-12-18
Yes fdisk -l shows a * next to /dev/sda1, under Boot.

find /boot/grub/stage1 gets "Error 15: File not found".

---

### Post by falcon61102 on 2008-12-18
Alright, that's good about the boot flag.

And no worries with the GRUB sequence.  Below is a link to another thread and if you look about half way down the first thread you will see a quote from Tosk.  Follow the commands that he has listed and you should be good to go.  I ran into the same problem a while back trying to install to a USB drive and this is what fixed it.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by palmboy5 on 2008-12-18
I did all of his commands with the sudo mounts and stuff but find /boot/grub/stage1 still gets "Error 15: File not found".

I'm going to just reformat it to FAT32 (what it was originally before my install that WAS bootable) and try the installation again..

---

### Post by falcon61102 on 2008-12-18
Alright.  It may be that your GRUB didn't install correctly last time.  

Make sure when you are going through the install, you select the correct partition for the GRUB to be installed on and you should be good to go.

---

### Post by palmboy5 on 2008-12-18
In this screenshot from the guide
[img]http://www.pendrivelinux.com/wp-content/uploads/advanced.png[/img]

I have that "Install boot loader" checked. Selected in the drop down menu is the one that has the name of my flash drive to the right of the /dev/sda; in other words, the first option. I don't know why his screenshot didn't show a name, because even the other option(s) which didn't have names were just blank instead of repeating what was on the left.

---

### Post by falcon61102 on 2008-12-18
By selecting /dev/sda you are installing it to the HD itself and not a specific partition.  It's better to select an actual partition such as /dev/sda1.  Select the same partition that you are going to install Ubuntu into and you'll be fine.

---

### Post by palmboy5 on 2008-12-18
Well I tried both ways and both got problems:

Select /dev/sda for boot loader install boot error
```
[   15.398895] invalid compressed format (err=1)
[   15.400056] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
```

Select /dev/sda1 for boot loader install boot error
```
[   16.402549] Kernel panic - not syncing: No init found. Try passing init= option to kernel.
```

Both say this at the bottom
```
Kernel alive
kernel direct mapping tables up to 100000000 @ 8000-d000
```

---

### Post by palmboy5 on 2008-12-19
Anyone have any idea whats going on?

---

### Post by jackgu1988 on 2008-12-19
hi! i have a problem when trying to boot from the flash drive... i am using a dual boot system (debian and ubuntu) and when i try to boot from the flash nothing happens... just like before it asks whether i want debian or ubuntu... what can i do? :confused:

---

### Post by logos34 on 2008-12-19
> **jackgu1988 said:**
> hi! i have a problem when trying to boot from the flash drive... i am using a dual boot system (debian and ubuntu) and when i try to boot from the flash nothing happens... just like before it asks whether i want debian or ubuntu... what can i do? :confused:

did you correctly select the usb drive for Grub location as in post # 13 above?

---

### Post by jackgu1988 on 2008-12-20
don't i have to do this when i install ubuntu on the flash?

---

### Post by logos34 on 2008-12-20
> **jackgu1988 said:**
> don't i have to do this when i install ubuntu on the flash?

yes, that's why I'm asking

---

### Post by jackgu1988 on 2008-12-20
the problem is that i can't boot from the usb so that i can install ubuntu on it... :(

---

### Post by logos34 on 2008-12-20
> **jackgu1988 said:**
> the problem is that i can't boot from the usb so that i can install ubuntu on it... :(

no, you go into your linux or windows OS, run the pendrivelinux installer, and whnen you come to the bootloader step you need to specify 'sda' or 'sdb' (i.e. the mbr of the usb flsh drive) as the Grub location...finish the install and THEN you reboot to the usb (change the Bios boot disk order to boot USB first)

---

### Post by jackgu1988 on 2008-12-20
I followed this guide: [http://www.pendrivelinux.com/2008/11/01/ubuntu-810-install-using-the-built-in-usb-installer/](http://www.pendrivelinux.com/2008/11/01/ubuntu-810-install-using-the-built-in-usb-installer/) and I just can't boot from the flash... I don't know what else to do...

---

### Post by logos34 on 2008-12-20
oh, I thought you were using the other howto in the thread...Have you tried this:

> Notes: If your BIOS does not support booting from USB, you can use the USB Boot CD for Ubuntu 8.10 to launch your USB Ubuntu 8.10

[http://www.pendrivelinux.com/2008/11/01/ubuntu-810-install-using-the-built-in-usb-installer/](http://www.pendrivelinux.com/2008/11/01/ubuntu-810-install-using-the-built-in-usb-installer/)

So even though your Bios supports USB (you are able to select the USB drive in the Bios boot order, right?), you could try the USB Boot CD--if you're able to get the flash drive to boot you'll at least know it's a problem with the computer.  Hope that helps

---

