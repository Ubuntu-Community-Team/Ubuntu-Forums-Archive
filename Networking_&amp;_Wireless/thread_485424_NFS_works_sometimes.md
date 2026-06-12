---
title: "NFS works sometimes"
date: 2007-06-26
forum: Networking &amp; Wireless
---

### Post by 65 mustang on 2007-06-26
I have two 7.04 ubuntu systems.  One is a firewall and dhcp server for my network and has NFS shares on it.  The other client computer gets a DHCP address from the server, internet and mounts NFS shares on the server.  
I have setup shorewall firewall on the server per this guide:
[http://www.shorewall.net/two-interface.htm](http://www.shorewall.net/two-interface.htm)

I have setup NFS shares on the server and they will not always mount from the client.  I have 3 shares.  All are in the fstab.  One will mount at bootup and the other two will give me
```
mount: RPC: Timed out
```

What im doing right now is after booting up i will have to run "mount -a" a few times to get the other two to mount.  Getting the same RPC error as before when they dont work.

There is a wireless connection between these computers, although i dont think that is the problem.  Once the shares are mounted they seem fast.

Im guessing this is a NFS bug, a problem with my firewall configuration (although i think if it was firewalled it would never work) and third i would suspect the wireless.

I am looking for a way to debug this.  I have noticed that there are a LARGE number of other threads on here relating to NFS and the "mount: RPC: Timed out" error.  I have spent a few hours reading them but can not find my exact problem.

Any help is appreciated.

---

### Post by 65 mustang on 2007-06-26
Client side /etc/fstab:
```
10.1.1.1:/media/ddrive/MP3s /mnt/MP3s nfs rsize=8192,wsize=8192,timeo=14,intr
10.1.1.1:/media/ddrive/Movies /mnt/Movies/1 nfs rsize=8192,wsize=8192,timeo=14,intr
10.1.1.1:/media/fdrive/Movies2 /mnt/Movies/2 nfs rsize=8192,wsize=8192,timeo=14,intr
```

Server side /etc/exports
```
/media/ddrive/MP3s 10.1.1.1/24(ro,async)
/media/ddrive/Movies 10.1.1.1/24(ro,async)
/media/fdrive/Movies2 10.1.1.1/24(ro,async)
```

---

### Post by 65 mustang on 2007-06-26
Server firewall configuration shorewall:

/etc/shorewall/interfaces
```
#ZONE   INTERFACE       BROADCAST       OPTIONS
net     eth0            detect          dhcp,tcpflags,norfc1918,routefilter,nosmurfs,logmartians
loc     eth1            detect          tcpflags,detectnets,nosmurfs

```

masq
```
#INTERFACE              SUBNET          ADDRESS         PROTO   PORT(S) IPSEC
eth0                    eth1

```

policy
```

#SOURCE         DEST            POLICY          LOG LEVEL       LIMIT:BURST

#
# Note about policies and logging:
#       This file contains an explicit policy for every combination of
#       zones defined in this sample.  This is solely for the purpose of
#       providing more specific messages in the logs.  This is not
#       necessary for correct operation of the firewall, but greatly
#       assists in diagnosing problems.
#

#
# Policies for traffic originating from the local LAN (loc)
#
# If you want to force clients to access the Internet via a proxy server
# on your firewall, change the loc to net policy to REJECT info.
loc             net             ACCEPT
loc             $FW             ACCEPT
loc             all             REJECT          info

#
# Policies for traffic originating from the firewall ($FW)
#
# If you want open access to the Internet from your firewall, change the
# $FW to net policy to ACCEPT and remove the 'info' LOG LEVEL.
# This may be useful if you run a proxy server on the firewall.
$FW             net             ACCEPT
$FW             loc             ACCEPT
$FW             all             REJECT          info

#
# Policies for traffic originating from the Internet zone (net)
#
net             $FW             DROP            info
net             loc             DROP            info
net             all             DROP            info

# THE FOLLOWING POLICY MUST BE LAST
all             all             REJECT          info

```

rules
```

#ACTION         SOURCE          DEST            PROTO   DEST    SOURCE          ORIGINAL        RATE            USER/
#                                                       PORT    PORT(S)         DEST            LIMIT           GROUP
#                                                               PORT    PORT(S) DEST                    LIMIT   GROUP
#
#       Accept DNS connections from the firewall to the network
#
DNS/ACCEPT      $FW             net
#
#       Accept SSH connections from the local network for administration
#
SSH/ACCEPT      loc             $FW
#
#       Allow Ping from the local network
#
Ping/ACCEPT     loc             $FW

#
# Reject Ping from the "bad" net zone.. and prevent your log from being flooded..
#

Ping/REJECT     net             $FW

ACCEPT          $FW             loc             icmp
ACCEPT          $FW             net             icmp
#

```

zones
```

#ZONE   TYPE    OPTIONS                 IN                      OUT
#                                       OPTIONS                 OPTIONS
fw      firewall
net     ipv4
loc     ipv4

```

---

### Post by 65 mustang on 2007-06-27
Bump

---

### Post by 65 mustang on 2007-06-27
Any ideas, anything?  Help....  ](*,)

---

### Post by virgiltibbs on 2007-07-17
im getting the same problem....
my tthread is here [http://ubuntuforums.org/showthread.php?t=477695](http://ubuntuforums.org/showthread.php?t=477695)
but i havent found the solution yet
EDIT: i can see you have answered this
> 
you tried messing with firewall?

---

