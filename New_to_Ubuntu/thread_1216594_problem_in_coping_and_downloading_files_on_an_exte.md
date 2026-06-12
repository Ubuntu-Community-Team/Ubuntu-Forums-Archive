---
title: "problem in coping and downloading files on an external hardisk"
date: 2009-07-18
forum: New to Ubuntu
---

### Post by Bardock on 2009-07-18
[CENTER][COLOR=Sienna]Hello everybody,I hope you're all alright.[/COLOR]:)
[COLOR=SandyBrown]yesterday, I have a problem with my external hard disk[/COLOR]..><
..[COLOR=Sienna]I could open,play and read files but[/COLOR] ~~[COLOR=Sienna]when I'm trying to copy or download something to the hard disk.[/COLOR]
[COLOR=SandyBrown]It doesn't work[/COLOR]..!!?:confused:
t[COLOR=Sienna]he screen has displayed[/COLOR] " The destination is read-only."<--[COLOR=Sienna]I tried to change the permission but it also didn't work:([/COLOR]
[COLOR=SandyBrown]but when I'm trying  to copy files in widows it works[/COLOR]..!!:o
..[COLOR=Sienna]I hope any one can help me[/COLOR] ,,[COLOR=Sienna]because this problem make me crazy and confuse me [/COLOR]><!

 [COLOR=SandyBrown]Thank you[/COLOR],[COLOR=SandyBrown]In advance[/COLOR]:)
[/CENTER]

---

### Post by DanYoSon on 2009-07-18
when you were changeing the permisions where you useing sudo??

try
```
sudo chmod 777 harddrivename
```

that is what mine is and it works fine

---

### Post by Sidewinder1 on 2009-07-18
Or:
```
sudo chown -R your_username:your_username /media/disk
```enter your password when prompted---> There you have it!  :-)

HTH, Side

P.S. Welcome to ubuntu forums!!!!!

---

### Post by jerome1232 on 2009-07-18
Unless the drive is ntfs, in that case it's not being mounted correctly.

Unfortunately I'm really not sure how to adjust Ubuntu's auto-mount policy for external drives.

---

### Post by Bardock on 2009-07-18
[CENTER]> **DanYoSon said:**
> when you were changeing the permisions where you useing sudo??

try
```
sudo chmod 777 harddrivename
```that is what mine is and it works fine

> **Sidewinder1 said:**
> Or:
```
sudo chown -R your_username:your_username /media/disk
```enter your password when prompted---> There you have it!  :-)

HTH, Side

P.S. Welcome to ubuntu forums!!!!!

[COLOR=Sienna]Thank you gays but I tried these command before[/COLOR] [COLOR=Sienna]but nothing succeed[/COLOR],,[COLOR=Sienna]it keeps telling me[/COLOR]..
..[COLOR=SandyBrown]That [/COLOR]"this destination is read-only",,[COLOR=SandyBrown]but the second hard disk still  works well[/COLOR]..?

[COLOR=Sienna]some one told me that this problem is generated[/COLOR] [COLOR=Sienna]when the usb is removed in the unsafe mode[/COLOR]..??

[COLOR=Sienna][COLOR=SandyBrown]However as I said  it works well with Windows[/COLOR][/COLOR],,[COLOR=SandyBrown]but with Ubuntu  it doesn't[/COLOR]..><

[/CENTER]

---

### Post by jerome1232 on 2009-07-18
With the disk plugged in would you mind posting the output of mount ?

```
mount
```

---

### Post by Shpongle on 2009-07-18
i had a similar problem, with a usb , and i tried the commands , what did work in the end was moving all the stuff onto a windows pc format the usb and put it all back on, then it worked fine, i think it was removed unsafely too and thats what caused it, been working fine since

---

### Post by Sidewinder1 on 2009-07-18
If that's the case, go into windows and "Safely remove hardware,...etc.etc.
Then reboot ubuntu and try the chmod or chown commands. If that doesn't do it I'm not sure what will...

---

### Post by jerome1232 on 2009-07-18
chmod/chown doesn't work on ms filesystems. You have to mount them with certain options to get the permissions right.

ie

