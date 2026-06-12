---
title: "[SOLVED] No Webcam Intrepid - Suyin Corp. Compaq c700 series"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by kaffeboy on 2008-12-23
I finished a clean install from DVD (previous install was from CD and wasnt reading CDs). I installed Skype so I could videochat with my family. I get video, just not the video you'd want.

I'm on Ubuntu 8.10 Intrepid Ibex with all current updates as of 12/23/08.

I get some sort of yellowish static. In the other end, apparently it's all green.

Heres my lsusb output.
```
Bus 004 Device 003: ID 064e:c108 Suyin Corp. 
Bus 004 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```  
So basically Bus 004 is the Webcam by Suyin Corp on this Lappy. There's a picture in my website(blog) on what it looks like. Any info or help would be appreciated. I've been looking into this for the last 4 hours and no luck. I had to download a new libv4l to get THIS!

[http://kaffeboy.wordpress.com/2008/12/23/this-webcam-sucks-on-ubuntu-810/]("http://kaffeboy.wordpress.com/2008/12/23/this-webcam-sucks-on-ubuntu-810/")

Apparently this runs on uvcvideo. It ran fine on Ubuntu Ultimate Edition 2.0, but the wireless wasn't playing nice so I decided to return to the regular distro.

If I do **luvcview -f yuv** I get the same thing.

---

### Post by kaffeboy on 2008-12-23
I finally found it by browsing though launchpad bugs. I hope this bug gets fixed soon.

[https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/282473](https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/282473)

---

