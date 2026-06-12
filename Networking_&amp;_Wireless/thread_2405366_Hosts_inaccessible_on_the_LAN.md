---
title: "Hosts inaccessible on the LAN"
date: 2018-11-05
forum: Networking &amp; Wireless
---

### Post by joshuatfox on 2018-11-05
My Ubuntu (Bionic) hosts are inaccessible to each other on the Wifi LAN:
[LIST=1]
[*]I tried running  an HTTP server on various ports from 8000 and up. *netstat *shows that the servers  **are** listening. Accessing that server from localhost works. But accessing it from the other host using a browser, *telnet* or *nc* does not work -- no connection.
[*]*arp -a* does show them to each other.
[*]*ping* ip-address shows "inaccessible"
[*]They are on the same network and *ifconfig* shows that they have the same subnet mask. They have IP addresses 192.168.1.16 and  192.168.1.24.
[*]*nmap* shows that all ports are "filtered."
[*]*ufw* is *inactive*
[*]If I activate *ufw *and expose these ports -- no change.
[/LIST]

How do I expose these servers on the LAN?

---

### Post by The Cog on 2018-11-05
It sounds as though there some firewall rules preventing access. Please post the output of the command 
```
sudo iptables-save
```
This will show any residual firewall rules that may still be in place even with ufw disabled. iptables-save does not save the configuration, it just outputs a full listing that could be saved and restored if you wanted to.

---

### Post by joshuatfox on 2018-11-05
OK, both  *[COLOR=#000000][FONT=&amp]sudo iptables-save [/FONT][/COLOR]*and *[COLOR=#000000][FONT=&amp]sudo cat /proc/net/ip_tables_names [/FONT][/COLOR]*give no output, an empty-result.[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]

---

### Post by The Cog on 2018-11-05
In that case I think we need more detailed info. First, try this command (just in case, although I expect an error):
```
sudo nft list ruleset
```
and get a tcpdump of the wlan traffic. In one window, run:
```
sudo tcpdump -nn -i wlan0
```
or whatever your wlan interface is called, and then try a ping from another window. Let's see what the tcpdump says.

---

### Post by joshuatfox on 2018-11-05
nft shows nothing not much
```
table inet filter {
	chain input {
		type filter hook input priority 0; policy accept;
	}


	chain forward {
		type filter hook forward priority 0; policy accept;
	}


	chain output {
		type filter hook output priority 0; policy accept;
	}
}

```

But I understand now that the issue is in my network. My two computers are connected through an access point that is not the primary router.

When I turned off the access point and connected the devices to the primary router, they get different IP addresses -- 192.168.1.2 and .6 , and can ping and connect to each other.
 
But I do need the access point, as it has a stronger  wifi signal. How do I get the hosts to connect despite this? It seems to me that if they are on the same netmask/subnet they  *should* be able to connect.

---

### Post by The Cog on 2018-11-05
That doesn't sound good. Can we see the output of **ip route**?

---

### Post by joshuatfox on 2018-11-06
I think the cause was mismatched security protocols across the access points. 

I fixed that, and things are better now -- I managed to connect the hosts and I *think *they are on the secondary AP.
  
But to be sure, how can I tell which AP I am connected to?

---

