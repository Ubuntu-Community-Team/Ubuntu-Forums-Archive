---
title: "A Lot of Bad Things Have Suddenly Happened"
date: 2010-11-14
forum: New to Ubuntu
---

### Post by SillySod on 2010-11-14
When I switched my computer on today, I found that a lot of things had changed from last night!

I am on Ubuntu 9.04 using Xcfe session.

Firstly, the Applications menu had renamed itself to "Xcfe Menu", the "Places" tag on the Places menu had disappeared and also the Firefox icon next to the Places menu had gone.

I didn't think much of it at the time and carried on, but then I found that Phatch wouldn't work any more.  It loaded, and I could load an action list, but dropping some images into it and asking it to execute didn't do anything.

I closed down Phatch and tried to re-load it, but it won't load any more, a Phatch bar appears along the bottom for a moment but then this disappears and it won't load any more.

I tried to re-start my computer, but then I had a problem where I couldn't log in, I just kept getting the log in window re-appearing every time I put in my password.

Eventually I managed to log in to an Xfce session after quite a bit of trouble, can't remember just what I did but I tried logging into Gnome and KDE sessions which worked, and I also used CTRL-ALT-F7 at one point, so now I am back to having my normal log in session, but still things aren't right.

For some reason, the background picture changed back to the picture I was using about 6 months ago, all my Thunar windows changed to showing icons instead of detailed listings, and the log out button doesn't bring up a Shutdown/Restart/Log off set of options any more, it just takes me straight back to the log in screen without any warning.

Phatch still won't work, and I re-installed it but that didn't help.  I also installed the latest version, but that said that all my action lists weren't compatible, so that's no use as I have about 15 different action lists which I use regularly which I've refined over the last couple of years, and I don't have the time to start again from scratch.

I've been able to put some things right by manually setting options but I'm still not back to how I was when I shut down my computer last night, so can anyone help me with these things I don't seem to be able to do:

1.  Restore the Firefox icon to the task bar next to the Places menu
2.  Get Shutdown/Restart/ etc. menu back when I press the log off icon
3.  Get Phatch working, or at least have the ability to import my action lists into the new version

Also any ideas on why all this started to happen would be handy!

---

### Post by SillySod on 2010-11-14
I've got Phatch back, I had to install the old version on the other PC and then copy a file called settings.cPickle from the .phatch directory in the main user directory onto the same location on my computer, and that brought it back to life!

So, point number 3 is resolved, but any help with 1 & 2 would be very much appreciated!

---

### Post by Hippytaff on 2010-11-14
you should be able to right click on the panel and click 'add to panel' to get your firefox icon back

---

### Post by tgalati4 on 2010-11-14
In a terminal:

dmesg | more

(spacebar to move forward, Control-C to quit)

Look for errors, could be a failing disk that trashed your user settings.

Whenever you lose stuff in linux, that's the first thing to check.

---

### Post by SillySod on 2010-11-17
Right, looks like I'm back to normal now!  I got the Firefox icon back next to "Places" by creating a Launcher and filling in all the details.  I managed to fix the logout problem as well by ticking a box in the "Session and Startup" menu called "Prompt on logout".

I still don't know why any of this happened though!  Trying dmesg wasn't very instruction, I don't understand what the output was telling me!

I haven't noticed any disc problems, there's been no loss of data, so I remain bamboozled!

Is there a way to save all my profile settings, colour scheme, etc. so I can put it on a memory stick in case it vanishes again?

---

### Post by Hippytaff on 2010-11-17
You can use a package called remastersys or use the startup disc creator in System menu :-)
 
Edit -> Just relised your using Xubuntu, not sure what the Xsfe version of startup disc creator is called or if there is one, but remastersys will create an ISO of the current setup which you can either burn to cd/dvd or pit on usb, either as a live environment or as just a copy of the iso.

---

### Post by kaldor on 2010-11-17
You can also copy + paste your entire home folder (including the hidden files)to an external drive.

---

### Post by ironic.demise on 2010-11-17
> **kaldor said:**
> You can also copy + paste your entire home folder (including the hidden files)to an external drive.
Most people have their /home on a separate drive for this purpose.

---

### Post by sky_ceiling on 2010-11-17
perhaps a bad update caused this?

---

### Post by tgalati4 on 2010-11-20
I haven't used XFCE in a while, but if it crashes, it can limp along with the behavior that you described.  Sometimes a control-alt-backspace will reset it--sometimes only a cold boot will reset XFCE to its original  condition.  You can simply backup the .xfce directory, that is where all the icons and menus are stored.  You can also try to restart XFCE from the commandline.  I think the command is xfce4-start.

---

### Post by SillySod on 2010-12-12
Thanks for the suggestions, I did try copying my home folder to another drive but eventually I got an error saying something couldn't be read, an access denied type of error, so I think I might need to do something from terminal to do the copy instead of a click and drag operation.

I've also discovered that there are some disc errors on the Ubuntu partition of the drive where Ubuntu is installed, which might have caused the strange problems in the first place.

I have reorganised my PC by putting an external drive inside my PC on the second IDE bus instead of a CD-ROM drive, so I've got plenty of disc space for playing about at the moment.

What I am trying to do now is to make the drive containing the Ubuntu partition entirely into a Linux drive.  Originally, this volume was an NTFS drive, being a second drive I'd added a year or two after I got my PC.  When I installed Ubuntu about 2 years ago, I shrank the NTFS partition from taking up the full drive capacity of 120GB to 50GB, then I put a Linux-swap partition of 10GB next to it, and used the remaining 50GB as the ext3 partition for Ubuntu.

I've deleted the NTFS partition from this drive and moved the Linux-swap partition to the beginning of the drive, so this should leave just over 100GB for my ext3 partition and I want to expand the current ext3 partition to use up all the remaining space.

However, I can't!  I've tried this several times with Gparted, and it takes about 2 hours to do a disc check, which doesn't report any errors, and then it starts to copy all the sectors from their current location to the new location towards the beginning of the disc.  It copies about 18GB and then says there is an input-output error and aborts.

I ran e2fsck last night with the -c option and it told me it had marked 16 bad blocks, so I tried the Gparted process again but it still aborted at the same sector as previously.

I can't think of any way round this apart from to format the partition.  If I'm going to do that, I might as well format the whole drive just to be on the safe side.

So, I suppose the question is, can I copy all my system partition to the new drive I've just added, then format the drive and copy it back, or do I need to be aware of boot sectors and things so that my PC can still find Ubuntu when it's moved from one end of the disc to another?

---

### Post by Jose Catre-Vandis on 2010-12-12
This sort of thing can happen if you have a full hard disk / partition

---

