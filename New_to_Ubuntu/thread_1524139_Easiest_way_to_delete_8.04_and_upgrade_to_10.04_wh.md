---
title: "Easiest way to delete 8.04 and upgrade to 10.04 while keeping xp"
date: 2010-07-04
forum: New to Ubuntu
---

### Post by Jonas thomas on 2010-07-04
Hello,
I have a machine in which I want to blow away 8.04 and install 10.04 without removing XP.
The live CD offers 3 choices
1) Install side by side.
2) Blow away everything
3) Manual configuration.

I don't want to update 8.04 to 10.04 (I hacked it up pretty bad and I just want a fresh start)
The Manual configuration sort of intimidates me, and I worried that I'm going to screw it up. 

What is the safest/easiest way of doing this?  Should I install side by side and then, use the live CD Gpart to delete the 8.04 partition and resize it?

---

### Post by Sonsum on 2010-07-04
I think you'll have to install them side-by-side. Install 10.04 on the 8.04 partition.

Make sure to back up anything you can't afford to lose.

---

### Post by mike555 on 2010-07-04
If you want to just format 8.04 , then find out which partition it is on and install to that partition .......

---

### Post by -humanaut- on 2010-07-04
When your using the live media to install just go to manual partition and over write the existing 8.04 partition(s).

---

### Post by WRDN on 2010-07-04
You first need to find which partition Ubuntu is on - type into the Terminal (Applications -> Accessories -> Terminal):

```
sudo fdisk -l
```

*Note: Thats a lowercase "L"*

Now, you can just install 10.04, formatting and installing onto this partition.

In case you don't have your /home folder on a seperate partition, and you want to keep it, you can read about the required process here: [http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/](http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/)

---

### Post by Jonas thomas on 2010-07-04
> **WRDN said:**
> You first need to find which partition Ubuntu is on - type into the Terminal (Applications -> Accessories -> Terminal):

```
sudo fdisk -l
```

*Note: Thats a lowercase "L"*

Now, you can just install 10.04, formatting and installing onto this partition.

In case you don't have your /home folder on a seperate partition, and you want to keep it, you can read about the required process here: [http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/](http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/)

I'm barbecuing and messing with partitions at the moment. A recipe for disaster.

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe245e245

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        9729    57665317+   5  Extended
/dev/sda5            2551        9541    56155176   83  Linux
/dev/sda6            9542        9729     1510078+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

