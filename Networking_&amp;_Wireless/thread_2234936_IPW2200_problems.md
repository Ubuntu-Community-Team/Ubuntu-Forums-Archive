---
title: "IPW2200 problems"
date: 2014-07-17
forum: Networking &amp; Wireless
---

### Post by achamberlain46and2 on 2014-07-17
Hi guys! My wireless keeps dropping out and has terrible performance! Tried a clean install of 14.04LTS and i'm having the same trouble. I apologise for anything in advance, i am an ubuntnoob.

I'm running an intel ipw2200 and i have a lot of dmesg, syslog and kernlogs.
Sorry, i feel stupid!

---

### Post by tgalati4 on 2014-07-17
Try resetting the card.  Pull the cover on the bottom of the laptop, gently pull out the card and reseat it.  Make sure the 2 antenna connections are secure.  It's possible that your antenna wires have worn out--they go through the hinge in the screen.  It's also possible that you have too many neighbors.  Try moving to where there is less people.

---

### Post by jjaakkol on 2014-09-06
I have "old and good" problem with my IBM T40. WLAN works random amount of time and then:

 ipw2200: Firmware error detected.  Restarting. 

Installed yesterday 14.04 Lubuntu to IBM T40.

```
dmesg | grep ipw
[   12.960341] libipw: 802.11 data/management/control stack, git-1.1.13
[   12.960348] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   13.145561] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   13.145570] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   13.217982] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   13.513928] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
[  294.337101] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[  301.234995] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[  315.260248] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[  322.072242] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[  346.901865] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[  356.930156] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[  396.343701] ipw2200: Firmware error detected.  Restarting.
[ 1742.482638] ipw2200: Firmware error detected.  Restarting.
[ 1827.917518] ipw2200: Firmware error detected.  Restarting.


```

```
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 05
       serial: 00:15:00:11:d9:72
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) ip=192.168.255.3 latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: irq:11 memory:c0210000-c0210fff


```

```
md5sum /lib/firmware/ipw2200*
045a46163341514ef17490c76bd0c858  /lib/firmware/ipw2200-bss.fw
44cdedc8d5a0eb727466ed982db97a53  /lib/firmware/ipw2200-ibss.fw
ebc70dce66f876695fa8852b8ff757ee  /lib/firmware/ipw2200-sniffer.fw


```

I have googling A LOT about this issue but no final solution in my case found. I have tried different WLAN hardware (same model) no success. With XP WLAN worked. 

 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:01 UTC 2014 i686 i686 i686 GNU/Linux

---

