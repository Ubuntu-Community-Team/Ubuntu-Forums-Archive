---
title: "Help with GParted for installation"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by annie227 on 2009-11-17
Hi,
I recently uninstalled Karmic as I was having issues(mainly with kINO and kdenlive and burning) and being newish I decided to revert to 9.04 until I was more confident.
On reflection I've decided I'd like to now triple boot XP,Jaunty and karmic,working out the problems with karmic as I continue being able to work successfully with 9.04.
I find partitions and installation quite a challenge when things like this occur
;
I can't delete that little slice between sda1 and sda6 which appeared after an aborted reinstallation attempt of Karmic.
When I first popped in the disk the 3 OS's were going to be side by side but I pulled the slider back just a little on XP,sda1 to give karmic  more space and then aborted that appeared and I want to delete it and start again.
I hope that's clear enough,thanks
edit-oh,darn,how do i insert the screenshot(I've done it once before)?

---

### Post by pootan on 2009-11-18
Unfortunately without a screenshot noone can give you much advice. If you scroll the page down when you edit your post or write a new message you will see Additional Options you will see Attach Files. 

Click the text box that says Manage Attachments and you should be able to upload a screen shot as long as it matches one of the supported formats.

---

### Post by ranch hand on 2009-11-18
A screen shot of gparted (full screen gparted) would be nice.

What would be more helpful, perhaps is the result of;
```

sudo fsdisk -l

```
that is a lower case L at the end there.

Here is mine for my 2 internals;
```

jak@jak-desktop:~$ sudo sfdisk -l
[sudo] password for jak: 

Disk /dev/sda: 38913 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0+   4697    4698-  37736653+  83  Linux
/dev/sda2      24583   38912   14330  115105725    5  Extended
/dev/sda3      18209   24582    6374   51199155   83  Linux
/dev/sda4       4698   18208   13511  108527107+  83  Linux
/dev/sda5      37777+  38912    1136-   9124888+  82  Linux swap / Solaris
/dev/sda6      24583+  26482    1900-  15261687   83  Linux
/dev/sda7      26483+  31609    5127-  41182596   83  Linux
/dev/sda8   *  31610+  32916    1307-  10498446   83  Linux
/dev/sda9      32917+  37776    4860-  39037918+  83  Linux

Disk /dev/sdb: 38913 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdb1   *      0+  38912   38913- 312568641    5  Extended
/dev/sdb2          0       -       0          0    0  Empty
/dev/sdb3          0       -       0          0    0  Empty
/dev/sdb4          0       -       0          0    0  Empty
/dev/sdb5      38276+  38912     637-   5116671   82  Linux swap / Solaris
/dev/sdb6      31846+  38275    6430-  51648943+  83  Linux
/dev/sdb7      29298+  31845    2548-  20466778+  83  Linux
/dev/sdb8      22911+  29297    6387-  51303546   83  Linux
/dev/sdb9      20482+  22910    2429-  19510911   83  Linux
/dev/sdb10      3769+  20481   16713- 134247141   83  Linux
/dev/sdb11         0+   3768    3769-  30274398   83  Linux
jak@jak-desktop:~$ 

```

---

### Post by annie227 on 2009-11-18
I pasted that command in the terminal and
computer@computer-desktop:~$ sudo fsdisk -l
sudo: fsdisk: command not found
computer@computer-desktop:~$ 
was the result-still trying to work out why-with the s/shot

---

### Post by annie227 on 2009-11-18
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2dbb671e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15282   122752633+   7  HPFS/NTFS
/dev/sda2           15283       30237   120126037+   5  Extended
/dev/sda3           30238       60801   245505330    7  HPFS/NTFS
/dev/sda5           15283       15291       72261    7  HPFS/NTFS
/dev/sda6           15292       29624   115129791   83  Linux
/dev/sda7           29625       30237     4923891   82  Linux swap / Solaris
computer@computer-desktop:~$ 
the sda1 is XP,sda3 is a storage partition,sda6 is Jaunty,
hope that helps


there-it's saying the s/shot is an invalid image when I try to upload it btw

---

### Post by kansasnoob on 2009-11-18
To take a screen-shot go to Accessories > Screen-shot. Save it Desktop or wherever, then click on the paper clip thingy.

See mine:[ATTACH]136686[/ATTACH]

Mouse pointer is on the spot. In the pop-up click on Browse, select Desktop or location of saved screenshot. That will show a list of available objects, double click the right one. Then click on upload. Then click on the paper clip thingy again. It should be listed there, so just click it.

When done select Preview Post to see if it's right.

---

