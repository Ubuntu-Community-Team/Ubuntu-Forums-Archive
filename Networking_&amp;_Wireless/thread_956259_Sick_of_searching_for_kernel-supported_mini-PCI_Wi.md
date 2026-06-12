---
title: "Sick of searching for kernel-supported mini-PCI WiFi card"
date: 2008-10-23
forum: Networking &amp; Wireless
---

### Post by summersab on 2008-10-23
Alright, yell at me for not searching, but I have done my share. The community wiki that lists supported WiFi cards in Ubuntu frankly stinks, and it's a bunch of people saying what "sorta" works. There is nothing clear that I have ever found to say that a card works "out of the box - no catch!" Ralink is listed by FSF as working "out of the box" but then has a link to "download drivers here." One thing that I have loved about Linux is that for just about everything but a video card (and that is even simple now), I don't have to track down drivers. Kernel modules automatically handle that for me. In my mind, "out-of-the-box" means that upon pulling it out of the box and putting it in my computer (and maybe installing Ubuntu fresh), the device will work. Not "out-of-the-box-and-using-the-included-drivers-that-are-also-in-the-box." That's dumb. Plug-n-play.

So, what I want to know, finally, is just this: is there or is there not a reliable WiFi 802.11g mini-PCI card in existence that has built-in kernel support so I WON'T have to recompile, I WON'T have to build drivers from source, and all I have to do is put it in my laptop, install a fresh copy of Ubuntu, and the kernel will take care of the rest, allowing me to immediately get on the internet upon completion? Those are a lot of qualifiers. They are again:

- Reliable
- 802.11g
- Built-in kernel support
- No need to compile drivers
- No need to recompile kernel with modules
- Automatically set up, detected, and working after a fresh Ubuntu install

This is all I want in life (well, not quite . . . ), and I'm so sick of my Broadcom. Please, don't beat around the bush anymore. Just tell me exactly what I want to know already so I can stop running into dead ends on Google!

Thank you so much in advance. Sorry this is so long. Please don't let me down. I just want to buy something.

---

### Post by roelpeeters on 2008-10-23
What you might want to look into is a intel based wifi card. Myself I have good experiences with Intel 4965 AGN chipset / card. In addition, I found out that D-Link DWL-G630 is now supported out of the box with ubuntu 8.04.1. Here I am talking about my own experience: Up until 8.04 I had to download the ralink drivers, compile the source and install it. Then setup a configuration file. It would work, but it was a lot of work each time for the installation. Then two weeks ago I decided to reinstall my OS, and downloaded the latest ubuntu live cd (8.04.1). Guess what, recognized automatically and I only needed to use the network manager configure the network.

D-Link has several versions of their DWL-G630 pcmcia wifi card, make sure to get the one with the ralink chipset (rt61).

Roel

---

