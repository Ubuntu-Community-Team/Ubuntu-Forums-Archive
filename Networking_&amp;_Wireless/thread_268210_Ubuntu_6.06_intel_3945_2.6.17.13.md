---
title: "Ubuntu 6.06 intel 3945 2.6.17.13"
date: 2006-09-29
forum: Networking &amp; Wireless
---

### Post by Charles Hand on 2006-09-29
Wow. I'm really frustrated.

Ubuntu 6.06, intel 3945 wireless chip, kernel 2.6.17.13. Core duo 686 smp. I've read dozens of procedures, most of which don't match up with my directory structure for some reason.

I tried ndiswrapper, but I get 

[4294700.493000] ndiswrapper (load_wrap_driver:112): loadndiswrapper failed (65280); check system log for messages from 'loadndisdriver'

and my sense from the Internet is that this is an unresolvable bug in something.

So I tried to compile ipw3945 driver from intel. (This is where some of the major directory disconnects happen). It complained that it couldn't find ieee80211.h, even though I pointed to it in a dozen different places using make IEEE80211_INC=xxx. So I downloaded ieee80211 from sourceforge, removed all over references to it and compiled it.

No matter where I tell make to put the ieee80211 includes, ipw3945 won't acknowledge that there is a ieee80211.h file there, when THERE IS!!!

So I finally tried to make ipw3945 using make IEEE80211_INC=<source directory where I built ieee80211>. Finally it got past the not finding ieee80211.h file, but now it complains that it wants .mod files, and there  are no .mod files in that directory. Nor are there any .mod files in any of the include directories for ieee80211.

](*,) 

Has anybody gotten anything to work? Well, I know from searching the forums that different people have found different things to work. I guess what I'm trying to find is, how do I get all these things that are supposed to work to work?

The wireless chip works right out of the box when I install Ubuntu with a 386 single-processor kernel. No ipw3945, no ndiswrapper.

---

### Post by Charles Hand on 2006-09-29
OK, I got something to eat. 

I think I'm going to:
a) Remove everything everywhere related to iee80211
b) Rebuild the 2.6.17.13 kernel from scratch
c) Focus on hacking the sources/makefile for ipw3945 until I can force it to compile using the ieee80211 files which come with the kernel.

I think this course is best because it has the minimum number of source files to hack - less than the kernel or ndiswrapper.

---

### Post by Charles Hand on 2006-09-30
OK I've gotten ipw3945 to compile, and I've gotten it to start up manually and run the wireless chip.

Now I need to learn how to integrate this into Ubuntu so I don't have to start the driver/daemon up by hand. Anybody who knows anything about that, feel free to chime in. When I get done I'll write a howto.

---

### Post by Bardia on 2006-10-05
I'm stuck too.  Just bought an MSI 1057 and Installed EMT64 Ubuntu.  I've never used Linux deeper than the GUI before, so I haven't even been able to understand the how-to's people have been writing.

Anyway, my 3945 Wireless works just fine in Windows, but Ubuntu can't see it.  I spoke with a guy on IRC, and he had me run some commands that seemed to show that Ubuntu has a driver for it installed, but it doesn't work yet.

I also installed a gnome wireless utility, and that doesn't recognize the wifi card either.

Basically, I'm really in need of help on this one too.  Unfortunently I'm very much a techie and computer geek, but a complete newbie with Linux, so I need something even more basic than the how-to's that have already been posted.

I'd very much appreciate a step-by-step if anyone figures this out.  I'll be able to research pretty much anything on my own to learn this thing once I have internet, but without my wifi card I'm hosed.

---

