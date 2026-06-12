---
title: "Does not automatically obtain ip adress, DHCP does not work (Arris TM402 over usb)"
date: 2007-02-17
forum: Networking &amp; Wireless
---

### Post by Sasa Vilic on 2007-02-17
Hi, I am using Ubuntu 6.06 and I have cable modem Arris TM402. 

My problem is computer does not automatically obtain ip addres. (Provider chello, Vienna)

After I manually configure static ip addres, gateway and nameservers it works, but that is not solution for future. I have tried "sudo dhclient" and couldn't obtain ip adress.

Can it be solved?

regards,

Sasa Vilic

---

### Post by Sasa Vilic on 2007-02-18
Nobody have same problem and solution? :)

---

### Post by chili555 on 2007-02-18
Several approaches come to mind: first, I would do sudo ifdown eth0 (or whatever your relevent interface is) followed by sudo ifup eth0. Take note of the terminal output. Does the computer get an IP address? Or, does it just timeout with no DHCP offers?

Second, I would look in the administration page of the cable modem to see if the DHCP server is actually turned on. You can look in the documentation for the cable modem to see how to access the administration page. Usually it's a browser page you open, something like [http://192.168.100.1](http://192.168.100.1).

I would also look at your /etc/network/interfaces file to see if the relevent interface is set to use DHCP. It should read something like this:

```
auto eth0
iface eth0 inet dhcp
```

Post back and let us know.

---

### Post by Sasa Vilic on 2007-02-18
```
sudo ifdown eth2
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth2/00:13:11:7b:7d:30
Sending on   LPF/eth2/00:13:11:7b:7d:30
Sending on   Socket/fallback
```

```
salex@salex-laptop:~$ sudo ifup eth2
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth2/00:13:11:7b:7d:30
Sending on   LPF/eth2/00:13:11:7b:7d:30
Sending on   Socket/fallback
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 16
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

```
salex@salex-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

iface eth0 inet dhcp

iface eth1 inet dhcp

[B]auto eth2
iface eth2 inet dhcp[/B]

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto eth1

auto eth0
```

Getting ip by DHCP works on Windows but not on ubuntu, so I gues it that DHCP server is not turned down. (Connection through USB)

Connection through ethernet card does not work on windows or ubuntu, but i think that is because provider didn`t unlock that MAC address.

I tried also dhclient eth2, but end was same.

---

