---
title: "RT3090 fails to connect"
date: 2013-11-30
forum: Networking &amp; Wireless
---

### Post by jp734 on 2013-11-30
I have an RT3090 that I'm trying to get to work but having a really difficult time. I've researched and found a lot of topic regarding this device but could not find the solution.

When I execute **iwlist wlan1 scan** on terminal, for the most part, I would say 98% of the time, it will give me **No scan result**. The other two percent , it will give me a result with my router info. The only thing I notice that is suspicious is the quality of he signal. Considering I am only 5 feet away from the router, I am getting a 21/70 quality.

Other than that, the device is detected with the right driver installed.

sudo lshw -C network gives me:
>   *-network
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan1
       version: 00
       serial: 1c:65:9d:be:cd:78
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.11.0-12-generic firmware=0.34 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:49 memory:febf0000-febfffff


Any suggestions will be great. Any other info you need, just let me know. Thanks in advance

---

### Post by varunendra on 2013-12-03
This is one of the cards that scare me because of the hopeless dead ends they sometimes lead me to. But since no one else picked it up, I think it is safe to post as a BUMP to the thread, as well as ask for more information. If still no one else with better experience with it picked it up, I may try my luck.

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags, not the 'Quote' tags that you used above. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

