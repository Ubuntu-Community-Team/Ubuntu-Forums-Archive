---
title: "scp slow over Local LAN"
date: 2021-05-20
forum: Networking &amp; Wireless
---

### Post by seheatwole2 on 2021-05-20
I have an interesting issue and can't seem to find an answer in searching.  I have a smart camera running an older version of Debian that I connect to over a 1GigE switch.  The camera is 100Mbit ethernet and I am finding that one laptop I use can't download fast from the camera.  I have two laptops (brand new Dell latitude 5520 and 4 year old Dell latitude 4970) both running 20.04 and when I use scp to pull images off the camera, the older laptop pulls fine and downloads at N MBps but the new laptop seems to download at N kBps which gets slower and slower until nothing is transferring.  

Of interest is that scp uploading a file with the new laptop is fast but the download is slow.  Also, another interesting tidbit is that when I connect the camera directly to the laptop, i can download fast.  Only when connecting through a switch (and I have tried several) does the laptop establish a slow connection.  I have played with the output of ethtool and can't seem to find any difference between the new and old laptops running 20.04.  

Another issue I have encountered with the new laptop is that when running an ssh session, output will stall after intervals.  If I run a command in another terminal on the laptop (say "ls"), the ssh session will come back.  I have also noticed the UDP messages flowing from the camera to the laptop pause and come back to.  It is like the laptop falls asleep or something on the network interface.  Not sure if this is related but it the same network interface.

I am interested if anyone has an idea of where to look on this.  I haven't been able to find a solution via googling which usually has been my general way of solving issues like this.

---

### Post by TheFu on 2021-05-21
Seems really odd that one is "5" MBps and the other is "5" KBps.  How'd that happen?  The typical question is "what is different?"  Things to check:
[LIST]
[*]Ethernet cables. Don't use wifi. Wifi is too hard to isolate for performance testing. Don't use it until the last part of testing when everything else has been excluded.
[*]Switch ports.
[*]Versions of ssh/scp.
[*]Are static IPs used on all devices?
[*]DNS can be slow to time-out of all devices aren't in DNS, use IP addresses for testing.
[*]Are they all using IPv4 or all using IPv6?  IPv6 gets priority, if enabled.  I still disable it on all my computers because I don't know how to properly secure it. It doesn't honor NAT, for example, so a NAT router doesn't help if IPv6 is involved. 
[*]If you use the 3-device method, is it faster? Perhaps that's on an rsync thing. I tend to use rsync more than scp these days. Basically, the source and target are specified by the 3rd machine. This means both the source and the target have different machines/IPs specified.
[/LIST]

Also, not being vague would be helpful.  Exact bandwidth numbers. Exact NICs. Exact drivers. Exact switches, routers, everything. Just tweak/remove any MACs from output.

An easy way to gather much of this information is to use lshw and inxi.
```
inxi -Nxxxz
sudo lshw -C network
```

---

### Post by seheatwole2 on 2021-05-27
Thanks for the reply and information. It took me a couple of days to get back to the lab and get the laptops to test with. 

 I have tested this on multiple switches (all unmanaged NetGear or Linksys 1 Gbit types). I am using relatively new Cat5e and Cat6 cables which work well on other computers.  I have been using static IPs and using IPs in the commands to avoid DNS.  I turned off IPV6 on the offending laptop and it didn't solve the problem. ssh version is OpenSSH 8.21 on both machines.  Not sure is this is an rsync vs scp issue since the one computer is fast in upload and download but the other is fast on upload but super slow on download.

  I ran the inxi and lshw commands on both laptops and the output is below:

