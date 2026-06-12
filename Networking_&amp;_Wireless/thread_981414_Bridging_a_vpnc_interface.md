---
title: "Bridging a vpnc interface"
date: 2008-11-13
forum: Networking &amp; Wireless
---

### Post by Aethylred on 2008-11-13
Sanity check time. Everything looks like it should work, but it doesn't. I need some comments and advice.

The situation:

Internet----ADSL----UBUNTU-PROXY----SWITCH----INTRANET

The device in question here is UBUNTU-PROXY. It is configured as a bridge router/firewall/interception proxy/um... let's just call it "Proxy" between the ADSL router connecting us to the Internet and our network switch. Generally out network is 10.10.10.0/24 with 10.10.10.1 as the gateway (the ADSL router), which is automatically configured with DHCP.

Currently it's doing that job just fine, we are being bridged across it right now without any problems.

The Proxy is a Compaq Proliant 1600 with Ubuntu 8.04 LTS Server installed. It's using the onboard tlan NIC as eth0 connected to the ADSL, and a generic gigabit RealTek r8169 as eth1 connected to our switch. I've run apt-get update recently and the full uname -a response is:

```

Linux NZUBU-PROXY 2.6.24-21-server #1 SMP Wed Oct 22 00:18:13 UTC 2008 i686 GNU/Linux

```

It's configured in /etc/network/interfaces here

```

# bridge the ports, and fake the MAC
 auto br0
 iface br0 inet static
        address 10.10.10.105
        network 10.10.10.0
        netmask 255.255.255.0
        broadcast 10.10.10.255
        gateway 10.10.10.1
        bridge_ports eth0 eth1
        bridge_hw 00:08:54:51:09:01

pre-up iptables-restore > /etc/iptables.rules

post-up ip route flush dev eth0
post-up ip route flush dev eth1
post-up ip route add to 10.10.10.0/24 dev br0
post-up ip route add default via 10.10.10.1 dev br0

```

The iptables being reloaded have not yet been configured for any firewalling or filtering apart from redirecting Port 80 traffic through Squid3.

The default routing table is pretty basic:

```

route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.10.10.0      *               255.255.255.0   U     0      0        0 br0
default         10.10.10.1      0.0.0.0         UG    0      0        0 br0

```

Now, that's the basics, and they work.

We want to use the Proxy to hook our LAN to a remote LAN with using the Linux Cisco VPN client, vpnc, installed with apt-get of course. I've edited up a config file in /etc/vpnc/myvpn.conf 

```

IPSec gateway XX.XX.XX.XX
IPSec ID <username>
IPSec secret <password>
Xauth username <username>
Xauth password <password>
Interface name tun0

```

When I run sudo vnpnc myvpn the tun device comes up, and the proxy can access the machines on the remote network. As well as setting up the tun0 interface, vpnc has also modified the routing table so (XX.XX.XX.XX is the IPSec gateway address as per mylan.conf... other IPs have had their names changed to protect the innocent):

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.100.10.20    *               255.255.255.255 UH    0      0        0 tun0
XX.XX.XX.XX     10.10.10.1      255.255.255.255 UGH   0      0        0 br0
10.100.20.0     *               255.255.255.0   U     0      0        0 tun0
10.100.10.0     *               255.255.255.0   U     0      0        0 tun0
10.10.10.0      *               255.255.255.0   U     0      0        0 br0
default         10.10.10.1      0.0.0.0         UG    0      0        0 br0

```

I have also tried the same connection creating the interface as a TAP device, which also works.

This all works too, and there is a split horizon happening as the internal network is still visible and the proxy can still reach the intranet, and it still works just fine as a bridge for the rest of the intranet.

Now for the bit that doesn't work.

I want the proxy to transparently route traffic from the intranet (10.10.10.0/24) to the remote machines (10.100.10.0/24 adn 10.100.20.0/24) via the VPN connection (dev tun0 or dev tap0).

At first glance it looks like the routing tables above should do that. see the 10.100.10.0/24 dev tun0 and 10.100.20.0/24 dev tun0 lines, they should do it, but no, internal workstations can not ping the remote network. Only the proxy can.

When workstations on the intranet try and traceroute/tracert to the remote network, they skip the proxy and try to reach them via the gateway at 10.10.10.1, and that's not going to work.

Things I have tried:
[LIST]
[*]using iptables to try doing some NAT forwarding
[*]creating the VPN interface as a TAP device and adding it to the bridge interface with brctl addif br0 tap0 (which breaks it)
[*]using the routing tables on 10.10.10.1 to forward traffic back to the proxy as a gateway to the remote networks, that just creates a routing loop.
[*]route and ip route won't let me do "route add -net 10.254.12.0/24 gw 10.10.10.105 dev tun0", I can choose the gateway IP _or_ the outbound interface, but not both.
[/LIST]

Does anyone have any suggestions or help?

---

