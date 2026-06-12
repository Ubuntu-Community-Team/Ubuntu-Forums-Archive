---
title: "Broadcom BCM4318 Stopped Working"
date: 2007-08-20
forum: Networking &amp; Wireless
---

### Post by marcushe on 2007-08-20
Hi,
,
I have a Compaq Presario V2000 with the Broadcom BCM4318 wireless card & Feisty.  Initially I ran the fwcutter firmware stripper, and my wireless worked great.  However the other day while using the machine, the wireless capabilities just stopped working.  I can see the names of, and decipher signal strengths of the networks, but can't connect to any of them - encryption or not.  I tried installing the windows drivers with ndnisutil, but they come back as a invalid device error.

This happened to me once in Windows - I did a system restore to a couple weeks back and it worked fine after then.  So clearly it's some kind of software issue.  Below is some outputs the wireless is giving while having this problem.

Is there anything I can reset, like a cache?  Or is there a solution to this.

Thanks!

- Marcus

chris@chris-laptop:~$ sudo wlassistant
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kbuildsycoca running...
Reusing existing ksycoca
kio (KService*): WARNING: The desktop entry file /usr/share/applications/DefaultPlugins.desktop has Type=Link instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/DefaultPlugins.desktop
kio (KSycoca): ERROR: No database available!
Loaded application options.
DHCP Client: dhclient
All executables found.
iwconfig_status: /sbin/iwconfig
==>stderr: lo        no wireless extensions.

eth0      no wireless extensions.

Wireless interface(s): eth1
Permissions checked.
ifconfig_status: /sbin/ifconfig eth1
scan: /sbin/iwlist eth1 scan
Networks found: 3
Checking for active connection.
Trying to get gateway address...
...from 'route'
No default gateway.
Checking for active connection.
Trying to get gateway address...
...from 'route'
No default gateway.
Checking for active connection.
Trying to get gateway address...
...from 'route'
No default gateway.
ACTION: CONNECT.
kill_dhcp: /sbin/dhclient -r eth1
==>stderr: Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:14:a5:7a:8c:dd
Sending on   LPF/eth1/00:14:a5:7a:8c:dd
Sending on   Socket/fallback
ifup: /sbin/ifconfig eth1 up
iwconfig_set: /sbin/iwconfig eth1 mode managed channel 6 key off essid linksys
iwconfig_ap: /sbin/iwconfig eth1 ap 00:0C:41:AB:85:7A
ifconfig_dhcp: /sbin/dhclient -q eth1
==>stderr: There is already a pid file /var/run/dhclient.pid with pid 134993416
Trying to get gateway address...
...from 'route'
No default gateway.
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
Launched ok, pid = 26960
OggS-SEEK: at 0 want 60408 got 51136 (diff-requested 60408)
OggS-SEEK: at 60352 want 520 got 0 (diff-requested -59832)
Checking for active connection.
Trying to get gateway address...
...from 'route'
No default gateway.
Checking for active connection.
Trying to get gateway address...
...from 'route'
No default gateway.
Checking for active connection.
Trying to get gateway address...
...from 'route'
No default gateway.
ACTION: CONNECT.
kill_dhcp: /sbin/dhclient -r eth1
==>stderr: There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:14:a5:7a:8c:dd
Sending on   LPF/eth1/00:14:a5:7a:8c:dd
Sending on   Socket/fallback
ifup: /sbin/ifconfig eth1 up
iwconfig_set: /sbin/iwconfig eth1 mode managed channel 6 key open bluehouse essid 49er Elite
==>stderr: Error : unrecognised wireless request "bluehouse"
iwconfig_ap: /sbin/iwconfig eth1 ap 00:1B:63:2D:65:85
ifconfig_dhcp: /sbin/dhclient -q eth1
==>stderr: There is already a pid file /var/run/dhclient.pid with pid 134993416
Trying to get gateway address...
...from 'route'
No default gateway.
OggS-SEEK: at 0 want 60408 got 51136 (diff-requested 60408)
OggS-SEEK: at 60352 want 520 got 0 (diff-requested -59832)
Checking for active connection.
Trying to get gateway address...
...from 'route'
No default gateway.
Checking for active connection.
Trying to get gateway address...
...from 'route'
No default gateway.

---

### Post by marcushe on 2007-08-21
bump

---

### Post by kevdog on 2007-08-21
Please post 
lshw -C network
iwlist scan

Not sure whats wrong at this point

---

