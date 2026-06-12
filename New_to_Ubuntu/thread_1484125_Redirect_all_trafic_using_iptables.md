---
title: "Redirect all trafic using iptables"
date: 2010-05-15
forum: New to Ubuntu
---

### Post by Joker5bb on 2010-05-15
I have got a virual AP setup with dhcpd apache and airbase-ng 
and im trying to get it into Non Transparent mode,

i have tried this but it does not work:
```
10.ifconfig at0 up
11.ifconfig lo up
12.ifconfig at0 10.0.0.1 netmask 255.255.255.0 
13.ifconfig at0 mtu 1400
14.route add -net 10.0.0.0 netmask 255.255.255.0 gw 10.0.0.1
15.iptables --flush
16.iptables --table nat --flush
17.iptables --delete-chain
18.iptables --table nat --delete-chain
19.iptables -t nat -A PREROUTING -p udp -j DNAT --to 10.0.0.1
20.iptables -P FORWARD ACCEPT
21.iptables -t nat -A PREROUTING -p tcp --dport 80 -j DNAT --to 10.0.0.1
```

if i type 10.0.0.1 in the client then it will go to my webpage

---

### Post by HermanAB on 2010-05-15
Check the iptables man page for the 'redirect' parameter.

---

### Post by cdenley on 2010-05-18
I don't think what you are trying to do will work with DNAT or REDIRECT. If I remember correctly, the problem with DNAT is it will change the destination IP, but the source IP will remain the same. The initial packet will reach the server, but then responses sent back to the client will have the source IP of the actual server, not the IP the client was establishing a connection to.

REDIRECT will only redirect packets to the local machine. Perhaps if you use it in combination with the rinetd package, you will get the desired results.

---

