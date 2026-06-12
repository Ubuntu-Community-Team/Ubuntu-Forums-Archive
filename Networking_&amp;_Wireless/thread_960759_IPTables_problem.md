---
title: "IPTables problem"
date: 2008-10-27
forum: Networking &amp; Wireless
---

### Post by Scormen on 2008-10-27
Hi all,

I am learning a bit of IPTables this evening. I have made this small collection of rules. As you can see, I have commented out the rule for HTTP traffic, port 80. But... I still can access the webserver.

What is wrong with these rules?
And the main question... how can I improve this, how do you do it? :) 

```
#!/bin/bash

#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#
#                                                                                         #
#                             IPTables testserver.lan                                     #
#                                                                                         #
#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#

#------------------------------------------------------------------------------------------
# IPTables binary
#------------------------------------------------------------------------------------------

IPT="/sbin/iptables"

#------------------------------------------------------------------------------------------
# The network interface we will use
#------------------------------------------------------------------------------------------

EXTIF="eth0"
UNIVERSE="0.0.0.0/0"

echo -e "\nExternal interface: $EXTIF"
echo -e "Loading firewall server rules..."

#------------------------------------------------------------------------------------------
# Flush everything and set default policy to drop
#------------------------------------------------------------------------------------------

$IPT -P INPUT DROP
$IPT -F INPUT 
$IPT -P OUTPUT DROP
$IPT -F OUTPUT 
$IPT -P FORWARD DROP
$IPT -F FORWARD 
$IPT -F -t nat

# Flush the user chain if it exists
if [ "`$IPT -L | grep drop-and-log-it`" ]; then
   $IPT -F drop-and-log-it
fi

# Delete all User-specified chains
$IPT -X

# Reset all IPTables counters
$IPT -Z

#------------------------------------------------------------------------------------------
# Create a DROP chain
#------------------------------------------------------------------------------------------

$IPT -N drop-and-log-it
$IPT -A drop-and-log-it -j LOG --log-level info
$IPT -A drop-and-log-it -j DROP

#------------------------------------------------------------------------------------------
# INPUT: Incoming traffic from various interfaces.  All rulesets are 
#        already flushed and set to a default policy of DROP. 
#------------------------------------------------------------------------------------------

echo -e "- Loading INPUT rulesets"

# Allow loopback interface
$IPT -A INPUT -i lo -s $UNIVERSE -d $UNIVERSE -j ACCEPT

# Allow universe going to extern address
$IPT -A INPUT -i $EXTIF -s $UNIVERSE -j ACCEPT

# Allow any related traffic coming back to the server in
$IPT -A INPUT -i $EXTIF -s $UNIVERSE -m state --state ESTABLISHED,RELATED -j ACCEPT

echo -e "- Allowing EXTERNAL access to the server"

# - SSH
$IPT -A INPUT -i $EXTIF -m state --state NEW,ESTABLISHED,RELATED -p tcp -s $UNIVERSE --dport 2222 -j ACCEPT

# - FTP
$IPT -A INPUT -i $EXTIF -m state --state NEW,ESTABLISHED,RELATED -p tcp -s $UNIVERSE --dport 20:21 -j ACCEPT
$IPT -A INPUT -i $EXTIF -m state --state NEW,ESTABLISHED,RELATED -p tcp -s $UNIVERSE --dport 35000:35999 -j ACCEPT
$IPT -A INPUT -i $EXTIF -m state --state NEW,ESTABLISHED,RELATED -p tcp -s $UNIVERSE --dport 989 -j ACCEPT
$IPT -A INPUT -i $EXTIF -m state --state NEW,ESTABLISHED,RELATED -p tcp -s $UNIVERSE --dport 990 -j ACCEPT

# - DNS
$IPT -A INPUT -i $EXTIF -m state --state NEW,ESTABLISHED,RELATED -p tcp -s $UNIVERSE --dport 53 -j ACCEPT
$IPT -A INPUT -i $EXTIF -m state --state NEW,ESTABLISHED,RELATED -p udp -s $UNIVERSE --dport 53 -j ACCEPT

# - HTTP and HTTPS
#$IPT -A INPUT -i $EXTIF -m state --state NEW,ESTABLISHED,RELATED -p tcp -s $UNIVERSE --dport 80 -j ACCEPT
$IPT -A INPUT -i $EXTIF -m state --state NEW,ESTABLISHED,RELATED -p tcp -s $UNIVERSE --dport 443 -j ACCEPT

# - POP3 and POP3S
$IPT -A INPUT -i $EXTIF -m state --state NEW,ESTABLISHED,RELATED -p tcp -s $UNIVERSE --dport 110 -j ACCEPT
$IPT -A INPUT -i $EXTIF -m state --state NEW,ESTABLISHED,RELATED -p tcp -s $UNIVERSE --dport 995 -j ACCEPT

# - IMAP and IMAPS
$IPT -A INPUT -i $EXTIF -m state --state NEW,ESTABLISHED,RELATED -p tcp -s $UNIVERSE --dport 143 -j ACCEPT
$IPT -A INPUT -i $EXTIF -m state --state NEW,ESTABLISHED,RELATED -p tcp -s $UNIVERSE --dport 993 -j ACCEPT

# - SMTP and SMTPS
$IPT -A INPUT -i $EXTIF -m state --state NEW,ESTABLISHED,RELATED -p tcp -s $UNIVERSE --dport 25 -j ACCEPT
$IPT -A INPUT -i $EXTIF -m state --state NEW,ESTABLISHED,RELATED -p tcp -s $UNIVERSE --dport 587 -j ACCEPT
$IPT -A INPUT -i $EXTIF -m state --state NEW,ESTABLISHED,RELATED -p tcp -s $UNIVERSE --dport 465 -j ACCEPT


# Syn-flood protection
$IPT -A INPUT -p tcp --syn -m limit --limit 1/second --limit-burst 5 -j ACCEPT

# Furtive port scanner protection
$IPT -A INPUT -p tcp --tcp-flags SYN,ACK,FIN,RST RST -m limit --limit 1/second --limit-burst 5 -j ACCEPT

# Ping of death protection
$IPT -A INPUT -p icmp --icmp-type echo-request -m limit --limit 1/second --limit-burst 5 -j ACCEPT


# Catch all rule, all other incoming is denied and logged
$IPT -A INPUT -s $UNIVERSE -d $UNIVERSE -j drop-and-log-it


#------------------------------------------------------------------------------------------
# OUTPUT: Outgoing traffic from various interfaces.  All rulesets are 
#         already flushed and set to a default policy of DROP. 
#------------------------------------------------------------------------------------------

echo -e "- Loading OUTPUT rulesets"

# Loopback interface is valid.
$IPT -A OUTPUT -o lo -s $UNIVERSE -d $UNIVERSE -j ACCEPT

# Anything else outgoing on remote interface is valid
$IPT -A OUTPUT -o $EXTIF -d $UNIVERSE -j ACCEPT

# Catch all rule, all other outgoing is denied and logged
$IPT -A OUTPUT -s $UNIVERSE -d $UNIVERSE -j drop-and-log-it

echo -e "Firewall server rules loading complete\n"
```

