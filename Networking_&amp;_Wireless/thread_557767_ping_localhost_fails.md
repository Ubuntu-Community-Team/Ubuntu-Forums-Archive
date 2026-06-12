---
title: "ping localhost fails"
date: 2007-09-23
forum: Networking &amp; Wireless
---

### Post by dalailama on 2007-09-23
I cannot ping localhost. It just hangs. However internet access is no problem.

1) my /etc/network/interfaces
> 
auto lo
iface lo inet loopback

mapping hotplug
        script grep
        map eth0

iface eth0 inet dhcp


2) # cat /proc/sys/net/ipv4/icmp_echo_ignore_all
     0

3) # iptables -n -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

4)

# ifconfig lo
lo        Link encap:Local Loopback
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:62268 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62268 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5764607 (5.4 MiB)  TX bytes:5764607 (5.4 MiB)

Does anyone have any other suggestions ?

---

### Post by spd106 on 2007-09-23
You appear to have lost the IPv4 address on lo. What do you have in the /etc/hosts file?

---

### Post by dalailama on 2007-09-23
This is what my localhost looks like:

127.0.0.1       localhost.localdomain   localhost       casbah

casbah is my hostname.

---

### Post by noob12 on 2007-09-23
Make sure this entry is still present in your **/etc/network/interfaces** file.  If not, add it:
```

auto lo
iface lo inet loopback

```
Then I'd reboot.

---

