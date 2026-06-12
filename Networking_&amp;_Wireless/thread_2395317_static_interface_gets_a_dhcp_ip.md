---
title: "static interface gets a dhcp ip?"
date: 2018-06-29
forum: Networking &amp; Wireless
---

### Post by sniper8752 on 2018-06-29
I have two interfaces.  One is set to static, the other, dhcp.   the dhcp did not pull a ip, so I did a dhclient, and it pulled one just fine.  Then I did an ip addr, and noticed that the static interface drew a ip as well.  I did a ifdown then ifup, and now it has two ips - the static one, and the dhcp one.  Why would a static interface pull an ip when running dhclient?  do I need to define the interface when I run dhclient? How do I drop the dhcp address on the static interface?

---

### Post by chili555 on 2018-06-29
Where are they defined? Network Manager? netplan? /etc/network/interfaces? Or where?

Please show us the details of the relevant files.

What is your Ubuntu version?```
lsb_release -a
```Is this a server or a desktop? A virtual machine? Or what?

Details, please.

---

### Post by sniper8752 on 2018-06-29
> **chili555 said:**
> Where are they defined? Network Manager? netplan? /etc/network/interfaces? Or where?

Please show us the details of the relevant files.

What is your Ubuntu version?```
lsb_release -a
```Is this a server or a desktop? A virtual machine? Or what?

Details, please.
They are defined in the interfaces file.
lsb returns ubuntu 16.04 (server)
It is a server. 

```

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
address x.x.x.x
netmask x.x.x.x


```

---

### Post by chili555 on 2018-06-30
> do I need to define the interface when I run dhclient? Ideally, yes, however, the typical method to get an IP address for interfaces defined in /etc/network/interfaces is to ifdown and then ifup the specific interface in question. For example:```
sudo ifdown eth0 && sudo ifup -v eth0
```The -v for verbose should give output that shows that the interface got an IP address by DHCP.

Likewise, this:```
sudo ifdown eth1 && sudo ifup -v eth1
```...should show that the designated static IP was given.

Check:```
ifconfig
```

---

