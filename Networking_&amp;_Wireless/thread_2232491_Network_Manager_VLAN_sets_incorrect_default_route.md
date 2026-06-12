---
title: "Network Manager VLAN sets incorrect default route"
date: 2014-07-02
forum: Networking &amp; Wireless
---

### Post by devin-geekosphere on 2014-07-02
New install of 14.04 on Lenovo T530

Turn off WiFi (hardware) & unplug network cable to ensure no network connection
Boot laptop, and login
Go to Network Manager and click on Edit Connections
Add new Connection for VLAN
set values:
```

    Connection Name: VLAN connection 44
    Parent interface: eth1
    VLAN id: 44
    VLAN interfacename: VLAN-44

```
and click save
plug in network cable
(port is set for VLAN 44 tagging)
eth1 and VLAN-44 both get DHCP address (yeah!)
ping 8.8.8.8 gives "Destination Host Unreachable"
route shows 3 entries:
```

Destination    Gateway       Genmask        Flags Metric Ref   Use Iface
default        192.168.44.1  0.0.0.0        UG    0      0     0   eth1
192.168.44.0   *             255.255.255.0  U     1      0     0   eth1
192.168.44.0   *             255.255.255.0  U     0      0     0   VLAN-44

```
which is odd as the default needs to go through VLAN-44 so that the packets are tagged
if I delete the default route and add a new one changing only the interface
```

Destination    Gateway       Genmask        Flags Metric Ref   Use Iface
default        192.168.44.1  0.0.0.0        UG    0      0     0   VLAN-44
192.168.44.0   *             255.255.255.0  U     1      0     0   eth1
192.168.44.0   *             255.255.255.0  U     0      0     0   VLAN-44

```
now all of the networking works

Is there a way in Network Manager to tell it to use the VLAN for all traffic? or am I required to manually change the routes?

---

### Post by The Cog on 2014-07-02
I am surprised that eth0 (untagged) also gets an IP address on the same subnet as the tagged VLAN. That looks wrong to me. I wouldn't expect two vlans to be running the same subnet. Are you manually assigning an address to eth0 in the GUI? Perhaps you don't really want eth0 gaining an address at all.

Beyond that I'm afraid I can't help as I've never used the VLAN GUI - I've only ever configured vlans in /etc/network/interfaces.

Oh, and I don't know if the GUI pays attention or not, but I believe it is convention to refer to a vlan interface as the main interface dot vlan number, e.g. "eth1.44".

---

### Post by devin-geekosphere on 2014-07-02
eth1 is setup as whatever the defaults of the install are, it is dhcp for sure, and it gets the same IP as the VLAN-44. So yeah seems weird that it even gets an IP, which is what happens when I connect a CentOS machine to the same jack.

I have used multiple names for the VLAN interface and it does not seem to matter if it is VLAN-44, eth1.44 or bob.

Thanks for the reply.

---

### Post by The Cog on 2014-07-03
Well, can you stop eth1 from trying to use DHCP? With any luck, VLAN-44 will get hte default route in that case.

---

### Post by devin-geekosphere on 2014-07-07
> **The Cog said:**
> Well, can you stop eth1 from trying to use DHCP? With any luck, VLAN-44 will get hte default route in that case.

sounds like a plan, how does one do that?  I would like to keep using the Network Manager I and do not see an option to configure it that way.

---

### Post by The Cog on 2014-07-10
I would think that you go to the IPv4 settings for eth0 and set it to disabled. 
I would hope that any separate vlan interface would have its own IPv4 settings page where you would leave DHCP enabled.

I haven't tried this myself as  all my VPN connected servers are configured by /etc/network/interfaces file (no GUI on a server).

---

### Post by devin-geekosphere on 2014-07-10
> **The Cog said:**
> I would think that you go to the IPv4 settings for eth0 and set it to disabled. 
I would hope that any separate vlan interface would have its own IPv4 settings page where you would leave DHCP enabled.

I haven't tried this myself as  all my VPN connected servers are configured by /etc/network/interfaces file (no GUI on a server).

I tried this and it worked! However if I then connect it to a non-VLAN network it doesn't. So I am stuck manually editing it no matter what. :(

---

