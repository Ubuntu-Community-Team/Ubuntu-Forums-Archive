---
title: "Intel 82845G Integrated Graphics... Ubuntu 9.10"
date: 2010-06-20
forum: New to Ubuntu
---

### Post by Stigmata13 on 2010-06-20
Hello. I've been using Ubuntu for a while, but I need some advice. I recently got my brother to switch to Ubuntu. He was previously using Windows XP, but his system was so bogged down the performance was horrible, so I managed to convince him to switch. His system specs are:

2.6ghz Pentium 4
256-384 mb of ram? Not sure on the exact number here, but it's one of those.
40 gigabyte hard drive
And his graphics controller is an integrated Intel 82845G

I had heard that Xubuntu ran better on older machines, so I downloaded and burnt a copy of Xubuntu 10.04, but I couldn't get it to boot, I would get strange graphic distortions, and the screen would then blank. This would repeat until I hardkilled it.

Anyway, I ended up installing Ubuntu 9.10 (32 bit, of course) on his computer, and it installed fine (slowish, but to be expected), but it would only boot into a resolution of 800x600 max, with no hardware acceleration.

I did some searching, and I found out that adding "nomodeselect" to the grub bootloader would solve the resolution problem. Well, it did, but it created a problem of it's own. Since then, at the recommended resolution for that card, the system became very laggy and unresponsive, and simply moving the cursor would cause it not to show any movement, and then 5-10 seconds later jump to a different spot on the desktop.

Having used linux for a while, I knew this was a graphics problem, but I can't seem to figure out how to fix it. However, after selecting "fail safe mode" as the gnome session, the lag seemed to go away, but acceleration for flash videos, and simple visualizations perform horribly.

Does anyone have any advice on how I can go about solving this problem? Or maybe, does anyone know a release of Ubuntu this particular graphics card will work with, while still having 3-d capabilities? I'm willing to downgrade, I just want to make it work, but I can't seem to figure out how. Any suggestions?

---

### Post by Stigmata13 on 2010-06-20
Just a little update. I attempted to install version 8.04... but it seems that went even worse than 9.10. I removed and disabled all compiz effects, but the system lagged bad, and froze up. Following some guides, I attempted to edit the xorg.conf file following some suggestions I found online, but all attempts would say something similar to "file does not exist" when trying to save from gedit. The file was empty to start with.

Anyway doesn't Ubuntu claim to work better on older hardware than windows? This is a joke, something like this should have been fixed ages ago. It's not like this is a particularly rare chipset, thousands of people probably still use it, and I have tried 3 different versions (8.04, 9.10, 10.04) and cannot get them to work in a decent manor.

---

### Post by shawnansasio on 2010-06-20
There are updated graphics drivers in 10.04 so if those dont work..... get your bro a new laptop! that graphics controller stinks so badly i can smell it from here! but seirously try a more lightweight distro

---

### Post by ronnielsen1 on 2010-06-20
> 2.6ghz Pentium 4
256-384 mb of ram? Not sure on the exact number here, but it's one of those.

The 2.6 Ghz is fine. The 256 - 384 mb is not. You will not be satisfied trying to run the big boys (Kde and Gnome) I have a 2.6 Ghz with 2G of ram and it works great. If you're wanting to run gnome, I'd put at least 512 M of memory, preferably more (The more - the faster) or use a lightweight window manager like lxde or fluxbox

---

### Post by shawnansasio on 2010-06-20
[http://lubuntu.net/](http://lubuntu.net/) <---- Try this

---

### Post by Stigmata13 on 2010-06-20
It's a desktop pc actually, an older one but he bought it with his own money, and he uses it for lightweight stuff (surfing the internet, listening to mp3's, etc) so he's pretty satisfied with what he's got. As for getting him a new pc... that's not exactly within my funds right now... lol...

Anyway my attempts at getting Ubuntu to work on his PC has been a nightmare.
I've searched for his chipset, but most of the solutions involve editing /etc/x11/xorg.conf, but I CANNOT no matter how hard I try.

Typing either "sudo gedit /etc/x11/xorg.conf" or "gksudo gedit /etc/x11/xorg.conf" both bring up a blank page, which is no surprise for me, since other users claim this chipset doesn't make an xorg.conf but it can use one. However, after I edit the file using another xorg.conf people have claimed work with the chipset, It tells me the file does not exist and does not allow me to save it.

I added the "nomodeset" line to the GRUB_CMDLINE_LINUX option and updated grub, but even with that, I've found it will not allow a resolution above 800x600. Going to System-Preferences Resolution, The display shows up as unknown, and the only resolutions available are 800x600 max, and the refresh rate is stuck at (61hz?) <-I don't know why 61?

It seems to me that the problem is the computer can't correctly detect the monitor and set the display resolution and refresh rates. All the solutions for this have either involved raising the dedicated graphics memory in BIOS (and option that is not available in this PC's BIOS, i've tried, and editing the xorg.conf file (which I can't do, since it just won't seem to let me for some reason.)

This is really giving me a headache...

Edit: Also, i know the RAM amount is low, but it ran fine. The only problem I can't seem to figure out is how to get the resolution/refresh rates working correctly, and no matter what I try, it just doesn't seem to want to work...

---

