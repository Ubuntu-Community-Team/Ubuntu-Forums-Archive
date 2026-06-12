---
title: "[SOLVED] Port Forwarding from ppp0 to eth0"
date: 2008-08-21
forum: Networking &amp; Wireless
---

### Post by MichiGreat on 2008-08-21
Hello!

I have a problem that seems to be quite easy, though I really wonder why I haven't found some helpful hint anywhere.

I have a router based on Xubuntu 8.04.1 that is connected via a DSL line to the Internet. This interface is known to Linux as ppp0. The PC also has a normal ethernet card, eth0. On the computer, using VMware Server, there runs a virtual PC that shares eth0 and has an fixed IP address and indeed it can communicate with the host OS, for example via Samba. Inside the virtual PC there runs a web and a mail server. All I want now is that TCP ports 25 and 80 of the ppp0 interface are forwarded to the virtual PC, so that the services inside it run as if they were connected directly to the Internet. Through Google I found this command:

iptables -t nat -A PREROUTING -i ppp0 -p tcp --dport 80 -j DNAT --to 192.168.1.2:80

According to the documentation of iptables, this sounds quite reasonable. But however, it doesn't work. When I try to access the website with

[http://84.119.xx.xxx/](http://84.119.xx.xxx/)

it doesn't work, though it works with

[http://192.168.1.2/](http://192.168.1.2/)

Any ideas?

Best regards,

Michael

---

### Post by Carroarmato0 on 2008-08-21
I'm having a very similar issue when setting up a VPN server that uses PPTP.

The VPN creates the ppp0 interface when I'm connectiong. However my internet traffic goes through eth0. When I'm connected to my VPN I can see my local network (eg. 192.168.x.x), but I've tried and tried setting up iptables to route ppp0 traffic to eth0, but with so success.

One tip I got from someone on irc was to Masquerade your traffic. Didn't really help me, but I hope it'll help you.

---

### Post by MichiGreat on 2008-08-21
> **Carroarmato0 said:**
> ...but I've tried and tried setting up iptables to route ppp0 traffic to eth0, but with so success.

One tip I got from someone on irc was to Masquerade your traffic...

Sounds like

iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE

would possibly help you. This enables to route all traffic from eth0 via ppp0 to the Internet. Is that what you want? However, this already works on my machine. But the counterwise direction does not work (routing traffic from Internet into LAN).

---

### Post by SpaceTeddy on 2008-08-21
Your iptables command is correct from what i can see. There must be another problem. Has your VM a default gateway set and can it access the internet ? My guess is that is misses some basic routing... i think... 

hope it helps :)

---

### Post by MichiGreat on 2008-08-23
> **SpaceTeddy said:**
> Your iptables command is correct from what i can see. There must be another problem. Has your VM a default gateway set and can it access the internet ? My guess is that is misses some basic routing... i think... 

hope it helps :)
This is definitely not the case. As I wrote in my posting above, the VM can be reached from the LAN and the VM itself can reach other computers in the LAN as well as in the Internet. What I found out so far is that at boot time runs a script "ufw". I already removed it, but "iptables -t filter -n -L" still yields a long list of entries, though IMO it shouldn't do that.

---

### Post by SpaceTeddy on 2008-08-24
mhm... ok. Forwarding should work with only one rule set in the nat table. AS far as i know, at least. So lets clear out all those rules in all tables manually and make sure that we only have loaded what we need. Also, for starters we are allowing anything to pass in any direction.

```
sudo iptabes -F --table mangle
sudo iptables -F --table nat
sudo iptabkes -F --table filter
sudo iptables FORWARD ACCEPT
sudo iptables -t nat -A PREROUTING -i ppp0 -p tcp --dport 80 -j DNAT --to-destination 192.168.1.2

```

maybe that helps...

---

### Post by MichiGreat on 2008-08-28
> **SpaceTeddy said:**
> 
```
sudo iptabes -F --table mangle
sudo iptables -F --table nat
sudo iptabkes -F --table filter
sudo iptables FORWARD ACCEPT
sudo iptables -t nat -A PREROUTING -i ppp0 -p tcp --dport 80 -j DNAT --to-destination 192.168.1.2

```

maybe that helps...

```

sudo iptables -F --table mangle
sudo iptables -F --table nat
sudo iptables -F --table filter
sudo iptables FORWARD ACCEPT
sudo iptables -t nat -A PREROUTING -i ppp0 -p tcp --dport 80 -j DNAT --to-destination 192.168.1.2

```
The 4th command does not work! If I execute the rest of it, my Internet connection does not work any more and Firefox freezes.

