---
title: "[SOLVED] How do I enable and use wireless in Kubuntu on Acer 5220 Laptop?"
date: 2008-07-07
forum: Networking &amp; Wireless
---

### Post by Rytron on 2008-07-07
Hi,
How do I enable and use wireless in Kubuntu on Acer 5220 Laptop?

Here is info on system:
Broadcom BCM94311 802.11g Wireless

I have seen some instructions on doing this but they are very tricky. Hopefully there is someone out there with the exact same model who could provide specific instructions on getting wireless going for me.

Please help.

Thanks.

---

### Post by Ayuthia on 2008-07-07
> **Rytron said:**
> Hi,
How do I enable and use wireless in Kubuntu on Acer 5220 Laptop?

Here is info on system:
Broadcom BCM94311 802.11g Wireless

I have seen some instructions on doing this but they are very tricky. Hopefully there is someone out there with the exact same model who could provide specific instructions on getting wireless going for me.

Please help.

Thanks.
You might go to the Konsole and see which revision of the 4311 card you have.  The rev 01 will work with the b43 driver or NDISwrapper in Ubuntu.  If you have the rev 02, NDISwrapper is the only one that is currently working on the Kubuntu install.  Just open up Konsole and type:
```
lspci -nn
```

Here is a link that can help you install the b43 driver and also has the link to the NDISwrapper no-fluff method:
[http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754)

Hope that helps.

---

### Post by Rytron on 2008-07-10
Here is a section of the output:

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabi                                                                                                   t Ethernet PCI Express [14e4:1693] (rev 02)
04:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PC                                                                                                   I [14e4:4311] (rev 01)

---

### Post by Rytron on 2008-07-16
I connected my laptop to my wireless modem via a lan cable.
Then I went to System > Hardware Drivers Manager; then there was a tick box to download the required broadcom drivers. I did that. I disconnected the LAN cable and tryed the wireless. This post is being done with wireless internet - IT WORKS PERFECT!

:popcorn:

Edit: on the subject of wireless problems - others having trouble with Linux and wireless internet can check out this:
[http://easylinuxwifi.org/]("http://easylinuxwifi.org/")

---

