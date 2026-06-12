---
title: "I have just installed ubuntu and wish to remove windows xp pro"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by glennlad on 2009-01-18
I downloaded the ISO and mounted it in windows, ubuntu is installed successfully but I didn't get the option to wipe over the partition or make a new one etc. I want to remove windows XP completely from the hard drive and boot screen. Without having to reinstall ubuntu. 

I think windows and ubuntu are on the same partition. 
Does anyone know if and how I can remove windows from the partition without touching or reinstalling ubuntu?

Thanks in advance.

---

### Post by Dumbestcrayon on 2009-01-18
Windows and Ubuntu can't be on the same partition. 

If you want to remove Windows you can try and format the partition that its on. This will cause you to lose everything on that partition, Its probably NTFS. 

Your Ubuntu should be on ext3 or ext2.

If you know what you're doing with a partition editor use this.

```
sudo apt-get install gparted
```

I haven't used gparted but there should be an option to delete the NTFS (windows) partition.

---

### Post by glennlad on 2009-01-18
That went straight over my head to be honest with you, 
how do i find out what ext its on?
I go into the file system and windows is under host, what does that mean?

sorry I'm not to good on computers

---

### Post by Dumbestcrayon on 2009-01-18
Okay if you're not really good with this and don't understand then its probably not a good idea to be messing around with a partition manager. If you do something wrong then its very possible to mess something up and you won't be able to boot anything at all.

The basic way to do it is..

Open gparted. (open terminal and type... sudo gparted)

Look for your windows partition (it should be labeled NTFS) Right click on it and click unmount (may not have to do this but try it anyways) then click delete at the top of the window.

BEFORE you do any of this make sure you take everything off of the partition and move it to ubuntu. 


If this does not work exactly like this don't do anyting else. Come back here and ask questions because, like I said, Its very easy to mess something up with a partition manager.

---

### Post by talsemgeest on 2009-01-18
> **glennlad said:**
> That went straight over my head to be honest with you, 
how do i find out what ext its on?
I go into the file system and windows is under host, what does that mean?

sorry I'm not to good on computers
Ok, you install gparted, using the command DumbestCrayon gave you. You open it with System>Administration>Partition Editor and then delete your windows xp partition. It should be labled "NTFS". Just make sure that you don't delete anything labled as EXT3 or SWAP, since they are for ubuntu. After that you should be able to resize your Ubuntu partition to take up the free space left by the xp partition.

Take a look at the partition program, and this *should* make sense.

---

### Post by glennlad on 2009-01-18
OK thanks, 2 questions

1.) how do you install gparted? I've downloaded the files and i dunno what to do now.

2.) on the the system > administration tab I have an option that says Install  this system permanently to your hard drive, thought i had already done that?

---

### Post by theozzlives on 2009-01-18
> **glennlad said:**
> OK thanks, 2 questions

1.) how do you install gparted? I've downloaded the files and i dunno what to do now.

2.) on the the system > administration tab I have an option that says Install  this system permanently to your hard drive, thought i had already done that?

I think you installed using WUBI, under Windows. When you boot do you see GRUB, or Windows Boot Menu?

---

### Post by Montblanc_Kupo on 2009-01-18
In laymans terms... did you install Ubuntu from INSIDE windows? If so... you need to start over and boot from the Ubuntu CD rather than put it into the computer while windows is running. If you do that and click the "install" choice... it will allow you to wipe out windows completely by just using the installer... and you won't need to worry about the instructions that they're giving you.

---

### Post by Elfy on 2009-01-18
Sounds to me like you installed wubi - ubuntu inside wubi - to make that a standalone install is possible, but probably easiest to start again.

If you want to remove windows completely the easiest option is to use the "install to whole disk option" This will remove _anything_ you had on the disk.

IF ubuntu is in the windows add/remove then that is what you have done, if that is definitely the case you need to boot with the livecd.

I would check how you have it set up - if people think it's not wubi the ways to deal with it are completely different.

---

