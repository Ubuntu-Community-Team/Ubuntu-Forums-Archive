---
title: "iptables help needed"
date: 2008-02-17
forum: Networking &amp; Wireless
---

### Post by komputes on 2008-02-17
Fellow Linux users,
I am trying to understand iptables and have been spending the last 3 days looking over documentation, and yet I am not sure if I am doing this correctly. Can someone please validate my commands and comment on what I may be doing wrong. I'm pretty sure I have to open up some other things to get this working, perhaps allow loopback interface, or specify output and input, perhaps even allow forwarding, flush other tables or setup NAT, Help is appreciated!

250 Machines--------->[Gateway Running iptables firewall]-------------->(The Interwebs)

Requirements of the firewall:

1) Block all net traffic (don't worry since iptables works top down, we will be piercing this rule with holes)

```
# iptables -F #Flushes Current Table Rules
# iptables -P INPUT DROP 
#NEW POLICY: Filters all packets destined to the firewall.

# iptables -P OUTPUT DROP 
#NEW POLICY: Filters all packets originating from the firewall

# iptables -P FORWARD DROP 
#NEW POLICY: Filters all packets to servers accessible by another NIC on the firewall.
```


2) Allow machines behind the firewall in the IP range of 192.168.1.0/24 to connect to mydomain.com's host address only. The host address is 13.37.80.08 and the protocol is https.

```
iptables -A OUTPUT -p https -s 192.168.1.0/24 -d 13.37.80.08 -j ACCEPT 
#APPEND: add chain link to the OUTPUT chain. Allow all traffic from 192.168.1.0-255 on https protocol to go out to 13.37.80.08.
```


3) Allow machine 192.168.1.100 to have unrestricted access to The Interwebs

```
iptables -A OUTPUT -p ALL -s 192.168.1.100 -j ACCEPT 
#APPEND: add chain link to the OUTPUT chain. Allow all traffic from 192.168.1.100 on all protocols.
```

---

### Post by psyburn on 2008-02-17
Note: I will try to be clear but forgive my shortcomings...
Mind you I started out using Webmin to configure iptables to get the knack of valid rules

First off I don't recommend DROP for OUTPUT till you know exactly what you need in and out

Not bad but you'll need to go back over the page for iptables to find the valid options for each tag
```
man iptables
```
--OR--
[http://linux.die.net/man/8/iptables]("http://linux.die.net/man/8/iptables")

Your rules will both need to be written as such:
```
iptables -A FORWARD -s 192.168.1.0/24 -d 13.37.80.08 -p tcp -m tcp --sport 1024:65534 --dport 443 -j ACCEPT
```
Also you'll need a return line (requesting doesn't do any good unless you can hear what the reply is)
```
iptables -A FORWARD -s 13.37.80.08 -d 192.168.1.0/24 -m state --state ESTABLISHED,RELATED -j ACCEPT
```

And for that last line (unrestricted access for 192.168.1.100)
```
iptables -A FORWARD -s 192.168.1.100 -j ACCEPT
iptables -A FORWARD -d 192.168.1.100  -m state --state ESTABLISHED,RELATED -j ACCEPT
```

