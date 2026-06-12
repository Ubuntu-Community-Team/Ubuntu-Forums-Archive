---
title: "iptables and logging"
date: 2013-10-15
forum: Networking &amp; Wireless
---

### Post by ant2ne on 2013-10-15
I've followed [URL="http://notepad2.blogspot.com/2012/06/enable-iptables-logging-on-ubuntu-linux.html"]these instructions here 
[/URL] and I've even added 
```
echo "Setting up logging"
iptables -A INPUT  -m limit --limit 1/s --limit-burst 7   -j LOG --log-prefix "[IPTABLES INPUT "
iptables -A OUTPUT  -m limit --limit 1/s --limit-burst 7   -j LOG --log-prefix "[IPTABLES OUTPUT "
iptables -A NAT  -m limit --limit 1/s --limit-burst 7   -j LOG --log-prefix "[IPTABLES NAT "
iptables -A PREROUTING  -m limit --limit 1/s --limit-burst 7   -j LOG --log-prefix "[IPTABLES PREROUTING "
iptables -A POSTROUTING  -m limit --limit 1/s --limit-burst 7   -j LOG --log-prefix "[IPTABLES POSTROUTING "

```In my iptables script. But All it seems to log is INPUT and OUTPUT dropped packets. Which is mostly worthless. I want to log all packets that are accepted and or natted. What would be the correct command line for this?

---

### Post by Doug S on 2013-10-15
You will have to show us those rules in the context of your overall iptables rule set. They might need to be inserted further up the various chains rule sets to be effective. I assume you want to do this just for debugging purposes, as there is the potential for a great many log entries. Watch your log file sizes carefully. Post the output for "sudo iptables -v -x -n -L" and "sudo iptables -t nat -v -x -n -L" or "sudo iptables-save -c".

---

### Post by ant2ne on 2013-10-15
I have a 70G hard drive dedicated to nothing but this firewall. If needed I will get a larger hard drive. If needed I can tweak " -m limit --limit 1/s --limit-burst 7" to keep the logs manageable, but I want to know exactly who access certain internal NATted devices or the firewall itself. I want to be able to know when, for how long, and from what IP. I'm also thinking of creating a second device to function as a bridge that does nothing but observing packets and writing them to the log. But one step at a time.

