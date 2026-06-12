---
title: "Help with IPTables for OVPN Gateway on Ubuntu Server 20.04 LTS"
date: 2021-09-05
forum: Networking &amp; Wireless
---

### Post by fsociety3765 on 2021-09-05
Hi all,

I need some help with getting IPTables setup for use as an OVPN gateway on Ubuntu Server 20.04 LTS. I have been battling with this on/off for the past month or so and I cannot seem to get it working properly. At least not in the way I want it to work.

Ultimately, I want this server to be on the network connected to an OVPN server and then on an as-needed basis be able to point other machines on the network to this server via the default gateway, so the traffic is routed back and forth through the OVPN connection. However, I need to maintain SSH and other LAN access to all devices at all times as well. So the server running the OVPN gateway I need SSH access to so I can manage it. Then any machine I point to it, which will mainly be other Ubuntu Servers, I also need SSH access to but also access to any services those server may be running. For example web services on various ports etc...

There is a mass of tutorials out there, all with slight differences which I have tried and failed to get working. Currently my IPTables setup is a hash of various different configs that I have found, as I have been doing a lot of trial and error, trying to get things working.

Netplan Config:
```

# This is the network config written by 'subiquity'
network:
    renderer: NetworkManager
    ethernets:
        ens18:
            addresses: [192.168.10.91/24]
            gateway4: 192.168.10.1
            nameservers:
                addresses: [192.168.10.251,192.168.10.252,192.168.10.1]
                search: [internal.domain.com]
            dhcp4: false
            optional: true
    version: 2

```

Current IPTables script:
```

#!/bin/bash


# Flush
iptables -F


# Allow SSH Connections
iptables -A INPUT -p tcp --dport 22 -m conntrack --ctstate NEW,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -p tcp --sport 22 -m conntrack --ctstate ESTABLISHED -j ACCEPT


# Setup VPN Tunnel Rouing
iptables -t nat -A POSTROUTING -o tun+ -j MASQUERADE
iptables -A FORWARD -i tun+ -o ens18 -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A FORWARD -i ens18 -o tun+ -j ACCEPT


# Allow VPN Tunnel Out
iptables -A OUTPUT -o tun+ -m comment --comment "vpn out" -j ACCEPT


# Allow Loopback Traffic
iptables -A INPUT -i lo -j ACCEPT


# Allow ICMP
iptables -A INPUT -i ens18 -p icmp -m comment --comment "icmp in" -j ACCEPT
iptables -A OUTPUT -o ens18 -p icmp -m comment --comment "icmp out" -j ACCEPT


# Allow Communication with LAN
iptables -A OUTPUT -d 192.168.0.0/16 -o ens18 -m comment --comment "lan" -j ACCEPT


# Allow All Established, Related Traffic to Return
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT




# Allow OVPN Traffic
iptables -A OUTPUT -o ens18 -p udp -m udp --dport 1194 -m comment --comment "allow vpn traffic" -j ACCEPT


# Allow NTP Traffic
#iptables -A OUTPUT -o ens18 -p udp -m udp --dport 123 -m comment --comment "ntp" -j ACCEPT


# Allow DNS Traffic
#iptables -A OUTPUT -o ens18 -p udp -m udp --dport 53 -m comment --comment "dns" -j ACCEPT


# Allow Connections to NordVPN IPs
#iptables -A OUTPUT -p tcp -d 217.138.202.75 --dport 443 -m comment --comment "nordvpn IP" -j ACCEPT
#iptables -A OUTPUT -p tcp -d 104.18.230.229 --dport 443 -m comment --comment "nordvpn IP" -j ACCEPT


# Drop All Other Traffic
#iptables -A OUTPUT -o ens18 -j DROP
#iptables -I FORWARD -i ens18 ! -o tun+ -j DROP


iptables -P FORWARD DROP
iptables -P INPUT DROP
iptables -L


# Log All Dropped Packets
#iptables -N logging
#iptables -A INPUT -j logging
#iptables -A OUTPUT -j logging
#iptables -A logging -m limit --limit 2/min -j LOG --log-prefix "IPTables general: " --log-level 7
#iptables -A logging -j DROP


# Save Out
echo "saving"
iptables-save > /etc/iptables.rules
echo "done"

```

Current OVPN Connection Command:
```

sudo openvpn --config "/etc/openvpn/ovpn_udp/bg53.nordvpn.com.udp.ovpn" --auth-user-pass /etc/openvpn/auth.txt

```

99-sysctl.conf:
```

#
# /etc/sysctl.conf - Configuration file for setting system variables
# See /etc/sysctl.d/ for additional system variables.
# See sysctl.conf (5) for information.
#


#kernel.domainname = example.com


# Uncomment the following to stop low-level messages on console
#kernel.printk = 3 4 1 3


##############################################################3
# Functions previously found in netbase
#


# Uncomment the next two lines to enable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
#net.ipv4.conf.default.rp_filter=1
#net.ipv4.conf.all.rp_filter=1


# Uncomment the next line to enable TCP/IP SYN cookies
# See http://lwn.net/Articles/277146/
# Note: This may impact IPv6 TCP sessions too
#net.ipv4.tcp_syncookies=1


# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.ip_forward=1


# Uncomment the next line to enable packet forwarding for IPv6
#  Enabling this option disables Stateless Address Autoconfiguration
#  based on Router Advertisements for this host
#net.ipv6.conf.all.forwarding=1




###################################################################
# Additional settings - these settings can improve the network
# security of the host and prevent against some network attacks
# including spoofing attacks and man in the middle attacks through
# redirection. Some network environments, however, require that these
# settings are disabled so review and enable them as needed.
#
# Do not accept ICMP redirects (prevent MITM attacks)
#net.ipv4.conf.all.accept_redirects = 0
#net.ipv6.conf.all.accept_redirects = 0
# _or_
# Accept ICMP redirects only for gateways listed in our default
# gateway list (enabled by default)
# net.ipv4.conf.all.secure_redirects = 1
#
# Do not send ICMP redirects (we are not a router)
#net.ipv4.conf.all.send_redirects = 0
#
# Do not accept IP source route packets (we are not a router)
#net.ipv4.conf.all.accept_source_route = 0
#net.ipv6.conf.all.accept_source_route = 0
#
# Log Martian Packets
#net.ipv4.conf.all.log_martians = 1
#


###################################################################
# Magic system request Key
# 0=disable, 1=enable all, >1 bitmask of sysrq functions
# See https://www.kernel.org/doc/html/latest/admin-guide/sysrq.html
# for what other values do
#kernel.sysrq=438

```

The connection to the OVPN server part works. I am pretty certain all magic needs to happen in the IPTables part but currently the above IPTables rules applied, my SSH connection to the server gets disconnected right at the point when the tunnel is established.

Any help would be greatly appreciated. If you need any further information please ask. I have provided everything I think should be necessary.

Thanks,

FS

---

