---
title: "Ubuntu Server has 4 IPs on one physical port, other 3 ports not responding"
date: 2017-12-20
forum: Networking &amp; Wireless
---

### Post by 82blue on 2017-12-20
I installed Ubuntu Server 16.04 LTS on a mini-pc with 4 network ports. Static IPs configured in /etc/networking/interfaces as:
```

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# Ethernet Port 1
auto enp1s0
iface enp1s0 inet static
        address 192.168.1.2
        netmask 255.255.255.0
        gateway 192.168.1.1

# Ethernet Port 2
auto enp3s0
iface enp3s0 inet static
        address 192.168.1.3
        netmask 255.255.255.0
        gateway 192.168.1.1

# Ethernet Port 3
auto enp4s0
iface enp4s0 inet static
        address 192.168.1.4
        netmask 255.255.255.0
        gateway 192.168.1.1

# Ethernet Port 4
auto enp2s0
iface enp2s0 inet static
        address 192.168.1.5
        netmask 255.255.255.0
        gateway 192.168.1.1
```

Initially I boot with no ethernet cables plugged in. When I plug a network cable into one of the ports and connect directly to my laptop (with an IP on the same subnet), I can ping all 4 ip addresses at that one port. If I move the cable to the other three ports I am unable to ping any of these addresses. That port remains configured with all four IPs on that one active port until I reboot, then all four IPs move to one of the other 3 ports and the current port becomes unusable. I have to move the cable around until I find the port where I can ping the IPs, then I can ssh in again. 

The last lines in dmesg looks like this:
```
[32.155309] igb 0000:03:00.0 enp3s0: igb: enp3s0 NIC Link is Down 
[35.327466] igb 0000:01:00.0 enp1s0: igb: enp1s0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX/TX 
[35.327693] IPv6: ADDRCONF(NETDEV_CHANGE): enp1s0: link becomes ready 
[40.238792] igb 0000:01:00.0 enp1s0: igb: enp1s0 NIC Link is Down 
[43.499011] igb 0000:02:00.0 enp2s0: igb: enp2s0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX/TX 
[43.499239] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready 
[49.130225] igb 0000:02:00.0 enp2s0: igb: enp2s0 NIC Link is Down 
[51.630495] igb 0000:04:00.0 enp4s0: igb: enp4s0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX/TX
[51.630723] IPv6: ADDRCONF(NETDEV_CHANGE): enp4s0: link becomes ready
```

The problem persists through a re-install, so far I can't configure more than one physical port. I checked BIOS for options, enabling a "network stack" disables all ports so that I'm locked out of the machine. So it's not that. 

I'm not sure what my first step should be here. Any suggestions?

---

### Post by 82blue on 2017-12-22
The problem seems to be assigning static ips from the same subnet to different physical interfaces. If I assign static ips from different subnets, all the interfaces come up and I can ping each ip from its respective interface. For example:

```
source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# Ethernet Port 1
auto enp1s0
iface enp1s0 inet static
        address 192.168.0.1/24

# Ethernet Port 2
auto enp3s0
iface enp3s0 inet static
        address 192.168.1.1/24

# Ethernet Port 3
auto enp4s0
iface enp4s0 inet static
        address 192.168.2.1/24

# Ethernet Port 4
auto enp2s0
iface enp2s0 inet static
        address 192.168.3.1/24

```

Maybe its a feature? Its kinda like bonding, only different. I don't know if this will be an issue for me or not.

---

### Post by derek-ross666 on 2017-12-22
Why would you want to use 4 interfaces on the same subnet?

---

### Post by QIII on 2017-12-22
> **derek-ross666 said:**
> Why would you want to use 4 interfaces on the same subnet?

Comes in handy with multiple VMs on a server when you want each to have its own IP.

One example.

---