My entire script. If you see any other errors in my script feel free to point them out.
```

#!/bin/bash
######################
#
#      Configuring hardware and
#
#  settings up variables for the script
#
######################


## MTU IDK why it needs to be executed several times
## but if only executed once it only goes up a little
## bit each time.

 ifconfig eth0 mtu 1500
 ifconfig eth1 mtu 1500

echo "setting up variables"
_ethOUT=eth1
    #_ethOUT is DHCP from ISP (outgoing interface)
_ethIN=eth0
dhclient -v $_ethOUT
echo $_ethOUT

_GATEWAY=$(ifconfig $_ethOUT | grep -v inet6 | grep inet | cut -d : -f 2 | sed 's/Bcast//')
echo "The gateway inteface is $_ethOUT and its IP is $_GATEWAY"
echo "The internal interface is $_ethIN"
_Me=10.1.1.69
_FTP=10.1.1.5
_RUNUO=10.1.1.7
_RUNUO_PORT=8888
_RUNUO2=10.1.1.19
_RUNUO2_PORT=8889
_CYGNENOS=10.1.1.3
_myDNS=$_CYGNENOS
_myDHCP=$_CYGNNOS
_Win2k8Server=10.1.1.9
_OpenDNS=208.67.222.222
_Player=10.1.1.17
_Webdav=$_ethOUT
_Webserver=10.1.1.5
_Unfiltered=10.1.1.1
_Minecraft1=10.1.1.21
_Minecraft2=10.1.1.22


########################
#
# FLUSHING
#
#
########################
iptables -F INPUT
iptables -F OUTPUT
iptables -F FORWARD
iptables -t nat -F PREROUTING
iptables -t nat -F POSTROUTING


########################
#
# LOGGING
#
#
########################
echo "Setting up logging"
iptables -A INPUT  -m limit --limit 1/s --limit-burst 7   -j LOG --log-prefix "[IPTABLES INPUT "
iptables -A OUTPUT  -m limit --limit 1/s --limit-burst 7   -j LOG --log-prefix "[IPTABLES OUTPUT "
iptables -A NAT  -m limit --limit 1/s --limit-burst 7   -j LOG --log-prefix "[IPTABLES NAT "
iptables -A PREROUTING  -m limit --limit 1/s --limit-burst 7   -j LOG --log-prefix "[IPTABLES PREROUTING "
iptables -A POSTROUTING  -m limit --limit 1/s --limit-burst 7   -j LOG --log-prefix "[IPTABLES POSTROUTING "

#iptables -A INPUT -i eth1 -m limit --limit 5/m --limit-burst 7 -j LOG --log-prefix "[IPTABLES  Dropped INPUT: "
#iptables -A OUTPUT -m limit --limit 5/m --limit-burst 7 -j LOG --log-prefix "[IPTABLES  Dropped OUTPUT: "
#iptables -A NAT  -m limit --limit 5/m --limit-burst 7 -j LOG --log-prefix "[IPTABLES  Dropped NAT: "
#iptables -A PREROUTING  -m limit --limit 5/m --limit-burst 7 -j LOG --log-prefix "[IPTABLES  Dropped PREROUTING: "
#iptables -A POSTROUTING -m limit --limit 5/m --limit-burst 7 -j LOG --log-prefix "[IPTABLES  Dropped POSTROUTING: "




##########################
#
# ICMP
#
##########################
iptables -A OUTPUT -p icmp --icmp-type echo-request -j ACCEPT
iptables -A INPUT  -p icmp --icmp-type echo-reply   -j ACCEPT
iptables -A INPUT -p icmp --icmp-type echo-request -m limit --limit 1/s -i eth0 -j ACCEPT


# Work around for stupid websites blocking ICMP (just for normal surfing)
 iptables -t mangle -A FORWARD -p tcp --tcp-flags SYN,RST SYN -j TCPMSS --clamp-mss-to-pmtu
# Allow ICMP for frag notification
# --icmp-type 8 = ping
# iptables -t filter -A INPUT -p icmp -s 0/0 -d $ip_eth2 -m state --state NEW -j ACCEPT


################
#
# Masqurading
#
#################
echo "setting up masqurading"
# only need the one outgoing interface for internet access
 iptables -t nat -A POSTROUTING -o $_ethOUT -j MASQUERADE
# iptables -t nat -A POSTROUTING -o $_ethOUT -j SNAT --to $_GATEWAY

################
#
# INPUT
#   - IN TO THIS SERVER
#
###############
echo "setting up INPUT"
# default states
iptables -I INPUT 1 -i lo -j ACCEPT
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
# remote admin ssh and webmin
iptables -A INPUT -i $_ethIN -p tcp --dport ssh -j ACCEPT
iptables -A INPUT -i $_ethIN -p tcp --dport 3000 -j ACCEPT
iptables -A INPUT -i $_ethOUT -p tcp --dport 3000 -j REJECT

#iptables -N LOGGING
#iptables -A INPUT -j LOGGING
#iptables -A LOGGING -p tcp -m limit --limit 5/min -j LOG --log-prefix "Dropped TCP: " --log-level 7
#iptables -A LOGGING -p udp -m limit --limit 5/min -j LOG --log-prefix "Dropped UDP: " --log-level 7
#iptables -A LOGGING -p icmp -m limit --limit 5/min -j LOG --log-prefix "Dropped ICMP: " --log-level 7


################
#
# OUTPUT
#
################



###################
#
# FORWARD
#
##################
echo "setting up FORWARD"
iptables -A FORWARD -j ACCEPT


##################
#
# RUNUO DNAT
#
#################
echo "setting up RUNUO DNAT"
iptables -t nat -A PREROUTING -p tcp --dport $_RUNUO_PORT -j DNAT --to $_RUNUO:$_RUNUO_PORT
iptables -t nat -A POSTROUTING -s $_RUNUO -p tcp --sport $_RUNUO_PORT -j SNAT --to-source $_GATEWAY
iptables -t nat -A PREROUTING -p tcp --dport $_RUNUO2_PORT -j DNAT --to $_RUNUO2:$_RUNUO2_PORT
iptables -t nat -A POSTROUTING -s $_RUNUO2 -p tcp --sport $_RUNUO2_PORT -j SNAT --to-source $_GATEWAY

##########################
#
# RDP NATs
#
#########################
echo "setting up RDP DNAT"
iptables -t nat -A PREROUTING -i $_ethOUT -p tcp --dport 3389 -j DNAT --to $_Player:3389



######################
#
# Webserver DNAT
#
#######################
iptables -t nat -A PREROUTING -p tcp -i  $_ethOUT --dport 80 -j DNAT --to $_Webserver:80 
iptables -t nat -A PREROUTING -p tcp -i $_ethOUT  --dport 443 -j DNAT --to $_Webserver:443 



#####################
#
# OpenDNS DNAT OUTGOING
#
####################
echo "setting up OpenDNS prerouting (the trap)"
# Need to change the below line to --to $_myDNS:53 so that DNS traffic not from 
iptables -t nat -A PREROUTING  -s $_Me -p udp --dport 53 -j DNAT --to 8.8.8.8:53
iptables -t nat -A PREROUTING  -s $_Me -p tcp --dport 53 -j DNAT --to 8.8.8.8:53

iptables -t nat -A PREROUTING  -s $_RUNUO2 -p udp --dport 53 -j DNAT --to 8.8.8.8:53
iptables -t nat -A PREROUTING  -s $_RUNUO2 -p tcp --dport 53 -j DNAT --to 8.8.8.8:53

iptables -t nat -A PREROUTING  -s $_RUNUO -p udp --dport 53 -j DNAT --to 8.8.8.8:53
iptables -t nat -A PREROUTING  -s $_RUNUO2 -p tcp --dport 53 -j DNAT --to 8.8.8.8:53


iptables -t nat -A PREROUTING ! -s $_myDNS -p udp --dport 53 -j DNAT --to $_OpenDNS:53
iptables -t nat -A PREROUTING ! -s $_myDNS -p tcp --dport 53 -j DNAT --to $_OpenDNS:53


########################
#
#   Default settings end
#   of chain and  rejects
#
########################
echo "setting up defaults for end of chains"
iptables -A INPUT -i $_ethOUT -j DROP
iptables -A INPUT -i $_ethIN -j ACCEPT
iptables -A OUTPUT -j ACCEPT










########################
#
#  OTHER STUFF
#
########################
iptables -L

/etc/init.d/ntop restart

```

