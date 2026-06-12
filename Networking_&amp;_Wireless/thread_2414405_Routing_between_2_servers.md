---
title: "Routing between 2 servers"
date: 2019-03-09
forum: Networking &amp; Wireless
---

### Post by uthall on 2019-03-09
Hello,

I have 2 ubuntu 14 server configured as per below (example ips):

ServerA: Internal IP 192.168.1.1 External IP 123.123.123.1 
ServerB: Internal IP 192.168.1.2 External IP 234.234.234.1 

I have an appliction on ServerA that communicates with ServerB only using its public addess of 234.234..234.1.

I want to force the app to communicate to ServerB over the internal 192 network.

Is there any way i can do this using routing tables?

Any advice would be great.

---

### Post by TheFu on 2019-03-09
If they are on the same subnet, then the 192.168.1.x router should handle it.Just use the 192.168.x.x IPs/hostnames when you want to stay on that subnet.  If not, you can add direct routes from each machine to the other using the route command. 

Support for 14.04 ends in about a month.  Move to a supported release - 16.04 or 18.04 ASAP.

And just make certain that you have the route you want used with a lower metric setting. 

On each machine, you'll need to show the routing table.  **route -n **will do that.

---

### Post by uthall on 2019-03-09
Thanks but the app on serverA will communicate to serverB over the public interface, not the private one.

Essentially i want to redirect any traffic from ServerA to 234.234.234.1 (ServerB Public int), to 192.168.1.2 (ServerB  private int)....and vice versa from ServerB to A

Im hoping this makes sense.....

---

### Post by Doug S on 2019-03-10
Does the app decide that server B is at 234.234.234.1 via some external DNS lookup of some domain name?

If yes, then one suggestion is to override via the /etc/hosts file. (do "man hosts" for details.)
Another suggestion (what I do) is to run a local bind9 DNS server that does the domain name mapping to the internal IP address.

