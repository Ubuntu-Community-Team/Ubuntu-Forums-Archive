---
title: "Laptop stopped connecting to wireless router, but LiveCD works fine."
date: 2007-01-18
forum: Networking &amp; Wireless
---

### Post by JimDanger on 2007-01-18
I have a Dell Inspiron 6000D with a Kubuntu 6.10 install. I have a US Robotics MaxG (USR5461) wireless router that I use to connect my laptop to the web. The router is 192.168.2.1 and is named USR. My laptop is set to 192.168.2.3. I also have a desktop that's wired to the router. For the past 3 weeks I've had absolutely no problem ever connecting to the router, but today it just won't join. I tried configuring every which way possible, and even reset the router, but still had no luck. The only thing I could think to do was to reinstall Kubuntu, but I want to stay away from this because it'll be a pain in the butt if I have to reinstall every time my wireless decides to not work. 

I put in a copy of the Kubuntu LiveCD and I was able to connect to my router using the same information I had on the actual install, and it worked flawlessly. I'm thinking it might be a conflict somewhere with something I may have installed, but I'm not sure exactly how to find that out.

I'm hoping maybe someone can help me, so I logged the output of **sudo wlassistant** to see what actions it was taking and any errors it might generate. I logged the output from the LiveCD which worked fine, and then from my actual install.

Please let me know if you see any obvious red flags...

**sudo wlassistant from the LiveCD which WORKED!**
```
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
kded: ERROR: KUniqueApplication: Registering failed!
kded: ERROR: Communication problem with kded, it probably crashed.
Loaded application options.
DHCP Client: dhclient
All executables found.
iwconfig_status: /sbin/iwconfig
==>stderr: lo        no wireless extensions.

eth0      no wireless extensions.

Wireless interface(s): eth1
warning: /etc/resolv.conf not writable
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

knotify: cannot connect to X server :0.0
ERROR: KUniqueApplication: Registering failed!
ERROR: Communication problem with knotify, it probably crashed.
Permissions checked.
ifconfig_status: /sbin/ifconfig eth1
scan: /sbin/iwlist eth1 scan
Networks found: 3
Checking for active connection.
Trying to get gateway address...
...from /var/lib/dhcp3/dhclient.leases
...from 'route'
No default gateway.
ACTION: CONNECT.
Checking for active connection.
Trying to get gateway address...
...from /var/lib/dhcp3/dhclient.leases
...from 'route'
No default gateway.
Checking for active connection.
Trying to get gateway address...
...from /var/lib/dhcp3/dhclient.leases
...from 'route'
No default gateway.
Checking for active connection.
Trying to get gateway address...
...from /var/lib/dhcp3/dhclient.leases
...from 'route'
No default gateway.
Checking for active connection.
Trying to get gateway address...
...from /var/lib/dhcp3/dhclient.leases
...from 'route'
No default gateway.
Checking for active connection.
Trying to get gateway address...
...from /var/lib/dhcp3/dhclient.leases
...from 'route'
No default gateway.
kill_dhcp: /sbin/dhclient -r eth1
==>stderr: Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:15:00:1b:bb:f4
Sending on   LPF/eth1/00:15:00:1b:bb:f4
Sending on   Socket/fallback
ifup: /sbin/ifconfig eth1 up
iwconfig_set: /sbin/iwconfig eth1 mode managed channel 11 key open s:MySecretKey12 essid USR
iwconfig_ap: /sbin/iwconfig eth1 ap 00:14:C1:0B:AB:4E
ifconfig_manual: /sbin/ifconfig eth1 192.168.2.4 netmask 255.255.255.0
resolv.conf: nameserver 192.168.2.1
resolv.conf: nameserver 192.168.2.1
route: /sbin/route add default gw 192.168.2.1
Internet now accessible.

```

**sudo wlassistant From my install which DID NOT WORK:**

```
jim@tokyo:~$ sudo wlassistant
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0
kded: ERROR: KUniqueApplication: Registering failed!
kded: ERROR: Communication problem with kded, it probably crashed.
Loaded application options.
DHCP Client: dhclient
All executables found.
iwconfig_status: /sbin/iwconfig
==>stderr: lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

Wireless interface(s): eth1
Permissions checked.
ifconfig_status: /sbin/ifconfig eth1
scan: /sbin/iwlist eth1 scan
Networks found: 1
Checking for active connection.
Trying to get gateway address...
...from 'route'
Gateway address: 192.168.2.1
ACTION: CONNECT.
kill_dhcp: /sbin/dhclient -r eth1
==>stderr: There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:15:00:1b:bb:f4
Sending on   LPF/eth1/00:15:00:1b:bb:f4
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.2.1 port 67
send_packet: Operation not permitted
ifup: /sbin/ifconfig eth1 up
iwconfig_set: /sbin/iwconfig eth1 mode managed channel 11 key open s:MySecretKey12 essid USR
iwconfig_ap: /sbin/iwconfig eth1 ap 00:14:C1:0B:AB:4E
ifconfig_manual: /sbin/ifconfig eth1 192.168.2.4 netmask 255.255.255.0 broadcast 192.168.2.255
resolv.conf: nameserver 192.168.2.1
resolv.conf: nameserver 192.168.2.1
route: /sbin/route add default gw 192.168.2.1
Trying to get gateway address...
...from 'route'
Gateway address: 192.168.2.1
==>stderr: ping: sendmsg: Operation not permitted
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

knotify: cannot connect to X server :0.0
ERROR: KUniqueApplication: Registering failed!
ERROR: Communication problem with knotify, it probably crashed.
==>stderr: ping: sendmsg: Operation not permitted
Application options saved.
Kernel socket closed.

```

I hope someone can help me out here, I'm missin' the web!

Thanks!
Jim

---