```
sudo mkdir /media/tmpmnt
sudo mount -t ntfs /dev/sdx# /media/tmpmnt -o umask=000
```

---

### Post by Bardock on 2009-07-18
[CENTER]> **jerome1232 said:**
> With the disk plugged in would you mind posting the output of mount ?

```
mount
```

[COLOR=Sienna]Ok as you wised[/COLOR]..[COLOR=SandyBrown]Really the result is weired see[/COLOR]..!!:o
> 
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-13-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/master/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=master)
/dev/sda5 on /media/D type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda6 on /media/E type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /media/Z type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
[/CENTER]

---

### Post by jerome1232 on 2009-07-18
Which partition is it? Z?

---

### Post by brookie on 2009-07-18
> **Sidewinder1 said:**
> If that's the case, go into windows and "Safely remove hardware,...etc.etc.
Then reboot ubuntu and try the chmod or chown commands. If that doesn't do it I'm not sure what will...

I had this same problem when I used my external usb hdd on a friends vista machine to deliver some data files. I didn't use the 'remove safe' icon tool in the windows systray. I drove out of town, only to have to return to his house, plug my drive back into his system, and use 'remove hardware safely'. I then plugged my drive back into my ubuntu machine and it was back to normal. Did you give it a try? :D
Cheers,
brook

---

### Post by Bardock on 2009-07-18
[CENTER]> **jerome1232 said:**
> Which partition is it? Z?

[COLOR=Sienna]it's the external hard disk that I have problem with[/COLOR]..><
[/CENTER]

---

### Post by Bardock on 2009-07-18
[CENTER]> **DillByrne said:**
> i had a similar problem, with a usb , and i tried the commands , what did work in the end was moving all the stuff onto a windows pc format the usb and put it all back on, then it worked fine, i think it was removed unsafely too and thats what caused it, been working fine since

[COLOR=Sienna]Someone suggested it to me[/COLOR]:)~~[COLOR=Sienna]but it's difficult choice if it's not impossible[/COLOR]..
..[COLOR=SandyBrown]because the files size is too large[/COLOR]..><

> **Sidewinder1 said:**
> If that's the case, go into windows and "Safely remove hardware,...etc.etc.
Then reboot ubuntu and try the chmod or chown commands. If that doesn't do it I'm not sure what will...

> **brookie said:**
> I had this same problem when I used my external usb hdd on a friends vista machine to deliver some data files. I didn't use the 'remove safe' icon tool in the windows systray. I drove out of town, only to have to return to his house, plug my drive back into his system, and use 'remove hardware safely'. I then plugged my drive back into my ubuntu machine and it was back to normal. Did you give it a try? :D
Cheers,
brook

[COLOR=SandyBrown] [COLOR=Sienna]I tried but nothing changed[/COLOR][/COLOR]..><
[/CENTER]

---

### Post by jerome1232 on 2009-07-18
> **Bardock said:**
> [CENTER]

[COLOR=Sienna]it's the external hard disk that I have problem with[/COLOR]..><
[/CENTER]

Well based on that output of mount there are two disks in your system right now /dev/sda and /dev/sdb, I'm going to assume /dev/sdb is the external disk and /dev/sdb1 is the partition your having problems with.

In which case let's unmount it and remount it with options that should work and see how that goes.

```
sudo umount /dev/sdb1
sudo mkdir /media/tempfs
sudo mount -t vfat /dev/sdb1 /media/tempfs -o umask=000
```

Now you should be able to create/delete files on the drive.

---

### Post by brookie on 2009-07-18
[COLOR=SandyBrown] [COLOR=Sienna]I tried but nothing changed[/COLOR][/COLOR]..><
[/CENTER][/QUOTE]

