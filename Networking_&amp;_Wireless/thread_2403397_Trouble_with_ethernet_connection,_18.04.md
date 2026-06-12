---
title: "Trouble with ethernet connection, 18.04"
date: 2018-10-10
forum: Networking &amp; Wireless
---

### Post by James_Creasy on 2018-10-10
Having trouble getting the ethernet connection to work on one of my Ubuntu machines following my gigabit fiber installation. It works on one machine and not the other

**Not working:** 
I plug in the cable to the Surface Laptop dock, and I see a light there. Ubuntu 18.04. 

Does not switch to the wired connection and I can't find where to select in the UI.

I'm following the Ubuntu documentation here: [https://help.ubuntu.com/stable/ubuntu-help/net-manual.html.en](https://help.ubuntu.com/stable/ubuntu-help/net-manual.html.en)

But the instructions don't seem to match the dialog I see. (see attachment)

I looked a few answers about setting up an ethernet connection but could not get it to work. 

**Working:**
 Plugged the cable into my Ubuntu 16.04 machine and it switched over to the wired connection automatically. 


I get only about 150mbps on the wifi, and 945mbps on the wired connection so I really want to get it to work. 


$ sudo lshw -C network
  *-network                 
       description: Wireless interface
       product: 88W8897 [AVASTAR] 802.11ac Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 00
       serial: c4:9d:ed:a8:15:51
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=mwifiex_pcie ip=192.168.86.176 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:132 memory:a1500000-a15fffff memory:a1400000-a14fffff
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: docker0
       serial: 02:42:12:c2:18:e1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=172.17.0.1 link=no multicast=yes

$ lspci | grep -i net
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88W8897 [AVASTAR] 802.11ac Wireless

---

### Post by NM5TF on 2018-10-10
open a terminal and type

```
ip link
```

post the output & use code tags please...

---

### Post by James_Creasy on 2018-10-10
```
$ ip link
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: wlp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP mode DORMANT group default qlen 1000
    link/ether c4:9d:ed:a8:15:51 brd ff:ff:ff:ff:ff:ff
3: docker0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN mode DEFAULT group default 
    link/ether 02:42:69:52:87:af brd ff:ff:ff:ff:ff:ff
4: enxbc8385f72540: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP mode DEFAULT group default qlen 1000
    link/ether bc:83:85:f7:25:40 brd ff:ff:ff:ff:ff:ff
```

---

### Post by James_Creasy on 2018-10-10
Based on that output I added this to the interfaces file

[FONT=courier new]auto enxbc8385f72540[/FONT]
[FONT=courier new]iface enxbc8385f72540 inet dhcp

[FONT=arial]and did:[/FONT]

sudo ifup enxbc8385f72540

[FONT=arial]and success! Thanks! (edited: premature, did not work on reboot, see below)[/FONT]









[/FONT]

---

### Post by NM5TF on 2018-10-11
Great news !!!

now if you could mark the thread SOLVED so others can use the information, it would be great

tommy

---

### Post by James_Creasy on 2018-10-11
Thanks for the reminder. Somehow, and somewhat ironically, the SSO for this forum has bifurcated my logins so I have a different one on each machine. Could not find the Solved option until I figured that out.

---

### Post by wildmanne39 on 2018-10-11
> the SSO for this forum has bifurcated my logins so I have a different one on each machine. Could not find the Solved option until I figured that out. 
Do you mean you have a different username depending which machine you login on? If so please start a thread in the Resolution Centre and we will work on fixing the issue.

