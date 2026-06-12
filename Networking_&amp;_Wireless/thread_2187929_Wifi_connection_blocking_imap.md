---
title: "Wifi connection blocking imap"
date: 2013-11-14
forum: Networking &amp; Wireless
---

### Post by mavdlind on 2013-11-14
Hi there,
I use two imap servers (gmail and work). At work, or elsewhere, no problem in accessing both via thunderbird. At home, the imap server for work cannot connect. The problem is system-wide: I tried other email clients and always get variation on 'imap failed connection to server'.
I tried to delete the connection in the settings and then redo it, with no success. 
Any suggestion?

Thanks in advance
Marc

---

### Post by SeijiSensei on 2013-11-14
I'm sure you've already asked the administrators at your workplace about this problem, right?  What did they say?

I can think of lots of reasons why someone trying to connect to a workplace mail server from some random location on the Internet would be unsuccessful. Until you talk to the administrators, we really cannot help.

---

### Post by mavdlind on 2013-11-15
The problem does not lie with the server at workplace: I have been able to connect to the imap server at other locations, including abroad. I really think that the issue lies with the setting of my own wifi.

---

### Post by SeijiSensei on 2013-11-15
No wifi router is going to block access to the IMAP ports by default. If you reset the router to factory defaults, can you still not connect?

Do you have a firewall on the Ubuntu machine?  Please post the output of "sudo /sbin/iptables -L -nv" inside [noparse]```

```[/noparse] tags.

---

### Post by mavdlind on 2013-11-15
Resetting of the router did not work
Output is:
Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         


Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         


Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source

---

### Post by SeijiSensei on 2013-11-15
OK.  Let's try something else.  Run the command "telnet name.of.the.server 143" and see what happens.  If that fails because the server requires an encrypted connection, then replace 143 with 993 and see if that works better.  If both methods fail with a "host unknown" type of error, replace the server's name with its IP address.  It could be a DNS problem.

---