Here are some rules to allow basic interaction with other clients (presuming this gateway is not 192.168.1.100)
Slap it all together:
```

#!/bin/bash
echo "Flushing old rules"
iptables -F
iptables -t nat -F

echo "Setting default rules"
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT ACCEPT
#
# Input below here
#
echo "Setting allowed inputs"
# Accept traffic from internal interfaces
# Allow loopback interface
iptables -A INPUT -i lo -j ACCEPT
# Accept traffic with the ACK flag set
iptables -A INPUT -p tcp -m tcp --tcp-flags ACK ACK -j ACCEPT
# Allow incoming data that is part of a connection we established
iptables -A INPUT -m state --state ESTABLISHED -j ACCEPT
# Allow data that is related to existing connections
iptables -A INPUT -m state --state RELATED -j ACCEPT
# Accept responses to DNS queries (for WAN
iptables -A INPUT -p udp -m udp --dport 1024:65535 --sport 53 -j ACCEPT
# Accept responses to our pings
iptables -A INPUT -p icmp -m icmp --icmp-type echo-reply -j ACCEPT
# Accept notifications of unreachable hosts
iptables -A INPUT -p icmp -m icmp --icmp-type destination-unreachable -j ACCEPT
# Accept notifications to reduce sending speed
iptables -A INPUT -p icmp -m icmp --icmp-type source-quench -j ACCEPT
# Accept notifications of lost packets
iptables -A INPUT -p icmp -m icmp --icmp-type time-exceeded -j ACCEPT
# Accept notifications of protocol problems
iptables -A INPUT -p icmp -m icmp --icmp-type parameter-problem -j ACCEPT
#
# End INPUT section
#
# Here are our rules
#
# Allow LAN to talk to https server
iptables -A FORWARD -s 192.168.1.0/24 -d 13.37.80.08 -p tcp -m tcp --sport 1024:65534 --dport 443 -j ACCEPT
iptables -A FORWARD -s 13.37.80.08 -d 192.168.1.0/24 -m state --state ESTABLISHED,RELATED -j ACCEPT
# Allow unrestricted access for 192.168.1.100
iptables -A FORWARD -s 192.168.1.100 -j ACCEPT
iptables -A FORWARD -d 192.168.1.100  -m state --state ESTABLISHED,RELATED -j ACCEPT
#
# hide computers behind the firewall (nat table rule)
# change **eth1** to your internet side interface
iptables -t nat -A POSTROUTING -o **eth1** -j MASQUERADE

```

The MASQURADE rule is needed so all the others may connect through
Mind you there is kernel forwarding that needs to be enabled as well

Disclaimer: This is the best I can do without mac-filtering or interface (i.e. eth0, wlan0, etc...) options, otherwise I tend to be a bit more specific...

Mind you this will cut off all access (except for 192.168.1.100) to the outside world so I presume 192.168.1.100 is a proxy for all the rest

---

### Post by komputes on 2008-02-17
psyburn, thank you very much for your allowed input rules. I've added some notes to them and I also have some questions for you. 

1) Don't I need a policy stating that I want to block all network traffic before I start putting in ACCEPT statements?
 
2) I don't quite understand the following source port statements: --sport 1024:65534 and --dport 1024:65535. Why this range and why is one 65535 while the other one is 65534? 

3) Is the following line necessary, since this will already on a gateway router running dd-wrt: iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE (I'm not sure masquerading is what I'm trying to do)


