---
title: "How to fix only &quot;root&quot; can unmount /dev/sdf5 (external HD  backup) from /Media/Grsync"
date: 2010-04-02
forum: New to Ubuntu
---

### Post by mikodo on 2010-04-02
I mounted an USB external HD (/dev/sdf5) to /media/Grsync, to apply a backup with Grysnc. The backup seemed to go OK, but now when I click on the icon for the external disk to unmount it I get the message below; I had set the permissions for it @ 700 I guess that was wrong. Should I reset permissions for in chmod as: 

sudo chmod -R 777/media/dev/sdf5

 
I have no idea what to do next. Will it be OK to just power it down with my computer and then shut it off? Or maybe just shut it off with my desktop running?

Is there any way to shut down the external HD without the risk of loosing data because it was not unmounted first?

ERROR MESSAGE: Unable to unmount Backups umount: only root can unmount /dev/sdf5 from /media/Grsync


Thanks.

---

### Post by humanaut on 2010-04-03
I'd try chmod 666 and if all else fails gksu nautilus right click change permissions.

---

### Post by Encrypted_Soldier on 2010-04-03
Did you try using "sudo" and unmounting it manually?

---

### Post by Funnnny on 2010-04-03
> Will it be OK to just power it down with my computer and then shut it off? Or maybe just shut it off with my desktop running?

