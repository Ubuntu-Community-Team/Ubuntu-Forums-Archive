---
title: "PCI/USB Wireless card that just works??"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by Johny79 on 2007-10-21
Before I start I'll say that I'm fairly new to Linux/Ubuntu :)

I've been running it on my laptop for a while, first 6.06, and just moved to 7.10, and my experience of it has been great, the built in wireless worked straight off with no configuration other than adding the WPA key.

So with it going so well on my laptop I thought I'd give it a go on one of my desktops, and this is where I hit a big problem, the Dynamode USB wireless adapter isn't recognized, and after doing lot's digging around via Google I can't find a mention of any compatibility for any Dynamode wireless adapters anywhere!

So assuming it just wasn't going to work I thought "No problem, I'll just buy another wireless adapter", so I began looking around for one that was compatible, a few days later I find myself still searching, I found another thread in the forum (quite old) that gave a link to a list of USB / PCI adapters and whether they work "out of the box" or not, of the few that do work "out of the box" I can't find a single one of them on sale anywhere in the UK, and for most it's only a specific version of the card that works, and most of the time you don't know precisely what version you will get until it arrives!

I'd prefer a USB adapter, but PCI would be ok, so does anyone know of one which will definitely work "out of the box"?? Surely there must be at least one available!?

---

### Post by SactoBob on 2007-10-22
A wireless bridge.
[http://ubuntuforums.org/showthread.php?t=572070](http://ubuntuforums.org/showthread.php?t=572070)

---

### Post by Johny79 on 2007-10-22
Yeah I did consider that, I even have an AP laying around, but unfortunately my ISP supplied ADSL router doesn't support bridging (well it would if they hadn't used their own firmware version), and it would break my TOS to try and use a different one, plus they wouldn't give me the settings for it :(
Should using the AP as a repeater work? I've just been playing and set the AP up as a Repeater, it sees the main ADSL router, reports a good signal strenth, and that it's connected, i've matched settings between them, including security but it's not forwarding anything on, does a repeater just forward the wireless signal or requests made via it's ethernet port too??

Completely stuck :(

---

### Post by SactoBob on 2007-10-22
> but unfortunately my ISP supplied ADSL router doesn't support bridging

I am a bit lost. I don't think your router needs to support bridging. The bridge itself takes care of that. Your wireless router will see the bridge as just another client, like a pci or usb wireless card.  It is the bridge that converts the wireless communications from the router to multiple wired outlets.  So I guess I must be missing something?

If you can get a wireless card talking to your router, I don't see how you can't get a bridge talking to your router, which it should do "out of the box".  I don't understand why you need a repeater??  Don't you just want an out of the box solution to wirelessly connect from your wireless router to a desktop?

---

### Post by amphet on 2007-10-22
I have a Microsoft MN-510, it doesnt actually works "out of the box" but you can install linux-wlan-ng and get it running pretty quick. I have been using it since Edgy without any major issues.

---

