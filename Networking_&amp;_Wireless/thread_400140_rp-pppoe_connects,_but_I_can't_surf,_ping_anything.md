---
title: "rp-pppoe connects, but I can't surf, ping anything etc."
date: 2007-04-03
forum: Networking &amp; Wireless
---

### Post by spock84 on 2007-04-03
I tried googling the problem, but couldn't find anything useful.

What can I do about it? :)

---

### Post by gborzi on 2007-04-03
I have had the same problem with "sudo pon dsl-provider" in a special situation: when the PC gets an IP address through dhcp from the ADSL modem and I use the pon command, I could not surf and ping. Only the name resolution works (i.e. nslookup). I solved this problem by adding the line > replacedefaultroute to the /etc/ppp/peers/dsl-provider file, just after the defaultroute line. I hope this applies to rp-pppoe also.

---

### Post by spock84 on 2007-04-03
After some more googling I saw someone recommending trying the command 'ifconfig eth0 down'. I have no idea what it does, but it solved the problem. :D

---

### Post by gborzi on 2007-04-03
That command (ifconfig eth0 down) actually shut down the driver for eth0, so that rp-pppoe can re-activate it with the right configuration.

---

### Post by spock84 on 2007-04-03
Cool. Thanks. Is it permanent? It seems to be..

---

### Post by gborzi on 2007-04-03
> **spock84 said:**
> Cool. Thanks. Is it permanent? It seems to be..

Well, it depends on your hardware. I'll try to explain it examining two possibilities:
[LIST=1]
[*]Your ADSL ethernet modem is on and you turn on the PC or do a network restart (sudo /etc/init.d/networking restart): your eth0 interface will get an IP with and a gateway from the modem.
[*]You turn on the modem while the PC is already on: depending on the hardware the OS may detect that there is a dhcp server and get an IP with and a gateway as before; or it may not detect anything and leave the interface unconfigured and so ready for rp-pppoe.
[/LIST]

You can look at what happens using the *route -n* and *ifconfig* command. The former command shows you the routing table of the kernel, the latter without arguments the interface configuration. For example on my system *route -n* gives the following output ```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.100.1   0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     0.0.0.0         255.255.255.224 U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0
```
Look at the last line. It shows that for generic IP addresses (0.0.0.0) the ppp0 interface is used. If you don't turn off eth0 before using rp-pppoe, the eth0 interface is used for generic addresses, but it can't actually go outside its range of addresses.

Hope this is clear.

---

