---
title: "can't get prism 3890 on advent 7039 to work"
date: 2006-08-15
forum: Networking &amp; Wireless
---

### Post by lmcogs on 2006-08-15
Hi 
Running 2.6.15-26-k7, dapper drake and all seems to be going well but can't get the internal wireless card which is a prism 3890 to work.

iwconfig gives wireless on eth2 but no access point.
lsmod |grep prism
prism54 61064 0
don't seem to be any firmware.

modprobe -l |grep prism gives both prism54_softmac/islsm and prism2 modules.

Any help please

---

### Post by claneverett on 2007-01-16
Today I decided to take the plunge with my laptop (an Advent 7039) and set up Ubuntu. I've been using it for a while on desktop machines but I avoided the laptop because I thought it would be problematic. I was wrong.

I have found a way around this wireless network problem, although it may be classed as a bit of a cheat by the more hardcore Linux users :-D 

I have read a number of posts that identified the hot key button as a problem with this model of laptop, although someone suggested messing around with the bios may resolve this issue. This is not strictly true although it does help.

I started by installing the original windows disk that came with the machine. I then downloaded the latest bios from the Advent support site here

http://support.pcworld.co.uk/layout.aspx?ID={fdd2b14a-fccf-4a19-9693-2a6837f69d87}&CatID={0570be4c-fedf-4474-a2f1-21b35bba8daa}

Follow the instructions carefully to make sure you install this correctly.

I then rebooted the machine and hit F12 to enter the set up (BIOS). Navigate to the Advance tab. Go through the options until you find the one related to the wireless networking hardware. It has two settings, "Disabled" and "Last State". Select "Last State". Save the BIOS and exit.

Boot Windows and using the appropriate button activate the wireless network.

Shut down the laptop.

I then ran Ubuntu 6.10 for AMD 64 desktop from the live CD. I fired up the Networking tool and activated the wireless network in the properties dialogue. I filled out my network details in the correct places and hit OK.

That was it, everything works and I am typing this on my laptop using a wireless connection.

To test this wasn't a fluke I unplugged the laptop and disconnected the battery. When I reconnected and rebooted it all worked fine. I guess you just need to initially run windows to set the Prism Wireless Network chip in to the correct mode. I will now be deleting windows!

I hope this helps, and perhaps one day we will find a more elegant solution!

Regards,

Chris

---

