---
title: "Can't see ubuntu machine on local network"
date: 2017-06-16
forum: Networking &amp; Wireless
---

### Post by xeperis2 on 2017-06-16
Fresh installed ubuntu 16.04 Desktop. Did a `apt-get install openssh-server`.

From MacOS I can see ubuntu machine on the network with `arp -a`. Can ping, can connect via ssh.
From Windows machine - NADA. `arp -a` does not list ubuntu machine, from windows 10 ubuntu bash - can not ssh.

Tried `sudo ufw disable`, tried disabling windows securities/firewalls.
Computers are connect via one router (local network).

Any ideas?

P.S. can see MacOS machine in windows just find. And ubuntu machine does not see windows machine ip in local network.

---

### Post by TheFu on 2017-06-16
What are the IPs for the client and the server?  Need to determine if this is a network issue or just a name resolution issue.  Try using **putty 192.168.x.x** where the IP is that for the Ubuntu ssh machine.

"Local network" doesn't mean anything to Unix systems, unless you've enabled Samba. For Windows, local network is "cifs" so don't expect random other TCP services to show up there. Web servers won't, LDAP servers won't, and ssh servers won't.

Windows was designed for LAN use and broadcasts "I'm here, I'm here" on the subnet for CIFS clients to see. This doesn't scale to internet-size.  Linux hasn't done this, since Unix doesn't.  That means you need to setup name resolution so all clients and servers to know about each other.  There are 3 common methods.
a) /etc/hosts
b) DNS server for the LAN (lots of manual config with this)
c) zeroconf/avahi

Avahi is included in desktop Ubuntu's. Don't know about servers, but my setup steps purge it.
I use /etc/hosts, since we only have about 30 systems.  Windows puts there /etc/hosts file somewhere else. It can only be edited using "Admin rights."  There are lots of how-tos on the internet about this.

So ... if you want to try avahi, use the **hostname.local** as the name.  So, if the hostname is hadar, then **ssh hadar.local** is what you want.

Arp will only see ethernet machines on the same subnet that have announced on the network or been used.

No firewall is enabled by default on Ubuntu systems. This is because there aren't any services that listen and are enabled by default.  When you install the ssh server, at that point, it would make sense to enable the firewall and limit which external machines can connect.  For me, that is pretty easy. Just install **fail2ban** with openssh-server.  Fail2ban will automatically block brute force attacks and is pre-setup for normal ssh server settings.  If you change the ssh port, then the fail2ban settings will need to be changed too.

Just re-read the OP.  Have you tried putty? On Windows, **putty** is the normal ssh client. Can't really help more, as I've never seen Win10.

---

### Post by xeperis2 on 2017-06-18
Thanks **TheFu** for the pointers. I tried **putty** tho I could not connect through router assigned IP. I eventually just forwarded some ports to the machine and managed to connect though external IP so ATM it's fine, since I wanted to host some CI stuff for a project. Much thanks for **fail2ban**.

---

### Post by TheFu on 2017-06-18
What are the IPs for the client and the server?
You should only need 1 port forward.  The others are security risks.

'CI' ???

---

