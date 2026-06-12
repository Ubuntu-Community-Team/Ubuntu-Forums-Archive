---
title: "Configuring DWL-G122 and/or Xircom RealPort Ethernet"
date: 2008-08-27
forum: Networking &amp; Wireless
---

### Post by TheDonkey on 2008-08-27
Ok, so I've had an old Dell Latitude PP01X laying around for a couple years now without a harddrive, and my Windows server crashed, so instead of trying to fix THAT, I decided to pull this one out and get Ubuntu running for a server.

Problem is, I can't get networking running...sorta...
Explanation follows

I went and installed 8.04 Desktop on the beast, I then plugged my DWL-G122 into it, and everything was fine and dandy, it saw it, it recognized and connected to my WPA Encrypted WiFi network.
The reason I HAD to use the G122 is because the Xircom card already in the machine wasn't working(or so I thought)

Turns out that the pins were just bent in and it didn't see the cable.

So now that I've played around with the GUI, I wanna reinstall but this time, install to the Server version to save RAM and space(it's only a 10GB HD)

Problem is, is that I can't do that until I can figure out how to get at least one networking method running from the CLI


The ethernet card for some reason doesn't get an IP from my router(WRT54G with DD-WRT V.24) No matter what I try, teh light on the card and router light up, the card transmits, but never receives and no IP is given. I've also tried setting it static with no luck.

As far as WiFi goes, I can't seem to find a decent comprehensive guide on how to get WPA2 configured and running from the CLI, it all works fine from the GUI, but that's not what I want.



This is a really confusing post to read, and I see that myself, so if you need clarification, I'd be more than happy to clarify.

Thanks in advance for any help.

---

