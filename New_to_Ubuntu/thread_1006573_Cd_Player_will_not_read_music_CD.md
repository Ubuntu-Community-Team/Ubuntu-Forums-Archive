---
title: "Cd Player will not read music CD"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by wheelerrver on 2008-12-09
When I insert a music CD I do not get anything on Rhythmbox music player or on Audio CD Extractor.  When I try to add files using Rhythmbox, it shows the cd drive, but does not yield any results when I click on it.  When I insert an MP3 cd it loads normally and I am able to download the files using Rhythmbox.  Although this works with MP3 cd's I still get a message first that the drive cannot be mounted, then if I wait a minute it works.

I have downloaded the files suggested for ubuntu in a thread on Comprehensive Multimedia and Video Howto ([http://ubuntuforums.org/newthread.php?do=newthread&f=326](http://ubuntuforums.org/newthread.php?do=newthread&f=326)).  This still does not work, but I do get a lot better fonts!:)

My computer is an older Toshiba Satellite 1415 S173.  Ubuntu Intrepid, CD is TEAC DW 224E

Any recommendations?

---

### Post by Daveth on 2008-12-09
Is this failure to play music cd's true with other players?

---

### Post by Michael.Godawski on 2008-12-09
Can you post your fstab file please?

```
cat /etc/fstab
```

Make sure the iso9660 is added to the cd-rom entry.

---

### Post by wheelerrver on 2008-12-09
Here is what that code generated:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d0372c4c-7065-4c52-940c-62f10661e706 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=e1aeafdf-79c4-4759-94a9-2819d38da7b3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


I see the iso9660 here.  Is this what you were referring to?

---

### Post by wheelerrver on 2008-12-09
Regarding trying other programs, this is the only player I have on the computer, so I tried the ripping program and got nothing there, either.

---

### Post by mc4man on 2008-12-09
When you put an audio cd in the drive does an icon appear either on the desktop or in places -> computer? (audio disk

Put an audio cd in and after the drive settles run this (should say on last line for your *-cdrom: drive,  'status=ready' vs. 'status=open'
```

sudo lshw -C disk
```

---

### Post by wheelerrver on 2008-12-10
I did as you suggested and the results were:

*-cdrom
       description: DVD reader
       product: DW-224E
       vendor: TEAC
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 7.0A
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom

I see it does say ready, so, I wonder what that means.  I was so long in getting back to this because I pulled the current hard drive and put in the old one with Windows XP -- I had the same malfunction there, so I think it must be something more basic that is the problem.  If you have any additional ideas, I would appreciate them.

---

### Post by wheelerrver on 2008-12-10
When I put in an Audio CD I do not get an icon anywhere.  I do get one when it is a data CD.

---

### Post by mjheagle8 on 2008-12-10
try inserting an audio cd.  then go to places->computer.  there should be an icon for your cd/dvd drive that shows if something is inserted or not. if there is nothing in the drive, it will just say 'cd-rw/dvd-rw drive' or whatever your drive is called.  if there is a disk, it will show the name of the disk.

---

### Post by wheelerrver on 2008-12-10
Thanks, I have tried that and get the basic cd-rw/dvd-rw drive not the CD title.  When I do it with a data CD it gives the CD name.

---

### Post by mc4man on 2008-12-10
With an audio cd in the drive, like when you ran the lshw, go to home folder -> edit -> show hidden files -> .gvfs and see if there is a "cdda mount on scd0" present.

Also try inserting an audio cd and holding down the shift button, do you get a pop up? (wait for up to 10 -15 sec

---

### Post by wheelerrver on 2008-12-10
Doing the first process results in seeing that the .gvfs folder is empty. 
 
The second process results in nothing happening.  No popup.

When I put in a data cd, I first get a popup which says:

UNABLE TO MOUNT LOCATION 

DBus error org.freedesktop.DBus.Error.NoReply:  Did
not receive a reply.  Possible causes include:  the 
remote application did not send a reply, the message
bus security policy blocked the reply, the reply timeout
expired, or the network connection was broken.


If I click OK on the message, the drive starts to run again and soon the disk icon appears.  I can download the files or take other actions with them.

---

### Post by networm1230 on 2008-12-10
It might be your hardware configrashion chack the hardware chack the cable

---

### Post by networm1230 on 2008-12-10
do you have all the codec installed gstream for audio to do this go to applications add/remove select all and all on the applications look for gstreamer and install them
 
hop this helps

---

### Post by mc4man on 2008-12-10
Your clearly not having cdda files recognized or you're missing 'support' for them. 
(unless it's a drive issue, hard to test on a laptop.

Are you using hardy or intrepid?

Do you have access to an external dvd drive?


Edit ; You could try re-installing in synaptic (DO Not Remove, just reinstall (most likely won't help 
gvfs
libgnomevfs2-0
libgstreamer0.10-0
libgstreamer-plugins-base0.10

---

### Post by wheelerrver on 2008-12-11
mc4man - thanks for staying with me on this.

I reinstalled the packages, but no change in the results.  Hmmm, I do have access to an external CD drive - it's in my storage unit somewhere.  I will dig it out and give it a try to see if it is a hardware issue - could be a few days until I can get there.  I am using Intrepid.

For both mc4man and networm - I suspect there is some sort of hardware (or maybe bios?) problem.  As I said, I booted this computer with Windows XP and could not read a music cd then either.  That sort of eliminates Ubuntu as the problem, doesn't it?

---

### Post by mikechant on 2008-12-11
> That sort of eliminates Ubuntu as the problem, doesn't it?
Well, probably true, in which case it could well be a hardware problem with the DVD/CD drive. 

But this fstab entry:

```
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
```

Looks a bit odd to me. I haven't got access to my Ubuntu machine at the moment, but I'm sure it has no fstab entry at all for the DVD/CD drive - it's all done by auto mounting. It might be worth trying removing this line from fstab (using sudo gedit /etc/fstab) and rebooting to see if that helps. Note that gedit will back up the old fstab to /etc/fstab~ in case you want to go back to the original.

---

### Post by glotz on 2008-12-11
Since nobody mentioned it yet, is there some form of DRM? Is it an actual [CD](http://en.wikipedia.org/wiki/Red_Book_(audio_CD_standard))?

---

### Post by mc4man on 2008-12-11
> As I said, I booted this computer with Windows XP and could not read a music cd then either. That sort of eliminates Ubuntu as the problem, doesn't it?

I read that line and somehow missed the whole point, most definitely a drive problem. 
It may be something mechanical, the laser is dirty, or both.

While it may not help at this point, you could try blowing the drive out with canned air. They do make cleaning disks but they they can do more harm than good.

Your fstab is fine.

---

### Post by wheelerrver on 2008-12-11
I will try using compressed air to clean the drive, just in case that is the deal.  Just seems strange that it can read other disks, but not the music CD's.

If the cleaning does not work, I will pick up my external drive in the next couple of days and see if it works.  

Mikechant, I will not try changing the fstab until I try the other drive, but I appreciate your comment.  

Glotz, I have tried several regular commercial music CD's so I don't think the problem lies there.  Thanks, though.

Oh, by the way, just as a test I tried burning an audio disk, and that failed, too.

---

### Post by john_spiral on 2008-12-13
> **wheelerrver said:**
> Here is what that code generated:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d0372c4c-7065-4c52-940c-62f10661e706 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=e1aeafdf-79c4-4759-94a9-2819d38da7b3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


I see the iso9660 here.  Is this what you were referring to?

try:

**sudo fdisk -l **

lists all the hard drives and their partitions, could be /dev/scd0 already exists as another hard drive device?

---

