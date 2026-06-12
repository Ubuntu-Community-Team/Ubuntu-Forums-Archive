---
title: "what is embelm,why device has strange names"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by Adi100 on 2009-10-28
hello to all,

I searched, could not find the answers:

1- what are embelms are they keyword or tags just a fancy reminder type icon.
    when i inserted a infected USB disk with autorun on it it showed emblem as no write does this mean Read only.

2- why disks and devices have strange names( no offence here, if it so let it be so),kindly point me to a sutable article for reading on these devices.

3- kindly point me  to booting process of linux( this is best method to learn OS)

4-I have liitle exposure however linux gives a feel of collection of very very large nos of   programs.

More qustions in next post

regards

Adi

---

### Post by dsprenkels on 2009-10-28
Hello,

I wouldn't consider myself as an Ubuntu expert, but I have some answers:


[LIST=1]
[*]Emblems are fancyreminder type icons. However, these can be used by programs to indicate them. Nautilus automaticly indicates read-only and no-read files and directories; Dropbox (a closed-source program) also uses these icons to indicate the status of files.
[*]Disks and devices have strange names? Well, the devices system is other than in windows. In Ubuntu, you have all the devices listed in /dev (They're a lot of them.) These names are pretty cryptic. /dev/sda - first hard disk; /dev/sda1 - first partition of first hard disk. The cdrom devices are listed here as well. Then you can mount them. With USB-drives and cdrom this happens automaticly. They're almost always mounted in /media. A cdrom could be mounted at /media/cdrom0. A USB-drive would be mounted at /media/(drive-name). Then you'll see them on your desktop with their names. I see my USB drive as PLUTONIA (that's how I called it). I wouldn't know how they have strange names. (Sorry, I couldn't find an article.)
[*]Don't ask me.
[*]Everyone is welcome to add a program. That's why tere are so many. Just try them. Installing is only a few seconds. (Sorry if this answer is crap, I don't know what exposure means...)
[/LIST]

---

### Post by martrn on 2009-10-28
1. No. No write usually means you the users has no permission to write.

2. Everything in linux is a file for example /dev/ram0 is your memory  /dev/lp0 is your printer /dev/hda  is the first hard disc etc...ect... This only gets complicated if you limited a system to say the letters of the aplphabet, thats were things get confusing.
[http://www.oracle.com/technology/pub/articles/calish_filesys.html]("http://www.oracle.com/technology/pub/articles/calish_filesys.html")

3. You don't ned to know about the boot process (not everyone does) in order to use a gnu/linux system such as ubuntu.  But in any case :-
[http://linuxbasics.org/tutorials/during/booting]("http://linuxbasics.org/tutorials/during/booting")
[http://wiki.freegeek.org/index.php/The_Linux_Boot_Sequence]("http://wiki.freegeek.org/index.php/The_Linux_Boot_Sequence")

4.  Ubuntu uses the apt (advanced packing tool) as a method of storing and distribution is programs and libaries.  It is A++

---

### Post by sandyd on 2009-10-28
> **Adi100 said:**
> hello to all,
 
I searched, could not find the answers:
 
1- what are embelms are they keyword or tags just a fancy reminder type icon.
when i inserted a infected USB disk with autorun on it it showed emblem as no write does this mean Read only.
 
2- why disks and devices have strange names( no offence here, if it so let it be so),kindly point me to a sutable article for reading on these devices.
 
3- kindly point me to booting process of linux( this is best method to learn OS)
 
4-I have liitle exposure however linux gives a feel of collection of very very large nos of programs.
 
More qustions in next post
 
regards
 
Adi
 
 
1. You can type "gksudo nautilus" then navigate to /media/disk to gain write support
2. Their named according to their type. for example, some usb devices show up as usb0, usb1, usb2... .etc .etc

---

### Post by undecim on 2009-10-28
1: I'm pretty sure emblems are just keywords/tags that you can use as reminders for yourself.

2: are you referring to the device names (i.e. /dev/sda) or drive labels (i.e. "disk")?

With Linux, one of the ways things are kept simple as that everything is a file. When you mount, for example, /dev/sdb1 to /media/disk, you are telling the kernel to look at the special file /dev/sda for information regarding to contents of the folder /media/disk.

This is convenient because we can also mount drive "images" as filesystems (for example, you can mount an .iso file as a CD-ROM drive)

There is also UUID (which Ubuntu uses a lot), which is a unique number that doesn't change even if the number or order of the physical drives change. This keeps you from having to rewrite fstab everytime you add a hard drive (sometimes even including removable drives)

If you are talking about the labels and mount points, the default name is "disk" followed by "disk-1", "disk-2", etc.

3: There is a lot to the Linux boot process. There is Grub to load the kernel and basic files needed before disks are used. Then there are initrd scripts that mount filesystems, and then there are the boot scripts that are different for most Linux distributions.

I found a good article on this here: [http://www.ibm.com/developerworks/library/l-linuxboot/index.html](http://www.ibm.com/developerworks/library/l-linuxboot/index.html)

4: I'm afraid I don't completely understand this question. (is it a question?) Linux is comprised mostly of very many small programs and libraries, each of which are meant to do one thing, and do it well.

This makes it easy to write scripts (i.e. you can write a script to just make several programs or libraries work together to perform one complex task), and so there are lots of alternative programs you use for most anything

---

### Post by Adi100 on 2009-10-29
Thank you undecem,carlee and martn for answering and giving important links.

[quote=Adi100;8181332]
4-I have liitle exposure however linux gives a feel of collection of very very large nos of   programs.

Actually my meaning was I am totally new to linux ( sorry for bad english0

regards

Adi

---

