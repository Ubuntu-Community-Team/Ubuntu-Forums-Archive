---
title: "port forwarding from VPN server to client"
date: 2014-08-07
forum: Networking &amp; Wireless
---

### Post by jwfoley on 2014-08-07
I'm running an OpenVPN Access Server, which is Ubuntu with some extra software installed, on an Amazon EC2 instance. A file server is permanently connected as a VPN client with a static IP address (10.0.0.2). The client doesn't have a public IP, so I want to forward some ports from the VPN server to the client file server. For testing I have left all ports open on the VPN server via the EC2 configuration.

The VPN server has several interfaces: it connects to the WAN through eth0, and it connects to the client through as0t0. So I tried this to forward port 7500 on the VPN server to 22 on the file server, for SSH:
```
# iptables -t nat -A POSTROUTING --out-interface as0t0 -j MASQUERADE
# iptables -A FORWARD --in-interface eth0 -j ACCEPT
# iptables -t nat -A PREROUTING -p tcp -i eth0 -m tcp --dport 7500 -j DNAT --to-destination 10.0.0.2:22
```

based on this post: [http://www.linuxquestions.org/questions/linux-server-73/iptable-port-forward-between-two-lan-interface-945719/](http://www.linuxquestions.org/questions/linux-server-73/iptable-port-forward-between-two-lan-interface-945719/)

But then when I attempt to SSH to port 7500 on the VPN server from a third machine, it fails:
```
$ ssh -p 7500 user@vpnserver
ssh: connect to host vpnserver port 7500: Connection refused
```

I am not very knowledgeable about networking and know nothing about iptables. Is one of my commands wrong? Or is iptables not even the right way to do this?

---

### Post by SeijiSensei on 2014-08-07
First, try dropping the masquerading rule.  You don't need to masquerade inbound traffic that you are forwarding back to another machine.

---

### Post by jwfoley on 2014-08-08
Sorry for the slow reply; I thought I had e-mail notifications configured correctly and I was wrong.

I tried this:
```
# iptables -t nat -A POSTROUTING --out-interface as0t0
# iptables -A FORWARD --in-interface eth0 -j ACCEPT
# iptables -t nat -A PREROUTING -p tcp -i eth0 -m tcp --dport 7500 -j DNAT --to-destination 10.0.0.2:22

```

and got the same result. What's the next troubleshooting step?

---

### Post by SeijiSensei on 2014-08-08
The first command does nothing at all. What if you just use the latter two?  For testing purposes, I'd remove the "--in-interface eth0" directive and just allow all forwarding for now.  Do you also have this rule:
```
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
```

---

### Post by jwfoley on 2014-08-09
No luck with this:

```
# iptables -A FORWARD -j ACCEPT
# iptables -t nat -A PREROUTING -p tcp -i eth0 -m tcp --dport 7501 -j DNAT --to-destination 10.0.0.2:22
```

and no luck adding this either:

```
# iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
```

What now?

Also, should I be resetting my configuration somehow between attempts? For now I'm just changing the port number in case my previous attempts are conflicting with the current one.

---

