---
title: "XP ICS to  Ubuntu machine"
date: 2008-06-21
forum: Networking &amp; Wireless
---

### Post by tc3racer on 2008-06-21
Hi There.

I am having real bad problems with my ICS between my machine my main one that can connect to internet is xp i have a cross over cable to my ubuntu machine i have given the card in the ubuntu machine an adress of 192.168.0.2 my second card which is in my main machine an adress of 192.168.0.1 they seem to be able to ping each other. however i cannot connect to the internet on ubuntu machine. I have enabled internet sharing on my main pc to give access to the internet on the second card. I can access the internet on xp machine with no problems.

---

### Post by alastair on 2008-06-21
Check :

1) You can ping the XP machine from Ubuntu. On ubuntu, open a terminal and :

ping 192.168.0.1

2) Check the network routing on ubuntu - in the terminal, type :

route -n

What does it print? We need to know what gateway is set.

3) Also - "ifconfig -a" might help as well.

I assume no firewall is installed on either machine.

Ubuntu "sudo iptables -L -n" contains no rules.

---

