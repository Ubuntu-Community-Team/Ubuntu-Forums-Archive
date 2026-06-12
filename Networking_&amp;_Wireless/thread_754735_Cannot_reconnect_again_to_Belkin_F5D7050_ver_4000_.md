---
title: "Cannot reconnect again to Belkin F5D7050 ver 4000 USB"
date: 2008-04-14
forum: Networking &amp; Wireless
---

### Post by vale25 on 2008-04-14
- brand newly installed ubuntu 7.10, ndiswrapper-common/utils.1.9 of the installation CD 
- Belkin F5D7050 version 4000 USB wireless adapter with original Windows drivers

Thanks to dstew and wieman1 sticky I managed to get connected. However, I noticed a unusual slowness, not only due to my limited RAM (192 MB). Later on I realized that a process is literally eating my CPU. 

 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5248 root      10  -5     0    0    0 S **54.9**  0.0  33:18.49 ntdriver           

After restarting several times the computer it was absolutely impossible to extablish again the connection. Remember that at least once it went through, this means the configuration was initially valid.

I would ask you to look (sorry for long mail, I put all info required by the sticky post). If noone will provide me a miraculous command to get it running again, at least we can show to ndiswrapper developers the problem and they might find a solution for that :-)

Here some printouts from the successful initial installation:

va@va-laptop:~$ sudo ndiswrapper -i /media/cdrom0/files/Driver/BLKWGU.inf
[sudo] password for va:
installing blkwgu ...
va@va-laptop:~$ ndiswrapper -l
blkwgu : driver installed
        device (050D:705C) present (alternate driver: zd1211rw)

va@va-laptop:~$ sudo modprobe ndiswrapper
va@va-laptop:~$ sudo depmod -a


I blacklist then the zd1211rw as shown in thread, I do not know whether was really done.


va@va-laptop:~$ sudo iwlist scan
[sudo] password for va:
lo        Interface doesn't support scanning.

eth0      Scan completed :
          Cell 01 - Address: 00:90:D0:ED:F7:36
                    ESSID:"SpeedTouch38333E"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=100/100  
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 384ms ago
...
va@va-laptop:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       physical id: 2
       logical name: eth0
       serial: 00:17:3f:8f:8e:6d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b/g



Now I will follow the instructions of the thread:

va@va-laptop:~$ wpa_passphrase SpeedTouch38333E <my-psswd>
network={
        ssid="SpeedTouch38333E"
        #psk="<my-psswd>"
        psk=<generated-psswd>
}

edited:

va@va-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
wpa-driver wext
wpa-ssid SpeedTouch38333E
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk <generated-psswd>

sudo /etc/init.d/networking restart


At this moment everything was fine (but slow). Then I rebooted the computer. I first realized that I need to redo the commands:

va@va-laptop:~$ sudo modprobe ndiswrapper
va@va-laptop:~$ sudo depmod -a

to reloadit to the kernel (the second depmod I am not sure if really necessary)


From now on any trial to restart/ stop/ force-load to /etc/init.d/networking has failed.

Worth mentioning a bug by showing this line:

There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120

I was checking, removing it by hand, there was no such pid, so this could be also interesting to be checked. I do not comment the printouts from now on, they must be self explaining

