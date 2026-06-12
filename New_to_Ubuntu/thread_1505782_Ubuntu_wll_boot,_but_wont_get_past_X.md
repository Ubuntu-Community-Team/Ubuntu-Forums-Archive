---
title: "Ubuntu wll boot, but wont get past X"
date: 2010-06-09
forum: New to Ubuntu
---

### Post by Mr. R on 2010-06-09
When I boot Ubuntu normally, it will boot but it won't display the usual boot up screen, it will just say "Starting Up..." and go directly to X (the desktop) about a few seconds later. Once it has started, there are no panels, just a mouse, and my custom solid black color for my desktop wallpaper. If it matters, it doesn't even show the purple solid colored wallpaper, which appears after the Ubuntu boot up screen. I cannot right click and open a menu (I think there was a problem about this in 10.04.) In that case, I am left with a nonfunctional desktop on tty7.

One important thing, I have not backed up any documents on Ubuntu yet. I really don't even know how to do it "properly." I want to keep away from unsafe disk operations unless absolutely necessary.

So how can I fix this?

---

### Post by arrange on 2010-06-09
Have you been doing anything of relevance recently or has it happened all of a sudden? It's a fresh install? Are you able to boot into *Recovery mode* from Grub? Have you checked the HDD/filesystem (*fsck*)?

---

### Post by Mr. R on 2010-06-09
> **arrange said:**
> Have you been doing anything of relevance recently or has it happened all of a sudden? It's a fresh install? Are you able to boot into *Recovery mode* from Grub? Have you checked the HDD/filesystem (*fsck*)?
I have not been doing anything out of the ordinary. I upgraded Ubuntu from 8.04 to 10.04, so not a fresh install. I can boot into recovery mode, but I cannot type anything in, and I don't have a PS/2 keyboard to test. And I can't run fsck without a terminal, but maybe if I close the desktop and log in to another tty then maybe I can run fsck.

I can fresh install 10.04 as long as I can access the files. I will attempt to boot up with the Live CD and see if it recognizes the HDD and then transfer to a flash drive or another backup HDD.

---

