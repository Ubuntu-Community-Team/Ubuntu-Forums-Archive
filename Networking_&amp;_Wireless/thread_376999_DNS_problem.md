---
title: "DNS problem"
date: 2007-03-05
forum: Networking &amp; Wireless
---

### Post by mjskia1 on 2007-03-05
I tried installing Kvpnc and vpnc in order to try connecting to a VPN.   However, that didn't go so well, so I uninstalled them after I gave up trying to figure out the settings (using aptitude).  Somehow, and I really don't understand how at all, this hosed my DNS.  I can't do anything by domain name -- not WWW, not ping, not SSH, not e-mail -- but by IP addresses, I can at least get ping working.  I know it's not an external problem because the network is working fine for the dual-boot Windows.  Anyone know where the first place I should look is?

Thanks in advance!

---

### Post by Floppyjoe on 2007-03-05
This Link may be of help to you.

[http://www.opendns.com/start/unix.php](http://www.opendns.com/start/unix.php)

Floppyjoe

---

### Post by chili555 on 2007-03-05
The DNS nameservers are listed in /etc/resolv.conf. Ideally, if you connect with DHCP, when you do sudo ifdown <your_interface> followed by sudo ifup <your_interface> you will populate resolv at the same time you get an IP address from your ISP or router.

Not so ideally, you can go into the administration pages of your router and copy them off and sudo gedit /etc/resolv.conf to put them in. Here's mine, slightly obscured, for example: ```
chili@LAPTOP:~$ cat /etc/resolv.conf
nameserver 205.152.37.xx
nameserver 205.152.132.XX
```

And really, really not ideally, you can put in the Gateway IP address you get from route -n: ```
chili@LAPTOP:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

``` So, you would put in:```
nameserver 192.168.1.1
```

---

### Post by mjskia1 on 2007-03-05
Thanks to your help, I figured out the problem.  Somehow, probably related to the VPN, resolv.conf got wiped, which of course left me without any nameservers.  The ifdown and ifup fixed the problem, though I am a little curious as to why this didn't happen automatically on reboot.  Nevertheless, I have the Internet back and I've learned a little in the process.

Thanks again!

---

