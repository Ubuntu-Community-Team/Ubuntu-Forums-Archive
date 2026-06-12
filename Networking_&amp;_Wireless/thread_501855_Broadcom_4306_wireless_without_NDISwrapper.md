---
title: "Broadcom 4306 wireless without NDISwrapper"
date: 2007-07-15
forum: Networking &amp; Wireless
---

### Post by Mark Phelps on 2007-07-15
I'm trying to get my HP laptop working without installing NDISwrapper (I know, that's how EVERYONE else is doing it, but I've spend two days downloading and installing every bcmwl5 driver I could find, and nothing works. And, yes, I read all 62 pages of the thread and tried every option listed.  At the end, I did have a wlan0 network, but any attempt to scan with it produced a "no networks found" result. And, yes, I tried with and without WEP -- same results.  Presuming that maybe the wireless router was simply down, I rebooted back into Windows and voila! wireless network came up right away.

So now, it's back to Kubuntu on the laptop to try again.

I'm trying to do this in Kubuntu simply by editing the various system files and restarting the network.

Since I'm not using NDISwrapper, I'm also not using wlan0, but instead, eth0 and eth1.  My lshw -C network yields the following:
============================
t@ubuntu:~# lshw -C network
  *-network:0 DISABLED
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@00:09.0
       logical name: eth1
       version: 02
       serial: 00:90:4b:46:26:92
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-15-generic latency=64 link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:d0002000-d0003fff irq:10
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 00
       serial: 00:0d:9d:89:02:b7
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=full ip=192.168.0.111 latency=90 link=yes maxlatency=52 mingnt=11 multicast=yes port=twisted pair speed=100MB/s
       resources: ioport:2400-24ff iomemory:d0006000-d0006fff irq:10
=====================
my /etc/network/interfaces has the following:
======================
root@ubuntu:~# cat /etc/network/interfaces
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid XXXXXXXX
wireless-key XXXXXXXXX

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp
#wireless-essid XXXXXXXXX
#wireless-key XXXXXXXXX
root@ubuntu:~#                      
========================
BTW, the essid and key are not really "X"s

/etc/iftab has the following:
=========================
eth1 mac 00:90:4b:46:26:92
=========================
Yes, this the correct Mac address. You can check that agains the output of lshw above.

Results of ifdown -a; followed by ifup -a
==================
oot@ubuntu:~# ifdown -a
There is already a pid file /var/run/dhclient.eth0.pid with pid 10855
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:0d:9d:89:02:b7
Sending on   LPF/eth0/00:0d:9d:89:02:b7
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 67
root@ubuntu:~# ifup -a
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:0d:9d:89:02:b7
Sending on   LPF/eth0/00:0d:9d:89:02:b7
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 192.168.0.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.111 -- renewal in 37145 seconds.
SIOCSIFFLAGS: No such file or directory
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
Listening on LPF/eth1/00:90:4b:46:26:92
Sending on   LPF/eth1/00:90:4b:46:26:92
Sending on   Socket/fallback
receive_packet failed on eth1: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
RTNETLINK answers: Network is down
run-parts: /etc/network/if-up.d/avahi-autoipd exited with return code 2
root@ubuntu:~#       
==================
Problem is that NOTHING will enable the wireless network!  I've tried clicking the network icon, opening the applet, and enabling the network.  It just times out.

Here's the results of iwconfig:
===================
root@ubuntu:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"XXXXXXXX"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid
          RTS thr:off   Fragment thr:off
          Encryption key:XXXXXXXXX   Security mode:open
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@ubuntu:~#      
===================
Again, the real essid and WEP key are not "X"s.

The command iwlist eth1 scan yields the error message "eth1, interface doesn't support scanning : No such device".

Results of dhclient essid:
===================
root@ubuntu:~# dhclient essid XXXXXXXX
There is already a pid file /var/run/dhclient.pid with pid 11273
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
XXXXXXXX: ERROR while getting interface flags: No such device
XXXXXXXX: ERROR while getting interface flags: No such device
SIOCSIFADDR: No such device
essid: ERROR while getting interface flags: No such device
essid: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
root@ubuntu:~#    
===================

What is making this a real challenge is that I'm doing this all from a liveCD booting Kubuntu 7.04.  I'm trying to get the wireless working on a Windows laptop so I can remove Windows and replace it with some derivative of UBuntu.  I've tried the "Broadcom 4306 with Ndiswrapper" stuff booting into Ubunto Gnome, but that doesn't work (see the beginning of this post).  I've tried booting with Kubuntu -- and now, that doesn't work, either.

I installed the wlassistant, but it finds no networks -- and I know that at least four are within range of my laptop at home, including my secure network whose WAP is only 20 feet away.

I've also read about modifying the firmware with a bcm43ss installation -- but I don't want to break the windows installation.  I need something to work in wireless mode.

Anyone have any ideas about anything else I could try?  Anything else I can post here that would help isolate the problem?

---

### Post by El Viejo Lobo on 2007-07-15
I have been in this nightmare myself with Broadcom 4318 I am not sure if I can help you but I will give you all my bookmarks about this issue. I hope that you will get something good of it.
[http://del.icio.us/yigal_lupo/broadcom](http://del.icio.us/yigal_lupo/broadcom)

---

### Post by James.Dedon on 2007-07-15
I got my Broadcom 4306 up and running in a flash by just using the bcm43xx-fwcutter.  You can download it from the debian site that comes up with a google search.  You need to have the computer hooked up to a wired connection when you run it because it fetches the driver.  

Here's the link. [ http://packages.debian.org/unstable/utils/bcm43xx-fwcutter]("http://packages.debian.org/unstable/utils/bcm43xx-fwcutter").  It worked like a champ for me.

---

### Post by MyR on 2007-07-15
this might help, theres 5 tests on here
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom)
peace

---

### Post by Mark Phelps on 2007-07-16
Using the links provided, was able to download and install bcm43xx firmware using the links on the DarkN00b post -- but that limits me to 11mb. While this is OK for email and web browsing, the laptop has builtin 54g.  SO, I tried the same script to install the NDISwrapper stuff, and although the script claims that the NDISwrapper stuff installs and configures correctly (which it does because ndiswrapper -l produces the write output), just like before, when I followed the How-tos and did everything manually, it still doesn't work.  Even tried modifying /etc/network/interfaces to include a static address (withing the range that my router assigns) and pointing to my router as a gateway.  Running iwconfig still shows that there is no access point. Using ifup for wlan0 still gets no DHCPOFFERS.  Also, using iwlist for wlan0, with the scan option, fails to see my network at all.

I've been hacking at this for several days nearly full-time now, and I thought I saw a post on this forum where someone had figured out how to get the fwcutter method (bcm43xx firmware) to work faster than 11mb.  But, I've tried lots of searches, and can't find that anymore.  With some 26,000 threads, and some of the 4306-broadcom threads going on for 60 pages or more, I just don't have the time to search them all.  Have tried advanced search but didn't see a way to specify using ALL of the keywords.

Was trying to get wireless working on the HP laptop before I reformatted the hard drive (to remove windows XP home) and reinstalled Ubuntu. Doesn't look like I can do that.

---

