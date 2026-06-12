---
title: "Aspire One networking stopped working!"
date: 2008-11-09
forum: Networking &amp; Wireless
---

### Post by poldie on 2008-11-09
I've had 8.10 32 bit on my Aspire One for a few days now and what impressed me most was I was able to get wireless working painlessly. I booted up, logged in and after a few seconds I was online.  Today it stopped working, and I've spent 30 mins going nowhere.  I followed these instructions:

[https://help.ubuntu.com/community/AspireOne110L](https://help.ubuntu.com/community/AspireOne110L)

Although I've actually got the model 150 with 120gb hard drive.

I think I've disabled the wireless network (adaptor? driver?) somehow.  I can't get to the page where I can choose from the local wireless routers I can connect to.  I can get online using a wired connection, and I tried to reinstall the package from that URl but it didn't install anything and it made no difference.  I've rebooted etc, and tried the switch on the front.  

Any ideas what I can do to sort this?


Edit: I've tried installing wicd - wired networking works with this but again no wireless networks found.

ifconfig -a (something I've seen people request to diagnose this sort of thing) shows eth0, lo, pan0, wlan0 and wmaster0 entries.  I have no other wireless hardware, so I have no way of proving that my wireless router still works.  It has the wireless led lit, though, and it's definately online as I'm using it now on my desktop pc via ethernet. Anyway, there are other wireless networks in my area I can usually see - it would be a coincidence if for the first time ever they all have stopped at the same time this problem as turned up.

Is there some way of brute force reinstalling any part of ubuntu related to networking?


Edit2: The problem seems to have gone away. I turned the laptop off (rather than just restarting), took a break, and when I turned it on it was all working again (although with wicd, not the regular network manager).  

One thing - the audio then wasn't working, and I had to spend 10 mins hunting for options for that. I did a test and found that OSS audio worked, but not alsa or pulseaudio.  I know very little about all this - is there some way the audio and network problems were connected?  I didn't use audio at all while I was trying to fix the network problems.

My earlier question still stands - is there some way of doing a repair or reinstall of stuff like network (or audio etc) in case this sort of problem happens again?

---

### Post by all13d on 2008-11-09
Heck of a coincidence; I just had my aspire's audio stop working a couple hours ago, and after a reinstall, network isn't working either.  Did your audio give static whenever you tried to play something?

---

### Post by poldie on 2008-11-10
> **all13d said:**
> Heck of a coincidence; I just had my aspire's audio stop working a couple hours ago, and after a reinstall, network isn't working either.  Did your audio give static whenever you tried to play something?

Yes. Perhaps it wasn't a coincidence. Maybe some upgrade went out which affects the part of Ubuntu which deals with aspire wireless and audio. I didn't change anything. Play around with the preferences on the volume control icon on the panel and see if you can fix the problem by choosing a different mixer or something.

---

### Post by neilmusgrove on 2008-11-10
My Acer Travelmate wireless has stopped working over the past few days too, previously it was fine. It is based on the Intel 2200 chip. It looks like some updates have broken it. The strange thing is it occasionally works now but about 3/4 of the time it doesn't.

---

