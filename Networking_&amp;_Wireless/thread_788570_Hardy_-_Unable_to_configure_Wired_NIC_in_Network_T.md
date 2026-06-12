---
title: "Hardy - Unable to configure Wired NIC in Network Tools"
date: 2008-05-09
forum: Networking &amp; Wireless
---

### Post by CMKRNL on 2008-05-09
I have a 3CSOHO100B-TX 910-A01 wired NIC connected to a cable modem through an old Linksys BEFSR4 router that is working, but slowly. By slowly I mean that when I update my system, I see download speeds of 40 - 50kb/sec. I previously had 7.04 installed and usually saw download speeds > 110kb/sec.

When I reboot into Windows XP and download files, like the 8.04 .iso, I get 3-400kb/sec.

When I go into Network Tools and select eth0 and IPV4 and click configure, I get prompted for my password and then this message is displayed:

The interface does not exist. Check that it is correctly typed and that it is correctly supported by your system.

The only other interface is the loopback interface and I have no other NICs on the computer, so if eth0 doesn't exist, why do I have network connectivity?

Shouldn't I be able to configure the eth0 interface?

I'm wondering if the tulip driver is putting the NIC into half duplex mode or something else that is causing it to run slow.

lshw -C network output is:
  *-network               
       description: Ethernet interface
       product: 3CSOHO100B-TX 910-A01 [tulip]
       vendor: 3Com Corporation
       physical id: c
       bus info: pci@0000:00:0c.0
       logical name: eth0
       version: 31
       serial: 00:04:75:b5:3f:0a
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 ip=192.168.1.100 latency=32 maxlatency=128 mingnt=64 module=tulip multicast=yes

Bob

---

### Post by dmallery on 2008-05-13
hi

i have this problem on two machines: amd64 and i386, dapper and hardy.  my isp can plug his xp laptop in and get 100kB+ while i can only get 8-28kBps on the same connection.  the link is a 5.8Ghz "wifi" connecting over about 15 miles.  the physical connection for the test is direct to the radio.  no routers/ switches in line. (not that they make any difference.)  the ethernet is at 100.  i have no problem with network tools.

this has been going on for a long time.  i gave up downloading releases.  it's time for a fix.

any ideas would be welcome.

thanks

dave mallery

---

