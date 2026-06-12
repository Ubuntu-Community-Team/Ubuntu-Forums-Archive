---
title: "Setting up an internet gateway"
date: 2008-03-02
forum: Networking &amp; Wireless
---

### Post by Ashfire908 on 2008-03-02
I've been trying to set up a system to act as an internet gateway. It works at the moment, but it doesn't do what I want it to do, and I've had trouble making it work the way I want it to. It needs to (obviously) provide internet to the network, forward new incoming external connections to the server on the network, and it would be nice to have active FTP and IRC DCC work (from looking around you can apparently do this somehow from the gateway). Currently, the only thing that works is the basic internet sharing.

The only thing I need to do right now is to figure out how I should setup my iptables. I've looked though howtos and guide and nothing really works or covers what I want to do and I'm not good at setting up iptables.

Now, for the technical details. The gateway system provides internet from a cell phone dialed into my cell phone company's network (my cell phone company is Alltel). The dialing is done by wvdial, which is enabled/disabled by ifup/ifdown, as the interface ppp0. There are two ethernet interfaces on the gateway, but only one is plugged in and enabled at a time. The first, eth0, is a usb adapter, and is used for when the system is acting like a standard gateway. The second interface, eth1, is for when the gateway is plugged into the router's (the wired DHCP router) WAN port. (This configuration is not used at the time but it may be setup like this in the future.)
The IP of the eth0 interface is set static to 192.168.1.99, and the subnet mask is 255.255.255.0, and the broadcast address is 192.168.1.255. The IP of the eth1 interface is set static to 192.168.2.100, and the subnet mask is 255.255.255.0. The external interface, ppp0, is dynamically set.
The IP of the server I want to route new incoming connections to is 192.168.1.90. The internal network's IPs are in the 192.168.1.0/24 range, and the netmask is 255.255.255.0. Except for the Xbox 360, server, and gateway, all the computers. The DHCP router's IP is 192.168.1.1.

Below is a image of my network layout:
Key:
"Ubuntu Server LAMP, SSHd" - The internal network's server. It's IP is 192.168.1.90.
"Ubuntu Dialup Gateway" - The network's gateway.
Dotted line coming from the gateway to the server - Represents the forwarded incoming connections.

Notes:
The second cell phone connected to the laptop is for the laptop's use only. it is independent from the gateway, and the laptop does not act as a gateway.
There is actually a switch between the gateway and wireless router, and the DHCP router. The switch is unmanaged and does nothing special.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=61396&stc=1&d=1204491712[/IMG]

---

### Post by SpaceTeddy on 2008-03-02
i am not sure i understand the setup of your network... but if i might suggest that you simply setup port-forwarding on your ppp0 device, that should fix the problem.

first, to see if i am on the right track here, i would suggest you add this rule to your iptables set and see if you can reach the webserver running on the ip 192.168.1.90 from the internet (Testing the Apache is easy since it does not do anything fancy :) )
> sudo iptables -A PREROUTING --table nat -i ppp0 -p tcp --dport 80 -j DNAT --to-destination 192.168.1.90

what this does is, it takes any paket comming in from the internet (on the device ppp0, specified with the flag -i) that uses the tcp protocol (-p tcp) directed at port 80 (--dport 80) and rewrites it to be directed at the ip 192.168.1.90 (--to-destination 192.168.1.90)

the -A PREROUTING means that this packet get rewritten BEFORE it enters the routing stages. The paket will still pass through the Forward Chain, so make sure you allow port 80 there too. In the forward chain it will have the destination IP already rewritten and is NOT directed at your router anymore)
If you are unsure about the forward chain, add these rules to it
```
sudo iptables -A FORWARD -p tcp --dport 80 -j ACCEPT
sudo iptables -A FORWARD -p tcp --sport 80 -j ACCEPT
```
this will let any traffic pass throught your gateway that connects has something to do with port 80

the --table nat means that this rule is in the nat table (network address translation). The table can be displayed by using
```
sudo iptables -L -table nat
```

if this works, then *all* you have to do is fix the ports in these rules to match the desired services that you want to pass and that should be it.

and now i just have to pray i understood you right :)

---

### Post by Ashfire908 on 2008-03-03
Sorry I didn't get around to reading it yesterday, the cell phone setup is free on nights and weekends, so I'll try this tonight. I already knew some of this stuff, but i didn't know how the rules got processed.

Is there a way to forward all ports/connections to the server and not just single ports (or port ranges except if it's the full range of ports)?

---

### Post by SpaceTeddy on 2008-03-04
sure there is... you'd need to rewrite the forward and nat rule to not be port specific...
i.e. - they would change into this

```
sudo iptables -A PREROUTING --table nat -i ppp0 -j DNAT --to-destination 192.168.1.90
```

this will forward **anything comming in on the ppp0 device to the given ip (no matter what protocoll or port)**

and since you want to allow anything, the two FORWARD rules change from port specific to ip specific, looking like this
```
sudo iptables -i ppp0 -d 192.168.1.90 - ACCEPT
sudo iptables -o ppp0 -s 192.168.1.90 - j ACCEPT
```

hope it works :)

---

