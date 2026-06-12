---
title: "Wireless Issue"
date: 2007-01-04
forum: Networking &amp; Wireless
---

### Post by Riyonuk on 2007-01-04
Alright, I've been connect before to the same network, and just one day out of the blue it doesnt work anymore. So I do "iwlist wlan0 scan" to make sure the network is still there and it is. So I tried diffrent things and just formatted my whole hardrive and decided to start over. It still doesnt work. The Wireless Card is recgonized, I set it to the right ESSID which is "NETGEAR" and it says "Configuring Card or something like that". So what am I doing wrong? It would be nice to get an answer within the next hour, as I'm currently at the library, its my only internet access as of now u_u

```
riyonuk@ubuntu:~$ ip a | grep inet6
riyonuk@ubuntu:~$ lsmod | grep ipv6
riyonuk@ubuntu:~$ iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:0F:B5:EE:9D:70
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 9 11 6 12 18 24 36 48 54 
                    Quality:195  Signal level:0  Noise level:86
                    Extra: Last beacon: 0ms ago

riyonuk@ubuntu:~$ sudi iwconfig wlan0 essid - "NETGEAR"
bash: sudi: command not found
riyonuk@ubuntu:~$ sudo iwconfig wlan0 essid - "NETGEAR"
Password:
riyonuk@ubuntu:~$ iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:0F:B5:EE:9D:70
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 9 11 6 12 18 24 36 48 54 
                    Quality:149  Signal level:0  Noise level:34
                    Extra: Last beacon: 3ms ago

riyonuk@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b linked  ESSID:"NETGEAR"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:B5:EE:9D:70   
          Bit Rate=11 Mb/s   Sensitivity=80/85  
          Retry:on   Fragment thr:off
          Power Management:off
          Link Quality=33/100  Signal level=-110 dBm  Noise level=-189 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

riyonuk@ubuntu:~$ iwlist
Usage: iwlist [interface] scanning
              [interface] frequency
              [interface] channel
              [interface] bitrate
              [interface] rate
              [interface] encryption
              [interface] key
              [interface] power
              [interface] txpower
              [interface] retry
              [interface] ap
              [interface] accesspoints
              [interface] peers
              [interface] event
riyonuk@ubuntu:~$ cat /etc/resolv.conf
nameserver 208.67.222.222
nameserver 208.67.220.220
# nameserver 192.168.1.1
riyonuk@ubuntu:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 4676
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:40:ca:5b:60:38
Sending on   LPF/eth0/00:40:ca:5b:60:38
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.wlan0.pid with pid 4915
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:05:5d:96:99:81
Sending on   LPF/wlan0/00:05:5d:96:99:81
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:40:ca:5b:60:38
Sending on   LPF/eth0/00:40:ca:5b:60:38
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:05:5d:96:99:81
Sending on   LPF/wlan0/00:05:5d:96:99:81
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ ok ]
riyonuk@ubuntu:~$ :( I hate life >_>
```

---

### Post by Riyonuk on 2007-01-04
I know its possible to get internet, and I have a pretty good connection. Is there some command I need to be doing?

---

### Post by Metaljaz on 2007-01-04
Try reading through this thread, may help.

[http://www.ubuntuforums.org/showthread.php?t=308879](http://www.ubuntuforums.org/showthread.php?t=308879)

---

