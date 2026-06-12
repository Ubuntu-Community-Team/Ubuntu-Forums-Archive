---
title: "Smc Wireless"
date: 2004-12-13
forum: Networking &amp; Wireless
---

### Post by idarnor on 2004-12-13
Hello all. I am new to Ubunto and new to the forum so please give me some advise. I installed Ubuntu but I have problems with my wireless card. From what I have read on different linux forums the SMC 2802w is not supportet. Is that so?

---

### Post by bcmc on 2005-01-03
I have a SMC 2635w card and it is detected in Xandros but not in Ubuntu although it shows up in device manager. I was woundering how to config it.

---

### Post by micko121 on 2005-04-14
I've been working on getting my SMC2635W card to work for hours, and finally got it to work.  From what I gather:

First, go into Synaptic, search for and install the "linux-headers" package for your version of Ubuntu (if it's a clean, plain vanilla Hoary install, that means "linux-headers-2.6.10-5-386").  This provides the kernel source needed to compile the driver module.

If you have a [COLOR=Red]RED card[/COLOR], which I gather is "version 1" of this model, download and install a driver from [[COLOR=Red]THIS SITE[/COLOR]](http://aluminum.sourmilk.net/adm8211/) (the latest version should work with Hoary).  The install is really straightforward:  first go into Synaptic and make sure you have the "module-init" package installed, then just extract the driver and run "make install".  Then it should work.

I say "should", because I couldn't get it to work for me.  It turns out that that's because I had a [COLOR=Blue]BLUE card[/COLOR] ("version two"), which meant that I needed drivers for a totally different chipset.  You can get those drivers at [[COLOR=Blue]THIS SITE[/COLOR]](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads).  This one requires that you type "make" and then "make install".  It will give a message about /etc/modules.conf not existing, and then it will "append" to that file, which means it actually creates it.  Since I wasn't at all sure that Ubuntu would know to look at that file, I opened the newly created /etc/modules.conf file and copied the line from it into the "misc" section of /etc/modprobe.d/aliases.  I'm not positive this step is necessary, since I didn't test before doing it, but I don't think it can hurt, either.
Finally, type the following lines into the terminal:
modprobe rt2400
ifconfig ra0 up
The indicator on the card should light up at this point.  Now you can go into the System menu, Administration, Networking, and the card should show up as ra0, a Wireless Network Connection! Click on it, click Properties, and set it up as you need, and you're good to go.  If it doesn't work the first time, try restarting and then see if it does.  The only issue I've come across is that it doesn't correctly report signal strength (it always lists 0%).

An alternative solution to either of these is to use [ndiswrapper](http://sourceforge.net/projects/ndiswrapper/), which puts a wrapper around Windows drivers.  Ubuntu comes with ndiswrapper installed, so that's one benefit to this approach.  (The [driver files still need to be installed](http://ndiswrapper.sourceforge.net/phpwiki/index.php?Installation) separately, though).  Apparently it works decently, too, but I haven't tried it.

Good luck, I hope this helped!  :) 

-Mike

---

