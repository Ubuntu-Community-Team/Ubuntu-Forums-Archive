---
title: "Directing traffic between two NIC's"
date: 2021-06-17
forum: Networking &amp; Wireless
---

### Post by herman98 on 2021-06-17
Hi all,
This is my first time posting here. Image in attachments shows my current network scheme.

Laptop(netbook) configured as a server Ubuntu server 20.04 installed it has 4tb samba server deluge runs as a daemon and im 
using its wifi as an access point bridged with its onboard ethernet (br0). And it has usb to gigabit ethernet plugged on one of the usb ports. 
What i want to do is i want to direct different apps traffics between nics. Deluge and samba should reach wan & lan via usb to gigabit ethernet adapter and bridged 
ap should reach wan & lan through 10/100 onboard ethernet. What and which configurations should i do?

interface names: 10/100 onboard: enp9s0 usb to gigabit adapter: enx00e04c689782

The things i tried:
- Tried link aggregation but no luck because link speeds not matched. Tried balance-rr (round-robin) mode but it bottlenecked hard. I can get more throughput via usb to gigabit eth.
- Bridged 10/100 with wifi adapter and assigned static ip, also for usb to eth adapter but server uses 10/100 link for all of the wan & lan communication.
- Edited /etc/samba/smb.conf ;   interfaces = 127.0.0.0/8 enx00e04c689782 and ;   bind interfaces only = yes changed nothing, should i edit out 127.0.0.0/8 interface?
- Searched for binding deluge to interface most of the answers related to vpns and workarounds i suppose that deluge has no support for interface binding. I didn't tried any of the workaround because i concerned about cannot revert the settings that i changed and forced to reinstall ubuntu server

ifconfig output:
br0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.23  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::fccf:45ff:feec:7b5e  prefixlen 64  scopeid 0x20<link>
        ether 00:24:54:e6:34:46  txqueuelen 1000  (Ethernet)
        RX packets 737572  bytes 594082505 (594.0 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1044388  bytes 706176857 (706.1 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

enp9s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        ether 00:24:54:e6:34:46  txqueuelen 1000  (Ethernet)
        RX packets 861992  bytes 742785961 (742.7 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1095044  bytes 716202631 (716.2 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 18

enx00e04c689782: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.22  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::2e0:4cff:fe68:9782  prefixlen 64  scopeid 0x20<link>
        ether 00:e0:4c:68:97:82  txqueuelen 1000  (Ethernet)
        RX packets 627151  bytes 125676196 (125.6 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 556  bytes 52498 (52.4 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 16448  bytes 27908101 (27.9 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 16448  bytes 27908101 (27.9 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp5s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::ba03:5ff:fe07:1665  prefixlen 64  scopeid 0x20<link>
        ether b8:03:05:07:16:65  txqueuelen 1000  (Ethernet)
        RX packets 50673  bytes 10026754 (10.0 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 132153  bytes 143012284 (143.0 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

I can share other details of configs if asked.

Samba, netplan config files is at attachments.

Apologies if any mistakes made about post or language, English is not my native language.
Thank you in advance.

---

### Post by TheFu on 2021-06-18
If you want to redirect traffic, then routing must be enabled.  To route, different subnets are mandatory.  Having 2 NICs on the same subnet won't allow routing to easily be setup.  They need to be different subnets and the kernel setting to support forwarding for both IPv4 and IPv6 is necessary.  This is done in the sysctl.conf file.

I don't think SMB traffic can be routed.

The image isn't clear for the use of the AP on the computer. What's the point when the router has an AP?

Unmanaged switches can't do advanced network things like bonded connections - that's another name for link aggregation.  You'll want a $150 switch for that.
What's the reason to have have 2 ethernet connections to the same switch on the same subnet? It isn't like you'll get 1.1Gbps because there are 2 links.  It doesn't work that way.  If you want failover between the NICs, then a better switch is needed. If you want traffic filtering, then I'd connect one of the computer ethernet cables to the router and the other to the switch. Then all traffic will need to run through the computer to get to the router/internet .... but that's what the router does already, so having 2 routers in series is a little confusing as shown.  

I have two routers in series myself, but the first router is mandated by the ISP and it is in bridge mode. Then my real router gets all the public IPs and hands those out in a 1-for-1 NAT to specific internal systems.  The WAN side is on a 50.x.x.x/29 subnet and the LAN sides have multiple subnets for different security networks.  On my network, wifi is at the ISP router and treated like raw, untrusted, internet traffic. Turns out that all wifi has not been secure since the 1990s - and still is not secure today.  Whenever using wifi, always use a vpn too.
[ATTACH=CONFIG]288679[/ATTACH]
That's an idea for how to do wifi and different security zones. Hope that image is clear.

---

