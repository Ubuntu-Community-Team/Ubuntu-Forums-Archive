---
title: "GRUB no longer appears"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by ImaginaryPixel on 2009-10-29
I installed Ubuntu 9.10 from a DVD that I burned.  I used the custom install option and created a swap partition of about 5 GB and / of about 28.  Windows 7 occupies 239 GB.  When I shutdown the computer and try to reboot into Ubuntu, GRUB does not even appear at all and it automatically goes into Windows 7.  I do not know if I installed Ubuntu correctly, I did not want to do a clean install so I did custom and I selected what I thought I needed, did I need to make more partitions than I did or is there a way to repair GRUB?

---

### Post by jrothwell97 on 2009-10-29
Welcome!

Ubuntu 9.10 uses GRUB 2, and the menu is hidden by default. Press and hold SHIFT on boot, and the menu should appear.

Good luck!

---

### Post by ImaginaryPixel on 2009-10-29
OK, I have tried holding shift but it still goes straight to Windows 7 without any thing appearing to change.  When exactly do I need to hold shift?  After the Splash image or right when I press the power button?

---

### Post by jrothwell97 on 2009-10-29
Hmm... this is odd.

Try booting from the Ubuntu CD again, open up Disk Utility (System/Administration/Disk Utility) and tell us what you see.

Alternatively, open Terminal (Applications/Accessories/Terminal) and run the following command:

```
sudo fdisk -l
```

(Just in case you weren't aware, when you enter your password at the terminal nothing will appear - no stars, bullets, etc. This is normal, your password is still going in.)

---

### Post by ImaginaryPixel on 2009-10-29
It says some stuff.  It only has windows marked as bootable, is that a problem? Do I need to mark linux as bootable?

[IMG]http://img265.imageshack.us/img265/6290/screenshot1u.png[/IMG]

---

### Post by jrothwell97 on 2009-10-29
Yes, definitely use Disk Utility to mark the Ubuntu partition as bootable.

Try rebooting and holding SHIFT again, and if that doesn't work, come back here and we'll walk you through reinstalling GRUB.

---

### Post by kansasnoob on 2009-10-29
> **jrothwell97 said:**
> Yes, definitely use Disk Utility to mark the Ubuntu partition as bootable.

Try rebooting and holding SHIFT again, and if that doesn't work, come back here and we'll walk you through reinstalling GRUB.

Nonsense! I'm sorry to be harsh but you're wrong. Look at mine:

> lance@lance-desktop:~$ sudo fdisk -l
[sudo] password for lance: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bffde

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2677    21502971    7  HPFS/NTFS
/dev/sda2            3764       19457   126062055    5  Extended
/dev/sda3            2678        3763     8723295   83  Linux
/dev/sda5            3764        4799     8321638+  83  Linux
/dev/sda6            4800        9284    36025731   83  Linux
/dev/sda7            9285       10301     8169021   83  Linux
/dev/sda8           10302       14879    36772753+  83  Linux
/dev/sda9           14880       15032     1228941   82  Linux swap / Solaris
/dev/sda10          15033       18174    25238083+  83  Linux
/dev/sda11          18175       19457    10305666   83  Linux


Only sda1 has a * to show "boot" even though I have three more bootable Linux OS's and trying to edit that will break things even worse!

---

### Post by ImaginaryPixel on 2009-10-29
I am in the process of making the 58GB partition bootable, but it has been "modifying" the partition for about 10 mins.  Any idea on how long it would take?

---

### Post by ImaginaryPixel on 2009-10-29
> **kansasnoob said:**
> Nonsense! I'm sorry to be harsh but you're wrong. Look at mine:



Only sda1 has a * to show "boot" even though I have three more bootable Linux OS's and trying to edit that will break things even worse!

Do you have an idea what to do?

---

### Post by kansasnoob on 2009-10-29
Please use the quote tags and post the ouput of:

```
sudo fdisk -l
```

and:

```
sudo blkid
```

---

### Post by ImaginaryPixel on 2009-10-29
For sudo fdisk -l
> Disk /dev/sda: 320.1 GB, 320072933376 bytes
4 heads, 44 sectors/track, 3551945 cylinders
Units = cylinders of 176 * 512 = 90112 bytes
Disk identifier: 0x97646c29

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          12        1176      102400    7  HPFS/NTFS
/dev/sda2            1176     2853760   251027456    7  HPFS/NTFS
/dev/sda3         2853761     3551936    61439488    5  Extended
/dev/sda5         2853761     2909247     4882834   82  Linux swap / Solaris
/dev/sda6         2909248     3551936    56556610   83  Linux
 

> ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="DCF492C7F492A376" LABEL="System Reserved" TYPE="ntfs" 
/dev/sda2: UUID="9AE8E328E8E300FD" TYPE="ntfs" 
/dev/sda5: UUID="4283a927-72f1-44b2-a0e6-fd0b1449d6d9" TYPE="swap" 
/dev/sda6: UUID="81c6b0fd-e364-4872-9bfd-17dcce64ea74" TYPE="ext4" 


---

### Post by drs305 on 2009-10-29
Simultaneous postings: You are going to have to determine if Karmic is installed. Run the commands recommended above. If it is installed:

You should hold down the shift key just after you would try to enter BIOS. Just hold it down until you see the menu. If you wait until you see a splash image it's too late (unless it's a BIOS splash). Nevertheless, you should see a Ubuntu option so there is likely a problem with the Grub 2 installation.

