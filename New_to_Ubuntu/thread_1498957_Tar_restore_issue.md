---
title: "Tar restore issue"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by BobJam on 2010-06-01
I restored my system using the tar method (from a backup.tar.gz.bz2 file I had made for just such "emergencies") detailed in a thread started by user "Heliode" back in May of 2005 ( [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087) . . . some 107 pages and 1066 posts long, the last post being just 4 days ago).  Granted, the beginning of that thread is OLD, but the method worked just fine.  (The reason I did the restore operation is not really pertinent to my problem . . . let's just say I'm a noob to ubuntu and messed up my desktop).

It worked just fine EXCEPT, and here is my problem, for the way it restored the mount of my home partition.  I think the issue is the mount, but am not sure . . . and as I detail the problem, you'll see that I really don't have my arms around all this mount stuff and the tar backup/restore method.

I had installed ubuntu originally with a seperate partition for my /home directory.  Previously, I had always seen desktop boot activity (and app opening activity) on my home partition . . . using gkrellm for monitoring my /home partition, which happens to be sda6.  Now grekellm shows absolutely NO activity on sda6, with all the activity shown on / (sda1 . . . the top panel on image below . . . I have it split into write/read operations).

[IMG]http://i510.photobucket.com/albums/s346/rbjamie/Ubuntu/Tarrestoreissue.png[/IMG]

[IMG]http://tinypic.com/a/239mq/4[/IMG][IMG]http://tinypic.com/a/239mq/4[/IMG][IMG]http://tinypic.com/a/239mq/4[/IMG]This is not a deal breaker . . . I mean, everything still works . . . but it's particularly bothersome since I purposely want my /home mounted on that seperate partition to be the one that my apps draw my settings from.

Solutions I tried:

[LIST]
[*] As root, attempted to throw root /home into trash, thinking that perhaps apps and desktop would then draw on home on sda6 partition.  No go there since system wouldn't allow it because "home" was busy.  Duhhhh . . . in hindsight, I think this was pretty much a stupid bone head idea.  Thank goodness the system is smarter than a new user.
[*] Inserted a LiveCD, and attempted to remove the root /home, having the same bone headed idea as above.  No go of course.  It occurs to me now that these "/homes" are one and the same and whatever I do with one I do with the other.
[*] With the liveCD, attempted to use the umount command on /home.  But this second time I couldn't even navigate to it.  There was only the /home of the liveCD . . . so am not sure it was even my /home in the last try.
[/LIST]
   
Now I'm thinking that perhaps the solution to this is burried somewhere in the 107 pages of that thread.  Have to go back and wade through them.  Or maybe it's so obvious to someone experienced and they'll think to themselves, "Well, yaaaah, you idiot bonehead bozo, if you made that backup you restored with BOTH / and /home included, WHAT DID YOU EXPECT?"

My sense is that the solution would be obvious to an experienced user.

Here's what I'm thinking.  Maybe if I just make the tar backup of the /home directory and then restore that, plus mount it to that seperate partition (don't have a clue about how to mount it there) and also do a reinstall from a liveCD for the / directory, I may have what I want (which is what I had originally).  So before I do some more setting configs for my apps, I better wait and see if this approach has any merit.

I also have a SystemRescueCD . . . would that be something I might want to use?

And here's another problem I have, that may or may NOT be related, now that I've done this bone headed restore.

Thunderbird and Firefox are painfully slow to start and then manipulate, though my broadband connection is just fine (I mean web sites load as fast as before).  Before when I had a seperate mounting for /home, they loaded quickly and manipulated quickly (plus had a lot more extensions since I had made this restored backup some 4 months ago).  Opera, Chrome, and Epiphany start quickly, so it's only TB and FF that exhibit this behavior (which is why I say this may NOT be related, but since TB and FF loaded quickly before I'm thinking it may be related.)

I've set my Visual Effects to "None", but the problem persists.  My VGA controller is "Intel Mobile 4 Series Integrated Graphics Controller".  No NVIDIA or ATI or anything fancy . . . just the plain vanilla that came with this Dell Inspiron 15N laptop I have.

Am still troubleshooting this TB and FF issue, and have yet to try a clean profile for them to see if maybe something other than my restore issue is causing it.


So, let me see if I can distill the questions:

1.  Is there a way that I can get my system back to how it was (at that backup point 4 months ago, WITH the /home mounted on it's own partition), OTHER than starting to do my configs from square one?  Or have I hosed it completely and I'll just have to bite the bullet and start all over IF I want that /home mounted on its own partition?

2.  Do you think the TB and FF issues are related to the way I restored, and is troubleshooting them as a seperate issue just spinning wheels?

(Ubuntu 9.10, Kernel 2.6.31-21-generic, GNOME 2.28.1, 4GB RAM, Intel Dual Core T4200 @ 2GHz, 250GB HDD).

---

### Post by weirdtalk on 2010-06-01
1)
I'm a little lost so I'll ask to make sure. You want to setup up / (root) and /home on separate partitions and then restore the files from a backup you have already made of both / and /home?

If that is the case (don't do this if you don't have a backup of your stuff & make sure to not delete your backup with these steps! Also please check to make sure that your backup really does have your files. Maybe you can tell I've been burned by a bad backup in the past?)

first check to see if they are separate or not:
```
$>df
Filesystem           1K-blocks      Used Available Use% Mounted on
rootfs               914590120 627827368 267250044  71% /
/dev/sda3            914590120 627827368 267250044  71% /
rc-svcdir                 1024       176       848  18% /lib/rc/init.d
udev                     10240       284      9956   3% /dev
/dev/shm               1617664      2144   1615520   1% /dev/shm
/dev/sda1               101086     54252     44747  55% /boot
/dev/sdb1            961432072 564256920 348337152  62% /media/disk

```

this is a list of my mounted partitions (I have the combined root and home). If the were separate there wont be a /home in the right most column.

If the is no /home then empty the /home folder (REMEMBER, don't delete the backup! In other words, it had better not be in /home)
```
$> sudo rm -rf /home/
```

Create the new partition and format it. (I prefer GParted.)

Mount the new partition to the /home folder (I read the word "mount" as bind, if that helps you with the concept of mounting)
```
$> sudo mount /dev/sda8 /home
``` Be sure to change /sda8 with the correct number. 

*This will keep it mounted ONLY until you reboot. To make it permanent you need to edit /etc/fstab

Restore the backup. (If you used the 1st post's commands to backup both / and /home in a single tar, you can use the restore command from the same post without problems.)


2)
It could be related, possibly a plugin or setting that changed, but it also could be something else too. I'd look at it after you solved the first problem and see if that fixed it.

---

### Post by BobJam on 2010-06-01
> **weirdtalk said:**
> 1)I'm a little lost so I'll ask to make sure.Sorry for being so twisted . . . is probably good that you asked confirmation of your understanding.

I've seen threads where the responder or the OP misunderstood the whole situation, and went along 'till somebody said "Oh, that's what you're talking about.  I thought you meant . . . blah, blah, blah . . .".  So, let me see if I can clarify, and don't hesitate to ask for further expansion.

BTW, thanks for the response.  Sounds like you've been through the drill and seen the movie.

Am really hesitant to do any more "tweaking" to my desktop or apps (to get things the way I "like" them) UNTIL I get this settled.  So for now I'll just have to deal with this TB and FF slow start (is really aggravating) and not having settings for the way I like stuff.  Don't want have to do it all over again.

> **weirdtalk said:**
> You want to setup up / (root) and /home on separate partitionsYes, BUT let me expand a little on this.  I already have the two partitions, and that is what I had when things were showing the sda6 /home directory  was active (gkrellm):

[IMG]http://i45.tinypic.com/1zlc1th.jpg[/IMG]

> **weirdtalk said:**
> and then restore the files from a backup you have already made of both / and /home?Yes, AND understand that this backup .tar.gz.bz2 file does in fact include **BOTH** / and /home **in the one file**.  I think that's what you were saying, isn't it?

> **weirdtalk said:**
> don't do this if you don't have a backup of your stuff & make sure to not delete your backup with these steps!I have the backup on a USB stick, so there's no chance of deleting it with any manipiulation of the HDD.

> **weirdtalk said:**
> Also please check to make sure that your backup really does have your files.Yes, I've looked at it in Archive Manager.

> **weirdtalk said:**
> first check to see if they are separate or not:```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             83460412  28169264  51051604  36% /
udev                   1788500       372   1788128   1% /dev
none                   1788500       340   1788160   1% /dev/shm
none                   1788500       112   1788388   1% /var/run
none                   1788500         4   1788496   1% /var/lock
none                   1788500         0   1788500   0% /lib/init/rw
/home                 83460412  28169264  51051604  36% /home
/dev/sde1              3912180   3288760    623420  85% /media/7805-OEA8
/dev/sdb1              3918848   1129024   2789824  29% /media/Cruzer
/dev/sdd1              4013568   1079296   2934272  27% /media/49F0-4ABE

```this is a list of **MY** mounted partitions.

> **weirdtalk said:**
> If the is no /home then empty the /home folder.This is the part where I'm getting confused.  Looks to me like it's showing /home, but is it **only** on the root partition?  Which I guess would make sense since I restored it to the root.  (**I don't see any sda6 on this listing.**)

> **weirdtalk said:**
> REMEMBER, don't delete the backup! In other words, it had better not be in /home.While it IS on /home, I also have it stored on / AND the USB stick.  So I think I have it stored in enough places so that I can't be in danger of deleting.
> **weirdtalk said:**
> ```
$> sudo rm -rf /home/
```Create the new partition and format it.Now I'm really getting confused (sorry for being so dense on this).  So would I delete that separate home partition I have (shown as sda6 above in my image of GParted.) and make another? 

> **weirdtalk said:**
> Mount the new partition to the /home folder (I read the word "mount" as bind, if that helps you with the concept of mounting)
```
$> sudo mount /dev/sda8 /home
``` Be sure to change /sda8 with the correct number.So if can use my existing sda6 partition, can I use this command to mount /home as it has been restored in /?

> **weirdtalk said:**
> *This will keep it mounted ONLY until you reboot. To make it permanent you need to edit /etc/fstabSo what would be the line I would put in fstab and where would I put it in that fstab file?

> **weirdtalk said:**
> Restore the backup. (If you used the 1st post's commands to backup both / and /home in a single tar, you can use the restore command from the same post without problems.)I'm going to hold off on all this 'till you confirm you think this is the right way to go.   BTW, if I do this and it doesn't work, since it's my call I certainly wouldn't think it was your fault if it doesn't work.  IOW, you're off the hook since it's up to me whether or not to take your advice.  But as I said, it seems you've been through the drill and seen the movie, so I'm certainly inclined to take your kind advice.


> **weirdtalk said:**
> 2)It could be related, possibly a plugin or setting that changed, but it also could be something else too. I'd look at it after you solved the first problem and see if that fixed it.As I said, will have to tolerate TB and FF for now.  Good advice here, I think.

Thanks again for all the help.

Stay tuned, I guess.

---

### Post by BobJam on 2010-06-01
*Update*:  The backup.tar.bz2 file is now **ONLY** in my / directory, not my /home directory.  I could have sworn that I stored it in three places:  1) the / directory, 2)the /home directory, and 3)a USB stick.