```
#!/bin/bash

#Variables - Set these variables to your particular needs
ALLOW_SERVER="13.37.80.08"
ADMIN_CONSOLE="192.168.1.100"
PC_CLUSTER="192.168.1.0/24"

echo "Flushing old rules"
iptables -F
iptables -t nat -F

echo "Setting default rules"
iptables -P INPUT DROP		#NEW POLICY: Filters all packets destined to the firewall
iptables -P FORWARD DROP	#NEW POLICY: Filters all packets to servers accessible by another NIC on the firewall
iptables -P OUTPUT ACCEPT	#NEW POLICY: Filters all packets originating from the firewall
#
# Input below here
#
echo "Setting allowed inputs"
# Accept traffic from internal interfaces
# Allow loopback interface
iptables -A INPUT -i lo -j ACCEPT
# Accept traffic with the ACK flag set
iptables -A INPUT -p tcp -m tcp --tcp-flags ACK ACK -j ACCEPT
# Allow incoming data that is part of a connection we established
iptables -A INPUT -m state --state ESTABLISHED -j ACCEPT
# Allow data that is related to existing connections
iptables -A INPUT -m state --state RELATED -j ACCEPT
# Accept responses to DNS queries (for WAN
iptables -A INPUT -p udp -m udp --dport 1024:65535 --sport 53 -j ACCEPT
# Accept responses to our pings
iptables -A INPUT -p icmp -m icmp --icmp-type echo-reply -j ACCEPT
# Accept notifications of unreachable hosts
iptables -A INPUT -p icmp -m icmp --icmp-type destination-unreachable -j ACCEPT
# Accept notifications to reduce sending speed
iptables -A INPUT -p icmp -m icmp --icmp-type source-quench -j ACCEPT
# Accept notifications of lost packets
iptables -A INPUT -p icmp -m icmp --icmp-type time-exceeded -j ACCEPT
# Accept notifications of protocol problems
iptables -A INPUT -p icmp -m icmp --icmp-type parameter-problem -j ACCEPT
#
# End INPUT section
#
# Here are our rules
#
# Allow LAN to talk to https server
iptables -A FORWARD -s $PC_CLUSTER -d $ALLOW_SERVER -p tcp -m tcp --sport 1024:65534 --dport 443 -j ACCEPT
iptables -A FORWARD -s $ALLOW_SERVER -d $PC_CLUSTER -m state --state ESTABLISHED,RELATED -j ACCEPT
# Allow unrestricted access for $ADMIN_CONSOLE
iptables -A FORWARD -s $ADMIN_CONSOLE -j ACCEPT
iptables -A FORWARD -d $ADMIN_CONSOLE  -m state --state ESTABLISHED,RELATED -j ACCEPT
#
# hide computers behind the firewall (nat table rule)
# change eth1 to your internet side interface
iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE

```

---

### Post by psyburn on 2008-02-18
To be clear I've never used dd-wrt or anything of that kind.
But thanks for clearing up that your using a dd-wrt router and not a computer with 2 NIC's



1) The policy is what happens if a packet does not meet any rule in the chain

2) those options ("--sport 1024:65534" and "--dport 1024:65535" specifically) can be omitted in this case. They were supposed to be the same number. Alas I've never been corrected for using 65535 instead of 65534 since computers start counting at 0.

EDIT: I'm tired so forgive me. 1024 -> 65534? are non-reserved ports. Computer ports max out at 65535 (start the count at 0 instead of 1). The first 1024 (0-1023) are reserved officially for certain services.
DNS (UDP port 53) and DHCP (UDP port 67[server] and 68[client]) as well as SSH (TCP port 22) and HTTP (TCP port 80) are all common sevices which use ports in this reserved space. Even more common is the use of UDP ports 137-139 for Windows Networking. Now any client these days will have nothing that will need to reach the internet on any of these lower 1024 ports. So any requests to Leave the LAN space should be denied. Adding to this is the fact that a client making a request will open a unused port "randomly" from this pool of ports spanning 1024-65534.

My use of 65535 in iptables has never given me an error so I've haven't been scolded enough to remember the count stopping at 65534

3) As far as I know it is. Your going to be doing a NAT with this so that rule is required. You can try it without it but I don't recommend it.

INPUT and OUTPUT chains are for that local "device" while the FORWARD chain is for passing packets through. To warn you, if you don't allow an admin port (22 for ssh, 80 for HTTP, etc...) on the local side on INPUT **you WILL be LOCKED OUT** till a reboot or hard reset....* I DON"T KNOW* what will let you back in...

EDIT: I went to dd-wrt wiki and saw that headache of a page on[ iptables]("http://www.dd-wrt.com/wiki/index.php/Iptables_command")
Good news is it tells us what the interface names are.
```
**Interfaces**
When using the -i or -o to define the physical interfaces, remember that by default:
vlan0 is the 4 LAN ports
vlan1 is the WAN port
eth1 is the WIFI
br0 is a bridge connecting the 4 LAN and the WIFI together
```