Many thanks,
Kris

---

### Post by lovinglinux on 2008-10-28
I'm also starting to learn iptables and I guess you know more than me. Anyway, here is what I think...

You should comment the following line:

```
$IPT -A INPUT -i $EXTIF -s $UNIVERSE -j ACCEPT
```

As far as I understand, this rule is basically allowing all input traffic from $UNIVERSE source IP. So it doesn't matter if you comment the HTTP line, because the connection attempt is capture by this line and accepted, thus not going through the rest of the chain.

---

### Post by Scormen on 2008-10-29
Thanks for your answer, lovinglinux, but httpd is still not blocked.

Someone else what has a idea?

Thanks,
Kris

---

### Post by Scormen on 2008-10-29
Hi all,

I have been playing with the rules again and now it is working.
If you are interested, here is my working IPtables script.
Port 80 is commented out, so it is not accessible.

```
#!/bin/bash

#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#
#                                                                                         #
#                           IPTables server.test.lan                                      #
#                                                                                         #
#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#-#

#------------------------------------------------------------------------------------------
# Basic configuration
#------------------------------------------------------------------------------------------

echo -e "\n+++++++++++++++++++++++++++++++++++++++++++++++++++++"
echo -e "Loading firewall server rules..."

# IPtables binary
IPT=/sbin/iptables

# External interface
EXTIF=eth0

# Everyone, the world
UNIVERSE=0/0

#------------------------------------------------------------------------------------------
# Flush everything
#------------------------------------------------------------------------------------------

echo -e "Flushing all rules and chains"

$IPT -F INPUT 
$IPT -F OUTPUT 
$IPT -F FORWARD 
$IPT -F -t nat

# Flush the user chain if it exists
if [ "`$IPT -L | grep SERVICES`" ]; then
   $IPT -F SERVICES
fi

# Delete all User-specified chains
$IPT -X

# Reset all IPTables counters
$IPT -Z

#------------------------------------------------------------------------------------------
# Set default policies
#------------------------------------------------------------------------------------------

echo -e "Loading default policies:"
echo -e "- output: ACCEPT"
echo -e "- input: DROP"
echo -e "- forward: DROP"

$IPT -P OUTPUT ACCEPT
$IPT -P INPUT DROP
$IPT -P FORWARD DROP

#------------------------------------------------------------------------------------------
# Create a SERVICES chain
#------------------------------------------------------------------------------------------

# Make a new chain SERVICES
$IPT -N SERVICES

#------------------------------------------------------------------------------------------
# INPUT: Incoming traffic from various interfaces.  All rulesets are 
#        already flushed and set to a default policy of DROP. 
#------------------------------------------------------------------------------------------

echo -e "Loading INPUT rulesets"

# Allow loopback interface
$IPT -A INPUT --in-interface lo -j ACCEPT

# Send all INPUT to SERVICES
$IPT -A INPUT -j SERVICES

# Allow responses
$IPT -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT


echo -e "Allowing EXTERNAL access to the server"

# Allow these services:

# - SSH
$IPT -A SERVICES -i $EXTIF -p tcp -s $UNIVERSE --dport 1234 -j ACCEPT

# - HTTP and HTTPS
#$IPT -A SERVICES -i $EXTIF -p tcp -s $UNIVERSE --dport 80 -j ACCEPT


#------------------------------------------------------------------------------------------
# Some small "shields"
#------------------------------------------------------------------------------------------

# Furtive port scanner protection
$IPT -A INPUT -p tcp --tcp-flags SYN,ACK,FIN,RST RST -m limit --limit 1/second --limit-burst 5 -j ACCEPT

# Ping of death protection
$IPT -A INPUT -p icmp --icmp-type echo-request -m limit --limit 1/second --limit-burst 5 -j ACCEPT


echo -e "...firewall server rules loading completed successful"
echo -e "+++++++++++++++++++++++++++++++++++++++++++++++++++++\n"
```

