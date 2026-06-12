---
title: "[SOLVED] accidentally &quot;recycled&quot; all files in /   is it possible to restore?"
date: 2009-06-09
forum: New to Ubuntu
---

### Post by j-d33zy on 2009-06-09
I stupidly thought i was deleting knoppix from my flash drive but actually deleted my entire / folder. I'm currently running on live cd trying to figure out how to recover files, i dont care about getting the os back, i can reinstal, but i have files i need! I tried exploring in nautilus as root, but to no avail. help please!

---

### Post by piousp on 2009-06-09
How did you deleted the files?

---

### Post by QIII on 2009-06-09
Are you running the Live CD on a Windows machine?

---

### Post by j-d33zy on 2009-06-09
i sent the files to the recycle bin, the computer was fairly useless there after and couldn't even get to grub after i restarted. yes its a PC if thats what you mean, it does have dual boot, but like i said, it cannot get to the bootloader.

---

### Post by 3startuna on 2009-06-09
> **j-d33zy said:**
> I stupidly thought i was deleting knoppix from my flash drive but actually deleted my entire / folder. I'm currently running on live cd trying to figure out how to recover files, i dont care about getting the os back, i can reinstal, but i have files i need! I tried exploring in nautilus as root, but to no avail. help please!

Dude you deleted your main partition? 

HOW? were you running live CD at the time? 

You shouldnt be able to delete anything

In any case their are programs available that will allow you to recover delteted files from a disc. Im not sure of one for linux, but im sure they exist. do a google search for them.

When you format,all that happens is that it recreates the file tables for the disc, it doesnt physically erase all files from the disc.

Also my ex roomate in college had accidentally formated his entirre hard drive while doing a OS upgrade. He was able to recover all his files using a linux program so im sure they exist.

I'll send him a message asking him for advice.

---

### Post by michy99 on 2009-06-09
The only way you could delete / is as root. If you sent it to the trash instead of actually deleting it, you should be able to simply restore it. But if you did it as root, (which is the only way to delete /) it would be in roots trash.

---

### Post by QIII on 2009-06-09
Linux has TestDisk and Photorec that work extremely well.

But you have to be running in Linux, get them from Synaptic or .deb ...

---

### Post by 3startuna on 2009-06-09
Ok check this out.

