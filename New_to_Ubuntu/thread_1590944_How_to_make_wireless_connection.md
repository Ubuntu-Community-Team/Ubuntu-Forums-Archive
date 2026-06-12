---
title: "How to make wireless connection"
date: 2010-10-08
forum: New to Ubuntu
---

### Post by Shellbak3 on 2010-10-08
I recently installed Ubuntu 10.04 LTS 64 bit on an HP (Compaq?) that was not being used at work.  The old OS (XP) is gone.  The only problem I've found so far is that while the Wireless indicator is lit, I don't know how to make a connection.  It's a BCM 4312 and lsmod shows it used by "0".

I'm at home today and have LAN access via a wire but at work I will only have wireless as this machine may not be connected to the work LAN less the IT police come for me - wouldn't work anyway.  So I need to get this working.  

At some point I'm going to attach a research grade camera to the notebook by LAN and will need to set a fixed IP adddress and mask.

I'd be ecstatic - or at least happy - if someone could point me in the right direction.

TIA

Nate

---

### Post by gordintoronto on 2010-10-08
While you have a wired connection, run System/Administration/Hardware Drivers. It should offer to "activate" the driver. 

Here's a useful Youtube video:
[http://www.youtube.com/watch?v=M-CTMCwXDzo](http://www.youtube.com/watch?v=M-CTMCwXDzo)

---

### Post by anewguy on 2010-10-08
You'll find a lot of threads on getting Broadcom wireless working, but let's give a brief outline of what's available and what to try first.

There are several ways to get this working - using native drivers, using Windows XP drivers or using the firmware cutter method.

The easiest and preferred way is to use native drivers.  To install these, you will need to temporarily hard-wire your PC to the router so you have an internet connection.  Then do the following:

- open a terminal window (Applications/Accessories/Terminal)

- type:

sudo apt-get update <press enter>

- wait for the above to finish

- open System/Administration/Hardware Drivers

- hopefully there will be a driver listed there now for your wireless.  Enable that driver.

- disconnect the hard-wire cable to your router

- reboot

That's the easiest and most preferred way.  If you can't get access to hard-wire to your router, perhaps you can at a neighbor or friend.

The next method would ndiswrapper.  This is simple to use so ignore any "bad press" you may read in the forum about it (some people are just adverse to it).  If you want to use this method, first get the Windows XP (they might have to be 64-bit drivers since you're using 64-bit Ubuntu - I really don't know) files for your adapter - the .inf and .sys files.  Then post back here and I can give you step-by-step instructions for getting this going.

For the firmware method I would need to defer to someone else who has actually used it.  I know a user name lkraemer on the forums who knows how to do this.

Dave ;)

---

### Post by Shellbak3 on 2010-10-08
Thanks gordintoronto and anewguy.  After I posted I found some info I had missed before and downloaded ndiswrapper.

But going to System->Administration->Hardware, following the instructions, and rebooting did the trick.

I'm connected.

---

### Post by anewguy on 2010-10-11
Just in case you need the info in the future, and for anyone else who may be following this thread:

- you don't need to download ndiswrapper.  Nor do you need to download the source for it and try to compile it.  Those are old postings.  If you have the LiveCD you installed from, all of the ndiswrapper things, including the GUI front end you SHOULD use (makes life MUCH easier) are all on the LiveCD:

With Ubuntu booted, put the LiveCD in the drive - just cancel if a message comes up about a disk with software packages being found.

Using "Places", navigate to the /pool/main/n folder on the LiveCD.  You will see 2 folders:

- 1 for ndisgtk
- 1 for ndiswrapper

Go to the ndiswrapper one first and install in the following order:  ndiswrapper common first, then ndiswrapper utilities.  Just double-click on the files there to begin installation.

Then go back to the ndisgtk folder and double-click on the file there to install ndisgtk.

To run:

- go to System/Administration/Windows Drivers to start ndisgtk

- select "new" or "add" (don't have that screen in front of me)

- point it to the .inf file for your Windows XP driver

For the vast majority of installations, this is all that is needed.  In very rare cases, modules may need to manually added or the blacklist.conf file may need to be edited.  So far, for the BCM43xx series, all anyone has had to do is point it to the .inf file - ndisgtk takes care of the rest.

Always remember that ndiswrapper (and therefore its' GUI'd front-end ndisgtk) can only work with Windows XP drivers.

Dave ;)

---

