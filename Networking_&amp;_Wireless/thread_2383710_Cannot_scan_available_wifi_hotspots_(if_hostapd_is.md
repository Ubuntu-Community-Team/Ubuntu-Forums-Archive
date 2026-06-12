---
title: "Cannot scan available wifi hotspots (if hostapd is running)"
date: 2018-01-28
forum: Networking &amp; Wireless
---

### Post by peterg17 on 2018-01-28
Hi,

My laptop asus n53sv runs Ubuntu 16.04.3 LTS (from /etc/lsb_release). I am attempting to set up my phone as a wifi hotspot and connect the laptop as a wifi client.

The laptop will work as a wifi hotspot. I use it to stream videos to my wifii-enabled television. I use my own hotspot systemctl service rather than the standard system stuff, which may be part of the problem. I have a complex networking environment with the computer functioning as a wifi hotspot with dlna server and the ethernet port connected to a tv tuner. The standard desktop networking does not appear to understand this environment.

Anyway I disable my hotspot service, and try to see what is out there by entering scanning commands. The command:
# **iw dev wlan0 info**
returns
*Interface wlan0*
*    ifindex 3*
*    wdev 0x1*
*    addr e0:b9:a5:66:ef:22*
*    ssid Jupiter*
*    type AP*
*    wiphy 0*
*    channel 1 (2412 MHz), width: 20 MHz, center1: 2412 MHz*

However when I try to scan, the command
# **iw dev wlan0 scan**
returns the message: *command failed: Operation not supported (-95)*

However I had hostapd running as a separate service, and when I stopped this service as well, scanning worked!
I only thought of this as I was composing this message, and thought I would leave it out there in case it helps someone else. Cost me hours.

---