So assuming your using ssh to admin, our script should now look something like this:
```

#!/bin/bash

#Variables - Set these variables to your particular needs
ALLOW_SERVER=13.37.80.08
ADMIN_CONSOLE=192.168.1.100
PC_CLUSTER=192.168.1.0/24

echo "Flushing old rules"
iptables -F
iptables -t nat -F

echo "Setting default rules"
iptables -P INPUT DROP		#NEW POLICY: Filters all packets destined to the firewall
iptables -P FORWARD DROP	#NEW POLICY: Filters all packets to servers accessible by another NIC on the firewall
iptables -P OUTPUT ACCEPT	#NEW POLICY: Filters all packets originating from the firewall
#
# Input below here
#
echo "Setting allowed inputs"
# Accept traffic from internal interfaces
# Allow loopback interface
#iptables -A INPUT -i lo -j ACCEPT
# Accept traffic with the ACK flag set
iptables -A INPUT -p tcp -m tcp --tcp-flags ACK ACK -j ACCEPT
# Allow incoming data that is part of a connection we established
iptables -A INPUT -m state --state ESTABLISHED -j ACCEPT
# Allow data that is related to existing connections
iptables -A INPUT -m state --state RELATED -j ACCEPT
# Accept responses to DNS queries (for WAN)
iptables -A INPUT -p udp -m udp --dport 1024:65535 --sport 53 -j ACCEPT
# Accept responses to our pings
iptables -A INPUT -p icmp -m icmp --icmp-type echo-reply -j ACCEPT
# Accept notifications of unreachable hosts
iptables -A INPUT -p icmp -m icmp --icmp-type destination-unreachable -j ACCEPT
# Accept notifications to reduce sending speed
iptables -A INPUT -p icmp -m icmp --icmp-type source-quench -j ACCEPT
# Accept notifications of lost packets
iptables -A INPUT -p icmp -m icmp --icmp-type time-exceeded -j ACCEPT
# Accept notifications of protocol problems
iptables -A INPUT -p icmp -m icmp --icmp-type parameter-problem -j ACCEPT
#
# End INPUT section
#
# Here are our rules
#
# Allow **ssh** access by Admin_console
iptables -A INPUT -s $ADMIN_CONSOLE -p tcp -m tcp --dport 22 -j ACCEPT
#
# Allow LAN to talk to https server
iptables -A FORWARD -s $PC_CLUSTER -d $ALLOW_SERVER -i vlan0 -o vlan1 -p tcp -m tcp --dport 443 -j ACCEPT
iptables -A FORWARD -s $ALLOW_SERVER -d $PC_CLUSTER -i vlan1 -o vlan0 -m state --state ESTABLISHED,RELATED -j ACCEPT
#
# Allow unrestricted access for $ADMIN_CONSOLE
iptables -A FORWARD -s $ADMIN_CONSOLE -i vlan0 -o vlan1 -j ACCEPT
iptables -A FORWARD -d $ADMIN_CONSOLE -i vlan1 -o vlan0  -m state --state ESTABLISHED,RELATED -j ACCEPT
#
# hide computers behind the firewall (nat table rule)
# change eth1 to your internet side interface
iptables -t nat -A POSTROUTING -o vlan1 -j MASQUERADE

```

To get to your output policy worries:
You would need to listen with a packet sniffer for a while under "normal use" and see what needs to be opened up and to see exactly what gets used.

