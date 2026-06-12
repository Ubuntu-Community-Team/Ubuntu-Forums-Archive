---
title: "WPA supplicant"
date: 2015-04-09
forum: Networking &amp; Wireless
---

### Post by Inisfad on 2015-04-09
Help, help help.....I upgraded to 14.04 a few days ago, and reset my wifi to use Wicd, as I had been doing in the past.  I can connect to the internet with no problem, but my entire computer is running slowly, freezing and you tube videos are choppy and laggy.  Although I've been with Ubuntu for a while, I am unfamiliar with coding, etc.  When running top and System Monitor, I see that my CPU usage is 100% at all times, whether on the internet or not, and that wpa_supplicant is using 70% or more of that usage at all times.  My computer is almost unusable because of this.  I have tried researching this on the internet, but, to be honest, do not understand much of what I am reading.  My laptop is fairly old and my graphics card is an AMD/ATI RS482M which is no longer supported by AMD and has no proprietary drivers.  I need to sort this out, and wonder if there is an alternative to wpa_supplicant, if the fact that I am using Wicd rather than Network Manager is presenting a problem, or how to remedy this.  Hopefully someone here has the answer to this, as I am totally frustrated.  Thanks!

---

### Post by chili555 on 2015-04-09
Many newer users install Wicd when they are having trouble connecting. The real, underlying problem is frequently a driver issue. Until the driver issue is resolved, the problems only get worse!

Did the problem start when you installed Wicd? Have you considered removing it and trying a different solution?

What is the wireless device?```
lspci -nn | grep 0280
```Or, if it's a USB:```
lsusb
```

---

### Post by Inisfad on 2015-04-09
My driver is no longer supported by AMD, however, in continuing to fiddle around with this, running top and checking to see usage, I see that when I stop services network-manager, wpa supplicant goes away, I am still able to get on to the internet, can now view you tube without any lagging, etc.  So, my question now becomes how to get rid of this, as it appears that everything works fine.  I had originally thought I had removed network manager upon my upgrade to 14.04 (through synaptic), but, for some reason, it appears to still be around.  Of course, a temporary work around is to just stop the service each time I start my computer, but I would like to get rid of it all together.  Thanks for any advice (and thanks for answering above, too....)

---

### Post by chili555 on 2015-04-09
> My driver is no longer supported by AMD, I'm not sure what this means. I was referring to the wireless driver.

In any case, it seems that you have the solution! I suggest you remove Network Manager:```
sudo apt-get purge network-manager*
```After a reboot, you should be all set.

---

### Post by Inisfad on 2015-04-09
Sorry, I meant my graphics card no longer had driver support from AMD.  Anyway, thank you, I'll run the code above, and get rid of this headache!!  Thanks for your help....

---

