---
title: "Installed Ubuntu 10.10 on SSD, need /home on HDD"
date: 2011-03-04
forum: New to Ubuntu
---

### Post by cobaltinfinity on 2011-03-04
Hi I just installed Ubuntu 10.10 on my 60GB SSD, looks gorgeous. I chose the basic option and told it to use the entire drive.

Then I created a 750GB partition on my Hard Disk and mounted it at **/media/HDD**

Two questions, gentlemen: 

[LIST=1]
[*][B] How do I move my /home folder to my Hard Disk so I don't fill up the SSD with docs/videos/junk etc?


[*] Ubuntu has also put a small 2.5GB Swap Space partition on the SSD. Was I unwise to allow it to do this given that it will require frequent writes, etc? Is it possible/recommended to move this Swap Space onto the Hard Disk too?[/B]
[/LIST]

Thanks so much for any suggestions! :):):):-\":P

---

### Post by fabricator4 on 2011-03-04
> **cobaltinfinity said:**
> Then I created a 750GB partition on my Hard Disk and mounted it at **/media/HDD**


[2]How do I move my /home folder to my Hard Disk so I don't fill up the SSD with docs/videos/junk etc?


Change the mount point from /media/HDD to /home  :-)

This is done in fstab.  The root of the second drive will become /home.  If you're not sure, post the contents of /etc/fstab

You'll need to move your user directory before rebooting.  You'll get an error if the user directory doesn't exist at boot time.  It's also a potential source of trouble if /username exists as a directory off the mount point and as a real directory off /home/username.  It would be best to boot the live CD then _move_ the username directory to the second drive, and change fstab before you reboot.

Keep a backup copy of /etc/fstab of course.

> 
[2] Ubuntu has also put a small 2.5GB Swap Space partition on the SSD. Was I unwise to allow it to do this given that it will require frequent writes, etc? Is it possible/recommended to move this Swap Space onto the Hard Disk too?[/B]


How much the swap file gets used depends on how much memory you have and how much memory you use, and if you use suspend mode etc.  

My understanding that the reliability off an SSD is actually higher than the reliability of a HDD.  Personally I have no problem having my swap file on the SSD in this machine.

Chris

---

### Post by seawolf167 on 2011-03-04
[Here]("https://help.ubuntu.com/community/Partitioning/Home/Moving") is a step-by-step guide for moving your home directory to a different partition

---

### Post by cobaltinfinity on 2011-03-04
> **fabricator4 said:**
> Change the mount point from /media/HDD to /home  :-)

This is done in fstab.  The root of the second drive will become /home.  If you're not sure, post the contents of /etc/fstab

You'll need to move your user directory before rebooting.  You'll get an error if the user directory doesn't exist at boot time.  It's also a potential source of trouble if /username exists as a directory off the mount point and as a real directory off /home/username.  It would be best to boot the live CD then _move_ the username directory to the second drive, and change fstab before you reboot.

Keep a backup copy of /etc/fstab of course.



How much the swap file gets used depends on how much memory you have and how much memory you use, and if you use suspend mode etc.  

My understanding that the reliability off an SSD is actually higher than the reliability of a HDD.  Personally I have no problem having my swap file on the SSD in this machine.

Chris

> **seawolf167 said:**
> [Here]("https://help.ubuntu.com/community/Partitioning/Home/Moving") is a step-by-step guide for moving your home directory to a different partition


Guys, that's absolutely amazing, it seems to have moved over like magic! Can't thank you enough. =D>=D>=D>

It was interesting going through the guide too, I've learned about a couple of commands I never heard of before. Bookmarked it for reference. Still blows my mind how fast and powerful the command line is when you know the magic words. 

Also I'm discovering the whole fstab thing. Right now my optical drive isn't mounting for some reason, although it shows up on the Disk Utility program ok. I suspect the solution will have something to do with fstab because currently there is no entry for it listed there. 

Thanks again guys!!! :P

---

### Post by jimmyjones on 2011-03-04
> **seawolf167 said:**
> [Here]("https://help.ubuntu.com/community/Partitioning/Home/Moving") is a step-by-step guide for moving your home directory to a different partition

I followed the guide and moved /home to a new partition.

I have a 32G SSD, I split it half, 15G for sda3, 14G for sda1, moved /Home to sda3

Now some questions.

When I moved the 3.5G that was Home to the other partition (sda3), I expected that my 'used' on sda1 would drop by the same amount (I deleted old_home directory from sda1). My used on sda1 is still 7.1G.

I booted to live USB and looked at Home on sda1, it's empty, as I expected, sda3 shows 3.4G as I expected.

What's still using 3.4G on sda1 ?

Can't seem to find it

---

### Post by jimmyjones on 2011-03-04
Found it.

Home_backup was in the root trash, which I couldn't see.

/root/.local/share/Trash

Booted recovery mode as Root and deleted them

Got my disc space back and now have a separate Home partition.

Thanks !

---

### Post by MrWylbur on 2012-02-27
My situation is very similar, I have added a SSD with Ubuntu 11.10.  Instead of upgrading, I did a new fresh install.  My original HDD drive is mounted in the machine, and contains my original home directory.  

Can I just change the home directory mount point to the old home directory and reboot, or do I have to copy the new home directory over the old home directory?  

Thanks!

---

### Post by audiomick on 2012-02-27
If your install is really fresh, it might be easier (if your old /home is a seperate partition) to just re-install and mount without formatting during the install the old home as the new home.

---

### Post by MrWylbur on 2012-02-28
The home directory contains all those hidden folders and files that run your stuff.  I need to just move the existing home folder then copy over all the files and stuff from the old to the new.  

I'm going to do the separate partition.  Thanks!

---

### Post by kaos2kx on 2013-02-05
Do these same procedures apply if I'm dual booting windows 7 from one drive, ubuntu 12.04 from a second drive, and want a third storage drive?  I'd like the storage drive to be equally accessible from windows or ubuntu.

---

### Post by wildmanne39 on 2013-02-05
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

