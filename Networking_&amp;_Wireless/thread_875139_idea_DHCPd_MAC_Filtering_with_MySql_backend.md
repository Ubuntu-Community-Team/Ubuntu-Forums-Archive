---
title: "idea: DHCPd MAC Filtering with MySql backend"
date: 2008-07-30
forum: Networking &amp; Wireless
---

### Post by eaglestrike7339 on 2008-07-30
I just wanted to see if anyone knew anything about this, or could offer an alternative. 

Goal: [easy]  -Have a DHCP server be filter MAC addresses and only give IPs to a computer if its MAC was on the allowed list. [/easy]
      [tricky]-Have this list be read from a column in a MySql database. [/tricky]
      [even trickier] -Have this action occur in real time [/et]

This system would be used to allow a PC to join a small subnet of other PCs, for the purpose of, say, gaming. 
Could there be a system of registering a PC, through the user-accessible means of an intranet webpage, and then allowing to connect within a short period of time (<2minutes?)

MAC filtering by itself is not difficult with dhcpd. The problem with a short-termed cron'd script, to print the MACs and replace the dhcpd.conf file is that the DHCP server would have to restart, which would drop connections (?). 

Any ideas on how to do this? Any input at all would be great, even if it was little more than gasping, pointing a finger and saying "oohh, good luck" or something. 

Thanks guys, 
eagle

---

### Post by antantant on 2010-03-29
Hi eagle,

I'm also looking to implement a similar system, did you ever have any luck with this?

Pulling new connections' MACs from a mySQL database in realtime would be the goal, but also time limiting the already-approved connections, which I've not yet looked into. 

For me, this would actually be better done at routing level, rather than DHCP/IP level, so instead of dropping the connection the client is forced to a 'blocked' page as such.

Sorry to post in such an old thread..!

Ant

---

### Post by dwarfolo on 2010-03-29
An alternative could be a combination of MySQL+PHP and iptables.
Upon  registering a PC to the system you can use PHP (or whatever cgi or  scripting tool you prefer) to update and run an iptables script with  specific rules to deny/allow access to the DHCP server from that specific MAC  address.

---

### Post by antantant on 2010-03-31
Interesting, I'm going to look more into an iptables method, sounds like it could be a good solution for me. Thanks for the suggestion, I'll post with how I get on.

---