My Ubuntu server and gateway needs a minimum of 3 rules just to get bare minimum internet usage. 
My rules for my gateway follow for a DROP policy OUTPUT chain:
```
# DHCP client calls
iptables -A OUTPUT -o eth1 -p udp -m udp --sport 68 --dport 67 -j ACCEPT
# Everything else (TCP & UDP)
iptables -A OUTPUT -o eth1 -p tcp -m tcp --sport 1024:65535 -j ACCEPT
iptables -A OUTPUT -o eth1 -p udp -m udp --sport 1024:65535 -j ACCEPT

# Allowed ICMP calls
# Accept responses to our pings
iptables -A OUTPUT -o eth1 -p icmp -m icmp --icmp-type echo-reply -j ACCEPT
# Accept notifications of unreachable hosts
iptables -A OUTPUT -o eth1 -p icmp -m icmp --icmp-type destination-unreachable -j ACCEPT
# Accept notifications to reduce sending speed
iptables -A OUTPUT -o eth1 -p icmp -m icmp --icmp-type source-quench -j ACCEPT
# Accept notifications of lost packets
iptables -A OUTPUT -o eth1 -p icmp -m icmp --icmp-type time-exceeded -j ACCEPT
# Accept notifications of protocol problems
iptables -A OUTPUT -o eth1 -p icmp -m icmp --icmp-type parameter-problem -j ACCEPT
```

---

### Post by psyburn on 2008-02-18
Sorry for the double post but I'm done for the night. I'll check back later...

Hope this helps enough to start...

---

### Post by komputes on 2008-02-18
This is fantastic, I will give it a try in a few minutes. One thing that still bothers me is that this will not necessarily block computers on 192.168.1.0/24 from sending out packets to anything other than 13.37.80.08. It only blocks the return of packets which are not from 13.37.80.08. Is there a way to give it more strict guidelines, blocking all output and only allowing in/out traffic related to 13.37.80.08, but still have the computers on the 192.168.1.0/24 LAN communicate with each other and see each other.

I have used wireshark to see what was going on in the background, and I want to block most of this. The only thing I want to allow is HTTPS to my server, but I'm sure there are some other standard rules that I need to allow standard LAN communication if I block everything.

I guess I can leave it as is and simply intert an additional line befor the $ALLOW_SERVER saying:

```
iptables -A FORWARD -s $PC_CLUSTER -i vlan0 -o vlan1 -p tcp -m tcp -j DROP
```

Which will block all outgoing tcp traffic from the cluster of computers, followed by

```

iptables -A FORWARD -s $PC_CLUSTER -d $ALLOW_SERVER -i vlan0 -o vlan1 -p tcp -m tcp --dport 443 -j ACCEPT
iptables -A FORWARD -s $ALLOW_SERVER -d $PC_CLUSTER -i vlan1 -o vlan0 -m state --state ESTABLISHED,RELATED -j ACCEPT
```

Which puts holes in the previous rules by allowing https traffic To and FROM $ALLOW_SERVER

---

### Post by psyburn on 2008-02-18
Look IPtables works like atop down sifting rack
The policy is the absolute last rule in the chain.
 If a packet matches nothing in the chain, then it will be DROP'd or ACCEPT'd according to policy.
If you put a global DROP or REJECT before the ALLOW then **everything will match** it and be dropped

```
iptables -A FORWARD -s $PC_CLUSTER -i vlan0 -o vlan1 -p tcp -m tcp -j DROP # All of your clusters HTTPS requests will match this rule so they will be DROPPED as well and never make it to the next rule.
iptables -A FORWARD -s $PC_CLUSTER -d $ALLOW_SERVER -i vlan0 -o vlan1 -p tcp -m tcp --dport 443 -j ACCEPT
iptables -A FORWARD -s $ALLOW_SERVER -d $PC_CLUSTER -i vlan1 -o vlan0 -m state --state ESTABLISHED,RELATED -j ACCEPT

```
--VS.--
```

iptables -A FORWARD -s $PC_CLUSTER -d $ALLOW_SERVER -i vlan0 -o vlan1 -p tcp -m tcp --dport 443 -j ACCEPT # requests to your HTTPS server will be ACCEPT'd and FORWARD'd
iptables -A FORWARD -s $ALLOW_SERVER -d $PC_CLUSTER -i vlan1 -o vlan0 -p tcp -m tcp --sport 443 -m state --state ESTABLISHED,RELATED -j ACCEPT # If a client has made a request FORWARD the reply form the server
iptables -A FORWARD -s $PC_CLUSTER -i vlan0 -o vlan1 -j REJECT # Everything (notice I took out the -p tcp) else requesting forwarding REJECT it since it's on the LAN side

```

