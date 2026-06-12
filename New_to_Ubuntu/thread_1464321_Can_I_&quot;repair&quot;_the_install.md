---
title: "Can I &quot;repair&quot; the install ?"
date: 2010-04-28
forum: New to Ubuntu
---

### Post by davexnet on 2010-04-28
I accidentally uninstalled some items when I was playing around in
Synaptic.  The first symptom was that some items were missing
from the System/Administration menu.  I have got some of them back,
but there are a few odd behavioral things too.

Is there a command I can issue that will cause Ubuntu to check
and if necessarily reinstall anything missing that would have been installed
on a clean install ?

I've been looking at apt-get - there are so many options, I can't seem to
find what I'm looking for, so I thought I'd better ask here.

Thanks for any info.

---

### Post by wilee-nilee on 2010-04-28
Look in history in synaptic it will tell you what you deleted. Sudo apt-get update in the terminal is the standard command for updates sudo apt-get upgrade is the standard command for the upgrade run the update first it may pick up some of what you have removed.

also if you don't know this already, when you enter your password in the terminal it doesn't show, just hit enter.

---

### Post by ankspo71 on 2010-04-28
In addition to going over the history in Synaptic Package Manager and reinstalling what got removed, you could also try reinstalling the package 'ubuntu-desktop'. You can mark it for reinstallation by right clicking on it, then click on the apply button.

Or you can try apt-get in the terminal:
```
sudo apt-get install --reinstall ubuntu-desktop
```

---

### Post by ibuclaw on 2010-04-28
> **ankspo71 said:**
> Or you can try apt-get in the terminal:
```
sudo apt-get install --reinstall ubuntu-desktop
```

If it's just a case that several items you have blindly removed require installing again, you shouldn't need the --reinstall argument in the above command.

---

### Post by davexnet on 2010-04-28
Well, I didn't think I was blindly uninstalling, I thought I was cleaning
up old crap.  I uninstalled a few things from the the Synaptic
(local or obsolete) area.

After rebooting the system it wouldn't even get to the graphical Interface.
All this action occurred in Ubuntu 8.10.

I must admit, I made what seems like an unnecessary and rash decision in my attempt to fix it, 
I upgraded the distribution to 9.04 by issuing a
command right there at the terminal screen.  Here's the thing though,
I thought doing the upgrade to 9.04  would "put back" those items but
it apparently did not.

The system is upgraded to 9.04, but the items at first, were not fixed.
At first boot, it booted up to the terminal once again, but I was able
to access the GUI by issuing "startx".  From there I re-entered Synaptic
and reinstalled some of the items,  some what blindly again,
(I didn't know about the Synaptic History unitl today) but it seems I made
some good choices (from the residual config area) because after rebooting,
the GUI returned and the System/Admin list of applets as well as 
"applications" looked more complete.  (For example the Applications/
Add/Remove was missing completely, but it's back now).

So that's where I am.  It probably looks hilarious to you experienced
guys and gals -  but I really appreciate the help.  There are some
non-related subjects I help out on in other forums,  so I see it 
from both perspectives.

I'm going to examine the history, and try the apt-get for ubuntu-desktop,
and I'll update the post later.
Thanks again.

---

### Post by davexnet on 2010-04-28
Ubuntu-desktop was not installed at all, according to Synaptic.
I installed it and rebooted, now I get the music again as the desktop
appears, and another item has reappeared in System/Admin.

I found some other items in History than were removed by me at about the
time I originally screwed up.   They are
libboost-date-time
libboost-filesystem
libboost-thread

How can I find out what levels these should be at for Jaunyy?
For example, libboost-date-time is not installed now, and 
libboost-filesystem and libboost-thread are at version 1.34 while
version 1.35 is not installed.  

This is what I see in Synaptic:
[[IMG]http://img63.imageshack.us/img63/1654/screenshotsynapticpackar.png[/IMG]](http://img63.imageshack.us/i/screenshotsynapticpackar.png/)

[[IMG]http://img175.imageshack.us/img175/2333/screenshotsynapticpacka.png[/IMG]](http://img175.imageshack.us/i/screenshotsynapticpacka.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

Thanks for any further info.

---

### Post by nothingspecial on 2010-04-28
Removing some packages, for example evolution, removes ubuntu-desktop which is your entire gui.

It`s a common pitfall.

---

### Post by Silent Warrior on 2010-04-28
For the Boost-libraries, my install (Mint 8, based on 9.10/Karmic) indicates version 1.38. Oh, right, Jaunty! That's 9.04... :oops:

It's possible the relevant version will be pulled in as a dependency, though - while manually installing libraries isn't perhaps the most harmful activity, you very rarely gain anything from doing so. Install a bunch of other packages, and you'll probably get the right version of Boost.
KDE4 seems to use Boost (just install akregator - if you don't want all the fluff, just go through the list of packages to install (filters, yummie!) and deselect the KDE-stuff while keeping the Boost-libs), as well as wallpaper-tray, mkvtools-gui, smc, gnash. Installing any of these should give you some fresher Boost-libs.

In Mint, Synaptic has a filter for package origins. Look at the entry pointing to your Ubuntu-mirror (ubuntu.lhi.is/main etc. for me, being on Iceland and all) and make sure your Boost is installed from there. Consider disabling any external repositories, if you have any active and carrying libboosts of their own.

Is the rest alright, then? You have your working desktop?

---

### Post by admiralspark on 2010-04-28
Yep, and running the Update Manager (System->Administrative->Update Manager) should update any old versions of the libraries (anything beginning with lib- ).
Notice: upgrading to ubuntu 9.04 will add/remove programs and 'control panel' apps because it's a different version, just so you know. :-)

---

### Post by davexnet on 2010-04-28
Running the update manager has done it's thing and there are no further
updates at this point.
The system is essentially working.  The login takes a little longer than 
it did compared to my previously working 8.10 system,
I get the little drum roll, enter userid/password, press enter and the 
screen goes black for 6 or 7 seconds.  Then you hear the Ubuntu jingle,
followed by  another 5 seconds or so of black screen, then the desktop
appears fully formed.

During restart, a box comes asking me to restart immediately or
allow the 60 second countdown.  If I continue, there is a beep from the
PC speaker.  Not sure what that is -An error perhaps?  never heard it
before.

This is a list (from the Synaptic history) of the other things that were
inadvertently uninstalled from 8.10.  I'm going to check each one to
see what the status is.  I might even install MKVtools to see what it
does.
apturl
fast-user-switch
gdeb1
gdm
gdm-guest-session
gnome-app-install
gnome-netstatus-applet
hwtest-gtk
network-manager-gnome
software-properties-gtk
ubufox
ubuntu-desktop
update-manager
update-notifier
usb-creator

---

### Post by nothingspecial on 2010-04-28
> **davexnet said:**
> Running the update manager has done it's thing and there are no further
updates at this point.
The system is essentially working.  The login takes a little longer than 
it did compared to my previously working 8.10 system,
I get the little drum roll, enter userid/password, press enter and the 
screen goes black for 6 or 7 seconds.  Then you hear the Ubuntu jingle,
followed by  another 5 seconds or so of black screen, then the desktop
appears fully formed.



I think you fixed it. :)

Do you have any problems?

---

