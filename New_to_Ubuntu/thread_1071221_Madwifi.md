---
title: "Madwifi"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by rottenpunker on 2009-02-15
I have an Atheros wireless card. When I go to System > Administration > Hardware Drivers, it says that my Atheros driver is activated. However, Wicd does not see any wireless networks. So I downloaded Madwifi-0.9.4, but I have no idea how to install it or what to do with it. I've done a lot of searching, but everything I've found is either written in a way that's way over my head, or it hasn't worked. So if anyone could give me some directions that I might be able to follow, I'd greatly appreciate it. :)

---

### Post by rharriso on 2009-02-17
well it's probably in a tarball right now, so untar the file and store it somewhere, then run the install script inside the folder. It comes with an install sscript i'm sure.

---

### Post by spcwingo on 2009-02-17
> **rottenpunker said:**
> I have an Atheros wireless card. When I go to System > Administration > Hardware Drivers, it says that my Atheros driver is activated. However, Wicd does not see any wireless networks. So I downloaded Madwifi-0.9.4, but I have no idea how to install it or what to do with it. I've done a lot of searching, but everything I've found is either written in a way that's way over my head, or it hasn't worked. So if anyone could give me some directions that I might be able to follow, I'd greatly appreciate it. :)

I had the same problem with the built-in drivers on the wife's machine.  I just unchecked the drivers in system>admin>hardware drivers and used ndiswrapper to install the Windows driver.  It works perfectly now.  To do that just pop your live CD back in the drive and open synaptic.  Now enable the CD rom as a source.  Search for ndisgtk and install it.  Now's the hard part.  Finding the XP driver for you model of card.  After you find it open ndisgtk (system>admin>windows wireless drivers) and press install.  Navigate to wherever your driver is and select the .inf file.  If it accepts it you should have wireless up and running at this point.

---

