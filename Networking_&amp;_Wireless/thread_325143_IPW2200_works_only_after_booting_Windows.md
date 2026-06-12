---
title: "IPW2200 works only after booting Windows"
date: 2006-12-25
forum: Networking &amp; Wireless
---

### Post by Afief on 2006-12-25
Hello,

I am dual booting Windows and Edgy on my laptop(Acer Travelmate 4100), what i'm finding weird is that my wireless won't work(Radio:off) unless i boot into Windows, turn off the laptop and boot into edgy after that.

Here are some outputs, i'm not sure if they are related(right now everything is working, or i wouldn't be able to post):
```
afief@ubuntu:~$ dmesg| grep ipw
[17179594.208000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
[17179594.208000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17179594.208000] Driver 'ipw2200' needs updating - please use bus_type methods
[17179594.208000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[17179594.456000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
```

```
afief@ubuntu:~$ lspci|grep Net
06:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
```

```
cat /var/log/messages| grep ipw220
Dec 23 17:01:26 ubuntu kernel: [17179596.580000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
Dec 23 17:01:26 ubuntu kernel: [17179596.580000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Dec 23 17:01:26 ubuntu kernel: [17179596.580000] Driver 'ipw2200' needs updating - please use bus_type methods
Dec 23 17:01:26 ubuntu kernel: [17179596.736000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Dec 23 17:01:26 ubuntu kernel: [17179597.036000] ipw2200: Radio Frequency Kill Switch is On:
Dec 23 17:01:26 ubuntu kernel: [17179597.036000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
Dec 24 00:09:42 ubuntu kernel: [17179590.556000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
Dec 24 00:09:42 ubuntu kernel: [17179590.556000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Dec 24 00:09:42 ubuntu kernel: [17179590.556000] Driver 'ipw2200' needs updating - please use bus_type methods
Dec 24 00:09:42 ubuntu kernel: [17179590.568000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Dec 24 00:09:42 ubuntu kernel: [17179590.824000] ipw2200: Radio Frequency Kill Switch is On:
Dec 24 00:09:42 ubuntu kernel: [17179590.824000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
Dec 24 02:18:35 ubuntu kernel: [17179589.792000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
Dec 24 02:18:35 ubuntu kernel: [17179589.792000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Dec 24 02:18:35 ubuntu kernel: [17179589.792000] Driver 'ipw2200' needs updating - please use bus_type methods
Dec 24 02:18:35 ubuntu kernel: [17179589.936000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Dec 24 02:18:35 ubuntu kernel: [17179590.148000] ipw2200: Radio Frequency Kill Switch is On:
Dec 24 02:18:35 ubuntu kernel: [17179590.148000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
Dec 24 10:30:17 ubuntu kernel: [17179593.432000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
Dec 24 10:30:17 ubuntu kernel: [17179593.432000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Dec 24 10:30:17 ubuntu kernel: [17179593.432000] Driver 'ipw2200' needs updating - please use bus_type methods
Dec 24 10:30:17 ubuntu kernel: [17179593.660000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Dec 24 10:30:17 ubuntu kernel: [17179593.868000] ipw2200: Radio Frequency Kill Switch is On:
Dec 24 10:30:17 ubuntu kernel: [17179593.868000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
Dec 24 11:06:08 ubuntu kernel: [17179593.096000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
Dec 24 11:06:08 ubuntu kernel: [17179593.096000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Dec 24 11:06:08 ubuntu kernel: [17179593.096000] Driver 'ipw2200' needs updating - please use bus_type methods
Dec 24 11:06:08 ubuntu kernel: [17179593.096000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Dec 24 11:06:08 ubuntu kernel: [17179593.352000] ipw2200: Radio Frequency Kill Switch is On:
Dec 24 11:06:08 ubuntu kernel: [17179593.352000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
Dec 24 11:14:08 ubuntu kernel: [17179596.228000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
Dec 24 11:14:08 ubuntu kernel: [17179596.228000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Dec 24 11:14:08 ubuntu kernel: [17179596.228000] Driver 'ipw2200' needs updating - please use bus_type methods
Dec 24 11:14:08 ubuntu kernel: [17179596.432000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Dec 24 11:14:08 ubuntu kernel: [17179596.636000] ipw2200: Radio Frequency Kill Switch is On:
Dec 24 11:14:08 ubuntu kernel: [17179596.636000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
Dec 24 11:20:16 ubuntu kernel: [17179594.652000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
Dec 24 11:20:16 ubuntu kernel: [17179594.652000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Dec 24 11:20:16 ubuntu kernel: [17179594.652000] Driver 'ipw2200' needs updating - please use bus_type methods
Dec 24 11:20:16 ubuntu kernel: [17179595.008000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Dec 24 11:20:16 ubuntu kernel: [17179595.236000] ipw2200: Radio Frequency Kill Switch is On:
Dec 24 11:20:16 ubuntu kernel: [17179595.236000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
Dec 24 14:25:59 ubuntu kernel: [17179593.188000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
Dec 24 14:25:59 ubuntu kernel: [17179593.188000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Dec 24 14:25:59 ubuntu kernel: [17179593.188000] Driver 'ipw2200' needs updating - please use bus_type methods
Dec 24 14:25:59 ubuntu kernel: [17179593.460000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Dec 24 14:25:59 ubuntu kernel: [17179593.660000] ipw2200: Radio Frequency Kill Switch is On:
Dec 24 14:25:59 ubuntu kernel: [17179593.660000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
Dec 24 16:52:41 ubuntu kernel: [17179591.380000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
Dec 24 16:52:41 ubuntu kernel: [17179591.380000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Dec 24 16:52:41 ubuntu kernel: [17179591.380000] Driver 'ipw2200' needs updating - please use bus_type methods
Dec 24 16:52:41 ubuntu kernel: [17179591.644000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Dec 24 16:52:41 ubuntu kernel: [17179591.860000] ipw2200: Radio Frequency Kill Switch is On:
Dec 24 16:52:41 ubuntu kernel: [17179591.860000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
Dec 24 08:26:06 ubuntu kernel: [17179590.176000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
Dec 24 08:26:06 ubuntu kernel: [17179590.176000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Dec 24 08:26:06 ubuntu kernel: [17179590.176000] Driver 'ipw2200' needs updating - please use bus_type methods
Dec 24 08:26:06 ubuntu kernel: [17179590.176000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Dec 24 08:26:06 ubuntu kernel: [17179590.456000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
Dec 24 21:47:42 ubuntu kernel: [17179589.868000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
Dec 24 21:47:42 ubuntu kernel: [17179589.868000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Dec 24 21:47:42 ubuntu kernel: [17179589.868000] Driver 'ipw2200' needs updating - please use bus_type methods
Dec 24 21:47:42 ubuntu kernel: [17179590.088000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Dec 24 21:47:42 ubuntu kernel: [17179590.308000] ipw2200: Radio Frequency Kill Switch is On:
Dec 24 21:47:42 ubuntu kernel: [17179590.308000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
Dec 24 21:51:52 ubuntu kernel: [17179591.220000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
Dec 24 21:51:52 ubuntu kernel: [17179591.220000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Dec 24 21:51:52 ubuntu kernel: [17179591.220000] Driver 'ipw2200' needs updating - please use bus_type methods
Dec 24 21:51:52 ubuntu kernel: [17179591.220000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Dec 24 21:51:52 ubuntu kernel: [17179591.460000] ipw2200: Radio Frequency Kill Switch is On:
Dec 24 21:51:52 ubuntu kernel: [17179591.460000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
Dec 24 21:57:09 ubuntu kernel: [17179593.200000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.1
Dec 24 21:57:09 ubuntu kernel: [17179593.200000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Dec 24 21:57:09 ubuntu kernel: [17179593.200000] Warning: PCI driver ipw2200 has a struct device_driver shutdown method, please update!
Dec 24 21:57:09 ubuntu kernel: [17179593.460000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Dec 24 21:57:09 ubuntu kernel: [17179593.692000] ipw2200: Radio Frequency Kill Switch is On:
Dec 24 21:57:09 ubuntu kernel: [17179593.692000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
Dec 25 00:52:03 ubuntu kernel: [17179594.208000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
Dec 25 00:52:03 ubuntu kernel: [17179594.208000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Dec 25 00:52:03 ubuntu kernel: [17179594.208000] Driver 'ipw2200' needs updating - please use bus_type methods
Dec 25 00:52:03 ubuntu kernel: [17179594.208000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Dec 25 00:52:03 ubuntu kernel: [17179594.456000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)

```

