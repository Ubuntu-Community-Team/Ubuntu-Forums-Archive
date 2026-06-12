---
title: "Slow upload speeds to ubuntu"
date: 2008-10-26
forum: Networking &amp; Wireless
---

### Post by Shwick2 on 2008-10-26
I have a home network set up with ubuntu 8.04 as the gateway and a windows pc on the lan.  When I try to upload a file to ubuntu I get slow speeds.

smbget from linux: 200kb/s
sftp put from windows: 100kb/s
pscp put from windows: 35 kb/s
ftp put from windows: 856.71Kbytes/s

I have no problems downloading from ubuntu to windows.  I get 11.2 MB/s, which I'm quite happy about as the theoretical limit for a 100 Mbit connection is 12.5 MB/s.  I get 11.2 MB/s with Windows File Sharing, sftp, pscp and ftp.

This is the result of sudo lshw for the card facing into my network.

```

           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth1
                version: 10
                serial: 00:08:54:dd:35:c4
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.1 latency=64 link=yes maxlatency=64 mingnt=32 module
=8139too multicast=yes port=MII speed=100MB/s

```

---

### Post by Shwick2 on 2008-10-31
Anyone have a problem like this before?  I'm sort of stumped and don't know how to proceed.  Maybe the Windows PC's onboard gigabit lan autonegotiated itself to 100Mbit/s down 10Mbit/s up?  How do I determine the autonegotiated lan card duplex speed?

---

### Post by Shwick2 on 2008-11-04
I looked around the net and couldn't find an easy way to determine how to get a Windows NIC to report what it's auto-negotiated speed was.  

I found out you could check the event logs, Control Panel -> Administrative Tools -> Event Viewer -> System.  I found events with source "yukonwxp" that said,

"Port A is up with 100 Mbps"
"Duplex State is Full Duplex"
"Pause Function is Rx and TX"

So my linux and windows machines are both configured with 100 Mbps Full Duplex.  I'm not 100% convinced for windows, I need an app that tells me.

I'm beginning to think this is something weird like my $15 Dynex switch is somehow limiting data to the soure PC to 10 Mbps... but that doesn't sound realistic.

---