### Post by glennlad on 2009-01-18
Oh so I've integrated this into windows?
I will wipe it off and start again when I have a new disc to burn to.

Thank you for your help

---

### Post by chuuk on 2009-01-18
> **glennlad said:**
> 
how do i find out what ext its on?


Just a quick note about file systems. A file system is a method by which a computer organises the files on your computer. Much like how you can arrange books on your shelf differently, according to height, colour, etc. Some file systems will give you faster access times to files on your disk (apart from other advantages).

XP partitions usually will be using the NTFS file system to store files. Newer Linux systems are usually using the Ext3 or Ext4 system. While Linux can read/write to the NTFS file system, Windows can't write to Ext systems without modification.

---

### Post by Elfy on 2009-01-18
> **glennlad said:**
> Oh so I've integrated this into windows?
I will wipe it off and start again when I have a new disc to burn to.

Thank you for your help

Ok - make sure that you have set your bios to boot from cd first, burn the download as an iso and it will boot.

IF you don't need anything kept then it will be straightforward to install it.

Good luck:)

---

### Post by glennlad on 2009-01-18
thank you :)

i just had a little brainwave; what would happen if I mount ubuntu ISO while im logged onto to my current ubuntu installation?

---

### Post by theozzlives on 2009-01-18
You NEED a CD.

---

### Post by egalvan on 2009-01-18
> **theozzlives said:**
> You NEED a **CD**.

Technically ( depending on your level of expertise )
this is NOT true.

It is possible to install Linux without a CD.

All you really NEED is a way to boot the machine (floppy, PXE NIC, hard drive, etc)
and a way to access the rest of the system (local CD/DVD or hard drive, network accessed CD/DVD or hard drive, or USB device).

But yes, a CD is probably the EASIEST, especially for a newcomer to the Linux world (or the computer world in general).

---

### Post by Elfy on 2009-01-18
indeed I got sidetracked - you can do it, but I would prefer to do it with a cd myslef

[https://help.ubuntu.com/community/Installation#Installation](https://help.ubuntu.com/community/Installation#Installation) without a CD

---

### Post by Dumbestcrayon on 2009-01-18
> **egalvan said:**
> Technically ( depending on your level of expertise )
this is NOT true.

It is possible to install Linux without a CD.

All you really NEED is a way to boot the machine (floppy, PXE NIC, hard drive, etc)
and a way to access the rest of the system (local CD/DVD or hard drive, network accessed CD/DVD or hard drive, or USB device).

But yes, a CD is probably the EASIEST, especially for a newcomer to the Linux world (or the computer world in general).


If you're being 'technical' about it. He already said he wasn't good with computers. Some of us can do it this way but we don't need to get that deep into it with him. He can just do it the easy way and learn all of that stuff later.

The best way to get the CD is to get the torrent. Its MUCH faster. The torrent link is on the Ubuntu website. 

[http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)

get this one for easiest install..

ubuntu-8.10-desktop-i386.iso.torrent (for 32 bit)

---

### Post by Montblanc_Kupo on 2009-01-18
> **dumbestcrayon said:**
> if you're being 'technical' about it. He already said he wasn't good with computers. Some of us can do it this way but we don't need to get that deep into it with him. He can just do it the easy way and learn all of that stuff later.

+1

---

### Post by glennlad on 2009-01-19
Its hard enough with a CD lol, I've downloaded the iso, burnt it to disc, booted from disc, i get the splash page, then the options;

1.try ubuntu without touching current system
2.install
3.driver update live cd
4.boot from 1st hard disk.

I pressed 2 as i want to completly wipe off windows, then i will get the ubuntu text at the top with a orange bar at the bottom that goes back and forth. 
Then my screen will go blank, and text apperead i cant remember what it said but it began with numbers for example [45.7754.778] then it went through loads of them then at the end it said "stop trace" or something on the lines of that.

To be honest this is doing my head in, i'm going to try the alternative cd see if that will work and if not then I will stick with windows. :(

---

