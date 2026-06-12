---
title: "Removal of stubborn files !!!!!!!!!"
date: 2011-03-16
forum: New to Ubuntu
---

### Post by Caeser on 2011-03-16
***Hello to all you bilinguals out there!***
On following a thread from the forums i tried to do a complete backup. Went well until I got an error. Something about an instance of something being open or similar too that. As I could not find any poignant advice searching the net, I closed terminal. Now I have tar.gz2 file stuck in me system files that seems be quite happy where it is! As of just now I can see that the tar file has miraculously gone. It was only 1.4 gig so I guess it was a long way from finishing the backup. I have a initrd.img file I would like some information on please. Before I venture into another backup attempt, I would most graciously accept any relevant advice on how to back it up to an external hard drive. Preferably with all the terminal commands necessary. And please I only speak simple English, so If you could put yourself in my shoes for like when you first started off with linux, that would be of great help!!!! I have only had a few years experience on the dreaded windows, but am ready for this new challenge.
    Thanking you all in advance. This my first post ever so be kind!
   *** I tried for days to delete that dastardly file !!!!!!!***:popcorn:

---

### Post by nothingspecial on 2011-03-16
Don't delete the initrd.img file!

What backup instructions did you follow?

---

### Post by jtarin on 2011-03-16
It would help if you could post a link to the forum that you followed for your method of backup.
If you have files that are problematic to delete it is possibly a permission thing. A simple method is to enter the command in the terminal```
sudo nautilus
```(enter password) which will bring up an instance of Nautilus File manager, as root. Navigate to the offending file and right-click and choose delete. It is not advisable to delete an intrid.img file unless you know _[COLOR="Red"]without a doubt[/COLOR]_ that it is a duplicate you have mistakenly made.

---

### Post by deconstrained on 2011-03-16
The initrd.img file is a compressed disk image, the contents of which get copied into your computer's memory (ram) when you boot up your computer. It is necessary for Ubuntu to start up properly.

It sounds like you are backing up not only your personal documents but your system as well. If this is the case, then I'd recommend looking into a backup method that preserves permissions, ownership and and modification times on files, so that if you have to restore everything, it will work seamlessly as though it was never gone. Just making copies of your system files is guaranteed to fail unless you use rsync with the -a flag for archiving. 