sorry, :(
hope you get this figured out soon
good luck

---

### Post by Sidewinder1 on 2009-07-19
Wow! This has gone beyond enigma. I know how frustrated I am with your problem; I can imagine how you must feel. Did you try putting on your conical, aluminium foil hat and searching for gremlins? Did you beat the dog? Won't affect the problem but might make you feel better, not the dog, though..
OK, I'll take one last stab at this...
Boot into windoze; make sure windoze *sees* the external hard drive.
Go through the *Safely Remove Hardware* steps.
Turn off or unplug power cord to Ext. HDD.
Cold/Hard reboot your computer, making sure it's complteely powered down for at least 20 seconds.
Start ubuntu; when it's completely booted, *then* turn on or plug in the power cord to your Ext. HDD.
Click on Places---->Home
In the left column right click on the Ext. HDD and in that menu click Mount. NOTE: if the Ext. HDD has two partitions (NTFS/FAT32 and ext3/ext4) you'll have to mount each separately using the process above.
Each drive (partition)  should now have an icon on your Desktop. Right click it, then click Properties, then click Volume and write down the Mount Point; you'll use this exact mount point in the command that I will give you (my Ext HDD has two partitions, ext3 and NTFS, since I mounted the ext3 first it's mount point is /media/disk and the NTFS partition's mount point is /media/Cavalry 500 Gig External HD_)
**Now**, here goes:
```
sudo chown -R Bardock:Bardock /mount point
``` 
Where Bardock is your login username on your ubuntu computer.
Where mount point reads exactly as it did in the result of your right click on Volume.
In my case it would be   sudo chown -R Sidewinder:Sidewinder /media/disk
Enter your password when prompted. 
That should be all.
You may have to *chown* both/all partitions.

If all of the above fails miserably, I must surrender on the field of battle and go in search of some Sctoch; even if it's only 0800 local here.

HTH,
Side

---

### Post by Bardock on 2009-07-19
[CENTER]> **jerome1232 said:**
> Well based on that output of mount there are two disks in your system right now /dev/sda and /dev/sdb, I'm going to assume /dev/sdb is the external disk and /dev/sdb1 is the partition your having problems with.

In which case let's unmount it and remount it with options that should work and see how that goes.

```
sudo umount /dev/sdb1
sudo mkdir /media/tempfs
sudo mount -t vfat /dev/sdb1 /media/tempfs -o umask=000
```Now you should be able to create/delete files on the drive.

[COLOR=Sienna]Your assuming was right[/COLOR]:)..[COLOR=Sienna]but nothing changed see the image below[/COLOR]..><
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=121629&stc=1&d=1248006878[/IMG]
[/CENTER]

---

### Post by jerome1232 on 2009-07-19
What brand of external drive is this?

---

### Post by Bardock on 2009-07-19
[CENTER]> **brookie said:**
> [COLOR=SandyBrown] [COLOR=Sienna]I tried but nothing changed[/COLOR][/COLOR]..><
[/CENTER]