### Post by Ashfire908 on 2008-03-04
Ok so, I was finally able to write and testout a iptables setup. Here's the setup i used:
```
#!/bin/sh
# Expermental iptables setup
# Still being worked on...

echo "Setting up expermental iptables setup..."

echo "SETUP:"

## Clear any existing rules, 
iptables -P INPUT ACCEPT
iptables -F INPUT 
echo "Policy - Table: filter  Chain: INPUT    ACCEPT"
iptables -P OUTPUT ACCEPT
iptables -F OUTPUT 
echo "Policy - Table: filter  Chain: OUTPUT   ACCEPT"
iptables -P FORWARD DROP
iptables -F FORWARD 
echo "Policy - Table: filter  Chain: FORWARD  DROP"
iptables -t filter -F
iptables -t nat -F
iptables -t mangle -F
iptables -t raw -F

## Delete all User-specified chains
iptables -X

## Allow packets across the internal interface
iptables -A FORWARD -i eth0 -o eth0 -j ACCEPT
echo "filter - FORWARD: Allow packets across the internal interface  YES"

## Allow new connections going out
iptables -A FORWARD -i eth0 -o ppp0 -s 192.168.1.0/24 -j ACCEPT
echo "filter - FORWARD: Allow new connections going out              YES"

## Accept solicited tcp packets
iptables -A FORWARD -i ppp0 -o eth0 -m state --state ESTABLISHED,RELATED  -j ACCEPT
echo "filter - FORWARD: Accept solicited tcp packets                 YES"

## Allow forwarding to internal server
iptables -A FORWARD -i ppp0 -o eth0 -d 192.168.1.90 -m state --state NEW -j ACCEPT
echo "filter - FORWARD: Allow forwarding to internal server          YES"

## Forward incoming connections to server
iptables -A PREROUTING --table nat -i ppp0 -m state --state NEW -j DNAT --to-destination 192.168.1.90
echo "nat - PREROUTING: Forward incoming connections to server       YES"

## Do Masquerading
iptables -A POSTROUTING -t nat -j MASQUERADE
echo "nat - POSTROUTING: Do Masquerading                             YES"

## Enable ip forwarding
echo 1 > /proc/sys/net/ipv4/ip_forward
echo "Enable ip forwarding                                           OK"
```This is what the iptables became:

```
root@hampe-desktop-a:~# iptables -L -v
Chain INPUT (policy ACCEPT 3451 packets, 272K bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     0    --  eth0   eth0    anywhere             anywhere            
 6955  869K ACCEPT     0    --  eth0   ppp0    192.168.1.0/24       anywhere            
 6451 5334K ACCEPT     0    --  ppp0   eth0    anywhere             anywhere            state RELATED,ESTABLISHED 
  257 16882 ACCEPT     0    --  ppp0   eth0    anywhere             192.168.1.90        state NEW 

Chain OUTPUT (policy ACCEPT 2520 packets, 327K bytes)
 pkts bytes target     prot opt in     out     source               destination         
root@hampe-desktop-a:~# iptables -L -v -t nat
Chain PREROUTING (policy ACCEPT 2704 packets, 680K bytes)
 pkts bytes target     prot opt in     out     source               destination         
  256 16822 DNAT       0    --  ppp0   any     anywhere             anywhere            state NEW to:192.168.1.90 

Chain POSTROUTING (policy ACCEPT 1 packets, 164 bytes)
 pkts bytes target     prot opt in     out     source               destination         
  797 82973 MASQUERADE  0    --  any    any     anywhere             anywhere            

Chain OUTPUT (policy ACCEPT 57 packets, 3908 bytes)
 pkts bytes target     prot opt in     out     source               destination
```Ok, here's the good part: New traffic coming in the ppp0 interface (the cell phone) is corectly being sent to 192.168.1.90 (the server). Also, standard NAT is working as well. The current problem is that I cannot connect to the server from internally in the network when using the network's outside IP. Packets don't come out from the gateway (whild they should) nor do the packets get sent directly from my desktop to the server (which they shouldn't). I assume one of my rules is too restrictive. I'll mess around and see if I can find the rules or at least the section where it gets dropped.

---

### Post by SpaceTeddy on 2008-03-05
> **Ashfire908 said:**
> 
## Do Masquerading
iptables -A POSTROUTING -t nat -j MASQUERADE

you might want to change that rule to read 
```
iptables -A POSTROUTING -o ppp0 -t nat -j MASQUERADE
```
since masquerading traffic in the internal network is usually not a good choice. I would only masquerade what has to be masqueraded - so only what really goes out into the internet

you cannot access the internal server with the external ip, because only those pakets that come in from the internet (on device ppp0) get rewritten. everything from the internal network is not, so the requests stay at the gateway.
You can, of course, remove the -o ppp0 from the masquerading rule, which would rewrite any paket from any device to be redirected - but then you have absolutly no network access to your gateway anymore - it will forward any and every paket to your internal host. i would recommend against that.

I don't really see a reason to access the internal host with the external ip address, instead, i would use a dns (internally) that resolves the internal hosts different, giving back the correct internal ip (192.168.1.90). while everyone on the internet will then get your external ip, you can still use the hostname in your LAN without any troubles, since you are the only one who knows the internal one.

---

