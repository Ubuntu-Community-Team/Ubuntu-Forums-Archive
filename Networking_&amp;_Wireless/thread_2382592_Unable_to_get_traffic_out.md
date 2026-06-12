---
title: "Unable to get traffic out"
date: 2018-01-15
forum: Networking &amp; Wireless
---

### Post by sniper8752 on 2018-01-15
I setup an ubuntu server with two nics; one internal and one wan-facing.  When I connect a client to the internal-facing, it seems to work fine.  When I plug in the wan, I can't do much.  I set the wan interface to auto, and it gets assigned an ip.  To narrow down the issue, I attempt to ping 8.8.8.8 to avoid dns issues, and it fails.

---

### Post by SeijiSensei on 2018-01-15
First, you must enable packet forwarding by uncommenting the line
```
net.ipv4.ip_forward=1
```
in the file /etc/sysctl.conf.  Remove the hash mark at the beginning of the line, then reboot.

The next step depends on how you want traffic to flow over your network.  The simplest solution is to add a "masquerading" rule on the server.  Suppose that the Internet-facing interface is eth1.  Then you add the rule

```
/sbin/iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
```

Now all traffic from hosts behind this server will appear to come from the server's eth1 interface with its IP address.  I usually add one-off iptables rules to /etc/rc.local so they will run at boot.

You could avoid masquerading on the server if you add a static route to your Internet router telling it that traffic for the network behind the server should be sent to the server.  That's probably more complicated than using masquerading.

See:  [https://help.ubuntu.com/community/Internet/ConnectionSharing#Ubuntu_Internet_Gateway_Method_.28iptables.29](https://help.ubuntu.com/community/Internet/ConnectionSharing#Ubuntu_Internet_Gateway_Method_.28iptables.29)

---