One rather easy way of preserving permissions/times/ownership (and it's easy to restore from) is to create an image of the entire hard drive partition. A piece of software that looks promising for this application is CloneZilla, though I've personally never used it; 
[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by jtarin on 2011-03-16
> **deconstrained said:**
> 
One rather easy way of preserving permissions/times/ownership (and it's easy to restore from) is to create an image of the entire hard drive partition. A piece of software that looks promising for this application is CloneZilla, though I've personally never used it; 
[http://clonezilla.org/](http://clonezilla.org/)I use 
Paragon Partition Manager 10 from a USB stick to do this and I swear by it. You can Google for a free download. It is no longer being offered by Paragon but it can be found if you look diligently enough. It uses Linux to do the work at boot-time.

---

### Post by Caeser on 2011-03-16
I thank you all for your quick responses.
this the link 
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)
Yes I was trying to do exactly as the instructions said but did not realise i should have just done it straight  to my external drive. I thought I could just cut and paste it. I did end up deleting the file. I read something about the Ubuntu does like an indexing scan once a day so maybe that´s why the file could not be found. It&#347; gone now. The tar file !If someone can give me a better way of doing a backup plz be thorough with directions. Thank you all for your interest and help. I so much want to understand this linux trip.
Hey I&#7743; getting there!
Gotta crawl b4 u can walk !!!!!!

---

### Post by nothingspecial on 2011-03-16
Here is a similar thing with full explanation as to what's going on.

[http://openubuntu.com/index.php/topic,671.msg20209.html#msg20209](http://openubuntu.com/index.php/topic,671.msg20209.html#msg20209)

Have a read up on grsync as well. And I wouldn't just copy and paste stuff from the internet before you understand what it's going to do. ;) That way reinstalling lies.

---

### Post by nothingspecial on 2011-03-16
Oh yes and pay close attention to the final paragraph in that how to.

---

### Post by Caeser on 2011-03-16
Thank you to my advisors.
Those links were most helpful esp that snippet about the backup with the never-ending archive that will not halt. Guess that´s what had me screwed from the start!
Now without sounding too lame, can someone point me on the right path to what the command is to save the backup file to my Wd drive and after a reread of that article I think I will be ready to give it a go! Oh and and thank all very much for your help. 
#!/bin/bash

before="$(date +%s)"; sudo tar --same-owner -cpvzf /media/Backup/10.10_Backup_16-3-11.tgz
 --exclude=/proc --exclude=/lost+found --exclude=/sys --exclude=/mnt --exclude=/tmp
 --exclude=/media /; after="$(date +%s)"; echo "Elapsed time: $(expr $after - $before) seconds.";
 echo -e "\a"
***Could someone edit this script for me please. Much grateful***

---

### Post by nothingspecial on 2011-03-16
```
before="$(date +%s)"; sudo tar --same-owner -cpvzf [COLOR="Red"]/media/Backup[/COLOR]/10.10_Backup_16-3-11.tgz
--exclude=/proc --exclude=/lost+found --exclude=/sys --exclude=/mnt --exclude=/tmp
--exclude=/media /; after="$(date +%s)"; echo "Elapsed time: $(expr $after - $before) seconds.";
echo -e "\a"
```

The only bit you need to change is the bit in red. That needs to be the path to your external drive.

---

### Post by Caeser on 2011-03-16
Am not having much luck with this backup. Not sure if I have the right file path. My disk utility tells me its /dev/sdg. This directory tree is taking awhile to get used to after coming from vista. here is what I get from terminal if anyone can decipher it!

dave@dave-GQ559AA-ABG-a6220a:~$ before="$(date +%s)"; sudo tar --same-owner -cpvzf dev/sdg/Backup/10.10_Backup_16-3-11.tgz/
tar: Cowardly refusing to create an empty archive
Try `tar --help' or `tar --usage' for more information.
dave@dave-GQ559AA-ABG-a6220a:~$ --exclude=/proc --exclude=/lost+found --exclude=/sys --exclude=/mnt --exclude=/tmp/
bash: --exclude=/proc: No such file or directory
dave@dave-GQ559AA-ABG-a6220a:~$ --exclude=/media /; after="$(date +%s)"; echo "Elapsed time: $(expr $after - $before) seconds.";/
bash: --exclude=/media: No such file or directory
Elapsed time: 0 seconds.
bash: /: is a directory
dave@dave-GQ559AA-ABG-a6220a:~$ echo -e "\a"

dave@dave-GQ559AA-ABG-a6220a:~$ before="$(date +%s)"; sudo tar --same-owner -cpvzf /media/Backup/10.10_Backup_16-3-11.tgz
tar: Cowardly refusing to create an empty archive
Try `tar --help' or `tar --usage' for more information.
dave@dave-GQ559AA-ABG-a6220a:~$ --exclude=/proc --exclude=/lost+found --exclude=/sys --exclude=/mnt --exclude=/tmp
bash: --exclude=/proc: No such file or directory
dave@dave-GQ559AA-ABG-a6220a:~$ --exclude=/media /; after="$(date +%s)"; echo "Elapsed time: $(expr $after - $before) seconds.";
bash: --exclude=/media: No such file or directory
Elapsed time: 0 seconds.
dave@dave-GQ559AA-ABG-a6220a:~$ echo -e "\a"

dave@dave-GQ559AA-ABG-a6220a:~$ 

Tried it with the original code from the guide as well. As you can see no luck either way!
thx all

---

### Post by matt_symes on 2011-03-16
Hi

```
before="$(date +%s)"; sudo tar --same-owner -cpvzf /media/Backup/10.10_Backup_16-3-11.tgz
--exclude=/proc --exclude=/lost+found --exclude=/sys --exclude=/mnt --exclude=/tmp
--exclude=/media /; after="$(date +%s)"; echo "Elapsed time: $(expr $after - $before) seconds.";
echo -e "\a"
```

It all needs to be on one line. It is only one command and not 3.

Kind regards

---

### Post by nothingspecial on 2011-03-16
Also use the path from /media

type ```
mount
```

Here's my backup drive (which happens to be labled backup)

```
/dev/sdg1 on /media/backup type ext3 (rw,nosuid,nodev,uhelper=udisks)
```

So I would put

```
before="$(date +%s)"; sudo tar --same-owner -cpvzf /media/backup/10.10_Backup_16-3-11.tgz
```

So you need to put ```
/media/[COLOR="Red"]whatever_your_drive_is_labled[/COLOR]/10.10_Backup_16-3-11.tgz
```

---

### Post by Caeser on 2011-03-16
Have had no luck ! Here is what terminal is coming up with.

dave@dave-GQ559AA-ABG-a6220a:~$ before="$(date +%s)"; sudo tar --same-owner -cpvzf /media/Elements/Backup/10.10_Backup_16-3-11.tgz
tar: Cowardly refusing to create an empty archive
Try `tar --help' or `tar --usage' for more information.
dave@dave-GQ559AA-ABG-a6220a:~$ --exclude=/proc --exclude=/lost+found --exclude=/sys --exclude=/mnt --exclude=/tmp
bash: --exclude=/proc: No such file or directory
dave@dave-GQ559AA-ABG-a6220a:~$ --exclude=/media /; after="$(date +%s)"; echo "Elapsed time: $(expr $after - $before) seconds.";
bash: --exclude=/media: No such file or directory
Elapsed time: 0 seconds.
dave@dave-GQ559AA-ABG-a6220a:~$ echo -e "\a"
Not sure what the backup path should be-maybe a suggestion ***plz***

---

### Post by Caeser on 2011-03-16
Oh I have tried. Something just not clicking here. maybe this can help

dave@dave-GQ559AA-ABG-a6220a:~$ mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/dave/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dave)
/dev/sdb1 on /media/Elements type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
dave@dave-GQ559AA-ABG-a6220a:~$ 

[B][I]
this is my back up drive
[/I][/B]/dev/sdb1 on /media/Elements type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

---

### Post by Caeser on 2011-03-16
dave@dave-GQ559AA-ABG-a6220a:~$ mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/dave/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dave)
/dev/sdb1 on /media/Elements type ext4 (rw,nosuid,nodev,uhelper=udisks)
dave@dave-GQ559AA-ABG-a6220a:~$ before="$(date +%s)"; sudo tar --same-owner -cpvzf /media/Elements/10.10_Backup_16-3-11.tgz[sudo] password for dave: 
tar: Cowardly refusing to create an empty archive
Try `tar --help' or `tar --usage' for more information.
dave@dave-GQ559AA-ABG-a6220a:~$

---

### Post by deconstrained on 2011-03-17
**Goddammit, just forget tar.** Entering commands you've copied and pasted off the internet verbatim is a bad idea in general (it can end really bad if you're not careful) and just wastes your time trying to decipher them and figure out which parts to change and which parts you need, unless you have already learned how to compose arguments for the relevant program(s) by reading the manual page (use the command 'man tar' for details) and are copying/pasting for convenience's sake. **Just make a disk image using a program that has a graphical user interface,** believe me, it'll be easier.

