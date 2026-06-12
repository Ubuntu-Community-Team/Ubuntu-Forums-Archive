---
title: "SSH issue or what ?"
date: 2018-08-01
forum: Networking &amp; Wireless
---

### Post by Vaclav Vasek on 2018-08-01
I have managed, for test purpose,  to activate BOTH Ethernet and WiFi connections on my SSH server. 
Is that OK? 

When I try SSH to Ethernet IP which was previously working solo I get this message:  

os64@os64-desktop:~$ ssh jim@10.0.1.38
ssh: connect to host 10.0.1.38 port 22: No route to host
os64@os64-desktop:~$ 

When I try SSH to WiFi IP I get no response: 

os64@os64-desktop:~$ ssh jim@10.42.0.1

Any help would be greatly appreciated.

---

### Post by SeijiSensei on 2018-08-01
Just choose one interface, presumably the Ethernet one.  Having both interfaces on the same network can create routing problems.

Using both interfaces adds no performance benefit unless you use [bonding]("https://help.ubuntu.com/community/UbuntuBonding").

---

### Post by Vaclav Vasek on 2018-08-01
Thanks for the reply , appreciate that. 

So for test purposes I'll try bonding.

---

