---
title: "Hopeless Idiot Can't Operate Wired Network Connection in Ubuntu 6.10"
date: 2006-11-07
forum: Networking &amp; Wireless
---

### Post by thecritick on 2006-11-07
I've installed Ubuntu 6.10 on a machine that previously networked successfully, but now it doesn't connect with my router or any other computer. Please help! I'm a total beginner, but I can't learn anything about the system because I can't get the machine online in the first place!

The ethernet card (192.168.1.2) is properly cabled to the router - and I can't get any connection to it using DHCP.

With DHCP, all the Network Interface reports are "not available". I've tried a lot of things but none of them have made the slightest bit of difference. I also can't find a walk-through that solves the problems.

Can anyone point me in a useful direction?

---

### Post by SoggyCornflake on 2006-11-07
First try typing in a command line ```
ifconfig
```
That command will return all the status of your ethernet devices.  It may help people diagnose problems if you could post results.

> The ethernet card (192.168.1.2) is properly cabled to the router - and I can't get any connection to it using DHCP.


I'm not sure I follow what You're saying here.  Is 192.168.1.2 the IP address of your computer when You're booted into Windows? or is it the IP address of the router?

> With DHCP, all the Network Interface reports are "not available". I've tried a lot of things but none of them have made the slightest bit of difference. I also can't find a walk-through that solves the problems.
Have you tried a hard coded IP address?  If you have a small personal network you could get away with this approach.  If you're connecting to a corporate network that probably won't be a good idea. If you do decide to go that route, you need to know the subnet mask and the gateway address your router uses.

---

### Post by MrWhiteKeys on 2006-11-07
if ifconfig doesn't work try typing in the command line:

sudo dhclient

---

### Post by thecritick on 2006-11-07
Yeah, this is inefficient because I have to write it all out and type it all in again on another computer, so there may be copying errors. My router is 192.168.1.2. My computer is set to IP 192.168.1.101, which should be free on the network.

I get the following results from ifconfig:

eth0

Link encap: Ethernet HWaddr 00:10:4B:C3:B0
inet addr: 192.168.1.101 Bcast: 192.168.1.255 Mask: 255.255.255.0

UP BROADCAST MULTICAST MTU:1500 Metric: 1
RX Packets: 0 errors: 0 dropped: 0 overruns: 0 frame: 0
TX Packets: 0 errors: 0 dropped: 0 overruns: 0 carrier: 0
collisions: 0 txqueuelen: 1000
RX Bytes: 0 (0.0b) TX Bytes: 0 (0.0b)
Interrupt: 11 Base address: 0x1400


l0 is clearly different...

---

### Post by Iowan on 2006-11-07
What's in the **/etc/network/interfaces** file? With the hard-coded address, you *should* see results from ```
ping 192.168.1.2
```

---

### Post by thecritick on 2006-11-08
etc/network/interfaces file says:

auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.1.101
netmask 255.255.255.0
gateway 192.168.1.2

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto eth0

--

Pinging results in:
From 192.168.1.101 cmp_seq=n Destination Host Unreachable

---

### Post by stream303 on 2006-11-13
Just for grins, have your tried setting up your Ubuntu box in dhcp mode rather than static.  (check the properties box in System > Administration > Networking > highlight card > properties > enable connection > dhcp)

Let's see if this gets you off the ground - we can switch back to static later if this works...

---

### Post by thecritick on 2006-11-14
I've tried that now. Pinging 192.168.1.2 gives me the following response:

connect: Network is unreachable

---

### Post by thecritick on 2006-11-14
And from ifconfig, the following:

eth0

Link encap: Ethernet HWaddr 00:10:4B:C3:B0
inet addr: 192.168.1.101 Bcast: 192.168.1.255 Mask: 255.255.255.0

UP BROADCAST MULTICAST MTU:1500 Metric: 1
RX Packets: 0 errors: 0 dropped: 0 overruns: 0 frame: 0
TX Packets: 1 errors: 0 dropped: 0 overruns: 0 carrier: 1
collisions: 0 txqueuelen: 1000
RX Bytes: 0 (0.0b) TX Bytes: 60 (60.0b)
Interrupt: 11 Base address: 0x1400

This is different (why?) from what I had with manual config, but needless to say it still doesn't work.

---

