---
title: "Deleting hardrive space on windows doesnt reflect on ubuntu?"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by radamez85 on 2009-12-20
So i just deleted about 50gbs worth of space on windows..but it doesnt reflect on ubuntu..How do I get the space that shows in my 'disk utility' to actually relfect on ubuntu, as in usable to me ?

---

### Post by muse3332 on 2009-12-20
so basicly you want to transfer the space that ur using with windows and give some or all to linux?

---

### Post by radamez85 on 2009-12-20
Alll of the unused space. Heres a screenshot i took, lemme know if this helps. <3 
[http://c4.ac-images.myspacecdn.com/images02/142/l_2866ed844bee4262a399dd4e203c4b17.png]("http://c4.ac-images.myspacecdn.com/images02/142/l_2866ed844bee4262a399dd4e203c4b17.png")

---

### Post by radamez85 on 2009-12-20
im sorry this is a much better size of the screenshot of my desktop.

[http://img69.imageshack.us/img69/3021/helpp.png]("http://img69.imageshack.us/img69/3021/helpp.png")

---

### Post by muse3332 on 2009-12-20
ok this is what you have to do there is a program called ubuntu one use that to back up all your files then put in a clean install then select "use up intire disk" this is the best way to not damdger ur hard disks  this si my desktop pretty neat right?

---

### Post by radamez85 on 2009-12-20
thats slick bro!
but it says i already have ubuntu one installed..
is this a reinstall of the entire ubuntu OS and removal of windows ?

tad confused, my apologies.

---

### Post by muse3332 on 2009-12-20
well im sorry i wasnt thinking of that well basicly ur gonna do a clean install of the ubuntu only.. and keep windows  the way it is or you could share the space between windows and ubuntu by unistalling ubuntu and installing it inside windows just put in the cd when windows is booted the select bot inside windows  the both share the same space BREAK THE BOUNDRIES! lol oh and yeah ubuntu one is supposed to be installed

---

### Post by Elfy on 2009-12-20
Hi - you don't need to reinstall anything. There are ways to get the space available in ubuntu. Wwe need some information though.

If you open a terminal from the Apps Accessories menu and run this command

```
sudo fdisk -l
```

Then we need to know if you want to use the space in both ubuntu and windows.

---

### Post by muse3332 on 2009-12-20
qoq forest piskie good thing you came -.- lol (friendly teasing) doh! i completely forgot about that! well lets work on this together we can help this lad

---

### Post by radamez85 on 2009-12-20
Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
radhamesjr@ubuntu:~$ 


I want all the space for ubuntu..
if possible i would like most of the space for ubuntu with some space on windows...

---

### Post by muse3332 on 2009-12-20
see forest! he wants all the space for ubuntu and some for windows "Hi - you don't need to reinstall anything" maybe he does.. lol (friendly teasing) :)

---

### Post by radamez85 on 2009-12-20
lol, i finished deleting a ton of stuff off of the windows side thinking it would transfer to ubuntu... theres like 40GBs of free space </3

---

### Post by Elfy on 2009-12-20
Run the whole command I gave you please - then give us the output. If you got that output you made a mistake in the syntax.

---

### Post by 3rdalbum on 2009-12-20
(personal facepalm, I didn't realise the poster was using Wubi...)

---

### Post by radamez85 on 2009-12-20
i typed in sudo fdisk -l

heres everything in the terminal please advise me if I typed some incorrectly. <3
its saying invalid but i typed in "sudo fdisk -1" as you said.

radhamesjr@ubuntu:~$ sudo fdisk -1
[sudo] password for radhamesjr: 
fdisk: invalid option -- '1'

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
radhamesjr@ubuntu:~$

---

### Post by Elfy on 2009-12-20
if it all goes horribly wrong - try pasting :)

that is a lower case L not a 1

---

### Post by radamez85 on 2009-12-20
hahah! L > 1 that was the problem =/ srry.

radhamesjr@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdcecdcec

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS
radhamesjr@ubuntu:~$

---

### Post by Elfy on 2009-12-20
Thanks - I assume that you have installed ubuntu with wubi.

What I would do as it would be the most simplest method would be to create a new ntfs partition in the space inside windows.

When you are using wubi the windows drives should be available in /hosts

When youa reusing wubi then resizing the disks is not wuite so simple you need to use something called LVPM.

You can create extra virtual disks, not something I have done though. Perhaps 2rd album would have more experience there.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20create%20a%20virtual%20disk%20in%20Ubuntu?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20create%20a%20virtual%20disk%20in%20Ubuntu?)

---

### Post by radamez85 on 2009-12-20
Thank you very much guys!
All is well for.
For future reference, i will be buying a new laptop. How can i get a ubuntu that stands alone, and avoid windows completely ?

---

### Post by 3rdalbum on 2009-12-20
> **radamez85 said:**
> Thank you very much guys!
All is well for.
For future reference, i will be buying a new laptop. How can i get a ubuntu that stands alone, and avoid windows completely ?

Set your computer's BIOS so the "boot order" or "boot sequence" starts with your CD or DVD drive. Insert the Ubuntu CD and start up the computer, and it will boot off the CD. At the first menu, choose "Install Ubuntu" and the system will load into RAM and run the installer.

Follow the prompts. At the screen where you can choose to erase a disk or resize a partition, choose the Resize option. Move the little slider in the bottom bar graph towards the left to resize Windows downwards and allocate space to Ubuntu.

Continue the installation and you're done!

---

### Post by Elfy on 2009-12-20
> How can i get a ubuntu that stands alone, and avoid windows completely ?

> At the screen where you can choose to erase a disk or resize a partition, choose the Resize option.Use the Whole Disk Option I would have thought.

---

