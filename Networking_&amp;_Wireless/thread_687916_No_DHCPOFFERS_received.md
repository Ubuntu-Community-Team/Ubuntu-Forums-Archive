---
title: "No DHCPOFFERS received"
date: 2008-02-04
forum: Networking &amp; Wireless
---

### Post by ThatBuddykid on 2008-02-04
Hi I'm new to the forums and linux in general. I Just installed Ubuntu Dapper Drake (6.06.1 LTS) on a new computer. All I had in the way of an internet card was my Net Gear WG121 usb v2 so I popped it in to the usb port but the nothing seemed to happen on the computer side (the device itself lit up both the connected to usb and the connected to wireless green lights). I then tried to install the drivers from the cd but alas they didn't support linux but the open source community of coarse had a fix for this, ndiswrapper which I successfully installed and got it to recognize the device (Hardware present: Yes). I then went to configure it and couldn't quite get it to connect using the networking GUI even though I put in the correct ESSID. So I looked around and read a ton of documentation and found a guide to configuring the wireless connection via the Terminal. What ever guide i used I got the following result when it should of connected

Listening on LPF/eth1/00:09:5b:a2:e7:50
Sending on     LPF/eth1/00:09:5b:a2:e7:50
Sending on     Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
xxxx@xxxx-xxxx:~$

I've tried everything I can think of and done a lot of research but I can't seem to figure this one out so help me if you can and thanks so much in advance.

PS. I <3 Linux and Ubuntu

---

### Post by wieman01 on 2008-02-05
Please post the following:
> sudo iwlist scan
> sudo lshw -C network
> sudo cat /etc/network/interfaces
> sudo ndiswrapper -l
> sudo iwconfig

---