Your admin_console will need to go before you cluster rules or else it will be subject to the same scrutiny

Final rules: [short version - No Input, policy, flush stated, All implied to be prepended before this]
```

# Allow unrestricted access for $ADMIN_CONSOLE
iptables -A FORWARD -s $ADMIN_CONSOLE -i vlan0 -o vlan1 -j ACCEPT
iptables -A FORWARD -d $ADMIN_CONSOLE -i vlan1 -o vlan0  -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -s $PC_CLUSTER -d $ALLOW_SERVER -i vlan0 -o vlan1 -p tcp -m tcp --dport 443 -j ACCEPT # requests to your HTTPS server will be ACCEPT'd and FORWARD'd
iptables -A FORWARD -s $ALLOW_SERVER -d $PC_CLUSTER -i vlan1 -o vlan0 -p tcp -m tcp --sport 443 -m state --state ESTABLISHED,RELATED -j ACCEPT # If a client has made a request FORWARD the reply form the server
iptables -A FORWARD -s $PC_CLUSTER -i vlan0 -o vlan1 -j REJECT # Everything (notice I took out the -p tcp) else requesting forwarding REJECT it since it's on the LAN side

```

On a LAN I prefer REJECT since it saves time and bandwidth (router says NO versus ignoring the client and the client asking 40+ times again(I kid you not!))

---

### Post by komputes on 2008-02-18
Thanks for your patience psyburn, I'm actually getting more used to iptables, but there are still basic network functions that I must learn to allow in the ALLOWED INPUT rule list, so please bare with me. One command bugged out die to impropper syntax when I tried to run the script:

My console is not liking this line

```
iptables -A INPUT -p tcp -m tcp --tcp-flags ACK ACK -j ACCEPT
```

it seems to be the "-m tcp" that it doesn't like, can you review/explain if you know what it going on?

P.S. If you reply with the correct order and the correction to this line can you put it all in CODE box in the proper order and I will give it a try.

Thanks again!

---

### Post by psyburn on 2008-02-18
Huh that line is quite valid and it's not even mine...
I've used it since Webmin considered it a necessary rule for a "Block all incoming on interface" setup.

Try checking the spacing to make sure there is only one space between everything..

**-p** is protocol
to block or allow a certain protocol you use 
```
[iptables -A XXXXX -p tcp -j REJECT]
```
**-m** is module options 
```
[iptables -A XXXXX -p tcp -m tcp --dport 80 -j REJECT]
```
the above would REJECT all traffic on port 80 (HTTP mostly)

All I know is that the line (iptables -A INPUT -p tcp -m tcp --tcp-flags ACK ACK -j ACCEPT) is valid... unless you care to post the error and let me see if I can make sense of it. Please post the error.