---

### Post by Doug S on 2013-10-15
Well, I don't know why it is not working for you. I tried your rule in my iptables rule set and it worked fine. My default logging level is 4, maybe yours is different. Try specifying the logging level.
Here is my output with a rule similar to yours:```
doug@doug-64:~/init$ [COLOR=#ff0000]sudo iptables -v -x -n -L[/COLOR]
Chain INPUT (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination
       0        0 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0
... a bunch of direct drop stuff deleted ...
[COLOR=#ff0000]      90     6762 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 1/sec burst 7 LOG flags 0 level 4 prefix "[IPTABLES INPUT "[/COLOR]
       0        0 LOG        tcp  --  eth0   *       0.0.0.0/0            0.0.0.0/0            state INVALID LOG flags 0 level 6 prefix "IINVALID:"
       0        0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcpflags:! 0x17/0x02 state NEW LOG flags 0 level 6 prefix "NEW TCP no SYN:"
```And the related area of my source script:```
#************************* debug experimenting only *******************************
# test all TCP packets. (be careful of log file sizes)
#$IPTABLES -A INPUT -i $INTIF -p tcp ! --syn -j LOG --log-prefix "ZZN:"
[COLOR=#ff0000]$IPTABLES -A INPUT  -m limit --limit 1/s --limit-burst 7   -j LOG --log-prefix "[IPTABLES INPUT "[/COLOR]
#$IPTABLES -A INPUT -i $INTIF -p tcp ! --syn -j LOG --log-prefix "ZZN:" --log-level info
#$IPTABLES -A INPUT -i $INTIF -p tcp --syn -j LOG --log-prefix "ZZS:" --log-level info
#$IPTABLES -A INPUT -p tcp ! --syn -j LOG --log-prefix "ZZN:" --log-level info
#$IPTABLES -A INPUT -p tcp --syn -j LOG --log-prefix "ZZS:" --log-level info
```

---

### Post by ant2ne on 2013-10-15
Here are those commands you asked for.

