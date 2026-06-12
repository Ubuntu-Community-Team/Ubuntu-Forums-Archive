---
title: "FTP doesn't work with Ubuntu configured as router"
date: 2008-06-28
forum: Networking &amp; Wireless
---

### Post by ba_rich on 2008-06-28
I've configured Ubuntu Linux 8.04 as a router as described in [here]("http://ubuntuforums.org/showthread.php?t=376283&")

It uses the following iptables setup:

iptables -t nat -A POSTROUTING -s 10.1.1.0/24 -o eth1 -j MASQUERADE
iptables -A FORWARD -s 10.1.1.0/24 -o eth1 -j ACCEPT
iptables -A FORWARD -d 10.1.1.0/24 -m state --state ESTABLISHED,RELATED -i eth1 -j ACCEPT

HTTP and POP connections are working like a charm.

When a FTP client on the local LAN attempts to connect to a FTP server on the Internet, it fails.

Then initial connection to port 21 succeeds. The opening of the data connection (150) fails.

What needs to be added to the iptables setup to allow the return data connection to be routed to the originator on the internal LAN and succeed?

---

### Post by ba_rich on 2008-06-28
The ip_conntrack_ftp and ip_nat_ftp kernel modules are needed for FTP to work. These are not automatically loaded with the default ubuntu.

To have them loaded at boot, add the module names to /etc/modules. Reboot and FTP works !

---

### Post by kevdog on 2008-06-28
Or simply load them from your iptables script since this is run as root.

---

### Post by ba_rich on 2008-06-28
Where is the iptables script?

---

### Post by kevdog on 2008-06-28
Didn't you make one or did you type in the iptables commands manually?

---

### Post by ba_rich on 2008-06-28
The iptables commands were entered on the command line, then saved (iptables-save). The saved tables are loaded from the /etc/network/interfaces (pre-up iptables-restore < ...).

Are you saying a script could also be used (pre-up script)?

---

### Post by kevdog on 2008-06-28
Yes it could -- you could call the script if you wanted.  If you just wanted the iptables to be active all the time -- you could also stick reference to it in /etc/rc.local and it would load at boot.  Just depends what you want to do -- there is no right answer. 

I usually find however that it is easy to place all the commands in a shell script, since its really easy to change and make modifications months later (if the file is well commented).  Ive looked at the results of iptables-save and its really hard to interpret what the original intent of the firewall was -- its not so obvious to me at least.

---

