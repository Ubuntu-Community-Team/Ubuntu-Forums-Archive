---
title: "Weird issue"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by ts13209 on 2009-10-28
I am fairly new to Ubuntu having my Dell Mini 9 netbook since this past Spring. In that time I haven't really done much but surfing the Internet,and  playing some Ubuntu games . In that time period I think I have been notified twice that there were updates to download and install, for which I did. Last night i signed off my computer and shut it down completely like I always do. Today when I signed on, I noticed changes had taken place overnight. First thing I noticed was the desktop picture and beginning music was gone, then the bar which has the games, web option and other options did not appear. At this time a message appeared which said,
**"the configuration defaults for the gnome power manager has not been installed correctly"please contact computer admin.**

At the same time,I noticed my regular graphics and colors had also been changed. I did a little research on Google and was able to fix (I think ) the gnome power manager issue, yet the graphics are still messed up. More research indicates a problem with the driver for video might be the issue. I followed the instructions, but it appears the only driver I ca find is the device driver for the Broadcast A Wireless Driver. Does this even sound close to what might be causing my issues?
From what I can gather by reading other people's similar issues is that there must have been an update last night that I didn't see. Many people seem to report similar issues after installing an update. What can I do to restore my desktp picture, the bar with the icons for the web, games , and productivity, etc, and get the graphics to return to the style they were last night before I signed off? I appreciate any help anybody can offer me. Being fairly new to Ubuntu I find a lot of the info overwhelming so I will try my best to understand what people are trying to say in an attempt to help me solve these issues. Thank you.

---

### Post by lavinog on 2009-10-28
Did this version of ubuntu come with your dell?

can you start synaptic, reload, then mark all updates and click apply.

---

### Post by ts13209 on 2009-10-29
> **lavinog said:**
> Did this version of ubuntu come with your dell?

can you start synaptic, reload, then mark all updates and click apply.
Yes, this version came pre-installed on the Dell. I tried doing what you recommended but after I mark all updates, the apply tab is not highlighted so I cannot click on it.
Here is some info at the bottom of the screen , I don't know if it may help. This is what it says before I click the mark all updates tab: 24,084 packages listed, 1202 installed, 0 broken, 0 to install/upgrade,0 to remove. Once I click the mark all updates tab it says "successfully  marked all available upgrades". In the center of the page in the big blank box it says,"No package is selected." and the apply button is not highlighted. Am I doing anything wrong here?

---

### Post by lavinog on 2009-10-29
I recall seeing other users have problems with the limited space on the dell mini 9 netbooks.

how much free space do you have?
You should be able to check with system monitor, or if you can get a terminal window use the **df** command.

---

### Post by ts13209 on 2009-10-29
I went to the system monitor and this is what I found on the System Tab:
Release 8.04(hardy)
kernel linux 2.6.24-24-lpia
GNOME 2.22.3 Hardware
Memory 493.3 MiB
System Status
Available Disk space 420.7 MiB

On the File Systems Tab:
Device: 
/dev/sda2 total 3.4 GiB Free 599.6 GiB Available 420.2 MiB Used 2.8 GiB  87%
gvfs-fuse-daemon has the same values as the /dev/sda2.

The netbook came with a 4GB hard drive.

---

### Post by lavinog on 2009-10-29
It is likely that you ran out of drive space during an update.  There have been similar issues with others using the 4g model.

Try and cleanup as much space as possible by removing unneeded programs, clearing your cache in firefox, empty your recycle bin, open your ~/.thumbnails folder in nautilus and delete all of the thumbnails (sometimes this can get to be over 500M if you look at alot of images.)

I would also get a low profile flash drive and use that for secondary storage.

After you free up some space, you might be able to go into synaptic and look at the history to see what were the more recent packages installed, and re-install them.

---

