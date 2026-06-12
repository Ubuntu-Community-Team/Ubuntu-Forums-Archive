---
title: "Quad Booting"
date: 2010-02-26
forum: New to Ubuntu
---

### Post by Indian_Guy101 on 2010-02-26
Hello,
I have a computer with Ubuntu 8.04 installed on a single SATA harddrive. I have three extra SATA harddrives, and I would like to install another OS on each. My goal is to be able to quadboot Ubuntu 8.04, Windows XP Pro, Mac OS X86 10.4.8 Tiger, and Excelixis ( a variant of Xubuntu), with each OS on a separate SATA harddrive. I do not want to reformat my current Ubuntu 8.04 harddrive. How would I go about doing this? I do not have an understanding of how bootloaders work.
Thanks.

---

### Post by captain_171 on 2010-02-26
This is how I use to dual boot with more then one drive.
I disconnected all the drives that I was not using so I did not have to worry about destroying them but remember what port on the board that drive was plugged into such as SATA 0 or PATA 0 Master because this can mess things up later.
Then install the OS you want to use on that one drive.
From that point on you just connect that drive when you want to boot.
If you want to add all the drives is when it become a bit more interesting the way I would do it is after you have all the OS's installed. Then connect them and set the BIOS to boot using one of the Linux drives. Then make sure Linux can see all the drives make note on where each drive is such as /dev/sda or /dev/sdb then you will need to configure that /boot/grub/menu.lst and add each OS to that file if you need more help doing that just ask.

---

### Post by johngreth on 2010-02-26
If you have grub2 installed you can let the computer automatically discover the other operating systems by typing
```
sudo update-grub
```
This is a lot easier than trying to figure out menu.1st.

This might also help: [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

Also, is your computer a mac? If so, you might want to use mac's boot loader instead of grub. If not, it's going to be nearly impossible if not totally impossible to get Tiger running. Mac is very protective about it's software.

---

### Post by egalvan on 2010-02-26
This gentleman installed a "few" more than you...
maybe you can pick up some pointers :)

*How to install and boot **145 operating systems** in a PC*


[http://www.justlinux.com/forum/showthread.php?t=147959](http://www.justlinux.com/forum/showthread.php?t=147959)

---

### Post by oldfred on 2010-02-27
You can unplug drives with windows and get it working again. Other systems may all install as drive 0 and then have issues multibooting if all are plugged in. It is better to leave all drives plugged in and in BIOS select the drive you want to install to as the default boot, so grub or the bootloader is in that drives MBR.
I liked and reviewed the saikee post and set up a grub partiiton for booting and that works great with grub legacy. Grub2 is very good at finding other systems, but does not like to be installed to a partition. With multiple drives you can have every MBR with a different  boot loader and chainboot to each.

[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_)
[http://www.troubleshooters.com/linux/grub/grubpartition.htm](http://www.troubleshooters.com/linux/grub/grubpartition.htm)

---

### Post by Mark Phelps on 2010-02-28
> **oldfred said:**
> ... Grub2 is very good at finding other systems, ...
+1 My experience (on my multiboot, multiOS machine) exactly ...

> With multiple drives you can have every MBR with a different  boot loader and chainboot to each.

Again, excellent choice. This allows you to boot drives individually should you need to do repairs or recoveries -- with NO risk to the other installed OSs.

Just boot from an Ubuntu-installed drive (with GRUB2 installed to it), open a terminal, type "sudo update-grub" -- and it should find all the other OSs.

---

### Post by themusicalduck on 2010-02-28
I have OSX installed on my PC with the chameleon bootloader. Currently grub2 chainload it properly.. Funnily enough, it used to do it fine until it was updated a little while ago. It might work with a different bootloader for OSX or if you just put something like chameleon instead of grub, but I don't know much about it. If I want to boot into OSX at the moment, I need to make a bootable pen drive with chameleon on it and boot from that.

I think grub 1 does boot it properly though. You just have to point it to the right partition in menu.lst

---

### Post by Indian_Guy101 on 2010-04-14
Thank you everyone for your inputs. I am sorry about the late response as I have been very busy (school and all) I recently took out my Ubuntu harddrive and put in another one on which i installed WIndows XP. Then the thing is, the XP harddrive wouldn't boot. Stupid WIndows.

---

