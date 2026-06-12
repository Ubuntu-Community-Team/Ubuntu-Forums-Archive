---
title: "How to add ICMP rule to allow clients to ping my server?"
date: 2020-02-18
forum: Networking &amp; Wireless
---

### Post by bc-uk on 2020-02-18
I have two servers. First server is running Red Hat Linux Enterprise. This is how I set its firewall to accept ping requests:

```
sudo firewall-cmd --zone=public --permanent --add-port=5000/tcp

sudo firewall-cmd --zone=public --permanent --add-port=5000/udp

firewall-cmd --permanent --direct --add-rule ipv4 filter INPUT 0 -p icmp -s 0.0.0.0/0 -d 0.0.0.0/0 -j ACCEPT
```

I also have a freshly setup Ubuntu server. Here's how I opened the ports:

```
sudo ufw allow 5000/tcp

sudo ufw allow 5000/udp
```

And I added the following line to the /etc/ufw/before.rules file (as suggested elsewhere online):

```
-A ufw-before-input -s 0.0.0.0/0 -d 0.0.0.0/0 -p icmp --icmp-type echo-request -j ACCEPT
```

I restarted ufw, but am still not able to ping this server.

I've dumped the results of iptables -L in the file below, in case it might help:

[https://www.dropbox.com/s/6rg3r5kfsj0zinu/iptables_output.txt?dl=0](https://www.dropbox.com/s/6rg3r5kfsj0zinu/iptables_output.txt?dl=0)

I'm new to ubuntu, so not sure what to do next. Any help much appreciated.

---

### Post by EuclideanCoffee on 2020-02-18
Ensure this returns 0.

cat /proc/sys/net/ipv4/icmp_echo_ignore_all

If not, add it as a rule.

# echo “net.ipv4.icmp_echo_ignore_all = 0” >> /etc/sysctl.conf 
# sysctl -p

---

### Post by bc-uk on 2020-02-18
Thanks for the suggestion, but that is already set to 0 in /etc/sysctl.conf and /etc/ufw/sysctl.conf. Here's the full listing for /etc/ufw/sysctl.conf:

```
# Configuration file for setting network variables. Please note these settings
# override /etc/sysctl.conf. If you prefer to use /etc/sysctl.conf, please
# adjust IPT_SYSCTL in /etc/default/ufw.
#

# Uncomment this to allow this host to route packets between interfaces
#net/ipv4/ip_forward=1
#net/ipv6/conf/default/forwarding=1
#net/ipv6/conf/all/forwarding=1

# Turn on Source Address Verification in all interfaces to prevent some
# spoofing attacks
net/ipv4/conf/default/rp_filter=1
net/ipv4/conf/all/rp_filter=1

# Do not accept IP source route packets (we are not a router)
net/ipv4/conf/default/accept_source_route=0
net/ipv4/conf/all/accept_source_route=0
net/ipv6/conf/default/accept_source_route=0
net/ipv6/conf/all/accept_source_route=0

# Disable ICMP redirects. ICMP redirects are rarely used but can be used in
# MITM (man-in-the-middle) attacks. Disabling ICMP may disrupt legitimate
# traffic to those sites.
net/ipv4/conf/default/accept_redirects=0
net/ipv4/conf/all/accept_redirects=0
net/ipv6/conf/default/accept_redirects=0
net/ipv6/conf/all/accept_redirects=0

# Ignore bogus ICMP errors
net/ipv4/icmp_echo_ignore_broadcasts=1
net/ipv4/icmp_ignore_bogus_error_responses=1
net/ipv4/icmp_echo_ignore_all=0

# Don't log Martian Packets (impossible packets)
net/ipv4/conf/default/log_martians=0
net/ipv4/conf/all/log_martians=0

# Change to '1' to enable TCP/IP SYN cookies This disables TCP Window Scaling
# ([http://lkml.org/lkml/2008/2/5/167](http://lkml.org/lkml/2008/2/5/167))
net/ipv4/tcp_syncookies=0

#net/ipv4/tcp_fin_timeout=30
#net/ipv4/tcp_keepalive_intvl=1800

# normally allowing tcp_sack is ok, but if going through OpenBSD 3.8 RELEASE or
# earlier pf firewall, should set this to 0
net/ipv4/tcp_sack=1

# Uncomment this to turn off ipv6 autoconfiguration
#net/ipv6/conf/default/autoconf=0
#net/ipv6/conf/all/autoconf=0

# Uncomment this to enable ipv6 privacy addressing
#net/ipv6/conf/default/use_tempaddr=2
#net/ipv6/conf/all/use_tempaddr=2
```

---

### Post by bc-uk on 2020-02-18
And here's my etc/ufw/before.rules file:

```
# rules.before
#
# Rules that should be run before the ufw command line added rules. Custom
# rules should be added to one of these chains:
#   ufw-before-input
#   ufw-before-output
#   ufw-before-forward
#

# Don't delete these required lines, otherwise there will be errors
*filter
:ufw-before-input - [0:0]
:ufw-before-output - [0:0]
:ufw-before-forward - [0:0]
:ufw-not-local - [0:0]
# End required lines


# allow all on loopback
-A ufw-before-input -i lo -j ACCEPT
-A ufw-before-output -o lo -j ACCEPT

# quickly process packets for which we already have a connection
-A ufw-before-input -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A ufw-before-output -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A ufw-before-forward -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT

# drop INVALID packets (logs these in loglevel medium and higher)
-A ufw-before-input -m conntrack --ctstate INVALID -j ufw-logging-deny
-A ufw-before-input -m conntrack --ctstate INVALID -j DROP

# ok icmp codes for INPUT
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-input -p icmp --icmp-type source-quench -j ACCEPT
-A ufw-before-input -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-input -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT

# ok icmp code for FORWARD
-A ufw-before-forward -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-forward -p icmp --icmp-type source-quench -j ACCEPT
-A ufw-before-forward -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-forward -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-forward -p icmp --icmp-type echo-request -j ACCEPT

-A ufw-before-input -s 0.0.0.0/0 -d 0.0.0.0/0 -p icmp --icmp-type echo-request -j ACCEPT

# allow dhcp client to work
-A ufw-before-input -p udp --sport 67 --dport 68 -j ACCEPT

#
# ufw-not-local
#
-A ufw-before-input -j ufw-not-local

# if LOCAL, RETURN
-A ufw-not-local -m addrtype --dst-type LOCAL -j RETURN

# if MULTICAST, RETURN
-A ufw-not-local -m addrtype --dst-type MULTICAST -j RETURN

# if BROADCAST, RETURN
-A ufw-not-local -m addrtype --dst-type BROADCAST -j RETURN

# all other non-local packets are dropped
-A ufw-not-local -m limit --limit 3/min --limit-burst 10 -j ufw-logging-deny
-A ufw-not-local -j DROP

# allow MULTICAST mDNS for service discovery (be sure the MULTICAST line above
# is uncommented)
-A ufw-before-input -p udp -d 224.0.0.251 --dport 5353 -j ACCEPT

# allow MULTICAST UPnP for service discovery (be sure the MULTICAST line above
# is uncommented)
-A ufw-before-input -p udp -d 239.255.255.250 --dport 1900 -j ACCEPT

# don't delete the 'COMMIT' line or these rules won't be processed
COMMIT
```

---

### Post by EuclideanCoffee on 2020-02-18
There shouldn't be a problem on the host. Perhaps you are seeing icmp traffic filtered at your layer 2 or layer 3 level. More information on your network topology may be needed.

---

### Post by bc-uk on 2020-02-18
Both servers are VMs running on Oracle Cloud. They're both within a VCN. Here are the VCN Ingress rules:

[IMG]https://i.imgur.com/gGS3ZwK.png[/IMG]

---

### Post by EuclideanCoffee on 2020-02-18
Yes, it appears Oracle is blocking ICMP traffic.

From Oracle's documentation [source: [https://docs.cloud.oracle.com/en-us/iaas/Content/Network/Concepts/securityrules.htm](https://docs.cloud.oracle.com/en-us/iaas/Content/Network/Concepts/securityrules.htm)]

[h=3]Enabling Path MTU Discovery Messages for Stateless Rules[/h][COLOR=#666666][FONT=&quot]If you decide to use stateless security rules to allow traffic to/from endpoints outside the VCN, it's important to add a security rule that allows ingress ICMP traffic type 3 code 4 from source 0.0.0.0/0 and any source port. This rule enables your instances to receive Path MTU Discovery fragmentation messages. This rule is critical for establishing a connection to your instances. Without it, you can experience connectivity issues. For more information, see [Hanging Connection]("https://docs.cloud.oracle.com/en-us/iaas/Content/Network/Troubleshoot/connectionhang.htm").[/FONT][/COLOR]
[h=2]Rules to Enable Ping[/h][COLOR=#666666][FONT=&quot]The VCN's [default security list]("https://docs.cloud.oracle.com/en-us/iaas/Content/Network/Concepts/securitylists.htm#Default") contains several default rules, but not one to allow ping requests. If you want to ping an instance, make sure the instance's applicable security lists or NSGs include an *additional* stateful ingress rule to specifically allow ICMP traffic type 8 from the source network you plan to ping from. To allow ping access from the internet, use 0.0.0.0/0 for the source. Note that this rule for pinging is separate from the default ICMP-related rules in the default security list. Do not remove those rules.[/FONT][/COLOR]

---

### Post by bc-uk on 2020-02-18
That's odd, because the RHLE VM server works fine (can be pinged OK) - both VMs are within the same VCN. Anyway, I added the rule, as suggested (see below), but still not able to ping the Ubuntu VM.

[IMG]https://i.imgur.com/9nEO8rs.png[/IMG]

---

### Post by EuclideanCoffee on 2020-02-18
Check dmesg and journalctl -xe for messages indicating that ufw is blocking icmp.

---

### Post by bc-uk on 2020-02-19
Tried looking at both of those, and there's no mention of ufw port 5000, or the IP address I try to ping from. I also tried disabling ufw, but still not able to ping the server.

---

### Post by bc-uk on 2020-02-19
With ufw disabled, pinging the server on port 22 works, so I guess this narrows it down a bit?

---

### Post by EuclideanCoffee on 2020-02-19
Boy, this is confusing. You can try dropping your iptables with iptables -F and then ping.

[Note: I use ufw for my Debian public server on a VPS, and I don't have so many problems. Perhaps it's the Oracle image adding extra layers of security that I'm not familiar with. Typically Ubuntu has only a few minimal security features, depending on versions.]

---

### Post by bc-uk on 2020-02-19
Dropping the iptables worked - I was then able to ping the server on port 5000. However, I then re-enabled ufw, and it kicked me out of the server, and I can no longer log back in. I guess I have trashed this instance? I can delete it and set a new one up if there's no other option. Luckily there wasn't any important data on it.

---

### Post by bc-uk on 2020-02-19
Crisis averted - rebooting the VM has let me back in. I guess it's not OK to keep ufw disabled if this server is publicly accessible?

---

### Post by bc-uk on 2020-02-19
Also, rebooting the server has caused the route tables to be recreated:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG        0 0          0 ens3
10.0.0.0        0.0.0.0         255.255.255.0   U         0 0          0 ens3
169.254.0.2     10.0.0.1        255.255.255.255 UGH       0 0          0 ens3
172.17.0.0      0.0.0.0         255.255.0.0     U         0 0          0 docker0
```
Is it obvious from that what the issue is?

---

### Post by EuclideanCoffee on 2020-02-19
Not entirely obvious from this table. iptables -F will drop your firewall rules. You need to save your iptables when you drop them, so by rebooting, your iptables were restored likely.

So now that issue is gone since the reboot? That's good. I wish we could've gleamed a little more information on what was the root of the problem.

Edit:

You can manage your firewall rules directly with iptables, since that is what ufw is doing in a nicer format. It's up to you if you'd like to manage your firewalls in this way. I use ufw and haven't had this problem yet, so I cannot say what is yours.

---

### Post by bc-uk on 2020-02-19
> **EuclideanCoffee said:**
> So now that issue is gone since the reboot?
No, I can only ping on 5000 if I drop the iptable.

---

### Post by EuclideanCoffee on 2020-02-21
Sorry for the delay. I was confused what you meant by pinging a certain port number.

Ports belong to your transport layer, typically TCP or UDP. So you shouldn't typically be able to ping a port, as ICMP does this.

You have a few tools available. The most common are telnet and nmap.

When you say you're pinging the port, you are literally able to write the ping command and only to specific ports?

This makes me suspect that there is something outside of the Ubuntu box causing the problem. If you have bridging, I would look there.

I recommend this as further reading: [https://serverfault.com/questions/309357/ping-a-specific-port](https://serverfault.com/questions/309357/ping-a-specific-port)

This is the extent of my knowledge. So I wish you best of luck.

---

