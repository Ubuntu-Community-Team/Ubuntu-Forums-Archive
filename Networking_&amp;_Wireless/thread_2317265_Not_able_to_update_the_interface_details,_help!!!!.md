---
title: "Not able to update the interface details, help!!!!"
date: 2016-03-15
forum: Networking &amp; Wireless
---

### Post by soamz on 2016-03-15
I have a server with public IP and its online and working fine. Public IP is configured at eth0. 

Its a SNMP monitoring server, so I connected a cable from my access layer switch to the eth1 and did sudo nano /etc/network/interfaces

And added two private IP virtual interfaces to eth1:1 and eth1:2

Then did sudo service networking restart
But it says, 

stop : Job failed while stopping
start : Job is already running : networking 


Already tried doing ifconfig eth1 down and up. 
Still no go. 

What am I missing ?

[ATTACH=CONFIG]267820[/ATTACH][ATTACH=CONFIG]267819[/ATTACH]

---

### Post by michi1983 on 2016-03-16
Hi,

try a ```
sudo /etc/init.d/networking restart
```
or a ```
sudo ifdown eth1 && sudo ifup eth1
```

---

