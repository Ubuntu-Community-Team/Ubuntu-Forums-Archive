---
title: "Wireless kind of works"
date: 2007-04-19
forum: Networking &amp; Wireless
---

### Post by BioSLuDge on 2007-04-19
Ok so I'm kinda new to ubuntu (but not linux) and I'm trying to get my wireless to work.  I have setup ndiswrapper and it seams to work just fine as I can scan networks etc. and I can connect just not the way I would like to.

Here is what I get if right after I boot kubuntu.

> andrew@greifswald:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"insecure.utah.edu"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:0B:86:92:43:C3
          Bit Rate=36 Mb/s   Tx-Power:32 dBm
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:68/100  Signal level:-52 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:45  Invalid misc:1508   Missed beacon:0

andrew@greifswald:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr **:**:**:**:**:**
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17

eth0:avah Link encap:Ethernet  HWaddr **:**:**:**:**:**
          inet addr:169.254.7.230  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1844 (1.8 KiB)  TX bytes:1844 (1.8 KiB)

wlan0     Link encap:Ethernet  HWaddr **:**:**:**:**:**
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:172 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:20309 (19.8 KiB)  TX bytes:1682 (1.6 KiB)
          Interrupt:16 Memory:efdfc000-efe00000



When I try to connect to the insecure.utah.edu wireless network in knetworkmanager (it is scanning for networks just fine) it hangs at about 28% and then never connects.

Here is the output of iwconfig and ifconfig after doing that.

> andrew@greifswald:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"insecure.utah.edu"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:0B:86:92:43:C3
          Bit Rate=18 Mb/s   Tx-Power:32 dBm
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:70/100  Signal level:-51 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:750  Invalid misc:19273   Missed beacon:0

andrew@greifswald:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr **:**:**:**:**:**
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17

eth0:avah Link encap:Ethernet  HWaddr **:**:**:**:**:**
          inet addr:169.254.7.230  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:35 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3344 (3.2 KiB)  TX bytes:3344 (3.2 KiB)


I know the wireless is working ok because if I restart the networking in init.d it connects to insecure.utah.edu and I am able to connect to the internet (note eth0 is not connected to a wired network when I ran this).

> andrew@greifswald:~$ sudo /etc/init.d/networking restart
Password:
 * Reconfiguring network interfaces...
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 5794
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/**:**:**:**:**:**
Sending on   LPF/eth0/**:**:**:**:**:**
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 155.98.249.252 port 67
There is already a pid file /var/run/dhclient.wlan0.pid with pid 4327
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/**:**:**:**:**:**
Sending on   LPF/wlan0/**:**:**:**:**:**
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 155.101.209.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
There is already a pid file /var/run/dhclient.eth0.pid with pid 6847440
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/**:**:**:**:**:**
Sending on   LPF/eth0/**:**:**:**:**:**
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
eth1: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth1.pid with pid 6847440
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
eth2: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth2.pid with pid 6847440
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
ath0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.ath0.pid with pid 6847440
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 6847440
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/**:**:**:**:**:**
Sending on   LPF/wlan0/**:**:**:**:**:**
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 155.101.209.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 155.101.209.1
bound to 155.98.245.*** -- renewal in 1589 seconds.
                                                                         [ OK ]
andrew@greifswald:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"insecure.utah.edu"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:0B:86:92:43:C3
          Bit Rate=11 Mb/s   Tx-Power:32 dBm
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:70/100  Signal level:-51 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:825  Invalid misc:21538   Missed beacon:0

andrew@greifswald:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr **:**:**:**:**:**
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17

eth0:avah Link encap:Ethernet  HWaddr **:**:**:**:**:**
          inet addr:169.254.7.230  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:46 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4293 (4.1 KiB)  TX bytes:4293 (4.1 KiB)

wlan0     Link encap:Ethernet  HWaddr **:**:**:**:**:**
          inet addr:155.98.245.***  Bcast:155.98.245.255  Mask:255.255.255.0
          inet6 addr: fe80::219:7dff:fe53:ccb0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3444 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1965 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1869207 (1.7 MiB)  TX bytes:282928 (276.2 KiB)
          Interrupt:16 Memory:efdfc000-efe00000



Any ideas why knetworkmanager does not work?

here is the output of ndiswrapper
> andrew@greifswald:~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4328) present


And I'm using feisty faun (and I have updated everything).

Thanks for your time
Bio

---

