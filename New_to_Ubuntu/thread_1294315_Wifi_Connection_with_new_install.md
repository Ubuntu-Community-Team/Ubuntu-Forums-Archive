---
title: "Wifi Connection with new install"
date: 2009-10-18
forum: New to Ubuntu
---

### Post by WebToad on 2009-10-18
Howdy all,

I have been using 8.04 on one of my desktops for a while.  The install was very easy, and this has a wired net connection.  Though I have been using the OS, I have not yet messed with any real custom builds or installs.  Soon, I will inherit a laptop that I want to experiment with.

How difficult id it to set up a WiFi connection at install?

For this installation I will be using 9.04, and the computer is an off brand.  It has a MSI 1024 mobo, core 2 processor, about 1.8ghz, with 1.5 gigs of Ram.  When my wife bought this it had Vista Home Premium installed...not a "likable" OS at all.  I have about 15 different distros, but am most familiar with Ubuntu and PCLOS.

All assistance appreciated.

---

### Post by PorkyPie on 2009-10-18
Is this what you are looking for? [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

---

### Post by 3rdalbum on 2009-10-18
> **WebToad said:**
> How difficult id it to set up a WiFi connection at install?

How long is a piece of string?

If the chipset is supported out-of-the-box (which it should be if you chose your laptop correctly :-)  ) then you just click on the Network Manager applet, click on your network, type your WPA passphrase and you're in. This should work from the live CD.

If the chipset is not supported out-of-the-box, it may require a trip to the Hardware Drivers program with a wired connection to install the driver.

In the worst-case scenario, the only driver might be one you have to compile yourself (in which case you need "build-essential" and "linux-headers-generic" from your wired connection to build it) or a Windows driver that can work in Ndiswrapper.

---