``` 

Need to get back to the burgers..... Back in a little while.

---

### Post by WRDN on 2010-07-04
From the result you quoted above:

/dev/sda1 = Windows partition (don't overwrite this!)

/dev/sda2 = Extended partition containing:
/dev/sda5 = Ubuntu and /home are contained here
/dev/sda6 = Swap partition (similar to Windows page file)

In short, you want to overwrite /dev/sda5 with Ubuntu 10.04.

Oh, and enjoy the burgers :)

---

### Post by Jonas thomas on 2010-07-04
> **WRDN said:**
> From the result you quoted above:

/dev/sda1 = Windows partition (don't overwrite this!)

/dev/sda2 = Extended partition containing:
/dev/sda5 = Ubuntu and /home are contained here
/dev/sda6 = Swap partition (similar to Windows page file)

In short, you want to overwrite /dev/sda5 with Ubuntu 10.04.

Oh, and enjoy the burgers :)

There were brats also  ;)...
So clicking on the Install Ubuntu 10.04 on the Live CD desktop.
Step 1) Keyboard 
Step 2) Timezone
Step 3) Keyboard
Step 4) Selected:Specify Partitions Manually (Here is where things start getting murky for me)
I clicked on the row for /dev/sda5?
What's the next step.... Do I just highlight the row and click forward or do I need to do something else?

---

### Post by WRDN on 2010-07-04
Yep. Select "Specify Partitions Manually", select the /dev/sda5 row and click "Edit Partition". Set the mount point to "/", and click OK. Click the "Format" checkbox for /dev/sda5. After that, you're all set. The current swap partition will be reused and automatically selected by the installer.

---

### Post by Jonas thomas on 2010-07-04
If I highlight the row and click forward I get the message:
"No root file system is defined. Please correct this from the partitioning menu"

A very polite message..
So... I think I need to double click on /dev/sda5
Do I need to:
Click on the "Us as Pull down" select on x3 (since this is what I use the last time)
Enable the format the partition check box
Click Ok
and then click forward?? Is this the correct path?

---

### Post by WRDN on 2010-07-04
The message "No root file system is defined. Please correct this from the partitioning menu" appears because you haven't specified a partition with a mount point of "/" (as noted in post #9).

---

### Post by -kg- on 2010-07-04
OK, you want to completely get rid of 8.04 and fresh-install 10.04...

When in the partitioning section of the installer, highlight your sda5 and click edit partition.  You will be presented with a window where you can perform partitioning operations on the selected partition.

Since you want to wipe out 8.04, you want to format that partition, so select the drop down menu and select to format to ext4 (or ext3, if you prefer).  Then below that is where you select the mount point of the partition.  You need to select "/" (root) from that list.

Then, when you click forward, you won't get the message and the installation will proceed as normal.  Just be careful and don't select your Windows partition, and there will be no danger to it.

---

### Post by Jonas thomas on 2010-07-04
> **WRDN said:**
> The message "No root file system is defined. Please correct this from the partitioning menu" appears because you haven't specified a partition with a mount point of "/" (as noted in post #9).

Oh c#$p.. Didn't do the "/" part. (probably shouldn't have sucked down those beers over the barbeque) Now I've done it....I'm not sure what happened here.  I tried backing up to fix things up and at I have a message box "Please wait. Resizing Partition" It seems to be stuck at 50% for about 5 minutes.  I'm thinking I should restart the live session and start over....
(Am I'm going to regret that?)

---

### Post by WRDN on 2010-07-04
I would wait a while. Partitioning can take a while. If it has crashed though, then you should be safe restarting.

---

### Post by -kg- on 2010-07-04
> **WRDN said:**
> I would wait a while. Partitioning can take a while. If it has crashed though, then you should be safe restarting.

Definitely ***_do not_*** stop a partitioning operation in the middle of it!  You'll have a huge job ahead of you if you do.

> ...I'm not sure what happened here. I tried backing up to fix things up and at I have a message box "Please wait. Resizing Partition"

What it sounds like you did was back up and choose "Install side by side."  It is now shrinking one or the other of the partitions present on your hard drive.  If it's shrinking your 8.04 partition, you *might* (and I say *_might!_*) be OK, but if it's resizing your Windows partition...

Best to let it finish (if it's not absolutely stuck) and go from there.  Read the pages at the link in my signature block for additional information on Partitioning operations.

> (probably shouldn't have sucked down those beers over the barbeque)

You're probably right! :P  It's always best to have a clear head before performing any operation that involves messing about with installations, and *especially* partitions!  I hope everything comes out OK, and if the installation succeeds, read my post above.  If you have any further questions, I'd be more than happy to assist you...step by step, if necessary.

I basically wrote the pages at the link in my signature block, and have installed Ubuntu on quite a few computers now, under quite a number of different scenarios.

---

### Post by Jonas thomas on 2010-07-05
Turned the computer off and back on and reinstalled.  Everything seemed have gone ok.  I switched some monitors around and things got weird.  Re-installed again and it seems like we're back in business.
I spend weeks trying to get pulse audio to work in 8.04.  I got so frustrated I blew it away and installed esound.  Except with the weirdness that occured when I switched monitors, 10.04 is an order of magnitude better than 8.04..

Thank you everyone for the help..

---

### Post by -kg- on 2010-07-05
I'm glad it went well for you and yes, I agree that 10.04 is orders of magnitude better than 8.04.  I started with 8.04, and while it was good, I had no end of little problems with it.  With the exception of Intrepid, each subsequent release was better and better.

I haven't had Lucid installed for very long yet, but so far it seems to be a step up once again.  Good luck, and have fun!

---

