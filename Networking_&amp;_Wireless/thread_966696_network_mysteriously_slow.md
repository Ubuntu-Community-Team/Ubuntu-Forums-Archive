---
title: "network mysteriously slow"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by shortridge11 on 2008-11-01
i've got a home server hooked up to my home network.  My network is set up like so: internet through router, router to gig switch, all machines are on the gig switch.  I'm getting really slow speeds on my network though, and i can't figure it out.  Even doing things like connecting to my server through ssh can take up to 15 seconds.  I know this isn't normal...any suggestions to why this would be happening? or any way to diagnose the problem? I'm running 8.10 on 1 of the machines in my house, and 8.04 on my server, and windows on the other 2.

---

### Post by shortridge11 on 2008-11-03
I'm going to post the output of iperf and ethtool as soon as possible. Any other suggestions on how to test my wired network speed would be very welcome.

---

### Post by puppywhacker on 2008-11-03
Hi,

my suggestion would be to use mii-tool, tcpdump and ssh -v ...

sudo mii-tool
sudo tcpdump -i eth0 -v
or save it to the network
sudo tcpdump -i eth0 -w /tmp/slownetwork.pcap

When you say ssh connects slow, use the verbose debugging to show where it is slow.
ssh -v otherhost

slow network can be caused by anything, like ipv6 routing while you don't use ipv6, routing over a slow path, like out over the internet and back. wrong MTU settings, network saturation by looping ip-traffic, network interface cards not auto negotiating properly, some process conflicting with the network interface. bad physical cables, bad chipsets, not the correct driver, no DMA activated. firewall rules. bad nameservers ...

The list goes on and on ... so it's hard to determine without too much debug information.

sudo tcpdump -i eth0 -w /tmp/slownetwork.pcap
and break it with CTRL+C
Use wireshark to analyze your network traffic, you only need to trace a few seconds worth of traffic and not more than 100packets.

anyway goodluck

---

### Post by shortridge11 on 2008-11-03
awesome. That gives me a new direction to go.  Well, i fixed my ssh problem, apparently my my DNS was doing a reverse lookup, and that adds a lot of time so i edited my sshd.config file and added a line that turned that off.  I'll post anything else i find though. I really appreciate the help!

---

