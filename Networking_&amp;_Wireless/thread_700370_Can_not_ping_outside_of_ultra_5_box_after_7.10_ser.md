---
title: "Can not ping outside of ultra 5 box after 7.10 server install."
date: 2008-02-18
forum: Networking &amp; Wireless
---

### Post by shakerj on 2008-02-18
Can not ping outside of ultra 5 box after 7.10 server install. 

--------------------------------------------------------------------------------

Hello,

I have 12 Ultra Sparc5 and 14 Ultra Sparc 10 systems I am in the process of moving from Solaris 8 to Ubuntu 7.10 Server edition.

I have loaded my first system with Ubuntu release 7.10 Server on 1 of the Ultra 5 systems.

I can ping the localhost and the IP at Eth0 but fail to ping anything on the local network. 

The /etc/hosts file has all the entries. But can not seem to ping outside the box. 
The /etc/network/interfaces file also had the appropriate Ip's setup at install with the Eth0, netmask, Default gateway and dns servers. And they are in the file.
I administered the setups on all Solaris systems and they are functioning fine. We are utilizing subnet but this is not the issue because I cannot ping the default gateway. The Card was detected fine at install and worked before the installation with solaris. 

ip route

130.140.224.0 /22 dev eth0 proto kernel scope link src 130.140.224.101 default via 130.224.254 dev eth0 metric 100

Are there any known bugs that anyone is aware of?
I hate to ask being that I have administered so many systems with Solaris.

Thanks for any help..

---

