---
title: "Changed router, &quot;Default Route&quot; still points to old router address"
date: 2020-12-02
forum: Networking &amp; Wireless
---

### Post by sp40140 on 2020-12-02
I had Asus router (192.168.29.1). It broke. I got new TP-Link (192.168.0.1).
The new router is up and running. All the devices are connected and no issues.
However, one desktop can't connect to internet. It is hard wired.
When I look at the connection profile, it has"
Correct IP address (issued by new router) under 192.168.0.1/24
Correct DNS (new router) 192.168.0.1.

Wrong "Default Route" 192.168.29.1 (pointing to old router ip).

I looked into /etc/netplan. But it looks like the "renderer : NetworkManager". And there's nothing else in the config/yaml file.
I also, looked around in /etc/network and /etc/NetworkManager directories. But haven't been able to track this entry down.

Could you tell me how to correct this?

Output from command: ip address:

```

1: lo:<LOOPBACK, UP, LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    inet 127.0.0.1/8 scope host lo
        valid_lft forever preferred_lft forever
2: eno1: <BROADCAST, MULTICAST, UP, LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    inet 192.168.0.130/24 brd 192.168.0.255 scope global dynamic noprefixroute eno1
        valid_lft 4459sec preferred_lft 4459sec
    inet 192.168.29.195/24 brd 192.168.29.255 scope global noprefixroute eno1
        valid_lft forever preferred_lft forever
3: virbr0 <NO-CARRIER, BROADCASE, MULTICAST, UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    inet 192.168.122.1/24 brd 192.168.122.255 scope global virbr0
        valid_lft forever preferred_lft forever
```

---

### Post by TheFu on 2020-12-02
```
2: eno1: <BROADCAST, MULTICAST, UP, LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    inet 192.168.0.130/24 brd 192.168.0.255 scope global dynamic noprefixroute eno1
        valid_lft 4459sec preferred_lft 4459sec
    inet 192.168.29.195/24 brd 192.168.29.255 scope global noprefixroute eno1
        valid_lft forever preferred_lft forever
```
Somehow you have 2 IPs assigned to the same NIC.
Also, showing the **route -n** output would be helpful.  **ip** command output is ugly.

If you've looked in the GUI, in /etc/netplan/, in /etc/network/ then I don't know where else you should have placed network configs.  You could manually just bring down the unwanted IP.  Wouldn't hurt to check the log files.

BTW, network configs has changed drastically the last few years. Would be nice to know which release you are running and whether DHCP is used.

---

### Post by sp40140 on 2020-12-03
Thank you.

How do I manually bring down the unwanted IP?

output from route -n:
```

Destination     Gateway             Genmast           Flags     Metric     Ref     Use     Iface
0.0.0.0           192.168.29.1      0.0.0.0             UG        202         0       0         eno1
0.0.0.0             192.168.0.1      0.0.0.0             UG        20100     0       0         eno1
169.254.0.0      0.0.0.0             255.255.0.0      U          1000       0       0         virbr0
192.168.0.0      0.0.0.0             255.255.255.0  U          100         0       0         eno1
192.168.29.0    0.0.0.0             255.255.255.0  U          202         0       0         eno1
192.168.122.0  0.0.0.0             255.255.255.0  U           100        0       0         virbr0

```
*forgive the formatting. I had to type it up since the machine's not connected.

---

### Post by TheFu on 2020-12-03
> **TheFu said:**
> 
BTW, network configs has changed drastically the last few years. Would be nice to know which release you are running and whether DHCP is used.

Answer the questions so people can help. Good luck.

---

### Post by sp40140 on 2020-12-03
Version is 20.04.1 LTS 64 bit.
DHCP is enabled and automatic.

---

### Post by sp40140 on 2020-12-07
Any ideas on how to fix this?

---

### Post by sp40140 on 2020-12-11
I re-built the server. 
Network is fine now.

---

