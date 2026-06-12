---
title: "Problems connecting to local network server with clean Hardy install on Dell Vostro 1"
date: 2008-07-19
forum: Networking &amp; Wireless
---

### Post by drplix on 2008-07-19
Hello.  Looking for ideas for how to diagnose a very bizarre network issue with a clean vanilla install of Hardy 8.04 64-bit on a Dell Vostro 1510 laptop.

Network Topology:

A. Hardy 8.04 Server running MythTV and other services including ssh and vnc login. (Gigabit Wired NIC connected to Gateway D).

B. (Problem laptop) Dell Vostro 1510 with Wired Gigabit Realtek RTL8111/8168B and Wireless Broadcom BCM4310 (rev 01).

C. (Working Control Laptop) HP 6715B with Broadcom BCM4312 wireless NIC.

D. Gateway ADSL router and DHCP server.

E. Asus Wireless Access Point connected to Gateway D.

Symptoms:

Good:

A, C, D, E all work together correctly. Laptop C can run a MythTV fronted over WiFi to the MythTV server A.  Can also access web services and remote login using both ssh and vnc.

Bad:

Laptop B has WiFi connection to the network and can access the internet through the gateway D.
B can only connect to the Web server (80) of A using Firefox.  Other ports timeout.  More weirdly I cannot telnet to port 80

telnet 192.168.100.8 80  hangs.

More weirdness,  B has full access to control laptop C on the local network - ssh and web servers etc. Also no issues with gateway D. No issues.

ssh from B to A gives 'publickey required' response (all my ssh uses PKI access with password disabled).  When I try ssh with PKI key ssh crashes immediately.

All machines have no iptables firewall and report:

iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 

All machines have default hosts.allow and hosts.deny policy.

Tests of B to A:

Ping is no problem.
Traceroute is no problem and reports the same as for C.
Portscan from B to A shows open ports for 80 (HTTP), 3306 (MySQL) etc.
telnet 192.168.100.8 3306 hangs (on C it gives me the mysql handshake).

Other issues:

The realtek wired NIC does not work at all.  I had a 'race condition' just to get the install connected at all.  No wired NIC and the 8.04.1 CD image wl driver was broken for BCM4310 - I had to install ndiswrapper with the Dell Win XP drivers to get the WiFi working then apply all the patches for the system including the latest kernel image and headers.  With the system fully patched and current the wl driver now works for BCM so I have got rid of the ndiswrapper.   Still no luck with realtek wired NIC.  I have removed the driver with 'rmmod r8169' and no longer have eth0 device.

One other thing I turned off ipv6 on B but this made no difference - all my other systems are Hardy 8.04 with standard default network settings and have no issues with ipv6.

Help Please:

I'm pretty comfortable with basic networking and have never experienced a problem like this before.  I'd love to hear some suggestions for how I can diagnose the problem.  The obvious thing would be to look at the firewall of B and A but B can access all of C and C can access all of A and all machines have iptables as shown above and default settings for hosts.allow etc.

Thanks in advance.

---

### Post by drplix on 2008-07-19
Still not solved this.  Have tried obvious things like reverting back to ndiswrapper driver.  Any suggestions, even just tools that might help me understand why the connection is bouncing off the server?

---

### Post by jim10 on 2008-08-03
Your problem may be the same one I am having [http://ubuntuforums.org/showthread.php?t=838873](http://ubuntuforums.org/showthread.php?t=838873)

---

