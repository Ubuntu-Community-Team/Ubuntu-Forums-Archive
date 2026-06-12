---
title: "Wireless stuck disabled after install of HW Sensors App"
date: 2010-09-28
forum: New to Ubuntu
---

### Post by JamButty on 2010-09-28
My wireless is stuck in disabled mode. This happened immediately after installing Hardware Sensors Monitor app, rebooting and adding it to the panel. I removed it from the panel, removed the app and booted again, but it remains disabled. Other threads I have found all seem to be initial OS installation issues, so they did not seem relevant. Wireless worked instantly and flawlessly immediately after first installing Ubuntu 2 months ago and since.
Am running Ubuntu LL with  a PRO/Wireless 2200BG [Calexico2] wireless. Currently hardwired which works but is very inconvenient.

Caveat - just before the above, I installed the lm-sensors and python support and rebooted, but that did not knock out the wireless. I have not removed those yet.

Anyone familiar with this?

for whatever it is worth, here is the full output of ```
sudo lshw -C network
``````
 *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:11:43:71:0f:f6
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.0.104 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:18 memory:dcffe000-dcffffff
  *-network:1 DISABLED
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:01:0f:6f
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=radio off
       resources: irq:17 memory:dcffd000-dcffdfff
```

---

### Post by marshmallow1304 on 2010-09-28
Could the wireless be actually physically off?  If there's a button or Fn+F* combination to toggle wireless power, try that.

---

### Post by xircon on 2010-09-28
Check this file:

```
cat /var/lib/NetworkManager/NetworkManager.state
```

If any of the lines say false edit and change to true save and reboot:

```
sudo gedit /var/lib/NetworkManager/NetworkManager.state
```

Then reboot.

I was told this works:

```
sudo service network-manager stop
sudo rm /var/lib/NetworkManager/NetworkManager.state
sudo service network-manager start
```

but it doesn't for me

---

### Post by JamButty on 2010-09-28
That was it! Embarrassed it was that simple, but glad it's up again. Had this machine for several years and never had a need to know about that. Thanks!

---

### Post by xircon on 2010-09-28
Stupid, almost embarrassing bug, wish somebody would fix it :)

Did the start/stop thing work for you?

---

### Post by JamButty on 2010-09-28
More simple than that - it was physically turned off thru  Fn+F2. I have been having chronic issues with the system freezing during boot and must have done that inadvertently while trying to get to a prompt with <cntrl><alt> <F2> while it was hanging after a boot.

---

