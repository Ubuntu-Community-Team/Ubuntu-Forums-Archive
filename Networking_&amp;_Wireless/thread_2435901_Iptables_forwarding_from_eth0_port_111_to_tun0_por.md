---
title: "Iptables forwarding from eth0 port 111 to tun0 port 222"
date: 2020-01-28
forum: Networking &amp; Wireless
---

### Post by radji on 2020-01-28
Here is the rule of forward packets from tun0 to eth0:

/sbin/iptables -A FORWARD -i eth0 -o tun0 -j ACCEPT

Could you please help, what i need to add to this rule for forwarding all packets for e.g. from eth0 port 111 to tun0 port 222?

---

### Post by slickymaster on 2020-01-28
Thread moved to **Networking & Wireless** for a better fit

---

### Post by SeijiSensei on 2020-01-28
You don't need anything special for those ports. What you do need, though, is another FORWARD rule with the interfaces reversed:

```
/sbin/iptables -A FORWARD -i tun0 -o eth0 -j ACCEPT
```

assuming the default forwarding policy is DENY or REJECT. With only one inbound rule, you don't allow for replies to be sent.

---

### Post by radji on 2020-01-29
I understand that 
Also:
/sbin/iptables -A FORWARD -i eth0 -o tun0 -j ACCEPT

What about forwarding only specific ports 111 to 222 with that interfaces
222 to 111?

---

### Post by SeijiSensei on 2020-01-29
I don't understand the question. Are you asking how to limit the forwarding to those ports? For that I'd add an input rule:
```
/sbin/iptables -A INPUT -i eth0 -p tcp --dport 111:222 -j ACCEPT
```
You'd need another rule with "-p udp" if you need to forward UDP traffic arriving on those ports. 

Also make sure you have IPv4 forwarding enabled in /etc/sysctl.conf. Uncomment the line
```
net.ipv4.ip_forward=1
```
if you have not yet done so.

If you're talking about forwarding specific ports to machines behind this one, you need another set of rules that uses the "nat" table.  Without more detail on what you're trying to do, I can't help much more.

You do realize that many ports in the range 111 to 222 provide well-known services.  See the file /etc/services for details.  If you're creating your own services, you need to use higher-numbered ports.  Typically I use ports above 50000 where official services are rare.

---

### Post by radji on 2020-01-30
Ok, thanks a lot

---

