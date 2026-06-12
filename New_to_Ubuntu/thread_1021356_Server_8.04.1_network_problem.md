---
title: "Server 8.04.1 network problem"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by kaissa on 2008-12-25
Hello,

  I have searched for a solution for this problem on the forums. The solutions mentioned did not help me. I cannot ping to my router. Here is the information:

1. ifconfig:
eth0 Link encap:Ethernet HWaddr 00:d0:b7:85:d6:68
inet addr:192.168.1.19 Bcast:192.168.1.255 Mask:255.255.255.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 KB) TX bytes:0 (0.0 KB)

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:904 (904.0 B) TX bytes:904 (904.0 B)

2. network
interfaces:
address 192.168.1.19
netmask 255.255.255.0
gateway 192.168.1.1
# dns-* options are implemented by the resolvconf package, if installed
dns-nameservers 192.168.1.1 195.175.39.40
dns-search PBNet

3. resolv.conf
nameserver 192.168.1.1
nameserver 195.175.39.40

4.netstat -rn
Destination   gateway  genmask   flags    mss  window  irtt ifae
192.168.1.0    0.0.0.0  255.255.255.0 u   0     0      0    eth0
0.0.0.0        192.168.1.1 0.0.0.0    ug  0     0      0    eth0

Thank you for your time,

---

### Post by linux_tech on 2008-12-25
what is output of 
```
ip neigh
```

---

### Post by linux_tech on 2008-12-25
also 
```
cat /etc/network/interfaces
```

---

### Post by kaissa on 2008-12-26
ip neigh shows nothing. I get back to the command prompt.

cat /etc/network/interfaces:

 # ... loop network ..
  auto lo
  iface lo inet loopback

  # the primary network interface
  auto eth0
  iface eth0 inet static
     address  192.168.1.19
     netmask 255.255.255.0
     gateway 192.168.1.1
     dns-nameservers 192.168.1.1 195.175.3.40
     dns-search PBNet

Thanks for your time,

---

### Post by linux_tech on 2009-01-06
Your interfaces file does not look complete;
try adding

network 192.168.1.0

broadcast 192.168.1.255


then restart the networking service

  ```
  sudo /etc/init.d/networking restart
```

---

