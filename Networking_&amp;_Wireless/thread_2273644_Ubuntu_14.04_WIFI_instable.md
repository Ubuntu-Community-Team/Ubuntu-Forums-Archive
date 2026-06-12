---
title: "Ubuntu 14.04 WIFI instable"
date: 2015-04-14
forum: Networking &amp; Wireless
---

### Post by daniel_k3 on 2015-04-14
Hi,

I installed Ubuntu 14.04 on my new laptop - HP ProBook
From some reason it connects and drops all the time from any wifi network I try
I also tried to use external USB wifi card, it works sometimes but also unstable.
Any help would be appreciated

WIFI details:
description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 38:63:bb:cb:25:87
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz

---

### Post by ian-weisser on 2015-04-15
Have you ruled out the access point or router? Consumer-grade sometimes provides solid connections for some and flaky for others when it needs to be reset.
Have you ruled out interference from too many networks trying to use the same (or adjacent) channels?
Have you ruled out poor connections caused by the geometry and materials of the space? Are you too far from the access point, or trying to access through opaque material?

Sometimes-it-works-and-sometimes-it-doesn't does not seem like a typical software or driver problem.
Both-hardware-are-flaky also seems to point outward instead of the laptop.

---

### Post by michi1983 on 2015-04-15
> **daniel_k3 said:**
> Hi,

WIFI details:
description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 38:63:bb:cb:25:87
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
This is your eth0, this is your wired connection. And to be honest, you already have a problem there because you only negotiate with the router on 10Mbit/s.
So i would suggest that you set up your router from scratch.
Then I would use [LinSSID]("http://sourceforge.net/projects/linssid/") or [WiFi Radar]("https://apps.ubuntu.com/cat/applications/precise/wifi-radar/") to check if any channels from the neighborhood are interfering.

---

### Post by daniel_k3 on 2015-04-16
Hi guys,

Thanks for the advice
I don't believe that it would be down to router settings as I have my old laptop with the same operating system and standard configurations that is working fine,
at home and in the office. In both places there are no custom router configurations.
Is there anything else that you think that I can do to resolve it? I'm happy to provide any supporting details

---

### Post by michi1983 on 2015-04-16
yes, please go to the sticky post on top of the forum and execute the script and post the result here.

---

### Post by daniel_k3 on 2015-04-16
Please see attached, I hope that helps

---

### Post by michi1983 on 2015-04-17
Alright, please follow [this]("http://ubuntuforums.org/showthread.php?t=2273794&highlight=RTL8723BE") link. This guy had the same problem and got solved ;) Good luck!

---

### Post by daniel_k3 on 2015-04-18
Michi1983, it worked like a magic, all I had to do was to  run the first try and reboot. Thank you so much

echo "[COLOR=#6A6A6A][FONT=arial]**options [COLOR=#417394]rtl8723be[/COLOR]**[/FONT][/COLOR][COLOR=#545454][FONT=arial] fwlps=0 swlps=0" | sudo tee /etc/modprobe.d/rtl8723be.conf[/FONT][/COLOR]

---

### Post by michi1983 on 2015-04-18
That was not my work though ;) I just showed you the way.
Glad it works now!

---

