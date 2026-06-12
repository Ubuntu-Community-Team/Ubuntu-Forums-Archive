---
title: "Feisty to Hardy to No Networks"
date: 2008-05-23
forum: Networking &amp; Wireless
---

### Post by dietrichmd on 2008-05-23
Ok, I had feisty up and running all nice like, then I decided to upgrade to Hardy.  That is when all the problems started.  Aside from some cosmetic issues, hardy is great, but....

My network has 3 wired connections that are always on.  2 of these are windows (vista and xp) the other is ubuntu (this machine that I am currently using to type this message).  Now, here is where things get fun.

THe VISTA machine can see all machines on the network, and connect to them and do things just fine.

The XP machine cannot see the ubuntu machine, although it can ping and resolve it from a command prompt.

The UBUNTU machine cannot see any of the windows machines.  It can ping by IP just fine, but cannot ping via the hostname without winbind and that makes it REAL slow.

Since I figured this was an upgrade issue initially, i have since formated and reloaded hardy as a fresh install (much nicer this way), so everything is fresh and 'out of the box' so to speak.

I will also say that I have spent the better part of 4 hours looking for this answer last nite and today, and have seen MANY similar issues, but with no results.  So if anybody can point me to the right direction, that would be great.

Also, here is the output of some of the commands I saw on other posts from my machine:

---------
dmduke@jupiter:~$ smbtree
Password: 
failed negprot
failed negprot

-----------
root@jupiter:/home/dmduke# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0


--------
/etc/hosts
127.0.0.1	localhost
127.0.1.1	jupiter

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

-----------
/etc/samba/smb.conf

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = HOME

# server string is the equivalent of the NT Description field
   server string = %h

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

netbios name = jupiter

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = true





Thanks

PS:  Firewalls are set to accept ICMP on all machines (ubuntu has no firewall loaded)

---

### Post by mapes12 on 2008-05-23
You may have seen this already but if not this may help:

[http://ubuntuforums.org/showthread.php?t=500734](http://ubuntuforums.org/showthread.php?t=500734)

---

### Post by dietrichmd on 2008-05-23
No, that didn't do the trick either.  I'm fairly certain its not a firewall issue, and using pyneighborhood, it fails to scan my workgroup.

---

