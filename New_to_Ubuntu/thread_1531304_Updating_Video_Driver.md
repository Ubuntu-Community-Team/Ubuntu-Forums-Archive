---
title: "Updating Video Driver"
date: 2010-07-14
forum: New to Ubuntu
---

### Post by Demolition Man on 2010-07-14
I started this discussion in [this]("http://ubuntuforums.org/showthread.php?t=1530575") thread, but I thought I'd start my own rather than hijack that one. I would like to update my video driver from the one currently installed (xf86-video-intel, ver. 2.9.1) to the newest available driver (xf86-video-intel, ver. 2.12.0). This new driver package is not available in Synaptic Package Manager. What should I do? TIA

---

### Post by baguahsing on 2010-07-14
Are you able to go to the video card website and download a linux driver?  Is there a software source that you can add?

---

### Post by maizuddin35 on 2010-07-14
does this mean you want to update and install your latest graphic card driver in your computer?

---

### Post by maizuddin35 on 2010-07-14
[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Install_Latest_Nvidia.2FATI_drivers](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Install_Latest_Nvidia.2FATI_drivers)
try to look this one, and find "driver"

---

### Post by Demolition Man on 2010-07-14
> **baguahsing said:**
> Are you able to go to the video card website and download a linux driver?  Is there a software source that you can add?

That's the thing, I'm on an ASUS 1005HAB netbook, but ASUS has NO linux drivers for this model on their website. I know the video chip is the Intel 945GME, so I tried Intel's website and I haven't had much luck there either.

---

### Post by Demolition Man on 2010-07-14
Well, after doing some research, it looks like xf86-video-intel is the only Linux driver for ALL Intel graphics chips. The development of xf86-video-intel is supported by Intel.

Alright, so I'm giving up trying to update the video driver, but I still have an issue, certain flash videos on the web don't play very well. The videos are choppy and slow. I have tried just about every fix I've been able to find for known flash issues with no luck. Am I just S.O.L.?

---

### Post by stantiques on 2010-07-23
This worked for me:

[http://www.howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx](http://www.howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx)

---

