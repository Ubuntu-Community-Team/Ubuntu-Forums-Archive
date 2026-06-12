---
title: "could not stat the resume device file or hybernate to death"
date: 2010-10-17
forum: New to Ubuntu
---

### Post by hekastos on 2010-10-17
Hi 
I have a small problem after closing the lid of my laptop while ubuntu 10.10 was still running (I thought thats possible) it does not boot anymore, but it says

resume:  could not stat the resume device file '/dev/dm-0'

on every boot... (no matter normal or recovery)
What can I do?

Oh and btw. if I get this fixed and I really hope so, how do I make a 100% image of my harddisk on a usb drive which I only have to clone back when I freak out my system again?

Thx kindly for any help!
cya

---

### Post by Hippytaff on 2010-10-17
Think this is either a bug or something to do with your swap partition..not sure...could be none of the above (I'm still a bit new too)...can you post the output of

```

df

```

to do this, open a terminal - CTR+ALT+T
type the command, highlight copy and past here :-)

---

### Post by hekastos on 2010-10-17
unfortunately I'm not able to do as you suggest, my comp a asus k50in boots,then he stops, when I now press alt f7 it says:

resume: libcrypt version: 1.4.5
resume:  could not stat the resume device file '/dev/dm-0'
Please type in the full path name to try again or press enter to boot the system

If I try enter nothing
if I alt switch to another consol black screen
only working keys contr alt delete ... reboot...
I could boot it with a live system from cd ... or put the hdd into another comp ...

---

### Post by amjjawad on 2010-10-17
What's the size of your SWAP partition?

As for backup, you just need to backup your important data files. As for Ubuntu itself, the whole installation process is less than 15mins so it's pointless to backup Ubuntu itself if you ask me.

Your Live CD/USB is kind of your rescue media in case something will go wrong. Also, if you have an external HDD, that would be much better to keep your important files there.

---

### Post by Hippytaff on 2010-10-17
> **hekastos said:**
> unfortunately I'm not able to do as you suggest, my comp a asus k50in boots,then he stops, when I now press alt f7 it says:

resume: libcrypt version: 1.4.5
resume:  could not stat the resume device file '/dev/dm-0'
Please type in the full path name to try again or press enter to boot the system

If I try enter nothing
if I alt switch to another consol black screen
only working keys contr alt delete ... reboot...
I could boot it with a live system from cd ... or put the hdd into another comp ...

sounds like it might bee a bug...log the bug here
[https://launchpad.net/ubuntu/+bugs](https://launchpad.net/ubuntu/+bugs)

---

### Post by hekastos on 2010-10-17
Thx a lot for your replys!
@Hippytaff
Before I file a bug report I will try to tackle this. I booted from a live cd and started looking, most people in google describe the error related to a failure in initramfs,  my laptop was set to hibernate when the lid is closed since this was the first time (and last ;) ) obviously hibernate does not work, so the question is what does initramfs do and is it related to hibernate and can that be fixed somehow if it goes wrong. I will research. Which log would you consult for this?
The /var/log/pm-suspend.log says performing hibernate success no errors

