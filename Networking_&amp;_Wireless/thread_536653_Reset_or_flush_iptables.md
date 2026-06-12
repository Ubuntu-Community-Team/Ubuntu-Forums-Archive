---
title: "Reset or flush iptables"
date: 2007-08-28
forum: Networking &amp; Wireless
---

### Post by JustinMorris on 2007-08-28
I messed something up trying to get my eth1 to talk to my eth0.  Now nothing talks to anything at all now, which sucks because I use this box is a media center and a test web server, etc and its all down.  How else can I do to flush out iptables?  I used webmin to set them up.  Of course I cannot access that now.

I have tried:
```

iptables -F
```

```
iptables --flush
```

```
sudo iptables -P INPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -t nat -P PREROUTING ACCEPT
sudo iptables -t nat -P POSTROUTING ACCEPT
sudo iptables -t nat -P OUTPUT ACCEPT
sudo iptables -F
sudo iptables -t nat -F
sudo iptables -X
sudo iptables -t nat -X
```

Thank you for any help.

---

### Post by jaspreet on 2007-08-28
you may like to install firestarter ( A User Interface for setting up firewall) to reconfigure firewall on your system. Try the following link:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_IPtables_Firewall_Configuration_GUI_.28Firestarter.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_IPtables_Firewall_Configuration_GUI_.28Firestarter.29)

---

### Post by JustinMorris on 2007-08-28
This is just Ubuntu server btw :-/

I couldn't even install firestarter, since I have no internet access anymore though because of the iptables issue.

---

### Post by will71110 on 2007-08-28
First to an "ifconfig", make sure your IPs are still right.
Do "route" and make sure there is an 0.0.0.0 route to your gateway.
Also see if your "arp" using "arp -a" has the MAC address of your gateway.

Let me know the results. (Also try a ifconfig eth0 up, maybe your interface turned off?)

---

### Post by jaspreet on 2007-08-28
> **JustinMorris said:**
> This is just Ubuntu server btw :-/

I couldn't even install firestarter, since I have no internet access anymore though because of the iptables issue.

if you use iptables -F this should flush all the current rules and should let all kind of traffic move in or out. If you still cannot access internet, the problem is not with firewall. Maybe your netconnection needs to be reconfigured, ethernet/modem cable is unplugged etc.

are you able to ping other systems on your network??

---

### Post by JustinMorris on 2007-08-29
lol, my "ethernet/modem cable is unplugged"

Nice one.  I'm not an idiot.  All other systems on the network worked just fine until I started messing with the iptables on this system and apparently there might be a bug with iptables -F

I spent too much time, so I just reinstalled ubuntu.

---

