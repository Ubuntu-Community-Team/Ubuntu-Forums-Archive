---
title: "Can GRUB be Fixed, Repaired or whatever????"
date: 2010-09-28
forum: New to Ubuntu
---

### Post by suomalainen on 2010-09-28
Ubunteros,

2 months ago I installed Ubuntu 10.04LTS on my USB Seagate 500GB Expansion Portable Drive.

Prior to the install process, I removed the hard disk drive that resided in my Dell Inspiron 2200 and then proceeded with the Ubuntu install.

I can launch Ubuntu 10.04LTS but not in the conventional way by using Grub and choosing between 2 different operating systems.

Instead, my process goes as follows during boot-up:

1. Turn on the power to the laptop

2. During boot-up hit F2, when prompted to do so, in order to enter BIOS setup
 
3. When in BIOS I go to Boot Sequence and either remove internal HDD as a bootable device or add it as the second bootable device. Here's how it works and why. If I add the internal HDD as the second bootable device then the next time I boot up the sequence will move to removing the internal HDD as a bootable device. And each time I boot-up I rotate between the 2 choices.

4. Once this step is completed I save my work and Ubuntu 10.04 LTS boots up.

5. I must adhere to these steps precisely if I want to use Ubuntu. No if's ands or but's about it!


WHAT I WOULD LIKE TO SEE AND OR ACHIEVE

I would like to be able to power on my laptop and have GRUB allow me to choose beween 2 operating systems. In my case Windows XP or Ubuntu 10.04LTS


Anyway, does anyone know how to go about tackling this issue?

Thanks!

P.S. I would like to ask that anyone that responds with assistance to please read my post a second time. I have posted a similar post before and too many times people ask questions that are already identified in my original post. Example: What happens when you press F2? Or is the internal HDD installed?

---

### Post by Silent Warrior on 2010-09-28
I have no idea how to help you myself (I only use internal drives), but one thing I CAN tell you is that you aren't the first to try this. A search through the forums should provide some helpful tips.
Personally, what I think you need to do is to boot into Ubuntu, with both drives attached, of course, then run some os-prober, then update grub, and you should see both OSes listed.

I was intentionally unspecific because a careless grub-update could make unexpected things happen to your Windows boot-loader. Look for better advice before doing anything.

---

### Post by cariboo on 2010-09-28
Grub2 needs to be installed on the mbr of the first hard drive in order for it to do what you want. boot into Ubuntu, then open an Applications->Accessories->Terminal. At the prompt type:

```
sudo grub-install /dev/sda
```

where /dev/sda is the first hard drive in your system. The in the same terminal type:

```
sudo update-grub
```

After update-grub you should see something that looks like this:

```
sudo update-grub
[sudo] password for cariboo: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Ubuntu maverick (development branch) (10.10) on /dev/sdb1
done
```

[list]
[*] The first line is the kernel I boot from
[*] The second line is the recovery mode boot option
[*] The third line is memtest, which can be used to diagnose memory problems
[*] The fourth line is Windows 7 boot option
[*] The fifth line is a second Mavrick install.
[/list]

If you are dual booting, you should only see two entires for Ubuntu, one for memtest and one for Windows.

---

### Post by suomalainen on 2010-09-28
cariboo907,

Thanks for the response. Is there a terminal command I can use and then post so that we know what exactly is on each sda?

Also, If I decide to disconnect my USB which has Ubuntu on it my laptop will still boot up except that it will use windows right?

---

### Post by suomalainen on 2010-09-28
cariboo907,

I ran the terminal command you suggested and it doesn't list Windows XP... Did I now damage something???

Thanks

vo@pvo-laptop:~$ sudo grub-install /dev/sda
[sudo] password for paavo: 
Probing devices to guess BIOS drives. This may take a long time.
Searching for GRUB installation directory ... found: /boot/grub
Installing GRUB to /dev/sda as (hd0)...
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)	/dev/fd0
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdd
vo@vo-laptop:~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.32-24-generic
Found kernel: /boot/vmlinuz-2.6.32-23-generic
Found kernel: /boot/vmlinuz-2.6.32-22-generic
Found kernel: /boot/vmlinuz-2.6.32-21-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

