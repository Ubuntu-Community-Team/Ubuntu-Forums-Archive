---
title: "Vista and Ubuntu 9.04 on Fake Raid1+0"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by apco25 on 2009-05-12
[FONT=Calibri][SIZE=3]Hello,[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]In addition to the below I have tried installing 9.04 and 8.10 Alternate CDs.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]I am new to the Linux world so my understanding of the boot process is limited. I am trying to run a “quad Boot” system (I know it’s no different from a dual boot). I have 3 windows versions and am trying to add Ubuntu.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]I have read the following documents:[/SIZE][/FONT]
[[FONT=Calibri][SIZE=3]http://www.howtoforge.com/creating-a-dual-boot-system-on-raid10-ubuntu-windows[/SIZE][/FONT]]("http://www.howtoforge.com/creating-a-dual-boot-system-on-raid10-ubuntu-windows")
[FONT=Calibri][SIZE=3]and[/SIZE][/FONT]
[[FONT=Calibri][SIZE=3]https://help.ubuntu.com/community/FakeRaidHowto[/SIZE][/FONT]]("https://help.ubuntu.com/community/FakeRaidHowto")
[FONT=Calibri][SIZE=3]The bottom line is between the two docs, I am able to mount the other Windows Partitions in Linux via dmraid. R/W works and all.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]I was also able to install Ububtu on an extra 100GB partition. I however cannot boot into Ubuntu. I have it as a boot option, but it just locks up on boot.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Using the above as references I noticed a couple things:[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]1). After installing dmraid I still cannot see the RAID10. I have to supply the following commands:[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Sudo dmraid –r[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Sudo dmraid –ay[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]According to the docs I should be able to see the RAID10 partitions directly after the install without these commands.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]2). When doing the GRUB test for the (hd0) command to “find /boot/grub/stage1” it keeps saying file not found, even though I can see the file in that directory on my RAID10 Ubuntu 100GB partition.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]3). I have tried to edit the menu.lst file and change the (hd0,x) to several partitions (just guessing) and they all seem to see (hd0,0) no matter what I put in there.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]I am afraid even if I get the GRUB correct, it will still not boot as I cannot get the dmraid commands in so the bootloader sees the RAID10 before booting begins.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]How can I get it to boot properly?[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]I am using [/SIZE][/FONT]**[COLOR=black][FONT=Helvetica]Ubuntu 9.04 [/FONT][/COLOR]****[COLOR=black][FONT=Helvetica]Desktop. [/FONT][/COLOR]**[FONT=Calibri][SIZE=3]I have an Nvidia fake raid on a StrikerII extreme motherboard with 4 WD hard drives. It seems to support this RAID config since I can mount and see the partitions and I was able to complete the install. Maybe I am not putting the correct string in **[FONT=Calibri]/etc/initramfs-tools/modules? [/FONT]**Thanks for any help.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Apco25[/SIZE][/FONT]

---

### Post by apco25 on 2009-05-13
OK,
 
I have an update. I tried to get Grub to install. I cannot get it to fine the file after the commands:
 
(all in root mode)
mkdir /target
mount /dev/mapper/mapper/nvidia_fjejedge7 /target
mount --bind /dev/ /target/dev
mount -t proc proc /target/proc
mount -t sysfs sys /target/sys
chroot /target
 
installed (grub and dmraid) on the chroot /target
cp /usr/lib/grub/i386xx/* /boot/grub
 
I made sure the files for grub are now in the /target/boot/grub directory
 
grub
 
(now in grub terminal)
device (hd0) /dev/mapper/nvidia_fjejedge
(no errors after this command)
find /boot/grub/stage1
 
Then it cannot find the file (seems no matter what it do).
 
 
If I cannot find the file I cannot install the grub loader.
 
Is it just that I cannot get grub to work with RAID10 with Nvidia fakeraid? If not, should I submit a bug? Someone should know about this. I guess I will just stick with Windows, it actually works.
 
Apco25.

---

### Post by apco25 on 2009-05-13
Maybe I am in the wrong forum for this question. can someone at least suggest where I can ask this and get an answer?

---

