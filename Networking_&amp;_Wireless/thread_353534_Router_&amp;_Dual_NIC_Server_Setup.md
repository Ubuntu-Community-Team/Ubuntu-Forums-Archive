---
title: "Router &amp; Dual NIC Server Setup"
date: 2007-02-04
forum: Networking &amp; Wireless
---

### Post by smokey_58au on 2007-02-04
I'm a newbie to Linux Ubuntu and after having been so impressed with it on my desktop I have decided to jump in and replace my SBS 2003 with the Dapper LTS Server.  My question relates to the best way to set up my home office config.  My current setup is:

ADSL Modem/Router------->Server (2 NICs)------->3 x XP Workstations

I have a VOIP phone and wireless access point that both connect directly to the router so that they maintain connectivity if the server is down.

I would like anyone's advice on whether I should enable the NAT, Firewall & DHCP on my modem/router or hand over some/all of those tasks to the server. Given that my first line of defence is the router, what additional security should I install on my server - I am thinking Squid and Dansguardian in addition to the separation of the internal networks via the NICS?  Also, can you please help me with the settings required to put my NICS on separate networks (they are currently on 192.168.10.xx - external, and 192.168.0.xx - internal) so that the workstations (on the 0.xx network) can access the internet?  Thanks in anticipation of any assistance.

Cheers,

Rob

---

### Post by smokey_58au on 2007-02-05
Still no replies but I have pushed on and I'm stuck between the 2 NIC's.  I can ping from the local PC's (192.168.0.xx) to both server NIC's (192.168.0.10 and 192.168.10.3) but they can't ping my router (192.168.10.1). The server (192.168.10.3) can access the router (192.168.10.1) and internet ok but can't ping the local PC's. I think it will be a routing issue but networking isn't my strong point and I would appreciate any assistance.  I am using static IP's and don't have DHCP or DNS set up on the server yet as I just want to establish full connectivity first. 

Any help would be greatly appreciated!

Here is the output of ipconfig -a:

eth0      Link encap:Ethernet  HWaddr 00:0C:F1:D5:7C:EF
          inet addr:192.168.10.3  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:f1ff:fed5:7cef/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:713 errors:0 dropped:0 overruns:0 frame:0
          TX packets:118 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:202914 (198.1 KiB)  TX bytes:14199 (13.8 KiB)
          Base address:0x8c00 Memory:fc9e0000-fca00000

eth1      Link encap:Ethernet  HWaddr 00:0C:F1:D5:7C:F0
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:f1ff:fed5:7cf0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:861 errors:0 dropped:0 overruns:0 frame:0
          TX packets:476 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:66390 (64.8 KiB)  TX bytes:26288 (25.6 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:328 (328.0 b)  TX bytes:328 (328.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

Here is the my /etc/network/interfaces file:

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.10.3
        netmask 255.255.255.0
        network 192.168.10.0
        broadcast 192.168.10.255
        gateway 192.168.10.1
        # dns-* options are implemented by the resolvconf package, if installed
        # dns-nameservers 192.168.10.1

# The secondary network interface
auto eth1
iface eth1 inet static
        address 192.168.0.10
        netmask 255.255.255.0
        network 192.168.0.10
        broadcast 192.168.0.255
        gateway 192.168.10.3
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.10.3
        # up route add -net 192.168.10.1 netmask 255.255.255.0
        # down route del -net 192.168.10.1 netmask 255.255.255.0

---

