---
title: "Not able to configure a permanent VLAN"
date: 2016-03-30
forum: Networking &amp; Wireless
---

### Post by leti3 on 2016-03-30
Hello all,

I am new on Ubuntu, and I have to use the Version: Ubuntu 12.04.4 LTS.

I want to configure a VLAN, but I cannot reach the point to get it permanently...

What I did:

1/ Activate the module:
**sudo su -c 'echo "8021q" >> /etc/modules'**

2/ Update file /etc/network/interfaces: (it looks like now as below)
*auto eth0*
*iface eth0 inet static*
*address 192.168.111.111*
*netmask 255.255.255.0*
 
***auto eth0.4093***
***iface eth0.4093 inet static***
***address 192.168.101.111***
***netmask 255.255.255.0***
***vlan-raw-device eth0***
 
*auto eth1*
*iface eth1 inet static*
*address 192.168.121.111*
*netmask 255.255.255.0*


3/ I reboot and tried to activate the interface:
**set ifup eth0.4093**
Nothing happens and if I check with **ifconfig**, no VLAN4093 is listed

4/ However, using the **ip **command it works... and only adding this line (The ip addr is like already known because of the /etc/network/interfaces)
**ip link add link eth0 name eth0.4093 type vlan id 4093**


But each time I reboot and I check with **ifconfig**, the VLAN is no more listed...

Why the config I put in the /etc/network/interfaces is not taken completely in account?

Thanks for your feedback

---

### Post by michi1983 on 2016-03-30
Hi,

I can only recommend to do this tutorial step by step and it will work. 
[https://wiki.ubuntu.com/vlan](https://wiki.ubuntu.com/vlan)
I did the same on my Linux Server.

P.S. I would also suggest to update to Ubuntu 14.04 LTS, 12.04 is out of date.

---

### Post by leti3 on 2016-03-31
Hi Michi,

Tx for your feedback.
Actually, my VLAN works using the method I described...
The only think is: I lose it each time I reboot and I have to "relink" using just the command:
[B]ip link add link eth0 name eth0.4093 type vlan id 4093

[/B]I think you 're right, I should change my version and maybe it could solve all my PB, but I don't have the possibility for the moment.
I will push over this solution for the next week.
For the moment even if I am not satify, I found a workaround adding the Ip-command in my **rc.local** file but I would like to understand...

---