---

### Post by suomalainen on 2010-09-28
Does this help anything. PLEASE NOTE IT WAS DONE PRIOR TO THE RECENT TERMINAL COMMANDS.

============================= Boot Info Summary: ==============================

=> No boot loader is installed in the MBR of /dev/sda
=> Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in
partition #2 for /boot/grub.

sda1: __________________________________________________ _______________________

File system: vfat
Boot sector type: Dell Utility: Fat16
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files/dirs: /COMMAND.COM

sda2: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows XP
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows XP
Boot files/dirs: /boot.ini /ntldr /NTDETECT.COM

sda3: __________________________________________________ _______________________

File system: vfat
Boot sector type: DEll Restore: Fat32
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files/dirs: /COMMAND.COM

sdb1: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows XP
Boot sector info: No errors found in the Boot Parameter Block.
Operating System:
Boot files/dirs:

sdb2: __________________________________________________ _______________________

File system: ext3
Boot sector type: -
Boot sector info:
Operating System: Ubuntu 10.04.1 LTS
Boot files/dirs: /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab
/boot/grub/core.img

sdb3: __________________________________________________ _______________________

File system: swap
Boot sector type: -
Boot sector info:

---

### Post by suomalainen on 2010-09-28
I re-booted my laptop and now I have a error 21 message.

Can this be fixed?

---

### Post by Silent Warrior on 2010-09-29
Hm... If I understand correctly, you first had GRUB on sdb, and now you've installed it to sda as well. I don't think that in itself should be catastrophic, but you might have problems with it in the future - I think I did, having GRUB installed both to the MBR and a partition.
First check that you're booting off the correct drive. /dev/sda would be your Windows-drive.

---

### Post by eriktheblu on 2010-09-29
OK, you have windows on your internal disk (sda) and Ubuntu on your external (sdb)

What you wanted to do was set boot priority (in the BIOS) of your external USB device above the internal disk. This way when the USB drive is plugged in it will boot to grub, and when it isn't it will boot to Windows.

When you executed sudo grub-install /dev/sda it attempted to install grub on your internal drive. This was not a good idea. It seems to have failed to install grub, and messed up your MBR. Disconnect your USB drive, and boot to a Windows recovery disk to adjust the MBR of your internal disk (Google fixmbr for instructions).

I think you had grub right the first time, you just needed to adjust the boot priority. My Dell laptop is primarily a windows machine so I manually override the boot priority when I want to boot from USB, but I have set it up with USB first without any difficulty.

---

### Post by suomalainen on 2010-09-29
eriktheblu, You stated the following:

> What you wanted to do was set boot priority (in the BIOS) of your external USB device above the internal disk. This way when the USB drive is plugged in it will boot to grub, and when it isn't it will boot to Windows.

BUT I STATED AT THE OUTSET THE FOLLOWING:

> I can launch Ubuntu 10.04LTS but not in the conventional way by using Grub and choosing between 2 different operating systems.

Instead, my process goes as follows during boot-up:

1. Turn on the power to the laptop

2. During boot-up hit F2, when prompted to do so, in order to enter BIOS setup

3. When in BIOS I go to Boot Sequence and either remove internal HDD as a bootable device or add it as the second bootable device. Here's how it works and why. If I add the internal HDD as the second bootable device then the next time I boot up the sequence will move to removing the internal HDD as a bootable device. And each time I boot-up I rotate between the 2 choices.


Thanks for the info on fixmbr.

---

### Post by eriktheblu on 2010-09-29
I don't recommend this, but if you want to get a little crazy you might try:

1. If you are using Windows 7 or Vista, use Vista to allot ~256 MB of blank space on your internal HDD

1a. If you are using XP or earlier, defrag in Windows, then resize using Gparted.

2. Using Gparted, create an ext4 partition in the blank space

3. Edit /etc/fstab so /boot is mounted on your new partition

4. sudo grub-install /dev/[new partition]

From there set the internal HDD as your primary boot device in the BIOS.

---

