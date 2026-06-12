---
title: "[SOLVED] Unique issues with Netgear WG311v3"
date: 2008-10-28
forum: Networking &amp; Wireless
---

### Post by HotCupOfJava on 2008-10-28
Hello, all - I am trying to get a Netgear WG311v3 wireless card working on my father-in-law's computer. He is using an older AMD Duron box running Xubuntu Hardy. Here is the problem:

The card IS installed and does show to be working, but the machine will freeze when I attempt to surf using Firefox. It does this regardless of whether I am using a DNS url or an IP address in the browser bar. Here is what is weird: I CAN download and install packages through Synaptic! 

What I have already tried: I have used earlier versions of Xubuntu. Dapper has the same problem. Gutsy will NOT install on this box for some reason (the CD is OK - I have done the MD5SUMS for the image AND verified the burn). I AM using NDISWrapper. I have tried the Windows 98, ME, 2000, AND XP drivers. same problem with all. I have tried using WICD instead of Network Manager. I have made sure the firmware on the router is up-to-date. No issues with the connection on any other wireless device. 

Any ideas/help is much appreciated.

---

### Post by HotCupOfJava on 2008-10-29
OK - nevermind. I ended up installing the card into another old box he had - also on Xubuntu Hardy. This one wouldn't boot with the card in it. I fixed that by adding "acpi=off" to the list of boot options. There was apparently an IRQ issue. If anyone else needs to know how to do this, look [here]("https://help.ubuntu.com/community/BootOptions").

---

