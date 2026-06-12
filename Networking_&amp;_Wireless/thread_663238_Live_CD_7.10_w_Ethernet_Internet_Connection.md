---
title: "Live CD 7.10 w/ Ethernet Internet Connection"
date: 2008-01-09
forum: Networking &amp; Wireless
---

### Post by Eriol-kun on 2008-01-09
Hello, I'm new to the forums and to Ubuntu itself.

So far so good with it; I've tried other distros but Ubuntu is by far my favorite. I mainly use live distros for troubleshooting, like now.

The problem is, I'd like to be able to connect Ubuntu to the internet using the Live CD. A couple of questions arise from here:

1) Is this possible?
2) If it is, what steps are needed to be able to configure a connection?
3) Specifically, can a Static IP connection with 2 DNS servers be applied to the live CD?

Basically, what I'm trying to do is to troubleshoot/recover files from a laptop (a pretty old Presario 2000M) but I'd also like to connect it to the internet for comodity issues (e.g. Downloading RAR for Ubuntu to be able to read/split files for recovery is my final goal). Right now I'm using another box (Windows) to access the internet.

I've tried to compile some info that I might need. I'm a total newbie to the Linux/Ubuntu ambience, being someone who grew up with Windows 3.11 when I was like 5. Anyways:

*About the internet connection:*
ISP distributed a Modem/Router/Machine with the Internet Service (I believe it is PPPoE), specifically a Paradyne 6212-I2-200-0PA. It seems it is a connection with a range of static IPs; I'll try with one I know that works. DHCP doesn't work in Windows either, so it has to be configured manually.

As for what I'd like to input in this config, is the following:

> IP Address: 201.227.94.180
Subnet Mask: 255.255.255.0
Gateway: 201.227.94.177
DNS Servers (2): 201.225.225.225, 201.224.73.162

I also ran *sudo lshw* and got what I thought was pertinent to the connection:

> *-network:0
description: Ethernet interface
product: RTL-8139/8139C/8139C+
vendor: Realtek Semiconductior Co., Ltd.
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0
version: 10
serial: 00:c0:9f:b4:f6:ab
size: 100MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt autonegotiation
configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s

If you need anything else please state it and I'll try to get it. I hope that with this info it is sufficient for a solution. Thanks for your patience and time in reading this, and thanks for the help as well, in advance.

---

### Post by pebo on 2008-01-10
No reason why not. The RTL-8139 card should be automatically detected by the live cd and the driver loaded. You can check using```
lsmod | more
```From the menu go System=>Administration=>Network and set your configuration
Good luck:)

---