@amjjawad
My swap partition is 8 GB (double Ram I'm told) and
Forgive me a bit of rambling after a hard day with a not working ubuntu, because
I needed 15 min to install ubuntu
5 min for skype
5 min to make my cd burner appear in the burning app
15 min to get the proprietary graphics and audio drivers installed and working in which by the way the new ubuntu does a awesome job assisting you
1h to install virtual box with a OS to be able to use the occasional Photoshop, because I wasn't able in another
1h to install Photoshop with wine
2h to turn the picture of the webcam which is mounted upside down in skype
not to speak about linking a disconnected wpa2 support to my wlan driver (I still don't understand it completely, it was a copy paste orgy) and 
3h research and rebooting for the question why and how a boot parameter has to be given to the kernel so a restart would work.
That is, again you may forgive the slightly talkative part, but it could have been longer, mainly the reason, why I don't want to just backup my 3 openoffice documents after reenabling me to restart the thing ;)

---

### Post by JustinR on 2010-10-17
> **hekastos said:**
> Thx a lot for your replys!
@Hippytaff
Before I file a bug report I will try to tackle this. I booted from a live cd and started looking, most people in google describe the error related to a failure in initramfs,  my laptop was set to hibernate when the lid is closed since this was the first time (and last ;) ) obviously hibernate does not work, so the question is what does initramfs do and is it related to hibernate and can that be fixed somehow if it goes wrong. I will research. Which log would you consult for this?
The /var/log/pm-suspend.log says performing hibernate success no errors

@amjjawad
My swap partition is 8 GB (double Ram I'm told) and
Forgive me a bit of rambling after a hard day with a not working ubuntu, because
I needed 15 min to install ubuntu
5 min for skype
5 min to make my cd burner appear in the burning app
15 min to get the proprietary graphics and audio drivers installed and working in which by the way the new ubuntu does a awesome job assisting you
1h to install virtual box with a OS to be able to use the occasional Photoshop, because I wasn't able in another
1h to install Photoshop with wine
2h to turn the picture of the webcam which is mounted upside down in skype
not to speak about linking a disconnected wpa2 support to my wlan driver (I still don't understand it completely, it was a copy paste orgy) and 
3h research and rebooting for the question why and how a boot parameter has to be given to the kernel so a restart would work.
That is, again you may forgive the slightly talkative part, but it could have been longer, mainly the reason, why I don't want to just backup my 3 openoffice documents after reenabling me to restart the thing ;)

Hi,

With an Ubuntu LiveCD/USB go to Applications > Administration > Disk Utility, find your HDD - click the Swap Partition and reformat it as Swap.

---

### Post by hekastos on 2010-10-17
I tried diskutility and it writes /dev/sda3 swap -I formated-, also I tried mkswap /dev/sda3, which worked too. But next boot same error ;(
It happens after/during running /scripts/local-premount if that says anything!?

---

### Post by hekastos on 2010-10-17
is that normal? why is sda3 commented out could that be the mistake?

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=6c8f1d77-1ff6-40ab-a27f-2acc44c27428 /               ext4    errors=remount-ro 0       1
# /data was on /dev/sda2 during installation
UUID=55e046de-57ab-43d1-a9b3-ab3d1595f14c /data           ext3    defaults        0       2
#/dev/sda3       none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
```

---

### Post by Hippytaff on 2010-10-18
Looks like something went wrong with partitioning. Back everything up and try reinstalling ubuntu?

---

### Post by hekastos on 2010-10-18
Thanks if that is the only solution I will do it, but I'm a bit sad, so much work for a flawless system and now everything again, just because of one try with hibernate, is everyone in the future able to kill my laptop by closing the lid? Somehow that should be fixable? Is there no log or anything I could consult?

---

### Post by amjjawad on 2010-10-18
> **hekastos said:**
> Thanks if that is the only solution I will do it, but I'm a bit sad, so much work for a flawless system and now everything again, just because of one try with hibernate, is everyone in the future able to kill my laptop by closing the lid? Somehow that should be fixable? Is there no log or anything I could consult?

Before doing anything, I suggest to use [Google]("http://www.google.com"). Try to search there.

I've read some where (can't remember where) that Ubuntu has some problems with Hibernate. I do have one but it's not that much important but annoying though.

---

### Post by hekastos on 2010-10-18
I tried google, many people there describe it as a initramfs problem, how would I reinstall initramfs on my laptop while booting from a live cd? (Unfortunately the exact doings of initramfs are still a bit misty to me even after reading all wikipedia in that subject), but before I reinstall I will try anything...

---

### Post by Hippytaff on 2010-10-18
Ubuntu uses swap when hibernating, so maybe this is the problem, but as amjjawad said, have a google before you reinstall - also if you decide to reinstall I would advise you select manual partition and follow a tutorial (loads about), have a seperate /home partition.
 
the general advice is Swap space should be twice as big as the amount of ram you have (unless you've got a massive amount of ram)

---

### Post by Hippytaff on 2010-10-18
> **hekastos said:**
> I tried google, many people there describe it as a initramfs problem, how would I reinstall initramfs on my laptop while booting from a live cd? (Unfortunately the exact doings of initramfs are still a bit misty to me even after reading all wikipedia in that subject), but before I reinstall I will try anything...
 
You usually get dumped in initramfs when the installtion is duff - sorry, I've had it too, really frustrating though you can probably fix it, but I don't know how...so I just reinstalled :-)

---

### Post by hekastos on 2010-10-18
The problem is not my data, because thats backuped on my usb drive, the problem is I finally had a system running smoothly, with all drivers, with all necessary software, updates etc. And one hibernate later everything is gone, and I fear if someone closes my laptop lid it will happen again. In any case I need a hdd clone program, so I can clone the whole thing after and before every script, patch, config change I run...
Still I would prefer learning to understand the issue and fix it, it really should be possible, don't you think? Where would you start a in detail research?

---

### Post by Hippytaff on 2010-10-18
Maybe look into creating a swap partition with gparted and see if this works!?

---

### Post by theozzlives on 2010-10-18
> **hekastos said:**
> The problem is not my data, because thats backuped on my usb drive, the problem is I finally had a system running smoothly, with all drivers, with all necessary software, updates etc. And one hibernate later everything is gone, and I fear if someone closes my laptop lid it will happen again. In any case I need a hdd clone program, so I can clone the whole thing after and before every script, patch, config change I run...
Still I would prefer learning to understand the issue and fix it, it really should be possible, don't you think? Where would you start a in detail research?

My laptop is set to suspend when the lid is closed and it works fine. I haven't tried 10.10's hibernate as of yet so I can't comment on that.

I just hibernated my tower and it worked without a hitch, must be your swap partition. I'd say boot live and delete it with gparted and make a new one.

---

### Post by hekastos on 2010-10-18
I reallz think I|m going crazy, I tried gparted from the live cd and it says:
```

sudo gparted
======================
libparted : 2.3
======================

glibmm-ERROR **: 
unhandled exception (type std::exception) in signal handler:
what: basic_string::_S_create

```
Its obviously this bug:
[https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/617885](https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/617885)
but I don|t really understand the fix.
apt-cache policy gparted
gives me
```

  Installed: 0.6.2-1ubuntu1
  Candidate: 0.6.2-1ubuntu1
  Version table:
 *** 0.6.2-1ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ maverick/main i386 Packages
        100 /var/lib/dpkg/status

```

@theozzlives I will not touch suspend or hibernate ever again, if I get this back to boot. :)

---

### Post by Hippytaff on 2010-10-18
Are you sure the live cd is not corrupt?, check the md5sum of the iso you downloaded and burn at the slowest speed
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by theozzlives on 2010-10-18
Alternatively, you can get the gparted live CD and do it that way. I really think if you trash your swap and make a new one it should boot.

K, the risky test. I just hibernated my laptop without a hitch so it has to have something with either your install, or your swap. If you didn't do a md5sum, you could very well have a corrupt install.

---

### Post by amjjawad on 2010-10-18
Don't have much to say because the guys said it all.
I'm very interested to know what will happen next.

---

### Post by tajiknomi on 2010-10-18
[SIZE=2]*Stuck with Lucid....10.04*[/SIZE]

---

### Post by hekastos on 2010-10-18
So I downloaded a image checked the checksum, started, tried gparted, error as above.
Is it possible that ubuntu uses any swap space even from a live cd that exists and gparted can not manipulate active swap space or something like that?
I downloaded the gparted live image with it I was able to delete and reinstall the swap space, what didn't help, and to resize it, but that didn't help either.
I'm really finished with my wisdom ;(

---

### Post by hekastos on 2010-10-18
OMFG, people you are the best! I write this finally from the dead system, the gparted live cd seem to have done its job, the error still exists but now I was able to press enter and the system boots, now I only have to find out how to kill the error so I don't have to press enter on every boot. But now the system is back so ask about whatever output you are interested in to locate the problem...
And many thx again, that was a majorly important step for my system and my frustration tolerance ;)

---

### Post by hekastos on 2010-10-18
that did it !!!

```

swapoff /dev/dm-0                  # deactivate it for now.
mkswap -c -L swap-here /dev/dm-0   # make a new one with a label.
swapon LABEL=swap-here        # reactivate it by name just to be sure
swapon -s                    # you can't be too paranoid, check it again.
grep device /etc/uswsusp.conf   
perl -pi -e 's,/dev/dm-0,LABEL=swap-here,' /etc/uswsusp.conf
grep device /etc/uswsusp.conf                 # check if the edit worked
update-initramfs -u
```

But I'm still not finished, because I have now a new bug: gparted doesn't work in my system. If someone wants to follow up [here]("http://ubuntuforums.org/showthread.php?p=9991991")
But at least this problem seems solved, thx a lot again people for your support!

---

### Post by heatpumpcontrol on 2010-10-18
I Tried the GParted Live Disc to no avail.

My situation was that after the upgrade, the pc would not boot because the reference to my Swap partition was incorrect. For some reason my partition's UUIDs were changed along with the associated change.. /dev/sdf instead of /dev/sdb.

I noticed that Grub displayed two Kernels, the new one and the old one. I noticed that if I selected the previous Linux Kernel 2.6.32-25, I would get it to boot. 

I messed around some more and decided to delete both installed Kernels, 2.6.35-22 and the old 2.6.32.25.(Big Mistake!) I then could only reinstall 2.6.35-22 because the other was not avail for Maverick. 

After a reboot, it wouldn't start at all. However, what I did was, selected recovery mode (I have also lost my grub Time out counter), and upon getting to the point of the 'Could not stat the resume...' message, I tapped the ENTER buttons on the keyboard continuously and WOW!, it went passed the error and the pc continued to boot. 

After the prompts and questions, I logged into my account and installed Kernel Linux 2.6.35-22-server. Rebooted and for whatever reason, it will boot using the server Kernel but not the generic Kernel. 

Hope this helps some else out. Just be sure to keep hitting the ENTER key while in the recovery mode in order to get past the error. Now I'm just dealing with the Grub Timeout error. No countdown. StartUp-Manager does not help.

Good luck

Edit:

The fix I discovered for the Grub Timeout issue. [Here]("http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9993635#post9993635")

---

### Post by trichome tetrahydron on 2012-08-31
I would like to start by saying I have had this problem on two different computers, my old toshiba satellite L300 and recently on my thinkpad T530.

Last time, this was the thread that helped me solve the issue. Both times I have experienced the same error - not booting, and receiving the error message about /dev/dm-0, being told to press enter but upon pressing it nothing happens.

So far I have followed the same steps I did last time:

1. using the lubuntu live cd I opened gparted, and found a partition with a warning exclamation mark on it. I deleted it and reformatted it to have linux-swap as the filesystem.

2. I rebooted and chose the ubuntu safe-mode option in GRUB, then pressing enter continuously and very fast, as heatpump recommended. This was able to get me past the error message and got to the splash-login screen with lubuntu working properly after choosing "resume" option (normal boot) from among some others.

3. I ran $sudo apt-get purge hibernate. This package is definitely what caused the problem. I installed it, hibernated to test, and then couldn't boot. Seems like lubuntu 12.04 just doesn't get along with hibernate...

3. I am now entering the commands hekastos gave...

Okay, right off the bat I'm a little confused since I feel like last time the commands worked... but already $sudo swapoff /dev/dm-0 gives "swapoff: /dev/dm-0: swapoff failed: No such file or directory"...

I opened /proc/swaps and found no entries, perhaps because I deleted my old swap which got corrupted. I'm going through the process of making ubuntu know about the swap partition i created. I open gparted (not in live-cd, we are still in recovery-booted-lubuntu) and get the path of the swap space (/dev/sda7 for me) and have made a line for it in my /etc/fstab file:

/dev/sda7 none swap sw 0 0 

Then I just ran $sudo swapon --all --verbose and it finds and registers /dev/sda7 fine, but for /dev/mapper/cryptswap1 it says "stat failed: No such file or directory", so I just comment out the line for /dev/mapper/cryptswap1 in my /etc/fstab...

Now when I re-open /proc/swaps I can see /dev/sda7 accounted for.

I will now reboot and see if these steps (purge "hibernate" and re-setting-up my swap partition) have done any good...

Okay I just tried to boot from the normal GRUB entry and got a black screen. I'm going to try again... Damn! The same error... could not stat the resume device file /dev/dm-0...

So I am now booting back into recovery mode GRUB option. Using the "spam ENTER" trick I am past the error message. This time I choose the "fsck" option which presents itself and promises to check all file systems. It tells me "/dev/sda5: Superblock last mount time is in the future (by less than a day, probably due to the hardware clock being incorrectly set) FIXED." (sda5 is the lubuntu partition on my computer) I press enter and choose "resume" mode (normal boot). I get to my splash-login screen safely.

Now that I'm booted in again, I try to follow the commands hekastos posted, again. I still receive the same errors about /dev/dm-0 not existing, but when I grep /etc/uswsusp.conf for "device" I see the line "resume device = /dev/dm-0". Interesting... I skip ahead and try the command update-initramfs -u, which warns "cryptosetup: WARNING: failed to detect canonical device of /dev/dm-0"

Not sure what good this has done, I reboot again...

AND IT WORKED!!! :D:D:D

Well, I hope that my tale has been inspiring to whoever encounters this frustrating and stupid error in the future. There are apparently problems with trying to hibernate when you have encrypted swap, but I'm pretty sure than in the process of fixing this all I replaced my encrypted swap setup with a plain swap at /dev/sda7 (on my computer it's sda7 anyway)... not sure if i want to try to hibernate again because this was a lot of steps... but apparently there's a thread where you can learn how to use encrypted swap with hibernate:

[http://ubuntuforums.org/archive/index.php/t-1986821.html](http://ubuntuforums.org/archive/index.php/t-1986821.html)

PEACE everybody

---