Oh well here is the (mostly working) script in its entirety:
```
#!/bin/bash

#Variables - Set these variables to your particular needs
ALLOW_SERVER=13.37.80.08
ADMIN_CONSOLE=192.168.1.100
PC_CLUSTER=192.168.1.0/24

echo "Flushing old rules"
iptables -F
iptables -t nat -F

echo "Setting default rules"
iptables -P INPUT DROP		#NEW POLICY: Filters all packets destined to the firewall
iptables -P FORWARD DROP	#NEW POLICY: Filters all packets to servers accessible by another NIC on the firewall
iptables -P OUTPUT ACCEPT	#NEW POLICY: Filters all packets originating from the firewall
#
# Input below here
#
echo "Setting allowed inputs"
# Accept traffic from internal interfaces
# Allow loopback interface
#iptables -A INPUT -i lo -j ACCEPT
# Accept traffic with the ACK flag set
iptables -A INPUT -p tcp -m tcp --tcp-flags ACK ACK -j ACCEPT
# Allow incoming data that is part of a connection we established
iptables -A INPUT -m state --state ESTABLISHED -j ACCEPT
# Allow data that is related to existing connections
iptables -A INPUT -m state --state RELATED -j ACCEPT
# Accept responses to DNS queries (for WAN)
iptables -A INPUT -p udp -m udp --dport 1024:65535 --sport 53 -j ACCEPT
# Accept responses to our pings
iptables -A INPUT -p icmp -m icmp --icmp-type echo-reply -j ACCEPT
# Accept notifications of unreachable hosts
iptables -A INPUT -p icmp -m icmp --icmp-type destination-unreachable -j ACCEPT
# Accept notifications to reduce sending speed
iptables -A INPUT -p icmp -m icmp --icmp-type source-quench -j ACCEPT
# Accept notifications of lost packets
iptables -A INPUT -p icmp -m icmp --icmp-type time-exceeded -j ACCEPT
# Accept notifications of protocol problems
iptables -A INPUT -p icmp -m icmp --icmp-type parameter-problem -j ACCEPT
#
# End INPUT section
#
# Here are our rules
#
echo "Allowing ssh access on LAN side"
# Allow ssh access by Admin_console
# Lets allow it from anywhere we trust
# Hardwired LAN
iptables -A INPUT -s $ADMIN_CONSOLE -i vlan0 -p tcp -m tcp --dport 22 -j ACCEPT
# Wireless LAN
iptables -A INPUT -s $ADMIN_CONSOLE -i eth1 -p tcp -m tcp --dport 22 -j ACCEPT
#
# FORWARD rules below here
#
# Allow unrestricted access for $ADMIN_CONSOLE
# Allow outgoing requests to the internet
iptables -A FORWARD -s $ADMIN_CONSOLE -i vlan0 -o vlan1 -j ACCEPT
# Allow incoming replies from the internet if the admin_console has made a request
iptables -A FORWARD -d $ADMIN_CONSOLE -i vlan1 -o vlan0  -m state --state ESTABLISHED,RELATED -j ACCEPT
#
# Allow LAN to talk to https server
# Allow outgoing requests to https server
iptables -A FORWARD -s $PC_CLUSTER -d $ALLOW_SERVER -i vlan0 -o vlan1 -p tcp -m tcp --dport 443 -j ACCEPT
# Allow incoming replies from https server if a PC has made a request
iptables -A FORWARD -s $ALLOW_SERVER -d $PC_CLUSTER -i vlan1 -o vlan0 -m state --state ESTABLISHED,RELATED -j ACCEPT
#
# REJECT any requests by the pc_cluster to talk to the internet
iptables -A FORWARD -s $PC_CLUSTER -i vlan0 -o vlan1 -j REJECT
# Everything else requesting forwarding REJECT it since it's on the LAN side
#
# Allow Wireless to talk to wired LAN comment both of these out if you don't want wired and wireless talking to each other
iptables -A FORWARD -s $PC_CLUSTER -i eth1 -o vlan0 -j ACCEPT
iptables -A FORWARD -s $PC_CLUSTER -i vlan0 -o eth1 -j ACCEPT
#
# hide computers behind the firewall (nat table rule)
# change eth1 to your internet side interface
iptables -t nat -A POSTROUTING -o vlan1 -j MASQUERADE

```

---

### Post by psyburn on 2008-02-19
Double post, sorry.

Well komputes how did it go?

---

### Post by komputes on 2008-02-20
Well it didn't quite work out, and I don't want to brick the router, so I will try it on a computer I have which has 2 network interfaces, hopefully that will work out for me.

Currently reading:

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)
[http://ornellas.apanela.com/dokuwiki/pub:firewall_and_adv_routing](http://ornellas.apanela.com/dokuwiki/pub:firewall_and_adv_routing)
[http://www.cse.msu.edu/~minutsil/iptables.html](http://www.cse.msu.edu/~minutsil/iptables.html)

---

