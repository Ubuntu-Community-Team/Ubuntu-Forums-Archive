---
title: "couple easy questoins"
date: 2007-06-04
forum: Networking &amp; Wireless
---

### Post by nonewmsgs on 2007-06-04
i have a neat little home LAN with damn near all my computers upgraded to ubuntu 7.04.  what i find weird is that ping ip works but ping computername doesnt.  if i ping the computername from itself i get the typical localhost response, but from a computer 2 feet away, it needs the actual ip.  when i use the router assigned ip everything's fine 'n' dandy.  why cant it see the computer name?

question 2: can i set the remote resolution for vncviewer?  right now i can login remotely change it, and then get booted and then relogin and im fine but i would like to know if it is possible as some kind of switch or paramater.

---

### Post by zero-9376 on 2007-06-05
for the hostname lookup issue, the solution that i found works for me is editing the /etc/dhcp3/dhclient.conf and uncommenting the send host-name line and changing the hostname to that of the computer. You will probably have to restart networking after that for the changes to take effect. 

You may be able to determine if this is the problem by looking at your routers client table and see if hostnames are already being registered.

---

### Post by croto on 2007-06-05
hey, 

I'm not sure I can give you a definite solution, but I'll try to point in the right direction. In order for each computer to know the domain name of the others, AFAIK, there are two ways. One is to set a DNS server in the LAN that would inform all computer what IP corresponds to each computer. Some advanced routers have that feature. 
The second way, probably the easiest, is by using the file /etc/hosts. That file holds the same information locally. That is, you can write in it pairs of domain names and IPs, that will be used to resolve those domain names. The only catch is that the router should give every time the same IP to each computer in the network.

Hope that helps, and happy hacking.

---

