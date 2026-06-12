---
title: "A few problems... Im frustrated and feel like a huge noob"
date: 2010-12-31
forum: New to Ubuntu
---

### Post by jinba.ittai on 2010-12-31
I like using linux because of the speed difference I experience when switching from windows. But every time i install ubuntu, there seems to be something wrong with the install that I dont have the knowledge to fix. Im still pretty knew to linux and the command line...


Today I face a couple of problems.

1. I cant install anything from the software center apt-get *Pic related* (error in pic below)


2. I cant play my audio/mp3 files due to some kind of error, ill try to explain this better when i can get the error to show up again. for now it just wont play the music 


3.Im used to booting straight into the login screen, but with this new 10.10 (which didnt have a gui installer, had some crazy looking dos-like selections which i had no idea how to use) boots up and shows a purple screen with no login gui, but a text version. This stays put on the screen for about 10 minutes asking for login and pass before the gui finally loads. 

I was considering switching to gentoo, but then i heard it takes some 8+ hours to install, and im not having that. 

I might just redownload and re-install 10.10 to see if that helps at all.

---

### Post by endotherm on 2010-12-31
well, for 1, I would try ```
sudo apt-get update
``` and see if it completes correctly. if it does, try software-center again. the error is saying it can't find a file that it just downloaded, so you will have to try to download it again. 

for 2, send us the error messages and we'll see what we can do. do you have you installed the mediubuntu repositories and the ubuntu-restricted-extras packages? they have many good codecs that aid audio and video playback. 

as for item 3, it sounds like you have the alternate installer cd. Try downloading the standard install (32 or 64 bit if you have more than 3GB RAM) if you choose to reinstall. it may be exactly what you need, as something definitely does not sound right with your boot sequence. you may want to boot with [MemTest86+]("https://help.ubuntu.com/community/MemoryTest") and make sure your RAM is in good working order. also check System -> Administration -> Disk Utility to make sure your smart data shows the drive as healthy. since you just installed, the file system should be clean, but if you mount a drive used by a previous install as your home, you may want to run fsck on it. otherwise, check the dmesg log and note the entries around any wide periods of time between messages. let us know what you find.

there is a boot info script that can help trackdown boot up problems: [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

and also bootchart, a great tool for visualizing the amount of time each boot process takes to complete: [http://ubuntuforums.org/showthread.php?t=531453](http://ubuntuforums.org/showthread.php?t=531453)
see #3 for install and use instructions. just install it, and reboot. when done your chart will be in /var/log/bootchart/

---

### Post by jinba.ittai on 2010-12-31
Just gona back up everything and reinstall. I have more hard drives if this one isnt doing so well.

the update didnt change anything. 

Will post results after reinstall

---

### Post by jinba.ittai on 2010-12-31
Tried installing 10.04 but after the first purple screen, the disk refused to load a proper display. 

Im assuming that the 10.04 disk doesnt have a proper driver for Nvidia gt 220. Unfortunately my onboard vga port died a little while ago. 

Im in the process of downloading the 10.10 64 bit iso, does this disk have a driver to support the gt220?

---

### Post by endotherm on 2010-12-31
I've had an issue in past, when just after installing the os, the output stops going to the non-integrated video card, if the internal one was not disabled in the bios first. after you have a working desktop you will be able to install an nvidia driver for your card, but you have to get there first.
check your bios for an option to disable the integrated video, and see if that helps.

---

### Post by jinba.ittai on 2010-12-31
Well i dont have the fastest internet, so i have to wait about 30 minutes for 10.10 to finish downloading, then ill try to install by disk and check that option in teh bios as well. 

But im pretty sure i already turned that option to only enable the pci gpu instead of onboard. 


If i cant get it to work, ill have to reformat the hdd, and install through windows (and fix the windows mbr)


alot of work for tonight , but ill get it done however. 

If worse comes to worse, ill put this box in the closet and use my intel dual core. But wont be using my gt 220 =[

---

### Post by ikt on 2010-12-31
How unlucky with your ubuntu woes :(

For the 1st one I can see it's having an issue with the ms core fonts, try heading into terminal and doing:

sudo apt-get install msttcorefonts

and then rebooting, but it really seems like:

[https://bugs.launchpad.net/ubuntu/+source/aptdaemon/+bug/549867](https://bugs.launchpad.net/ubuntu/+source/aptdaemon/+bug/549867)

This was fixed 6 months ago, so the updates should have fixed it.

---

### Post by jinba.ittai on 2010-12-31
Re-installed 10.10! Everything working smoothly now! 

While i was up all night dealing with 3 computers, i decided to build a box out of the spare parts i had.


3Tb worth of hdds, Think ill make a server now! 

Thanks for the help! Cya later!

---

