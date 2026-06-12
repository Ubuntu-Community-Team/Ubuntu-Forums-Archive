---
title: "Configuring /etc/network/interface file"
date: 2014-04-04
forum: Networking &amp; Wireless
---

### Post by jwb2 on 2014-04-04
Hey there!
New Ubuntu user here, I've learned linux on Red Hat distrobutions (CentOS), when configuring my interfaces I used to configure them using the /etc/sysconfig/network-scripts/ifcfg-eth0 file. I think the equivalent in Unbuntu is /etc/network/interface. 
When I return cat /etc/network/interface all I get back is 

[PHP]
root@ubuntu:/etc/network$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback[/PHP]

In CentOS, when I configured /etc/sysconfig/network-scripts/ifcfg-eth0, I was able to assign my values easily, much like the feedback you get from ifconfig.

Btw, Im doing this primarily for static IP.

Thanks

---

### Post by tgalati4 on 2014-04-04
[http://askubuntu.com/questions/214170/whats-the-default-etc-network-interfaces](http://askubuntu.com/questions/214170/whats-the-default-etc-network-interfaces)

Reboot or follow the procedures below to restart networking:

[http://askubuntu.com/questions/103171/editing-network-interfaces-without-system-rebooting](http://askubuntu.com/questions/103171/editing-network-interfaces-without-system-rebooting)

---

### Post by jwb2 on 2014-04-04
so, just add in the values shown into the configuration file in your first link?

---

### Post by SeijiSensei on 2014-04-05
Take a look at [https://help.ubuntu.com/12.04/serverguide/network-configuration.html](https://help.ubuntu.com/12.04/serverguide/network-configuration.html).

You need to add a stanza for eth0 that looks like the one described in the "Static IP Address Assignment" section of that document:
```
auto eth0
iface eth0 inet static
address 10.0.0.100
netmask 255.255.255.0
gateway 10.0.0.1
```
If you want to specify the DNS servers the machine should use, add the line:
```
dns-nameservers 1.2.3.4 5.6.7.8
```
below the gateway directive with the correct addresses for the servers you wish to use.  Note the "s" on the end of "dns-nameservers;" it's easy to forget.  To add a default search domain, add a line like "dns-search example.com" with the domain(s) you wish to search in for unqualified hostnames.

---

