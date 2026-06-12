---
title: "Intel 82547GI Gigabit and Fiesty"
date: 2007-09-23
forum: Networking &amp; Wireless
---

### Post by keoie on 2007-09-23
Hi all, 

I have just install Ubuntu 7.04 and have extremely low internet speeds as compared to a Windows XP build on the same machine.

The machine has the Abit IC7-Max 3 motherboard.

The output of lspci -nn reads:
02:01.0 Ethernet controller [0200]: Intel Corporation 82547GI Gigabit Ethernet Controller [8086:1075]

The output of ethtool eth0 reads:

Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  Not reported
        Advertised auto-negotiation: No
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: off
        Supports Wake-on: umbg
        Wake-on: g
        Current message level: 0x00000007 (7)
        Link detected: yes

I'm connected to the internet via Cisco switch with has its ports hard coded to 100/full. 

Any ideas of how to increase network speeds? 

TIA!!!

---

### Post by noob12 on 2007-09-23
Looks like you manually forced it to 100mbps too.  Did it not autonegotiate successfully?  

When you say slow network speeds, what are you using to measure it?    I've seen really slow behavior in Samba through Nautilus even when iperf and other tools show good rates and when access through direct cifs/smbfs mounts are fast.

Are you seeing any errors in tail /var/log/kern.log or dmesg?

You might also try building the latest Intel driver and seeing if things improve.

---

### Post by keoie on 2007-09-23
I've never been a  big fan of autonegotiate with Cisco networking equipment. I've seen it not work too many times.

There are no error messages in the kern.log....

I'm using [www.speedtest.net](www.speedtest.net) to check downloads and uploads. In the Windows XP build (same machine) I get speeds of:

[[IMG]http://www.speedtest.net/result/186733126.png[/IMG]](http://www.speedtest.net)

With Ubuntu, I get:

[[IMG]http://www.speedtest.net/result/186820042.png[/IMG]](http://www.speedtest.net)

Let me try the latest intel driver and see what happens.

Thanks!

---

### Post by noob12 on 2007-09-23
Going over the WAN introduces a lot more variables.    Try doing local tests using say iperf.

I'm not familiar with that test tool, but it may be interacting poorly with the TCP window control algorithm.  How long do you run the test?

I'm not at all confident that this is a driver issue at all, so not sure you are going to see any improvement with updated ones.  That said, no harm in trying.  Backup your original drivers.

---

### Post by keoie on 2007-09-23
I've run a few other tests:

[http://miranda.ctd.anl.gov:7123/](http://miranda.ctd.anl.gov:7123/)

running 10s outbound test (client to server) . . . . . 93.41Kb/s
running 10s inbound test (server to client) . . . . . . 209.31kb/s
Your Workstation is connected to a Dial-up Modem
Alarm: Duplex Mismatch condition detected Switch=half and Host=full (this is totally false... I've checked the settings on the switch and eth0, both hard coded to 100 Full)

and

[http://kirana.psc.edu/NPAD/](http://kirana.psc.edu/NPAD/) - The output is entirely too large to post here ;-)

They both come up with the same results as the previous test. 

One other item, the nic is built into the motherboard.

I'm wondering if the eth0 settings are restricting the bandwidth somehow. I'm getting about 30% of the bandwidth that I should be getting. As I'm a total newb when it comes to configuring network adapters in Ubuntu/Linux, is there a guide out there that I can use to assist me?

---