```
nt2ne@fw:/var/log$ sudo iptables -v -x -n -L
[sudo] password for ant2ne: 
Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
     274    60995 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 5/min burst 5 LOG flags 0 level 7 prefix "Dropped: "
     353    79405 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 5/min burst 5 LOG flags 0 level 7 prefix "Dropped: "
     432    92832 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 5/min burst 5 LOG flags 0 level 7 prefix "Dropped: "
     511   105025 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 5/min burst 5 LOG flags 0 level 7 prefix "Dropped: "
     590   117991 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 5/min burst 5 LOG flags 0 level 7 prefix "Dropped: "
     669   135330 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 5/min burst 5 LOG flags 0 level 7 prefix "Dropped: "
     748   150984 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 5/min burst 5 LOG flags 0 level 7 prefix "Dropped: "
     791   158641 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 5/min burst 5 LOG flags 0 level 7 prefix "Dropped: "
    7139  1793616 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
    8598  1339939 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 1/sec burst 7 LOG flags 0 level 4 prefix "[IPTABLES INPUT"
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 0
    3619   767228 ACCEPT     icmp --  eth0   *       0.0.0.0/0            0.0.0.0/0            icmptype 8 limit: avg 1/sec burst 5
   20397  1905038 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
       0        0 ACCEPT     tcp  --  eth0   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:22
    1146    68760 ACCEPT     tcp  --  eth0   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:3000
       0        0 REJECT     tcp  --  eth1   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:3000 reject-with icmp-port-unreachable
    6867  1456573 DROP       all  --  eth1   *       0.0.0.0/0            0.0.0.0/0           
    1414   146487 ACCEPT     all  --  eth0   *       0.0.0.0/0            0.0.0.0/0           

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
  638431 250326260 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
    8127  2659400 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 1/sec burst 7 LOG flags 0 level 4 prefix "[IPTABLES OUTPUT"
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 8
   32438  9601471 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain LOGGING (0 references)
    pkts      bytes target     prot opt in     out     source               destination         
      28     2108 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 5/min burst 5 LOG flags 0 level 7 prefix "Denied TCP: "
      75    23718 LOG        udp  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 5/min burst 5 LOG flags 0 level 7 prefix "Denied UDP: "
       0        0 LOG        icmp --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 5/min burst 5 LOG flags 0 level 7 prefix "Denied ICMP: "
      10      864 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 5/min burst 5 LOG flags 0 level 7 prefix "Dropped TCP: "
      42    12747 LOG        udp  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 5/min burst 5 LOG flags 0 level 7 prefix "Dropped UDP: "
       0        0 LOG        icmp --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 5/min burst 5 LOG flags 0 level 7 prefix "Dropped ICMP: "
       7      744 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 5/min burst 5 LOG flags 0 level 7 prefix "Dropped TCP: "
      25     7491 LOG        udp  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 5/min burst 5 LOG flags 0 level 7 prefix "Dropped UDP: "
       0        0 LOG        icmp --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 5/min burst 5 LOG flags 0 level 7 prefix "Dropped ICMP: "

```

&

```
ant2ne@fw:/var/log$ sudo iptables -t nat -v -x -n -L
Chain PREROUTING (policy ACCEPT 16017 packets, 2153911 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 DNAT       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:8888 to:10.1.1.7:8888
       0        0 DNAT       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:8889 to:10.1.1.19:8889
       4      196 DNAT       tcp  --  eth1   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:3389 to:10.1.1.17:3389
       1       40 DNAT       tcp  --  eth1   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:80 to:10.1.1.5:80
       0        0 DNAT       tcp  --  eth1   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:443 to:10.1.1.5:443
    1271    77038 DNAT       udp  --  *      *       10.1.1.69            0.0.0.0/0            udp dpt:53 to:8.8.8.8:53
       0        0 DNAT       tcp  --  *      *       10.1.1.69            0.0.0.0/0            tcp dpt:53 to:8.8.8.8:53
       0        0 DNAT       udp  --  *      *       10.1.1.19            0.0.0.0/0            udp dpt:53 to:8.8.8.8:53
       0        0 DNAT       tcp  --  *      *       10.1.1.19            0.0.0.0/0            tcp dpt:53 to:8.8.8.8:53
      25     1425 DNAT       udp  --  *      *       10.1.1.7             0.0.0.0/0            udp dpt:53 to:8.8.8.8:53
       0        0 DNAT       tcp  --  *      *       10.1.1.19            0.0.0.0/0            tcp dpt:53 to:8.8.8.8:53
     189    11832 DNAT       udp  --  *      *      !10.1.1.3             0.0.0.0/0            udp dpt:53 to:208.67.222.222:53
       0        0 DNAT       tcp  --  *      *      !10.1.1.3             0.0.0.0/0            tcp dpt:53 to:208.67.222.222:53

Chain INPUT (policy ACCEPT 1350 packets, 110335 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 168 packets, 13600 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 8 packets, 420 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
    6706   468900 MASQUERADE  all  --  *      eth1    0.0.0.0/0            0.0.0.0/0           
       0        0 SNAT       tcp  --  *      *       10.1.1.7             0.0.0.0/0            tcp spt:8888 to:96.35.17.165
       0        0 SNAT       tcp  --  *      *       10.1.1.19            0.0.0.0/0            tcp spt:8889 to:96.35.17.165
ant2ne@fw:/var/log$ 


```


