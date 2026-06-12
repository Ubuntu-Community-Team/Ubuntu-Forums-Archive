---
title: "P2P with a firewall"
date: 2007-01-02
forum: Networking &amp; Wireless
---

### Post by fenomenoxp on 2007-01-02
Hi everyone!
I'm trying to get a p2p file sharing client to work with Edgy amd64. I'm using a firewall set up with Firestarter (I don't khow much about firewalls, I must confess). I configured Firestarter to block all ports (Incoming and outgoing connections) except a list of them (including http, ftp and so on). 
I have tried with gtk-gnutella, but It doesn't work (it does when the firewall is off). I have tried also with apollon, but it wont work (Gnutella and OpenFT plugins don't connect). Apollon does not work with the firewall off, so I suppose it might be a configuration problem. Finally I tried with aMule, but it seems not to work (I find results, but no download). Anyway, I prefer not to use amule, because it's too slow for me. 
Anybody knows a way to solve this problem? Anybody got apollon to work or is it a bug (I have googled around and found no solution)?

---

### Post by suoko on 2007-01-20
I'm trying right now to have firestarter running and not blocking amule traffic.
From firestarter "active connections" pane, it seems amule uses a large number of ports.
 currently amule opens the following ports:

4662 (set in "port to be used" in amule preferences)
4672 (set in "port to be used" in amule preferences)
59222
32296
3851
55628
49260
25974
4242
10276

but I guess many of these ports are open randomly by amule.

---

### Post by x1a4 on 2007-01-26
Hi,

How do you connect to the Internet?  Your router may have a built-in firewall and things get blocked there.  To get aMule working correctly, login to your router (usually you can do this by pointing your browser to [http://192.168.1.1/](http://192.168.1.1/)) and add the following rules under Firewall > Port Forwarding: 

Rule Name: eDonkey
Protocol:     TCP
Port Start:  4662
Port End:    4662
Port Map:   4662

Rule Name: eDonkeyUDP1
Protocol:     UDP
Port Start:  4665
Port End:    4665
Port Map:   4665

Rule Name: eDonkeyUDP2
Protocol:     UDP
Port Start:  4672
Port End:    4672
Port Map:   4672

To change *iptables* do the following from a terminal or console: 

[i]sudo iptables -A INPUT -p tcp --dport 4662 -j ACCEPT
sudo iptables -A INPUT -p udp --dport 4665 -j ACCEPT
sudo iptables -A INPUT -p udp --dport 4672 -j ACCEPT[/i]

To remove these rule do the same except replace ACCEPT with DROP

Also, your ISP may be blocking certain ports--you should ask them.  With me, the #1 criterion when choosing my ISP was that they absolutely do not block any ports.

Finally, many P2P networks, like ED2K, require you to upload a great deal of files before increasing your download speed.

---

