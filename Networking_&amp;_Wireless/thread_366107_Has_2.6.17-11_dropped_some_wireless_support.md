---
title: "Has 2.6.17-11 dropped some wireless support?"
date: 2007-02-20
forum: Networking &amp; Wireless
---

### Post by OldGaf on 2007-02-20
I see quite a few people who had support for wireless cards in 2.6.17-10, but once they upgrade to 2.6.17-11 the card can not be detected. I understand that if you compiled third party drivers you will need to do so again after the kernel update. But this is not the same. These cards worked "out-of-the-box" with previous kernels but the new one seems to not support them.

Can anyone comment on this?

---

### Post by gradedcheese on 2007-02-20
Yeah, there is an ABI change introduced at -11 that causes the need for recompiled drivers.  Many people have this same problem.  My suggestion is to reboot into the previous kernel (which is perfectly fine to continue using).  To do that, reboot and press ESC right after the BIOS screen to get into the Grub menu.  Select the second-newest kernel and boot.  If that fixes it, make that kernel the default.

---

### Post by OldGaf on 2007-02-20
> **gradedcheese said:**
> Yeah, there is an ABI change introduced at -11 that causes the need for recompiled drivers.  Many people have this same problem.  My suggestion is to reboot into the previous kernel (which is perfectly fine to continue using).  To do that, reboot and press ESC right after the BIOS screen to get into the Grub menu.  Select the second-newest kernel and boot.  If that fixes it, make that kernel the default.

Thanks for the reply..... this board is so busy now that it can be hard to get a reply.

I *can* get it to work by booting to an older kernel, BUT...... I need the latest Nvidia driver and that seems to need 2.6.17-11. 
As I said, there was no need to compile the nic under the old kernel...... it just worked. My question is, did they *DROP* support in this new kernel?

BTW..... what does ABI stand for?

---

### Post by gradedcheese on 2007-02-20
No one dropped support for anything.  The ABI (application binary interface) changed, which is considered OK to do because drivers should be open source and can then be recompiled as needed.  However updates to such kernels shouldn't have been handled the way Ubuntu did it (in my opinion).

The significance of an ABI change is basically like this: some data structures or similar things changed to improve the kernel and/or fix bugs.  The drivers compiled for the previous kernel assume certain data structures, but they need to be compiled (and possibly modified) for the new ABI in order to work with this new kernel.  This is normally not a big deal, but it definitely didn't get handled too gracefully.

What driver are you using?  If you don't know, then what chipset are you using?  Running "lspci" should tell you the latter.  Chances are that the ubuntu people did update your driver and its available via apt-get or update manager, but if you don't have 'net access, it's hard to get it ;)  You could, from the old kernel, try to update and see if you get a new modules package.  Finally, if all else fails, you can download and compile the driver for the new kernel yourself.  This isn't actually that hard to do, if you need to.

---

### Post by OldGaf on 2007-02-20
> **gradedcheese said:**
> No one dropped support for anything.  The ABI (application binary interface) changed, which is considered OK to do because drivers should be open source and can then be recompiled as needed.  However updates to such kernels shouldn't have been handled the way Ubuntu did it (in my opinion).

The significance of an ABI change is basically like this: some data structures or similar things changed to improve the kernel and/or fix bugs.  The drivers compiled for the previous kernel assume certain data structures, but they need to be compiled (and possibly modified) for the new ABI in order to work with this new kernel.  This is normally not a big deal, but it definitely didn't get handled too gracefully.

What driver are you using?  If you don't know, then what chipset are you using?  Running "lspci" should tell you the latter.  Chances are that the ubuntu people did update your driver and its available via apt-get or update manager, but if you don't have 'net access, it's hard to get it ;)  You could, from the old kernel, try to update and see if you get a new modules package.  Finally, if all else fails, you can download and compile the driver for the new kernel yourself.  This isn't actually that hard to do, if you need to.

I don't know what driver I am using as it just worked on it's own. I did not need to install any drivers for it. 
It is a D-link DWL-G510. The system sees it as follows:
> $lspci
Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)

I do have an onboard nic that does work so I do have access until I move the box back upstairs.

---

### Post by gradedcheese on 2007-02-20
Ah yes, I have that same chipset (Atheros AR5005G) in my card.  Unfortunately my laptop's motherboard just died, otherwise I'd update to -11 and recompile and then take you through the same steps.  Since you have a working LAN interface, try updating so that you have any possible module updates installed and see if that helps (in -11).  

If not, what you need is to compile madwifi for -11, this will not be very painful to do.  You need the right headers package:

sudo apt-get install linux-headers-2.6.17-11-generic

Now download the madwifi driver source, uncompress it, and build it (just cd to its directory and run "make").  That should do it.  The only trouble is I am not sure if you need madwifi or madwifi-ng (the former is sometimes called madwifi-old) and with my dead laptop I can't try it for you.  I hope that helps a little anyway.

---

### Post by OldGaf on 2007-02-20
> **gradedcheese said:**
> Ah yes, I have that same chipset (Atheros AR5005G) in my card.  Unfortunately my laptop's motherboard just died, otherwise I'd update to -11 and recompile and then take you through the same steps.  Since you have a working LAN interface, try updating so that you have any possible module updates installed and see if that helps (in -11).  

If not, what you need is to compile madwifi for -11, this will not be very painful to do.  You need the right headers package:

sudo apt-get install linux-headers-2.6.17-11-generic

Now download the madwifi driver source, uncompress it, and build it (just cd to its directory and run "make").  That should do it.  The only trouble is I am not sure if you need madwifi or madwifi-ng (the former is sometimes called madwifi-old) and with my dead laptop I can't try it for you.  I hope that helps a little anyway.

Thanks. Sorry to here about your MoBo :( 
I did a reinstall of the system this morning and did a dist-upgrade. I have all the headers / restricted modules etc.
I just tried ndiswrapper without success and started downloading madwifi prior to reading your reply. I will try both wifi and wifi-ng.

I am still wondering why it will not work "out-of-the-box" with -11 when it did with -10!!!!! 
You may want to hold off on going to -11 once your system is up and running.

---

### Post by gradedcheese on 2007-02-20
The reason for working with -10 and not -11 is that the driver (which comes with Ubuntu, do not use ndiswrapper!) was built for the -10 ABI.  It needs to be rebuilt for -11 and then it will work fine, but it looks like the ubuntu guys didn't make a package to facilitate this :(  By the way, these ABI changes don't happen that often, so this is sort of an odd problem, and not indicative of what to expect normally.

I hadn't upgraded to -11 yet, but when I do I'll just rebuild the driver.  That is, once my replacement motherboard arrives (eBay to the rescue, as usual).

---

### Post by OldGaf on 2007-02-20
OK, I got working with Madwifi. Thanks very much for your help with this. I will pass this info on to the many forums I have threads posted on this.

Good luck with your MoBo. !

---

### Post by gradedcheese on 2007-02-20
Good job!  Yes, do tell others how to solve the problem.  Specifically, tell them in here: [http://www.ubuntuforums.org/showthread.php?t=358004](http://www.ubuntuforums.org/showthread.php?t=358004)

---

### Post by MikeDK on 2007-04-16
hi, just want to add, that i got no problems with sound in 5.1 stereo in feisty with 2.6.20-15-generic
thou it was working fine maybe even better in 2.6.20-14-generic Mainboard is an MSI NEO FSR, but ill guess itll be better as final release of feisty's just around the corner cheers m8's LOL wrong thread

But anyway's happy release

---