Are you logging NAT entries. For example, if someone comes knocking on my firewall on port 80, just before the firewall sends the guest to my webserver I'd like that to be logged. If someone attempte to connect to my Windows box via RDP (port 3389) I'd like that to be logged as well.

---

### Post by Doug S on 2013-10-15
You are getting a lot of hits for your INPUT and OUTPUT chain rules, so there should be log entries. You might want to add a rule to your FORWARD chain instead of your NAT rule. Try changing this line:```
iptables -A NAT  -m limit --limit 1/s --limit-burst 7   -j LOG --log-prefix "[IPTABLES NAT "
```to this:```
iptables -A FORWARD  -m limit --limit 1/s --limit-burst 7   -j LOG --log-prefix "[IPTABLES NAT "
```and do you see any errors listed when you run your script?

Edit: By the way. This stuff seems to be hanging around from some earlier version of your script or from somewhere else:```
Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
     274    60995 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 5/min burst 5 LOG flags 0 level 7 prefix "Dropped: "
     353    79405 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 5/min burst 5 LOG flags 0 level 7 prefix "Dropped: "
     432    92832 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 5/min burst 5 LOG flags 0 level 7 prefix "Dropped: "
     511   105025 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 5/min burst 5 LOG flags 0 level 7 prefix "Dropped: "
     590   117991 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 5/min burst 5 LOG flags 0 level 7 prefix "Dropped: "
     669   135330 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 5/min burst 5 LOG flags 0 level 7 prefix "Dropped: "
     748   150984 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 5/min burst 5 LOG flags 0 level 7 prefix "Dropped: "
     791   158641 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 5/min burst 5 LOG flags 0 level 7 prefix "Dropped: "
```

---

