---
title: "Disabling certain wi-fi channels"
date: 2015-06-16
forum: Networking &amp; Wireless
---

### Post by PenguinLust on 2015-06-16
I want to setup multiple wireless routers to use the same access point. Unfortunately, some of the routers I have give me trouble w/a couple of Ubuntu installations. These problems would be acceptable if I could just prevent the Ubuntu client systems from using the channels that the problem routers use. But I don't know how to do that.

---

### Post by tgalati4 on 2015-06-17
I don't understand your setup.  Generally, each wireless router becomes a different Access Point (AP), unless you have them set up as extenders or bridges.

It's not easy to force an endpoint to use a specific frequency, because that is at a lower level than what the software controls.  You can view the current channel using *iwlist*:

> tgalati4@Mint17 ~ $ iwlist wlan0 channel
wlan0     11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency:2.427 GHz (Channel 4)


You connect to unique SSID's that are broadcast by each AP.  The channel is either hard-coded or dynamic (auto-channel) by the AP, so if you have a unique SSID for the router that you want your Ubuntu machine to connect to, then use that.  

Why are your Ubuntu client systems having problems with some routers?

---

### Post by PenguinLust on 2015-06-17
> **tgalati4 said:**
> I don't understand your setup.  Generally, each wireless router becomes a different Access Point (AP), unless you have them set up as extenders or bridges.
Right, I guess what I meant was multiple APs but a unique SSID.

> Why are your Ubuntu client systems having problems with some routers?
I imagine quirks in some routers that Linux drivers are not robust to. W/one router I went as far as is humanly possible, but my desktop wouldn't work until I changed routers. Another router (w/open source firmware) doesn't seem to like my LUbuntu system. I lost patience w/that one quickly.

---

