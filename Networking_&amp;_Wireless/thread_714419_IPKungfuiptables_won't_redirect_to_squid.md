---
title: "IPKungfu/iptables won't redirect to squid"
date: 2008-03-03
forum: Networking &amp; Wireless
---

### Post by KidneyPi on 2008-03-03
I can't get squid working after moving the server I'm working on. Everything worked fine when eth0 was 10.0.1.200. eth0 is the external interface. eth1 is the internal interface. Both are now on the 192.168.1.0/24 network. eth0 is 192.168.1.3. eth1 is 192.168.1.200. The 10.0.1.0 network is my home network. The server is now in a client's server room.

Here is the squid.conf:
```
http_port 192.168.1.200:3128 transparent
icp_port 3130
hierarchy_stoplist cgi-bin ?
acl QUERY urlpath_regex cgi-bin \?
cache deny QUERY
emulate_httpd_log on
refresh_pattern ^ftp:		1440	20%	10080
refresh_pattern ^gopher:	1440	0%	1440
refresh_pattern .		0	20%	4320
acl all src 192.168.1.0/24
acl limited src "/etc/squid3/limited"
acl good dstdomain "/etc/squid3/good.hosts"
acl bad dstdomain "/etc/squid3/bad.hosts"
acl badip dst "/etc/squid3/bad.ip"
acl goodip dst "/etc/squid3/good.ip"
acl idiot src "/etc/squid3/idiot"
acl god src "/etc/squid3/god"
acl craigslist dstdomain "/etc/squid3/craigslist"
acl nickl src 192.168.1.182
http_access allow god
http_access allow craigslist nickl
http_access deny idiot
http_access allow good
http_access allow goodip
http_access allow good
http_access allow limited good
http_access deny limited
http_access deny bad
http_access allow all
http_access deny all
http_access deny all
http_reply_access allow all
icp_access allow all
coredump_dir /var/spool/squid3

```

I'm using ipkungfu to start the firewall. In the redirect.conf, it says 
```
tcp:80:3128:internal
```

Here is the ipkungfu.conf:
```
EXT_NET="eth0"
INT_NET="eth1"
LOCAL_NET="192.168.1.0/255.255.255.0"
GATEWAY=1
FORBIDDEN_PORTS="135 137 139"
SUSPECT="DROP"
KNOWN_BAD="DROP"
PORT_SCAN="DROP"
GET_IP="192.168.1.3"
DISALLOW_PRIVATE=0
WAIT_SECONDS=5

```

Why would it suddenly quit working when changing the address of eth0? What can I do to fix it?

---

### Post by SpaceTeddy on 2008-03-04
i am not sure if it has anything to do with it, but a computer should not have two network cards on the same subnet, since it does not know where the subnet is then. they need to be singled out. If you want your server to answer the subnet on both IP's, you should add a virtual IP to the network card.
If you want the server to segment the network, i suggest you look into network bridges...

like i said, i don't know if that is the problem, but as far as i understand networks, this setup is not supported...

---

