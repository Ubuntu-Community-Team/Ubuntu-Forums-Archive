---
title: "iptables and DNS: incoming traffic with destination port 53"
date: 2019-01-07
forum: Networking &amp; Wireless
---

### Post by stecour on 2019-01-07
Hi all

I'm currently setting up iptables rules on my web server. Almost everything works as I expect it to work, but for the rules applied to DN lookup queries.
Here is my understanding:
[LIST]
[*]DN lookup requests are sent to the port 53 of DN servers (by default) 
[*]DN lookup requests can happen over both TCP and UDP protocols 
[/LIST]
Therefore, I set up the following rules:
```

iptables -A INPUT -p tcp --sport 53 -j ACCEPT
iptables -A INPUT -p udp --sport 53 -j ACCEPT

```
In other words, accept any incoming connections coming from the port 53 (supposing they are responses for the DN queries my server will send to the port 53).
However, this doesn't work. A *nslookup ubuntuforums.org* command times out. And here is the part I'm not getting: if I add the iptables rules below, then it works
```

iptables -A INPUT -p tcp --dport 53 -j ACCEPT
iptables -A INPUT -p udp --dport 53 -j ACCEPT

```
If I'm reading the above correctly, it means that I'm accepting incoming connections sent to the port 53 of my server. I don't understand why this is needed.
I used tcpdump to see what is going on when I run *nslookup ubuntuforums.org* and I can't see any connections sent to the port 53 of my machine.
There is obviously something I'm missing but I don't know what... Does anyone have an idea?
Thanks in advance.

---

### Post by stecour on 2019-01-10
Update: I posted on ServerFault too and someone just provided an explanation for this issue: [https://serverfault.com/a/948383/442581](https://serverfault.com/a/948383/442581)

---

### Post by The Cog on 2019-01-10
I would add that you should not just blindly permit any incoming packets that were sent from source port 53. Although this would allow responses from DNS servers in, it would also allow the bad guys to connect to any port/service on your server, simply by using their own port 53 to initiate the connection.

It is normal to add a rule that permits anything in that is ESTABLISHED or RELATED to the INPUT chain. Linux keeps track of all connections, and when it makes an outgoing connection (permittied by the OUTPUT rules) then any response to that connection is regarded as ESTABLISHED. When using some protocols, the initial connection can require further connections on different ports (e.g. the data transfer connection by FTP). The connection tracking can recognise this and automatically regard the new connection as being RELATED to the already-permitted control connection. Without permitting RELATED packets, some protocols simply can't work unless you open huge numbers of ports incoming.

So in summary, deny everything by default policy, permit OUTPUT connections to services on known ports that you want (like 53 DNS), and permit INPUT connections that are ESTABLISHED,RELATED.
Actually, I normally permit anything outgoing and just restrict incoming to established,related.

---

