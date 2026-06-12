---
title: "Ethernet card very limited speed"
date: 2024-06-24
forum: Networking &amp; Wireless
---

### Post by invalidsun on 2024-06-24
To start this off, I am very new to Linux/Ubuntu. This is on a fresh install of Ubuntu 24.04, to be used as a media server / in-house web server.
My ethernet card seems to be limited to 40-50 mbps at best and I have spent hours trying to figure this out. I should be getting 1gbps down/up.
I have tested with a different cable and port, no luck. Tested the same cable and port with Windows PC, that received the full gig. Tested bridging the connection from my Windows PC, still got 40mbps on the Ubuntu.
The card is capable of 1gbps, and did so when it ran Windows itself, so I'm not sure what I'm doing wrong here. Also, I do not know how to install drivers on Ubuntu (I said I was new), so if that shows to be the case, please guide me on the steps. I did look into the chip and it stated that it required the alx driver, which I do appear to have, but I could be wrong. Here's my _**lshw**_: 

```

invalidsun@bernahl:~$ sudo lshw -C network
  *-network DISABLED        
       description: Wireless interface
       product: Dual Band Wireless-AC 3168NGW [Stone Peak]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 10
       serial: 68:ec:c5:68:cc:7a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=6.8.0-35-generic firmware=29.198743027.0 3168-29.ucode latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:126 memory:df200000-df201fff
  *-network
       description: Ethernet interface
       product: QCA8171 Gigabit Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 10
       serial: 30:9c:23:8c:f6:f3
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx driverversion=6.8.0-35-generic duplex=full ip=192.168.1.12 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:19 memory:df100000-df13ffff ioport:d000(size=128)

```

