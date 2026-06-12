---
title: "How do I create a raw image file from a HD and restore it?"
date: 2010-08-11
forum: New to Ubuntu
---

### Post by tabcom on 2010-08-11
I've began my new experience into ubuntu world \\:D/with a specific need . . . 

How do I create a raw image file of a lap top hd that is HP-UNIX in format plugged in via a usb adapter cable to my computer --> saved to a usb memory stick. 

After that is completed, I want to disk copy the image file back to another laptop hd. 

1. How do I **view** the laptop hd and the usb drive that the raw data file is to be transferred to?

2. How do I **create** a new image from the laptop HD to USB.

3. How do I **restore** the new image from the USB to a different HD.

If there are common 'how to' links available, that would be of great benefit to me.

Looking forward to having fun with this project!!

---

### Post by mapes12 on 2010-08-11
Remastersys
Partimage
Clonezilla
FSarchiver

to name a few. Google will find them.

---

### Post by tabcom on 2010-08-12
Having researched the software list provided, I tried clonezilla because it created a boot disk to clone images. During the process of setting parameters, clonezilla would recognize both of my hard drive. The problem is that the source disk is **vfat**. 

So, I'm looking for a cloning application that will clone in **vfat**.

---

### Post by earthpigg on 2010-08-12
what about using [dd]("http://en.wikipedia.org/wiki/Dd_%28Unix%29") on the laptop itself, from within HP-UX?

or dd from within an ubuntu live cd on the laptop? dd doesn't need to recognize the data in order to be able to create an image. once upon a time, before linux could read NTFS, people where using DD to clone Windows NT/XP volumes without being able to actually understand any of the data on the volume that was being cloned. dd just copies the ones and zeros, essentially. :P

you said 'raw', and it doesn't get much more raw than that. note that if the hard drive is 60gb, the image created may just end up being 60gb.

---

### Post by dcollier on 2010-08-12
I have found that if clonezilla doesn't work, try using ping, which is a different cloning open source software.

---

### Post by tabcom on 2010-08-12
At the ubuntu desktop, I can see my 2 drives. The source drive is sdc. The designation drive is sdb4.

Is there a terminal command to copy the raw data of sdc (vfat) to sdb4 (fat) and make sdb4 a vfat drive?

---

### Post by tabcom on 2010-08-12
Thanks for the suggestion to use dd.

At the ubuntu desktop, I can see my 2 drives. The source drive is sdc. The designation drive is sdb4.
 
 sdc (vfat)  sdb4 (fat) I want sdb4 to become a vfat drive after copying the sdc drive.

Not being nimble with the terminal keystrokes, do I enter the command at the root directory?
 
 When I open a terminal window, I get a ubuntu@ubuntu:~$ prompt.

It looks like I need to run:[FONT=Verdana]
    
  [/FONT]**dd if=/dev/sdc of=/dev/sdb5 bs=4096 conv=noerror**[B]
  
where on the command prompt do I run the command?
  

[/B]

---

### Post by earthpigg on 2010-08-12
it doesn't matter where you run it. the paths are specified in the command.

---

### Post by tabcom on 2010-08-13
OK -- I ran the dd command successfully. 

Results:

File copied successfully: deva.cor.e 

One thing that concerns me is that the cloned drive is still FAT.
The source drive was a VFAT.

Do I need to format the clone to VFAT and then re-run the dd command?

---

### Post by tabcom on 2010-08-13
Answering my own question (maybe):

unmount the drive.

sudo mkfs.vfat /dev/sdb4

---

### Post by mapes12 on 2010-08-14
From what I've read via Google, VFAT and FAT are the same thing. It appears to be a naming convention thing.

---

### Post by tabcom on 2010-08-14
VFAT and FAT may very well be the same.

I ran the dd command, as suggested, and it did copy the one file that was on the source drive.

I wonder why the Disk Utility window recognizes one drive (source) as VFAT and the target drive FAT (even after I ran sudo mkfs.vfat /dev/sdb4 )?

---