[https://ubuntuforums.org/forumdisplay.php?f=123](https://ubuntuforums.org/forumdisplay.php?f=123)

---

### Post by James_Creasy on 2018-10-11
I just marked the thread unsolved because today when I booted the machine,

```
ip link
```
no longer shows my Ethernet interface. There is still a missing piece to this puzzle.

```
$ sudo ifup enxbc8385f72540
Internet Systems Consortium DHCP Client 4.3.5
Copyright 2004-2016 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Cannot find device "enxbc8385f72540"
Error getting hardware address for "enxbc8385f72540": No such device

If you think you have received this message due to a bug rather
than a configuration issue please read the section on submitting
bugs on either our web page at [www.isc.org]("http://www.isc.org") or in the README file
before submitting a bug.  These pages explain the proper
process and the information we find helpful for debugging..

exiting.
Failed to bring up enxbc8385f72540.
```

---

### Post by wildmanne39 on 2018-10-11
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by James_Creasy on 2018-10-11
Is that better? Thanks for the tips, did not find the code tags prior.

---

### Post by wildmanne39 on 2018-10-11
Your welcome and looks good!

---

### Post by NM5TF on 2018-10-11
what is the output of

```
inxi -N
```

almost sounds like a hardware failure starting to happen...

tommy

---

### Post by James_Creasy on 2018-10-15
```
$ inxi -N
Network:   Card: Marvell 88W8897 [AVASTAR] 802.11ac Wireless driver: mwifiex_pcie
```

I've discovered that *sometimes* I can get the ethernet interface to show up on 'ip link' by disconnecting the dock connector from the laptop and reconnecting it. Not consistent though. I've repro'd this on two different dock connectors, one at home and one at the office.

---

### Post by heynnema on 2018-10-16
If you're running on a SSD, you run the risk of things  booting faster than the network is coming online and then you'll need to modify the following file: `/etc/systemd/system/network-online.target.wants/NetworkManager-wait-online.service`

```
[Unit]
Description=Network Manager Wait Online
Documentation=man:nm-online(1)
Requires=NetworkManager.service
After=NetworkManager.service
Before=network-online.target

[Service]
Type=oneshot
ExecStart=/usr/bin/nm-online -s -q --timeout=60
RemainAfterExit=yes

[Install]
WantedBy=network-online.target

```
and change the timeout from `30` to `60`.

update: this doesn't fix the problem... sigh... a newer kernel does :-)

---

### Post by James_Creasy on 2018-10-17
I changed the timeout to 60 as suggested, the ethernet interface is still not visible:

```
$ inxi -N
Network:   Card: Marvell 88W8897 [AVASTAR] 802.11ac Wireless
           driver: mwifiex_pcie
```

I then disconnected and reconnected the dock connector on the laptop, now 'ip link' shows the ethernet interface:

```
$ ip link1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: wlp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP mode DORMANT group default qlen 1000
    link/ether c4:9d:ed:a8:15:51 brd ff:ff:ff:ff:ff:ff
3: docker0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN mode DEFAULT group default 
    link/ether 02:42:41:4e:0f:80 brd ff:ff:ff:ff:ff:ff
4: enxbc8385f72540: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN mode DEFAULT group default qlen 1000
    link/ether bc:83:85:f7:25:40 brd ff:ff:ff:ff:ff:ff
```

I added this new id to the /etc/network/interfaces file and ran 'ifup':

```
$ sudo ifup enxbc8385f72540
Internet Systems Consortium DHCP Client 4.3.5
Copyright 2004-2016 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/


Listening on LPF/enxbc8385f72540/bc:83:85:f7:25:40
Sending on   LPF/enxbc8385f72540/bc:83:85:f7:25:40
Sending on   Socket/fallback
DHCPDISCOVER on enxbc8385f72540 to 255.255.255.255 port 67 interval 3 (xid=0x2b48a007)
DHCPDISCOVER on enxbc8385f72540 to 255.255.255.255 port 67 interval 4 (xid=0x2b48a007)
<snipped more DHCPDISCOVER...>

No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

Not yet working.

---

### Post by heynnema on 2018-10-22
Turns out that my previous post about changing a timeout value doesn't fix the problem. I've been banging my head against the wall with this problem for weeks. I had checked everything. NetworkManager. Netplan. Now... here it comes... this problem originally showed up in kernel -29, and was still present with kernel -36. I just upgraded from 18.04 to 18.10, and I haven't seen the problem again! Kernel problem.

---

### Post by James_Creasy on 2018-10-29
I will definitely try that when I get home today, thanks!

I had given up and switched to a Dell since that seemed to work fine with 18.04.

---