Older laptop that doesn't have the issue:
```

inxi -Nxxxz
Network:   Device-1: Intel Ethernet I219-LM vendor: Dell driver: e1000e v: 3.2.6-k port: f040
bus ID: 00:1f.6 chip ID: 8086:15d7
Device-2: Intel Wireless 8265 / 8275 driver: iwlwifi v: kernel port: f040
bus ID: 02:00.0 chip ID: 8086:24fd

sudo lshw -C network
*-network                
description: Wireless interface
product: Wireless 8265 / 8275
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:02:00.0
logical name: wlp2s0
version: 78
serial: 38:de:ad:21:b4:fc
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=iwlwifi driverversion=5.8.4-050804-generic firmware=36.77d01142.0 8265-36.ucode ip=128.154.10.24 latency=0 link=yes multicast=yes wireless=IEEE 802.11
resources: irq:130 memory:ef000000-ef001fff
*-network
description: Ethernet interface
product: Ethernet Connection (4) I219-LM
vendor: Intel Corporation
physical id: 1f.6
bus info: pci@0000:00:1f.6
logical name: enp0s31f6
version: 21
size: 1Gbit/s
capacity: 1Gbit/s
width: 32 bits
clock: 33MHz
capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=full firmware=0.1-4 ip=192.168.5.101 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
resources: irq:131 memory:ef200000-ef21ffff

```

Newer laptop with issue:
```

inxi -Nxxxz
Network:   Device-1: Intel driver: iwlwifi v: kernel port: 3000 bus ID: 0000:00:14.3
chip ID: 8086:a0f0
Device-2: Intel Ethernet I219-LM vendor: Dell driver: e1000e v: 3.2.6-k port: efa0
bus ID: 0000:00:1f.6 chip ID: 8086:15fb

sudo lshw -C network
*-network:0              
description: Wireless interface
product: Intel Corporation
vendor: Intel Corporation
physical id: 14.3
bus info: pci@0000:00:14.3
logical name: wlp0s20f3
version: 20
serial: 68:3e:26:6d:3d:23
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=iwlwifi driverversion=5.8.0-53-generic firmware=55.d9698065.0 QuZ-a0-hr-b0-55.u ip=10.0.108.84 latency=0 link=yes multicast=yes wireless=IEEE 802.11
resources: iomemory:600-5ff irq:16 memory:603f29c000-603f29ffff
*-network:1
description: Ethernet interface
product: Ethernet Connection (13) I219-LM
vendor: Intel Corporation
physical id: 1f.6
bus info: pci@0000:00:1f.6
logical name: enp0s31f6
version: 20
size: 1Gbit/s
capacity: 1Gbit/s
width: 32 bits
clock: 33MHz
capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=full firmware=0.8-4 ip=192.168.5.103 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
resources: irq:199 memory:8e300000-8e31ffff

```

Any insight is much appreciated.  I have tried every trick that I know of and can't figure it out.  As I said before, when I remove the switch (doesn't matter which one) and plug directly into the camera, the problem goes away.

---

### Post by TheFu on 2021-05-27
Also, what are the routing tables for each.  They appear to be connected to different networks. If the priority isn't setup correctly, then the wrong network path might be used. Perhaps causing a loop in the network?

BTW, the NICs are not identical between those laptops.  I don't know what the difference is between the 2 versions, but that could be worth looking into.

---

### Post by seheatwole2 on 2021-06-09
I didn't get the routing tables but did find a solution to the issue though I can't explain why.  The difference between the two setups (directly connecting to the camera and connecting through the unmanaged switch) was one is a direct connection to a 100Mbit ethernet link and one is connecting to the same interface but through a 1Gbit switch.  Ethtool showed that the direct connection negiotated the link to 100Mbps but when connected to the switch the laptop was at 1Gbit.  Through the switch we have fast upload from the laptop but slow downloads.  I forced the connection to 100Mbps via:
> ethtool -s interface speed 100 duplex full autoneg on
This fixed the issue and the downloads were back to full speed.  Not sure why the new NIC and driver have issues negotiating the connection over the switch.  I tested this against multiple computers with 100Mbit interfaces (including the camera where I originally ran into the trouble) and had the same issue so it is the laptop and not the camera.  

I think baring a new driver, I can limp along with modifying the connection when I have to connect to something with a speed difference through a switch.

---

### Post by TheFu on 2021-06-09
So, post #2, bullet point 2 was correct?

---

