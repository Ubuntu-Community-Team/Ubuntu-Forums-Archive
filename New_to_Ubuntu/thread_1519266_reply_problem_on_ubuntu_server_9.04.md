---
title: "reply problem on ubuntu server 9.04"
date: 2010-06-27
forum: New to Ubuntu
---

### Post by sihar on 2010-06-27
Dear ubuntu community

I have problem on ping 
which case
ubuntu server : 192.168.46.3
gateway : 192.168.46.1

when I ping gateway from ubuntu server, I got output
From 192.168.46.3.................. destination host unreachable
64 bytes from 192.168.46.1

but, when I ping gateway from other computer, I got good output.
Please help me.
Any suggestions are welcome.

---

### Post by CharlesA on 2010-06-27
Please post the output of these commands:

```
ifconfig
```

```
route
```

---

### Post by sihar on 2010-06-27
ifconfig
---
eth0
inet addr: 192.168.46.3 bcast:192.168.46.255 mask:255.255.255.0

route
---
destination    gateway   genmask
192.168.46.0 *             255.255.255.0

---

### Post by CharlesA on 2010-06-27
route should look like this:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
localnet        *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1	0.0.0.0         UG    100    0        0 eth0

```

---

### Post by sihar on 2010-06-27
I cut some

here the detail
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.46.0    *               255.255.255.0   U     0      0        0 eth0

---

### Post by CharlesA on 2010-06-27
Try running this:

```
sudo route add default gw 192.168.46.1 eth0
```

---

### Post by sihar on 2010-06-27
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.46.0    *               255.255.255.0   U     0      0        0 eth0
default        192.168.46.1    0.0.0.0        UG    0         0          0 eth0
```the output still "destination host unreachable"
T_T

---

### Post by CharlesA on 2010-06-27
Is the machine getting an IP from DHCP or is it using a static IP?

---

### Post by sihar on 2010-06-28
static IP sir

---

### Post by CharlesA on 2010-06-28
Can you post the output of /etc/network/interfaces?

---

### Post by sihar on 2010-06-28
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.46.3
network 192.168.46.0
netmask 255.255.255.0
broadcast 192.168.46.255
#gateway 192.168.1.1
```

---

### Post by CharlesA on 2010-06-28
That's the problem then, you have no gateway or dns servers listed.

This is what mine says:

```
iface eth0 inet static
        address 192.168.1.2
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        dns-nameservers 192.168.1.1
        dns-search asgard.lcl


```

Uncomment gateway (remove the #) and change it to 192.168.46.1, add in your DNS servers as well, then restart networking/reboot machine.

See if that does anything.

---

### Post by sihar on 2010-06-29
after go desperate.
I go to hardware division.
I told him to check the computer whether the computer have some problem.
He check RJ45 connector, and he assume the cable not in good condition.
Although that, the cable still work in some computer.
After that, he renew the connector and it works now.

Thanks for your support, Mr. CharlesA.


Warm regards,


Sihar

---

