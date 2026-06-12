---
title: "Is Nvidia's DualView possible with Ubuntu?"
date: 2011-01-25
forum: New to Ubuntu
---

### Post by moj on 2011-01-25
Hi

Just installed 10.10 64-bit, my first Linux install. Everything seems fine, except that after installing the Nvidia driver for my 9600GT card, there is no option in X Server, to run DualView, like there is in the Nvidia Control Panel for Windows. Am I missing something or is there no DualView for Linux? I've Googled and Googled to no avail :(

Basically, what I'm after, is to have each monitor configured separately (as with the "seperate X Screen" configuration), with the ability to drag windows from one monitor to the other. TwinView does not offer this and I'm not after one big desktop, spread over both monitors.

DualView was perfect for my needs; not sure I want to lose it TBH :/

Without the Nvidia driver installed, I was able to set up my monitors how I want using the system>preferences>monitors tool, but this is disabled with the Nvidia driver in play and disabling the Nvidia driver is not an option for me, since without it, my GPU fan becomes ridiculously loud. 

Anyone have any ideas please? I'd hate to have to ditch Ubuntu already :(

---

### Post by robsoles on 2011-01-25
I am running two monitors using the "current version" of NVIDIA accelerated driver (version current) and I have two screens configured.

Please review my screenshot and post back if your "NVIDIA X Server Settings" window looks that different for yours or how to set dual screens using it still eludes you :)

---

### Post by moj on 2011-01-25
> **robsoles said:**
> I am running two monitors using the "current version" of NVIDIA accelerated driver (version current) and I have two screens configured.

Please review my screenshot and post back if your "NVIDIA X Server Settings" window looks that different for yours or how to set dual screens using it still eludes you :)

That's exactly the same driver version and exactly how my X Server window looks, I just cannot figure out how to enable dragging windows from one monitor to the other. All I can get, are separate desktops on each monitor, without the ability to drag windows over from one to another like with Nvidia's DualView setting on XP.

---

### Post by themusicalduck on 2011-01-25
If you highlight the screen and click configure, can't you select DualView or TwinView or whichever it is from there?

I can't check my configuration now as I'm not on my home PC, but I have my Nvidia card setup using that option and it works exactly how it seems you want yours to work.

---

### Post by robsoles on 2011-01-25
Sorry, I missed where you implied you had seen the mode I am using, I thought you hadn't even clicked the 'configure' button :embarrased:

I just put up with the fact that they are seperate. If you want to drag windows back and forth between monitors then TwinView is the way. I don't want to upset you or anything but if you could drag windows from one monitor using this "DualView in MS Windows", particularly if you could see the window in each monitor for a moment as you dragged it, then that is exactly the same as TwinView - though MS Windows is less revealing of the true nature of what they (and you) are doing.

If you configure TwinView as a big desktop then you want matching monitors (I have one setup of this at work :)) and a window won't "maximise" over the entire space, behaviour is actually pretty close to MS Windows behaviour (though the memories are fading ;)) - windows will maximise to the monitor they occupy the most when you click the button. Screenshots will be the full width of the monitors combined.

Panels don't appear in the other monitor but it should be possible to make some if you want them.

Sorry if you can't stand it.

---

