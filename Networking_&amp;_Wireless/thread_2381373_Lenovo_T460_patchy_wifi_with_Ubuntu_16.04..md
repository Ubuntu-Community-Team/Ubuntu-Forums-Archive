---
title: "Lenovo T460: patchy wifi with Ubuntu 16.04."
date: 2017-12-30
forum: Networking &amp; Wireless
---

### Post by chah on 2017-12-30
I have recently installed 16.04 on a Lenovo T460 which has an Intel 8260 chipset. With the original ucode firmware (21), I can get something like 1-2 minutes of connectivity before the wifi drops out. A drop-out does not mean that I lose connectivity to the router, I still have an IP address, but all connection to the internet just suddenly halts, with all browser tabs hanging until a time-out occurs. Disconnecting the wifi from the router followed by reconnecting gives me another 1-2 minutes of connectivity.

I tried changing the ucode in /lib/firmware by renaming some of the files there. I found that an older version: iwlwifi-8000C-13.ucode gives me maybe 30 minutes upto a couple of hours of connectivity, but still eventually drops out.

Here is the results from the wireless-info script: [http://paste.ubuntu.com/26284975/](http://paste.ubuntu.com/26284975/)

I see many people with the same problem, but nothing I've tried has worked. Could some of the gurus here help with their expert advice? I've currently moved near to my router and am connected through a wire cable.

Thanks!

---

### Post by jeremy31 on 2017-12-30
See if chili555's advise helps [https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520](https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520)

---

### Post by chah on 2017-12-30
Thanks for the suggestion jeremy31, I just tried the suggestions there. Turning off the power management seemed to make my connection time worse rather than better. I could connect for maybe 1 to 2 seconds before being dropped.

I tried setting the region as recommended, but when I did iw reg get to check, it hadn't changed.

---

### Post by jeremy31 on 2017-12-31
Have you set IPv6 to ignore in network manager?  Can you change the wifi router to use channel 9?  Is there a setting in the router for WMM/QoS that can be enabled?

---

