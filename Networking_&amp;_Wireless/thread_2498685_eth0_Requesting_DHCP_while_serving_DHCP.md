---
title: "eth0 Requesting DHCP while serving DHCP"
date: 2024-06-23
forum: Networking &amp; Wireless
---

### Post by armegeden on 2024-06-23
Hello,

Odd one here. I have a Pi setup to join apartment Wireless (wlan0), then share that connection out eth0 for my Philips Hue that only accepts ethernet.  I've had this working for months.  

The problem is it randomly drops every few weeks, or a restart could cause it to stop.

```

$ uname -aLinux ubuntu 5.15.0-1055-raspi #58-Ubuntu SMP PREEMPT Sat May 4 03:50:14 UTC 2024 armv7l armv7l armv7l GNU/Linux

```

I think the problem is:

My ISC-DHCP server shows this client info:
[COLOR=#010101][FONT=RobotoMonoLocal]b8:27:eb:0a:**83:a2** with 10.0.0.114

[/FONT][/COLOR]The problem is my eth0 should be 10.0.0.1 via netplan:
```

s@ubuntu:~$ more /etc/netplan/50-cloud-init.yamlnetwork:
  version: 2
  renderer: networkd
  wifis:
    wlan0:
      access-points:
        WiFi:
          password: PASS
      dhcp4: true
      dhcp4-overrides:
        route-metric: 1
      optional: true
**  ethernets:**
**    eth0:**
**      dhcp4: no**
**      addresses:**
**        - 10.0.0.1/24**
      routes:
        - to: default
          via: 172.20.1.1
      nameservers:
        addresses: [8.8.8.8,8.8.4.4]
syn@ubuntu:~$

```

The 172 address is my apartments default.
As you can see, I tried "dhcp4:no" for eth0 with no luck.

```

s@ubuntu:~$ **ifconfig**
**eth0**: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::ba27:ebff:fe0a:83a2  prefixlen 64  scopeid 0x20<link>
        ether b8:27:eb:0a:**83:a2**  txqueuelen 1000  (Ethernet)
        RX packets 939  bytes 68477 (68.4 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 890  bytes 134167 (134.1 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


**eth0:avahi**: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet **169.254.11.75**  netmask 255.255.0.0  broadcast 169.254.255.255
        ether b8:27:eb:0a:**83:a2**  txqueuelen 1000  (Ethernet)

```

I have no idea what that avahi interface is, but it keeps showing up in /var/log/syslog:
```

Jun 23 20:48:58 ubuntu dhclient[844]: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9 (xid=0xced1d262)
Jun 23 20:49:07 ubuntu **dhclient**[844]: DHCPDISCOVER on **eth0 **to 255.255.255.255 port 67 interval 9 (xid=0xced1d262)
Jun 23 20:49:08 ubuntu systemd[1]: Starting Cleanup of Temporary Directories...
Jun 23 20:49:08 ubuntu systemd[1]: systemd-tmpfiles-clean.service: Deactivated successfully.
Jun 23 20:49:08 ubuntu systemd[1]: Finished Cleanup of Temporary Directories.
Jun 23 20:49:16 ubuntu dhclient[844]: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9 (xid=0xced1d262)
Jun 23 20:49:25 ubuntu dhclient[844]: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13 (xid=0xced1d262)
Jun 23 20:49:38 ubuntu dhclient[844]: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10 (xid=0xced1d262)
Jun 23 20:49:48 ubuntu dhclient[844]: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16 (xid=0xced1d262)
Jun 23 20:50:04 ubuntu dhclient[844]: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21 (xid=0xced1d262)
Jun 23 20:50:25 ubuntu dhclient[844]: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21 (xid=0xced1d262)
Jun 23 20:50:46 ubuntu dhclient[844]: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8 (xid=0xced1d262)
Jun 23 20:50:54 ubuntu dhclient[844]: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20 (xid=0xced1d262)
Jun 23 20:51:14 ubuntu dhclient[844]: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18 (xid=0xced1d262)
Jun 23 20:51:32 ubuntu dhclient[844]: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7 (xid=0xced1d262)
Jun 23 20:51:39 ubuntu dhclient[844]: No DHCPOFFERS received.
Jun 23 20:51:39 ubuntu dhclient[844]: No working leases in persistent database - sleeping.
Jun 23 20:51:39 ubuntu avahi-autoipd(eth0)[1791]: Found user 'avahi-autoipd' (UID 116) and group 'avahi-autoipd' (GID 125).
Jun 23 20:51:39 ubuntu avahi-autoipd(eth0)[1791]: Successfully called chroot().
Jun 23 20:51:39 ubuntu avahi-autoipd(eth0)[1791]: Successfully dropped root privileges.
Jun 23 20:51:39 ubuntu avahi-autoipd(eth0)[1791]: Starting with address 169.254.11.75
Jun 23 20:51:44 ubuntu avahi-autoipd(eth0)[1791]: Callout BIND, address **169.254.11.75 on interface eth0**
Jun 23 20:51:44 ubuntu avahi-daemon[676]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.11.75.
Jun 23 20:51:44 ubuntu avahi-daemon[676]: New relevant interface eth0.IPv4 for mDNS.
Jun 23 20:51:44 ubuntu avahi-daemon[676]: Registering new address record for 169.254.11.75 on eth0.IPv4.
Jun 23 20:51:48 ubuntu avahi-autoipd(eth0)[1791]: Successfully claimed IP address 169.254.11.75
Jun 23 20:52:11 ubuntu systemd[1]: Started Session c1 of User syn.
Jun 23 20:52:12 ubuntu systemd[1]: session-c1.scope: Deactivated successfully.
Jun 23 20:57:35 ubuntu dhclient[844]: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (xid=0x58899428)
Jun 23 20:57:38 ubuntu dhclient[844]: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (xid=0x58899428)
Jun 23 20:57:41 ubuntu dhclient[844]: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8 (xid=0x58899428)

```

I'm not sure how it's happening, but it looks like my eth0 interface boots with 10.0.0.1, but at some point, b8:27:eb:0a:83:a2 (eth0!) requests a DHCP address, gets it, and overwrites 10.0.0.1 and everything goes dead.

Any ideas or suggestions? I would just like to set-and-forget this.  The Pi does nothing else but enable the connection on eth0.

Thank you for any advice!  This has been frustrating

---