If anybody has an idea how to get this to work without Windows i'd very much appreciate it. Booting into windows and back takes about 5 minutes.

Thanks in advance
Afief

---

### Post by miwi on 2007-01-02
Hi,
> **Afief said:**
> Hello,
I am dual booting Windows and Edgy on my laptop(Acer Travelmate 4100), what i'm finding weird is that my wireless won't work(Radio:off) unless i boot into Windows, turn off the laptop and boot into edgy after that.

Just wanted to tell you that I had the same problem over the last days with an Acer TravelMate 292LMi. See details in [http://forum.ubuntuusers.de/topic/65988/](http://forum.ubuntuusers.de/topic/65988/) (german). Searching for a solution, amongst other things I found your posting here. If you're still facing the problem it might be interesting for you that (at least on my side) it seems the acerhk kernel module doesn't identify the notebook type correctly. Currently I simply execute the following shell script to force it to identify it as a TM 290, and then turn the Wifi module on:
```
#!/bin/sh
sudo modprobe acerhk force_series=290
sudo echo "1" > /proc/driver/acerhk/wirelessled
```

Being a Linux novice, I'm still looking for a way to execute that automatically at boot time or at least at login time. Any help?

-Michael

---

### Post by jodeet on 2007-01-08
same deal as the originator reported, only on an HP Compaq nw8240 model laptop.

Thanks for the post.  I hadn't figured out the rhyme or reason yet as to how to make wireless work/not-work in Ubuntu.

One thing that may be worthy to add, is that the wireless management gui ('Wireless Assistant 0.5.5' in Kubuntu) always sees the available wireless networks, no matter whether MsWinXP was the previous bootup or not.  It's just that if MsWinXP was not the previous bootup, then the wlassistant fails to 'connect' to the wireless a.p.

---