If you care about umount it, just power your com down an remove it.
Or you can sudo umount (I think it'll work)
> sudo umount /media/Grsync

---

### Post by mikodo on 2010-04-03
Below are screenshots of df -h and of /etc/fstab, both showing the HIGHLIGHTED  mounted external HD that I want to "unmount". At this stage, all I want to do is unmount it from /media/Grysnc and reclaim the ext. HD and not go ahead with using it for Grsync. Please post any easy way to do this.

Thank you.

---

### Post by mikodo on 2010-04-03
> **Funnnny said:**
> If you care about umount it, just power your com down an remove it.
Or you can sudo umount (I think it'll work)

nope, sudo umount didn't do it.

---

### Post by yetiman64 on 2010-04-03
Try 

```
sudo umount /dev/sdf5
```Or if that fails, it looks like sdf5 is a partition on /dev/sdf, and you may have to try

```
sudo umount /dev/sdf
```to unmount the "whole" USB stick (sorry USB HDD)

---

### Post by mikodo on 2010-04-03
> **yetiman64 said:**
> Try 

```
sudo umount /dev/sdf5
```Or if that fails, it looks like sdf5 is a partition on /dev/sdf, and you may have to try

```
sudo umount /dev/sdf
```to unmount the "whole" USB stick (sorry USB HDD)

I ran the first code and it unmounted the HD with no icon on the desktop. Powered off the HD and repowered and there was no icon. Ran 

sudo mount /dev/sdf5

 and it is back mounted, but will not unmount again without running

 sudo umount /dev/sdf5 

again. I'll try your second code and report.

When I ran the second code 

sudo umount /dev/sdf 

it says that it is not mounted; though the icon is still on the desktop and cannot be unmounted.

Thanks.

EDIT: Why doesn't my # code feature work when I try it??? Sorry for the code in regular print.

---

### Post by yetiman64 on 2010-04-03
When plugging in a USB HDD it should be automounted (by mtab). However it sounds if the HDD is partitioned and that may be causing some sort of problem with this process. Someone more Avanced than myself should probably talk you through this one. 

Anyone ???

Regards

> EDIT: Why doesn't my # code feature work when I try it??? Sorry for the code in regular print.Use the Go Advanced Button

Acknowleging thanks in post #10 without reposting.  Bye

---

### Post by mikodo on 2010-04-03
Thanks for the help yetiman64!

---

### Post by mikodo on 2010-04-03
Well, I must have really messed up the mounting of my usb HD. I can only mount it by root. Also, I can mount or unmount in root by either:



sudo mount /dev/sdf5  and unmount by sudo umount /dev/sdf5  


                       and                      


sudo mount /media/Grsync  and unmount by sudo umount /media/Grsync



I keep getting errors that the 500 GB Filesystem can only be mounted by root.

So, that's it. Sorry, I still can't seem to find the Go Advanced Button or find any other way to present proper code boxes.

Thank you.

---

### Post by da burger on 2010-04-03
Mounting is something only root can do anyway. You should always need sudo to mount or unmount. I know this is a rubbish work around but could you put a launcher on your desktop that runs```
gksudo umount /dev/sdf5
```.

To use the code boxes press the "#" button. Then put the code inside the [.CODE] and [./CODE] without the dots. If the button doesn't work you can put the tags in manually

---

### Post by mikodo on 2010-04-03
I can live with 


sudo (u)mount /dev/sdf5 


to unmount and mount the ext. HD. Is it safe and usable to do it this way, for backups in Grsync. What I mean is if I have to get my data returned to my /home because I botched it somehow, will it still be available from the ext.HD, doing it this way?

Thanks.

---

### Post by mikodo on 2010-04-03
I am guessing doing backups this way is OK. I am able to delete data on my desktop and run Grsync and have it returned in the backup sequence.

Sure don't know what I did to cause this behaviour though; or why the heck the code boxes don't work for me any more.

Thanks everyone.

---

### Post by yetiman64 on 2010-04-03
Mikodo,  Best to read this completely before entering anything  to see if it suits (its a bit long :))
I just noticed the screenshot of fstab (That is what's locking the drive to roots control). fstab is used to mount fixed filesystems. Whereas mtab handles the mounting/unmounting of external devices (you are now wanting to use the device as a normal USB drive - is that correct?).

Did you put that entry in there yourself? If so it may have to be removed or mtab will not process the mounting - sounds like whats happening.

First thing you should try is #ing out the entry.

If connected unmount it as before with

In terminal enter

```
sudo umount /dev/sdf5
```Enter your password

and I'd suggest unplugging it when unmounted.


Then enter

```
gksudo gedit /etc/fstab
```You may not have to enter a password 2nd time (though not sure with one command sudo then gksudo) I suspect not though.

At the line

> /dev/sdf5    /media/Grsync   ext4    defaults  0       0insert a #  -this stops fstab processing it on every bootup and is likely whats stopping its automounting.

it should look like

> #/dev/sdf5    /media/Grsync   ext4    defaults  0       0Save then close the file.

Try plugging the device in again. I suspect by the 5 in sdf5 that mtab might mount more than one partition, so you could end up with multiple partitions mounted as individual "drives". It should mount them all on your desktop as usual, And they all should appear as USB drives.

May be worth a try if you want to avoid the previous workarounds.

Good Luck and Hope this works.

Edit: An extra bit of info is if this works you'll be able to unmount any unneeded "drives" by right clicking and choosing "Unmount" through nautilus or the desktop icon. Also to remount should be as easy as going to Places > Removable Media then click on the drive. When initially plugging in be a bit patient as it might take a while to register the new drives with the system. [COLOR=Blue]Also you may have to then change some permissions to write to the partitions though not to sure yet. I also don't know what effect this will have on Grsync backups as /dev/sdf5 will no longer mount to /media/Grsync - probably should check out about using Grsync to external devices before trying this (though it may be as simple as pointing Grsync to the new folder in /media -- best to make sure 1st). Also check if ext4 filesystem mounting is possible on external drives I think so but am not completely sure of it.
[/COLOR]

---

### Post by mikodo on 2010-04-03
Oh my goodness yetiman64; you are exactly correct in guessing I had entered a line in /etc/fstab for Grsync. Unfortunately, I continued to play on the computer untill 08:00 in Canada here, for a total of ~20 continuous hours on the computer. At the end, I was as a newbie, trying some of the options of Grsync and wound up deleting all of my data on my /home, except for Desktop and lost and found. Of course I had deleted my previous Sbackup information from my external HD backup in preparation of using Grsync. So I had no backup yesterday and lost the data. I found that using a Live CD of Karmic showed just the same data in /home, just Desktop and Lost and Found. I booted into Hardy on the same drive and Gparted showed next to no data in the Karmic partitions also. So figuring that the data was gone, I used Gparted in Hardy to delete the Karmic partitions to just use Hardy until I had time to do a fresh install of Karmic or Lucid. Then rebooted Hardy and found that my Grub Loader wouldn't load, and I didn't know what to do next, and went to bed. I got up after a few hours, emptied my HD with a Live CD of Gparted and reinstalled Karmic just now. 

Now, all this is not a great loss, because I had no pictures, music, videos, of any sort on this, my only computer. I am truly new to computers and am trying to learn the basics of Unix systems first, before playing with toys like pics, music, downloading video binaries, etc. So, this is just another learning experience for me. 

I didn't closely read your post about editing out the line in Fstab et al, I **certainly** will be reading it closely in the future when I learn to edit Fstab later.

```
Guess what. I just used the icons up in the top of page and the Bold icon worked as it should, so probably the code feature will also. The new install seemed to fix that for me.
```

So.., thank you so very much for your interest in my difficulties, your work in trying to help me solve the problem(s), and your time and effort in all of this; All very much appreciated!

So on to starting over; Again!

Mike

---

### Post by mikodo on 2010-04-03
Double post

---

### Post by mikodo on 2010-04-03
Code:

```
sudo umount /dev/sdf5
```

Enter your password

and I'd suggest unplugging it when unmounted.


Then enter

Code:

```
gksudo gedit /etc/fstab
```

Yes that would have fixed it. I was trying to put a # in front of the line, just didn't know how to use it to edit/etc/fstab with gedit. Now I have a record here in the forums how to do it

Thanks again,

Mike

PS: Please read my earlier post on what I finally wound up doing. Also, I just turned on my attached external usb HD and mtab didn't recognize it. I will be using your fix for it earlier than I thought.

CHIMO!

---

### Post by yetiman64 on 2010-04-03
> PS: Please read my earlier post on what I finally wound up doing. Also, I just turned on my attached external usb HD and mtab didn't recognize it. I will be using your fix for it earlier than I thought.
Yes I've read your past posts. Its unfortunate about the backup loss, but unfortunately these things can happen, best if we learn from the experience though.

I hope you end up with an easier to use USB HD, just pay close attention to the highlighted comments as I know nothing about using Grsync.

If you try this and it works you may have to alter some permission changes for writing to the "drives", as I've noticed in the past how mtab when first mounting a new drive seems to use pretty tight defaults. Once you set the new permissions (if you need to) the changes you make should be remembered by mtab for the partition (even after future disconnects / reconnects). 

Technical: Also I think that fstab and mtab are really only configuration files for whatever process that does the mounting/unmounting. 

I just hope my descriptions don't lead you astray in the future. I'm not far out of beginner stage myself (ie if I am out yet) after 2 1/2 years (since Gutsy 7.10)

Nev 
 Edit: Just got you're VM. You're Welcome.

---

### Post by mikodo on 2010-04-05
> **yetiman64 said:**
> Mikodo,  Best to read this completely before entering anything  to see if it suits (its a bit long :))
I just noticed the screenshot of fstab (That is what's locking the drive to roots control). fstab is used to mount fixed filesystems. Whereas mtab handles the mounting/unmounting of external devices (you are now wanting to use the device as a normal USB drive - is that correct?).

Did you put that entry in there yourself? If so it may have to be removed or mtab will not process the mounting - sounds like whats happening.

First thing you should try is #ing out the entry.

If connected unmount it as before with

In terminal enter

```
sudo umount /dev/sdf5
```Enter your password

and I'd suggest unplugging it when unmounted.


Then enter

```
gksudo gedit /etc/fstab
```You may not have to enter a password 2nd time (though not sure with one command sudo then gksudo) I suspect not though.

At the line

insert a #  -this stops fstab processing it on every bootup and is likely whats stopping its automounting.

it should look like

Save then close the file.

Try plugging the device in again. I suspect by the 5 in sdf5 that mtab might mount more than one partition, so you could end up with multiple partitions mounted as individual "drives". It should mount them all on your desktop as usual, And they all should appear as USB drives.

May be worth a try if you want to avoid the previous workarounds.

Good Luck and Hope this works.

Edit: An extra bit of info is if this works you'll be able to unmount any unneeded "drives" by right clicking and choosing "Unmount" through nautilus or the desktop icon. Also to remount should be as easy as going to Places > Removable Media then click on the drive. When initially plugging in be a bit patient as it might take a while to register the new drives with the system. [COLOR=Blue]Also you may have to then change some permissions to write to the partitions though not to sure yet. I also don't know what effect this will have on Grsync backups as /dev/sdf5 will no longer mount to /media/Grsync - probably should check out about using Grsync to external devices before trying this (though it may be as simple as pointing Grsync to the new folder in /media -- best to make sure 1st). Also check if ext4 filesystem mounting is possible on external drives I think so but am not completely sure of it.
[/COLOR]
Just a quick update on this. Since I completely reinstalled Karmic to the internal HD, I now, have no lines in etc/fstab that reflects anything about Grsync. I continue to get permission errors when trying to run Grsync with the connected usb HD. I disconnected and reconnected the HD from the computer and still get the errors about permissions with Grsync after being it beingrun. I am not able to click on the icon for the external HD and unmount it either, after using Grsync. I disconnected that external HD and connected a spare I had laying around with all the same problems with the first HD.  I tried another usb port and had the same results. So, I guess the problem lies on how I set the permissions for using Grsync, I dunno?? and don't know what to do about that. I suppose I could continue to use Grsync as root, with mounting and unmounting the externalHD(s), and running Grsync that way, but I don't want to do that. Probably I would run in to some other kind of permission problems down the road.

I connected both of these HD's to the computer separately of each other after removing Grsync/rsync from the computer, and in both instances, I was able to "normally" mount and unmount them. I used both of external HD's independent of other with Sbackup, for continued backup assurance and both times they worked as always, with no change in behaviour, from when I used them for backups with the Sbackup utility in the past.

So, for now I am out of luck and patience trying to run Grsync, and will continue to use Sbackup for backups, until I can figure out the permissions problems with Grsync/rsync, or decide to use another utility for backups all together. 

Thanks everyone.

---

### Post by kimonworkbox on 2011-12-18
If you would like a speedy fix, I recommend MountManager, a GUI fstab editor. Available in the respository. It will save you from manually modifying a corrupted fstab.

I had two NTFS file systems that refused to mount in Ubuntu, one was a Windows 7 bootable partition, the other an external Western Digital terabyte  USB drive. Things went bad after the system froze (a rare event in Ubuntu) and they were not cleanly unmounted.

The options I selected in MountManager for each of these device partitions (sda2 and sdb1) were:

* Deselect: Allow mandatory locks on the file system
* Select: Attempt to mount an already mounted file system 
* Change: Who can mount the file system (from administrator to everybody)

Select Partition Menu > Apply
Then select Partition Menu > Mount (this enables another Mount button over on the right near the mount point menu that also needs to be clicked)

This allowed successful mounting for me. No more errors. I suspect the original error was related to running out of disk space.

It would be recommendable to ensure that "Allow mandatory locks on file system" is reselected and applied to any relevant partitions after successful mounting. (And mount privileges as preferred).  

*As with all partitioning & mounting applications - use @ your own risk.

---

### Post by howefield on 2011-12-18
Thanks for replying, but as a thread getting on for 2 years old, we'll put it to sleep.

---

### Post by lisati on 2011-12-18
> **kimonworkbox said:**
> If you would like a speedy fix, I recommend MountManager, a GUI fstab editor. Available in the respository. It will save you from manually modifying a corrupted fstab.

A speedy fix probably would have been useful 18 months ago...... :D

Thread closed.

---

