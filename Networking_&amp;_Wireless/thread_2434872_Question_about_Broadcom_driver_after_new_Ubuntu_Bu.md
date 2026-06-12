---
title: "Question about Broadcom driver after new Ubuntu Budgie install"
date: 2020-01-12
forum: Networking &amp; Wireless
---

### Post by davepool on 2020-01-12
Allow me to introduce myself as perhaps your newest "New to Ubuntu" user...who also happens to still be rather new to Linux. Within the past few months I've had exposure to MX Linux and Linux Mint, primarily. And it's the latter I keep on my primary laptop (the one I expect to remain functional despite my floundering!). But in order to give me a platform to continue to explore Linux, I recently bought a used Lenovo Thinkpad X131e (with 8 gig of RAM) and that's the one I intend to use as playground and laboratory for learning about Linux.

The second distro that I installed on the Thinkpad is Ubuntu Budgie. The _*second*_ one? Yes, the first one was Deepin. Geopolitical issues aside (and the EULA, the data collecting, etc) it was its insistence that a password I had just used to login with was invalid (repeatedly) when I wanted to install another package that made me decide to move on to something else...which became Ubuntu Budgie.

But bear with me a bit longer, please, about that Deepin install.  Per usual, I had used Etcher to flash the .iso onto the USB and after validating the flash, it was pronounced Successful. But after Deepin was installed, once I started to add additional packages, I noticed that the downloads were taking forever. My download of FreeOffice, which normally takes 2-3 minutes, took 56 minutes (to cite but one example)!  Note that this was not a case of the wireless adapter not functioning at all (Google has produced many solutions for that situation). Rather, this was just painfully slow performance.

But I put that behind me when I installed Ubuntu Budgie (again using Etcher for the flash and, again, all being Successful). Once installed, I started the same process of installing additional packages and this time they all went smoothly.  Was it as fast as it could have been (potentially)? I'm not sure, since this Thinkpad is new to me.  

Nevertheless, the difference in wifi performance between the two distros on the same device is pretty startling.  Could the Deepin installer actually have been corrupted despite Etcher's assurance otherwise? Could it have been complete and uncompromised but still possibly installed (via its developers) a less than optimal wifi driver?

And now my probably predictable question is this: is the Ubuntu Budgie installation giving me the most wifi performance it can? I don't want to be ungrateful here...I mean, I have wifi that's operating. So I'm not in a bind. But has it all installed correctly for max performance? When I check via Software & Updates, this is what I see reported under the Drivers tab:

[B]Broadcom Limited BCM4313 802.11bgn Wireless Network Adapter
This device is using an alternative driver
(X) Using Broadcom 802.11 Linux STA wireless driver source from bcmwl-kernel-source (proprietary)
(  ) Do not use the device[/B]

Does that appear as it should?  I also note that there is some mouse-type below that information:

[B]1 proprietary driver in use

A proprietary driver has private code that Ubuntu developers can't improve or review. Security and other updates are dependent on the driver vendor.
[/B]
Is that, too, the best news I could receive? To this newbie, it sounds worrisome. Can Broadcom be depended on to update the driver?  I'm already aware that there are some updates that cannot be done via wifi and require a hardwire ethernet connection....so I'm prepared for that, if it's necessary.

Dave

---

