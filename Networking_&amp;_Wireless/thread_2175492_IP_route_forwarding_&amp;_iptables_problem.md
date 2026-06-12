---
title: "IP route forwarding &amp; iptables problem"
date: 2013-09-19
forum: Networking &amp; Wireless
---

### Post by ElToro on 2013-09-19
Got a problem with forwarding traffic through a server on a small home network. Due to energy consumption concerns and wanting to avoid the expenditure of a separate computer just for routing / Squid, the server works both as a Squid 3 proxy and as a Serviio mediaserver. The idea is to have Squid run in intercept mode. However, I seem to be unable to get the forwarding between eth0 and eth1 right; only some programs connect to the Internet (notably Skype). No mail, browsers, etc.

The topology is 

router (192.168.0.1) ---- NIC1 (eth0 - 192.168.0.2) server NIC2 (eth1 - 10.0.0.1) ----- LAN

Output of netstat -rn
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth0
10.0.0.0        0.0.0.0         255.255.255.0   U         0 0          0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
```

Output of iptables -L
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  10.0.0.0/8           anywhere             tcp dpt:3128

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere             state RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
REJECT     tcp  --  anywhere             cpanel19.proisp.no   tcp dpt:xmpp-client reject-with icmp-port-unreachable
REJECT     tcp  --  anywhere             213.162.240.106      tcp dpt:xmpp-client reject-with icmp-port-unreachable
```

Output of iptables -t nat -L:
```
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         
REDIRECT   tcp  --  anywhere             anywhere             tcp dpt:http redir ports 3128
DNAT       tcp  --  anywhere             anywhere             tcp dpt:http to:192.168.0.2:3128
REDIRECT   tcp  --  anywhere             anywhere             tcp dpt:http redir ports 3128

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         
MASQUERADE  all  --  anywhere             anywhere            
MASQUERADE  all  --  anywhere             anywhere
```

IP4 forward is on: *net.ipv4.ip_forward = 1*

I have been trying to get this to work for a while and any help would be greatly appreciated.

I think this is most probably a frowarding problem, not a Squid-problem, but just in case:

Output from grep -v "^#" /etc/squid3/squid.conf | sed -e "/^$/d"
```
acl all src 0.0.0.0/0.0.0.0
acl QUERY urlpath_regex cgi-bin \?
cache deny QUERY
acl apache rep_header Server ^Apache
acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl to_localhost dst 127.0.0.0/8
acl lan src 10.0.0.0/8
acl SSL_ports port 443 563 # https, snews
acl SSL_ports port 873 # rsync
acl Safe_ports port 80 # http
acl Safe_ports port 21 # ftp
acl Safe_ports port 443 563 # https, snews
acl Safe_ports port 70 # gopher
acl Safe_ports port 210 # wais
acl Safe_ports port 1025-65535 # unregistered ports
acl Safe_ports port 280 # http-mgmt
acl Safe_ports port 488 # gss-http
acl Safe_ports port 591 # filemaker
acl Safe_ports port 777 # multiling http
acl Safe_ports port 631 # cups
acl Safe_ports port 873 # rsync
acl Safe_ports port 901 # SWAT
acl purge method PURGE
acl CONNECT method CONNECT
http_access allow manager localhost
http_access deny manager
http_access allow lan
http_access allow purge localhost
http_access deny purge
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access allow localhost
http_access deny all
http_reply_access allow all
icp_access allow all
http_port 3128 transparent
hierarchy_stoplist cgi-bin ?
access_log /var/log/squid3/access.log squid
coredump_dir /var/spool/squid3
refresh_pattern ^ftp:        1440    20%    10080
refresh_pattern ^gopher:    1440    0%    1440
refresh_pattern -i (/cgi-bin/|\?) 0    0%    0
refresh_pattern (Release|Packages(.gz)*)$      0       20%     2880
refresh_pattern .        0    20%    4320
visible_hostname MusicServer
always_direct allow all
hosts_file /etc/hosts
```

---

### Post by ElToro on 2013-09-19
Added info: This is a network without DHCP. All addresses on the network are static.

---

### Post by ElToro on 2013-09-19
More added info: When I do *sudo squid3 restart* I get:
2013/09/20 01:37:59| WARNING: (B) '::/0' is a subnetwork of (A) '::/0'
2013/09/20 01:37:59| WARNING: because of this '::/0' is ignored to keep splay tree searching predictable
2013/09/20 01:37:59| WARNING: You should probably remove '::/0' from the ACL named 'all'
2013/09/20 01:37:59| WARNING: Netmasks are deprecated. Please use CIDR masks instead.
2013/09/20 01:37:59| WARNING: IPv4 netmasks are particularly nasty when used to compare IPv6 to IPv4 ranges.
2013/09/20 01:37:59| WARNING: For now we will assume you meant to write /32

---

### Post by ElToro on 2013-09-19
Got it to work! Using this setup: [http://ubuntuforums.org/showthread.php?t=2168571](http://ubuntuforums.org/showthread.php?t=2168571), but with static IPs on clients.  Note: Each connection needs to have gateway on eth1 (in my case 10.0.0.1), while DNS is the cable modem on 192.168.0.1.

---

