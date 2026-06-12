---
title: "BCM4309 wireless on Latitude D600"
date: 2008-07-03
forum: Networking &amp; Wireless
---

### Post by HieroPosche on 2008-07-03
I've been trying for the past few days to get my BCM4309 internal wireless card up and running, and can't seem to figure it out for the life of me.

At one point I had my wireless funtioning on feisty and gutsy, but then I swapped my laptop over to slackware.  Was using slack for about a year and never got the wireless working on that, so decided to come back to gutsy (HH didn't show the restricted drivers, and I couldn't get anything to load manually, so I figured I'd try gutsy again) I don't recall having to do anything other than enabling the restriced drivers for the "firmware for broadcom 43xx chipset family" when I had it working in the past.

Now when I try to enable those drivers, I get the message

```
The software source for the package
bcm43xx-fwcutter
is not enabled.
```

I've tried manually installing the fwcutter package via thumb drive, and I've also tried installing ndiswrapper, but the dell drivers don't work for ndiswrapper.

I've searched high and low for a HOWTO or workaround for this card, but can't find it anywhere.  If anyone happens to know how to get this card up and running again, either with Gutsy or Hardy, I would greatly appreciate it.

---

### Post by HieroPosche on 2008-07-03
Finally succeeded in (i believe) properly installing and configuring bcm43xx-fwcutter so that the restricted driver can be used.  I was able to use the restricted driver manager to browse to the .sys file for the driver and it seems to have accepted it, but it is still not showing any networks available.

Is there something I missed?

---