If you know Karmic is installed and you can't get Ubuntu to display a menu, consider reinstalling Grub 2 via the LiveCD.

Here is the link for doing this, from the Community Documentation:
[https://help.ubuntu.com/community/Grub2#ReinstallingfromLiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

### Post by kansasnoob on 2009-10-29
> **ImaginaryPixel said:**
> I am in the process of making the 58GB partition bootable, but it has been "modifying" the partition for about 10 mins.  Any idea on how long it would take?

That was a bad, bad thing to do!

My best guess is that you'll have to reinstall.

---

### Post by jrothwell97 on 2009-10-29
I stand corrected...

The next step is to reinstall GRUB. We now know your Linux install lives on /dev/sda6 (this is the path Ubuntu uses to write to the partition), which uncomplicates things greatly.

We'll start by opening the terminal again, creating the necessary folders and mounting the drives. Run the following command:
```
sudo mkdir /mnt/dev /mnt/proc
sudo mount /dev/sda6 /mnt
sudo mount -o bind /dev /mnt/dev
sudo mount -o /proc /mnt/proc
```
Now, we will *change root* into your Ubuntu install - this creates a fake shell which will act like its root is the same as your Ubuntu partition.
```
sudo chroot /mnt
```
Now, run this command, which will reinstall GRUB:
```
sudo grub-install /dev/sda
```
If you get errors, run
```
sudo grub-install --recheck /dev/sda
```
Now, reboot, and you *should* (fingers crossed) be able to get into Ubuntu.

When you get back into Ubuntu, I suggest you run
```
sudo update-grub2
```
as this will allow you to boot into Windows again by pressing the Shift key at boot time.

Good luck!

---

### Post by ImaginaryPixel on 2009-10-29
> **kansasnoob said:**
> That was a bad, bad thing to do!

My best guess is that you'll have to reinstall.
I cancelled and it said it was cancelled so I don't think anything happened. and I did what you told me to in the previous posts.

---

### Post by ImaginaryPixel on 2009-10-29
Ok, I am going to go ahead and reinstall GRUB2

This is what happened
> ubuntu@ubuntu:~$ sudo mkdir /mnt/dev /mnt/proc
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo mkdir /mnt/dev /mnt/proc
mkdir: cannot create directory `/mnt/dev': File exists
mkdir: cannot create directory `/mnt/proc': File exists
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/dev
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo mount -o /proc /mnt/pro
mount: can't find /mnt/pro in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# sudo grub-install /dev/sda
sudo: unable to resolve host ubuntu
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
root@ubuntu:/# 


---

### Post by ImaginaryPixel on 2009-10-29
I was unable to reinstall GRUB2 so I don't know what to do.

---

### Post by ImaginaryPixel on 2009-10-29
Now, my computer boots to grub but it displays an error message
error: no such partition found

---

### Post by drs305 on 2009-10-29
> **ImaginaryPixel said:**
> I was unable to reinstall GRUB2 so I don't know what to do.
> **ImaginaryPixel said:**
> Now, my computer boots to grub but it displays an error message
error: no such partition found

It is looking more and more like Karmic was never correctly installed. It's time to attempt another reinstallation. Before you do that, you might want to boot the LiveCD and run Gparted (System, Administration, Gparted) and see what has happened in the way of partitioning. Once you open Gparted, you can decide whether you want to delete any and all Ubuntu partitions you created during the install or whether you want to set them up and use manual partitioning on the next attempt.

This assumes that you had attempted a clean install and that none of these partitions had any of your personal data/files on them.

---

### Post by ranch hand on 2009-10-29
You could do something radical, like trying to use the rescue from LiveCD listed in the wiki;

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

The part you need is near the bottom of the page.

You could also listen to folks that have worked with grub 2 for months now.  This might help.  kanasnoob and drs305 not only have used it but actually know how to do some very interesting things with it.

You would do well to look at drs305s sig for some links to his work, for instance.

A search of these forums would have turned these things up before you started screwing with your partition table.

---

### Post by armware on 2009-11-19
your typo stands out:

```

ubuntu@ubuntu:~$ sudo mount -o /proc /mnt/pro
mount: can't find /mnt/pro in /etc/fstab or /etc/mtab
```

also i'm pretty sure you need to run  sudo update-grub /dev/sda

---

