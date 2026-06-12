---
title: "Ethernet fails when resuming from suspend"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by AncientPC on 2009-02-10
The network monitor will show the connecting symbol "Trying to get network address" and then fail.  `sudo /etc/init.d/networking restart` and `sudo ifconfig eth0 down; sudo ifconfig eth0 up` doesn't help the situation.  I can try to connect again by selecting the Network Monitor > Auth eth0, but it just tries to connect and fails again.  Any suggestions?

---

### Post by jbrown96 on 2009-02-11
How about ```
sudo ddclient
``` to request a new IP address.

---

### Post by AncientPC on 2009-02-11
> **jbrown96 said:**
> How about ```
sudo ddclient
``` to request a new IP address.
I don't have that installed, but looking at the package contents it is for updating a dyndns.org address which I don't have.  I don't understand how this command might help.

---

### Post by jbrown96 on 2009-02-12
I'm sorry. I meant ```
sudo dhclient
```

---

### Post by AncientPC on 2009-02-12
When running `sudo dhclient` after resume from suspend:
```
ting@AncientPC:~$ sudo dhclient
[sudo] password for ting: 
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/pan0/5e:c5:c1:90:a8:ba
Sending on   LPF/pan0/5e:c5:c1:90:a8:ba
Listening on LPF/eth0/00:50:8d:d9:4a:42
Sending on   LPF/eth0/00:50:8d:d9:4a:42
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

Running the same command after rebooting:
```
ting@AncientPC:~$ sudo dhclient
[sudo] password for ting: 
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/pan0/52:82:25:6a:a9:d8
Sending on   LPF/pan0/52:82:25:6a:a9:d8
Listening on LPF/eth0/00:50:8d:d9:4a:42
Sending on   LPF/eth0/00:50:8d:d9:4a:42
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER of 192.168.1.23 from 192.168.1.1
DHCPREQUEST of 192.168.1.23 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.23 from 192.168.1.1
bound to 192.168.1.23 -- renewal in 35163 seconds.
```

---

### Post by da2na on 2009-02-26
I had the same problem with Ubuntu 8.10 x64...  This is a known bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/288281](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/288281)

Here's the fix:

Create or edit this file: /etc/pm/config.d/local
Add this line: SUSPEND_MODULES="forcedeth"
Save the file and that should do it...

Cheers,

-F

---

### Post by AncientPC on 2009-02-26
> **da2na said:**
> I had the same problem with Ubuntu 8.10 x64...  This is a known bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/288281](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/288281)

Here's the fix:

Create or edit this file: /etc/pm/config.d/local
Add this line: SUSPEND_MODULES="forcedeth"
Save the file and that should do it...

Cheers,

-F
That solved my problem immediately, thanks!

---

### Post by yeaitsdark on 2009-03-01
Thanks da2na. This was driving me crazy! With the way the economy is these days I've been trying to save money every way possible. Thank you very much :)

---

