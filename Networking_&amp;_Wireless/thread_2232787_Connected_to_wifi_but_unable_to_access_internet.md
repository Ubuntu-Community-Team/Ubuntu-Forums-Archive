---
title: "Connected to wifi but unable to access internet"
date: 2014-07-04
forum: Networking &amp; Wireless
---

### Post by migpato on 2014-07-04
Hi all,

I've recently upgraded my laptop to Ubuntu 14.04 LTS and ever since I've had trouble accessing the internet with some wifi connections. In some cases all works fine. In other cases I do see the wifi and connect to it without problems (I can also see the router and access its configuration details), but I simply can't browse any site. I have also connected directly with the cable, but the same happens, i.e. not able to access any site.

I have tried several solutions posted in the forum for similar problems, but none seemed to work in my case.

Attached is the output the wireless script ([http://ubuntuforums.org/showthread.php?p=12350385#post12350385](http://ubuntuforums.org/showthread.php?p=12350385#post12350385)) in the case of the wifi not working.

Any suggestion is very welcome! Thanks for your support!

---

### Post by lotharmat on 2014-07-04
Have a look at this:

```

Intel Ultimate-N 6300

?

iwl6000

No

No

No

This wireless card does not work in Karmic. (iwlagn expects firmware/ucode version 3 or lower, but 4 is the only version available). Installing linux-backports-modules-karmic fixes this. BugLink linux-archive.org thread Blog post detailing fix

2010-01-29
```

According to the wiki, the 6300 doesn't really play nicely!

---

### Post by Bucky Ball on 2014-07-04
> **lotharmat said:**
> According to the wiki, the 6300 doesn't really play nicely!

The link you provide is from 2010. Long time in Linux land. ;)

Please provide the output of:

```
sudo lshw -C network
```

Also, are you running a static IP on your local machine? Connecting through your own router/access point?

Welcome to the forums.

---

### Post by migpato on 2014-07-04
Hi,

Thanks a lot for your replies!

Here is the output of lshw -C network:
```
  *-network
       description: Ethernet interface
       product: 82579LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: 3c:97:0e:40:c7:0a
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e latency=0 multicast=yes
       resources: irq:20 memory:f3a00000-f3a1ffff memory:f3a3b000-f3a3bfff ioport:6080(size=32)
  *-network
       description: Wireless interface
       product: Centrino Ultimate-N 6300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 3e
       serial: 24:77:03:cf:07:00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-30-generic firmware=9.221.4.1 build 25532 ip=192.168.178.32 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:47 memory:f3000000-f3001fff
```

> Also, are you running a static IP on your local machine?
I am not sure if I am running a static IP (sorry, I am a bit of a beginner...), but I suppose not since in the IPv4 settings of this wireless the method "Automatic (DHCP)" is selected. Does that answer your question?

> Connecting through your own router/access point?
In the particular case I'm having the problem, I am indeed connecting through my own router.

Thanks in advance for any suggestions!

---

