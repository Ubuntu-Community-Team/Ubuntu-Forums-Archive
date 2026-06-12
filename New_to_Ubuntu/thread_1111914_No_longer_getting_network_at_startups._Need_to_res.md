---
title: "No longer getting network at startups. Need to restart every time"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by stig on 2009-03-31
I have two 5-year-old Pentium PCs which are networked via cable and Speedtouch broadband router and use them for my small home business. They were upgraded at the same time last year to Ubuntu 8.04 and they have the same software applications.

They have been working successfully on the network for a couple of years until last Sunday (29th March). Now one works as before but the other fails to startup the network at each boot. It fails to connect to the net via Firefox, Thunderbird, gFTP and shows no PCs when I do Places/Network (and my other PC cannot see it). I have to use sudo /etc/init.d/networking restart and then the connections to the Net are OK. (At first, before I realised I could restart it, I thought I had a failed network card and swapped it for one from an old PC but it made no difference.)

Both PCs had been in use on Saturday (28th March) with no problems - creating documents, browsing, email etc all OK. No changes were made to the system files except that both PCs received the Ubuntu update to Firefox/XULrunner within 30 minutes of each other.

Both PCs have the Network Manager icon and it shows `Network Enabled' clicked on both. The network settings on the two PCs are the same. "Wired connection: address dchp" is ticked. The /etc/network/interfaces file shows on both:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

I cannot understand why anything would have changed on one PC and not the other. Nothing unusual was done on either PC, to hardware or software. And when I do the network restart command in the terminal the internet connection returns OK but not the network. I have re-intalled Samba files on the broken PC but with no change.

I searched the Ubuntu forum but only found a problem back in 2007 when Network Manager seemed to be switching off the network after it had been started at boot. A workaround was to uninstall or disable Network Manager. I tried uninstalling it but it made no difference to the broken PC and I have re-installed it.

Help would be welcome!

---

### Post by stig on 2009-03-31
More information on my problem...

ifconfig on the problem computer immediately after boot and before restart of connection gives:

```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:05:5d:75:15:03  
          inet6 addr: fe80::205:5dff:fe75:1503/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:468 (468.0 B)
          Interrupt:18 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1322 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1322 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:66100 (64.5 KB)  TX bytes:66100 (64.5 KB)
```


After running sudo /etc/init.d/networking restart I get:

```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:05:5d:75:15:03  
          inet addr:10.0.0.3  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::205:5dff:fe75:1503/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:678 errors:0 dropped:0 overruns:0 frame:0
          TX packets:586 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:796783 (778.1 KB)  TX bytes:75067 (73.3 KB)
          Interrupt:18 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1443 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1443 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:72402 (70.7 KB)  TX bytes:72402 (70.7 KB)
```

---

### Post by stig on 2009-04-02
Still no success. I still can't get the problem PC to auto start the network at boot even though this one does auto start and they are on the same router and I've now changed both the network cards and cables without any effect.

When I run sudo /etc/init.d/networking restart I get:

```
[sudo] password for ******: 
 * Reconfiguring network interfaces...    RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:05:5d:75:15:03
Sending on   LPF/eth0/00:05:5d:75:15:03
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 10.0.0.138 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:05:5d:75:15:03
Sending on   LPF/eth0/00:05:5d:75:15:03
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER of 10.0.0.3 from 10.0.0.138
DHCPREQUEST of 10.0.0.3 on eth0 to 255.255.255.255 port 67
DHCPACK of 10.0.0.3 from 10.0.0.138
bound to 10.0.0.3 -- renewal in 3369 seconds.
eth1: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth1.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
 * Stopping NTP server ntpd
   ...done.
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
 * Starting NTP server ntpd
   ...done.
Bind socket to interface: No such device
Failed to bring up eth1.
eth2: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth2.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
ath0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.ath0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
wlan0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
```

Then I can access the Internet but still cannot connect to my other computer. Yet the network was working fine on Saturday!

lspci shows:
02:06.0 Ethernet controller: VIA Technologies, Inc. VT6105 [Rhine-III] (rev 86)

---

### Post by superprash2003 on 2009-04-02
hmm.. ,maybe you could try setting up static ip..for some reason your router isnt giving your machine an ip at the first try.. probably due to the large number of interfaces you have up and running

---

### Post by stig on 2009-04-02
Hi, thanks for helping! I'm not very knowledgeable about computers although I've been using Ubuntu for a couple of years. I'm not sure what you mean by `a large number of interfaces' I have not, to my knowledge, set up anything that meets this description - but then I don't know what these interfaces are. I use only cable networking, no wireless. My computers are otherwise very simple basic Ubuntu setups and I would have expected to have less of everything rather than more!

---

### Post by superprash2003 on 2009-04-03
your /etc/network/interfaces file shows 5 different interfaces.. which means a total of 5 network adapters( wireless +wired LAN cards).. do you have that many?? do you use vmware or anything similar?

---

### Post by stig on 2009-04-04
No, a wired network card, that is all. And no vmware as far as I know (I don't know what it is). These computers were built in about 2005 as Windows PCs, then Ubuntu Dapper, then Hardy. The PC giving the problem still has a Windows partition but it's redundant, never used now. The Hardy setups are standard, as from the upgrade from Dapper. The network was set up ages ago following the advice given by `Stormbringer' on these forums:

`HOWTO: Setup Samba peer-to-peer with Windows'
[http://ubuntuforums.org/showthread.php?t=202605&highlight=network+windows](http://ubuntuforums.org/showthread.php?t=202605&highlight=network+windows)

Nothing significant has been done to the computers for some time now. My wife and I use them for basic work and home use - documents, photos, browsing, email. There shouldn't be anything unusual about the setups.

On the advice of a colleague, I've now deleted the entries in the etc/network/interfaces file other than the lo and eth0. But the problem remains.

The ability to swap files between the PCs is no longer essential to me, but the inconvenience of having to `network restart' one of the PCs at every boot is annoying. And of course, there is just the nagging worry of what is actually going on? Why should things change for no obvious reason?

---

### Post by superprash2003 on 2009-04-05
could you post your /etc/network/interfaces file again.. you could try using static ip

---

### Post by stig on 2009-04-06
As requested, etc/network/interfaces file

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```

The colleague mentioned above suggested that I went to the /etc/rcS.d folder and renamed the networking file to a higher, unused, number. It was S40networking so I renamed it to S48networking. When I rebooted the computer (after a full shutdown) the connection was working immediately and I thought the renaming has been successful. But after another reboot it was failing again. I tried renaming it so that it was the highest number in the folder but it made no difference (I set it finally to S48 and left it).

I also tried booting the PC into the previous linux kernel (22, I'm on 23 from the last update). The connection worked with this and did so on several reboots, so I thought that might be a temporary solution. But next day - back to failed connection again!

I may well end up trying static IP but I still wonder why it isn't working OK on DHCP as it used to do.

---

### Post by stig on 2009-04-07
I've ended up going for the static IP option on the problem PC. After plenty of help from the Linux-knowledgeable colleague, we couldn't find anything that made the DHCP work on that computer immediately from boot permanently. Quite often, after making a change to the configuration the computer would give an Internet connection immediately after boot - but not on subsequent boots.

---

