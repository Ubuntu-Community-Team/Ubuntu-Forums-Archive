---
title: "Cannot select proprietary drivers (instantly reverts to non-proprietary / no drivers)"
date: 2015-01-27
forum: Networking &amp; Wireless
---

### Post by adam1234 on 2015-01-27
Hi all -

I am brand new to this forum, and relatively new to Ubuntu. I just installed UbuntuGnome 14.04.1 on my Dell XPS 8700 desktop computer, and I cannot get the proprietary driver for my wireless card to work (my card is: Broadcom Corporation BCM43142 802.11b/g/n rev 01). When I go to: "Software & Updates > Additional Drivers", the wireless card is shown. The GUI shows the following:

*****************************************************************
Broadcom Corporation: Wireless 1704 802.11n + BT 4.0I
        o Using Broadcom 802.11 Linux STA wireless driver source from bcmwl-kernel-source (proprietary)
        x Do not use this device
*****************************************************************

where "o" is an unmarked/unselected option, and "x" is a marked/selected option. When I click on "Using Broadcom..." and press "Apply Changes", it instantly reverts back to "Do not use this device" - meaning that I cannot use wireless at all. This is very frustrating, especially since I got the wireless to work when using the live-CD (before installation) using EXACTLY this technique.

**Note: For some reason, Dell refers to my wireless card as 1704, while Broadcom  usually refers to it as 43142 (I have no clue why they use different  names). But the disparity in the numbers is not the cause of my problem  (especially given that everything worked just fine on the live-CD).**

On a related (but less important) topic, this exact same phenomenon prevents me from trying out the proprietary NVIDIA 331.113 graphics driver (instead of the "X.Org X server -- Nouveau display driver"). All I wanted to do was check if using this X.Org driver had an impact on CPU usage compared with the NVIDIA driver. However, when I select the NVIDIA driver and click "Apply Changes", it instantly reverts back to the X.Org driver. The NVIDIA 331 driver is what I used with a different distro on this same computer. (my graphics card: NVIDIA GeForce GT 720)

Does anyone know how I should go about fixing this problem? And does anyone know why UbuntuGnome installation (but not the live-CD) would prevent me from using proprietary drivers? Thanks in advance!

---

### Post by kc1di on 2015-01-27
Hi adam1234 and welcome to Ubuntu forums,

you can do the same thing with the terminal. 

But first lets look at the following command in the terminal :
```
rfkill list all
```
and post the results here.
if the return you get has no hardware block proceed with the following command and install the driver that way:

```
sudo apt-get install bcmwl-kernel-source
```

once install is finished either reboot or enter this command and wait a minute or two and try the wireless again.
```
modprobe wl
```

good luck

P.S. the dell # is their own part # for that card.  Linux will recognize it as the Broadcom #.

you can also install the Nvidia driver the same way in the terminal : ```
sudo apt-get install nividia-331 
```

---

