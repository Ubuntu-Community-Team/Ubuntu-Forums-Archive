---
title: "Wireless Help: Linksys WPC54GS"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by jsattin on 2008-05-02
Hi. I just installed 8.04 without difficulty on my IBM Thinkpad T30.  It appears that my wireless card is recognized, and a driver installed, but it is disabled, despite my having enabled it in the network manager.  Of course, I might be wrong about any of the above!  Following is what I think are the most relevant data when I entered "lshw" into my terminal.  Thanks for any help!

*-network
description: Network controller
product: BCM4318 802.11g wireless LAN Controller
configuration: driver=b43-pci-bridge

*-network DISABLED
description: Wireless interface
physical id: 1
logical name: wlan0
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

---

### Post by dstew on 2008-05-02
Check in the System --> Administration --> Restricted Drivers Manager to see if there is firmware to install.

---

### Post by jsattin on 2008-05-03
There is (in 8.04) no "Restricted Drivers Manager" in System-->Administration.

There is a selection "Hardware Drivers".  When I open it, it says "No proprietary drivers are in use on this system."

I've since found that my ethernet connection doesn't work, either.

What a headache--any further thoughts?

Justin

---

### Post by dstew on 2008-05-03
It doesn't look good. There should be a firmare install available. See this [HowTo]("http://sudan.ubuntuforums.com/showthread.php?t=197102") at the top. If you can't get that firmware, you might have to do it the old-fashioned way.

There are two ways you can go to try to get the Broadcom wireless to work if the Hardy firmware tool is not working. One, try to get the native Linux drivers to work with the Broadcom firmware. [Here]("http://linuxwireless.org/en/users/Drivers/b43") is a page about that. Two, use ndiswrapper and the Windows drivers. [Here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") is a HowTo about that.

---

### Post by jsattin on 2008-05-03
I think I found the firmware.  I had to configure the package manager to look in the CD-ROM drive, and when I put my install CD in there, b43-fwcutter appeared.

I tried to install it, but encountered an error.  When I looked at the log, it appeared as if it were trying to access the internet as part of the process.  

As I mentioned in my last post, I can't get the ethernet connection to work, either, so it looks like I have to start there.

I'm not sure why the ethernet connection isn't working.  I'm using a cable modem hooked to a Linksys router.  Both the wireless and ethernet work on the Windows XP computer I'm using to post these questions.

So, any ideas why the ethernet connection isn't working?

Thanks very much for all your help!

---

### Post by jsattin on 2008-05-03
Oh wait, I misspoke.  My ethernet is NOT working on my other computer; only the wireless is working.

I changed the cable to no avail, so something else must be wrong.  I never thought I'd be up and running wirelessly and not be able to use my wired connection . . .

---