I thank anyone for replies, at least perhaps we give some more info to ndiswrapper team (before I throw thies Belkin to the trash can :-(

regards

valentin




sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:17:3f:8f:8e:6d
Sending on   LPF/eth0/00:17:3f:8f:8e:6d
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.254 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:17:3f:8f:8e:6d
Sending on   LPF/eth0/00:17:3f:8f:8e:6d
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
 

va@va-laptop:~/tmp$ sudo rm /var/run/dhclient.eth0.pid
va@va-laptop:~/tmp$ sudo /etc/init.d/networking stop
 * Deconfiguring network interfaces...                                          Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:17:3f:8f:8e:6d
Sending on   LPF/eth0/00:17:3f:8f:8e:6d
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.254 port 67
                                                                         [ OK ]
va@va-laptop:~/tmp$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:17:3f:8f:8e:6d
Sending on   LPF/eth0/00:17:3f:8f:8e:6d
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
 

Tasks: 107 total,   1 running, 106 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.6%us, 16.6%sy,  0.0%ni, 80.5%id,  0.3%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    190916k total,   187512k used,     3404k free,     5048k buffers
Swap:   369452k total,    41644k used,   327808k free,    63620k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5248 root      10  -5     0    0    0 S 54.9  0.0  33:18.49 ntdriver           
 4722 root      15   0  274m 8888 4528 S  2.0  4.7   0:24.37 Xorg               
 5173 va        15   0 91760  17m 8580 S  0.3  9.6   0:07.43 gnome-terminal     
 6009 va        15   0  2364 1152  876 R  0.3  0.6   0:00.05 top                
 

va@va-laptop:~/tmp$ ll /var/run/dhclient.eth0.pid
-rw-r--r-- 1 root root 0 2008-04-13 20:57 /var/run/dhclient.eth0.pid
va@va-laptop:~/tmp$ cat /var/run/dhclient.eth0.pid
va@va-laptop:~/tmp$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:17:3f:8f:8e:6d
Sending on   LPF/eth0/00:17:3f:8f:8e:6d
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

                                                                         [ OK ]

va@va-laptop:~/tmp$ ll /var/run/dhclient.eth0.pid
-rw-r--r-- 1 root root 5 2008-04-13 21:11 /var/run/dhclient.eth0.pid
va@va-laptop:~/tmp$ cat  /var/run/dhclient.eth0.pid
6870


va@va-laptop:~/tmp$ cat  /var/run/dhclient.eth0.pid
6870



va@va-laptop:~/tmp$ iwconfig
lo        no wireless extensions.

eth0      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:39 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

va@va-laptop:~/tmp$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
link-local      *               255.255.0.0     U     0      0        0 eth0
default         *               0.0.0.0         U     1000   0        0 eth0
va@va-laptop:~/tmp$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      No scan results




va@va-laptop:~/tmp$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      No scan results



va@va-laptop:~/tmp$ sudo lshw -C network
  *-network               
       description: Wireless interface
       physical id: 2
       logical name: eth0
       serial: 00:17:3f:8f:8e:6d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+blkwgu driverversion=1.45+Belkin,11/10/2005,6.3.2.16 link=no multicast=yes wireless=IEEE 802.11g


va@va-laptop:~/tmp$ sudo ifdown -v eth0
Configuring interface eth0=eth0 (inet)
run-parts --verbose /etc/network/if-down.d
run-parts: executing /etc/network/if-down.d/avahi-autoipd
run-parts: executing /etc/network/if-down.d/wpasupplicant
dhclient3 -r -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 6870
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:17:3f:8f:8e:6d
Sending on   LPF/eth0/00:17:3f:8f:8e:6d
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.254 port 67
ifconfig eth0 down
run-parts --verbose /etc/network/if-post-down.d
run-parts: executing /etc/network/if-post-down.d/avahi-daemon
run-parts: executing /etc/network/if-post-down.d/wireless-tools
run-parts: executing /etc/network/if-post-down.d/wpasupplicant
wpa_supplicant: terminating wpa_supplicant daemon via pidfile /var/run/wpa_supplicant.eth0.pid
Stopped /sbin/wpa_supplicant (pid 6839).


va@va-laptop:~/tmp$ sudo ifup -v eth0
Configuring interface eth0=eth0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
wpa_supplicant: wpa-driver wext
wpa_supplicant: /sbin/wpa_supplicant -B -P /var/run/wpa_supplicant.eth0.pid -i eth0 -D wext -C /var/run/wpa_supplicant
Starting /sbin/wpa_supplicant...
wpa_supplicant: ctrl_interface socket located at /var/run/wpa_supplicant/eth0
wpa_supplicant: wpa-ap-scan 1 -- OK
wpa_supplicant: configuring network block -- 0
wpa_supplicant: wpa-ssid "SpeedTouch38333E" -- OK
wpa_supplicant: wpa-psk ***** -- OK
wpa_supplicant: wpa-pairwise TKIP -- OK
wpa_supplicant: wpa-group TKIP -- OK
wpa_supplicant: wpa-key-mgmt WPA-PSK -- OK
wpa_supplicant: wpa-proto WPA -- OK
wpa_supplicant: enabling network block 0 -- OK

dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:17:3f:8f:8e:6d
Sending on   LPF/eth0/00:17:3f:8f:8e:6d
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
run-parts --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/avahi-autoipd
run-parts: executing /etc/network/if-up.d/avahi-daemon
run-parts: executing /etc/network/if-up.d/mountnfs
run-parts: executing /etc/network/if-up.d/ntpdate
run-parts: executing /etc/network/if-up.d/wpasupplicant

---

