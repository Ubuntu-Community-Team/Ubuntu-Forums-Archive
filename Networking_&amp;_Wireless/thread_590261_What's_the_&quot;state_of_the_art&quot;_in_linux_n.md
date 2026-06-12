---
title: "What's the &quot;state of the art&quot; in linux networking configuration today?"
date: 2007-10-24
forum: Networking &amp; Wireless
---

### Post by jemenake on 2007-10-24
First, a little background: I've got a laptop that I've had Debian on for about 5 years (before udev, hal, hotplug, sysfs, etc.). Old school. Over the years, upgrades have broken a thing or two and, in the process of fixing them, I discovered that there's a new way of doing 'xyz' that's much slicker than the old way. Super.

Then, I tried Ubuntu. Good lord! Everything just works... and much better than my legacy Debian install. Drive icons show up when I plug USB drives, etc. Nice! So, I decide to dual-boot my laptop with the old Debian and the new Ubuntu so that I can compare them... to discover the "new" way of doing things that Ubuntu is using and then I can make those changes to my Debian install (Yes, I could just switch to the Ubuntu, but I've got a lot of local stuff installed in my legacy install).

So... the first thing I wanted to fix was networking. On the Debian install, I've gone through, over the years, iwconfig scripts, waproamd, ifplugd, and wpa_supplicant. It works pretty well, but it doesn't automatically dhcp on the wireless when it boots or resumes from suspend. I could dive in and try to diagnose the issue, but I figured that I could just do it like Ubuntu does since it will then work with the spiffy network-manager applet as a bonus.

And that's where I'm stuck. I'm looking through /etc and I can't find anything that would let me configure the static/dynamic state of the interfaces, or WPA keys, or anything! /etc/network/interfaces only has my loopback interface. /etc/wpa_supplicant only contains a couple of generic scripts. I grepped all of /etc for "eth0" and "eth1" and the only thing I really found that seemed promising was /etc/udev/persistent-net-generator.rules, but that still didn't have anything involving dhcp. I just can't find where this stuff is all configured!

So, I give up. At some point when I wasn't paying attention, it appears that the Linux world greatly changed the way network interfaces are managed. Where is the config kept these days?

---