[http://www.ubuntugeek.com/recover-deleted-files-with-foremostscalpel-in-ubuntu.html](http://www.ubuntugeek.com/recover-deleted-files-with-foremostscalpel-in-ubuntu.html)

calm down and dont start installing stuff until you've read and understand what your doing. But those programs look promising.

---

### Post by j-d33zy on 2009-06-10
thanks for all the help, its greatly appriciated. im currently running a live cd as my installed ubuntu is unusable. @ michy99: how do i get to root's trash? basically i highlighted all the files in /  (ex. dev, bin, etc) then sent them all to recycle bin. stupid, i know. I looked into trying to find the files using  a program called foremost, but it cant seem to find any. also, i cant figure out how to point foremost to my external hard drive for a dump as i cannot dump on a live cd because of the space. thanks again.

---

### Post by QIII on 2009-06-10
A pain to do, but:

Can you install Knoppix on a USB drive, run Knoppix from there (I say Knoppix because you are probably used to it), install TestDisk or Photorec and use that environment to recover the files from the drive where you made the unfortunate error?

By the way.  Don't let anyone fool you.  We've all made bonehead moves.

---

### Post by asmoore82 on 2009-06-10
> **j-d33zy said:**
> basically i highlighted all the files in /  (ex. dev, bin, etc) then sent them all to recycle bin. stupid, i know.
This would not be possible unless you had done something screwy with permissions
or if you were running as root - both are extremely bad idea now you know why.

mount your drive under the liveCD and see if anything at all is left ...
```
ls -Ra /media
```

---

### Post by j-d33zy on 2009-06-10
well, im using an ubuntu live cd which works fine for what i need it to, but testdisk is used to recover deleted partions not really files, (from what ive read anyway) but i will give photorec a try. thanks.

---

### Post by j-d33zy on 2009-06-10
[@asmoore82:]("http://ubuntuforums.org/member.php?u=341737")
thanks, i found .Trash-0 but i cannot get into it. it says permission denied. i need some terminal 101. how do i get in there?

---

### Post by 3startuna on 2009-06-10
> **QIII said:**
> A pain to do, but:

Can you install Knoppix on a USB drive, run Knoppix from there (I say Knoppix because you are probably used to it), install TestDisk or Photorec and use that environment to recover the files from the drive where you made the unfortunate error?

By the way.  Don't let anyone fool you.  We've all made bonehead moves.

No doubt.

Thats why I keep all data on a completely seperate slave drive and only run the OS on the master.

lesson from the windows days :D

but im still puzled HOW he deleted the file system, that should not be possible.

All those files are locked and only root has that access

---

### Post by j-d33zy on 2009-06-10
im definately gonna make a separate partion. i have no idea how i deleted them as root, but i just sent them to the recycle bin. but seriously the command sudo cd doesn't work on the live cd, how do i get in there?

---

### Post by Cresho on 2009-06-10
If you have not reinstalled os, you can recover partition and all files intact.

partition table doctor can rebuild your partition leaving all lost files intact as long as you did not write over it such as reinstalling os on that partition.

I lost like 1 terabyte and recovered all files intact videos, pictures, music, all folder directory structure intact.  this software rebuilds ext3 partitions which i was using when i lost all and recovered.

[http://www.ptdd.com/](http://www.ptdd.com/)

---

### Post by QIII on 2009-06-10
TestDisk recovers partitions and what is inside them.

I've used it before that way.

It is even useful getting data back off of a crashed Windows drive, which I have done for people.

Photorec comes highly recommended, but I must say I've never used it.

---

### Post by ryanhaigh on 2009-06-10
> **j-d33zy said:**
> [@asmoore82:]("http://ubuntuforums.org/member.php?u=341737")
thanks, i found .Trash-0 but i cannot get into it. it says permission denied. i need some terminal 101. how do i get in there?

It seems that you were running as root when using the knoppix livecd. As such all the deleted files should be contained in the /.Trash-0 folder (where 0 is the UID of the user [and the root user is always 0]("http://en.wikipedia.org/wiki/User_identifier_(Unix)")).

Hopefully the Knoppix CD you were using implements the recycle bin properly as per the freedesktop spec but just in case you may want to make a COPY of the /Trash-0 folder on your external drive using either ubuntu/knoppix livecds.

So assuming you are running ubuntu livecd.

[LIST=1]
[*]Install the package [nautilus-gksu]("apt:nautilus-gksu")
[*]Restart nautilus, press alt-F2 and run "nautilus -q" and then alt-F2 again and run "nautilus" (without quotes)
[*]Mount the filesystem that contains /Trash-0, you should be able to do this just by double clicking from Computer
[*]If neccessary depending on how you mounted the filesystem open the newly mounted filesystem eg. /media/sda1
[*]Press ctrl-h to show hidden files
[*]Right click on Trash-0 and select open as administrator
[*]You should now be able to browse around that Trash-0 directory and COPY what you want onto an external drive which you should just be able to plug in at this point. BE CAREFUL you are running nautilus as root, although I don't know how much worse it could get :)
[*]Once you have a copy of everything you can try to restore the files to their original locations. To do this, in the root nautilus window enter trash: I haven't had the need to use this feature so I can't be sure if you will be able to just restore all items at once or you will have to do it one at a time. If it is one at a time post back here and maybe we can script something using trash-cli (allows you to manage trash/recycle bin from command line).
[*]With a whole lot of luck everything will restore to the correct locations and you might have a usable system.
[/LIST]

---

### Post by j-d33zy on 2009-06-10
@ryanhaigh: thank you so much. I was meaning to delete the info on the knoppix drive as it was plugged in when i was running ubuntu on my hd. i know that the files i need are on my harddisk not on the knoppix flashdrive. once i got into .Trash-0 on my hd, there were 2 folders, files and info. files was empty, and info had three blank text files, dev.trashinfo, proc.trashinfo, and sys.trashinfo.  I sent the files to the recycle bin, is that any differant than the trash?

---

### Post by H2SO_four on 2009-06-10
> **3startuna said:**
> No doubt.

Thats why I keep all data on a completely seperate slave drive and only run the OS on the master.

lesson from the windows days :D

but im still puzled HOW he deleted the file system, that should not be possible.

All those files are locked and only root has that access

I have a similar setup on my rig.  This way if something happens I can have a running system in no time flat.  

its really easy to delete your /.

I won't type the command (mods won't like it, i'm sure) but you need super-user power and its a forced remove of directory.  When I am going to upgrade to next edition I'm gonna run that command for fun first :)

---

### Post by ryanhaigh on 2009-06-10
> **H2SO_four said:**
> I have a similar setup on my rig.  This way if something happens I can have a running system in no time flat.  

its really easy to delete your /.

I won't type the command (mods won't like it, i'm sure) but you need super-user power and its a forced remove of directory.  When I am going to upgrade to next edition I'm gonna run that command for fun first :)