Also, if you're making a full system backup and don't want to have to make a disk image, boot to a live disk and mount your system partition first; there are temporary device files and symlinks in /proc, /dev and a few other system folders that you actually don't want to copy because they could interfere with proper udev aliasing at boot and cause strange errors, **hence the arguments --exclude=/proc, --exclude=/sys, etc, which tell tar to ignore these folders** *(FYI: you're getting error messages such as "[color=red]bash: --exclude=/proc: No such file or directory[/color]" because you copied and pasted the command **with carriage returns (a.k.a. linebreaks,returns,newlines) attached** and bash interpreted each line between them as a completely separate command, which didn't work.)*

---

### Post by nothingspecial on 2011-03-17
Like the title of the how to says "**one line**", but never mind

In your menu go Accessories > Text Editor

copy and paste this into it

```
#!/bin/bash

before="$(date +%s)"; sudo tar --same-owner -cpvzf /media/Elements/10.10_Backup_16-3-11.tgz \
--exclude=/proc --exclude=/lost+found --exclude=/sys --exclude=/mnt --exclude=/tmp \
--exclude=/media /; after="$(date +%s)"; echo "Elapsed time: $(expr $after - $before) seconds.";
echo -e "\a"
```

Press Ctrl-Shift-S and save it as backup.sh in your home

make it executable

```
chmod +x backup.sh
```

 then run it like so

```
./backup.sh
```

---

### Post by Caeser on 2011-03-17
Well deconstrained this is where i´m up to.
I can get terminal backing up with this command.

sudo tar --same-owner -cvpzf /media/Elements/backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys/

Goes along well for a good while until it hits

**/media/Elements/backup.tgz**  which I hoped would be excluded, but apparently not.
So terminal sits there idle for about 4mins and then presses on with backup, until a short while later when I get this   -    [B]/home/dave/Pictures/
tar: Exiting with failure status due to previous errors[/B]

I looked in my hard drive drive and there was a backup tar file of 4.3 gigs.
so it´s close. shame so close.

Seems I might have to try a GUI utility to back up. 
I have dual boot with vista and used norton ghost for windows. If I did a image backup of my whole drive would it back up ubuntu partions?

