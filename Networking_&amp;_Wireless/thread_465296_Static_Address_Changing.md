---
title: "Static Address Changing"
date: 2007-06-05
forum: Networking &amp; Wireless
---

### Post by KnifeyMcShanker on 2007-06-05
I have a little problem with Ubuntu 7.04 server.  I have the IP address set to static at 192.168.1.104 and everything in the /etc/network/interfaces file is set up correctly for static... yet every now and then my box changes its IP address via DHCP.  This is very annoying because I have various services that people use, and the ports used are of course forwarded to its static IP.  When it changes, everything goes down until someone notifies me of the problem.

Here's the contents of /etc/network/interfaces, if it helps:

```
knifeymcshanker@minmatar:/etc/network$ cat interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0

#dhcp
#iface eth0 inet dhcp

#static
iface eth0 inet static
address 192.168.1.104
netmask 255.255.255.0
broadcast 192.168.1.255
network 192.168.1.0
gateway 192.168.1.1

```

---

### Post by spd106 on 2007-06-05
This is just a suggestion, but you might want to consider removing the first iface line. Yes, it's commented out but I have read that this can cause problems (though that's very rare) and since it's not needed...

---

### Post by KnifeyMcShanker on 2007-06-05
Alright, I tried that, I'll wait a bit and see if it worked.

---

### Post by BarryBotha on 2007-06-27
Hi 

I am having exactly the same problem.
This server is running nagios monitoring and every time it switches back to DHCP all my monitored hosts go down.
It seems like its happening every morning 09:00 (GMT+02).

My /etc/network/interfaces file:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.2.7
        netmask 255.255.255.0
        network 192.168.2.0
        broadcast 192.168.2.255
        gateway 192.168.2.1

I find this behavior very strange - any ideas on what may be causing this?

Thanks
Barry

---

### Post by scxtt on 2007-06-27
is there a dhcp daemon running?

---

### Post by BarryBotha on 2007-06-27
There is no dhcp daemon running on the server itself. 
My firewall (Gnatbox 250) is running one though and this is where the server gets the IP from when it changes over to DHCP.
I've checked the /var/log/message file and nothing is reported at the time when this happened.

Barry

---

### Post by BarryBotha on 2007-06-28
Hallo

This happened again this morning. 
I am becoming quite concerned as I have 2 servers with this behavior.
Is this a known issue?

Thanks
Barry

(Linux devmon 2.6.20-15-server #2 SMP Sun Apr 15 07:41:34 UTC 2007 i686 GNU/Linux)

---

### Post by scxtt on 2007-06-28
have you tried turning off dhcpd on the firewall, just for kicks?

---

### Post by bagpussnz on 2008-03-31
Hi,
Has anyone got an update for this - I too am seeing exactly the same issue.
I've seen it on a number of Ubuntu server machines - which is a major pain (especially as one of them is a primary ldap server).

One of the suggestions was to remove commented iface lines - we don't have any of these.
/etc/network/interfaces is....

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.240.100
        netmask 255.255.252.0
        broadcast 192.168.240.255
        network 192.168.240.0
        gateway 192.168.240.1

 cat /etc/issue
Ubuntu 7.10 \n \l

I don't know if it's relevant, but the /etc/hosts file is, (the name of this host is ldap)

 cat /etc/hosts
127.0.0.1       localhost ldap.dmz.co.nz
127.0.1.1       ldap.dmz.co.nz      ldap
192.168.240.99  ldap2.dmz.co.nz ldap2

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts




Regards,
Ian.

---

### Post by The Cog on 2008-03-31
I haven't seen this on any of the Ubuntu servers I know of, so it's not a universal problem. I wonder if avahi-daemon is anything to do with it. Have you tried disabling that?

---

