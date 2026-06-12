---
title: "Hard drive or something else"
date: 2010-03-20
forum: New to Ubuntu
---

### Post by Rex Bouwense on 2010-03-20
I have Hardy on a Compact Desktop and when I went to boot it today I never got to the log in screen.  All I got was two inches of vertical lines on the top of the screen and about four red and orange horizontal lines underneath that.  Since I just downloaded a new kernal yesterday, I decided to use an older one but no go on that Idea.  I tried to boot from a live cd but I get the same display.  The monitor is good because I hooked it up to another computer.  Is my hard drive shot?

---

### Post by mechro on 2010-03-20
It could be the graphics card or on-board graphics.

If you happen to have a separate graphics card plus on-board graphics on the motherboard you could try unplugging the separate card and try booting a LiveCD.

---

### Post by Rex Bouwense on 2010-03-20
A friend of mine gave me this computer a couple of years ago and I immediately put Hardy on it so I don't know what's under the hood.  I'll check and see if I have a separate card and try your suggestion.  This caught me by surprise as I haven't had a single problem in the two years or so that I have been using it.

---

### Post by Rex Bouwense on 2010-03-20
I got the old Compaq Deskpro to boot from a live CD (Karmic Koala) so the video card isn't shot.  Right now I am running a disk test so that should tell me something.  I'm in limbo until it finishes.  Thanks anyway.

---

### Post by Rex Bouwense on 2010-03-20
The disk check passed but I still cannot boot from the hard drive.  Is there something I can check from the terminal if I can get to it?

---

### Post by mechro on 2010-03-20
When you get to the corrupted screen can you start a console (black screen, white text, command line entry)? Enter ctrl + alt + F1 to start a console. Enter ctrl + alt + F7 to get back to desktop or, in your case, corrupted screen.

If you can open a console, enter your username and password if requested and try...

```
sudo /etc/init.d/gdm restart
```

I don't know if that will work as your problem could be one of a number of things.

---

### Post by pme 72 on 2010-03-20
There could be a conflict with your video card drivers and Hardy. I ran into issues with my Compaq desktop, an ATI integrated Radeon Xpress 200 video chip set and Hardy. No problem with Karmic. To boot into Hardy I had to log into Safe Mode and install the restricted driver from the System/Administration/Hardware Drivers menu.

I ran into a black screen at log in on Jaunty and the fix was to get to a terminal prompt and disable the restricted driver. 

Are you able to get to a terminal prompt? The command lshw -c display will reveal your video card and driver.

That information could prove helpful.

---

### Post by Rex Bouwense on 2010-03-21
I have not been able to get to a prompt yet.  What grips me is that I have been using Hardy on that computer without a problem for roughly two years.  What is booting into the safe mode?

---

### Post by mechro on 2010-03-21
> **Rex Bouwense said:**
> What is booting into the safe mode?

Safe mode usually means a Safe Mode Gnome session available from the login screen which of course you can't do.

There should be a recovery option available from the Grub boot Menu which will take you to a command line console.

---

### Post by Rex Bouwense on 2010-03-22
> **pme 72 said:**
> There could be a conflict with your video card drivers and Hardy. I ran into issues with my Compaq desktop, an ATI integrated Radeon Xpress 200 video chip set and Hardy. No problem with Karmic. To boot into Hardy I had to log into Safe Mode and install the restricted driver from the System/Administration/Hardware Drivers menu.

I ran into a black screen at log in on Jaunty and the fix was to get to a terminal prompt and disable the restricted driver. 

Are you able to get to a terminal prompt? The command lshw -c display will reveal your video card and driver.

That information could prove helpful.

This was more of a problem than I thought.  I finally got the old Compaq to boot from a Live CD in low graphics mode and got the video card info.  Description: VGA compatible controller
Product: 86c968 (Vision 968 VRAM) rev 0
vendor: S3 Inc.
physical id: 9
bus info: pci@0000:02:09.0
version:  : 00
width: 32 bits
clock: 33 MHz
capabilities: vga_controller
configuration: latency

I'm not sure that helps me because I don't know what to do with that information.  At least I can get to a terminal now so if I knew what to do and it could be done from the terminal I could do it.  One other problem.  For some reason I cannot connect to the WiFi in the RV park we are staying at so I cannot use the repair the broken package option in the recovery boot option.  Is there anything that I can do off line or do I just wait the 39 days for Lucid to arrive.

---

### Post by pme 72 on 2010-03-22
Was there an "xfix" option in the Recovery Mode Menu? I saw this in the Ubuntu 8.04 Release Notes:

A new X windows recovery feature is available. If you are unable to boot after attempting changes, you can reboot, choose the restore option in the boot menu, and then select the 'xfix Try to fix X server' option on the Recovery Menu. This should restore your X windows configuration to a usable condition and allow you to boot normally.