But if the restore process mounted /home in the / directory, that might make sense that the file is now shown as only being in the / directory.  Not sure . . . just a novices speculation.

In any case, I still have it on the USB stick, so it is on removable media and safe from any HDD overwrites.

---

### Post by weirdtalk on 2010-06-02
well that's interesting. I thought that df would show it but you can use ```
sudo mount -l
``` to give a list of mounted items, and that way you'll be sure whether it is already mounted. My guess based on the sizes from df and gparted, you both / and /home on sda1.

Even if /dev/sda6 is not mounted it would be a good idea to mount it and see if the files are wanted or not. ```
sudo mkdir /media/six
sudo mount /dev/sda6 /media/six
cd /media/six
ls
```

> [QUOTE]Originally Posted by weirdtalk  
If the is no /home then empty the /home folder.
This is the part where I'm getting confused. Looks to me like it's showing /home, but is it only on the root partition? Which I guess would make sense since I restored it to the root. (I don't see any sda6 on this listing.)[/QUOTE]

No worries. The basic idea is: if we do NOT mount sda6 then /home is a normal folder and any files in /home are a part of sda1. If we DO mount sda6 to /home then /home is not really a folder it is a pointer or a link to sda6.

That in mind we cannot have /home be both a folder and a link so that is why I suggest emptying the /home folder (before sda6 is mounted)

after that is squared away, you can either use sda6 as is, empty it first, delete & remake it. Your choice, all are valid.

then mount /dev/sda6 /home
then to make permanent edit the fstab
```
sudo nano /etc/fstab
```

mine looks like this:
```
/dev/sda3               /                       ext4    user_xattr,noatime 1 1
/dev/sda1               /boot                   ext3    user_xattr,noatime 1 2
/dev/shm                /dev/shm                tmpfs   defaults        0 0
/dev/sda2               swap                    swap    defaults        0 0

