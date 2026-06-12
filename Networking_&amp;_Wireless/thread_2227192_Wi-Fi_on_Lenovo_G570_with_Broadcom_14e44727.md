---
title: "Wi-Fi on Lenovo G570 with Broadcom 14e4:4727"
date: 2014-05-31
forum: Networking &amp; Wireless
---

### Post by ldewit on 2014-05-31
Hi guys

I'm trying to get the Wi-Fi on my Lenovo to work, but so far I'm not having much luck.

Thinking this is a driver problem, I tried some driver options before finding the "How to install a driver for the Broadcom series of PCI wireless cards" in this forum. Wish I'd found this sooner! Anyway I have Ubuntu 14.04LTS for which the sticky states:

> Special case #1: This device uses the driver combination bcma and brcmsmac. It shouldn’t be necessary to install anything at all. Required firmware is installed by default in the package linux-firmware. In a few cases, it is necessary to blacklist b43 and ssb



and so I did my best to undo what I've done so far. I've added the blacklisting as the sticky indicates. Still no Wi-Fi though.

I'm seeing "Wi-Fi is disabled by hardware switch" when I click on the networking icon top of the unity interface. I now think this was never a driver problem at all, but rather the system not recognising the physical switch is enabled. I looked at

```

root@PETRIELENOVO:~# rfkill list wifi
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

which seems to confirm this. To be clear, I can see the 'Hard blocked' value for phy0 change when I toggle the switch. The value for ideapad_wlan stays at 'no' though no matter the switch setting.

I'n out of ideas on how to proceed on this, and would greatly appreciate any help or suggestions anyone might have to offer. I include the output of wireless_script.

---

### Post by praseodym on 2014-05-31
Please check this thread:

[http://ubuntuforums.org/showthread.php?t=2111690&p=12490285#post12490285](http://ubuntuforums.org/showthread.php?t=2111690&p=12490285#post12490285)

---

### Post by ldewit on 2014-05-31
Hi praseodym

Thanks a lot for replying. I've tried the suggestions in that post:

1) Yes, WLAN is activated in BIOS
2) HW reset (Did this twice to be sure)
3) Reset BIOS to default
4) rfkill unblock all

Unfortunately, I've not seen a change in rfkill list output. Also , the Wi-Fi is working from Windows (the machine can dual boot) so I think the HW should be OK?

Anything else I could try?

Thanks

---

### Post by ldewit on 2014-05-31
Seeing as the sticky says the Wi-Fi should work with no additional drivers required, I booted my machine from a USB drive with the latest 14.04 image. This should prevent any driver issues in my own installation from playing a role. Looking at rfkill list from this 'clean' installation still shows the Wi-Fi as being disabled though, so no luck there.

I've been thinking of doing a clean installation as a last ditch attempt to get the Wi-Fi working, but this would seem to indicate that that would not have any chance of succeeding.

---

### Post by ldewit on 2014-05-31
Finally made some progress when I booted into Windows, and left the 'soft' Wi-Fi key on when shutting Windows down. I'm not sure how this affected the 'hard' setting in Ubuntu, but since the soft key in Windows brings up a Lenovo manager I suppose it's not impossible this sets something in hardware which then persists when rebooting.

I've done this before though, without success, and so something I did had to have played a role as well. Possibly praseodym's advice above?

Anway, I'll monitor and mark this as closed if the Wi-Fi performs without issues.

---

### Post by ldewit on 2014-06-05
I've confirmed it's now working. I posted before, but the short and the long is fiddling with drivers wasn't required, which would have worked perfectly out of box. The issue was the soft key, which appears to be not all that soft.

Booting to Windows, setting the wirless to enabled on both hard and soft keys and rebooting to Ubuntu solved the problem. The windows softkey triggers some Lenovo application, which seems to set something persistant in the hardware the Ubuntu driver does not reset when toggling the soft key from Ubuntu.

---

