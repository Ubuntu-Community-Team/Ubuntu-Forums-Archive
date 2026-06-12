---
title: "Please Help With Dual Booting: NO MSFT !   /   e.g. Boot: &quot;Linux1 or Linux2&quot;"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by Ronok on 2009-02-08
[SIZE="2"]hi I am new to linux
Please Help me With [B]Dual Booting: Just 2 different Linux OS 
& NO MSFT ![/B] not anywhere in my computer, [SIZE="1"]or even in my house...[/SIZE]
**e.g. Boot: "Linux-OS-type1 or Linux-OS-type2"**

**my current condition:**
**I have 2 hard Disks**, 1st for OS 2nd for Data
**I have UBUNTU 8.10 installed** 2 months Now like it and want to Keep it 
and now want to **add openSUSE 11.1 and have a Dual Boot**
I have on CD/DVD Disk: Ubuntu 8.04, openSUSE 11.1[/SIZE]

I could follow "step by step" for the best way to do it
but I would rather not regress back to Ubuntu 8.04
lost time in getting back packets, upgrades, 
just want to add openSUSE 11.1 and then have Dual Boot Choice

(Below is how I have Partitioned my Disks)

[SIZE="1"](although there are over "1,070,000 Results" for "ubuntu dual boot"
in google 99% of them are "Linux+MSFT", I want "Linux+Linux"
maybe "Linux+openBSD/PCBSD" But never anything to do with MSFT
this is frustrating and like looking for good instructions in a Haystack) [/SIZE]

and since I am a beginner, 
[SIZE="1"]trying to adapt things in the Code that were ment for "Linux+MSFT" dual boot instructions 
and infer what it might be for "Linux+Linux" as well as specialized terminology, is understandably beyond me or other people at my level
I really need a "Linux+Linux" Dual Boot step by step 
I know it is "hold my hand-ish" and takes time out of someones day,[/SIZE]
But I know it would benefit a everyone afterwards
and I would be grateful !


**Filesystem**       Size:  Used: Avail: Type: Mounted on:  What For:
**Disk1** = 500GB for OS

/dev/sda1         20G  173M   19G  ext3  /media/disk-2  (future Linux-OS)
/dev/sda2        404G  7.6G  377G  ext3  /               **UBUNTU 8.10**
/dev/sda3         33G  177M   32G  ext3  /media/disk-1  (future Linux-OS)
/dev/sda4        5.8G    -     -     -   (extended)          -
     /dev/sda5   5.8G    -     -     -   (Swap)              -

**Disk2** = 1TB for Data
/dev/sdb1        867G   90G  733G  ext3  /media/ShuJu    My Data
/dev/sdb2        5.8G    -     -     -   (extended)          -
     /dev/sdb5   5.8G    -     -     -   (Swap)              -
/dev/sdb3         50G  180M   48G  ext3  /media/disk    (future Linux-OS)


I believe in trying **to be** that change that I want to see in the world
I want to Promote Linux / **Ubuntu**
I want to Learn, (so I can show people)
but I am just beginning
Thank you kindly 
Ronok

[http://www.gongkuo.com/electrical_division.htm]("http://www.gongkuo.com/electrical_division.htm")

---

### Post by yeats on 2009-02-09
If I'm understanding you correctly, you have Ubuntu 8.10 installed and you want to add a dual boot situation with OpenSUSE?  Even though the guides on the web are for MS/Linux combinations, they should still be useful.  Since your issues seem to be more OpenSUSE related than Ubuntu-related, have you tried an OpenSUSE forum?  I don't know OpenSUSE's installer at all (certainly not well enough to advise ...).

---

### Post by captain_conrad on 2009-02-15
hey

im also brand new to ubuntu and loving it to the MAX!
 
I have a dual boot with vista and ubuntu

i have no idea how it was done, a friend set my laptop up for me

but my advice to you is to look up one thing that my friend used

its called SGD or Super GRUB disk

GRUB means grand unified bootloader. I have no idea how it works but i have a super grub disk that my mate burned for me, and it had saved my life countless times because my vista has crashed so many times its ridiculous.

There must be threads here on the forums somewhere about SGD so u can look at them, just search it.

BASICALLY what this disk does is that whenever you start up your pc with this disk in it, the pc then gives you a list of things/places of where/what to boot from, like hard drive one or two or usb or cd or whatever.

and it can be installed so that u do not need to use the CD every time. (but holy moly i have no idea how)

When i switch my pc on, it shows me a list of things i can boot. My Ubuntu is the default highlighted entry and if i leave it for ten seconds it automatically boots that. If however i want my windows i just scroll down to my windows option and it boots windows.

Well this is my understanding of SGD. All i know is that it is an extremely powerfull and usefull tool. And it saved my ****, bigtime. Im an AutoCAD student (windows) and my vista on my laptop crashed an hour before an exam, and i managed to fix it using SuperGrubDisk, with a short call to my mate who gave it to me (and set up my whole dual boot on my pc). Thank goodness...

Best of luck, i hope this is somehow usefull???

peace

---

