---
title: "route table"
date: 2018-02-25
forum: Networking &amp; Wireless
---

### Post by sniper8752 on 2018-02-25
I am trying to setup my route table.  I notice that when I plug the ethernet cable in then remove it, the routing table changes.  This is causing an issue because I modify it, and when cable is removed, then plugged back in, I loose my changes.  What is causing this?  Is there any way to hard code these somewhere, or keep it from changing?  In my example, I have two interfaces.  When the cable is plugged in,it has this:
destination gateway genmask 
0.0.0.0 lan_ip 0.0.0.0
0.0.0.0 wan_ip 0.0.0.0

I remove the default lan ip, but when the cable is unplugged, and plugged back in again, it comes back.  I am also guessing it's not a good thing to have two defaults?

---

### Post by SeijiSensei on 2018-02-26
Just use one interface.  There's no benefit from having both active if they are on the same network subnet.

---

### Post by sniper8752 on 2018-02-26
They are not on the same subnet.  One is a external facing public IP, and the other is a local lan IP (e.g. 192.168.0.x).

---

### Post by SeijiSensei on 2018-02-27
Then only the Internet-facing interface should be the default gateway.  Don't use DHCP if you can help it.  Set up static addresses and static routes.

---

### Post by sniper8752 on 2018-02-27
I am confused as to what you are saying.  There is only one internet-facing interface.  Then I have an internal facing interface for my lan.  I have nat'ing and forwarding going on.  
I am not sure what you mean by don't use DHCP.  I don't feel like statically assigning IPs to each of my clients.

---

### Post by SeijiSensei on 2018-02-28
Only the Internet-facing interface should be the default gateway. If that doesn't happen automatically, you need to enforce it manually.

---

### Post by sniper8752 on 2018-03-01
How do I do that?

---

### Post by SeijiSensei on 2018-03-01
It sounds like you have DHCP servers on both sides of the box.  You can leave the Internet-facing side alone.  On the LAN-facing side you'll need to use [static addressing](https://help.ubuntu.com/lts/serverguide/network-configuration.html#static-ip-addressing).  Add a stanza like this to /etc/network/interfaces:

```

auto eno1
iface eno1 inet static
address 192.168.0.1
netmask 255.255.255.0

```

assuming the Ethernet interface is called "eno1".  Use the command "ifconfig" to see what names the interfaces have.  (You might need to install the net-tools package first if you don't have ifconfig.)

Since this specification doesn't have a "gateway" parameter, it will not set up a separate default route.

---

### Post by sniper8752 on 2018-03-01
Both interfaces are set to a static IP.

---

### Post by SeijiSensei on 2018-03-02
Do both stanzas in /etc/network/interfaces include a "gateway" directive?  As I said, only the Internet-facing one should have a gateway.

---