---

### Post by Rex Bouwense on 2010-03-22
> **pme 72 said:**
> Was there an "xfix" option in the Recovery Mode Menu? I saw this in the Ubuntu 8.04 Release Notes:

A new X windows recovery feature is available. If you are unable to boot after attempting changes, you can reboot, choose the restore option in the boot menu, and then select the 'xfix Try to fix X server' option on the Recovery Menu. This should restore your X windows configuration to a usable condition and allow you to boot normally.
I do not remember if it was there but I will check.  If it is there I will give it a try.  I cannot believe I am having this much trouble with a system that I have been using for about two years.  Hey, it happens.  Thank you.

---

### Post by Rex Bouwense on 2010-03-23
There is indeed an xfix option which I used and got the following reply:
xserver-xorg postinst warning:  overwriting possibly customized configuration file; backup in /etc/X11/xorg.conf .20100323095329   I believe I got that right because it doesn't stay on the screen very long.  I guess that means that the file that has the video in it has been overwritten.  Is it telling me that the backup is located in that file?  Now what?

---

### Post by pme 72 on 2010-03-23
Rex, I am out of suggestions. I did find this post:

[http://joeb454.ubuntuforums.org/showthread.php?p=6721384](http://joeb454.ubuntuforums.org/showthread.php?p=6721384)

It looks like the command he mentions brings up a list of xorg configuration files on the system. He recommends copying the last xorg configuration that was in use before having run xfix using the command he lists. If that does not help he recommends copying the one previous to that. 

Wish I could be more help.

---

### Post by Rex Bouwense on 2010-03-23
Thank you for your efforts.  Perhaps I am just too dense.  I tried what was written but I still have no picture.  I am now able to get to a command line from a normal boot.  However, I don't think that the two are even remotely related.  It is looking like I am going to have to re install Hardy or wait for Lucid.

---

### Post by pme 72 on 2010-03-23
You did better than I did with my (multiple) Hardy installation(s). I just tried a google search "Hardy black screen after kernel update" and got a lot of hits if you are still interested in pursuing a solution.

---

### Post by Rex Bouwense on 2010-03-23
I am going to continue to try to fix this thing until 29 April when I will get lucid anyway.  I don't have anything else to do.  After youy said that you did a Google search for black screen after kernal update, I figured that I could do the same so now I have a bunch of leads.  I don't know why I didn't do that first.  Thank you again for your time and ideas.

---

### Post by Rex Bouwense on 2010-03-23
> **pme 72 said:**
> You did better than I did with my (multiple) Hardy installation(s). I just tried a google search "Hardy black screen after kernel update" and got a lot of hits if you are still interested in pursuing a solution.
Can I just uninstall and reinstall the xserver or will that not even come close to achieving the desired results?

---

### Post by pme 72 on 2010-03-24
I do not know. It does not sound like something I tried though. You could try moving this or reposting to the MultiMedia/video area of the forum. The focus of attention there is more towards problems like the one you are having. Absolute Beginners Talk covers an enormously wide area of topics. The solution could be something simple that a seasoned video veteran might know and you might increase your odds of finding such a soul there.

---

### Post by pme 72 on 2010-03-25
By any chance did you have Desktop Effects enabled before you started having a problem?

---

### Post by Rex Bouwense on 2010-03-25
It is odd that you just posted.  I have just turned on the old Compaq and booted with a live cd in low graphics mode.  No I never did use any desktop effects on that computer.

---

### Post by Rex Bouwense on 2010-03-25
I just finished downloading Hardy Herron 8.04.4 and the md5sum was good.  I think that I may have to make a new bootable cd to reinstall.  I hate to do that but that will get rid of the stuff in the video file that is preventing me from booting properly.  I will have to find the driver for this old wifi card if it isn't recognized by 8.04.4.  The original Hardy didn't recognize it and I had to go through a few hoops to get it installed, but that is another problem and another thread if it should come to that.

---

### Post by Rex Bouwense on 2010-03-28
> **mechro said:**
> It could be the graphics card or on-board graphics.

If you happen to have a separate graphics card plus on-board graphics on the motherboard you could try unplugging the separate card and try booting a LiveCD.

I reread all of the posts made here and decided to unplug the separate graphics card which I did not do the first time.  Lo and behold Mechro you are a genius.  I booted from the live cd and everything was OK.  I rebooted, after taking the live cd out of the tray and everything was still OK.  Every program that I have tried worked just fine.  I have Wireless Internet and I can get to my email.  So, this thread will be marked as solved thanks to you.  I will use the internal video until I get a new separate video card.  Thank you again Mechro.

---

