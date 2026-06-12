---
title: "Belkin F5D7050"
date: 2007-09-03
forum: Networking &amp; Wireless
---

### Post by laytek on 2007-09-03
I have been working to enable wireless networking using Ubuntu. I just want to pass on what I have learned.
In my network the wireless access point is a Belkin 802.11g model F5D7230-4. I have two Belkin F5D7050 USB Network Adapters.

The first is an F5D7050 (FCC ID: K7SF5D7050), which turns out to be version 1. I believe this uses the rt2570 driver. I have spent 2 days compiling source code, blacklisting modules and trying any other advice that I could find from the internet. None worked. If I did nothing, my computer would lock up, with system monitor showing 100% CPU usage. Blacklisting certain modules would prevent the lockup. but the Adapter would not work and many strange things would happen (such as not being able to start any programs).

Then I remembered that I have a second adapter.

The second adapter is an F5D7050 (FCC ID: RAXWN4501H), which is version 4. I plugged this adapter into the USB port, and everything just worked! Network Manager showed all of the available wireless networks, security, etc. Too easy!!

I write this to tell  those that are much smarter than me concerning wireless networking that there is a problem in the Belkin world with these USB adapters (most likely a DUH statement). Maybe it has something to with the Adapter being properly recognized. Also, to those having problems, have faith. I know that Linux and Ubuntu can be frustrating at times, but it really works - most of the time. Consider different hardware if yours doesn't work.

LayTek

---

### Post by chris027 on 2007-09-04
lol, yea i second that. I've spent nearly a week trying to get a belkin 7050/2571chip (version 2 i believe) to work and still haven't. I've finally waved the white flag on the belkin and tried to use my other usb adapter, just to find out it uses the SAME ra(T)link chip! The problem with both adapters, they recognize the networks but won't connect to them. I also just installed wicd, to try that approach..same thing. There is a relatively new driver for it, the RT25USB, but so far I haven't found a tutorial on it and the included doc is very vague for a noob.

---

### Post by scrapnon on 2007-09-04
Yeah, the F5D7050v4 has the zd1211 chipset, and the driver for it has been include in the kernel since 2.6.20, So most distros with linux 2.6.20 or later should support it right outta the box.

---