### Post by arrange on 2010-06-09
Or you could make an extra partition for */home* (if you don't have one), copy the old home there and just reinstall the system.

Still I would check the HDD and filesystem from a LiveCD.

---

### Post by Mr. R on 2010-06-09
Well, although I was planning to reformat with ext4 anyways, a reformat with a new Live CD couldn't hurt, but I can still get in the terminal on tty1-6. I unmounted and ran fsck on the drive from the Live CD, it said it's clean. I also backed up and finally made the purchase of my 16GB flash drive useful.

Is there a way to stop the desktop server and restart it (with any debug options)?

---

### Post by arrange on 2010-06-10
Not sure if this is what you mean but ```
sudo initctl restart gdm
```

*gdm* logs messages to */var/log/syslog* for instance.

BTW did you *force* fsck? Sometimes it says *clean* because the journal is OK, but to be safe I think you should *fsck -f* the filesystem.

---

### Post by Mr. R on 2010-06-10
> **arrange said:**
> Not sure if this is what you mean but ```
sudo initctl restart gdm
```*gdm* logs messages to */var/log/syslog* for instance.

BTW did you *force* fsck? Sometimes it says *clean* because the journal is OK, but to be safe I think you should *fsck -f* the filesystem.

Alright, here's that output:
> ubuntu@ubuntu:~$ sudo fsck -f /dev/sda1
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda1: 373809/9674752 files (1.6% non-contiguous), 22489217/38696560 blocks
The** sudo initctl restart gdm** command works, but it doesn't solve the problem.

BTW, if I see slow progress, I'm going to be impatient and reinstall Ubuntu with either the xfs or ext4 file system, and hopefully it'll work. I think this happened after an update, maybe I should pay more attention to my updates--it's like they're dangerous or something...

---

### Post by lavinog on 2010-06-10
> **Mr. R said:**
> When I boot Ubuntu normally, it will boot but it won't display the usual boot up screen, it will just say "Starting Up..." and go directly to X (the desktop) about a few seconds later. Once it has started, there are no panels, just a mouse, and my custom solid black color for my desktop wallpaper. If it matters, it doesn't even show the purple solid colored wallpaper, which appears after the Ubuntu boot up screen. I cannot right click and open a menu (I think there was a problem about this in 10.04.) In that case, I am left with a nonfunctional desktop on tty7.

One important thing, I have not backed up any documents on Ubuntu yet. I really don't even know how to do it "properly." I want to keep away from unsafe disk operations unless absolutely necessary.

So how can I fix this?
can you use ALT-F2 or CTRL-ALT-T
If you can with either one, can you start nautilus?

Or if you can get to tty1, try creating a new user then login with the new user and see if the desktop works...it could be that you have a config file in your profile that is not compatible with the newer gdm.
Use the command **adduser** to create a new user.

---

### Post by Mr. R on 2010-06-10
> **lavinog said:**
> can you use ALT-F2 or CTRL-ALT-T
If you can with either one, can you start nautilus?

Or if you can get to tty1, try creating a new user then login with the new user and see if the desktop works...it could be that you have a config file in your profile that is not compatible with the newer gdm.
Use the command **adduser** to create a new user.
I created **adduser new**, and so I cannot use the **sudo** command now. It says I'm not in the sudo-ERS Someone can obviously tell now I'm not experienced at all.
BRB, Google.
EDIT: OK, I think
> sudo adduser new adminmight do it.

And what do I do after this????
EDIT2: Nautilus won't work under the command-line, and I can't use CTRL+Alt+T or Alt+F2. Restarting the gdm under the new account did nothing as well.

---

### Post by lavinog on 2010-06-10
> **Mr. R said:**
>  Restarting the gdm under the new account did nothing as well.

Did you try rebooting and logging in as the new user?
"restarting the gdm under the new account" sounds like you tried to start gdm with the new user credentials which is not the same as login.

---

### Post by Mr. R on 2010-06-10
Oh, wait, this is interesting. I was just about to shutdown with **sudo shutdown 0** and then It said that this landscape (i think it was called) daemon said [fail], next this recovery mode window came up. It has the option to fix packages with dpkg, update the GRUB bootloader, start with failsafe mode and clean the drive to create more free space. So I updated GRUB, fixed any broken packages, cleaned, and am now in failsafe mode. I'm pretty sure that there were no other important options there except options to go to root shell. Also, I have no idea how I got to the recovery mode.

Anyways, I'm currently in failsafe mode wondering what to do. I haven't read about diagnosing with failsafe mode yet. I just don't want to skip over the problem. I'm thinking that I might troubleshoot and diagnose something that was never the problem.

---

### Post by Mr. R on 2010-06-10
Sorry for the bump, right now I am bored and found two duplicate files in etc/modprobe.d/ with each duplicate having the ".conf" file extension and one missing it. I am trying to figure out if I should delete one of them. For example: alsa-base and alsa-base.conf are not identical, so there's some strange conflict here.

Back to the problem:
The only troubleshooting feature in failsafe boot after selecting it in recovery mode is the ability to view a couple of log files and edit one config file. I couldn't see anything strange or noticeable in the log files.

---

### Post by Mr. R on 2010-06-11
Alright, so I'm still trying to understand what the cause of the problem is or the procedures I should do to fix possible problems.
Fisrt, I think this is a software issue. I need to know if this issue comes from GRUB, X, GDM, or others. And is it the software or the config that might do this.

Again, in detail, the only keyboard shortcuts I can do are CTRL+Alt+F1, I cannot right click, there are no menus, there is no usual splash screen when I boot up. I can move the mouse and see that desktop runs but it won't show any panels. I have tried to fix any broken packages, repair GRUB, clean HDD, launch old kernel with an unusable command line (In GRUB, I have two kernel options with two recovery modes for each making four boot configurations, that's what I'm talking about). Finally, memtest86 doesn't work, it throws error 28.

---

### Post by lavinog on 2010-06-11
> **Mr. R said:**
>  Finally, memtest86 doesn't work, it throws error 28.

Is it saying: Error 28: Selected Item cannot fit into memory

What version of grub do you have?

Can you give some information about your system? Are you running a raid array?

---

### Post by Mr. R on 2010-06-14
> Is it saying: Error 28: Selected Item cannot fit into memoryYes.

> What version of grub do you have?> hp@hp:~$ grub --version
grub (GNU GRUB 0.97)> 
 Can you give some information about your system? Are you running a raid  array?     HP Pavilion a6157c. I have it running on 1 SATA drive. I think it either is configured as RAID 0 in the bios or its identity is "RAID-0".

---

### Post by Bodsda on 2010-06-14
Hi,

The memtest issue is a bug with Grub - [http://savannah.gnu.org/bugs/?3404](http://savannah.gnu.org/bugs/?3404)

To test your RAM, you will need to create a bootable memtest disc for now. But, back to the original issue, can you confirm that you logged into gdm after a standard boot as the new user? Not in tty1 or launching gdm 'as' the user, but on the normal login screen on tty7. 

Also, it is no real surprise that nautilus fails on tty1. Once you are logged in as the new user on tty7, open nautilus by pressing ALT+F2 and typing 'nautilus'. To get your panels, try running 'killall gnome-panel' 

Let us know how you get on.

Cheers,
Bodsda

---

### Post by Mr. R on 2010-06-14
> **Bodsda said:**
> Hi,

The memtest issue is a bug with Grub - [http://savannah.gnu.org/bugs/?3404](http://savannah.gnu.org/bugs/?3404)

To test your RAM, you will need to create a bootable memtest disc for now. But, back to the original issue, can you confirm that you logged into gdm after a standard boot as the new user? Not in tty1 or launching gdm 'as' the user, but on the normal login screen on tty7. 

Also, it is no real surprise that nautilus fails on tty1. Once you are logged in as the new user on tty7, open nautilus by pressing ALT+F2 and typing 'nautilus'. To get your panels, try running 'killall gnome-panel' 

Let us know how you get on.

Cheers,
Bodsda
Oh, so that's a motherboard issue? I dunno if it's ASUS Nforce, but it is ASUS. I luckilly have a memtest86 bootable CD all ready to go.

Yeah, let me (re)state very clearly, no other keyboard shortcuts, not even those, will work except CTRL+Alt+F# keys.
So there's no way I can do that to get in nautilus. I can pretty much tell that the desktop is running. I know that the daemons are running; I hear the start up sound, and that probably means GDM is running. I can also restart GDM with the **sudo initctl restart gdm** command in tty#.

---

### Post by Mr. R on 2010-06-14
Memtest86 completed 1 full pass with 0 errors.

---

### Post by shardvexspangler on 2010-06-14
Try booting Ubuntu failsafe (From the grub menu.), or try typing startx from the command line.

---

### Post by Mr. R on 2010-06-15
> **shardvexspangler said:**
> Try booting Ubuntu failsafe (From the grub menu.), or try typing startx from the command line.

Both of those will not work. startx will not run because it's already running, and running the failsafeX option in recovery mode, which runs failsafe for one session, has not worked.
Sorry, it is timely to post the exact error messages here, I have to transfer them to my flash drive :\

---

### Post by 0nelove on 2010-06-15
> **Mr. R said:**
> Both of those will not work. startx will not run because it's already running, and running the failsafeX option in recovery mode, which runs failsafe for one session, has not worked.
Sorry, it is timely to post the exact error messages here, I have to transfer them to my flash drive :\

**ok, I'm having the EXACT same problem as you.**  I have a recent install of 10.04 LTS and the last thing I did that, assumedly, broke the X install was remove evolution-related packages through synaptic.  Guessing I stupidly removed something that was important.  Other guess is latest round of updates (apt-get upgrade) may have borked something.

_Summary_:
Can get to graphical login splash screen but upon giving correct login & pw, screen blinks black, then returns to splash screen.

Can select grub recovery mode and dpkg fix packages did nothing to help.  Selecting "low graphics mode" from recovery menu gave exact same behavior as above, but with one screen active instead of 2.

EDIT: running startx from the login prompt, for me, just gives the black screen described by OP.  So, X just won't load (I guess)...

EDIT2: going to try this: [http://www.ubuntugeek.com/ubuntu-tiphow-to-removeinstall-and-reconfigure-xorg-without-reinstalling-ubuntu.html](http://www.ubuntugeek.com/ubuntu-tiphow-to-removeinstall-and-reconfigure-xorg-without-reinstalling-ubuntu.html)

EDIT3: that seemed to break things a bit more.  'Fatal server error: no screens found' ... booting from live CD to check what's left inside /etc/X11/xorg.conf

EDIT 4: not looking good.  Have purged and reinstalled xserver-xorg-core and xserver-xorg a few times with no result.  have done a lot of googling, but the solution I see most often resorted to is "reinstall the whole ball o wax" - ugh.  For clarity, the error on startx (for me) is:
```
(EE) Failed to load module "nouveau" (module does not exist, 0)
(EE) Failed to load module "nv" (module does not exist, 0)
(EE) Failed to load module "vesa" (module does not exist, 0)
(EE) Failed to load module "fbdev" (module does not exist, 0)
(EE) No drivers available.

Fatal server error:
no screens found
...
xinit: No such file or directory (errno 2): unable to connect to X server
xinit: No such process (errno 3): Server error.
```

sorry to hijack - but it seems like we are having the same error (or we were before I broke mine a bit more)...

EDIT 5:   :(

---

### Post by Mr. R on 2010-06-16
Alright, actually I can get in to tty1 and tty7 only through failsafeX. I am about to describe the error messages and visuals from failsafeX in detail because my camcorder sucks and the photo quality I take with my camera function also sucks.

After failsafeX bootup in low graphics mode, there is a desktop icon button, which pops open a menu, but I cannot select anything from it--it's useless.

I notice the bottom, properly-colored desktop panel with a desktop button and workspace switcher on the right side shows up (the workspace switcher is corrupted or something because the width of each of those three rectangles is longer than I have configured).

Finally, on whatever tty I have failsafeX start up on with gdm, there is a 1 pixel jittering horizontal line on the bottom of the screen.

Next I go into tty1, which outputs a message on every newline, filling the entire column of the screen with this:
> (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
I do not think the error keeps looping because the text would flash very quickly (about as quickly as the refresh frequency I have my monitor set on.)

OK, **now I go over in tty7**, and I receive, firstly, these messages:
> udevd[330]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/50-xserver-xorg-input-wacom.rules:##

Where ## seems to increase at a non-linear rate.
Also these very similar messages appear afterwards:

> udevd[330]: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/85-brltty.rules:##

Again, ## resets somewhere around 1 when these messages appear afterwards and increases at a non-linear rate.

On the very end it says (snipped):
> /dev/sdb1: clean . . . .

On the final newline, it reads:
> * Starting AppArmor profiles

And finally, a blinking underscore appears on the bottom-right of my screen (on the final newline).

I'm sorry for such detailed descriptions. But what is going on with this OS?

---

### Post by 0nelove on 2010-06-16
dude, I googled high and low and never found any workable solution to this issue.  I wish you good luck - after EDIT 5, I just took 3 hours and reinstalled/reconfigured.

good reason to always keep /home on a separate drive/partition.

---

### Post by Mr. R on 2010-06-16
0nelove, good luck to your problem as well.

I am going to try to fix one of the errors in tty7 by using the instructions from this article: [http://linuxindetails.wordpress.com/2009/12/30/udevd-sysfs-will-be-removed-in-a-future-udev-version-please-use-attr-to-match-the-event-device/]("http://linuxindetails.wordpress.com/2009/12/30/udevd-sysfs-will-be-removed-in-a-future-udev-version-please-use-attr-to-match-the-event-device/")

---

### Post by 0nelove on 2010-06-16
thanks - all resolved now with the 3hr reinstall.  hope you don't go over 3 [more] hours pulling out hairs, but I'll watch here to see if you have some success.  Perhaps you'll discover a way to save others some time in the future.

---

### Post by Mr. R on 2010-06-16
I had the wrong plan to install both OSes on seperate HDDs anyways. Grub won't recognise the partition and Windows won't recognize the other SATA drive (without some drivers). The point is, I need to re-partition and reformat anyway. I'll mark as [SOLVED] if Ubuntu 10.04 works after installing from an updated LiveCD with ext4. It's already been almost a week and nobody has the capability, urge or "something" to truly help.

---

### Post by KingYaba on 2010-06-17
> **0nelove said:**
>  Other guess is latest round of updates (apt-get upgrade) may have borked something.

_Summary_:
Can get to graphical login splash screen but upon giving correct login & pw, screen blinks black, then returns to splash screen.

Can select grub recovery mode and dpkg fix packages did nothing to help.  Selecting "low graphics mode" from recovery menu gave exact same behavior as above, but with one screen active instead of 2.

EDIT: running startx from the login prompt, for me, just gives the black screen described by OP.  So, X just won't load (I guess)...

EDIT2: going to try this: [http://www.ubuntugeek.com/ubuntu-tiphow-to-removeinstall-and-reconfigure-xorg-without-reinstalling-ubuntu.html](http://www.ubuntugeek.com/ubuntu-tiphow-to-removeinstall-and-reconfigure-xorg-without-reinstalling-ubuntu.html)

EDIT3: that seemed to break things a bit more.  'Fatal server error: no screens found' ... booting from live CD to check what's left inside /etc/X11/xorg.conf

EDIT 4: not looking good.  Have purged and reinstalled xserver-xorg-core and xserver-xorg a few times with no result.  have done a lot of googling, but the solution I see most often resorted to is "reinstall the whole ball o wax" - ugh.

EDIT 5:   :(

I'm having this same problem. The only updates I have recently installed, and can recall, was some evolution packages. Now the X Windows System won't work. Which is frustrating because I have a little work I need to get done. So what updates were released for Ubuntu in the last few days?

startx in CLI doesn't work
purging and reinstalling xserver-xorg doesn't work

But you're lucky; my system doesn't return me to the splash screen.

---

### Post by 0nelove on 2010-06-17
> **KingYaba said:**
> I'm having this same problem. The only updates I have recently installed, and can recall, was some evolution packages. Now the X Windows System won't work. Which is frustrating because I have a little work I need to get done. So what updates were released for Ubuntu in the last few days?

startx in CLI doesn't work
purging and reinstalling xserver-xorg doesn't work

But you're lucky; my system doesn't return me to the splash screen.

did you try booting from an older kernel?  If that doesn't work, you might want to go ahead and reinstall.  I keep 5 small 30gb partitions on my disk for the purpose of rotating various installations. Just keep your /home on a different drive or partition.   wish I had more insight for you.  Like I said, I googled around and didn't see an answer in an hour+, so I just reinstalled.

---

### Post by KingYaba on 2010-06-17
> **0nelove said:**
> did you try booting from an older kernel?  If that doesn't work, you might want to go ahead and reinstall.  I keep 5 small 30gb partitions on my disk for the purpose of rotating various installations. Just keep your /home on a different drive or partition.   wish I had more insight for you.  Like I said, I googled around and didn't see an answer in an hour+, so I just reinstalled.

I appreciate your quick response but it seems I have fixed my issue! :guitar::lolflag:

Anyway, I did try what you suggested; that is, booting from my older kernel. That did not work. 

So to sum up what I've tried in case someone has the same issue,

I booted in recovery mode
CLI login
sudo dpkg-reconfigure xserver-xorg
ditto the commands but for xserver-xorg-core

Rebooted. That didn't work. 

I tried purging (sudo apt-get remove purge) xserver-xorg and xserver-xorg-core once again in the CLI. 

Then I reinstalled those two followed by reconfiguring. 

It appeared to have not worked, Though, that time I could hear the Ubuntu drums sound where the login screen should be. Still a blank screen, unfortunately.

So then I decided to reinstall my ATI driver. I figured what the hell, this should beat completely reinstalling Ubuntu. Doesn't hurt to try, right? So I booted in the low graphical environment. Removed my ATI driver. Rebooted and logged back in--BUT WAIT--the normal login actually worked! :confused: So I downloaded and installed the latest ATI driver (10.6) and vuala! Here I am with a system that's working (for now).

So, was this truly an x window issue or an ATI driver issue?

FYI I keep my /home on a separate hard drive. :) But yes I was pretty close to reinstalling.

---

### Post by 0nelove on 2010-06-17
> **KingYaba said:**
> I appreciate your quick response but it seems I have fixed my issue! :guitar::lolflag:

Anyway, I did try what you suggested; that is, booting from my older kernel. That did not work. 

So to sum up what I've tried in case someone has the same issue,

I booted in recovery mode
CLI login
sudo dpkg-reconfigure xserver-xorg
ditto the commands but for xserver-xorg-core

Rebooted. That didn't work. 

I tried purging (sudo apt-get remove purge) xserver-xorg and xserver-xorg-core once again in the CLI. 

Then I reinstalled those two followed by reconfiguring. 

It appeared to have not worked, Though, that time I could hear the Ubuntu drums sound where the login screen should be. Still a blank screen, unfortunately.

So then I decided to reinstall my ATI driver. I figured what the hell, this should beat completely reinstalling Ubuntu. Doesn't hurt to try, right? So I booted in the low graphical environment. Removed my ATI driver. Rebooted and logged back in--BUT WAIT--the normal login actually worked! :confused: So I downloaded and installed the latest ATI driver (10.6) and vuala! Here I am with a system that's working (for now).

So, was this truly an x window issue or an ATI driver issue?

FYI I keep my /home on a separate hard drive. :) But yes I was pretty close to reinstalling.

All hail KingYaba!!!  awesome work man!  That's some good thinking and it's awesome that you posted the steps here.  I'm sure it'll help somebody in the future.  I don't think I ever reconfigured the -core files and I didn't think to trash/reinstall drivers.  rock on bud!  Hope this helps MR. R!

---