Can u advise me on a simple image back up tool for linux ? (there´s so many)
partmagic, back in time, clonzilla etc 

And I thank you once more for your help and patience

---

### Post by Caeser on 2011-03-17
Thought we had something happening there for awhile nothingspecial.
It executed and ran like before. Got error message in exactly the same place.
It´s nearly right !
thx

---

### Post by nothingspecial on 2011-03-17
I think you've actually had success, tar can give that error for many reasons.

I think if you extracted it you would find everything there.

Google that error message ;)

You'll see what I mean.

---

### Post by nothingspecial on 2011-03-17
Infact, read down the page in the link I posted. That error message is mentioned, yet he still manages to restore his system. You've done it :D

---

### Post by Caeser on 2011-03-17
[IMG]http://ubuntuforums.org/images/attach/jpg.gif[/IMG] [Screenshot.jpg]("http://ubuntuforums.org/attachment.php?attachmentid=186359&stc=1&d=1300363696") (53.9 KB)
 well if this is what all its meant to be i guess yes it&#347; done.
Thx people:)
 I hope you fellas can help me out next time
sure i´m gonna need some expert advice for awhile until i get into the groove.
plz let me know if you think thats the complete backup. It´s only 1.1GB

---

### Post by deconstrained on 2011-03-17
> **Caeser said:**
> Well deconstrained this is where i´m up to.
I can get terminal backing up with this command.

sudo tar --same-owner -cvpzf /media/Elements/backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys/

Goes along well for a good while until it hits

**/media/Elements/backup.tgz**  which I hoped would be excluded, but apparently not.
Since you've managed to get it working now, add --exclude=/media to the command line options, that should do it. /backup.tgz and /media/Elements/backup.tgz are two completely different paths, so --exclude=/backup.tgz will only exclude the file if it's stored at "/", aka root (instead of rather /media/Elements/ )

---

### Post by Caeser on 2011-03-18
Strange deconstrained can´t seem to get working.
but all i need to know is if you think that was a full backup i did with nothingspecial´s advice.
I don have music or videos to backup!
so what do you think ?

---

### Post by deconstrained on 2011-03-18
Okay, here, try this.

Save the following into "backup_exclude.txt":
```
proc/*
lost+found
sys/*
mnt/*
tmp/*
media/*
```

Then
```
sudo tar -X backup_exclude.txt --same-owner -cpva -f /media/Elements/backup.tar.gz -C / ./
```

I still think you should try doing this while booted to a livedisk (better yet, stick to a non-command-line program with a graphical user interface for making backups; it's better for newcomers to Linux); you want to capture the filesystem's contents while it's down. That way you don't copy all the temporary runtime files, system symlinks and other things that shouldn't be there, and copy only everything that's necessary for the system to boot. 

Think of it this way: when the system isn't booted/active, such files aren't there or are different than what they would be if it were booted, right? And the contents that are there in this state (not booted) reflect what they should be in order for it to start up properly, right? Then it would be a simpler and more reliable way of making backups to catch the system in this "frozen" state. You won't have to bother with exclude patterns in this case because nothing you don't want to copy will be there anyway.

---

### Post by deconstrained on 2011-03-18
<double-posted>

---

### Post by Caeser on 2011-03-19
ok. did all that. 
ran and ended the same as last time.

./home/dave/Pictures/
tar: Exiting with failure status due to previous errors

Same size 1.1 GB
I think that may be done though as that site said it might end with an error but always worked for him when he did a restore!!!

can advise me on a good GUI backup program.
I will give that a go and see what that comes up with.

---

### Post by kroq-gar78 on 2011-03-19
> **jtarin said:**
> It would help if you could post a link to the forum that you followed for your method of backup.
If you have files that are problematic to delete it is possibly a permission thing. A simple method is to enter the command in the terminal```
sudo nautilus
```(enter password) which will bring up an instance of Nautilus File manager, as root. Navigate to the offending file and right-click and choose delete. It is not advisable to delete an intrid.img file unless you know _[COLOR="Red"]without a doubt[/COLOR]_ that it is a duplicate you have mistakenly made.
not that it's very relevant to this thread, but WOAH!

use ```
gksudo nautilus
```
NOT
```
sudo nautilus
```

no expert, but from what I've heard use gksudo to do nautilus and other gui things that were supposed to be in "sudo". Apparently, it can really mess up permissions or something.

Just a word of warning.... ([http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo))

---

### Post by Caeser on 2011-03-20
Ok all, got things under control here.
Clonezilla was my saviour, plus i believe those command line back ups worked.
thanks to all for your help !

---

