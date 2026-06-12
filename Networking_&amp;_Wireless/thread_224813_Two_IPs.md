---
title: "Two IPs"
date: 2006-07-28
forum: Networking &amp; Wireless
---

### Post by skizz on 2006-07-28
Yes. I am using 2 IPs on my Windoze machine. The first (primary), 85.204.XXX.XXX is used for Internet connection and the second one (secondary), 10.10.XXX.XXX is used for IP 2 IP (direct connect) connection through my ISP's network. The output of my "ipconfig /all" in Windoze looks like this: 

> Windows IP Configuration:

        Host Name . . . . . . . . . . . . : xxxxx-c6bd049b0
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : SiS 900-Based PCI Fast Ethernet Adap
ter
        Physical Address. . . . . . . . . : 00-0A-E6-62-39-AF
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 85.204.110.139
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        IP Address. . . . . . . . . . . . : 10.10.110.139
        Subnet Mask . . . . . . . . . . . : 255.255.0.0
        Default Gateway . . . . . . . . . : 85.204.110.1
        DNS Servers . . . . . . . . . . . : 212.146.75.6
                                            212.146.75.98

Am I able to set-up a dual-IP connection in Ubuntu 6.06 LTS?

Thnks,
A.

---

### Post by steve.horsley on 2006-07-28
I know you can do it with ifconfig - like this:
> steve@StevesPC:~$ sudo ifconfig eth0:1 10.1.1.1 netmask 255.0.0.0
Password:
steve@StevesPC:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:85:31:30:14
          inet addr:192.168.8.101  Bcast:192.168.8.255  Mask:255.255.255.0
          inet6 addr: fe80::214:85ff:fe31:3014/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35591 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36650 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:14086630 (13.4 MiB)  TX bytes:2888195 (2.7 MiB)
          Interrupt:217 Base address:0x8000

eth0:1    Link encap:Ethernet  HWaddr 00:14:85:31:30:14
          inet addr:10.1.1.1  Bcast:10.255.255.255  Mask:255.0.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:217 Base address:0x8000



You may be able to manually edit /etc/network/interfaces and add it in there, but I'm not sure, I've never tried that.

---

### Post by SigmaX on 2006-07-28
Edit your /etc/network/interfaces to something similar to the following, by your configeration needs:

```
auto eth0
iface eth0 inet static
[INDENT]address 192.168.0.100
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1[/INDENT]
auto eth0:0
iface eth0:0 inet static
[INDENT]address 192.168.0.101
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1[/INDENT]

```

SigmaX

---

