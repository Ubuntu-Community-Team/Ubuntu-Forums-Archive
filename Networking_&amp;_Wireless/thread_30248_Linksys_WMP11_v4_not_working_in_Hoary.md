---
title: "Linksys WMP11 v4 not working in Hoary"
date: 2005-04-27
forum: Networking &amp; Wireless
---

### Post by Brunellus on 2005-04-27
I did a dist-upgrade from Warty to Hoary. 

This has broken my wlan access, which was expected.  My only 'net access is through a Linksys WMP11 v4 wlan adaptor, which I was able to get running reliably in warty by using ndiswrapper.

So after the upgrade-dist, I did the usual.  Removed all the .inf files from ndiswrapper, removed ndiswrapper itself, installed the necessary kernel-header files.  Built ndiswrapper with "make" (from the source tarball that I'd been using all that time).  Did a "make install."  no errors.  loaded the .inf files.  no errors.  Modprobe ndiswrapper returns no errors.

And yet, while lspci tells me that the Linksys card is there, and ndiswrapper reports all drivers loaded and hardware present, there is no wlan0 device!

I need to fix this as soon as possible.  

I'm running Hoary.  The kernel (and its headers) is 2.6.10-5-i386.

---

