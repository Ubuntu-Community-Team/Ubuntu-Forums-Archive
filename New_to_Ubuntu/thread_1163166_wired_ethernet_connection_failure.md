---
title: "wired ethernet connection failure"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by dascheer on 2009-05-18
hey guys, im having difficulties connecting to the internet via my wired ethernet connection.  i can connect to wireless fine.

ive browsed the community documentation, and it seems like my eth0 device is not configured.  i used network-admin and NetworkManager to help, but I still fail to connect to the internet.  I have the right MAC address and everything--i think.

ive heard other users are having issues with their wired connection, which supposedly is supposed to run error-free.  can someone point me in the right direction?  thanks!

Here are my specs:

eth0      Link encap:Ethernet  HWaddr 00:15:c5:10:3d:7b  
          UP BROADCAST MULTICAST  MTU:64  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1252 (1.2 KB)  TX bytes:3033 (3.0 KB)
          Interrupt:17 
 

and i ran "sudo /etc/init.d/networking restart" and this is what it gave me:

```
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 10682
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:15:c5:10:3d:7b
Sending on   LPF/eth0/00:15:c5:10:3d:7b
Sending on   Socket/fallback
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
SIOCSIFADDR: No buffer space available
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:15:c5:10:3d:7b
Sending on   LPF/eth0/00:15:c5:10:3d:7b
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
send_packet: Message too long
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
RTNETLINK answers: No such device
run-parts: /etc/network/if-up.d/avahi-autoipd exited with return code 2




```

---

### Post by cariboo on 2009-05-18
What is the output of:

```
sudo lshw -C network
```

The above command must be run in a terminal, it will tell us if the network card is detected properly and if the driver is loaded.

---

### Post by anewguy on 2009-05-18
Also, please post back the output of both of these:

lspci

lsusb



Thanks!
Dave :)

---

