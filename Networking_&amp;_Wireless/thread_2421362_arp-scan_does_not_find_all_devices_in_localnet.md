---
title: "arp-scan does not find all devices in localnet"
date: 2019-06-20
forum: Networking &amp; Wireless
---

### Post by thomas109 on 2019-06-20
Hi
I have a subnet 

```
192.168.0.0/20
```

running 
```
arp-scan 192.168.0.0/20
```

does not give ma all devices .

from different computers I get different results.....

any hints how to identify why arp-scan does not discover all?

also tried    ```
[COLOR=#000000][FONT=verdana]nmap sP 192.168.1.0/24[/FONT][/COLOR]
```

Thanks T

---

### Post by TheFu on 2019-06-20
The local arp table only contains hosts the local machine has connected to without going through a router.  i.e. ethernet-direct connections.
**sudo nmap -sT 192.168.1.0/20 **will find them all, assuming that is the correct subnet. Having the correct options is important. nmap requires sudo. Options require a '-'

---

### Post by thomas109 on 2019-06-21
> **TheFu said:**
> The local arp table only contains hosts the local machine has connected to without going through a router.  i.e. ethernet-direct connections.
**sudo nmap -sT 192.168.1.0/20 **will find them all, assuming that is the correct subnet. Having the correct options is important. nmap requires sudo. Options require a '-'

Hi thanks for your support,

I tried:    ```
sudo nmap -sT 192.168.0.0/20
```
having some IPs in the range 
192.168.13.x but they where not discovered....

I think they are part of the subnet 192.168.0.0/20  , right?

can ping ip 192.168.13.61 but this is not identified by nmap? is this possible?

strange and confused T

---

### Post by TheFu on 2019-06-21
The nmap command above tries to ping the host before bothering with a scan. If the IP doesn't respond to a ping, then it doesn't get scanned.  nmap can be told to scan without pinging first.  The manpage has that option spelled out.  The nmap manpage is a **must read**.

Is /20 the real subnet from the network admin?  You can't just make up whatever you like. The real subnet and the subnet used in these commands need to match.

---