Also, to show the speedtest results (and yes, I've tested on a couple other speed tests as well as downloads themselves)
```

invalidsun@bernahl:~$ speedtest-cli
Retrieving speedtest.net configuration...
Testing from Brightspeed (**redacted**)...
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by **redacted** (r**edacted**) [86.42 km]: 15.491 ms
Testing download speed................................................................................
Download: 27.98 Mbit/s
Testing upload speed......................................................................................................
Upload: 192.81 Mbit/s

```

---

### Post by TheFu on 2024-06-24
Speed test is about internet speeds, not NIC speeds.  Test between 2 systems on the same LAN only. Use **iperf3** for this.
You want the minimal number of wires and network devices between the two systems.  For example, 
```
$ iperf3 -c istar
Connecting to host istar, port 5201
[  5] local 172.22.22.5 port 41498 connected to 172.22.22.20 port 5201
[ ID] Interval           Transfer     Bitrate         Retr  Cwnd
[  5]   0.00-1.00   sec  5.85 GBytes  50.2 Gbits/sec    0   2.65 MBytes       
[  5]   1.00-2.00   sec  5.99 GBytes  51.5 Gbits/sec    0   2.65 MBytes       
[  5]   2.00-3.00   sec  5.58 GBytes  47.9 Gbits/sec    0   2.98 MBytes       
[  5]   3.00-4.00   sec  5.84 GBytes  50.2 Gbits/sec    0   3.15 MBytes       
[  5]   4.00-5.00   sec  5.99 GBytes  51.4 Gbits/sec    0   3.15 MBytes       
[  5]   5.00-6.00   sec  6.01 GBytes  51.6 Gbits/sec    0   3.15 MBytes       
[  5]   6.00-7.00   sec  5.54 GBytes  47.6 Gbits/sec    0   3.15 MBytes       
[  5]   7.00-8.00   sec  5.30 GBytes  45.5 Gbits/sec    0   3.15 MBytes       
[  5]   8.00-9.00   sec  5.15 GBytes  44.2 Gbits/sec    0   3.15 MBytes       
[  5]   9.00-10.00  sec  5.05 GBytes  43.3 Gbits/sec    0   3.15 MBytes       
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bitrate         Retr
[  5]   0.00-10.00  sec  56.3 GBytes  48.4 Gbits/sec    0             sender
[  5]   0.00-10.04  sec  56.3 GBytes  48.2 Gbits/sec                  receiver

iperf Done.
```
50 Gbps - not bad.  I cheated.  This was between a virtual machine and the host computer both running on the same hardware.  Let's go between two different systems, GigE connected with real CAT5e cables.
```
$ iperf3 -c istar
Connecting to host istar, port 5201
[  5] local 172.22.22.6 port 38142 connected to 172.22.22.20 port 5201
[ ID] Interval           Transfer     Bitrate         Retr  Cwnd
[  5]   0.00-1.00   sec   114 MBytes   958 Mbits/sec    0    352 KBytes       
[  5]   1.00-2.00   sec   112 MBytes   941 Mbits/sec    0    373 KBytes       
[  5]   2.00-3.00   sec   112 MBytes   939 Mbits/sec    0    373 KBytes       
[  5]   3.00-4.00   sec   113 MBytes   945 Mbits/sec    0    373 KBytes       
[  5]   4.00-5.00   sec   112 MBytes   937 Mbits/sec    0    419 KBytes       
[  5]   5.00-6.00   sec   113 MBytes   947 Mbits/sec    0    419 KBytes       
[  5]   6.00-7.00   sec   112 MBytes   939 Mbits/sec    0    419 KBytes       
[  5]   7.00-8.00   sec   112 MBytes   940 Mbits/sec    0    419 KBytes       
[  5]   8.00-9.00   sec   112 MBytes   939 Mbits/sec    0    419 KBytes       
[  5]   9.00-10.00  sec   113 MBytes   947 Mbits/sec    0    419 KBytes       
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bitrate         Retr
[  5]   0.00-10.00  sec  1.10 GBytes   943 Mbits/sec    0             sender
[  5]   0.00-10.04  sec  1.10 GBytes   938 Mbits/sec                  receiver

iperf Done.

```
Ok, that's more like it.  940 Mbps is what a GigE connection on the same LAN can be expected to provide. Not any higher.  All my switches and cables are GigE capable.  Both NICs are "I211 Gigabit Network Connection" NICs on both systems.  I don't have any 2.5 Gbps NICs.

I do have a USB3-to-GigE adapter that used the ALX driver that I use on a laptop, but that laptop hasn't been powered on since before COVID started.  When I last tested it, it was getting 920 Mbps according to iperf3 going through 2 switches from the other side of the house.

No way can my internet connection come close.  According to speedtest, I have:
```
Download: 28.29 Mbit/s
Upload: 6.24 Mbit/s
```
Which is what my $120+/month ISP bill says I should get. Of course, my connection isn't a typical residential connection and I have a /29 of public IPs, but still, my speeds should be 10x that (300/30 Mbps) to be competitive.  Last year, I tried fibre from the most hated company in my country. The service they provided was fantastic. Their billing problems went on for months, never to be solved and they didn't provide the specific thing I requested on day 1 when I signed up, but they kept charging me for it.  Since they couldn't fix the billing, I cancelled.  If I'd gotten their standard service and made due with it, and didn't mind them TAKING payments directly, I'd probably still have the service. It was solid, even at 300/300 Mbps.  Don't know what I'd do with a full 1 Gbps. Talk about overkill for our needs.

Anyway, speedtest isn't the way to test NIC performance.  You need to test the 2 closest, wired, computers, that support the speeds you think you should be getting and troubleshoot that first.

---

### Post by currentshaft on 2024-06-24
How are you connecting to the Internet? Is there a firewall appliance on the gateway?

---

### Post by invalidsun on 2024-06-24
So, I wasn't able to reach another device in the network with this, but I could test the direct connection to the network itself and that came up fairly okay, while still short of Gig speeds, this would be a speed I'd be comfortable achieving, but again, this is not the case across multiple different cases. My setup is a simple home system, it's the 2nd PC in the house, and the other PC regularly and consistently has pushed and pulled 940mbps every single day for the last 3 years.
```

invalidsun@bernahl:~$ iperf3 -c 192.168.1.1
Connecting to host 192.168.1.1, port 5201
[  5] local 192.168.1.12 port 42282 connected to 192.168.1.1 port 5201
[ ID] Interval           Transfer     Bitrate         Retr  Cwnd
[  5]   0.00-1.00   sec  92.8 MBytes   778 Mbits/sec    0    425 KBytes       
[  5]   1.00-2.00   sec  90.1 MBytes   756 Mbits/sec    0    449 KBytes       
[  5]   2.00-3.00   sec  89.5 MBytes   751 Mbits/sec    0    496 KBytes       
[  5]   3.00-4.00   sec  90.4 MBytes   758 Mbits/sec    0    496 KBytes       
[  5]   4.00-5.00   sec  91.9 MBytes   771 Mbits/sec    0    523 KBytes       
[  5]   5.00-6.00   sec  92.4 MBytes   775 Mbits/sec    0    556 KBytes       
[  5]   6.00-7.00   sec  90.9 MBytes   762 Mbits/sec    0    556 KBytes       
[  5]   7.00-8.00   sec  90.8 MBytes   761 Mbits/sec    0    556 KBytes       
[  5]   8.00-9.00   sec  91.0 MBytes   763 Mbits/sec    0    623 KBytes       
[  5]   9.00-10.00  sec  85.6 MBytes   718 Mbits/sec    0    623 KBytes       
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bitrate         Retr
[  5]   0.00-10.00  sec   905 MBytes   759 Mbits/sec    0             sender
[  5]   0.00-10.04  sec   902 MBytes   753 Mbits/sec                  receiver


iperf Done.

```

A short while after posting this, I did find a minor solution that made it start receiving at 200 mbps consistently. For those that might be having a similar issue, I'll put that here.
```
sudo vi /etc/NetworkManager/NetworkManager.conf
```
```

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false    **<--- Change this to true**

```
```

sudo service NetworkManager restart

```

---

### Post by invalidsun on 2024-06-24
> [COLOR=#000000]How are you connecting to the Internet? Is there a firewall appliance on the gateway?[/COLOR]

Directly to the primary router with a 3ft cat6 cable. No firewall.

---

### Post by currentshaft on 2024-06-24
Does that router have an interface you can access, to inspect and change settings, such as QoS and potential filtering taking place?

---

