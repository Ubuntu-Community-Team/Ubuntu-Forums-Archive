---
title: "no space for updates"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by Jgraber613 on 2009-05-28
I am new to Ubuntu and created a dual boot w/Windows XP on my computer.  Ubuntu worked fined for a few days and then the update manager popped up and indicated the need for some updates.  I clicked ok and got a msg that there was no more disk space and I needed 80 M.    The msg also suggest emptying trash (it was empty) and running sudo apt-get clean ( I could not figure out what this means). But checking my computer, it has 4.1G of free space on drive C;  but the "file system" lists 0 free.

Please -- how do I rectify this?  Thanks

Jeff Graber
[EMAIL="jgraber@email.com"]jgraber@email.com[/EMAIL]

---

### Post by philinux on 2009-05-28
In ubuntu open a terminal and post the results of this.

```
df -h
```

---

### Post by 3rdalbum on 2009-05-28
Space on your Windows partition ("C:\") doesn't count - that's Windows' space.

Go into the terminal (Applications > Accessories > Terminal) and type (or copy and paste) this:

```
sudo apt-get clean
```

---

### Post by drs305 on 2009-05-28
This wiki discusses how to find out why your free space may have disappeared and how to 'regain' it:
[https://help.ubuntu.com/community/RecoverLostDiskSpace]("https://help.ubuntu.com/community/RecoverLostDiskSpace")

---

### Post by Jgraber613 on 2009-05-31
> **philinux said:**
> In ubuntu open a terminal and post the results of this.

```
df -h
```
jgraber@jgraber-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             2.3G  2.3G     0 100% /
tmpfs                 249M     0  249M   0% /lib/init/rw
varrun                249M   92K  249M   1% /var/run
varlock               249M     0  249M   0% /var/lock
udev                  249M  148K  249M   1% /dev
tmpfs                 249M   76K  249M   1% /dev/shm
lrm                   249M  2.4M  247M   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M   20K 1004K   2% /tmp
/dev/sda1              17G   13G  4.2G  75% /media/Drive_C
jgraber@jgraber-desktop:~$ 
jgraber@jgraber-desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda6              2403388   2272040      9260 100% /
tmpfs                   254756         0    254756   0% /lib/init/rw
varrun                  254756       104    254652   1% /var/run
varlock                 254756         0    254756   0% /var/lock
udev                    254756       148    254608   1% /dev
tmpfs                   254756        76    254680   1% /dev/shm
lrm                     254756      2392    252364   1% /lib/modules/2.6.28-11-generic/volatile
overflow                  1024        20      1004   2% /tmp
/dev/sda1             17438526  13070083   4368443  75% /media/Drive_C
jgraber@jgraber-desktop:~$ df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda6     ext3    2.3G  2.2G  9.1M 100% /
tmpfs        tmpfs    249M     0  249M   0% /lib/init/rw
varrun       tmpfs    249M  104K  249M   1% /var/run
varlock      tmpfs    249M     0  249M   0% /var/lock
udev         tmpfs    249M  148K  249M   1% /dev
tmpfs        tmpfs    249M   76K  249M   1% /dev/shm
lrm          tmpfs    249M  2.4M  247M   1% /lib/modules/2.6.28-11-generic/volatile
overflow     tmpfs    1.0M   20K 1004K   2% /tmp
/dev/sda1  fuseblk     17G   13G  4.2G  75% /media/Drive_C


Thank you all for your replies.....
Please help me understand what I should do with this information!!
Jeff

---

### Post by Jgraber613 on 2009-05-31
> **3rdalbum said:**
> Space on your Windows partition ("C:\") doesn't count - that's Windows' space.

Go into the terminal (Applications > Accessories > Terminal) and type (or copy and paste) this:

```
sudo apt-get clean
```
Thanks for your support.  I tried it and nothing seemed to happen.... Please advise.
jgraber@jgraber-desktop:/dev$ sudo apt-get clean
jgraber@jgraber-desktop:/dev$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda6              2403388   2276728      4572 100% /
tmpfs                   254756         0    254756   0% /lib/init/rw
varrun                  254756       104    254652   1% /var/run
varlock                 254756         0    254756   0% /var/lock
udev                    254756       148    254608   1% /dev
tmpfs                   254756        76    254680   1% /dev/shm
lrm                     254756      2392    252364   1% /lib/modules/2.6.28-11-generic/volatile
overflow                  1024        20      1004   2% /tmp
/dev/sda1             17438526  13070084   4368442  75% /media/Drive_C

---

### Post by tommah04 on 2009-05-31
my guess is that when you chose partitions (side by side) you didn't give enough space to ubuntu.... you could either re-install, or I believe there's a program that lets you resize partitions

---

### Post by drs305 on 2009-05-31
The results show your system partition to be less than 3GB. The free space remaining on your Windows partition is only 4G. It would be a tight fit but is possible if you want to be very tight on both OS's. You could probably use gparted to trade some of your Windows space but now you would have two systems, both of which would be almost maxed out on available space. A bigger hard drive is probably the best solution.

To get a good idea of what type of space you have, open gparted and look at it graphically. System, Administration, Partition Editor, or "gksudo gparted". You can also see it graphically via System, Administration, System Monitor > File Systems tab.

---

### Post by Jgraber613 on 2009-06-16
Thank you all.  I went searching for the instructions for re-installing but did not find exactly what the instructions I am comfortable with.  
Do I un-install and then re-install?
I have two hard drives.
I cleaned up a lot of old windows files on the drive that Ubuntu loaded so there is more space.  Do I need to re-partition? 
Should I format that drive?
I have no files on the Unbuntu partition I need to save. Just need to re-install.
Thanks.

JG

---

### Post by drs305 on 2009-06-16
> **Jgraber613 said:**
> 
Do I un-install and then re-install?
I have two hard drives.
I cleaned up a lot of old windows files on the drive that Ubuntu loaded so there is more space.  Do I need to re-partition? 
Should I format that drive?
I have no files on the Unbuntu partition I need to save. Just need to re-install.
Thanks.
JG

You most likely have to repartition and increase the size of the original ubuntu partition. We would have a better idea if you ran the following and tell us which partition you are planning to use:
```

sudo df -Th | grep "/dev/sd" | sort

```

Or better yet, a screenshot of the drive as displayed in "gparted".

You can let the install disk do the repartitioning but I prefer to have things set up with gparted before I start the installation just so I know exactly how it is going to be done.

---

### Post by Jgraber613 on 2009-06-17
jgraber@jgraber-desktop:/dev$ sudo df -Th | grep "/dev/sd" | sort
/dev/sda6     ext3    2.3G  2.2G  2.9M 100% /
jgraber@jgraber-desktop:/dev$ ls -a sd*
sda  sda1  sda2  sda5  sda6  sda7

gparted keeps running with the message "searching /dev/sda partitions.  

I'm thinking I should just re-install.  Do I have to un-install before I re-install?

Thanks.

JG

---

### Post by Jgraber613 on 2009-06-17
jgraber@jgraber-desktop:/dev$ gksudo gparted
error: libhal_acquire_global_interface_lock: org.freedesktop.Hal.Device.InterfaceAlreadyLocked: The interface org.freedesktop.Hal.Device.Storage is already exclusively locked either by someone else or it's already locked by yourselfjgraber@

oops!  Perhaps I should just re-install.  Do I have to uninstall before I re-install?

Thanks

JG

---

### Post by drs305 on 2009-06-17
> **Jgraber613 said:**
> jgraber@jgraber-desktop:/dev$ gksudo gparted
error: libhal_acquire_global_interface_lock: org.freedesktop.Hal.Device.InterfaceAlreadyLocked: The interface org.freedesktop.Hal.Device.Storage is already exclusively locked either by someone else or it's already locked by yourselfjgraber@

oops!  Perhaps I should just re-install.  Do I have to uninstall before I re-install?

Thanks

JG

No you don't. During the partitioning section just make sure you have the system format the / partition by checking the 'format' box (if you are manually partitioning the install).

---

### Post by Jgraber613 on 2009-06-18
[IMG]file:///tmp/moz-screenshot.jpg[/IMG][IMG]file:///tmp/moz-screenshot-1.jpg[/IMG]hi
I am sorry to be such a newbie.  I tend to write in too much short hand.  there are two hard drives in my computer.  I would like to keep windows OS on one (C).  I deleted or moved most of the windows files from the other (D) so there is an additional 5 G of free space.  When I start going through the install, I get to the attached form.  It does not give me the option of applying the free space to the Ubuntu install. It does not let me make it bigger.  Please advise.

Thanks
JG

---

### Post by Jgraber613 on 2009-06-18
> **drs305 said:**
> The results show your system partition to be less than 3GB. The free space remaining on your Windows partition is only 4G. It would be a tight fit but is possible if you want to be very tight on both OS's. You could probably use gparted to trade some of your Windows space but now you would have two systems, both of which would be almost maxed out on available space. A bigger hard drive is probably the best solution.

To get a good idea of what type of space you have, open gparted and look at it graphically. System, Administration, Partition Editor, or "gksudo gparted". You can also see it graphically via System, Administration, System Monitor > File Systems tab.

Well I reinstalled and it did not change the size.  I went to look for "System, Administration, Partition Editor", and it is not there!

When I type "gksudo gparted" in a terminal window, nothing happens.

Please help.

Thanks 

JG

---

### Post by csl5010 on 2009-06-18
I had the same issue before using dual boot partition.
The problem is the windows OS occupied all the hard disk space. So ubuntu partition automatically get the rest of the space - which is very minimum.
What you can do is resize the windows partition size. Or, I totally overwrite it. Ubuntu is my only OS now.

---

### Post by nandemonai on 2009-06-18
> **Jgraber613 said:**
> Well I reinstalled and it did not change the size.  I went to look for "System, Administration, Partition Editor", and it is not there!

When I type "gksudo gparted" in a terminal window, nothing happens.

Please help.

Thanks 

JG

```
sudo apt-get install gparted
```

That said, you can't resize partitions while they're in use. To resize a / partition you'll need to do it from the liveCD.

---

### Post by presence1960 on 2009-06-18
gparted is not installed by default. if you want to run it from Ubuntu (not the Live CD) you must first install it by opening a terminal and running ```
sudo apt-get install gparted
```

You can resize your windows partition from Ubuntu, just make sure it is not mounted!

By the looks of your hard disk you are pretty much maxed out.

---

### Post by Jgraber613 on 2009-06-19
well, I installed and tried to run "System, Administration, Partition Editor", and it is not displaying the partitions. It keeps saying "searching dev/sda/ partitions."  It has been doing that for a few hours now!!!!

That second disk has over 5 G of free space to add to the 2.5 that Ubuntu took.
Is there no way I can just remove Ubuntu completely and start from 0?  or should I reformat that second disk and have the C drive be Windows and the D drive be Ubuntu?  And how should I format the second disk?

Thanks.  It is great having all you helpers out there.

JG

---