sorry, :(
hope you get this figured out soon
good luck[/quote]

[COLOR=Sienna]thank you for helping me[/COLOR]..^^

> Wow! This has gone beyond enigma. I know how frustrated I am with your problem; I can imagine how you must feel. Did you try putting on your conical, aluminium foil hat and searching for gremlins? Did you beat the dog? Won't affect the problem but might make you feel better, not the dog, though..
OK, I'll take one last stab at this...
Boot into windoze; make sure windoze *sees* the external hard drive.
Go through the *Safely Remove Hardware* steps.
Turn off or unplug power cord to Ext. HDD.
Cold/Hard reboot your computer, making sure it's complteely powered down for at least 20 seconds.
Start ubuntu; when it's completely booted, *then* turn on or plug in the power cord to your Ext. HDD.
Click on Places---->Home
In the left column right click on the Ext. HDD and in that menu click Mount. NOTE: if the Ext. HDD has two partitions (NTFS/FAT32 and ext3/ext4) you'll have to mount each separately using the process above.
Each drive (partition) should now have an icon on your Desktop. Right click it, then click Properties, then click Volume and write down the Mount Point; you'll use this exact mount point in the command that I will give you (my Ext HDD has two partitions, ext3 and NTFS, since I mounted the ext3 first it's mount point is /media/disk and the NTFS partition's mount point is /media/Cavalry 500 Gig External HD_)
**Now**, here goes:
[/center]
     Code:     sudo chown -R Bardock:Bardock /mount point [CENTER]Where Bardock is your login username on your ubuntu computer.
Where mount point reads exactly as it did in the result of your right click on Volume.
In my case it would be   sudo chown -R Sidewinder:Sidewinder /media/disk
Enter your password when prompted. 
That should be all.
You may have to *chown* both/all partitions.

If all of the above fails miserably, I must surrender on the field of battle and go in search of some Sctoch; even if it's only 0800 local here.

HTH,
Side[/CENTER]
[CENTER]
 [COLOR=SandyBrown]it doesn't  work unfortunately[/COLOR]..[COLOR=SandyBrown]I'm really in a bad situation[/COLOR]..><
..

> What brand of external drive is this?[COLOR=SandyBrown]the brand is My Book[/COLOR]..^^


[/CENTER]

---

### Post by jerome1232 on 2009-07-19
I don't know what else to try then, by all rights mounting it with that umask should have done it.

I see mixed results about My Books and Linux, some people have problems with them shutting themselves down in the middle of doing things and I did stumble on one thread with the same issue but no solution.

There doesn't happen to be some physical button/slider/switch on the drive that switches it from read only to read/write does there?

---

### Post by Bardock on 2009-07-20
[CENTER]> **jerome1232 said:**
> I don't know what else to try then, by all rights mounting it with that umask should have done it.

I see mixed results about My Books and Linux, some people have problems with them shutting themselves down in the middle of doing things and I did stumble on one thread with the same issue but no solution.

There doesn't happen to be some physical button/slider/switch on the drive that switches it from read only to read/write does there?

[COLOR=Sienna]it looks that there is something is related with System[/COLOR].. :o
..[COLOR=SandyBrown]more than the hard disk[/COLOR]!:confused:.. [COLOR=SandyBrown]because I lost some data[/COLOR]..:(
...[COLOR=Sienna]when this problem happened [/COLOR].. [COLOR=Sienna]but it works in windows[/COLOR]...><

[COLOR=SandyBrown]I don't know what to say[/COLOR]^^~~[COLOR=SandyBrown]but thank you very much for helping me[/COLOR]..:D
[/CENTER]

---

### Post by Sidewinder1 on 2009-07-20
> **Bardock said:**
> [CENTER]

[COLOR=Sienna]it looks that there is something is related with System[/COLOR].. :o
..[COLOR=SandyBrown]more than the hard disk[/COLOR]!:confused:.. [COLOR=SandyBrown]because I lost some data[/COLOR]..:(
...[COLOR=Sienna]when this problem happened [/COLOR].. [COLOR=Sienna]but it works in windows[/COLOR]...><

[COLOR=SandyBrown]I don't know what to say[/COLOR]^^~~[COLOR=SandyBrown]but thank you very much for helping me[/COLOR]..:D
[/CENTER]

I think you may have diagnosed your problem; perhaps a hardware issue, even the drive itself. My reasoning?
You have a My Book, which is a Western Digital Drive. 
Cavalry EXT. HDDs are Western Digital inside; I have four of them and used the chown method mentioned earlier and they work fine.
Don't get discouraged; never give up...
Side

---

### Post by Bardock on 2009-07-21
[CENTER]> **Sidewinder1 said:**
> I think you may have diagnosed your problem; perhaps a hardware issue, even the drive itself. My reasoning?
You have a My Book, which is a Western Digital Drive. 
Cavalry EXT. HDDs are Western Digital inside; I have four of them and used the chown method mentioned earlier and they work fine.
Don't get discouraged; never give up...
Side

[COLOR=Sienna]now I think it's really related  with the hardware[/COLOR]:o..[COLOR=Sienna]because I reinstalled Ubuntu[/COLOR]..
..[COLOR=SandyBrown]but nothing changed[/COLOR]!!..[COLOR=SandyBrown]but why it with windows works properly[/COLOR]...
...[COLOR=Sienna]there must be something that prevent[/COLOR]..[COLOR=Sienna]Ubuntu from writing data[/COLOR]!!

[COLOR=SandyBrown]Thank you for encouraging me[/COLOR]:)..[COLOR=SandyBrown]I must find the solution[/COLOR]..^^


[/CENTER]

---

