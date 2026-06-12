---
title: "internet fine, network blocked, help."
date: 2007-12-19
forum: Networking &amp; Wireless
---

### Post by Naegling23 on 2007-12-19
ok, so here is my problem:
I have two computers, they each have external internet access.  However, they cannot connect using nfs (after upgrading to gutsy).  Upon further investigation, I discovered that they cannot ping each other either.  So, in an experiment, I removed IPtables from one of them.  That one can now connect to the network (I know this because I could not access my router setting, after removing IPtables, I can).  So, the computer with IPtables installed still cannot access the internal network, and I know that IPtables is the culprit.  So, I installed firestarter to try to edit IPtables.  Now, if I start the firewall, I get no internet access at all, if I stop it, I get external internet access, but still no internal network access.  
My questing:
how can I configure iptables to allow access to the network and the internet using firestarter (or kmyfirewall since im a kde user)?
Additional info that might be usefull:
I have only one ethernet card, but im showing two controllers eth0 which shows zero activity, and eth1 which is the one being used (at least according to the traffic on firestarter).  Could this be where my problems lie?  Should I have only one?
Please help, this has been going on for months now, and I use nfs to keep my two computers syncronized as a sort of data backup system.

---

### Post by fain on 2007-12-19
check here for nfs and firewall setup

[http://ubuntuforums.org/showthread.php?t=352486]("http://ubuntuforums.org/showthread.php?t=352486")

---

### Post by Naegling23 on 2008-01-02
wow, couldnt quite figure that one out....im not looking for a locked down firewall though, im trying to run it fairly wide open.  Why can I not even access my router or ping other computers on the network?  Im trying to open it up as far as I can.

---

### Post by fain on 2008-01-02
Make sure your Ip addresses are all on the same subnet. Your probably using the subnet mask of 255.255.255.0 so this means that your private address has to have the first 3 octets the same. for example "192.168.0.1" router address. 192.168.0.2 computer 1 and 192.168.0.3 second computer and so on changing the last octet for each node. 

Your gateway needs to be the address of your router. You need the get the DNS from your ISP. Some routers can act as a DNS forwarder but its usually better to get the DNS from direct. 

Id recommend setting the ip addresses in order 1,2,3,etc so you can easily remember what computer has what address.

Usually i set my router to .1 address and my main computer at .2 and so on.

---