### Post by Doug S on 2013-10-15
> **ant2ne said:**
> Are you logging NAT entries. For example, if someone comes knocking on my firewall on port 80, just before the firewall sends the guest to my webserver I'd like that to be logged. If someone attempte to connect to my Windows box via RDP (port 3389) I'd like that to be logged as well.Note: I didn't notice this part before. Yes, I log all new web site inquiries, but in my case there is no nat involved (for the web server). Here is my script fragment:```
# HTTPd - Enable the following lines if you run an EXTERNAL WWW server
#
# Ver 0.40 add logging. ESTABLISHED,RELATED path is above so eliminate it here.
#
echo Allowing EXTERNAL access to the WWW server
#$IPTABLES -A INPUT -i $EXTIF -m state --state NEW,ESTABLISHED,RELATED -p tcp -s $UNIVERSE -d $EXTIP --dport 80 -j ACCEPT
$IPTABLES -A INPUT -i $EXTIF -m state --state NEW -p tcp -s $UNIVERSE -d $EXTIP --dport 80 -j LOG --log-prefix "NEW80:" --log-level info
#$IPTABLES -A INPUT -i $EXTIF -m state --state NEW -p tcp -m limit --limit 30/minute --limit-burst 5 -s $UNIVERSE -d $EXTIP --dport 80 -j ACCEPT
$IPTABLES -A INPUT -i $EXTIF -m state --state NEW -p tcp -s $UNIVERSE -d $EXTIP --dport 80 -j ACCEPT
```

---

### Post by ant2ne on 2013-10-15
Changing that to Forward instaed of NAT changed everything. I'm now logging packets but I'm not sure what I'm seeing. I think I'm logging the wrong interface (that is I'm logging my internal connections to the outside world.) But I'm not possitive. On the right track though.

---

### Post by Doug S on 2013-10-15
> **ant2ne said:**
> Changing that to Forward instaed of NAT changed everything. I'm now logging packets but I'm not sure what I'm seeing. I think I'm logging the wrong interface (that is I'm logging my internal connections to the outside world.) But I'm not possitive. On the right track though.Yes, both directions go through the FORWARD chain. You should be able to narrow down to what you really want via -i and/or -o specifiers. For your earlier question, I temporarily forgot that I am currently forwarding external http stuff from a different port to an internal server. I wasn't logging new connections to that server via my main firewall, but I would do this:```
#
# port forward stuff. see also the prerouting area.
$IPTABLES -A FORWARD -i $EXTIF -o $INTIF -p tcp --dport 80 -d 192.168.111.112 -m state --state NEW -j LOG --log-prefix "PFNEW80:" --log-level info
$IPTABLES -A FORWARD -i $EXTIF -o $INTIF -p tcp --dport 80 -d 192.168.111.112 -m state --state NEW -j ACCEPT
```

---

### Post by ant2ne on 2013-10-15
A quick sample of the log I'm generating```
Oct 15 18:48:06 fw kernel: [616772.194765] [IPTABLES FORWARD IN=eth1 OUT=eth0 MAC=00:e0:66:6a:c5:12:00:21:a0:fa:fa:d9:08:00 SRC=74.125.142.95 DST=10.1.1.69 LEN=52 TOS=0x00 PREC=0x00 TTL=41 ID=32509 PROTO=TCP SPT=80 DPT=37432 WINDOW=975 RES=0x00 ACK FIN URGP=0 
Oct 15 18:48:07 fw kernel: [616773.178126] [IPTABLES FORWARD IN=eth1 OUT=eth0 MAC=00:e0:66:6a:c5:12:00:21:a0:fa:fa:d9:08:00 SRC=23.194.146.110 DST=10.1.1.69 LEN=79 TOS=0x00 PREC=0x00 TTL=49 ID=47481 DF PROTO=TCP SPT=443 DPT=47258 WINDOW=8312 RES=0x00 ACK PSH URGP=0 
Oct 15 18:48:10 fw kernel: [616776.093241] [IPTABLES FORWARD IN=eth1 OUT=eth0 MAC=00:e0:66:6a:c5:12:00:21:a0:fa:fa:d9:08:00 SRC=63.251.34.134 DST=10.1.1.17 LEN=77 TOS=0x00 PREC=0x00 TTL=114 ID=20784 DF PROTO=TCP SPT=443 DPT=1845 WINDOW=3578 RES=0x00 ACK PSH URGP=0 
Oct 15 18:48:11 fw kernel: [616777.270691] [IPTABLES FORWARD IN=eth1 OUT=eth0 MAC=00:e0:66:6a:c5:12:00:21:a0:fa:fa:d9:08:00 SRC=50.63.243.230 DST=10.1.1.69 LEN=40 TOS=0x00 PREC=0x00 TTL=113 ID=19790 DF PROTO=TCP SPT=80 DPT=53580 WINDOW=0 RES=0x00 RST URGP=0
```10.1.1.69 is me. I'm not hosting anything on port 80. So this looks like me connecting to a web server.

Current relevant part of the above posted script (notice only Forward is commnted)
```
########################
#
# LOGGING
#
#
########################
echo "Setting up logging"
#iptables -A INPUT  -m limit --limit 1/s --limit-burst 7   -j LOG --log-prefix "[IPTABLES INPUT "
#iptables -A OUTPUT  -m limit --limit 1/s --limit-burst 7   -j LOG --log-prefix "[IPTABLES OUTPUT "
iptables -A FORWARD -i $_ethOUT -m limit --limit 1/s --limit-burst 7   -j LOG --log-prefix "[IPTABLES FORWARD "
#iptables -A PREROUTING  -m limit --limit 1/s --limit-burst 7   -j LOG --log-prefix "[IPTABLES PREROUTING "
#iptables -A POSTROUTING  -m limit --limit 1/s --limit-burst 7   -j LOG --log-prefix "[IPTABLES POSTROUTING "
```I'm forwarding, but only looking at the external interface, but logging stuff from me on the internal network. I'm lost.

---

### Post by ant2ne on 2013-10-15
Ha, looks like a simultaneous post. I will adjust my script to resemble yours.

---

### Post by Doug S on 2013-10-15
> **ant2ne said:**
> 10.1.1.69 is me. I'm not hosting anything on port 80. So this looks like me connecting to a web server.Yes, that is packets from whomever you have an HTTP session open with. You can tell more about what is going on by the TCP flags: The first entry is the end of a session close sequence; The second and third entries are regular packet stuff mid session; The last entry is a trying to reset the connection (some systems use RST and some use FIN to terminate sessions).

---

