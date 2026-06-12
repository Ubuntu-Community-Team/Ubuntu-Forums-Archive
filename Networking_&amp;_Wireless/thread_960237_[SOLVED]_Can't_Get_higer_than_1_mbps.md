---
title: "[SOLVED] Can't Get higer than 1 mbps"
date: 2008-10-27
forum: Networking &amp; Wireless
---

### Post by Snackmafia on 2008-10-27
Hello.  This is my first post.  I really love Ubuntu, but for the life of me can't get my megabytes per second higher than 1 ](*,).  On Windows, I am capable of 54 megabytes per second.  I was wondering if there was a way to increase the megabytes per second.

Thank you in advance, Ubuntu is awesome!:)


EDIT:
I solved it!  The problem was fixed in Intrepid Ibex

---

### Post by cob on 2008-10-27
What's your wireless adapter chip?  On my BCM4306, I can't get more than 5.5mb/s, you can set it this way:

```
sudo iwconfig wlan0 rate 5.5M
```

---

### Post by Snackmafia on 2008-10-27
Please excuse my delay, but I can't answer right now.  I gotta go, but I'll answer as soon as possible.

---

### Post by knix on 2008-10-27
If you have such low bitrates, you may well have a broadcom card and be using b43.
If you use ndiswrapper, that will usually give better performance.
The optimal choice for broadcom, however, is to use wl. This will work on Hardy or Intrepid. For a howto on wl, see the sticky about broadcom and hardy in this section ([http://ubuntuforums.org/showthread.php?t=880218]("http://ubuntuforums.org/showthread.php?t=880218"))

with either, you need to modprobe -r b43, b44, ssb, and the driver you choose. Then you will have to modprobe the driver and b44. Mine for ndiswrapper looks like this:
modprobe -r b43
modprobe -r b44
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44

or for wl
modprobe -r b43
modprobe -r b44
modprobe -r ssb
modprobe -r wl
modprobe wl
modprobe b44

You can put these in your /etc/rc.local file before exit 0 to have them done automatically each time you boot.

---

### Post by Snackmafia on 2008-10-29
> **knix said:**
> If you have such low bitrates, you may well have a broadcom card and be using b43.


I'm sorry, I am pretty good with computers but am a little bit beginnerish on Linux.  You lost me at b43 :confused::confused::confused:.


Sooooooooooooooo... what is b43???



Thank you for your time and patience so much, I am so excited that I may be able to use the internet on Ubuntu!:)

---

