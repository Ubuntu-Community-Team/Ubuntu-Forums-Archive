---
title: "sata drive not detected"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by jj3502 on 2008-12-31
my sata 320GB HDD is Not found in the partitioner V8.04:confused:
core 2 duo 2.66ghzs, 2GB ram, nvidia 7300 512mb, Sony rw+-

---

### Post by jj3502 on 2008-12-31
Plz help :(

---

### Post by Gadwil on 2008-12-31
Does your BIOS recognize it?

---

### Post by jj3502 on 2008-12-31
Yes

Window already instaled (trying to duel boot)

---

### Post by xjcannonx on 2008-12-31
can you post the output of ```
sudo fdisk -l
```

---

### Post by jj3502 on 2008-12-31
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 4043 MB, 4043309056 bytes
255 heads, 63 sectors/track, 491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04dd5721

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         492     3948512+   b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(490, 254, 63) logical=(491, 145, 38)
ubuntu@ubuntu:~$ 
```

---

### Post by Miljet on 2008-12-31
That sure don't look like a 320 GB hard drive to me!

Do you have more than one drive?

---

### Post by jj3502 on 2008-12-31
yes i have a 40GB one and a 320GB 
(windows boots from the 40GB one and uses the 320GB one for some files and programs)

If it helps its Windows xp pro sp3

---

### Post by Miljet on 2008-12-31
Well fdisk is not seeing the 320 GB drive. Are you sure that it is showing up in the BIOS? Have you gone into the BIOS and looked for it?

---

### Post by captain_171 on 2008-12-31
There is a setting in your bios about sata that u need to change its called sata compatibility setting u need to change that but sence u have windows installed u need to change it back when u boot into windows 
let know if u have questions

---

### Post by dragonwolf on 2008-12-31
I am having a somewhat similar issue well kinda it seems to me that ubuntu is not finding my hard drive when I am attempting to install ubuntu. it gets to the busybox promt, then displays (initramfs) and hangs I know the cd and my hardware are good I ussually run this as a windows box I'm new to linux so I thought I would try this on a diff HD after playing with it some in a VMWare machine inside windows. LIke I said I have used the Ubuntu DVD From Ubuntu b4 to load it in a VM and all My hardware works fine in windows.

below is a hardware list any help would be greatly appriciated-

XFX Nvidia 750a SLI Mobo
AMD Phenom 8650
4GB PC2 6400 
80GB Seagoate Berracuda Sata Drive
1 IDE DVD Burner
1 SAta DVD Burner
Nvidia 9800 GT Video Card
6 Port USB Expansion card (PCI)
13-1 Media Card Reader

I have disconnected all other hardware including the media card reader to no avail

---

### Post by jj3502 on 2009-01-01
miljet, as I said in my last post my bios and windows can read / write to it fine 

captain_171, in my bios there is a sata compatibility setting but that didn't help 

:confused:

---

### Post by jj3502 on 2009-01-01
because windows detects both drives could I install wubi?

---

### Post by egalvan on 2009-01-01
> **jj3502 said:**
> my sata 320GB HDD is Not found in the partitioner V8.04:confused:
core 2 duo 2.66ghzs, 2GB ram, nvidia 7300 512mb, Sony rw+-


Are you looking for the drive in the scroll box up at the top right-hand side of the Gparted windows?

GParted only shows one drive at a time.

My machine has two drives, here are two screenshots...
one shows the first hard drive, the other the second hard drive...

---

### Post by graphic on 2009-01-09
I have been having the same problem and now believe the motherboard (nForce XFX 750a SLI) to be the culprit (at least in my case). I was trying to install Ubuntu Server 8.10 64 and all was well except for when I got to disk detection, at which point I was prompted that no disk drive was detected and to either load a driver from a floppy, select from a list of drivers (none worked), or continue without a disk drive (why would I want to?). Tonight I will be attempting to use a precompiled binary from NVidia on a floppy to rectify this problem (this is not a very desirable solution as who the hell has a floppy drive any more) and I will post my results. I may also have to compile the driver myself on a working system and use that binary as the binaries provided by NVidia are for SuSE and other distros, if this turns out to be the case and works I will provide the binary in this thread. [Here is a link to the drivers from NVidia]("http://www.nvidia.com/object/linux_nforce_1.23.html"). 

Oh and by the way I also get the same (initramfs) prompt when trying to boot Ubuntu Desktop from the LiveCD, it doesn't actually "hang" for me I have some basic commands I can use, but nothing helpful.

If anyone gets around to trying to fix the problem in the ways I have suggested please post your results.

An interesting side note is that my old version of WindowsXP Pro (vintage 2001) blue screens when I try to do an install on this system, I believe this to be a problem in the same vain of the problems I've been having installing Ubuntu, except this version of XP being, so old, just barfs rather then failing gracefully. I imagine a newer version would not have the same problems. (It really is a pre-sp1 copy of XP, got it from my high school >_0 if you know what I mean).

---

### Post by forger on 2009-01-09
post the output of:
```

lspci -nn
sudo lshw -C disk

```

In case you are asked for a password, type it in and press Enter.

---

### Post by graphic on 2009-01-09
Did a quick look on a VMWare with Ubuntu 7.10 installed, and it seems sata_nv (driver from nVidia) is installed, I'd assume the same goes for 8.10. So I'm actually stumped. This is a rather annoying situation.

Didn't see your reply forger, I'll give that a try but I can't right now, not at the machine.

---

### Post by graphic on 2009-01-09
After some looking online and talking with the good people in the Ubuntu channel I have solved my problem (and perhaps dragonwolf's). 

Problem:
SATA drives (CD/DVD/HDD) not detected during install. This can also cause the "Boot from CD" feature on desktop editions to drop into the busybox prompt.

Suspected Culprit:
Power-saving features built into the Linux kernel in conjunction with my motherboard (nForce XFX 750a SLI). This is what I believe because I was told that "pci=nomsi nolapic noapic" had to do with disabling power saving features when booting. If this is not the case please add to this thread. Knowledge is power. 

Solution:
1) When at the install menu (has several options : Install, Check CD for defects, Test memory, etc...). I was installing so I that is what I was choosing. Press F6 twice to get to extra kernel boot options select "nolapic" and "noapic" then ESC. From pressing F6 you should see the kernel boot line delete "--" and add "pci=nomsi" hit enter. Go through the install prompt and install normally (hopefully you will get no "can't find drive" errors).

2) After the install your system should reboot, you should see the grub boot countdown, press ESC to get into the grub loader. Select the proper boot option (normally the first) and hit 'e'.
Select the line that says "kernel" and hit 'e' again. Remove "splash" from the boot option and add "pci=nomsi nolapic noapic" and hit enter, you'll be taken to the previous screen. Press 'b' to boot.

3) Hopefully Ubuntu should boot normally. After it does open a console version and use the following command
```
sudo nano /boot/grub/menu.lst
```
You will be prompted for your password, enter it and go to the very bottom of the the editor to the lines 
```

title           Ubuntu 8.10, kernel 2.6.27-7-server
uuid            1eeed980-8f03-4647-8115-94224929bca9...
kernel          /boot/vmlinuz-2.6.27-7-server...
initrd          /boot/initrd.img-2.6.27-7-server...
```
Note: Title will differ depending on your version

For the line that begins with "kernel" go to the end, remove "splash" and again add "pci=nomsi nolapic noapic" to the line. Hit Ctrl+X to exit, you will be prompted to save, say yes and you're done.

Reboot to test, hopefully you boot up just fine. 

Thanks for the help gogereaver in the Ubuntu channel on IRC and I also used [this]("http://ilikeubuntu.blogspot.com/2008/11/installing-ubuntu-810-on-laptop-with.html") blog post to get me going.

Again if I've made any errors in my assumptions about the problem or my solution is over-kill in some way add to this thread.

---

### Post by dragonwolf on 2009-01-12
> **graphic said:**
> After some looking online and talking with the good people in the Ubuntu channel I have solved my problem (and perhaps dragonwolf's). 

Problem:
SATA drives (CD/DVD/HDD) not detected during install. This can also cause the "Boot from CD" feature on desktop editions to drop into the busybox prompt.

Suspected Culprit:
Power-saving features built into the Linux kernel in conjunction with my motherboard (nForce XFX 750a SLI). This is what I believe because I was told that "pci=nomsi nolapic noapic" had to do with disabling power saving features when booting. If this is not the case please add to this thread. Knowledge is power. 

Solution:
1) When at the install menu (has several options : Install, Check CD for defects, Test memory, etc...). I was installing so I that is what I was choosing. Press F6 twice to get to extra kernel boot options select "nolapic" and "noapic" then ESC. From pressing F6 you should see the kernel boot line delete "--" and add "pci=nomsi" hit enter. Go through the install prompt and install normally (hopefully you will get no "can't find drive" errors).

2) After the install your system should reboot, you should see the grub boot countdown, press ESC to get into the grub loader. Select the proper boot option (normally the first) and hit 'e'.
Select the line that says "kernel" and hit 'e' again. Remove "splash" from the boot option and add "pci=nomsi nolapic noapic" and hit enter, you'll be taken to the previous screen. Press 'b' to boot.

3) Hopefully Ubuntu should boot normally. After it does open a console version and use the following command
```
sudo nano /boot/grub/menu.lst
```
You will be prompted for your password, enter it and go to the very bottom of the the editor to the lines 
```

title           Ubuntu 8.10, kernel 2.6.27-7-server
uuid            1eeed980-8f03-4647-8115-94224929bca9...
kernel          /boot/vmlinuz-2.6.27-7-server...
initrd          /boot/initrd.img-2.6.27-7-server...
```
Note: Title will differ depending on your version

For the line that begins with "kernel" go to the end, remove "splash" and again add "pci=nomsi nolapic noapic" to the line. Hit Ctrl+X to exit, you will be prompted to save, say yes and you're done.

Reboot to test, hopefully you boot up just fine. 

Thanks for the help gogereaver in the Ubuntu channel on IRC and I also used [this]("http://ilikeubuntu.blogspot.com/2008/11/installing-ubuntu-810-on-laptop-with.html") blog post to get me going.

Again if I've made any errors in my assumptions about the problem or my solution is over-kill in some way add to this thread.

same result diff aproaches I hit esc to get into the text based loader then use "live-install pci=nomsi" and all went fine from there to include grub setting up the dual boot with my windows drive flawlessly

But thanks anyways for the help :popcorn:

---

### Post by swerve121 on 2009-12-06
Thanks worked flawless. I been up all night trying to do this. But im using 9.1 and none of the words are there anymore. If someone could help me out with this problem

---

