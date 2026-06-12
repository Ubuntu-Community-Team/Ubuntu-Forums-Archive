---
title: "Unable to see router on network"
date: 2007-02-05
forum: Networking &amp; Wireless
---

### Post by PimpBob on 2007-02-05
I have recently decided to attempt running Linux on my home PC.  I started using Debian Linux with 2.4 kernel and network would work great.  then I needed to upgrade my kernel and couldn't get network to work with the 2.6.8 kernel.  So I downloaded Xubuntu and installed.  Still a problem with network.  'ifconfig' is showing the card but there is no IP address.  I have tried the pppoeconf util and still cannot find anything.  I have also tried 'dhclient' and still see's nothing.  I have also tried pinging the router and nothing.  

So I ran the Live CD and took out the slash option to watch what was loading and when it went to find my NIC card it found it but said there was some sort of problem and I should try using '8331 driver' (i think it said that but everything goes by real fast.)  

So my question is can i change the driver that loads the nick card. and if so how do i go about it. Also is there a log that has everything that was scrolled during boot?

---

### Post by PimpBob on 2007-02-05
I found out the problem.  aparently Debian based distributions have a problem loading RealTek 8139 Network cards.  to fix this I typed the following into the terminal

sudo modprobe 8139too

then when i rebooted I edited the grub menu and turned acpi off and removed the splash screen to see what happened and no more errors.  Firefox worked great.

---

