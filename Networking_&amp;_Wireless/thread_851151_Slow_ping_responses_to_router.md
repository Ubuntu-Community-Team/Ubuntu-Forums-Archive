---
title: "Slow ping responses to router"
date: 2008-07-06
forum: Networking &amp; Wireless
---

### Post by tobycatlin on 2008-07-06
Hello everybody,

I have been running the same hardware since Dapper and the wifi card i have has always worked. The card is unbranded (I think it has a texas instruments chipset) and i have always thought its a testament to ubuntu that it does work without serious messing around.

When i upgraded to Hardy it stopped connecting to my network. It seemed that the DHCP did not work. I manually set all the config attributes and i can connect to my router now. The network manager crashes in roaming mode but this isn't the main problem. Network traffic is very slow and after a couple of traceroutes i noticed that the ping responses from my router are slow.

toby@media-box:~/projects$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=255 time=2096 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=255 time=1096 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=255 time=97.2 ms
64 bytes from 192.168.0.1: icmp_seq=4 ttl=255 time=2042 ms
64 bytes from 192.168.0.1: icmp_seq=5 ttl=255 time=1045 ms
64 bytes from 192.168.0.1: icmp_seq=6 ttl=255 time=48.5 ms
64 bytes from 192.168.0.1: icmp_seq=7 ttl=255 time=2076 ms
64 bytes from 192.168.0.1: icmp_seq=8 ttl=255 time=1067 ms
64 bytes from 192.168.0.1: icmp_seq=9 ttl=255 time=69.9 ms
64 bytes from 192.168.0.1: icmp_seq=10 ttl=255 time=2213 ms
64 bytes from 192.168.0.1: icmp_seq=11 ttl=255 time=1215 ms
64 bytes from 192.168.0.1: icmp_seq=12 ttl=255 time=216 ms

--- 192.168.0.1 ping statistics ---
13 packets transmitted, 12 received, 7% packet loss, time 12006ms
rtt min/avg/max/mdev = 48.545/1107.222/2213.817/818.784 ms, pipe 3
toby@media-box:~/projects$ 

My laptop returns a ping in less than a 1ms so it must be something to do with my setup. I am guessing the wifi card driver. I guess it is running under some generic driver and i could improve things dramatically if i had the right one.

I have looked at many wifi troubleshooting pages but can't get this sorted, any help would be very much appreciated.

thanks
toby

---

### Post by tobycatlin on 2008-07-06
output from:
sudo lshw -C network

  *-network:0             
       description: Wireless interface
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: wlan0
       version: 00
       serial: 00:12:0e:12:9d:ee
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=acx_pci ip=192.168.0.2 latency=64 module=acx multicast=yes wireless=IEEE 802.11b+/g+

---

### Post by rothloup on 2011-09-23
I realize that this is an old thread, but it seems to be the only thread I can find that represents the same problem that I am having.

I just bought a Dell XPS and installed Ubuntu 11.04.  The wireless connection is nearly unusable.  When I started troubleshooting, I got a ping times that were similar to yours.  The most interesting thing I saw was that the ping times have a pattern to them - they start out at a high number (i.e. 3691 ms in the first line below), then decrease by 1000 ms with each packet.  When it hits zero, the pattern starts over with another very high ping time.  It almost looks like the packets are getting stuck in a buffer somewhere. I noticed that your ping times have the same pattern.

Did you ever solve your problem?  I am at a loss for what to do.  I have already tried the more common solutions, like disabling the wireless-N.

The wireless card is a Centrino Advanced-N 6230.

Any help from anyone would be appreciated!

rothloup@rons-linux-XPS:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_req=1 ttl=64 time=3691 ms
64 bytes from 192.168.1.1: icmp_req=2 ttl=64 time=2692 ms
64 bytes from 192.168.1.1: icmp_req=3 ttl=64 time=1692 ms
64 bytes from 192.168.1.1: icmp_req=4 ttl=64 time=692 ms
64 bytes from 192.168.1.1: icmp_req=5 ttl=64 time=7003 ms
64 bytes from 192.168.1.1: icmp_req=6 ttl=64 time=6003 ms
64 bytes from 192.168.1.1: icmp_req=7 ttl=64 time=5004 ms
64 bytes from 192.168.1.1: icmp_req=8 ttl=64 time=4004 ms
64 bytes from 192.168.1.1: icmp_req=9 ttl=64 time=3004 ms
64 bytes from 192.168.1.1: icmp_req=10 ttl=64 time=2004 ms
64 bytes from 192.168.1.1: icmp_req=11 ttl=64 time=1004 ms
64 bytes from 192.168.1.1: icmp_req=12 ttl=64 time=4.58 ms
^C
--- 192.168.1.1 ping statistics ---
13 packets transmitted, 12 received, 7% packet loss, time 12000ms
rtt min/avg/max/mdev = 4.587/3066.837/7003.950/2073.215 ms, pipe 8

---

