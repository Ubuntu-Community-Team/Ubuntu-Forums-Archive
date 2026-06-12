---
title: "iptables - one internal, two external networks"
date: 2014-06-28
forum: Networking &amp; Wireless
---

### Post by oppigard on 2014-06-28
[COLOR=#333333][FONT=Arial]Hi[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]I've set up a ubuntu server (14.04) to act as a router between our local workplace network, internet and corporate network.[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]The server has three network interfaces:[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial][B]
eth0:[/B]
Corporate network.
My ubuntu server has joined the active directory (likewise-open), this is needed to have access to the intranet, SAP and so on. It receives an IP address from the corporate dhcp server.
[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]**eth1:**
Internet.
This is just connected to a "clean" internet line.[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial][B]
eth2:[/B]
Local network
Running DHCP server for local network.

I have configured iptables according to this (with some small changes):[https://help.ubuntu.com/community/Router/Firewall](https://help.ubuntu.com/community/Router/Firewall)
It is routing traffic from clients to the internet, so everything seems to be in order.[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]What is left to do is to make iptables send traffic from clients that has a certain destination ip to the eth0 (corporate), and make it look like the traffic is coming from my server. And allow incoming traffic from those same ip's.[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]
So if anyone could point me in the right direction I would be truly grateful.[/FONT][/COLOR]

---

### Post by bobnn on 2014-06-28
The MASQUERADE or SNAT target in iptables for the corporate interface will make forwarded client traffic look like it is coming from the server.

For example,

```
iptables -t nat -s client_network/client_netmask -o eth0 -A POSTROUTING  -j MASQUERADE

```

or

```

iptables -t nat -s client_network/client_netmask -o eth2 -A POSTROUTING  -j SNAT --to-source server_IP_on_Corporate_network
```

are both accepted by iptables.  I've used the MASQUERADING myself.

the client_netmask can be in bits or network version( eg /24 = /255.255.255.0 )

The SNAT is generally recommended when the interface IP is static.

 Given that all the chains in the filter table are set to drop by default, I think you may have to add rules to the FORWARD chain  to get traffic from the client to the corporate network, but I'm unsure form your description and the link given.

Although the section form the script
```
# Local interface, local machines, going anywhere is valid
-A INPUT -i $INTIF -s $INTNET -d $UNIVERSE -j ACCEPT
```
may cover that.

You may also need an INPUT chain rule accepting  ESTABLISHED,RELATED  on the Corporate interface.  

Sorry to be vague, I don't have a full-blown test lab.

---

### Post by oppigard on 2014-06-29
Thank you very much! :)
Going with SNAT for now. Im currently doing this in Virtualbox with ws2012r2 as domain server, ubuntu server 14.04 as dhcpd and router, and a windows7 client, so I may need to make some changes for the real networks.

The only thing remaining is the changing of "hosts".. What I want is simple; a address (for example google.com) to resolv to the corporate server (eth0)
This is easy with the hosts file for local use, but all the examples I've read on using bind9 seem complex, and does not do what I want.
I've also stumbled upon DnsMasq, but I have not tried this out yet.

---

### Post by bobnn on 2014-06-29
I'm not sure I understand.  Why would you change what IPs google.com resolves to?  Your 3 NIC servers shold already be routing that.

If you want your 3 legged server to also be a web proxy, you run a proxy server on it, and you set it as the web proxy in the browsers that will use it.  If you want a transparent proxy, I've never done that.

---

### Post by oppigard on 2014-06-30
Just my own ignorance I guess :p
I was just thinking that my server would have trouble deciding which NIC to send what traffic to.
For instance, if a domain exists both on the internet, and on the intranet, will it see the difference?
But I'm not sure that the domains exists in both eth0 and eth1, so I'll just wait and see when I test the real server.

Only real "problem" I have now is that I can't ping from my server (only to), but that's probably just a little fault in my iptables:

```

# Corporate network
CORP="eth0"
CORPIP="11.0.0.50/24"


# Internet
INTERNET="eth1"
INTERNETIP="192.168.10.84/24"


# Local network
LAN="eth2"
LANIP="10.0.0.1/32"
LANNET="10.0.0.0/24"


# Everything else
UNIVERSE="0.0.0.0/0"


echo
echo "LAN: [Interface=$LAN] [IP=$INTERNETIP] [Network=$LANNET]"
echo "Internet: [Interface=$INTERNET] [IP=$INTERNETIP]"
echo "Corporate: [Interface=$CORP] [IP=$CORPIP]"


echo
echo -n "Loading rules..."


# Enabling IP forwarding
echo 1 > /proc/sys/net/ipv4/ip_forward




/sbin/iptables-restore <<-EOF;


*filter
:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT DROP [0:0]


###################################################
# INPUT: Incoming traffic from various interfaces #
###################################################


# Loopback interface is valid
-A INPUT -i lo -s $UNIVERSE -d $UNIVERSE -j ACCEPT




# Local interface, local machines, going anywhere is valid
-A INPUT -i $LAN -s $LANNET -d $UNIVERSE -j ACCEPT




# Remote interface, claiming to be local machines, IP spoofing, get lost
-A INPUT -i $INTERNET -s $LANNET -d $UNIVERSE -j REJECT
-A INPUT -i $CORP -s $LANNET -d $UNIVERSE -j REJECT




# External interface, from any source, for ICMP traffic is valid
-A INPUT -i $INTERNET -p ICMP -s $UNIVERSE -d $INTERNETIP -j ACCEPT
-A INPUT -i $CORP -p ICMP -s $UNIVERSE -d $CORPIP -j ACCEPT




# Allow any related traffic coming back to the MASQ server in.
-A INPUT -i $INTERNET -s $UNIVERSE -d $INTERNETIP -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
-A INPUT -i $CORP -s $UNIVERSE -d $CORPIP -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT




# Internal interface, DHCP traffic accepted
-A INPUT -i $LAN -p tcp --sport 68 --dport 67 -j ACCEPT
-A INPUT -i $LAN -p udp --sport 68 --dport 67 -j ACCEPT




# External interface, HTTP/HTTPS traffic allowed
-A INPUT -i $INTERNET -m conntrack --ctstate NEW,ESTABLISHED,RELATED -p tcp -s $UNIVERSE -d $INTERNETIP --dport 80 -j ACCEPT
-A INPUT -i $INTERNET -m conntrack --ctstate NEW,ESTABLISHED,RELATED -p tcp -s $UNIVERSE -d $INTERNETIP --dport 443 -j ACCEPT


# External interface, SSH traffic allowed
-A INPUT -i $INTERNET -m conntrack --ctstate NEW,ESTABLISHED,RELATED -p tcp -s $UNIVERSE -d $INTERNETIP --dport 22 -j ACCEPT


# Accept port 1234 to be forwarded (this rule needs to correspond with PREROUTING rules in NAT table)
#-A FORWARD -i $INTERNET -o $LAN -p tcp --dport 1234 -m conntrack --ctstate NEW,ESTABLISHED,RELATED -j ACCEPT


# Catch-all rule, reject anything else
-A INPUT -s $UNIVERSE -d $UNIVERSE -j REJECT




####################################################
# OUTPUT: Outgoing traffic from various interfaces #
####################################################


# Workaround bug in netfilter
-A OUTPUT -m conntrack -p icmp --ctstate INVALID -j DROP


# Loopback interface is valid.
-A OUTPUT -o lo -s $UNIVERSE -d $UNIVERSE -j ACCEPT




# Local interfaces, any source going to local net is valid
-A OUTPUT -o $LAN -s $INTERNETIP -d $LANNET -j ACCEPT
-A OUTPUT -o $LAN -s $CORPIP -d $LANNET -j ACCEPT


# local interface, MASQ server source going to the local net is valid
-A OUTPUT -o $LAN -s $LANIP -d $LANNET -j ACCEPT




# outgoing to local net on remote interface, stuffed routing, deny
-A OUTPUT -o $INTERNET -s $UNIVERSE -d $LANNET -j REJECT




# anything else outgoing on remote interface is valid
-A OUTPUT -o $INTERNET -s $INTERNETIP -d $UNIVERSE -j ACCEPT
-A OUTPUT -o $CORP -s $CORPIP -d $UNIVERSE -j ACCEPT


# Internal interface, DHCP traffic accepted
-A OUTPUT -o $LAN -p tcp -s $LANIP --sport 67 -d 255.255.255.255 --dport 68 -j ACCEPT
-A OUTPUT -o $LAN -p udp -s $LANIP --sport 67 -d 255.255.255.255 --dport 68 -j ACCEPT




# Catch all rule, all other outgoing is denied and logged. 
-A OUTPUT -s $UNIVERSE -d $UNIVERSE -j REJECT


# Accept solicited tcp packets
-A FORWARD -i $INTERNET -o $LAN -m conntrack --ctstate ESTABLISHED,RELATED  -j ACCEPT
-A FORWARD -i $CORP -o $LAN -m conntrack --ctstate ESTABLISHED,RELATED  -j ACCEPT


# Allow packets across the internal interface
-A FORWARD -i $LAN -o $LAN -j ACCEPT


# Forward packets from the internal network to the Internet
-A FORWARD -i $LAN -o $INTERNET -j ACCEPT
-A FORWARD -i $LAN -o $CORP -j ACCEPT


# Catch-all REJECT rule
-A FORWARD -j REJECT


COMMIT




###########################
# Address translations (only; there is no actual forwarding done here)
###########################
*nat
:PREROUTING ACCEPT [0:0]
:POSTROUTING ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]


# ----- Begin OPTIONAL FORWARD Section -----


#Optionally forward incoming tcp connections on port 1234 to 192.168.0.100
#-A PREROUTING -p tcp -d $INTERNETIP --dport 1234 -m conntrack --ctstate NEW,ESTABLISHED,RELATED -j DNAT --to 192.168.0.100:1234


# ----- End OPTIONAL FORWARD Section -----


# IP-Masquerade
-A POSTROUTING -o $INTERNET -j MASQUERADE
-A POSTROUTING -s $LANNET -o $CORP -j SNAT --to-source 11.0.0.50


COMMIT
EOF


echo " done."

```

---

### Post by SeijiSensei on 2014-06-30
> **oppigard said:**
> I was just thinking that my server would have trouble deciding which NIC to send what traffic to.

That's what routing is for.  Take a look at your routing table with "route -n".  You should see separate routes for each remote network and a default route that points to the Internet gateway.

---

