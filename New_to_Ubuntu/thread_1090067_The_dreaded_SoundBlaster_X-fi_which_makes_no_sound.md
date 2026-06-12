---
title: "The dreaded SoundBlaster X-fi which makes no sound"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by tracerbullet on 2009-03-07
Hey Absolute Beginner Talk!

Due to recent... happenings, I am preparing my desktop computer for a complete switch to Ubuntu. At this time I'm almost ready, I just need to iron out the last little kinks and quirks in my plan.

First of all, and this is the important question:

I can't get my Crative SoundBlaster X-fi XtremeMusic sound card to work in Ubuntu.

I have tried a couple of times already. The first time was a few years ago, when I did a full install of (I think it was) Hardy Heron (or possibly the one before that). During this period I remember that I could not get the normal alsa installation to work with it, and I believe I tried building a few drivers from source as well, including oss.

Then, earlier today I booted a Hardy Heron live CD and it would not give me any sound.

lspc -v detects the sound card, but the little volume control button on the top menu does not.

My question then remains, what do I do to get this naughty sound card to play nice with Ubuntu?

I have a couple of live CDs at hand, one has Hardy Heron (7.?) and the other has Intrepid Ibex (8.10).

Another option is to go ahead and completely [S]melt[/S] wipe my hard drive and install Ubuntu before attacking the problem.

But this is not the most attractive option since it means I will have to do it all over again in a week if I can't find a solution to this problem.


My second question is quite banal really, I am just wondering if 8.10 (which I already have a copy of) is the right choice, or if I should use another version. I hear 8.04 is the current "most" stable release?


Post script:

There is always the option of buying a shiny new sound card. But the computer in question is getting fairly old (built Oct 2005) that it might be a whole other challenge in itself to find compatible parts in this day and age?

A big preemptive thanks to everyone who wishes to offer some insight! I know how these things can be a headache both for the one sitting in the pig sty and the people trying to pull him out. :D

---

### Post by tracerbullet on 2009-03-08
Ok some more details:

Computer is booted with live CD v8.10.

I go into System > Preferences > Sound.

I set all four drop-down menus to ALSA.

Clicking "Test" now produces this error message:

> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresampe ! gconfaudiosink: Could not get/set settings from/on resource.

And the last of the four produces this message:

> gconfaudiosrc ! audioconvert ! audioresample ! fconfaudiosink profile=chat: Could not open audio device for playback.

A similar message is produced when I set all options to OSS.

> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresampe ! gconfaudiosink: Could not open audio device for playback.

PulseAudio:

> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresampe ! gconfaudiosink: Failed to connect stream: Invalid argument.

Additionally, after pressing "close" on the PulseAudio error message, the entire window locks up and I am asked to force quit it.

Edit: Oh and, relevant output from lspci -v:

> 05:07.0
Multimedia audio controller: Creative Labs SB X-Fi
Subsystem: Creative Labs Device 0021
Flags: bus master, medium devsel, latency 32, IRQ 3
I/O ports at a000 [size=32]
Memory at d3000000 (64-bit, non-prefetchable) [size=2M]
Memory at d3200000 (64-bit, non-prefetchable) [size=2M]
Capabilities: <access denied>

---

### Post by Trebaruna on 2009-03-08
Support for X-Fi is quite simply awful. For years, Creative didn't release any documentation or anything, and after quite a long time finally came up with a "beta" driver, which was horrid.
They've finally given up and released information, so now support is being worked on. I do not believe it is far enough along yet, though.

The good news is, if you purchase any PCI soundcard it ought to work in your machine. The guys and girls at ALSA have a nice list of supported cards: [http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main)

---

### Post by tracerbullet on 2009-03-08
Wow, that is one extensive list. :o :D

I'm a bit intimidated to tell the truth... what exactly is the difference between all those cards?

(I'm just going to go over the list and see if anything jumps out at me.)

---

### Post by Nepherte on 2009-03-08
Here's guide to get it to work on Intrepid: [http://ubuntuforums.org/showthread.php?t=870001](http://ubuntuforums.org/showthread.php?t=870001)

---

### Post by tracerbullet on 2009-03-08
> **Nepherte said:**
> Here's guide to get it to work on Intrepid: [http://ubuntuforums.org/showthread.php?t=870001](http://ubuntuforums.org/showthread.php?t=870001)
Thanks, I think I'll try this out. Obviously the guide assumes I'm on a full install, not a live CD, so I'll be doing a full install and try to get this working. =)

Installing Ubuntu 8.10...

Well that took all of 20 minutes. Not bad! Now to test out that guide.

Uh oh! Pizza is ready! *runs off to the kitchen*

---

### Post by tracerbullet on 2009-03-08
Success!! :KS :KS :KS

With the help of that excellent guide I have finally caoxed my SoundBlaster into working with Ubuntu!

Thanks everyone! :D

---