If no, then some iptables rules can be made to work (which I'll think about more, if required).

---

### Post by TheFu on 2019-03-10
Will definitely need to do some firewall work.
Seeing the routing table would be helpful.

At this point, perhaps asking what the final purpose of this question is would be helpful? Often specific questions like this are trying to re-invent a solution that has already been solved.

---

### Post by uthall on 2019-03-11
No problem.....

I have 2 OVH servers with vrack.

Both have a public IP, as well as private ips (vrack)

I have an application that sends data between the 2 servers, however the application only uses the public interface (ip), and wont use the internal private ips to communicate

Obviously, the performance will be better if the 2 servers communicate using the private addresses, so i need to find a way to make them both talk on the private ips.
 
Ive read that iptables will take any request from serverA to the public interface of serverB and redirect it to the private address of serverB, and vice versa.
 
I just don&#8217;t know the exact format of the iptables command.
 
Any help would be fantastic.

---

### Post by TheFu on 2019-03-11
> 
Obviously, the performance will be better if the 2 servers communicate using the private addresses, so i need to find a way to make them both talk on the private ips.

This is not obvious at all. Is the current networking near the max that it supports?  Usually, performance is NOT hindered by networking, rather other elements in the system are the issue.

And seeing the current routing tables on both hosts is still needed.

---

### Post by uthall on 2019-03-11
I have limited bandwidth out my public ip, and near unlimited over my private, so yes, performance will be better if they talks private ip to private ip.

route table server 1 (192.168.1.1)
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         144.217.74.254  0.0.0.0         UG    0      0        0 eth2
10.0.3.0        0.0.0.0         255.255.255.0   U     0      0        0 lxcbr0
144.217.74.0    0.0.0.0         255.255.255.0   U     0      0        0 eth2
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth3


Server 2 (192.168.1.2)
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         139.99.122.254  0.0.0.0         UG    0      0        0 eth0
10.0.3.0        0.0.0.0         255.255.255.0   U     0      0        0 lxcbr0
139.99.122.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1

---

### Post by SeijiSensei on 2019-03-11
Maybe I'm just dense, but why can't you use the internal IP addresses in the application itself rather than the public addresses?

---

### Post by uthall on 2019-03-11
lol......no your not, i did think of that.

Unfortunatly, the app only uses the public ips......cant be changed

---

### Post by Doug S on 2019-03-11
> **uthall said:**
> Unfortunatly, the app only uses the public ips......cant be changedI ask again (please see my earlier post): Is that via external DNS lookup of some donamin name?

---

### Post by uthall on 2019-03-11
i do not know, i cant tell......sorry

---

### Post by Doug S on 2019-03-11
Then my suggestion is that you try it (the /etc/hosts override method). If the app is using a FQDN (Fully Qualified Domain Name), then it should do what you want, but if the app is using a hard coded IP address, then it won't.

Example: s17.smythies.com is at 192.168.111.120 and DNS inquires will be answered by my internal DNS (bind). On another computer, s15, I'll override the DNS via /etc/hosts:

```
doug@s15:/etc$ ping s17
PING s17.smythies.com ([COLOR="#FF0000"]192.168.111.120[/COLOR]) 56(84) bytes of data.
64 bytes from s17.smythies.com (192.168.111.120): icmp_seq=1 ttl=64 time=0.604 ms
64 bytes from s17.smythies.com (192.168.111.120): icmp_seq=2 ttl=64 time=0.285 ms
64 bytes from s17.smythies.com (192.168.111.120): icmp_seq=3 ttl=64 time=0.272 ms
^C
--- s17.smythies.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 0.272/0.387/0.604/0.153 ms
doug@s15:/etc$ sudo cp hosts hosts.backup
doug@s15:/etc$ sudo nano hosts
doug@s15:/etc$ ping s17
PING s17.smythies.com ([COLOR="#FF0000"]192.168.111.80[/COLOR]) 56(84) bytes of data.

```Where this is what I did:
```
doug@s15:/etc$ cat hosts
127.0.0.1       localhost
127.0.1.1       s15.smythies.com        s15
127.0.1.1       s15.smythies.com        s15

[COLOR="#FF0000"]192.168.111.80  s17.smythies.com        s17[/COLOR]

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```By the way, I agree with TheFu and am not confident that it'll make any difference to throughput.

EDIT: I read a bit about OVH and vrack. I suppose, depending on your options, your "local" network bandwidth might be higher.

---

### Post by uthall on 2019-03-11
Thanks, ill try, but as im not sure if the app uses dns, id also like to try iptables.

Can you give me an iptable config?

[COLOR=#333333][FONT=&quot]server1: 192.168.1.1 (vrack)(eth3), 144.217.74.68 (public)(eth2)[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]server2: 192.168.1.2 (vrack)(eth1), 139.99.122.3 (public)(eth0)

[/FONT][/COLOR]

---

### Post by TheFu on 2019-03-11
Will ping from server1 to 192.168.1.2 work?
Will ping from server2 to 192.168.1.1 work?

Sometimes those subnets on different servers won't actually be on the same LAN unless specifically requested by the client. In fact, you can set this up in a lab easily using virtual machines.  Just setup 2 different NAT network devices on the same VM host ... or put the VMs on different VM-hosts and choose NAT for the networking.

If so, then I bet the /etc/hosts method will work perfectly. I use this all the time between LAN and WAN connection needs.  From inside the LAN, the /etc/hosts file points to other internal IPs for servers.  From the WAN, external DNS points to the public IPs for the rest of the world.  It is easier if you have different names-to-IP and the servers support that, but it also works fine without it.
```

192.168.1.1  server1  pub1.example.com
192.168.1.2   server2  pub2.example.com
```
Put these on both systems and any others on the LAN that need access to the 192.168.x.x addresses.

That's it. Much easier than setting up forwarding with iptables.

BTW, when posting code/text output, especially stuff that lines up, please use code tags.  1,000x easier to read.
 
Let me look up the iptables stuff ... I think you need PREROUTING and FORWARD rules.  Actually, if they are on the same real subnet, I don't think this will work.  Need to pull out a book. Hopefully, it isn't still on loan.  This is the book: [https://www.amazon.com/Linux-Firewalls-Detection-Response-iptables/dp/1593271417](https://www.amazon.com/Linux-Firewalls-Detection-Response-iptables/dp/1593271417) if you need a copy.

---

### Post by Doug S on 2019-03-11
> **uthall said:**
> Thanks, ill try, but as im not sure if the app uses dns, id also like to try iptables.

Can you give me an iptable config?

[COLOR=#333333][FONT=&quot]server1: 192.168.1.1 (vrack)(eth3), 144.217.74.68 (public)(eth2)[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]server2: 192.168.1.2 (vrack)(eth1), 139.99.122.3 (public)(eth0)

[/FONT][/COLOR]Maybe someone else can provide the iptables solution. It would take me a few hours to figure out and test (if I could even figure out a way to test it). I don't want to unless the hosts file override method doesn't work.

If you are not sure how to test if it is working or not with your app then I would suggest to use tcpdump (or wireshark, if you prefer) to check. On server 2:
```
sudo tcpdump -n -tttt -i eth0 host 144.217.74.68
```
and in another terminal, still on server 2:
```
sudo tcpdump -n -tttt -i eth1 host 192.168.1.1
```and you should see the traffic jump from eth0 to eth1 when you make the change to /etc/hosts. (if there is a lot of traffic, you might need to just run the tcpdump commands for a moment.)

EDIT: Oh, I see TheFu also replied, I guess while I was typing. @TheFu: from what I read about vrack I'm pretty sure it is all one 192.168.1.X sub-net specific to this client.

---

### Post by uthall on 2019-03-11
Thanks guys, ive tried the host solution and it just wont work. I dont know why.

I can certainly ping the hostnames and it resolved to their internal addresses, but the app just won&#8217;t work, or wont use the hosts file.

I think iptables is the only way, and help would be great.

---

### Post by TheFu on 2019-03-12
Slept on this problem.  Since they are on the same subnet, we just need to manage the metric settings for each.
See how better formatting helps?  Currently, 
```
route table server 1 (192.168.1.1)
Destination  Gateway        Genmask       Flags Metric Ref Use Iface
0.0.0.0      144.217.74.254 0.0.0.0       UG    0      0   0   eth2
10.0.3.0     0.0.0.0        255.255.255.0 U     0      0   0   lxcbr0
144.217.74.0 0.0.0.0        255.255.255.0 U     0      0   0   eth2
192.168.1.0  0.0.0.0        255.255.255.0 U     0      0   0   eth3


Server 2 (192.168.1.2)
Destination  Gateway        Genmask       Flags Metric Ref Use Iface
0.0.0.0      139.99.122.254 0.0.0.0       UG    0      0   0   eth0
10.0.3.0     0.0.0.0        255.255.255.0 U     0      0   0   lxcbr0
139.99.122.0 0.0.0.0        255.255.255.0 U     0      0   0   eth0
192.168.1.0  0.0.0.0        255.255.255.0 U     0      0   0   eth1
```


Something like this is what you need.
```
route table server 1 (192.168.1.1)
Destination  Gateway        Genmask       Flags Metric Ref Use Iface
0.0.0.0      144.217.74.254 0.0.0.0       UG    500    0   0   eth2
10.0.3.0     0.0.0.0        255.255.255.0 U     500    0   0   lxcbr0
144.217.74.0 0.0.0.0        255.255.255.0 U     500    0   0   eth2
192.168.1.0  0.0.0.0        255.255.255.0 U     100    0   0   eth3

Server 2 (192.168.1.2)
Destination  Gateway        Genmask       Flags Metric Ref Use Iface
0.0.0.0      139.99.122.254 0.0.0.0       UG    500    0   0   eth0
10.0.3.0     0.0.0.0        255.255.255.0 U     500    0   0   lxcbr0
139.99.122.0 0.0.0.0        255.255.255.0 U     500    0   0   eth0
192.168.1.0  0.0.0.0        255.255.255.0 U     100    0   0   eth1  
```

So the 192.168.x.x network gets priority.  metric can be modified a few different ways. The /etc/network/interfaces file is how I'd do it.  route command is another.  Perhaps ethtool, IDK.  Just add to each NIC stanza ```

              metric metric
                     Routing metric for default gateway (integer)
``` according to the interfaces manpage. E.g.
```
metric 500
```
or 100 for the 192.168.x.x stanzas for eth[13] on the hosts.

But as long as the metrics are zero (0) for all the networks, no other routes can be set as lower numbers, aka higher priority. By changing them to 500 and 100, lots of wiggle room is available.  Lower metric values get priority.

And for people like me who hate the non-column output from *ip route*, use **ip route | column -t**.

---

### Post by Doug S on 2019-03-12
> **uthall said:**
> Thanks guys, ive tried the host solution and it just wont work. I dont know why.

I can certainly ping the hostnames and it resolved to their internal addresses, but the app just won’t work, or wont use the hosts file.

I think iptables is the only way, and help would be great.I wonder if some DNS lookup caching is involved? Did you restart the app, after making the changes?

If the app really has hardcoded IP addresses, then it must be custom for you and therefore you should have the source and be able to change it.

@TheFu: I am not following your previous post about routing, and do not see how priority changes will change things. I have never been very good with routing, so maybe I'll learn something.

---

### Post by uthall on 2019-03-12
Thanks.......but i think im a little lost.

How does the above turn a packet from 139.99.122.3, destined for 144.217.74.68, turn into a packed from 192.168.1.1 destined for 192.168.1.2?

---

### Post by Doug S on 2019-03-12
For the iptables method, this seems to work on my main test server. I tested it by configuring a raspberry pi to use a static address for a temporary LAN that I made, also using an extra network interface card on my test server (s15). It redirects requests to a non-existent 192.168.111.65 to the raspberry pi at 192.168.237.8. When I ping, the replies come back from 192.168.237.8 but appear to have come from 192.168.111.65, as expected.

[B][SIZE=3]NOTE 1: You must be extremely careful with this stuff or you might lose the ability to communicate with these servers entirely.
NOTE 2: You need to merge what I suggest here with your existing iptables rules. And the rule order matters.
PROCEED AT YOUR OWN RISK.[/SIZE][/B]

This is the iptables script:
```
#!/bin/sh
FWVER=0.01
#
# uthall_rules Smythies 2019.03.12 Ver:0.01
#       See here:
#       https://ubuntuforums.org/showthread.php?t=2414405
#
#       run as sudo on s15.
#
#       Note: These rules likely need to be merged with
#       the existing iptables rules set.
#       Be extremely careful or access to the remote servers
#       might be lost.

echo "Loading uthall_rules rule set version $FWVER..\n"

# The location of the iptables program
#
IPTABLES=/sbin/iptables

#Setting the EXTERNAL and INTERNAL interfaces and addresses for the network
#
# Smythies (for testing)
EXTIF="br0"
EXTIP="192.168.111.112"
INTIF="enp1s0"
INTIP="192.168.237.7"

NETWORK="192.168.111.0/24"

UNIVERSE="0.0.0.0/0"

#CRITICAL: Enable IP forwarding since it is disabled by default
#
echo Enabling forwarding...
echo "1" > /proc/sys/net/ipv4/ip_forward

# Clearing any previous configuration
# Be careful here. I can do this on s15, but do not know
# about uthall's remote servers.
#
echo "  Clearing any existing rules and setting default policies.."
$IPTABLES -P INPUT ACCEPT
$IPTABLES -F INPUT
$IPTABLES -P OUTPUT ACCEPT
$IPTABLES -F OUTPUT
$IPTABLES -P FORWARD ACCEPT
$IPTABLES -F FORWARD
$IPTABLES -t nat -F
# Delete user defined chains
$IPTABLES -X
# Reset all IPTABLES counters
$IPTABLES -Z
# Smythies: While my references do not have it, I think this is needed.
$IPTABLES -t nat -Z

# First: redirect the traffic to the other network.
$IPTABLES -t nat -A OUTPUT -d 192.168.111.65 -j DNAT --to-destination 192.168.237.8

# Second: The desination needs to know what IP address to reply to.
$IPTABLES -t nat -A POSTROUTING -o $INTIF -j SNAT --to $INTIP

# At this point carry on. You (uthall) need to merge this into your existing iptables rule set.
#

echo uthall_rules rule set version $FWVER done.

```
On the test network interface on the server I ran:
```
sudo tcpdump -n -tttt -i enp1s0
```
which for this command on the server:
```
ping 192.168.111.65
```gave:
```
2019-03-12 13:56:26.449793 IP 192.168.237.7 > 192.168.237.8: ICMP echo request, id 3360, seq 8, length 64
2019-03-12 13:56:26.450422 IP 192.168.237.8 > 192.168.237.7: ICMP echo reply, id 3360, seq 8, length 64
2019-03-12 13:56:27.473775 IP 192.168.237.7 > 192.168.237.8: ICMP echo request, id 3360, seq 9, length 64
2019-03-12 13:56:27.474378 IP 192.168.237.8 > 192.168.237.7: ICMP echo reply, id 3360, seq 9, length 64
2019-03-12 13:56:28.497772 IP 192.168.237.7 > 192.168.237.8: ICMP echo request, id 3360, seq 10, length 64
2019-03-12 13:56:28.498455 IP 192.168.237.8 > 192.168.237.7: ICMP echo reply, id 3360, seq 10, length 64

```

Which results in:
```
doug@s15:~/iptables-tests$ ping 192.168.111.65
PING 192.168.111.65 (192.168.111.65) 56(84) bytes of data.
64 bytes from 192.168.111.65: icmp_seq=1 ttl=64 time=0.770 ms
64 bytes from 192.168.111.65: icmp_seq=2 ttl=64 time=0.722 ms
64 bytes from 192.168.111.65: icmp_seq=3 ttl=64 time=0.616 ms
64 bytes from 192.168.111.65: icmp_seq=4 ttl=64 time=0.708 ms
64 bytes from 192.168.111.65: icmp_seq=5 ttl=64 time=0.676 ms
64 bytes from 192.168.111.65: icmp_seq=6 ttl=64 time=0.678 ms
64 bytes from 192.168.111.65: icmp_seq=7 ttl=64 time=0.617 ms

```

---

### Post by uthall on 2019-03-13
Thanks, ill try this out.

Is this persistent, or will i lose this on reboot?

---

### Post by Doug S on 2019-03-13
> **uthall said:**
> Is this persistent, or will i lose this on reboot?No, it is not persistent.

For your 14.04 servers, and also for 16.04 (which is the version I'm still using) You can do this (where doug_firewall is my iptables and related items scripts):

```
doug@DOUG-64:~$ [COLOR="#FF0000"]cat /etc/network/interfaces[/COLOR]
# interfaces file for smythies.com 2016.01.30
#       attempt to set local DNS herein, as the method
#       used with the old 12.04 server no longer works.
#
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
[COLOR="#FF0000"]pre-up /home/doug/init/doug_firewall[/COLOR]
dns-nameservers 127.0.0.1

# The primary interface (d-link PCI card)
auto enp4s0
iface enp4s0 inet dhcp

# Local network interface (uses built in ethernet port)
auto enp2s0
iface enp2s0 inet static
  address 192.168.111.1
  network 192.168.111.0
  netmask 255.255.255.0
  broadcast 192.168.111.255

```
For a default 18.04 installation with netplan (which I do not like), the above method no longer works.

---

### Post by TheFu on 2019-03-13
> **Doug S said:**
>  @TheFu: I am not following your previous post about routing, and do not see how priority changes will change things. I have never been very good with routing, so maybe I'll learn something.

Perhaps I'm missing something. Questions help us to discover those issues.
I wasn't assuming hard-coded IPs. I was assuming hard-coded DNS-names.

I was assuming that /etc/nsswitch.conf is configured with "files" before "DNS". This is the default. The specific line:
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns
```

Routing doesn't matter when systems are on the same ethernet subnet. No routing involved.

So, if the /etc/hosts files on each system have the public DNS names pointing at the LAN IPs (as shown above). So, if the LAN IPs aren't being used after making that change, then the metric for each route (as shown in the route -n output), is going through first seen, first used.  By clearly making the LAN a higher route for other LAN addresses, then that interface will be used by both systems - eth1 and eth3 (from memory, don't quote me).

So, all traffic sent to server1.example.com from server2 will use the LAN subnet and all traffic sent to server2.example.com from server1 will use the LAN subnet too.  This offloads the public interfaces from being used for traffic.

My home-biz network is setup this way, but with 2 different non-routible, internal, LANs.  I have a storage network that is physically separate from the internet connected LAN.  All NAS/backup traffic goes over the storage LAN because of /etc/hosts configurations.  The only difference is that I have different names for the front-LAN and storage-LAN.  Internally, I access some websites hosted on the LAN using the public DNS names which resolve to internal LAN reverse-proxy servers here.  From outside, public DNS resolves to a few different IPs which have ports forwarded to the same reverse-proxy servers.

The OP hasn't shown any updates to the routing table or /etc/hosts at this point, so I'm lost as to what the config is at this point.  Servers running public accessible services need to be extremely careful with firewall rules.  Mine have thousands of rules, recently reduced thanks to **ipset**, to just about 50 each.  Interactions with iptables rules can be a challenge.

But I easily may have missed something.

---

### Post by SeijiSensei on 2019-03-13
> **uthall said:**
> Hello,

I have 2 ubuntu 14 server configured as per below (example ips):

ServerA: Internal IP 192.168.1.1 External IP 123.123.123.1 
ServerB: Internal IP 192.168.1.2 External IP 234.234.234.1 

I have an appliction on ServerA that communicates with ServerB only using its public addess of 234.234..234.1.

I want to force the app to communicate to ServerB over the internal 192 network.

Is there any way i can do this using routing tables?

Any advice would be great.

The amount of material in this thread is daunting by now.  So I'm going to start from scratch.

Does each server have two interfaces, one on the 192.168.1.0/24 subnet (lets call it eno1), and one on the public Internet (eno0) with addresses 123.123.123.1 and 234.234.234.1? Each machine can presumably ping the other via either interface, correct?  Also, I'm assuming you have IPv4 packet forwarding enabled in /etc/sysctl.conf (by uncommenting "net.ipv4.ip_forward=1" in that file). That's a requirement for this method because packets are going to be coming in the servers' internal interfaces intended for the external ones.

If so, I'd start by trying a simple pair of routes.  On ServerA

```
sudo ip route add 234.234.234.1 via 192.168.1.2
```

and on ServerB

```
sudo ip route add 123.123.123.1 via 192.168.1.1
```

If you have iptables rules in place, you might also need, on serverA,

```
sudo iptables -I INPUT -i eno1 -s 192.168.1.0/24 -d 123.123.123.1
```

and if FORWARD is blocked by default a rule something like

```
sudo iptables -I FORWARD -i eno1 -d 123.123.123.1
```

With corresponding rules on ServerB, of course.

---

### Post by Doug S on 2019-03-13
For the iptables rules, I suspect SeijiSensei meant to write:
```
sudo iptables -I INPUT -i eno1 -s 192.168.1.0/24 -d 123.123.123.1 -j ACCEPT
```and
```
sudo iptables -I FORWARD -i eno1 -d 123.123.123.1 -j ACCEPT
```because a rule with nothing to do if the packet matches won't do anything other than increment the rule counters.

@TheFu: Thanks for your further explanation. Still not sure I understand and I have now taken down my experimental setup and don't have time to set it up again.

---

### Post by SeijiSensei on 2019-03-14
Whoops. Yeah I forgot the "-j ACCEPT" targets!

Thanks, Doug.

---

### Post by uthall on 2019-03-16
> **Doug S said:**
> For the iptables method, this seems to work on my main test server. I tested it by configuring a raspberry pi to use a static address for a temporary LAN that I made, also using an extra network interface card on my test server (s15). It redirects requests to a non-existent 192.168.111.65 to the raspberry pi at 192.168.237.8. When I ping, the replies come back from 192.168.237.8 but appear to have come from 192.168.111.65, as expected.

[B][SIZE=3]NOTE 1: You must be extremely careful with this stuff or you might lose the ability to communicate with these servers entirely.
NOTE 2: You need to merge what I suggest here with your existing iptables rules. And the rule order matters.
PROCEED AT YOUR OWN RISK.[/SIZE][/B]

This is the iptables script:
```
#!/bin/sh
FWVER=0.01
#
# uthall_rules Smythies 2019.03.12 Ver:0.01
#       See here:
#       https://ubuntuforums.org/showthread.php?t=2414405
#
#       run as sudo on s15.
#
#       Note: These rules likely need to be merged with
#       the existing iptables rules set.
#       Be extremely careful or access to the remote servers
#       might be lost.

echo "Loading uthall_rules rule set version $FWVER..\n"

# The location of the iptables program
#
IPTABLES=/sbin/iptables

#Setting the EXTERNAL and INTERNAL interfaces and addresses for the network
#
# Smythies (for testing)
EXTIF="br0"
EXTIP="192.168.111.112"
INTIF="enp1s0"
INTIP="192.168.237.7"

NETWORK="192.168.111.0/24"

UNIVERSE="0.0.0.0/0"

#CRITICAL: Enable IP forwarding since it is disabled by default
#
echo Enabling forwarding...
echo "1" > /proc/sys/net/ipv4/ip_forward

# Clearing any previous configuration
# Be careful here. I can do this on s15, but do not know
# about uthall's remote servers.
#
echo "  Clearing any existing rules and setting default policies.."
$IPTABLES -P INPUT ACCEPT
$IPTABLES -F INPUT
$IPTABLES -P OUTPUT ACCEPT
$IPTABLES -F OUTPUT
$IPTABLES -P FORWARD ACCEPT
$IPTABLES -F FORWARD
$IPTABLES -t nat -F
# Delete user defined chains
$IPTABLES -X
# Reset all IPTABLES counters
$IPTABLES -Z
# Smythies: While my references do not have it, I think this is needed.
$IPTABLES -t nat -Z

# First: redirect the traffic to the other network.
$IPTABLES -t nat -A OUTPUT -d 192.168.111.65 -j DNAT --to-destination 192.168.237.8

# Second: The desination needs to know what IP address to reply to.
$IPTABLES -t nat -A POSTROUTING -o $INTIF -j SNAT --to $INTIP

# At this point carry on. You (uthall) need to merge this into your existing iptables rule set.
#

echo uthall_rules rule set version $FWVER done.

```
On the test network interface on the server I ran:
```
sudo tcpdump -n -tttt -i enp1s0
```
which for this command on the server:
```
ping 192.168.111.65
```gave:
```
2019-03-12 13:56:26.449793 IP 192.168.237.7 > 192.168.237.8: ICMP echo request, id 3360, seq 8, length 64
2019-03-12 13:56:26.450422 IP 192.168.237.8 > 192.168.237.7: ICMP echo reply, id 3360, seq 8, length 64
2019-03-12 13:56:27.473775 IP 192.168.237.7 > 192.168.237.8: ICMP echo request, id 3360, seq 9, length 64
2019-03-12 13:56:27.474378 IP 192.168.237.8 > 192.168.237.7: ICMP echo reply, id 3360, seq 9, length 64
2019-03-12 13:56:28.497772 IP 192.168.237.7 > 192.168.237.8: ICMP echo request, id 3360, seq 10, length 64
2019-03-12 13:56:28.498455 IP 192.168.237.8 > 192.168.237.7: ICMP echo reply, id 3360, seq 10, length 64

```

Which results in:
```
doug@s15:~/iptables-tests$ ping 192.168.111.65
PING 192.168.111.65 (192.168.111.65) 56(84) bytes of data.
64 bytes from 192.168.111.65: icmp_seq=1 ttl=64 time=0.770 ms
64 bytes from 192.168.111.65: icmp_seq=2 ttl=64 time=0.722 ms
64 bytes from 192.168.111.65: icmp_seq=3 ttl=64 time=0.616 ms
64 bytes from 192.168.111.65: icmp_seq=4 ttl=64 time=0.708 ms
64 bytes from 192.168.111.65: icmp_seq=5 ttl=64 time=0.676 ms
64 bytes from 192.168.111.65: icmp_seq=6 ttl=64 time=0.678 ms
64 bytes from 192.168.111.65: icmp_seq=7 ttl=64 time=0.617 ms

```

Thanks to everyone.

Dougs solution worked perfectly.......

Many thanks!

---

### Post by Doug S on 2019-03-16
Thanks for reporting back. I think SeijiSensei's proposed solution would have also worked. While I struggle with theFu's suggested solution, it would have been nice to know if it worked or not.

All of that aside, what I would really like to know is if this resulted in your original objective of higher throughput between the two computers?

---

### Post by uthall on 2019-03-17
Hey, no drama, wel its hard to say, but ultimately the traffic over the private vrack network is not part of my public bandwidth quota, which is the primary objective.

As to latency it seems bout the same.

---

### Post by The Cog on 2019-03-17
It just occurred to me that you probably don't need all that iptables stuff which is hard to understand and get right anyway. I think you can probably do it with static routes.
Given:
```
ServerA: Internal IP 192.168.1.1 External IP 123.123.123.1
ServerB: Internal IP 192.168.1.2 External IP 234.234.234.1
```

On server A, issue tha command:
```
sudo ip route add 234.234.234.1/32 via 192.168.1.2
```
and on server B, use:
```
sudo ip route add 123.123.123.1/32 via 192.168.1.1
```

---

### Post by Doug S on 2019-03-17
@The Cog: Your proposed solution is the same as SeijiSensei's. His related iptables rules were listed as "might also need", and I agree, because we don't know the OPs existing rules set and default policies. I also agree that /proc/sys/net/ipv4/ip_forward needs to be set.

@uthall: You had originally said this was a performance issue, which is why I asked. However your quota argument makes sense. Thanks.

---

### Post by The Cog on 2019-03-17
> **Doug S said:**
> @The Cog: Your proposed solution is the same as SeijiSensei's. His related iptables rules were listed as "might also need", and I agree, because we don't know the OPs existing rules set and default policies. I also agree that /proc/sys/net/ipv4/ip_forward needs to be set.

Doh! I missed that amongst all the iptables stuff. 
No need to worry about routing metrics - the more specific /32 route will take precedence over the default route whatever the metric values are.

> How does the above turn a packet from 139.99.122.3, destined for 144.217.74.68, turn into a packed from 192.168.1.1 destined for 192.168.1.2It doesn't change the addresses - it just changes the path the packets are sent over, short-circuiting the default route.

---

