---
title: "Bluetooth boombox paired/selected but audio still goes through speakers"
date: 2014-01-27
forum: Networking &amp; Wireless
---

### Post by mcmillanje on 2014-01-27
I have a system76 laptop with built in bluetooth running 13.10
I also have a bluetooth boombox (UE Boom) which I would like to use.

I successfully paired the UE Boom and It shows connected. In the sound settings it shows the device, and lets me click on it to select it. The only problem is: *all audio still goes through my laptop's built in speakers.*
[IMG]https://dl.dropboxusercontent.com/u/14514509/uepaired.png[/IMG]


I know the A2DP support is a little weird in linux, but I'd really like to get it working. Anyone have any insight?

---

### Post by mcmillanje on 2014-01-27
Figured it out. For some reason ubuntu's default bluetooth configuration program does not let you select the bluetooth profile to use. I installed blueman and was able to select a2dp and it works now.

---

### Post by maggaknet on 2014-08-28
finally a solution!!!!
tried everything so far without success. found in [http://ubuntuforums.org/showthread.php?t=2144841&page=2](http://ubuntuforums.org/showthread.php?t=2144841&page=2)

just type in terminal: pactl load-module module-bluetooth-discover

worked out of the box for me... i was absolutely stunned.

---

