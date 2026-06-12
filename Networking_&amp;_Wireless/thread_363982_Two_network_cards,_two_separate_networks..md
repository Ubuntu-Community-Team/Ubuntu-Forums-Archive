---
title: "Two network cards, two separate networks."
date: 2007-02-17
forum: Networking &amp; Wireless
---

### Post by DoktorNo on 2007-02-17
Hi there,

I have a box with two network cards. One card is eth1 (after update from Dapper the numbers of cards had shifted...), and is working under DHCP and is connected to cable modem. The second one, eth2, is intended to have static IP adress, and is intendent for separate LAN. No NAT, no routing, this network should be separated from the eth1.

The main problem is, that this setup is not working. When both interfaces are configured as I said, I cannot access to the internet, but the eth1 has correct IP gathered from my ISP. When I deactivate the eth2, the everything is OK.

How to make this setup to work properly?

---

### Post by koenn on 2007-02-17
have a look at /etc/network/interfaces
it should look something like this :

```
auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet static
        address 192.168.0.1
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255

```
(the addresses can be different)

---

### Post by DoktorNo on 2007-02-17
I have configured these cards by using graphic control panel.

I think the result is the same, but I'll try this one.

---

### Post by netztier on 2007-02-18
> **DoktorNo said:**
> One card is eth1 (after update from Dapper the numbers of cards had shifted...),

You can correct or even nail down ethX-assignment in the /etc/iftab file:

```
[FONT="Courier New"]marc@blaze:~$ more /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:A0:C9:98:82:0E arp 1
eth1 mac 00:50:8B:07:E9:83 arp 1
marc@blaze:~$[/FONT]

```

It took me quite a while to figure out why I just would'nt get a meaningful sequence of ethX numbering (eth1 always missing...), until I discovered that there was a stale entry for eth1 with a MAC address of a NIC I had removed from the system months before...

The other thing to check carefully for: 

What does your **default route** look like? try **[FONT="Courier New"]netstat -nr[/FONT]**

```
[FONT="Courier New"]marc@cube:~$ netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
172.20.125.0    0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         172.20.125.1    0.0.0.0         UG        0 0          0 eth0[/FONT]

```

the route for 0.0.0.0/0.0.0.0 should have the IP address of your ISP's next hop router as "Gateway" and should be using the correct interface.

In the GUI configuration (System -> Administration -> Networking), on the "Connections" tab, you have the list of network adapters in your system. Below it, there's a drop-down selection box for the "Default Gateway Device". Here, select the NIC that connects to your ISP.

best regards

Marc

---

### Post by DoktorNo on 2007-02-18
I have cleaned up the mess with NIC names, and removed the "gateway" entry for the secondary NIC. So far everything is going fine.

This is the routing table:

```
Kernel IP routeing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
10.200.0.0      0.0.0.0         255.255.0.0     U         0 0          0 eth1
0.0.0.0         10.200.0.1      0.0.0.0         UG        0 0          0 eth1
```

---

