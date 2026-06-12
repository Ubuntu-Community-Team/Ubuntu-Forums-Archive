---
title: "HELP!  autoremove has killed my OS!"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by myolbug on 2009-12-30
I have occasionally run sudo apt-get autoremove.  I ran it last night and then was online for while and shut down the computer.  Now, it will not boot!!!
Ubuntu 9.10 and the kernel is 2.6.31-16 with the latest updates.  It looks like it will boot and it will show the Ubuntu circle thing then it just hangs on a flashing cursor.

The on;ly other thing that I have done is when I went to boot this AM, I clicked on the little man on the lower right, this then popped up an options window.  I selected increase contrast/colors and then deselected it.  I couldn't get it to go back to the normal contrast, so I rebooted it from the logon screen.  This is when the problem started.

I chose to run the recovery mode and it basically just flashed a bunch of errors.

What the hell happened?
Is there anything I can do at command line to fix this?

---

### Post by Paqman on 2009-12-30
> **myolbug said:**
> 
I chose to run the recovery mode and it basically just flashed a bunch of errors.


It's normal to tons of scrolling text in recovery mode. Eventually it should give you the option to "drop to a root shell with networking", that'll give you a command line. Once you're at this command line you could try:
```
apt-get install ubuntu-desktop
```

(obviously if you want Xubuntu of Kubuntu the it's xubuntu-desktop and kubuntu-desktop respectively)

---

### Post by myolbug on 2009-12-30
I am running Recovery mode again, but the first time I ran it, it just kept displaying (media error) , DRDY ERR and error UNC, also, when recovery mode was done, the screen was just blank, nothing on it.

It also is showing configured for UDMA 133.  It is showing other errors.  It looks like all of a sudden my hard drive is unable to be read.  Unable to read inode xxx and others

---

### Post by MooPi on 2009-12-30
Before you try to install a new desktop, let's just try to update and upgrade and.
At console recovery```
 sudo apt-get update
``````
sudo apt-get upgrade
```
If this isn't possible it is probably time to check your disk for errors. Boot from live CD and open terminal > e2fsck -f -c -v /dev/sda1
where  /sda1   represents your hard drive, so change to fit your system

---

### Post by myolbug on 2009-12-30
I don't have anyway of entering code, my screen is blank.

Never mind, the screen went into a blank screensaver mode, recovery is still running.

---

### Post by myolbug on 2009-12-30
Okay, here are a couple of other error messages:
EXT - fs error (device sda1): ext3 get_inode_loc unable to read inode xxx
unrecovered read error auto reallocate failed

---

### Post by myolbug on 2009-12-30
I hope it isn't my HD, the PC isn't even and year old.

---

### Post by MooPi on 2009-12-30
It sounds like you have a disk error or bad sector on the hard drive. I've never attempted to fix a  file system but this same utility has a repair feature. so don't despair yet.

---

### Post by myolbug on 2009-12-30
Well, recovery is still running...  Takes a while, huh?

---

### Post by MooPi on 2009-12-30
glad to see your still here, thought I lost you.
Any messages as it checks the drive ?

---

### Post by myolbug on 2009-12-30
Nothing new, I think it is going through the drive bit by bit...

I am really happy I just bought my son a laptop for Christmas!

---

### Post by myolbug on 2009-12-30
Right now it is hanging up on [5293.480330] EXT3-fs error (device sda1):  ext3_get_inode_loc: unable to read inode block - inode=9281626, block=37126151

Should I just wait to see if it does something else?  It isn't doing anything anymore.

---

### Post by MooPi on 2009-12-30
Be prepared for round two. If it comes back with uncorrected errors you will need to execute another step. ```
e2fsck -p
```This is the repair process I spoke of. Let me know before you attempt please.

---

### Post by myolbug on 2009-12-30
Yeah right now, it is just stuck on my previous post.  Nothing has happened.

---

### Post by MooPi on 2009-12-30
Are you able to enter any command?
Try to start the next step     e2fsck -p

---

### Post by myolbug on 2009-12-30
I am unable to do anything, the cursor is just blinking like it is supposed to do something, but nothing is happening.

---

### Post by MooPi on 2009-12-30
I have to admit I'm in uncharted territory here and would feel guilty if I gave you bad advice. I can only suggest to dig deeper in the forum for a solution or punt and reboot. with the hope that everything works. Your in a pickle here and I'm not that qualified to give a definitive answer.

---

### Post by myolbug on 2009-12-30
Would it help if I tried booting into an older kernel?

---

### Post by MooPi on 2009-12-30
I've put out a call for help and hope someone else joins. That does sound possible but am doubtful that would be a solution.
Need to step away for about 20 minutes, hope things work out before I return.

---

### Post by myolbug on 2009-12-30
Yeah I tried the older kernel thing.  Nothing happened.

---

### Post by MooPi on 2009-12-30
If you can get back to recovery try the last command ```
e2fsck -p
```Correction don't attempt in recovery but from LIVE CD

---

### Post by myolbug on 2009-12-30
If I put in a live CD and select repair a broken system, will I run the risk of losing the contents of my drive?

---

### Post by MooPi on 2009-12-30
I don't know enough about hard drive structure to answer that question, but I will stand by my last post before I would attempt to repair a broken system. My reason for saying this is due to your hard drive errors. Your system may hang no matter of repair will help.

---

### Post by myolbug on 2009-12-30
So, how would I do this?  I can drop to command line, but I don't know what to do there.  Recovery mode just hangs, I finally hit ctrl alt delete and the system rebooted.

---

### Post by MooPi on 2009-12-30
If you can boot back to Live CD and repeat the process started earlier with ```
e2fsck -p
``` This is supposed to be the repair function. Hopefully this will correct the drive and allow for a normal boot.

---

### Post by MooPi on 2009-12-30
> **myolbug said:**
> If I put in a live CD and select repair a broken system, will I run the risk of losing the contents of my drive?
I'm sorry I believe I misunderstood this post. I don't believe that this will destroy your system, but only repair the file structure.

---

### Post by grenobel on 2009-12-30
> **myolbug said:**
> If I put in a live CD and select repair a broken system, will I run the risk of losing the contents of my drive?

No, data locations on the disk will just be remapped to different areas of the disk - unless there is major damage to your hard drive. In that case, the damage is already done. At that point an auto repair using a file system check will recover any usable data and then relocate that information.

---

### Post by MooPi on 2009-12-30
> **grenobel said:**
> No, data locations on the disk will just be remapped to different areas of the disk - unless there is major damage to your hard drive. In that case, the damage is already done. At that point an auto repair using a file system check will recover any usable data and then relocate that information.
Thank you for the assistance !

---

### Post by myolbug on 2009-12-30
If I use the CD, I get the following options:
Install Ubuntu
Check Disc for Defects
Test Memory
Boot from first hard disc
rescue a broken system


I select rescue and then follow the prompts.  I am then given the choice of:
Device to use as root file system;
/dev/sda1
/dev/sda2
/dev/sda5
do not use a root file system

sda1 is my hdd, but I don't know about the others what now?

---

### Post by grenobel on 2009-12-30
You can use /sda5 as that is the default location for the swap space.

---

### Post by myolbug on 2009-12-30
I get:

An error occurred while mounting the device you entered for your root file system (/dev/sda5) on /target.

Please check the syslog for more information.

Back                           Continue

---

### Post by Swagman on 2009-12-30
If that was me I'd boot into a live environment and see if I can access the hard drive. Saving out any files I want to keep. You can't save to the live cd so save em on the cloud or a dropbox.

Then..... Nuke it and start again. But it doesn't sound good. Did you do a dirty shutdown ?

---

### Post by myolbug on 2009-12-30
I m downloading the 64 bit desktop cd currently.  
If anyone has a link to the 64bit live cd, (if it is different than what I am downloading) I'll take it.

I had to go to Ubuntu 64bit alternative.  Trying to access it normally on my son's laptop only gives me the 32 bit option.

If I select /dev/sda1, it brings me to these options:

Execute a shell in /dev/sda1
Execute a shell in the installer environment
Reinstall GRUB boot loader
Choose a different root file system
Reboot the system

Which should I do?

---

### Post by myolbug on 2009-12-30
How do I boot into a live environment?

---

### Post by myolbug on 2009-12-30
bump?

---

### Post by MooPi on 2009-12-30
Insert the boot/Live CD used for installation.

---

### Post by myolbug on 2009-12-30
Okay, I have one that is beta, which I have been using, see above posts, but I am downloading anther one, but the server I am connected to is ridiculously slow.

---

### Post by myolbug on 2009-12-30
can I use the 9.10 beta for this?  I am not given the option to run it off of the disc.

---