### Post by marcushe on 2007-08-21
chris@chris-laptop:~$ sudo lshw -C network
Password:
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@05:00.0
       logical name: eth0
       version: 10
       serial: 00:16:36:3a:df:6b
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: ioport:a000-a0ff iomemory:c0208000-c02080ff irq:19
  *-network:1
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@05:02.0
       logical name: eth1
       version: 02
       serial: 00:14:a5:7a:8c:dd
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-generic latency=64 link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:c0204000-c0205fff irq:20
chris@chris-laptop:~$ 
chris@chris-laptop:~$ 
chris@chris-laptop:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@05:00.0
       logical name: eth0
       version: 10
       serial: 00:16:36:3a:df:6b
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: ioport:a000-a0ff iomemory:c0208000-c02080ff irq:19
  *-network:1
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@05:02.0
       logical name: eth1
       version: 02
       serial: 00:14:a5:7a:8c:dd
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-generic latency=64 link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:c0204000-c0205fff irq:20
chris@chris-laptop:~$ 


chris@chris-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1B:63:2D:65:85
                    ESSID:"49er Elite"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=89/100  Signal level=-45 dBm  Noise level=-71 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 3224ms ago
          Cell 02 - Address: 00:15:E9:78:39:FA
                    ESSID:"Habs"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=57/100  Signal level=-85 dBm  Noise level=-71 dBm
                    Extra: Last beacon: 9072ms ago

chris@chris-laptop:~$ 

Hope this helps...

Thanks!

- Marcus

---

### Post by marcushe on 2007-08-22
bump

---

### Post by marcushe on 2007-08-22
bump

---

### Post by kevdog on 2007-08-23
There were two routers listed in the output of iwlist scan.  Which one were you trying to connect to??

One the the routers ESSID has a name with a space in it:
> ESSID:"49er Elite"
Really there should be no space since this can cause problems and is technically a violation of the draft standard.

Also type these command at the command line and tell me what happens.  Im only interested in errors toward the end, since some of the initial commands might be overkill:

```

sudo ifconfig eth1 down
sudo ifconfig eth1 0.0.0.0
sudo dhclient -r eth1
sudo killall dhclient dhclient3
sudo ip route flush dev eth1
sudo ifconfig eth1 up
sudo ifconfig eth1 essid "<ESSID_in_QUOTES>"
sudo iwconfig eth1 mode Managed
sudo dhclient eth1

```

---

### Post by marcushe on 2007-08-23
Hi,

None of these commands really do much - because ifconfig  thinks eth1 doesn't exist, when it's actually listed it under ifconfig -a.  The flush didn't work because it said it had nothing to flush, etc.

Here is the output from the last command:

chris@chris-laptop:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFFLAGS: No such device
SIOCSIFFLAGS: No such device
Listening on LPF/eth1/00:14:a5:7a:8c:dd
Sending on   LPF/eth1/00:14:a5:7a:8c:dd
Sending on   Socket/fallback
receive_packet failed on eth1: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Thanks!

- Marcus

---

### Post by kevdog on 2007-08-23
I dont really understand what you mean about the eth1 part, however Im getting its not working.

Can you type the commands again and post the entire terminal output of the commands??

Also can you post once again
lshw -C network
ifconfig
/etc/iftab

---

### Post by marcushe on 2007-08-24
Alright, here you go!

chris@chris-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@05:00.0
       logical name: eth0
       version: 10
       serial: 00:16:36:3a:df:6b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: ioport:a000-a0ff iomemory:c0208000-c02080ff irq:19
  *-network:1
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@05:02.0
       logical name: eth1
       version: 02
       serial: 00:14:a5:7a:8c:dd
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-generic latency=64 multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:c0204000-c0205fff irq:20
chris@chris-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:3A:DF:6B  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:22882 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16038 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17063119 (16.2 MiB)  TX bytes:2537710 (2.4 MiB)
          Interrupt:19 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:14:A5:7A:8C:DD  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:101 overruns:0 frame:0
          TX packets:10609 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:445866 (435.4 KiB)
          Interrupt:3 

eth0:avah Link encap:Ethernet  HWaddr 00:16:36:3A:DF:6B  
          inet addr:169.254.6.196  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:19 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1374 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1374 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:137284 (134.0 KiB)  TX bytes:137284 (134.0 KiB)

chris@chris-laptop:~$ /etc/iftab
bash: /etc/iftab: Permission denied
chris@chris-laptop:~$ sudo /etc/iftab
Password:
sudo: /etc/iftab: command not found

---

