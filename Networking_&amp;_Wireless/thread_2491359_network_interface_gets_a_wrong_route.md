---
title: "network interface gets a wrong route"
date: 2023-10-05
forum: Networking &amp; Wireless
---

### Post by bschopman2 on 2023-10-05
Running an up-to-date headless Ubuntu server I'm puzzled configuring my networking. My network interface keeps getting a wrong route assigned and therefore can't access internet after a reboot. I'll see:
```
$ ip route
default via 192.168.2.254 dev eno1 src 10.0.0.9 metric 202
10.0.0.0/24 dev eno1 proto dhcp scope link src 10.0.0.9 metric 202
192.168.2.254 dev eno1 scope link src 10.0.0.9 metric 202

```

I've been manually removing this erroneous default route (192.168.2.254) and adding the right one (10.0.0.1), which fixes it until the next reboot.
```

$ sudo route del default
$ sudo ip route add default via 10.0.0.1
$ ip route
default via 10.0.0.1 dev eno1
10.0.0.0/24 dev eno1 proto dhcp scope link src 10.0.0.9 metric 202
192.168.2.254 dev eno1 scope link src 10.0.0.9 metric 202

```

But I want to fix it properly. So I'm using netplan to assign a static ip:
```

$ ls /etc/netplan/
99_config.yaml
$ cat /etc/netplan/99_config.yaml

network:
  version: 2
  ethernets:
    eno1:
      dhcp4: no
      dhcp6: no
      addresses:
        - 10.0.0.8/24
      routes:
        - to: default
          via: 10.0.0.1
      nameservers:
          addresses: [10.0.0.1]

```

And I've removed /etc/network/interfaces to eliminate the possibility that the old ifupdown package does anything. I've actually gone as far as removing the package. Also, I don't have any NetworkManager config files.
```

$ ls /etc/network/interfaces*
ls: cannot access '/etc/network/interfaces*': No such file or directory
$ systemctl status NetworkManager
Unit NetworkManager.service could not be found.
$ ls /etc/NetworkManager/
ls: cannot access '/etc/NetworkManager/': No such file or directory
$ sudo apt remove ifupdown
$ apt policy ifupdown
ifupdown:
  Installed: (none)

```

But still get this mysterious default route to 192.168.2.254 after a reboot. No other machines on my network have this problem. Where can this come from when I've specified a static ip in netplan? Any other config files where this erroneous route could be set?

I'm running version 20.04.6 LTS.
```

$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.6 LTS
Release:    20.04
Codename:    focal

```

---

### Post by The Cog on 2023-10-05
Odd. Do you have any VPNs configured?
What happens if you run [FONT=Courier New]**sudo dhclient -v**[/FONT] ? I'm wondering if some dhcp rogue might be handing out wrong allocations. 
Metric 202 looks peculiar to me too. I would be tempted to look at [FONT=Courier New]**ip rule list**[/FONT] as well? Any odd rules?

---

### Post by bschopman2 on 2023-10-05
Thanks for your reply,  The Cog. The output of the dhclient and ip rules don't show anything strange (see output below). The VPN question is a very good one! I might have installed a protonvpn or maybe nordvpn client on it. I'm currently trying to find where I could have put config files, what packages I can find or what uninstallers are available.

```

$ sudo dhclient -v
Internet Systems Consortium DHCP Client 4.4.1
Copyright 2004-2018 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eno2/0c:c4:7a:80:3a:af
Sending on   LPF/eno2/0c:c4:7a:80:3a:af
Listening on LPF/eno1/0c:c4:7a:80:3a:ae
Sending on   LPF/eno1/0c:c4:7a:80:3a:ae
Sending on   Socket/fallback
DHCPDISCOVER on eno2 to 255.255.255.255 port 67 interval 3 (xid=0x4a95dd13)
DHCPDISCOVER on eno1 to 255.255.255.255 port 67 interval 3 (xid=0x907db771)
DHCPOFFER of 10.0.0.8 from 10.0.0.1
DHCPREQUEST for 10.0.0.8 on eno1 to 255.255.255.255 port 67 (xid=0x71b77d90)
DHCPACK of 10.0.0.8 from 10.0.0.1 (xid=0x907db771)
RTNETLINK answers: File exists
bound to 10.0.0.8 -- renewal in 406623 seconds.
$ ip rule list
0:    from all lookup local
32766:    from all lookup main
32767:    from all lookup default
$ sudo apt purge openvpn openresolv
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package 'openresolv' is not installed, so not removed
Package 'openvpn' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
$ ls /etc/openvpn*
ls: cannot access '/etc/openvpn*': No such file or directory
$ ls /opt/openvpn*
ls: cannot access '/opt/openvpn*': No such file or directory

```

