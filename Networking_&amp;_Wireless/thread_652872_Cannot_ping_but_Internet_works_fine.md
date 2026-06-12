---
title: "Cannot ping but Internet works fine"
date: 2007-12-29
forum: Networking &amp; Wireless
---

### Post by zlorv on 2007-12-29
Hi all... got a little problem since yesterday;

First to the system: Ubuntu Feisty, set up about half a year ago and was running fine since then... using it as a file server.

To the problem: yesterday suddenly i couldn't connect anymore to the data on the server and couldn't ping it.
ok, went down in the basement to the server; it war operating normally, internet works fine...

ping to localhost works
ping to own IP works
ping to other LAN computer doesn't work
ping to gateway doesn't work
ping to http address - address is resolved in an IP but ping doesn't work

i'm using no firewall - and it was working great until yesterday...

i had the intention when i was setting up this box half a year ago to get to know linux a bit... but hadn't the time.. so need help here :)

greets and thanks in advance


P.S. sorry for my English -> not my native tongue

---

### Post by tgilber1 on 2007-12-29
If you're able to ping within your network, then I doubt that there is any issue with your linux box.  Have you tried pinging other sites from your network?  Have you tried pinging these same sites from another network?  Possible causes could be your router, destination IP, or your ISP is filtering icmp packets (ping relies on these packets).  Somewhere along your tracepath, icmp filtering may be occurring.

---

### Post by zlorv on 2007-12-29
ping inside my network doesn't work

the ubuntu box can't ping anything but localhost and his own address...
the other (windows) computers can ping everything (inside/outside) but the ubuntu box

so can't be the router or isp...

---

### Post by mellowd on 2007-12-29
Looks like your ubuntu box is filtering icmp. Check your firewall

---

### Post by zlorv on 2007-12-29
don't have a separate firewall

is there a default firewall in ubuntu? but how could it have changed from allow to deny without doing anything?

---

### Post by mellowd on 2007-12-29
Ubuntu comes with iptables. I've never configured it myself. Are you able to install firestarter? It's an application that you can use to configure iptables in a gui

---

### Post by tgilber1 on 2007-12-29
> **zlorv said:**
> ping inside my network doesn't work

the ubuntu box can't ping anything but localhost and his own address...
the other (windows) computers can ping everything (inside/outside) but the ubuntu box

so can't be the router or isp...

I concur with your assessment, did not realize that you could ping from other boxes.  In this case, you can use iptables to help diagnose problem.

sudo iptables -L # list filters for INPUT/FORWARD/OUTPUT

sudo iptables -L -t nat # list filters for nat tables #PREROUTING/POSTROUTING/OUTPUT

#Look for any line that prints out "icmp" and -j DROP/REJECT

ex.

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
DROP       icmp --  anywhere             anywhere 


1.  You can issue a quick iptables -F # flushes out filters - non-binding command, if iptables is not saved.  Firewall should restore on next boot, unless you save modified iptables firewall (e.g., sudo iptables-save)
2.  After issuing iptables -F and/or iptables -F -t nat, ping website.

---

