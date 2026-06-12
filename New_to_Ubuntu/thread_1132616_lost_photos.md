---
title: "lost photos"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by sekani on 2009-04-22
i have been trying to recover lost photos from a cdrom but still need some help.i have tried a few suggestions from readers but am stuck at this message....dean@dean-desktop:~$ sudo mount /dev/cdrom /mnt/cdrom -t iso9660 -o session=0 
mount: mount point /mnt/cdrom does not exist
dean@dean-desktop:~$ sudo mount /dev/cdrom /media/cdrom -t iso9660  -o session=0mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
can anyone tell me what to do next? thanks

---

### Post by Peter09 on 2009-04-22
Normally a CDrom will mount automatically, do you see it in the Places Menu? Do other CDroms mount automatically on your system?

---

### Post by Cresho on 2009-04-22
Try another cd player.

---

### Post by expatCM on 2009-04-22
run a lens cleaner?

---

### Post by sekani on 2009-04-22
i can see cdrom in ''places'. it comes up as 'Blank CD-RW disc' also other cd's do mount automatically

---

### Post by anaconda on 2009-04-22
> **expatCM said:**
> run a lens cleaner?

I broke my previous DVD-drive with a lens cleaner CD..  So be careful with it if you decide to go that way..

(it was my mistake though. didnt read the instructions THAT carefully and I did the cleaning for a few seconds too long..)

I think some rescue programs can search files from a cd that isn't mounted. Useful feature if the CD is so broken that it cant be mounted..

---

### Post by sekani on 2009-04-22
can you explain about 'lens cleaner'? this is the first time i have heard of it. how can it break the dvd drive?...thanks

---

### Post by expatCM on 2009-04-22
The lens cleaner I am referring to looks like a normal CD. However it has a small soft brush glued on at 90 degrees.  You run the CD a few times and it rotates.  The small brush passes over the lenses and removes any accumulated dust which will stop the laser from reading the CD / DVD media properly.

The cleaner should cost very little.

It is possible to manually clean the lenses but that is a pain ....

---

### Post by sekani on 2009-04-22
thanks for the lens cleaner explanation.i am not sure this will be the fix to the problem.this is the original post i submitted in feb........"i have tried to add some photos to a cd-rw that already had photos on it. the cd/dvd creator opened up automatically and i tried to write to disc but for some reason lost all the photos on the cd-rw! this is the first time i have used cd/dvd creator... i use ubuntu 8.10 and a dell inspiron 530s...have i lost the photos for good or can i retrieve them...i am guessing the problem is operator error,can anyone help?"

---

### Post by expatCM on 2009-04-22
I think you have to work this in steps.  Recovery of the photo's should be possible but you first need to work out what is the problem.

As a first step I would suggest that you take the media to another computer and see if it can be read there.  This will show whether the problem is with the media or the drive.

Depending on the outcome of the first step you will need to either do something about your drive or work on recovering the data from the media.

If you are to recover from the media there is a very effective program called PhotoRec (in the repositories) but it will only work if the media is good.  If you have a fundamental problem with the media then perhaps dvdisaster (in the repositories) will be able to help you recover generally what is on the media.

---

### Post by sekani on 2009-04-23
i have tried the disc with the photos missing in another computer that uses windows vista and it says that the disc is empty,702mb free....i then tried another cdrom with photos on it that works fine on vista in my computer with ubuntu and got this error message "DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken"...now i am more confused,it appears that i have two problems,one with the disc not displaying the photos and two not able to open photos from a good disc...i have now tried a music cd in my ubuntu computer and this opens 'rythembox music player' and works fine.

---

