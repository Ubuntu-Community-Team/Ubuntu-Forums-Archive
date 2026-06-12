---
title: "Trouble installing Belkin F5D7010 rev 5 PCMCIA wireless card"
date: 2008-08-31
forum: Networking &amp; Wireless
---

### Post by IrishPirate on 2008-08-31
First off I would like to say I am a total beginner to Linux.  I installed Heron on an older Dell 1.8ghz laptop with 256 RAM.  I have read until both are eyes are now bleeding LOL.  I found a post giving a really good how to about installing NDISWrapper-util-1.9, ndisgtk abd ndiswrapper-common.  Installed the driver from the original install CD and it said hardware was present.  Went to the network settings and set the passcode and DHCP and it showed it was connected with the activity light flickering but no connectivity with firefox.  Here's the strange part, I fiddled with the WPA or WPA2 setting (it kept bouncing between the 2 everytime I checked) and I had it working for about 5 minutes...then I restarted the system and it all went bye bye.  Now the problem is, after removing the driver and trying to start over the connect light on the card will stay lit and then go out, come back on for a few and then go out.  After a while it goes out and stays out.  Sorry for the long winded post but I wanted to be as detailed as possible.  Any suggestions are appreciated.  TIA!!

---

### Post by IrishPirate on 2008-09-02
Bump!  Anyone, anyone, Bueller, Bueller?

---

### Post by IrishPirate on 2008-09-08
Bump.  Hmm, no help at all!

---

### Post by swiftarrow on 2008-09-13
I did the same as you... right down to the old dell laptop - just for comparison, mines an Inspiron 1100 from 2003, now slaving away with Ubuntu Hardy Heron (8.04).  I have a Belkin PCMCIA wireless card, model F5D7010 version 7000.  This should work for your v5 also.  It seems that not many people are using this card, hence the lack of info.

Leaving aside the story, what finally worked for me was    :-({|=

First take your card out.

1) Complete update of the system (via ethernet cable):
     Go to the Control Center (keep it open, you'll need it later too).
     Choose "Update Manager"
     Click "Check"
     Click "Install Updates"
     Once everything's done, close the update manager.

2) COMPLETE removal of existing ndiswrapper
I had followed a lengthy tutorial written by some poor tired guy, and while it worked for him, it didnt for me, and ndiswrapper was misbehaving
     In the Control Center, choose "Synaptic package manager". Enter your password.
     Once it's loaded, click on the first package listed, and type "ndis"  It will scroll so that ndis is shown.
     There are three ndis packages (ndisgtk, ndiswrapper-common, and ndiswrapper-utils-x.x)
     Click on the green square next to ndiswrapper-common and choose "Mark for Complete Removal"
     Click Mark on the window that comes up
     Click Apply changes in synaptic
     Click Apply in the Summary window that pops up.  It will work for a minute, then be ready.

3) NEW download and install of ndiswrapper
     Now again scroll down to the NDIS packages
     Click on the grey square next to ndisgtk and choose "Mark for Installation".
     Click Mark in the window that pops up.
     Apply in Symantic, and again in the summary window that pops up.
     Close Synaptic once everything's done.
     Close the Control Center too.

4) Get the drivers:
     Go to [http://www.belkin.com/support/article/?lid=en&pid=F5D7010&aid=6003&scid=0](http://www.belkin.com/support/article/?lid=en&pid=F5D7010&aid=6003&scid=0)
     Choose your version and download the windows executable
     Open the executable USING ARCHIVE MANAGER (I actually used WinRAR in windows for this part, but I hope that the archive manager can handle it.)
     Browse through the .exe, and find your drivers for WinXP. (something like blkwgnv5) 
     Extract the .inf file somewhere where you'll find it.

5) Install the driver:
     Open the Control Center.
     You should now see a "Windows Wireless Drivers" option.  Open it.
     Choose "Install New Driver"
     In the window that pops up, click where it says "none" location bar, and find the driver.
     Choose Open
     Choose Install
     Now it should have an entry for your card under Currently installed windows drivers.  Great!
     Close Windows Wireless Drivers.
     Close the Control Center

6) Insert the card
and wait for it to turn on.
Mine acted differently than in windows. it turned on (amber light blinking) and then the green light turned on too!  I was surprised, as I hadn't given it the key to the network yet...

7) Switch to wireless
left click on the network manager applet up near the clock (two computers next to each other)
select the wireless network
all should be quite well...8)

8 ) Post back here with your results!

Although it seems like a long list, it's just because it's broken down into baby steps that I wish I had read any one of those countless nights of searching!

---

