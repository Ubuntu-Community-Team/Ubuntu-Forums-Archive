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

### Post by ntg on 2006-11-07
You should install the 686 **restricted **package as well 
(search for restricted in Synaptic)
after that it works unless you try to install a vanilla kernel...
That one I still haven't managed....

---

