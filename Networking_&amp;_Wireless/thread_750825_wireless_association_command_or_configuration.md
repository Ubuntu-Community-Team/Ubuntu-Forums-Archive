---
title: "wireless association command or configuration???"
date: 2008-04-09
forum: Networking &amp; Wireless
---

### Post by Red-Shield on 2008-04-09
i am trying to start a wirless network via the command prompt. i am using this string

**sudo iwconfig eth0 essid "linksys" **

and it seems to work i get this 

serial-killer@AMD64:~$ sudo iwconfig eth0 essid "linksys"
serial-killer@AMD64:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11g  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:16:B6:E4:4F:80   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=71/100  Signal level=-58 dBm  Noise level=-88 dBm
          Rx invalid nwid:0  Rx invalid crypt:2  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:13


**and then i use this command**

serial-killer@AMD64:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:16:6f:6c:b3:13
Sending on   LPF/eth0/00:16:6f:6c:b3:13
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.104 -- renewal in 41086 seconds.

**but my network at home requires a WEP pass word what am i missing**

---

### Post by Red-Shield on 2008-04-09
this is what happens when i try this it might not be the right command 

root@AMD64:~# iwconfig eth0 essid "serial-killer" enc s:#joanclara#
root@AMD64:~# iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      unassociated  ESSID:"serial-killer"  
          Mode:Managed  Frequency=2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:236A-6F61-6E63-6C61-7261-2300-00   Security mode:open
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:2  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:5   Missed beacon:0

root@AMD64:~# dhclient eth0
There is already a pid file /var/run/dhclient.pid with pid 7053
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:16:6f:6c:b3:13
Sending on   LPF/eth0/00:16:6f:6c:b3:13
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
Trying recorded lease 192.168.1.104
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

Trying recorded lease 192.168.1.102
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.
root@AMD64:~# iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      unassociated  ESSID:"serial-killer"  
          Mode:Managed  Frequency=2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:236A-6F61-6E63-6C61-7261-2300-00   Security mode:open
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:2  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:5   Missed beacon:0

it is unassociated why is this can any one help

---

### Post by Junglizer on 2008-04-10
> **Red-Shield said:**
> 

root@AMD64:~# dhclient eth0
**There is already a pid file /var/run/dhclient.pid with pid 7053**
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:16:6f:6c:b3:13
Sending on   LPF/eth0/00:16:6f:6c:b3:13
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
**Trying recorded lease 192.168.1.104**



At least from this section, what you can see in bold is that you are using a fall-back IP that you received from DHCP earlier. So you need to delete that entry: ```
rm  /var/run/dhclient.pid
```
then re-dhclient.

---