I guess there's no way of doing port forwarding with Ubuntu. :-/

Best regards,

Michael

---

### Post by SpaceTeddy on 2008-08-28
oh believe me, that can be done (i've done it more often than i can count on servers and routers all running ubuntu)... As for the fourth command - that one sets your iptables FORWARD chain to ACCEPT - what means it should let any and every packet pass through the machine (assuming that ip_forwarding is on and the routing i correct)... 

sadly, i have no more ideas on what to do...

[EDIT]

just saw.. the fourth command should be
> sudo iptables -P FORWARD ACCEPT

---

### Post by MichiGreat on 2008-08-28
> **SpaceTeddy said:**
> oh believe me, that can be done (i've done it more often than i can count on servers and routers all running ubuntu)... 
Which versions of Ubuntu is running on these machines? May be it is related to 8.04.
> **SpaceTeddy said:**
> As for the fourth command - that one sets your iptables FORWARD chain to ACCEPT - what means it should let any and every packet pass through the machine (assuming that ip_forwarding is on and the routing i correct)... 

sadly, i have no more ideas on what to do...

[EDIT]

just saw.. the fourth command should be

Alright, did that too. It doesn't help. Now I tried all that stuff in a Debian 4.0 box. When started up, this box has "clean" IP tables. I tried
/sbin/iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j DNAT --to-destination 192.168.1.2
to forward port 80 of this machine to the destination machine. I also tried adding ":80" at the end of the line. Also, I executed
iptables -P FORWARD ACCEPT
It all did not help. When I type
[http://192.168.1.125/](http://192.168.1.125/)
I get a timeout in Firefox.
I really would like to know what makes that all not working on my machines but working on yours. On a machine with port forwarding, what does
iptables -t nat -n --list
iptables -t filter -n --list
yield there? Can you post that, please? May be it helps me to analyze that problem.

---

### Post by SpaceTeddy on 2008-08-28
Here is full listing of one of my servers iptables ready to import via iptables-restore (ppp0 is the external device, eth0 is the internal network card with the clients attached).
Please note with this config that the server itself is barely allowed to do anything - it can only download updates, handle dns queries and issue dhcp-leases to clients. 
> 
server:/# iptables-save
# Generated by iptables-save v1.3.6 on Thu Aug 28 23:03:48 2008
*filter
:INPUT DROP [10201:3122931]
:FORWARD DROP [344:21975]
:OUTPUT DROP [8:466]
:drop-and-log-it - [0:0]
-A INPUT -m state --state ESTABLISHED -j ACCEPT 
-A INPUT -i lo -j ACCEPT 
-A INPUT -p icmp -j ACCEPT 
-A INPUT -p tcp -m tcp -m multiport --dports 22,80,443 -m state --state NEW -j ACCEPT 
-A INPUT -i eth0 -j ACCEPT 
-A INPUT -i ppp0 -p udp -m udp --sport 53 -j ACCEPT 
-A INPUT -p udp -m udp -m multiport --dports 123,1194 -j ACCEPT 
-A INPUT -p tcp -m tcp --dport 15000:15002 -j ACCEPT 
-A INPUT -p udp -m udp --dport 15000:15002 -j ACCEPT 
-A INPUT -i tun+ -j ACCEPT 
-A FORWARD -o ppp0 -p tcp -m tcp --tcp-flags SYN,RST SYN -m tcpmss --mss 1400:1536 -j TCPMSS --clamp-mss-to-pmtu 
-A FORWARD -m state --state RELATED,ESTABLISHED -j ACCEPT 
-A FORWARD -p icmp -j ACCEPT 
-A FORWARD -i eth0 -o ppp0 -m state --state NEW -j ACCEPT 
-A FORWARD -i tun0 -o eth0 -j ACCEPT 
-A FORWARD -i eth0 -o tun0 -j ACCEPT 
-A FORWARD -i tun2 -o eth0 -j ACCEPT 
-A FORWARD -i eth0 -o tun2 -j ACCEPT 
-A OUTPUT -m state --state ESTABLISHED -j ACCEPT 
-A OUTPUT -o lo -j ACCEPT 
-A OUTPUT -o eth0 -j ACCEPT 
-A OUTPUT -p icmp -j ACCEPT 
-A OUTPUT -p tcp -m tcp -m multiport --dports 22,80,443,8245 -m state --state NEW -j ACCEPT 
-A OUTPUT -o ppp0 -p udp -m udp --dport 53 -j ACCEPT 
-A OUTPUT -p udp -m udp -m multiport --sports 123,1194 -j ACCEPT 
-A OUTPUT -p tcp -m tcp --sport 15000:15002 -j ACCEPT 
-A OUTPUT -p udp -m udp --sport 15000:15002 -j ACCEPT 
-A OUTPUT -o tun+ -j ACCEPT 
-A drop-and-log-it -j LOG --log-level 6 
COMMIT
# Completed on Thu Aug 28 23:03:49 2008
# Generated by iptables-save v1.3.6 on Thu Aug 28 23:03:49 2008
*nat
:PREROUTING ACCEPT [126515:10549655]
:POSTROUTING ACCEPT [11051:1963551]
:OUTPUT ACCEPT [19003:2550211]
-A POSTROUTING -o ppp0 -j MASQUERADE 
COMMIT
# Completed on Thu Aug 28 23:03:49 2008
# Generated by iptables-save v1.3.6 on Thu Aug 28 23:03:49 2008
*mangle
:PREROUTING ACCEPT [27703480:10209207437]
:INPUT ACCEPT [18214624:2328928628]
:FORWARD ACCEPT [9488538:7880239347]
:OUTPUT ACCEPT [31179340:41715498186]
:POSTROUTING ACCEPT [40679255:49598518233]
COMMIT
# Completed on Thu Aug 28 23:03:49 2008


here is the output from ip_forwarding:
> server:/# sysctl net.ipv4.ip_forward
net.ipv4.ip_forward = 1


and here is the routing table :
> route -n
Kernel IP Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
**217.0.116.231   0.0.0.0         255.255.255.255 UH    0      0        0 ppp0**
10.8.16.2       0.0.0.0         255.255.255.255 UH    0      0        0 tun1
10.0.0.1        0.0.0.0         255.255.255.255 UH    0      0        0 tun0
192.168.4.0     10.0.0.1        255.255.255.0   UG    0      0        0 tun0
10.0.1.0        10.0.0.1        255.255.255.0   UG    0      0        0 tun0
192.168.1.0     10.0.0.1        255.255.255.0   UG    0      0        0 tun0
10.8.16.0       10.8.16.2       255.255.255.0   UG    0      0        0 tun1
192.168.0.0     10.0.0.1        255.255.255.0   UG    0      0        0 tun0
**192.168.110.0   0.0.0.0         255.255.255.0   U     0      0        0 eth1**
192.168.12.0    10.0.0.1        255.255.255.0   UG    0      0        0 tun0
192.168.11.0    10.0.0.1        255.255.255.0   UG    0      0        0 tun0
**192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0**
**0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0**

The bold lines are the imporant ones - the rest is only static vpn connections to span a private network over the internet. 
These are all the settings that are required on a computer to turn into a router. Optionally, you will need a dns server as well as a dhcp server to handle the clients... but in general, if you supply an ip-address to a client and hand it this machine as it's gateway (as well as supplying a working dns server) it should work just fine... 

i am more confused than ever about this :)


PS: i already have my full iptables configuration up there, but since you specifically asked for some output, i will supply it (again):

> server:/# iptables -t nat -n --list
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         
MASQUERADE  0    --  0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
server:/# iptables -t filter -n --list
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           state ESTABLISHED 
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp multiport dports 22,80,443 state NEW 
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp spt:53 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp multiport dports 123,1194 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpts:15000:15002 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpts:15000:15002 
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           

Chain FORWARD (policy DROP)
target     prot opt source               destination         
TCPMSS     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x06/0x02 tcpmss match 1400:1536 TCPMSS clamp to PMTU 
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           state NEW 
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           state ESTABLISHED 
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp multiport dports 22,80,443,8245 state NEW 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:53 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp multiport sports 123,1194 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:15000:15002 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp spts:15000:15002 
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           

Chain drop-and-log-it (0 references)
target     prot opt source               destination         
LOG        0    --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 


what you cannot see in this output is that i filter a lot on the incoming and outgoing interfaces of a packet... but you can find each line in the iptables-save command up the top and see the appropriate interfaces being used there. 

hope it helps :)

---

### Post by MichiGreat on 2008-08-29
> **SpaceTeddy said:**
> snipped
Hi!
Thanks a lot for all that stuff! Finally, I tried the following commands:
```

iptables -t filter -F
iptables -t filter -A INPUT -m state --state ESTABLISHED -j ACCEPT 
iptables -t filter -A INPUT -i lo -j ACCEPT 
iptables -t filter -A INPUT -p icmp -j ACCEPT 
iptables -t filter -A INPUT -p tcp -m tcp -m multiport --dports 25,80 -m state --state NEW -j ACCEPT
iptables -t filter -A INPUT -i eth0 -j ACCEPT 
iptables -t filter -A INPUT -i ppp0 -p udp -m udp --sport 53 -j ACCEPT 
iptables -t filter -A INPUT -p tcp -m tcp --dport 80 -j ACCEPT
iptables -t filter -A FORWARD -o ppp0 -p tcp -m tcp --tcp-flags SYN,RST SYN -m tcpmss --mss 1400:1536 -j TCPMSS --clamp-mss-to-pmtu 
iptables -t filter -A FORWARD -m state --state RELATED,ESTABLISHED -j ACCEPT 
iptables -t filter -A FORWARD -p icmp -j ACCEPT 
iptables -t filter -A FORWARD -i eth0 -o ppp0 -m state --state NEW -j ACCEPT 
iptables -t filter -A OUTPUT -m state --state ESTABLISHED -j ACCEPT 
iptables -t filter -A OUTPUT -o lo -j ACCEPT 
iptables -t filter -A OUTPUT -o eth0 -j ACCEPT 
iptables -t filter -A OUTPUT -p icmp -j ACCEPT 
iptables -t filter -A OUTPUT -p tcp -m tcp -m multiport --dports 25,80 -m state --state NEW -j ACCEPT
iptables -P FORWARD ACCEPT 
iptables -t nat -A PREROUTING -i ppp0 -p tcp --dport 80 -j DNAT --to-destination 192.168.1.2

```
And voila... I though I'd never see this, but from a machine in the local network that uses an outside proxy from Germany, the port forwarding from port 80 of ppp0 to 192.168.1.2 works! But then, my Internet connection on the router itself doesn't work anymore. :-( I will try to fix this and come again and report what must be done to be successful.

---

### Post by SpaceTeddy on 2008-08-29
you haven't allowed the machine itself to do dns lookups - or rather to send packets to udp/tcp port 53. That's why the machine itself cannot do anything.

BTW - the line 
> iptables -P FORWARD ACCEPT
renders all other lines that start with iptables -A FORWARD useless, and packets that do not match any rule there will be let through anyway. Just thought i'd point it out :)

---

### Post by MichiGreat on 2008-08-29
> **SpaceTeddy said:**
> you haven't allowed the machine itself to do dns lookups - or rather to send packets to udp/tcp port 53. That's why the machine itself cannot do anything.

BTW - the line 

renders all other lines that start with iptables -A FORWARD useless, and packets that do not match any rule there will be let through anyway. Just thought i'd point it out :)
So, now I have it all:
```

#!/bin/sh
iptables -t filter -F
iptables -t filter -A INPUT -m state --state ESTABLISHED -j ACCEPT 
iptables -t filter -A INPUT -p icmp -j ACCEPT 
iptables -t filter -A INPUT -p tcp -m tcp -m multiport --dports 25,80,110 -m state --state NEW -j ACCEPT
iptables -t filter -A INPUT -p tcp -m tcp --dport 25 -j ACCEPT
iptables -t filter -A INPUT -p tcp -m tcp --dport 80 -j ACCEPT
iptables -t filter -A INPUT -p tcp -m tcp --dport 110 -j ACCEPT
iptables -t filter -A INPUT -p tcp -i eth0 -j ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
iptables -t nat -A PREROUTING -i ppp0 -p tcp --dport 25 -j DNAT --to-destination 192.168.1.2
iptables -t nat -A PREROUTING -i ppp0 -p tcp --dport 80 -j DNAT --to-destination 192.168.1.2
iptables -t nat -A PREROUTING -i ppp0 -p tcp --dport 110 -j DNAT --to-destination 192.168.1.2

```
It successfully forwards ports 25, 80, and 110 to the desired machine and everything else works too. :-) I am quite happy now.
Thank you very much for your help! Once you are in Graz, I will invite you for a beer! :-)

---

### Post by MichiGreat on 2008-10-06
There was still one problem I wasn't aware when marking this thread SOLVED: When I typed in the address bar of Firefox, it freezed for about 3 minutes, so Firefox was unusable for me. But even that I could solve:
```

iptables -t filter -A INPUT -p tcp -i lo -j ACCEPT

```
I really don't understand why Firefox relies upon connections to the loopback interface, but however, now really everything works.

---

