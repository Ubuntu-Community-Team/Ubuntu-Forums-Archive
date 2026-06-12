---
title: "[server 12.04] syslog showing DHCPDISCOVER on eth0 (which is a slave to my bond0)"
date: 2014-01-22
forum: Networking &amp; Wireless
---

### Post by david144 on 2014-01-22
This system is a headless iSCSI target server, this isn't a critical problem just something confusing to me as I'm not sure why it would happen on a manual config
Any idea why my syslog is showing this:
```
Jan 22 20:35:08 iSCSI-SAN dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Jan 22 20:35:19 iSCSI-SAN dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Jan 22 20:35:31 iSCSI-SAN dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Jan 22 20:35:41 iSCSI-SAN dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
Jan 22 20:35:57 iSCSI-SAN dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21

```

eth0 -> bond0 slave (netgear ga311)
eth1 -> primary network (onboard NVidia adapter)
eth2 -> bond0 slave (netgear ga311)

ifconfig -a
```
bond0     Link encap:Ethernet  HWaddr 00:00:00:00:00:00
          inet addr:172.16.255.1  Bcast:172.16.255.255  Mask:255.255.255.0
          BROADCAST MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
eth0      Link encap:Ethernet  HWaddr 00:22:3f:f6:35:b9
          inet addr:172.16.255.1  Bcast:172.16.255.255  Mask:255.255.255.0
          inet6 addr: fe80::222:3fff:fef6:35b9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:58304616 errors:0 dropped:7 overruns:0 frame:0
          TX packets:52551243 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:56412919122 (56.4 GB)  TX bytes:52573947022 (52.5 GB)
eth1      Link encap:Ethernet  HWaddr 00:04:4b:03:c6:84
          inet addr:192.168.4.6  Bcast:192.168.4.255  Mask:255.255.255.0
          inet6 addr: fe80::204:4bff:fe03:c684/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:58767 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13660 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:17114823 (17.1 MB)  TX bytes:1237596 (1.2 MB)
eth2      Link encap:Ethernet  HWaddr 00:22:3f:f6:86:fb
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:157 errors:0 dropped:0 overruns:0 frame:0
          TX packets:157 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:16720 (16.7 KB)  TX bytes:16720 (16.7 KB)

```

interfaces:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto eth1
iface eth1 inet dhcp

auto bond0
iface bond0 inet static
address 172.16.255.1
netmask 255.255.255.0
bond-mode 6
bond-miimon 100

auto eth0
iface eth0 inet manual
bond-master bond0

auto eth2
iface eth2 inet manual
bond-master bond0

bond-slaves eth0 eth2

```

I was intending to do LACP but the switch I ordered didn't support it like the brochure said so I'm waiting on a new switch in the mean while I'm using mode 6.

While I was troubleshooting another unrelated issue with my cron jobs I saw these dhclient lines in the syslog and am wondering what the heck it's doing, ps aux only shows dhclient3 running on eth1 which is my lan and what I want using dhcp to get it's reserved address from the dhcp server.
```

root       954  0.0  0.0   7272  1016 ?        Ss   Jan20   0:00 dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.eth1.pid -lf /var/lib/dhcp/dhclient.eth1.leases -1 eth1

```

Thanks for any assistance in advance :)

---

### Post by david144 on 2014-01-23
..after having trouble just working without the balance-alb and trying to get my single nic to take over the IP address by commenting out everything after eth1 and re-doing my eth0, I'd come to the conclusion that wicd was no longer worth it. (I couldn't see my Netgear GA311's until I installed wicd after reading several other forums and blogs talking about wicd magically making the RTL8169S work and it of course made them work but somewhere along the line after my bond started acting up I thought hopefully I can just apt-get remove it)

Anyways after removing, purging, cleaning, and dpkg purging, my nics still showed up in ifconfig, they also started acting like /etc/network/interfaces was telling them to, and was no longer receiving dhclient messages in the syslog for adapters which were static.

I'll work on re-creating the bond and testing again but I think this can probably be closed, I'll mark it solved once I get the bond re-tested.

---

