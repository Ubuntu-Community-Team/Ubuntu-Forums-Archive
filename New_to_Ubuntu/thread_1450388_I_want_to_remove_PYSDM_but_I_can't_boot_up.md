---
title: "I want to remove PYSDM but I can't boot up"
date: 2010-04-09
forum: New to Ubuntu
---

### Post by jonobugs on 2010-04-09
I have only recently started using Ubuntu. Brand new newbie I am. 

I had wanted to automatically mount my internal hard drives because it was a bit annoying to mount them after the OS loaded up, so I researched the forums and found that a program called Pysdm would do the trick for me.

Unfortunately for me, I messed up and now my computer won't boot up properly. I looked at the forums once again and found a very similar thread but I have to admit I was quickly lost as I didn't fully understand all the commands that the very helpful people were giving out.

I read that I should remove some lines in the fstab file. I managed to boot up with my liveCD and following the instructions, I was able to edit the fstab file, but to be honest, it was unclear to me which lines I should edit out.

So far, I am still getting the errors. I basically want to remove the changes that pysdm made so that I can boot up my computer and remove the program as it's simply too dangerous for me.

If anyone can tell me which lines I should look for and edit out, I would be very grateful!! Or alternatively, tell me if I'm completely off track here and point me in the right direction.

Thanks in advance,

Jonathan

---

### Post by Paqman on 2010-04-09
> **jonobugs said:**
> 
So far, I am still getting the errors. I basically want to remove the changes that pysdm made so that I can boot up my computer and remove the program as it's simply too dangerous for me.


All pysdm does is provide a GUI for editing /etc/fstab, so it's no more dangerous than editing that file by hand. Probably less so actually.

Can you post up the contents of your /etc/fstab so we can have a look?

---

### Post by jonobugs on 2010-04-09
Yes, of course you can! I would have posted it earlier, but I was at a different computer and didn't have access to this information. Thanks for taking a look.

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                                     0  0  
# / was on /dev/sda5 during installation
UUID=2d09421f-6a33-4f88-aa28-9293d7ea10ef  /               ext4         users,user,owner                             0  1  
# swap was on /dev/sda6 during installation

UUID=db135643-ed14-4605-834c-d6452d0d16b0  none            swap         users,sw,user,owner                          0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8                        0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8                     0  0  
/dev/sda1                                  /media/sda1     ntfs         nls=iso8859-1,ro,umask=000                   0  0  
/dev/sda2                                  /media/sda2     ntfs         nls=iso8859-1,ro,users,umask=000,user,owner  0  0  
/dev/sdb1                                  /media/sdb1     ntfs         nls=iso8859-1,ro,users,umask=000,user,owner  0  0

---

### Post by ankspo71 on 2010-04-09
Hi, I use pysdm too, but only to automount a storage drive on sdb

your Ubuntu root partition "/" should look something like this:

```
UUID=2d09421f-6a33-4f88-aa28-9293d7ea10ef / ext4 **errors=remount-ro ** 0 1
```

That line was unmodified by pysdm (and from Ubuntu 10.04 beta2), except I added your UUID instead of mine.

Here is a copy of my fstab. Only my sdb2 drive entry was modified by pysdm.
> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid       0  0  
# / was on /dev/sda1 during installation
UUID=4cc78283-4564-4256-ae32-a27d94598a39  /               ext4  **errors=remount-ro **        0  1  
# swap was on /dev/sdb1 during installation
UUID=7e1ae295-8f14-463c-8fc0-7aa9649a98ee  none            swap  sw                        0  0  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8  0  0  
/dev/sdb2                                  /media/sdb2     ext4  users                     0  0  

---

### Post by ankspo71 on 2010-04-09
After responding to this post originally, I explored pysdm some more and discovered a bug that could cause people to incorrectly configure their hard drives. I never had a reason to configure my first hard drive, so I don't know how long I have overlooked this problem. I feel it is a dangerous/serious bug too. 

