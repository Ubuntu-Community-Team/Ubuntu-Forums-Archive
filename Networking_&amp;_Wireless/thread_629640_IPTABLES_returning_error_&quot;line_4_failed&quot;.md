---
title: "IPTABLES returning error &quot;line 4 failed&quot;"
date: 2007-12-02
forum: Networking &amp; Wireless
---

### Post by spleenz0r on 2007-12-02
Folks,
I am a long time reader, first time poster. ;)

I have been using a Slackware box as a firewall / NAT box for ages.  My network looks something like:

Internet > Modem > Slackware box > Switch > LAN

I am currently trying to build out an Ubuntu 7.04 box to replace the aging Slackware box, and am having problems getting a basic firewall script up and running.  When I try loading the script (either using a sudo /etc/init.d/iptables restart or sudo /sbin/iptables-restore < /etc/iptables.up.rules), I receive an error on the first call to iptables.  It comes back as (from the later command):

iptables-restore: line 4 failed

I have looked through the forums and googled the error and similar errors, but have not really found any good direction to go.

Can anyone here give me an idea on where to go next?

Here is my current iptables script (eth0 is external and eth1 is internal):
> #!/bin/sh

# Set default policy to accept, so as to not kill connection while script is running
iptables -P INPUT ACCEPT

# enable ip forwarding in the kernel
/bin/echo 1 > /proc/sys/net/ipv4/ip_forward

# Flush rules
iptables -F
iptables -t nat -F

# Delete chains
iptables -X firewall
iptables -N firewall

# Accept everything from loopback and LAN
iptables -A firewall -i lo -j ACCEPT
iptables -A firewall -i eth1 -j ACCEPT

# Forward LAN traffic from LAN $INTIF to Internet eth0
iptables -A firewall FORWARD -i eth1 -o eth0 -m state --state NEW,ESTABLISHED -j ACCEPT

# Enable masquerading to allow LAN internet access
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

# Accept SSH from certain IPs
iptables -A firewall -p tcp -i eth0 --dport 22 -s <hidden IP> -j ACCEPT 
iptables -A firewall -p tcp -i eth0 --dport 22 -s <hidden IP> -j ACCEPT 

# Accept anything from port 1024:65535 on TCP and UDP
iptables -A firewall -p tcp -i eth0 --dport 1024:65535 -j ACCEPT
iptables -A firewall -p udp -i eth0 --dport 1024:65535 -j ACCEPT

# Block out all other Internet access on eth0
iptables -A firewall INPUT -i eth0 -m state --state NEW,INVALID -j DROP
iptables -A firewall FORWARD -i eth0 -m state --state NEW,INVALID -j DROP

# Allow ICMP
iptables -A firewall -p icmp -i $EXTIF -j ACCEPT

# Redirect input to firewall chain
iptables -A firewall INPUT -j

# Set default policy on input chain
iptables -P INPUT DROP

Thanks in advance.
-spleenz0r

---

### Post by samaricsm on 2008-02-08
Have you tried putting the commands directly into the INPUT chain, as opposed to building the firewall chain and appending that to INPUT.  The fourth line is the attempt to destroy the firewall chain.  

I know, you're think, but this should work!  On my machine the -X was a warning that the chain did not exist.  It was definitely not a show stopper.  Make a copy try it.  If that fixes it, you have a new complaint, but working code.

---

