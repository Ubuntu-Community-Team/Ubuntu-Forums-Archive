---
title: "Weird wireless problem in Ubuntu 6.10"
date: 2007-03-30
forum: Networking &amp; Wireless
---

### Post by stefan.ciobaca on 2007-03-30
Here goes nothing. I've setup a small home network, with an Ubuntu server doing the NATing. Server is at 192.168.1.1 and Ubuntu 6.10 is at 192.168.1.126 (not relevant, but still).

From time to time, randomly, the connection from .126 to .1 goes blank. For example: any open ssh connections freeze, instant messenger stops working. To repro, I did this:

From 192.168.1.1 I ping'ed 192.168.1.126 and vice-versa. I then started a big download from .1 to .126 and waited.

scp [email]me@192.168.1.1:ubuntu*.iso[/email] .
me@192.168.1.1's password: 
ubuntu-7.04-beta-desktop-i386.iso               5%   35MB  26.3KB/s - stalled -st

As you can see, after a small while, the download stalled.

At the exact time, the ping from .126 to .1 says:
ping: sendmsg: Network is unreachable

And the ssh connection from which I do ping from .1 to .126 freezes (I must close the window, not even Ctrl+C works).

The internet connections generally works ok for viewing webpages, but when it comes to downloading big files or IMing for more than, say, 10 minutes, it just doesn't work. When .126 boots Windows, everything works just fine.

So the problem must be the wireless drivers on .126. I've checked everything, and I found just something that seems out of the ordinary:

```

me@mymachine:~$ dmesg | grep ipw
[17179590.956000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
[17179590.956000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17179590.956000] Driver 'ipw2200' needs updating - please use bus_type methods
[17179592.076000] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
[17179592.264000] ipw2200: Detected geography ZZA (11 802.11bg channels, 13 802.11a channels)
[17181655.452000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
[17181655.452000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17181655.452000] Driver 'ipw2200' needs updating - please use bus_type methods
[17181655.452000] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
[17181655.632000] ipw2200: Detected geography ZZA (11 802.11bg channels, 13 802.11a channels)

```

Does anyone know how I can fix these interruptions?

Thank you.

---

### Post by x64Jimbo on 2007-03-30
Have you tried using ndiswrapper with the Windows driver?

---

### Post by stefan.ciobaca on 2007-03-31
Nope. The laptop is Centrino and wireless worked flawlesly when I had Gentoo installed. So I'm pretty sure it's some sort of misconfiguration. I just don't know what to try next.
Any hint would be apreciated.

---

### Post by pfoff on 2007-04-09
I ran into the same problem on my thinkpad r52. Messages are:
```
Apr  9 09:24:25 tpr52 kernel: [17224917.448000] ieee80211: 802.11 data/management/control stack, git-1.1.13
Apr  9 09:24:25 tpr52 kernel: [17224917.448000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Apr  9 09:24:25 tpr52 kernel: [17224917.880000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
Apr  9 09:24:25 tpr52 kernel: [17224917.880000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Apr  9 09:24:25 tpr52 kernel: [17224917.880000] Driver 'ipw2200' needs updating - please use bus_type methods
Apr  9 09:24:25 tpr52 kernel: [17224917.880000] ACPI: PCI Interrupt 0000:04:02.0[A] -> GSI 21 (level, low) -> IRQ 66
Apr  9 09:24:25 tpr52 kernel: [17224917.884000] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
Apr  9 09:24:26 tpr52 kernel: [17224918.228000] ipw2200: Detected geography ZZE (13 802.11bg channels, 19 802.11a channels)
Apr  9 09:24:27 tpr52 kernel: [17224919.148000] eth1: NETDEV_TX_BUSY returned; driver should report queue full via ieee_device->is_queue_full.
Apr  9 09:24:27 tpr52 kernel: [17224919.360000] ADDRCONF(NETDEV_UP): eth0: link is not ready
```
Symptoms are network freezes and after every suspend i need to stop networking, remove wlan modules and restart networking. And even then, it tends not to work...
I configure the wlan stuff in /etc/network/interfaces: 
```
auto eth1
iface eth1 inet dhcp
       wpa-driver wext
       wpa-ssid FoFsWLAN
       wpa-passphrase PlainAsciiPassphrase
       wpa-key-mgmt WPA-PSK
       wpa-pairwise TKIP CCMP
       wpa-group TKIP CCMP
       wpa-proto WPA RSN

```
It never starts automatically, but after reloading modules and restarting network everything works...
I would appreciate any hint, cause I've no ideas where to search....

:wq

---

### Post by Roland of Gilead on 2007-04-09
This sounds exactly like [what's happening with my Thinkpad T40]("http://ubuntuforums.org/showthread.php?t=404538") (Centrino ipw2100).

---

### Post by Zwalther on 2007-04-09
The log files indicate a driver problem, so you should probably file a bug against the correct kernel package so the people in the kernel team can take a look at it. 

Oh, wait, that bug has already been filed: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/84418](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/84418)

You could add a comment saying that you're affected too. Maybe it will help speed up the fix.

---

### Post by pfoff on 2007-04-10
How'bout 2.6.20, is it affected, too? Any other solutions or patches? Wouldn't like to use praehistoric kernel versions, just because of this shitty bug....
Can't wait, as i need it at work...

---

### Post by x64Jimbo on 2007-04-12
You could try using NDISWrapper. I know it's dumb to have to use a Windows driver, but I have been using NDISWrapper'd Windows drivers on my Broadcom cards for 3 years and have not had nearly as many problems as when I've tried to use the kernel drivers. If it's critical that it work, you could try this until the bug is fixed.

---

