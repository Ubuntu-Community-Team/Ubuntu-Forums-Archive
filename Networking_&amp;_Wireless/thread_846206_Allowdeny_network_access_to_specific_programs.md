---
title: "Allow/deny network access to specific programs"
date: 2008-07-01
forum: Networking &amp; Wireless
---

### Post by kriukov on 2008-07-01
I use Firestarter to configure my firewall settings and I whitelist outcoming traffic by opening specific ports. However, a port can be only open to every application or forbidden altogether (or so I see in Firestarter settings), and I would like to be able to filter the applications using the port as well. Is it possible at all?

---

### Post by kevdog on 2008-07-01
I'm not sure with Firestarter.  Its possible however to append the rules you want to add by making a small script with the rules listed in the script, and then passing this script to iptables directly.  This will not interfere with Firestarter.

Can you give me some ideas about what you want to filter?  Are the outgoing or incoming ports?

---

### Post by milosz.galazka on 2008-07-01
If you want to allow only specified services (squid for example) then you could use iptables owner module.

---

### Post by kevdog on 2008-07-01
Yes you could also filter them at the application level or through use of black/white lists.

---

### Post by kriukov on 2008-07-01
2 kevdog: For example, I have outbound port 80 open. That means it is open to any application in my system. But let's say if I want Firefox to be able to use outbound port 80, and I don't want StarDict to use port 80. Or: I want only Firefox to use port 80, and no other application. 

I have all incoming ports blocked in Firestarter settings.

2 milosz.galazka: thanks, I will try to find out how to do that.

---

### Post by kevdog on 2008-07-01
I dont think iptables can filter packets originating at a certain application.  Im not an iptables expert but I don't remember this as an option.

---

### Post by milosz.galazka on 2008-07-01
but if on firewall packets from user userx are passed then 
su userx -c firefox 
will work as suscpected...

---

### Post by kevdog on 2008-07-01
Correction -- iptables can filter by the owner filter (however its not quite as straight forward as you want to do).  Take a look:
[http://iptables-tutorial.frozentux.net/iptables-tutorial.html#OWNERMATCH](http://iptables-tutorial.frozentux.net/iptables-tutorial.html#OWNERMATCH)

Here would be an example of how to do this using inetd as the process -- however if the process number changes then the rule would be invalid:

PID=`ps aux |grep inetd |head -n 1 |cut -b 10-14`

/usr/local/sbin/iptables -A OUTPUT -p TCP -m owner --pid-owner $PID -j ACCEPT

---

