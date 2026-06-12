---
title: "inconsistent wireless"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by The Foss on 2007-03-01
I am absolutely stumped as to why my wireless access won't work, and I need some assistance. The symptoms are very inconsistent, which is making it hard to diagnose.

The problem is with my personal desktop, Maverick. It has a Broadcom wireless card that I've used very successfully in the past. Maverick became a Linux machine in January- before that it ran Windows, and I never had any problems with network access, so I know the problem is not with the hardware. There are ten other machines connected to the network, nine PCs and a Mac, none of which have ever had a problem, so I'm fairly certain the network is not the issue.

Sometimes Maverick can connect to the network, and sometimes it can't. Unfortunately, that's about as clear as I can be. Sometimes I boot him up, and he connects just fine for a while, and then refuses to see the network. Sometimes he'll see the internal network, but refuse to connect to the Internet. (that's what he's doing now- I can browse files on the network, but can't access anything outside of it.) Sometimes he just won't connect at all.

On occasion, I can fix the problem by running ifdown and then ifup. However, that doesn't always work.

We use a set of static IPs on our network- 90 to 99 upstairs, 100 to 109 downstairs. Maverick is currently 192.168.1.91. 

This is the output from iwconfig:
eth0 IEEE 802.11b/g  ESSID:"linksys"  Nickname:"Broadcom 4318"
       Mode: Managed  Frequency: 2.437 GHz  Access Point: 00:14:BF:7D:9E:1B
       Bit Rate=11 Mb/s  Tx-Power=18 dBm
       RTS thr:off  Fragment thr:off
       Link Quality:23/100  Signal level=-83 dBm  Noise level=-73 dBm
       Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
       Tx excessive retries:0  Invalid misc:0  Missed beacon:0

Any thoughts?

---

### Post by tgalati4 on 2007-03-01
Here's a guess.  The windows driver activates Broadcom's proprietary signal circuitry that handles errors and poor signal quality.  This gives you a more reliable link than you would expect.

The Linux driver is probably a plain-jane, turn the radio on, send and receive packets.  Because the Broadcom chipset is proprietary and has not been released for any Linux development, the driver is a reverse-engineered, black box driver.

Have you tried the ndiswrapper that uses the window's driver under Linux?

Because wireless cards have come down in price, sometimes it is easier to switch to something more Linux friendly than it is to fight with proprietary drivers.

The other thing you can do is make sure you have good antenna placement that is away from other equipment.  Sometimes a larger antenna or "coffee can" antenna can help your reception.

Good luck!

Oh, and welcome to the community.

---

