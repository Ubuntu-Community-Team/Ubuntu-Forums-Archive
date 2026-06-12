---
title: "Trouble installing Dell wlan 1505 w/ ndiswrapper 1.55"
date: 2009-08-09
forum: New to Ubuntu
---

### Post by throwaway85 on 2009-08-09
First off, I apologize if this is addressed within the monstrous dell + ndiswrapper-1.51 thread.  I browsed through it, but was unable to find anything specific to my problem.

So here's what's [not] happening:  I installed ndiswrapper following the guide above, but had to do it three times:  The first time I installed 1.51, but it gave me a bunch of error messages when trying to install bcmwl5.  I went back to the start, removed ndiswrapper, reinstalled, same issue.  When I googled the error message, it was mentioned that there was an issue with user-compiled versions and that I should download the self-installing one.  Great.  I cleaned the previous install, and installed the new one.  I got a fatal error when trying to install bcmwl5, at the ndiswrapper -m part.  Googled that error message, and it said to install the latest version of ndiswrapper from sourceforge.

Great.

So I followed the instructions in the monster thread, removing all previous incarnations and installing ndiswrapper-1.55.  It worked beautifully.

-Except-

The first time I installed 1.51, it recognized my device and installed it as wlan0.  While this didn't actually work, it was nice to see.  This time, however, it installed as [14E4:4328], and there is no existing wlan0.  I've tried creating it manually, but... well, I'm here.

I would greatly appreciate any advice/suggetions.  I'm sure it's probably not a difficult fix, but this is the first time I've ever tried using Linux and I'm greatly confused.  So thanks in advance for any assistance.

P.S.  It won't always be like this, will it?

---

### Post by mhd78 on 2009-08-09
Don't know anything about your card specifically, but maybe try using ndisgtk.  If you are on Jaunty, do

apt-get install ndisgtk ndiswrapper-common ndiswrapper-utils-1.9

Then goto System --> Administration --> Windows Wireless Drivers
to install the inf file for your hardware.
hope this helps, and good luck!

---

### Post by throwaway85 on 2009-08-09
yeah, ndisgtk was the second one I tried.  I got a fatal error, but I was doing it through the console, so I'll try again.

*edit*

So I did what you suggested, and it installed the driver, but the error message "Unable to see if hardware is present."  The bmcwl5.inf file did get installed, and underneath it says the hardware is present, however it will not let me configure the network, saying "Could not find a Network Configuration Tool"

Any thoughts?  I appreciate the help so far.

---

### Post by throwaway85 on 2009-08-10
Shameless self-bump

---

### Post by throwaway85 on 2009-08-10
Another shameless self-bump.  Still stuck here.  I've tried numerous walkthroughs, I've reinstalled Ubuntu several times, still can't get it to work.  Any help would be greatly appreciated.




*EDIT* PROBLEM SOLVED!!!

I apologize in advance, but I feel the burning desire to say this:



!!~**** NDISWRAPPER~!!



Completely unnecessary for this problem.   The following fix fixes it beautifully:

[https://bugs.launchpad.net/ubuntu/+bug/365857](https://bugs.launchpad.net/ubuntu/+bug/365857)

I don't know how one would go about making that solution more visible.  I spent over a day trying to get it working, and it took 3 minutes to fix.

---

