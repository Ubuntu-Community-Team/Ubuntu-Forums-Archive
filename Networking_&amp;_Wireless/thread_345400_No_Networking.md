---
title: "No Networking"
date: 2007-01-24
forum: Networking &amp; Wireless
---

### Post by weaver4 on 2007-01-24
I am trying to get ubuntu to work behind a Cisco ASA 5510 firewall.

When I power the system up.  I have not ethernet connectivity to this box.

If I open up the Administration->network dialog box; select etho for the "Default Gateway Device" press OK the networking will start working.

But next time I do a restart I have to do it again.

I am using a static IP address, Gateway and Submask are correct.

---

### Post by kebes on 2007-01-24
I'm not sure what the problem is, but there are some commandline tools that may help you figure out what's going on. First, I would run "ifconfig" before and after you make changes to the admin settings. Is there a difference? Is the IP set before you press OK in the networking dialog?

Another thing to try: instead of using the network admin utility, what happens if you use the commandline:
sudo /etc/init.d/networking restart

Does the network start working after that? If so, you could set this command to run automatically at boot or whatever (an ugly hack but it might work). More importantly, it might give you error messages or new information to help fix the problem.

You can post the output of those commands here if you want. Someone might spot the problem. You may also want to take a look at the contents of these files:

/etc/network/interfaces
/etc/hosts
/etc/hostname


Hope that helps...

---

### Post by weaver4 on 2007-01-24
I did not see any differance in the ifconf files.  How do I set the "default gateway device" in some configuration file?

Here is the results of the ifconfig.

eth0      Link encap:Ethernet  HWaddr 00:04:61:4A:FB:27
          inet addr:11.1.1.5  Bcast:11.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::204:61ff:fe4a:fb27/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:468 (468.0 b)
          Interrupt:185 Base address:0xd800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

xxx@ubuntu-server:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:04:61:4A:FB:27
          inet addr:11.1.1.5  Bcast:11.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::204:61ff:fe4a:fb27/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:243 errors:0 dropped:0 overruns:0 frame:0
          TX packets:250 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:207655 (202.7 KiB)  TX bytes:34513 (33.7 KiB)
          Interrupt:185 Base address:0xd800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)

---

### Post by weaver4 on 2007-01-24
I ran networking restart and it did not fix the problem, but it gave me alot of errors.

Here is the output:

==========================================

 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
SIOCSIFNETMASK: Invalid argument
Failed to bring up eth0.

---

### Post by weaver4 on 2007-01-24
I did two things.

I changed the server name from ubuntu-server to ubuntuserver and then I re-entered all the static-ip address info, did a restart and it then it worked.

Explain That!

---

### Post by kebes on 2007-01-24
> **weaver4 said:**
> I changed the server name from ubuntu-server to ubuntuserver and then I re-entered all the static-ip address info, did a restart and it then it worked. Explain That!

Er... maybe just by changing one setting you forced the configuration to be reloaded.... or something... Anyways the important thing is that it now works!

---

