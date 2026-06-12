---
title: "WUSB11 2.6 problems in Hardy Heron"
date: 2008-08-17
forum: Networking &amp; Wireless
---

### Post by tablaboi on 2008-08-17
Hello,

I booted hardy heron from the live cd, and try to configure my wusb11 2.6 wireless usb network adapter to work. However, roaming mode completely fails. If i manually connect, I can see a bunch of networks, but they're all at 0%. Based on my rudimentary knowledge of terminal (and the great ubuntu forums), I tried to connect from terminal and here are my results:

```

To run a command as administrator (user "root"), use "sudo <command>". 
See "man sudo_root" for details. 
 
ubuntu@ubuntu:~$ lshw -C network 
WARNING: you should run this program as super-user. 
  *-network                
       description: Ethernet interface 
       product: RTL-8139/8139C/8139C+ 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 5 
       bus info: pci@0000:02:05.0 
       logical name: eth0 
       version: 10 
       serial: 00:19:21:54:f1:d2 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes 
  *-network DISABLED 
       description: Wireless interface 
       physical id: 3 
       logical name: wlan0 
       serial: 00:06:25:48:9b:24 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes driver=at76_usb driverversion=0.14beta1 firmware=1.103.4-169 wireless=IEEE 802.11b 
ubuntu@ubuntu:~$ sudo ifconfig wlan0 down 
ubuntu@ubuntu:~$ dhclient -r wlan0 
Internet Systems Consortium DHCP Client V3.0.6 
Copyright 2004-2007 Internet Systems Consortium. 
All rights reserved. 
For info, please visit http://www.isc.org/sw/dhcp/ 
 
can't create /var/lib/dhcp3/dhclient.leases: Permission denied 
Can't create /var/run/dhclient.pid: Permission denied 
drop_privileges: could not set group id: Operation not permitted 
ubuntu@ubuntu:~$ sudo dhclient -r wlan0 
Internet Systems Consortium DHCP Client V3.0.6 
Copyright 2004-2007 Internet Systems Consortium. 
All rights reserved. 
For info, please visit http://www.isc.org/sw/dhcp/ 
 
Listening on LPF/wlan0/00:06:25:48:9b:24 
Sending on   LPF/wlan0/00:06:25:48:9b:24 
Sending on   Socket/fallback 
ubuntu@ubuntu:~$ sudo ifconfig wlan0 up 
ubuntu@ubuntu:~$  
ubuntu@ubuntu:~$  
ubuntu@ubuntu:~$  
ubuntu@ubuntu:~$  
ubuntu@ubuntu:~$  
ubuntu@ubuntu:~$  
ubuntu@ubuntu:~$  
ubuntu@ubuntu:~$  
ubuntu@ubuntu:~$  
ubuntu@ubuntu:~$  
ubuntu@ubuntu:~$ sudo iwconfig wlan0 essid "xxxx" 
ubuntu@ubuntu:~$ sudo iwconfig wlan0 key yyyy
ubuntu@ubuntu:~$ sudo iwconfig wlan0 key open 
ubuntu@ubuntu:~$ sudo iwconfig wlan0 mode Managed 
ubuntu@ubuntu:~$ sudo dhclient wlan0 
There is already a pid file /var/run/dhclient.pid with pid 134519072 
Internet Systems Consortium DHCP Client V3.0.6 
Copyright 2004-2007 Internet Systems Consortium. 
All rights reserved. 
For info, please visit http://www.isc.org/sw/dhcp/ 
 
Listening on LPF/wlan0/00:06:25:48:9b:24 
Sending on   LPF/wlan0/00:06:25:48:9b:24 
Sending on   Socket/fallback 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping. 
ubuntu@ubuntu:~$ sudo modprobe r818x 
FATAL: Module r818x not found. 
ubuntu@ubuntu:~$ sudo modprobe r8187 
FATAL: Module r8187 not found. 
ubuntu@ubuntu:~$  


```

Note: xxxx was replaced w/ a real essid, same with yyyy

Does anybody else have this problem? Any solutions?

---

