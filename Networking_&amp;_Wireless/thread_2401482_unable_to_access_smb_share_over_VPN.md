---
title: "unable to access smb share over VPN"
date: 2018-09-18
forum: Networking &amp; Wireless
---

### Post by sniper8752 on 2018-09-18
My ubuntu server runs iptables.  I use openvpn to get logged onto my network.  I get an IP of 10.x.x.x, while my lan uses 192.x.x.x.  When I successfully get vpn'd in, I get a vaild 10.x.x.x address.  But when I try to access the share on 192, it times out.  I tail kern.log, but don't see any traffic from my device that I am vpn'ing in with.

---

### Post by SeijiSensei on 2018-09-19
Have you activated packet forwarding in /etc/sysctl.conf?  Ubuntu, like most Linux variants these days, won't forward packets between interfaces by default.

```

# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.ip_forward=1

```

Rebooting will then enable forwarding.  You can activate forwarding on the fly with the command:

```
sudo echo '1' > /proc/sys/net/ipv4/ip_forward
```

If you've done that already, make sure you have a FORWARD rule in iptables that lets traffic flow between the 10 and 192.168 networks.

---

### Post by sniper8752 on 2018-09-21
> **SeijiSensei said:**
> If you've done that already, make sure you have a FORWARD rule in iptables that lets traffic flow between the 10 and 192.168 networks.

I tried to do this.  So I have three interfaces on my server: the tunnel, wan and lan interface.  I basically created a rule to forward all traffic from the tunnel to the 192 network.  But it still does not work

---

### Post by SeijiSensei on 2018-09-24
Did you enable packet forwarding in /etc/sysctl.conf?  Regardless of the iptables rules, you still need to do this.

Do your rules look more or less like these:
```

/sbin/iptables -P FORWARD -j DROP
/sbin/iptables -A FORWARD -i tun0 -o eth0 -j ACCEPT
/sbin/iptables -A FORWARD -i eth0 -o tun0 -j ACCEPT

```
You need to enable traffic in both directions.

Do you have INPUT rules as well? If your INPUT policy is also DROP, you'll need at least
```

/sbin/iptables -A INPUT -i tun0 -j ACCEPT
/sbin/iptables -A INPUT -i eth0 -j ACCEPT

```

---

### Post by sniper8752 on 2018-10-05
I had my firewall wide open, and I couldn't load it.  So it sounds like it's not an iptables issue then?

---

