---
title: "cable modem problem"
date: 2007-07-24
forum: Networking &amp; Wireless
---

### Post by gand on 2007-07-24
hi,
i've recently switched to cable (as opposed to adsl) for my internet.  I'm pretty happy with it so far, apart from the fact that I have to turn the modem off and on every time a reboot my machine, and sometimes (not always) have to do a 'sudo /etc/init.d/networking restart'.

I'm using a WebSTAR EPC2100R2 modem, and it's connected via ethernet.

Here's example of output from ifconfig after rebooting (no connection):

```
mark@mark-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr A2:08:44:29:8F:C9  
          inet addr:77.99.173.193  Bcast:255.255.255.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2655 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:166671 (162.7 KiB)  TX bytes:5102 (4.9 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1712 (1.6 KiB)  TX bytes:1712 (1.6 KiB)

mark@mark-desktop:~$ ping google.com
ping: unknown host google.com
mark@mark-desktop:~$ ping 64.233.187.99
connect: Network is unreachable
```

Then after power off and on of modem (still no connection):
```
mark@mark-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr A2:08:44:29:8F:C9  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6816 errors:0 dropped:0 overruns:0 frame:0
          TX packets:130 errors:0 dropped:0 overruns:0 carrier:5
          collisions:0 txqueuelen:1000 
          RX bytes:424588 (414.6 KiB)  TX bytes:25098 (24.5 KiB)

eth0:avah Link encap:Ethernet  HWaddr A2:08:44:29:8F:C9  
          inet addr:169.254.7.53  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4904 (4.7 KiB)  TX bytes:4904 (4.7 KiB)
```

Then after restarting networking I get a connection:
```
mark@mark-desktop:~$ sudo /etc/init.d/networking restart
Password:
 * Reconfiguring network interfaces...                                                                                                      RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 6039
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/a2:08:44:29:8f:c9
Sending on   LPF/eth0/a2:08:44:29:8f:c9
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 62.30.144.119 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/a2:08:44:29:8f:c9
Sending on   LPF/eth0/a2:08:44:29:8f:c9
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 10.181.0.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 10.181.0.1
bound to 82.35.101.111 -- renewal in 1533 seconds.
eth1: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
eth2: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
ath0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
wlan0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
                                                                                                                                     [ OK ]
mark@mark-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr A2:08:44:29:8F:C9  
          inet addr:82.35.101.111  Bcast:255.255.255.255  Mask:255.255.248.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8482 errors:0 dropped:0 overruns:0 frame:0
          TX packets:146 errors:0 dropped:0 overruns:0 carrier:5
          collisions:0 txqueuelen:1000 
          RX bytes:531698 (519.2 KiB)  TX bytes:28479 (27.8 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:84 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6104 (5.9 KiB)  TX bytes:6104 (5.9 KiB)
```

I can always get a connection within a few seconds of booting up, so not major problem for me, but my girlfriend expects to switch pc on and for internet to work!

Any help would be much appreciated.
Cheers,
Gand

---

### Post by punx45 on 2007-07-24
looks like something is going wrong when the network interfaces are brought up during the boot process.  check /var/log/messages (or something like that, cant remember exactly, cant check :( ) and look for lines dealing with networking and see if there are any error messages.

---

### Post by gand on 2007-07-29
ok, had a look in /var/log/messages - get the following error when eth0 is brought up after I re-boot:
```
atl1 0000:03:00.0: Unable to enable MSI: -22
atl1: eth0 link is up 100 Mbps full duplex
```
but when I restart the modem (to get internet to work), don't get the error message:
```
atl1: eth0 link is down
atl1: eth0 link is up 100 Mbps full duplex
atl1: eth0 link is down
atl1: eth0 link is up 100 Mbps full duplex
```

So, looks like 'Unable to enable MSI' may be the problem.
Done a quick search, and looks like this error may be linked to my network driver - I'm using Attansic L1 Gigabit, so think I might try upgrading my driver, unless anybody else has a better idea?

Cheers

---