Just to make sure you are aware, if you run that command while your secondary drive is still mounted you will still loose everything.

---

### Post by ryanhaigh on 2009-06-10
> **j-d33zy said:**
> @ryanhaigh: thank you so much. I was meaning to delete the info on the knoppix drive as it was plugged in when i was running ubuntu on my hd. i know that the files i need are on my harddisk not on the knoppix flashdrive. once i got into .Trash-0 on my hd, there were 2 folders, files and info. files was empty, and info had three blank text files, dev.trashinfo, proc.trashinfo, and sys.trashinfo.  I sent the files to the recycle bin, is that any differant than the trash?

That doesn't sound promising. If you can please try and describe what you did to delete the files and everything you have done since.

---

### Post by j-d33zy on 2009-06-10
I highlighted all the folders in / then right clicked and move to recycle bin. I must have been running nautilus as root, because i dont think that i could delete it otherwise, but i dont remember running as root. Right after i did it i had a oh **** moment and went to the recycle bin, but it wouldn't let me open it, saying this directory dosent exist or something to that effect. but it was strage because the gui and everything still worked. but i couldnt open anything or use anything. i restarted, and it wouldnt even get to grub, saying something about grub config files missing. So i booted on ubuntu live cd, and here i am.

---

### Post by ryanhaigh on 2009-06-10
Sorry I missread your original post, I thought you had deleted the file while running knoppix.

I would have thought that if running as root the files should ALL have been stored in /.Trash-0 and the fact that those info files were there seemed to support this but at this stage it does appear as though the files are actually gone. Can you post the output of the command ```
df -h 
``` which will display the capacity and usage of your partitions.

I'm afraid you may be forced to revert to something like foremost/photorec to try and recover the files that you need there have been a number of tutorials on the web about this in the last year or so. Obviously a little late but you should really look into having backups for all the critical info you need, having data on a separate drive/partition is a good idea but what happens when that hard drive fails completely?

---

### Post by 3startuna on 2009-06-10
> **H2SO_four said:**
> I have a similar setup on my rig.  This way if something happens I can have a running system in no time flat.  

its really easy to delete your /.

I won't type the command (mods won't like it, i'm sure) but you need super-user power and its a forced remove of directory.  When I am going to upgrade to next edition I'm gonna run that command for fun first :)I know the coommand your talking about. But he should have been prompted for password. 

Im asking because he may have discovered a glitch

---

### Post by j-d33zy on 2009-06-10
[FONT=monospace]ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 1.5G  2.4M  1.5G   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                 1.5G  2.4M  1.5G   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  108K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  152K  1.5G   1% /dev
tmpfs                 1.5G   76K  1.5G   1% /dev/shm
rootfs                1.5G  102M  1.4G   7% /
/dev/sr0              699M  699M     0 100% /cdrom
/dev/loop0            676M  676M     0 100% /rofs
tmpfs                 1.5G   16K  1.5G   1% /tmp
/dev/sda6             232G   61G  159G  28% /media/disk

sda 6 is where the filesystem on the hd should be.
thanks again for all the help, I would have been lost without it.
[/FONT]

---

### Post by ryanhaigh on 2009-06-10
> **j-d33zy said:**
> [FONT=monospace]ubuntu@ubuntu:~$ df -h
/dev/sda6             232G   **61G**  159G  28% /media/disk
[/FONT]

As you can see the file system is reporting 61GB of space used, this is definitely a good sign. Now its just a matter of figuring out where the data actually is. Can you please open a terminal and do the following:

```

sudo -s #become root so you can see all file
ls -aR /media/disk/ > ~/filelist.txt #create a list of all files

```

You should then be able to open /home/ubuntu/filelist.txt assuming that you are running off the ubuntu livecd

---

### Post by j-d33zy on 2009-06-10
Found all the files.  They were in  /media/disk/root/.local/share/Trash/files  so i must have been running as root. You are a lifesaver. Thank you so much. i don't think that there is a way to restore it, but that doesn't matter, i'm just happy to find the files. you are definitely a linux guru.

---

### Post by ryanhaigh on 2009-06-10
Glad you were able to find all your stuff. 

If you are planning on installing ubuntu again you may want to copy /var/cache/apt/archives (probably in /media/disk/root/.local/share/Trash/files). This folder contains all the .debs you have downloaded since installing. If you back them up and copy them to the same place on your new install you won't have to redownload the packages. Whether its worth the trouble is probably dependant on your internet connection, for me this can save hours :(

Don't forget to mark this thread as solved in the thread tools

---