edit: I don't believe I have a vpn client installed:
```

$ dpkg -l | grep protonvpn
$ sudo apt-get --purge remove 'nordvpn*'
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package nordvpn*
E: Couldn't find any package by glob 'nordvpn*'
E: Couldn't find any package by regex 'nordvpn*'
$ sudo dpkg -P nordvpn
dpkg: warning: ignoring request to remove nordvpn which isn't installed
$  sudo dpkg -P nordvpn-release
dpkg: warning: ignoring request to remove nordvpn-release which isn't installed
$ ls /usr/share/keyrings/
# no vpn related files
$ ls /etc/apt/sources.list.d
# no vpn related files

```

---

### Post by The Cog on 2023-10-05
Curiouser and curiouser. All I can think of now is to see if that address is mentioned anywhere in /etc or other places where config might be stashed: 
[FONT=Courier New]**sudo grep -r "192\.168\.2\.254" /etc**[/FONT]
Or see if the address appears immediately after boot, or some time later, 
or see if it reappears when you restart networking: [FONT=Courier New]**sudo systemctl restart networking**[/FONT]

---

### Post by bschopman2 on 2023-10-06
Bingo, this must be it. These bottom 8 lines in /etc/dhcpcd.conf don't seem familiar to me at all. I have no idea where this comes from. Come to think of it, maybe I had pihole running on this machine at some point in time, that might have put it there (I'm eyeballing those dns servers). 

I'm deleting these bottom 8 lines where static IP's, routes and dns servers are assigned. The rest of the file seems fine to me.

```

$ sudo grep -r "192\.168\.2\.254" /etc
/etc/dhcpcd.conf:        static routers=192.168.2.254
$ cat /etc/dhcpcd.conf
# A sample configuration for dhcpcd.
# See dhcpcd.conf(5) for details.

# Allow users of this group to interact with dhcpcd via the control socket.
#controlgroup wheel

# Inform the DHCP server of our hostname for DDNS.
hostname

# Use the hardware address of the interface for the Client ID.
#clientid
# or
# Use the same DUID + IAID as set in DHCPv6 for DHCPv4 ClientID as per RFC4361.
# Some non-RFC compliant DHCP servers do not reply with this set.
# In this case, comment out duid and enable clientid above.
duid

# Persist interface configuration when dhcpcd exits.
persistent

# Rapid commit support.
# Safe to enable by default because it requires the equivalent option set
# on the server to actually work.
option rapid_commit

# A list of options to request from the DHCP server.
option domain_name_servers, domain_name, domain_search, host_name
option classless_static_routes
# Respect the network MTU. This is applied to DHCP routes.
option interface_mtu

# Most distributions have NTP support.
#option ntp_servers

# A ServerID is required by RFC2131.
require dhcp_server_identifier

# Generate SLAAC address using the Hardware Address of the interface
#slaac hwaddr
# OR generate Stable Private IPv6 Addresses based from the DUID
slaac private
interface eno1
        static ip_address=192.168.2.9/24
        static routers=192.168.2.254
        static domain_name_servers=1.1.1.1 1.0.0.1
interface eno1
        static ip_address=10.0.0.9/24
        static routers=10.0.0.1
        static domain_name_servers=9.9.9.10 149.112.112.10

```

---

### Post by The Cog on 2023-10-07
Nice find. Thanks for letting us know what it was rather than leaving us wondering.

---

### Post by bschopman2 on 2023-10-07
> **The Cog said:**
> Nice find. Thanks for letting us know what it was rather than leaving us wondering.

And thank you for helping me on this problem! It's been bothering me for months, so I'm very happy it's finally solved.

---

