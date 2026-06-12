---
title: "Trying to set up a wireless network, first time on Ubuntu..."
date: 2008-03-15
forum: Networking &amp; Wireless
---

### Post by Gamerunknown on 2008-03-15
I'm a total noob looking for help with using a wireless USB on my PC with Feisty Fox. I'm using a Belkin Wireless USB with a Zydas chipset, but I don't even know what that means. Nor do I know what "kernel" I'm on... I'm disappointed with how little I know, to be honest.

Apparently though, I have to find a "Makefile" in the archive of something I downloaded to convert my Windows drivers to Linux ones and I don't know how to access that. 

I think I can't use ndiswrapper, even though I downloaded it*, because it says it needs Windows Drivers. If they're for the device, that's fine, but I don't have the disc for a Windows OS. 

*I do have access to another computer, but it's occupied at the moment and I have to transfer files using USB.

Any help with finding out what a "Makefile" is will be appreciated, as will helping me set up a wireless network any other way.

I'm actually posting from the Wiis opera browser, if anyone was interested. 

Thanks, gamerunknown.

---

### Post by hookzilla on 2008-03-15
Don't feel too unusual.   I was the same way.  I'm still a noob, but I'm getting there, with lots of help from the good folks in this forum.  I'm probably not the best person to help you, but this will get you started

For starts, the first thing you'll need to know is the model and version of your adapter.  It's printed on the adapter somewhere.  Then you can lookup the specific chipset.    As for the drivers, look on the disc that came with the adapter.  There are other ways to find what they are, but the adapter info is the start.   

Welcome aboard and good luck.

---

### Post by chewearn on 2008-03-15
hi, if you are still interested:
The first thing to do is try the latest ubuntu, gutsy gibbon 7.10, instead of feisty fawn 7.04.  The reason: there is a huge improvement in wireless devices support going from 7.04 to 7.10.

I believed there is already a native linux driver for your Belkin USB adapter; therefore, there is no need to use ndiswrapper+windows driver.  The problem is, feisty fawn might be too old already and the Belkin device was not supported then.  


With gutsy gibbon 7.10, the device will probably be auto-detected and work right away, without any additional drivers needed to be installed.  Just make sure to plug Belkin in when you install ubuntu.

My source of info here:
[http://opensource.bureau-cornavin.com/belkin/index.html](http://opensource.bureau-cornavin.com/belkin/index.html)
[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=4519418](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=4519418)
Note of advice: don't follow the instructions in these webpages, unless you are already l33t in linux, and know what's going on.

---

### Post by Gamerunknown on 2008-03-15
Alright, I would try getting  Gutsy Gibbon if it wass 700Mb or less, since the most storage I've got at the moment are CDs...

But it's 4 gigs...  I think I have less than that left on this hard drive. Eeep.  

I've got a Belkin Wireless G, with a model number F5D7050. 

The drivers all begin with "BLKWGU" (9X, 2K, 64 and XP) and a website I visited (but forgot to bookmark :sad:) said something about a Zydas driver... 

I guess they correspond to the various OS. Funnily enough, I've bought several of the same Wireless USBs, since they're quite cheap and they work well enough. I'm just fairly clumsy and end up crushing them. I have quite a few different discs which may have different drivers I could try.

---

### Post by ugm6hr on 2008-03-15
> **Gamerunknown said:**
> Alright, I would try getting  Gutsy Gibbon if it wass 700Mb or less, since the most storage I've got at the moment are CDs...

But it's 4 gigs...  I think I have less than that left on this hard drive. Eeep.  

Where are you getting Gutsy from?  It fits on a single CD just fine.

After installation, it will take no more space than Feisty (about 10GB recommended total).

Whether Gutsy will solve the problem, I don't know.

In order to confirm exactly which Belkin device you have:

```
lsusb -v
```

---

### Post by Gamerunknown on 2008-03-19
Huh, I must have been downloading an odd version then. 

Well, I got Gutsy and I'm now online. Thanks guys. :mrgreen:

---