```
so I would copy the first line and change sda3 to sda6 and / to /home (also change ext4 to match what format your using for sda6, your gparted looks like ext3)

then restore.

---

### Post by BobJam on 2010-06-03
@weirdtalk,

Wow, wow, wow . . . I followed your instructions EXACTLY in your post #5, and it . . . **WORKED**!!

My compliments and thanks.  Indeed, I would award you the first place blue ribbon for "most helpful post".  Thanks VERY VERY much.

There were a few hiccups along the way, which I'll detail in more posts (because I don't want to make this too lengthy) for not only maybe your benefit but for other novices that happen to find this thread because they're having a similar problem.

Perhaps my experience with these "hiccups" will show other novices what **NOT** to do.

In any case, I now have my /home bound to sda6, AND as you speculated, TB and FF are now back to their old lightening selves.

Thanks VERY much again.

---

### Post by BobJam on 2010-06-03
OK . . . this is not a "hiccup", rather an observation on weirdtalk's recommendation regarding accessing my sda6 files and saving the ones wanted to removable media.

For novices viewing this thread . . . **DO IT EXACTLY AS WEIRDTALK SHOWED THE PROCEDURE in post #5**:

```
sudo mkdir /media/six
sudo mount /dev/sda6 /media/six
cd /media/six
ls

