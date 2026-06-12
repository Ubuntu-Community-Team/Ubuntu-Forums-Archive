---
title: "lost wired network - can't get it back (18.04, Dell XPS 9570 + TB dock TB16)"
date: 2019-01-15
forum: Networking &amp; Wireless
---

### Post by daffy_ on 2019-01-15
Hi, I have a Dell XPS 9570 running Ubuntu 18.04 and a Dell TB16 Thunderbolt dock where my cabled network is attached.

Sometimes I loose the physical network (left only with wireless) - and a reboot helps. One time I lost the physical network, I tried to be clever and try to re-enable it. Never scared of trying out things, I found this post:
[https://askubuntu.com/questions/1067204/on-ubuntu-18-04-ethernet-through-thunderbolt-is-detected-on-reboot-but-loses-co/1074540](https://askubuntu.com/questions/1067204/on-ubuntu-18-04-ethernet-through-thunderbolt-is-detected-on-reboot-but-loses-co/1074540)
With this recommendation:
[https://askubuntu.com/questions/1029250/ubuntu-18-04-ethernet-disconnected-after-suspend/1030154#1030154](https://askubuntu.com/questions/1029250/ubuntu-18-04-ethernet-disconnected-after-suspend/1030154#1030154)

Running this command: 
```
sudo lshw -C network
```
I had three ethernet interfaces, two were driver=bridge, and one was driver=veth. So I did this:

```

sudo modprobe -r veth
sudo modprobe -i veth

```

And now I am stuck with no physical network at all, even after reboot. Any idea on what I can do to get my physical network back? I assume that what happened was that some kind of virtual package was removed, and took with it the underlying drivers, and if I try to enable the virtual module nothing happens. 

If I run `sudo lshw -C network` now - I get two ethernet interfaces - the one which had `veth` is missing.

Thunderbolt docks are a mystery to me - and also to some of the Ubuntu devs it seems, with regards to how unstable things via thunderbolt is. (USB sometimes work, sometimes not (mostly not), have to run with no security, screen has to flicker on/off and change resolution a couple of times when attached, etc)

Hope someone can help me with this, please :)

---

### Post by TheFu on 2019-01-15
How about posting the actual output from those commands? Start with:
**sudo lshw -C network**
Please use code tags so things line up.

Thunderbolt is a security problem. Any bus that provides DMA is a security nightmare.

---

### Post by daffy_ on 2019-01-16
Thanks for the tip, will do so now. But first:
To debug the TB16 itself, I tried dual-booting to windows, and there wired network was working. Then I booted back to Ubuntu, and still no network. So I tried pulling the power of the TB16 and leaving it off power over the night. And today the wired network is back - so this might have been a combination of Ubuntu issues and TB16 issues.

However, here is the result of lshw:

```

&#10140;  ~ sudo lshw -C network
  *-network                 
       description: Wireless interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:3b:00.0
       logical name: wlp59s0
       version: 29
       serial: 0c:54:15:b6:2a:06
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.15.0-43-generic firmware=34.3125811985.0 ip=10.200.193.112 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:ed400000-ed403fff
  *-network:0
       description: Ethernet interface
       physical id: 2
       logical name: docker0
       serial: 02:42:ab:4f:04:e1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=172.17.0.1 link=no multicast=yes
  *-network:1
       description: Ethernet interface
       physical id: 3
       logical name: enx106530be464e
       serial: 10:65:30:be:46:4e
       size: 1Gbit/s
       capacity: 1Gbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8152 driverversion=v1.09.9 duplex=full ip=10.55.40.151 link=yes multicast=yes port=MII speed=1Gbit/s

```

Of these - the last one, with driver=r1852, was not present yesterday. There was a different version with driver=bridge (so I had two networks with driver=bridge, not one as of today)

So I still don't know what happened to the VETH network, but at least I have wired network back now.

---

### Post by daffy_ on 2019-01-16
> **TheFu said:**
> 
Thunderbolt is a security problem. Any bus that provides DMA is a security nightmare.

I am aware of that. A security nightmare - but a dream to use for end-users when it works :)

I started using it with security **on** under Ubuntu - but that caused too many problems - so now I have turned security off on Thunderbolt. Which is a bit sad. (and scary)

---

### Post by TheFu on 2019-01-16
enx106530be464e is the real card. There always must be that, period.  Virtual interfaces are useless without having a real interface to actually push traffic.  Too bad it is realtek and not an intel NIC.  Realtek can be flaky under linux and use more CPU, more interrupts, more RAM, to do the same things that intel NICs do with much less.

---

