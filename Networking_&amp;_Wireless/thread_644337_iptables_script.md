---
title: "iptables script"
date: 2007-12-18
forum: Networking &amp; Wireless
---

### Post by Dr Small on 2007-12-18
I am wanting to write a script to get Iptables to allow inbound (and outbound ?) for port 22 (ssh), and be able to have it for startup too, because I heard that everything is dropped when the system restarts.

I know how to use firestarter, but I want to be able to do all of this in the command line.
Any help, or suggested reading would be helpful :)

Thanks,
Dr Small

---

### Post by HermanAB on 2007-12-18
I think that you have a slight misconception about how Firestarter works.  It has two components to it.  On the one hand it is configuration tool for iptables (which in itself is front end for netfilter) and on the other hand it is a monitoring tool of the system logs.  

Once you have used Firestarter to configure the system, the configuration is saved and it is automatically applied on every restart.  You need not run the Firestarter GUI again to be protected.

So, do use Firestarter to configure the SSH rules, then relax and enjoy it - you'll be safe, even during a restart.

In any case, Linux networking is inherently safe, so even with no iptables rules, your system will still do OK!

Cheers,

Herman

---

### Post by Dr Small on 2007-12-18
Oh, I completely understand how firestarter works, and all, but I was expirimenting on how to do it in an environment where I couldn't use firestarter, like for example, a command line based system.

I completely have the concept of how firestarter works, and how it configures iptables, but I wanted to know how to do it the hard way, and how to do it all from the command line.

I went searching around, and found this script, but I know so little about iptables, that I don't know if this is sufficient to make it work properly:
```
#!/bin/sh

###################################
#				  #	
# IP Firewall script for 	  #
# PCC-Services			  #	
# Author: Mike Petersen		  #
#				  #
###################################



########## The Allowed Chain for TCP connections

iptables -N allowed
iptables -A allowed -p TCP --syn -j ACCEPT
iptables -A allowed -p TCP -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A allowed -p TCP -j DROP

########## TCP rules (Transmission Control Protocol)


### SSH port
iptables -A tcp_packets -p TCP -s 0/0 --dport 22 -j allowed
```

Dr Small

---