### Post by CelticWarrior on 2020-01-12
Yes, the driver is correct, apparently. You can confirm here: [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by jeremy31 on 2020-01-12
Moved to Networking and Wireless
Some of those work with either the open source or the proprietary module, some don't work well at all
Try disabling wifi power management, see if it  is better
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Reboot

---

### Post by davepool on 2020-01-12
Thanks, @jeremy31, for that suggestion. I might just try that...however, what's the "un-do" command of that, just in case? ;)

---

### Post by chili555 on 2020-01-12
> 
Broadcom Limited BCM4313 802.11bgn Wireless Network Adapter
This device is using an alternative driver
(X) Using **Broadcom 802.11 Linux STA wireless driver** source from bcmwl-kernel-source (proprietary)
( ) Do not use the device

Does that appear as it should? 

No. Please double-check: [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by davepool on 2020-01-12
@CelticWarrior thanks for the prompt response. I took a look at that thread and immediately experienced the condition known as MEGO (My Eyes Glazed Over) :-]

---

### Post by jeremy31 on 2020-01-12
davepool, post results from terminal for ```
lspci -nnk | grep -iA3 net; iwconfig
```

The way to reverse that other command is ```
sudo sed -i 's/wifi.powersave = 2/wifi.powersave = 3/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

---

### Post by davepool on 2020-01-12
@Chili555 Okay, upon second (and careful) read, those steps seem pretty clear. I'll let you know how it goes. Thanks!

---

### Post by davepool on 2020-01-13
> **chili555 said:**
> No. Please double-check: [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

@Chili555 this didn't go well....or it seems so.

First, I made sure I had the updates via sudo apt-get update

Then I entered sudo apt-get purge bcmwl-kernel-source (fearing I was burning a bridge behind me)

Okay, the lspct -nn -d 14e4: command produced [14e4:4727] (rev 01)

The bad news there is that this choice (at least the "rev 01" version) does not even appear on the list.  That said, obviously, [14e4:4727] *does* appear....at the very bottom.

Working from that, the Special Case 1 instructions (because I'm running 18.04) for echo resulted in "permission denied" statements (and that was after sudo -l told me I could do anything).

Thinking at that point that I should try maybe the Special Case 3 instructions, entering uname -r produced 5.0.0-37-generic and, if I understood that (being 3.8 and later) entering brcmsmac produced "Command not found".  Same results for entering bcmwl-kernel-source

The good news here is that whatever I've been left with after all that seems to work (I have not restarted the device) and my usual go-to test of playing a YouTube video shows it will play without breakup or stutter.

So...there were comments yesterday that what I had was not correct and I needed to go through the process you all provided.  With that not working, should I just leave well enough alone? Should I go back to the Budgie Welcome tool and the Getting Started/Drivers tab and re-install whatever that brings?

---

### Post by davepool on 2020-01-13
> **jeremy31 said:**
> Moved to Networking and Wireless
Some of those work with either the open source or the proprietary module, some don't work well at all
Try disabling wifi power management, see if it  is better
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Reboot

@jeremy31 So I tried that (knowing I had your "undo" string at the ready!) and I want to confirm one thing: after entering my password, that string did not produce any result in the terminal. Was that to be expected? Then...what indication(s) will there be that this change to wifi power management has taken effect?

---

### Post by jeremy31 on 2020-01-13
Your connection speed may improve as allowing Network Manager to enable wifi power management causes issues for many wifi devices

---

### Post by chili555 on 2020-01-13
> So...there were comments yesterday that what I had was not correct and I needed to go through the process you all provided. With that not working, should I just leave well enough alone? If everything is working as expected, why do anything at all?

It might be interesting to see what exact driver is in use, after all this. Please run and post:```
lsmod | grep -e brcm -e wl
```

---

### Post by davepool on 2020-01-13
> **jeremy31 said:**
> Your connection speed may improve as allowing Network Manager to enable wifi power management causes issues for many wifi devices

Gotcha. Thanks!

---

### Post by davepool on 2020-01-13
> **chili555 said:**
> If everything is working as expected, why do anything at all?

It might be interesting to see what exact driver is in use, after all this. Please run and post:```
lsmod | grep -e brcm -e wl
```

brcmsmac              569344  0
brcmutil               16384  1 brcmsmac
cordic                 16384  2 b43,brcmsmac
mac80211              819200  2 b43,brcmsmac
cfg80211              679936  3 b43,mac80211,brcmsmac
bcma                   61440  3 b43,brcmsmac

And the answer to your question is that in my initial post, after relating what had happened to my wireless speed during the brief flirtation with Deepin, I asked if there was any way to determine that whatever Ubuntu Budgie had installed (either in the original .iso or later via post-installation driver updates) was giving me the maximum I could achieve.

Further, when I posted what I saw reported in the Drivers tab of Software & Updates and asked "Does that appear as it should?" it was you who replied "No. Please double-check: https://ubuntuforums.org/showthread.php?t=2214110" 

So that's why I went through the whole process that you pointed me to. And I definitely appreciate the reply even if you now think the process wasn't necessary.

Anyway...what do you see above in the info you requested I post as the results of "lsmod | grep -e brcm -e wl"?

---

### Post by chili555 on 2020-01-13
> **davepool said:**
> brcmsmac              569344  0
brcmutil               16384  1 brcmsmac
cordic                 16384  2 b43,brcmsmac
mac80211              819200  2 b43,brcmsmac
cfg80211              679936  3 b43,mac80211,brcmsmac
bcma                   61440  3 b43,brcmsmac

And the answer to your question is that in my initial post, after relating what had happened to my wireless speed during the brief flirtation with Deepin, I asked if there was any way to determine that whatever Ubuntu Budgie had installed (either in the original .iso or later via post-installation driver updates) was giving me the maximum I could achieve.

Further, when I posted what I saw reported in the Drivers tab of Software & Updates and asked "Does that appear as it should?" it was you who replied "No. Please double-check: https://ubuntuforums.org/showthread.php?t=2214110" 

So that's why I went through the whole process that you pointed me to. And I definitely appreciate the reply even if you now think the process wasn't necessary.

Anyway...what do you see above in the info you requested I post as the results of "lsmod | grep -e brcm -e wl"?I definately think you needed to go through the process above; to research and find that the incorrect driver suite was installed, namely bcmwl-kernel-source; to remove it and allow the correct driver, namely brcmsmac, to take over and do a better job. That is, faster speeds and no stuttering.

Now that things are working correctly, I see no need whatever to, "...go back to the Budgie Welcome tool and the Getting Started/Drivers tab and re-install whatever that brings." That tool will happily reinstall the *_wrong_* driver again. Please do not do so.

---

### Post by davepool on 2020-01-13
> **chili555 said:**
> I definately think you needed to go through the process above; to research and find that the incorrect driver suite was installed, namely bcmwl-kernel-source; to remove it and allow the correct driver, namely brcmsmac, to take over and do a better job. That is, faster speeds and no stuttering.

Now that things are working correctly, I see no need whatever to, "...go back to the Budgie Welcome tool and the Getting Started/Drivers tab and re-install whatever that brings." That tool will happily reinstall the *_wrong_* driver again. Please do not do so.

Wow! Based on the responses I was getting from the terminal in going through that (such as "not found" and "not permitted") I really don't know how the proper steps came to pass!  But I'm certainly not complaining!  Thanks again!

No, I did not go back to the post-install tool...I was just spit-balling there. But is my computer's incorrect response to that tool....or the tool's incorrect action with my computer...anything that a developer somewhere (Solus? Ubuntu?) would benefit from knowing about?

---

### Post by chili555 on 2020-01-13
> 
.anything that a developer somewhere (Solus? Ubuntu?) would benefit from knowing about?
I'll work on it.

---

### Post by davepool on 2020-01-14
> **chili555 said:**
> I'll work on it.

Sounds like you might be discussing this with yourself, then? :) 

Sorry...bear with me. Being a new member, I am only just starting to learn who's who and does what. Thanks!

---

### Post by chili555 on 2020-01-14
> **davepool said:**
> Sounds like you might be discussing this with yourself, then? :) 

Sorry...bear with me. Being a new member, I am only just starting to learn who's who and does what. Thanks!Not really. I am not a developer. I am a rusty old volunteer that has managed, in my 18 years running one version or another of Linux, to learn just a bit about wireless networking. 

While I am honored to be an Ubuntu Member, that, in reality, means that you've been significantly helpful to other users over a significant time and that you applied for it in writing. That doesn't at all mean that I know the first thing about source code.

In fact, I doubt that there is a single developer here on this forum. As far as I know, we are all volunteers with no professional connection to Ubuntu or Canonical.

---

### Post by davepool on 2020-01-14
> **chili555 said:**
> Not really. I am not a developer. I am a rusty old volunteer that has managed, in my 18 years running one version or another of Linux, to learn just a bit about wireless networking. 

While I am honored to be an Ubuntu Member, that, in reality, means that you've been significantly helpful to other users over a significant time and that you applied for it in writing. That doesn't at all mean that I know the first thing about source code.

In fact, I doubt that there is a single developer here on this forum. As far as I know, we are all volunteers with no professional connection to Ubuntu or Canonical.

Interesting stuff. Thanks for the insights, both personal and general. I'm going to try not to badger anyone needlessly as I continue to learn about Linux.

I guess I *am* a bit puzzled, then, as to how/why the distro .iso for Ubuntu Budgie would install an incorrect wireless driver for my Thinkpad (though, come to think of it, I do not know if that happened in the original installation or in the post-install "First Things" update of the drivers....or, for that matter, if Deepin put the wrong driver in...or if the driver was incorrect to begin with [device bought used] and then neither Deepin nor Ubuntu detected it and corrected it).

---

### Post by davepool on 2020-01-15
Hey, @chili555, FWIW (I got a case of the upgrade itchies and, hey, y'know, foolin' around with installs and partitions and such was why I bought the used ThinkPad...) I installed Ubuntu Budgie 19.10 last night and when I got to the page where it asked if I wanted to install both updates and 3rd-party software (like drivers!) I specifically *didn't* tick the 3rd-party box. And when the install was done, I right-clicked on the wi-fi applet in the panel to select Connection Information and there it shows brcmsmac as the driver!  So...no installation of bcmwl-kernel-source along the way somewhere somehow. At the same time, however, I also did not go to the Drivers section of Getting Started and run that...because you told me that tool would happily install the wrong driver.

And, yeah, I then manually enabled access to 3rd-party software when I installed Vivaldi and when I enabled backports repository...but that's confining that permission to specific cases, not giving blanket permission

In the world of auto racing (where I'm a fan, not a participant) a well-known bit of wisdom in setting up a car for a particular track is "Never change more than one thing at a time" because otherwise you'll never know which change brought what result.  And, so....I violated that, because I a) opted out of 3rd-party software and b) also didn't run the driver update. But at least I came away with the correct driver installed.

---

### Post by chili555 on 2020-01-15
> select Connection Information and there it shows brcmsmac as the driver! Correct.> 
 "Never change more than one thing at a time" 
Also correct.

I assume that your wireless is working properly now. I wouldn't change a thing.

---

### Post by davepool on 2020-01-15
> **chili555 said:**
> Correct.Also correct.

I assume that your wireless is working properly now. I wouldn't change a thing.

It seems to be fine. The DL speeds I measured last night, though erratic (thanks, TDS), were not all that much slower than what I measured through my PC desktop via Ookla.

---