```(Change "sda6" to whatever device you want to look at).  At first, when I looked at the portion of the line that was "/media/six", I thought "What the heck is he naming it that way for?"  My suspicion is that it could have just as well been something like "/frog/green", but until weirdtalk clarifies that, my recommendation is to do it **EXACTLY** as he has it.

The creation of that directory did indeed allow me to view the old files stored on sda6, and copy/paste the ones I wanted to save to removable media.  (The process was tedious, but it was worth it because I got to save some configs and files I had made SINCE I made that tar backup . . . the moral of that story is to do these backups more often then every four months).

In any case, that's a worthwhile exercise if you need some of those files, especially considering that restoring the tar will overwrite them (I think . . . better safe than sorry) and you may loose them forever if you don't put them on removable media.

---

### Post by BobJam on 2010-06-03
This is one of the hiccups and a really weird part.

Here's my fstab file BEFORE the success:[INDENT][COLOR=Blue][B][I]# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=1732db3c-6d49-455a-9d2f-34868aa658d6 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=0cf7ace8-d9ae-43f6-a410-6ebafb3a072d /home           ext3    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=f07345d7-f056-47e4-8bdc-6adce994574f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
usbfs         /proc/bus/usb usbfs   devgid=14,devmode=0660 0 0
# DazukoFS ...
# Example of mounting one dir onto dazukofs (directory to be protected by AVIRA Guard)
#/home/shared /home/shared dazukofs
/home    /home    dazukofs
# ... DazukoFS
[/I][/B][/COLOR][/INDENT][COLOR=Black]And then here's my fstab file AFTER the success:

[/COLOR][INDENT][COLOR=Blue][B][I]# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=1732db3c-6d49-455a-9d2f-34868aa658d6 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=0cf7ace8-d9ae-43f6-a410-6ebafb3a072d /home           ext3    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=f07345d7-f056-47e4-8bdc-6adce994574f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0[/I][/B][/COLOR]
[/INDENT]Coupla' comments on these two iterations.

First, you can see that most of the lines are just remarks.  Of particular interest are the remark lines that "[COLOR=Blue]***# / was on /dev/sda1 during installation***[COLOR=Black]"[/COLOR][COLOR=Black]and "[/COLOR][/COLOR][COLOR=Blue]***# /home was on /dev/sda6 during installation***[COLOR=Black]".

That just confirms what I knew all along anyway.

However, there is **NOT** an unremarked line making sda6 a permanent mounting in the fstab file AFTER the success, which has me baffled.

This baffles me particularly because as weirdtalk instructed, I added the line "[/COLOR][/COLOR]/dev/sda6                   /home                           ext3    user_xattr,noatime 1 1" to my fstab file to make the binding permanent.

I did this via ```
sudo gedit
``` so I could save it back.

Nevertheless, it doesn't show up in the fstab file now (see the "AFTER" listing).  So, how then does the system know where /home is mounted every time I boot up?

You'll also notice four references to the "DazukoFS" in the "BEFORE" fstab listing (and one of them is not remarked out: "[COLOR=Blue]***/home    /home    dazukofs***[COLOR=Black]") and a reference to "Avira".

That's what got me into this mess, and I'll detail that episode next.
[/COLOR][/COLOR]

---

### Post by aeiah on 2010-06-03
> **BobJam said:**
> 
However, there is **NOT** an unremarked line making sda6 a permanent mounting in the fstab file AFTER the success, which has me baffled.

its mounting it by UUID rather than sda6. partition names can change so this is good.

i think the reason your fstab didnt work before is because of the dazukofs bit and nothing more.

---

### Post by BobJam on 2010-06-03
My DazukoFS/Avira incident.  I highly recommend novices do **NOT** do what I did.

I realize that Ubuntu really doesn't need a virus checker, but being that I send a lot of emails to Windows users (and visit a lot of malware sites purposely to rate/investigate them for WOT), I am trying to be "socially responsible" and not pass any Windows infections via email to my Windows buddies (even though I think they're foolish to be using Windows).

So, that's my reason for using a virus checker.

Now I know that Ubuntu comes with ClamAV, but all that does is detect . . . and I wanted to see if I could find something that would **REMOVE** the malware.  (I don't even know if such an animal exists).

So I decided to try Avira, which has a Linux version.

It installed DazukoFS, which is a kernel patch that allows an antivirus checker to do real time scanning.  Though I wasn't looking for that particular feature, I figured "What the heck".  **BIG MISTAKE**!!

I don't know exactly how or why, but right after I did the Avira install, my sda6 went invisible.

I had been wanting to try the tar restore, and this was indeed a reason to do so.  That did not solve my problem, and I think it may have made it worse.

So that's why I made my OP here about the tar restore.

Fortunately, weirdtalk walked me through what turned out to solve the problem.

To reiterate to novices:  I recommend that you **NOT** try Avira 'till you get more experience and know how to get out of the trouble it may cause.

Anyway, I guess that's what I get for trying to be "socially responsible".  For now I'm just going to scan with ClamAV now and then, and give my Windows buddies a heads-up if there's any detections.

---

### Post by BobJam on 2010-06-03
> **aeiah said:**
> its mounting it by UUID rather than sda6. partition names can change so this is good.I was wondering if that was the case.

So UUID's can't be changed?  (I don't know why anyone would want to do that anyway, especially a novice).  Anyway, seems like changing the UUID would mess up all sorts of things, like maybe GRUB and the thing wouldn't even boot.

> **aeiah said:**
> i think the reason your fstab didnt work before is because of the dazukofs bit and nothing more.That's my suspicion too, though I don't have a clue about how that Dazuko stuff works, except that it modifies the kernel . . . and that can't be good for some things (like evidently trying to read another partition).

---

### Post by weirdtalk on 2010-06-04
> **BobJam said:**
>  At first, when I looked at the portion of the line that was "/media/six", I thought "What the heck is he naming it that way for?"  My suspicion is that it could have just as well been something like "/frog/green", but until weirdtalk clarifies that, my recommendation is to do it **EXACTLY** as he has it.

As you guessed naming does not matter.

---

### Post by BobJam on 2010-08-13
I don't know if this is going to get much response since the thread is over two months old and I'm burying this question on page 2, but I have a follow-up question on the same theme.

Now that I've gone through the trouble of restoring with a backup that includes BOTH / and /home, and then having to manipulate things to get back to a seperatre /home partition, how can I avoid this the next time?

It looks like the solution would be to make two seperate backups, as detailed in that Heliode thread [here]("http://ubuntuforums.org/showpost.php?p=208854&postcount=69").

Thoughts?

---

