---
title: "madwifi-ng ioctl calls broken with 2.6.20 kernel"
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by B-Con on 2007-05-30
I was reading the madwifi-ng README and noted that ioctl calls only work in kernels up to the 2.6.15 kernel:
[quote=Madwifi Readme]MadWifi supports the use of the Wireless Extensions ioctl's equal to or
greater than WE18 (linux 2.6.15).[/quote]
Obviously I need ioctl in order to enter monitor mode with my wireless card that uses madwifi, with this kernel version (since I upgraded to Feisty) I've been unable to enter monitor mode with my card and always get some sort of error.What's up with this, do I have to downgrade my kernel to get monitor mode back? Is there some hack around to it?

---

### Post by spd106 on 2007-05-30
I'm no expert in this, but from what I have seen and read madwifi-ng has partial support for WE, i.e. not all controls are working. 

If you want to use your Atheros card for anything other than the normal client/infrastructure/managed mode then I strongly urge you to read the docs on the madwifi.org site. 

It's not trivial to manage this driver, though installing the madwifi-tools package from the universe repo will make it easier. Madwifi-ng is quite different to madwifi-old in many respects.

---

### Post by tturrisi on 2007-05-30
Not sure how up to date your info is.  I'm running madwifi latest version on Etch w/ kernel 2.6.18.4 and all works well, including monitor mode and even packet injection with airmon-ng.

---

### Post by spd106 on 2007-05-30
So how do switch between managed and monitor mode without using wlanconfig? As far as I know it's not bundled with Feisty. I suppose you can reload ath_pci and force a monitor mode VAP. But that's not a WE control.

Is there an iwpriv or iwlist command to do this?

I must admit that I've not used Feisty much yet. I'm genuinely interested to know how you do this as it would save me a lot of trouble.

---

### Post by tturrisi on 2007-05-30
[http://packages.ubuntu.com/feisty/net/madwifi-tools](http://packages.ubuntu.com/feisty/net/madwifi-tools)

---

### Post by B-Con on 2007-06-04
Still won't work.

```
$ wlanconfig ath1 create wlandev ath0 wlanmode monitor
wlanconfig: ioctl: Operation not supported
```

ioctl just does not seem to work with madwifi right now... What did you guys have to do to get it working, anything?

---

### Post by tturrisi on 2007-06-04
Your command is incorrect, should be:
wlanconfig ath0 create wlandev wifi0 wlanmode monitor
or
wlanconfig ath create wlandev wifi0 wlanmode monitor
This is because the actual wifi device is wifi0 and athX devices are in actuality virtual devices, thus the "parent" wifi0 is what is needed in the command for wlanconfig.  The parent wifi0 is what is used to setup the virtual devices.

[http://madwifi.org/wiki/UserDocs/MonitorModeInterface](http://madwifi.org/wiki/UserDocs/MonitorModeInterface)
also see useful madwifi docs liste here:
[http://madwifi.org/wiki/UserDocs](http://madwifi.org/wiki/UserDocs)

fyi, when using kismet, kismet will put the athX device into monitor mode for you, and when using aircrack-ng, you put the athX device into monitor mode using airemon-ng.

---

### Post by fuzzyworbles on 2007-07-12
I've got the same exact problem and I'm pretty sure that I've tried everything.

First i took the advice from some boards not to install madwifi on feisty fawn (2.6.20-16) and just to apt-get the madwifi-tools and restricted-drivers packages. When i tried to make ath0 out of wifi0 using wlanconfig i got the following error &#8220;wlanconfig: ioctl: Operation not supported.&#8221; So then i decided to install it manually with the latest build (madwifi-ng-r2576-20070712), and removing the supposed previous modules. same result. Then, under the recommendation from [http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu) i stopped the old ath_hal module in linux-restricted-modules, restarted, but with no avail. Then i followed the instructions on [http://wiki.debian.org/MacBook#head-e4a1f2cde8ad66bc01c97bfdadc85996ad80f688](http://wiki.debian.org/MacBook#head-e4a1f2cde8ad66bc01c97bfdadc85996ad80f688), but i got the same problem, &#8220;ioctl: Operation not supported.&#8221; The most recent thing i've  tried is finally, and rather blindly, what i hoped to be a magical cure-all script at [http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html). And as a note, everything compiles without a hitch.
	I read somewhere else where somebody reseeded the card for a similar problem, but there's got to be a more reasonable solution &#8211; i'm not excited about opening up my laptop. it's an ibm t30 with an atheros (cisco pci) card and madwifi works under windows.

does anybody have any other ideas before i install edgy or something sooner? appreciate it. I suspect that it's actually using the madwifi driver either provided by ubuntu or via my various install attempts. After all, i'm using it right now &#8211; it's just that I can't make athX!!!

somebody holler back.

---

