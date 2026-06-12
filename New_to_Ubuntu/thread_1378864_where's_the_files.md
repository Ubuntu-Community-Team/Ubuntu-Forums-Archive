---
title: "where's the files?"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by onyxvu on 2010-01-11
First i would like to apologize if this is somewhere else but i am extremely new here. i am dual booting on a 10+ year old computer with xp pro. i had to get a partitioning program just to partition the hard drive and install xubuntu 9.10. so now i would like to format the partition with windows on it- but..... where the heck is it?? HELP!!

---

### Post by gfunkera on 2010-01-11
have you tried using fdisk or gparted?

---

### Post by bcn17 on 2010-01-12
Type the command:

>sudo fdisk -l

Then paste the output. It has information for every harddisk and partition.

---

### Post by onyxvu on 2010-01-12
so i access this in command prompt? i am only used to the graphical display of files, this is very new to me. The only way i can view (c:/ in this case) is in command prompt? is it called command prompt or something else? thanks for any replies...
 
just to clarify- i am trying to access/view the windows partition from xubuntu. i have already quickly reviewed the starter guide but i didn't see it mentioned any where. i did see the drives (floppy, disk, usb) are accessed from the \media file. right?

---

### Post by halitech on 2010-01-12
normally most help you will get here will be done via the terminal (also known as the CLI, similiar to windows command prompt) because that way the instructions will be pretty much the same no matter if you are running ubuntu, kubuntu or Xubuntu. 

you won't actually see the files using ```
sudo fdisk -l
``` but it will tell us what partitions you have and assist us in helping you in hopefully finding your files.

When you boot up, do you still get the option to boot into windows?

---

### Post by onyxvu on 2010-01-12
yes, i am still able to boot into windows but i am looking to format that partition to be rid of windows but i am still "testing the waters". i was going to do it the other night but i couldn't find the files which has made me more leary. it's definitely different...  where do i access CLI from? i'm not in front of the computer now or i would look myself. i am not very familiar with command prompt, is there any other way of finding this info?

---

### Post by halitech on 2010-01-12
I believe the terminal is under Accessories - Terminal but I'm using a modified install with XFCE so my menus are a little different.

There are other ways but if we give you gui instructions, then it means you have to type things out in order to give us the info that will help us help you.

---

### Post by onyxvu on 2010-01-12
you mean info as far as my setup? i can provide whatever info you need or maybe you could give me a link to where this is explained (preferrably with pictures :D) i would like to learn this for myself but i REALLY appreciate your help.

---

### Post by halitech on 2010-01-12
right now we are just concerned with your drives and the partitions on them. easiest (I know you don't believe me right now on this but trust me, it is) is to open a terminal and run
```
sudo fdisk -l
```
then you can copy and paste from the terminal to here the same as you would in windows.

---

### Post by onyxvu on 2010-01-12
when you say: "then you can copy and paste from the terminal to here" do you mean post the results on this forum or to a "notepad" or someplace to keep for myself to reference? i assume this is sort of a toc (table of contents) command?

---

### Post by halitech on 2010-01-12
I mean post them here so we can help you with your original question

here is what mine looks like with 3 hard drives and a DVD burner

> daryl@debian:~$ sudo fdisk -l
[sudo] password for daryl: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd7bbb99b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3647    29294496   83  Linux
/dev/sda2            3648       19209   125001765   83  Linux
/dev/sda3           19210       19457     1992060   82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00051741

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         668     5365678+   7  HPFS/NTFS
/dev/sdb2             669       38913   307202962+  83  Linux

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd6e0d6e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       24321   195358401   83  Linux
daryl@debian:~$ 


---

### Post by warfacegod on 2010-01-12
If you would prefer a GUI:

Go to System> Admin.> Synaptic Package Manager> search *gparted*>right click it and mark for installation> click apply

---

### Post by onyxvu on 2010-01-12
i will try both later tonight- thank you all.

---

