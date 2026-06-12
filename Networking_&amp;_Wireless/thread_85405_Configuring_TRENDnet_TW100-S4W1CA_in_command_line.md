---
title: "Configuring TRENDnet TW100-S4W1CA in command line"
date: 2005-11-02
forum: Networking &amp; Wireless
---

### Post by dmh-bidlah on 2005-11-02
Hello.
I recently bought a TRENDnet router. I've configured it to use DHCP. I have to boxes, one with Kubuntu Breezy and the other Xubuntu Breezy. I've set up the router on the Kubuntu box using the KDE System Settings Network Settings tab. I've set eth0 to use DCHP and to activate when the PC starts.
Now i would also loki to do that on the other computer, but it doesn't have the KDE System Settings. So how would I go about configuring eth0 to use dhcp in command line.
Here is the relevant info on my Kubuntu box, which connects to the Internet, can access the router etc.

```
joosep@Edasi-1:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0C:6E:94:85:D0
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:6eff:fe94:85d0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21659 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21956 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:15489890 (14.7 MiB)  TX bytes:3133052 (2.9 MiB)
          Interrupt:23 Base address:0xa400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:664 errors:0 dropped:0 overruns:0 frame:0
          TX packets:664 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:23426 (22.8 KiB)  TX bytes:23426 (22.8 KiB)


```

```

joosep@Edasi-1:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```

```
joosep@Edasi-1:~$ cat /etc/hosts
127.0.0.1 localhost Edasi-1 localhost.localdomain

# The following lines are desirable for IPv6 capable hosts
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
joosep@Edasi-1:~$     
```

```
joosep@Edasi-1:~$ cat /etc/resolv.conf
nameserver 192.168.1.1
```
But I cannot find where the eth0 settings are saved...
Thanks for any help!

---

### Post by mips on 2005-11-02
System->Administration->Networking

---