Here is a nice video tutorial: [http://www.linuxjournal.com/video/mastering-iptables-part-i](http://www.linuxjournal.com/video/mastering-iptables-part-i)

Greetings

---

### Post by SpaceTeddy on 2008-10-29
right-o... erm... i don't want you to take this... wrong... but... your script is a little backwards... Let me explain why.

Usually, when you use stateful firewalling (--state) you are only allowing the outgoing packets with the SYN flag explicitly (or so i learned it). In your case, you allow any outgoing packet, and then check the incomming packets for the NEW flag - which leads the point that you don't only accept answer packets, but any traffic on the specified port. This basically means, that this rule

> $IPT -A INPUT -i $EXTIF -s $UNIVERSE -m state --state ESTABLISHED,RELATED -j ACCEPT

will accept any packet that your server has ever sent. It checks against the ACK flag in the tcp header and then checks if there is an existing connection related to this - since your machine sent the packet, there is. It send it via this rule :
> IPT -A OUTPUT -o $EXTIF -d $UNIVERSE -j ACCEPT

ok.. i am going to post a very simple iptables conifguration that will ONLY accept pakets on port 80. The server itself will not be able to forward any traffic and will not be able to query anything itself !

> sudo su
iptables -X
iptables -F
iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP

#these are generic rules for stateful firewall - always leave them in !
iptables -A INPUT -m state --state ESTABLISHED, RELATED -j ACCEPT
iptables -A OUTPUT -m state --state ESTABLISHED, RELATED -j ACCEPT

#now open the port for any incoming request to the webserver.
iptables -A INPUT -m state --state NEW -p tcp --dport 80 -j ACCEPT


the last rule i the acctual one that you need - the rest is static. You can add further specifications to it (like -i, -s or -d) to make it more restrictive. Also - a -d 0.0.0.0/0 is not necessary, as this is the default anyway and does not need to be set explicitly. 

well - i hope i didn't do any typos :)

---

### Post by Scormen on 2008-10-29
Many thanks for this very clear explanation, SpaceTeddy!
I'm gonna have a look further.

Kris

---

