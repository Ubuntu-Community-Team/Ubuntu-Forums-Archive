---
title: "Kernel upgrade didn't agree with my wireless"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by frutavana on 2009-04-07
This is my first post ever here. I'll first explain how I adopted Ubuntu (between square brackets) and then move on the problem I have, in case you don't feel like reading a couple of paragraphs of rambling.

[Two days ago, I decided to reinstall the old Win Xp on my laptop, as it was growing mortally slow. Anyway, as my laptop provider (Toshiba) did not ship a CD with the thing, I had to reinstall from that I386 folder. All went relatively smoothly, but I couldn't help noticing, upon starting the freshly-reinstalled OS for the first time, that my computer had been rendered useless by lack of drivers (no sound, no wireless and not ethernet card). Of course, I couldn't connect to the Internet to look for the driver. Bordering on desperation, I remembered I had an Intrepid Ibex CD lying around somewhere, with which I had been toying a while back.

Anyway, without much hope, I booted the CD and, before trying my hand at partitioning (I couldn't remember the recommended sizes and stuff, neither could I look them up here), I decided to try the LiveCD thing. To my utter delight, my computer was completely functional again, and I didn't have to install a thing! I promptly connected to the Internet, downloaded the drivers XP was missing, went back to XP and fixed everything up.

Now, until then, I hadn't been completely sure about using a dual boot XP/Ubuntu setup, because, even though I totally abhor Microsoft products, I absolutely need MS Office for work; and, on the other hand, I really couldn't think of any reason, other than ideological/philosophical ones (not that those are not valid), to install Ubuntu.

Anyway, now Ubuntu had proven itself practical. It excelled where XP failed miserably, and brought XP back to life to boot. So, out of sheer gratitude, I decided to install a small Ubuntu partition. And I'm loving it so far, except for one tiny little problem I'll now get into.]

The version I installed is 8.10, and comes with the 2.6.27-7 kernel. Everything worked smoothly after the installation: sound, video, wireless, you name it. However, after my first interaction with the Update Manager (about 270 updates, if I recall correctly), my wireless card (the infamous IPW2200) was no longer recognized (it started to come up as DISABLED in lshw). I know this is related to the upgrade to 2.6.27-11, according to what I've read in the forums. However, I couldn't manage to get it back up, mainly because I'm an utter newbie and can barely crawl through the terminal. I tried with ndiswrapper and the Windows driver, but only managed to lock the whole system up on startup. I tried installing that ipw2200 driver for Linux (ipw2200.sourceforge.net), but it's way above my league in computing terms.

Finally, I chose to reinstall the whole thing, as loading up the old kernel (2.6.27-7) on startup didn't seem to do the trick.

I'm now writing from Ubuntu, using my wireless connection, but with the 2.6.27-7 kernel. The update manager has come up already to remind me to upgrade, but I know that if I do that, I'll lose my wireless. SO:

1) What should I leave out of the upgrade in order to update everything but whatever it is that messes up my wireless card?
2) Is there any way of knowing when this bug (as I understand it is) will be fixed, so that I can update the kernel accordingly?

Thanks a lot, and excuse my verbosity.

---

### Post by skymera on 2009-04-07
Wow that was a long post.

Hmm, wireless issues are a bugger  i must say.
If i were you, I'd use the 2.6.27-7 kernel if it works, keep it installed :)

There might be a fix on newer patches of the kernel or even on the 2.6.28 kernel used in Ubuntu 9.04 :)

---

### Post by frutavana on 2009-04-07
> **skymera said:**
> Wow that was a long post.

Hmm, wireless issues are a bugger  i must say.
If i were you, I'd use the 2.6.27-7 kernel if it works, keep it installed :)

There might be a fix on newer patches of the kernel or even on the 2.6.28 kernel used in Ubuntu 9.04 :)

Thanks for the speedy reply and sorry for the length of the original post! I will keep the 2.6.27-7 kernel, as it works tip-top. Now, supposing I wanted to update everything BUT the kernel, would it be enough to uncheck all the updates labelled linux-image, linux-headers, etc.? I reckon those are the ones that will ultimately make my wireless go bonkers, but I don't know if there's another package capable of messing it up.

I have been browsing the manuals for a command to produce a list of the packages available in the update manager (there's 286 of them now) that I could post it here and see if anyone could point out the ones potentially dangerous for my wireless card. Alas, I couldn't find any such command.

---

### Post by ugriffin on 2009-04-07
This problem may be because of two reasons:

1) Support for your card was dropped in the new kernel (unlikely)
2) The kernel interface your driver worked with is incompatible with the new kernel version.

Number two happens to NVIDIA users who use the driver downloaded at NVIDIA.com (I am unsure about the Adept drivers.) Each time there is a kernel update, you have to compile a new kernel interface for your driver. I think there might be something there. Find out if your drivers use a kernel interface. If such, find out how to compile a new one for your current kernel version.

Hope that works.

---

### Post by frutavana on 2009-04-08
Well, first of all, thanks to Ugriffin for his/her answer. Unfortunately, I couldn't even start to look into it, for things have taken a turn for the worse:

I didn't install or update A THING, just the MS truetype fonts, and after restarting for them to load up, my network manager was **gone**, at least from the taskbar, so I couldn't use my wireless. I plugged the network cable in and the network manager popped up. I then upgraded the network manager frontend, daemon and libraries off Synaptics, and restarted again.

Now the Network Manager is back on the taskbar, but both my wired connection and my wireless connection show up as "UNMANAGED", so I can't connect either way. I'm writing from Win XP, so you'll have to bear with me to log back into Ubuntu and get back here in case you need me to check anything.

Thanks in advance.

EDIT: Well, things seem to be back to normal now, I edited the etc/NetworkManager/nm-system-settings.conf file to read managed=true, re-ran pppoeconf (not sure why I had to do that), and everything seems to be working now. I'll see what happens when I restart.

---