I just submitted a bug for this.
[https://bugs.launchpad.net/ubuntu/+source/pysdm/+bug/559416](https://bugs.launchpad.net/ubuntu/+source/pysdm/+bug/559416)
If anyone has this problem with pysdm, please login with your launchpad account and click on "it effects me too".

To the original poster:
Keep reporting back here if you can't boot. I'm sure someone here can get your system booting. I found a file named fstab.bak that pysdm must have created. it is located at /etc/fstab.BAK. If you have used pysdm only one time, then it is possible to restore the correct/original fstab settings using that backup file.

---

### Post by jonobugs on 2010-04-10
Hi, thanks for all the help. I kind of gave up on trying to figure out the fstab thing for a while and fixed the Windows partition I have. 

Anyway, I'm back at it and trying to understand all the terminology. I've been reading up a lot but I'm still confused about a few things. 

I can't seem to find the forum I used the first time to edit my fstab. The problem is that I don't have any rights to the folder and so I can edit, but I can't save any changes.

Anyway, unfortunately, the BAK file is no good as I didn't realize what I was doing before and I had already made one edit. Had I known there was a BAK file, I would have done that right away! Too bad for me.

I read that I should comment out all the files at the end of the fstab file, but I still can't get it to work. 

I'll keep you posted on what happens!

---

### Post by jonobugs on 2010-04-10
[COLOR=DarkGreen]**Oh, I believe I have solved the problem!**[/COLOR]

I was able to edit out the offending line.

For anyone new I'll explain what I did in case the same thing happens to you. I'm sure this will be simple for the average user, but I'm still quite new.

First, I have to say that PySDM is indeed not to be played with lightly.

I ran the program to try and get my hard drives to mount automatically, which they did, but then for some reason I was unable to write to my hard drives. They were all read only. So, I went back to PySDM to see if I could figure out what was wrong. I couldn't see how to fix it immediately, but I thought I would try and tick off all the boxes to see if that would allow me to write to the hard drives. That was my undoing.

The next time I tried to boot up I was unable to get into the OS and it hung on me. 

The error looked like this 

[COLOR=DarkRed]init: Failed to spawn mountall-shell main process unable to execute: permission denied
init: job process: 529: unhandled error from job_process_spawn: permission denied
init: failed to spawn mountall-shell post-stop process: unable to execute: permission denied
[/COLOR] 
I had to press reset. I then tried to boot using the recovery shell, but that came up with a similar if not the same error. 

The only way I could boot was to use the LiveCD, which I did.

So, looking up the error I found that the problem was in my fstab file, which appears to be a configuration file that tells your computer how to mount the hard drive partitions. Lots of technical jargon that I couldn't really grab all at once.

Anyway, someone wrote that the command should be commented out. There were a few problems with this. First, I had no idea WHICH line I should edit out. Second, I didn't know where the fstab file was. Finding it was apparently easy. It is listed under the /etc directory which can be found on the file system. This appears to be the directory in which Ubuntu is installed.

However, I ran into yet another roadblock. I wasn't able to edit the file. Or rather, I was unable to save the file. I'm still not sure why I wasn't able to edit it but I am guessing that I might have been looking at the CD system directory and of course I won't be able to save that file.

I read that I should unmount the drive using the terminal. In the terminal I unmounted the drive using the command

[COLOR=Blue]umount /dev/sdb5[/COLOR]

Where sdb5 is the drive that my system is on. I am guessing that many computers will have their system on sda1. However, I am using a dual boot system. You can find out the drives you have by using the command

[COLOR=Blue]sudo fdisk -l[/COLOR]

Your system should be of type LINUX, so unmount that drive first using the umount command.

[COLOR=Blue]umount /dev/sdb5 [/COLOR]  {change sdb5 to the name of your hard drive partition}

then you need to mount your drive again, but this time you will tell it where to mount so that you can read it. I'm sure it's more technical than that, but that's how I understand it.

[COLOR=Blue]mount /dev/sdb5 /mnt[/COLOR]

I used the /mnt directory, because that's what I read it should be on. I'm not sure if it makes a big difference if you change this name, but maybe it might.

Once I did that I was able to then edit my fstab file by using the command

[COLOR=Blue]gksudo gedit /mnt/etc/fstab[/COLOR]

NOTE: I highly recommend that before you do any editing on your fstab file that you back it up first. Name it fstab.bak1 or something. I believe that it will make a BAK file on it's own, but I could have saved myself a lot of trouble if I had made one.


What I did, was comment out a line  that listed my hard drive but instead of just commenting it completely out, I changed the line a bit. I had no idea what I was doing, but at that point I figured it didn't matter since my computer wasn't booting up anyway. NOTE: you can comment out a line by using the number sign (#) before the line (as follows)

# This line won't be executed in your fstab file


This is the point where I'm not sure if I actually fixed it or not, but my computer seems to be working. 

Anyway, for complete disclosure, I'll list the changes I made and how I made those decisions.


The line that I found was as follows:


[COLOR=DarkRed]UUID=2d09421f-6a33-4f88-aa28-9293d7ea10ef  /               ext4         users,user,owner                             0  1  [/COLOR]


When I first tried to open my fstab, I think I opened the fstab off of the LiveCD and THAT line was a little different. I noticed that it didn't have the users, user, owner option at the end, so I took that out and replaced it with the line from the CD fstab


[COLOR=DarkRed]UUID=2d09421f-6a33-4f88-aa28-9293d7ea10ef  /               ext4 errors=remount-ro  0 1 [/COLOR]



As you may notice, it has a bit extra on the end "errors=remount-ro 0 1


I have no idea what that does, but I thought that since I can boot up with my CD, why not try it? Also, I made a back up and only commented the other line out (so it's actually still there).


When I was playing around with PySDM, I checked the boxes for owners, users thinking that maybe I couldn't write to my hard drive because they didn't have permission. I'm not sure what it is supposed to do, but I can't say I was happy with the result.


I also changed the other UUID line in my fstab file and made similar changes as follows:


[COLOR=DarkRed]UUID=db135643-ed14-4605-834c-d6452d0d16b0  none            swap         users,sw,user,owner                          0  0  [/COLOR]


changed to:
[COLOR=DarkRed]UUID=db135643-ed14-4605-834c-d6452d0d16b0  none swap sw 0 0 
[/COLOR] 


Again, I have no idea what the stuff at the end means, but it seems to have done the trick. I didn't want to completely comment out the UUID line as I figure that my drives still need to mount.

So, that is the long and complicated story of how I changed the fstab file while using the LiveCD. The hardest part about all of this was trying to get my head around all the jargon that people use here as I'm not familiar with any of it and am learning as I go along. If any advanced (or even past beginner stage) person is reading this and an enlighten anyone further on all my mistakes, please feel free to do so. I know that I've probably said a lot of stupid things, but I figure I can still play the newbie card for a few more months.

I'm marking this as solved, but I am still holding my breath as I still haven't figured out how to mount my hard drives automatically!! (which is how I got into this mess in the first place) *sigh* more reading to do.

---

### Post by jonobugs on 2010-04-10
Okay...stupid question coming up. How do I mark this thread as solved??

---

### Post by Morbius1 on 2010-04-10
And for anyone out there that's playing the home version of this game I'd like to point out that only PySDM would have produced the following line:

>  /dev/sdb1                                  /media/sdb1     ntfs         nls=iso8859-1,ro,users,umask=000,user,owner  0  0     gibberish.

"ro" and "umask=000" in the same statement. ro is Read Only. umask=000 allows owner, group, and everyone else to read and write.

"users" and "user", and "owner" - Oh my 

In all seriousness though I find PySDM to be one of the most ironic pieces of software I've ever seen. It's basically the man page for mount "codified". It requires the user to know so much about the different options and how they should be used that he's more likely to just bring up fstab in a text editor.

---

### Post by Morbius1 on 2010-04-10
> Okay...stupid question coming up. How do I mark this thread as solved??
You should find it in the [COLOR=Red]"Thread Tools"[/COLOR] at the first post

---

