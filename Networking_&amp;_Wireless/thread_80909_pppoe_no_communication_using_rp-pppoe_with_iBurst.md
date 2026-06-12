---
title: "pppoe no communication using rp-pppoe with iBurst"
date: 2005-10-23
forum: Networking &amp; Wireless
---

### Post by dubuntu on 2005-10-23
I installed rp-pppoe to get an iBurst connection going on 5.04 using a modem via eth0.  This is my pppoe.conf:
#***********************************************************************
## pppoe.conf
## Configuration file for rp-pppoe.  Edit as appropriate and install in
# /etc/ppp/pppoe.conf
## NOTE: This file is used by the pppoe-start, pppoe-stop, pppoe-connect and
#       pppoe-status shell scripts.  It is *not* used in any way by the
#       "pppoe" executable.
## Copyright (C) 2000 Roaring Penguin Software Inc.
## This file may be distributed under the terms of the GNU General
# Public License.
## LIC: GPL
# $Id: pppoe.conf,v 1.11 2005/08/09 02:49:12 dfsExp$
#***********************************************************************
# When you configure a variable, DO NOT leave spaces around the "=" sign.
# Ethernet card connected to DSL modemETH='eth0'
# PPPoE user name.  You may have to supply "@provider.com"  Sympatico
# users in Canada do need to include "@sympatico.ca"
# Sympatico uses PAP authentication.  Make sure /etc/ppp/pap-secrets
# contains the right username/password combination.
# For Magma, use [email]xxyyzz@magma.ca[/email]
USER='myname.mysurname@isp.co.za'
# Bring link up on demand?  Default is to leave link up all the time.
# If you want the link to come up on demand, set DEMAND to a number indicating
# the idle time after which the link is brought down.
DEMAND=no
# DEMAND=300
# DNS type: SERVER=obtain from server; SPECIFY=use DNS1 and DNS2;
# NOCHANGE=do not adjust.
DNSTYPE=SPECIFY
# DNSTYPE=NOCHANGE
# Obtain DNS server addresses from the peer (recent versions of pppd only)
# In old config files, this used to be called USEPEERDNS.  Changed to
# PEERDNS for better Red Hat compatibilityPEERDNS=no
# PEERDNS=yes
DNS1=196.30.31.193
DNS2=196.46.70.1
# Make the PPPoE connection your default route.  Set to
# DEFAULTROUTE=no if you don't want this.
DEFAULTROUTE=yes

This is what I get from pppoe-start and pppoe-status:
root@ubuntu:/home/davide # pppoe-start
. Connected!
root@ubuntu:/home/davide #
root@ubuntu:/home/davide # pppoe-status
pppoe-status: Link is up and running on interface ppp0
ppp0      Link encap:Point-to-Point Protocol
          inet addr:196.2.103.99  P-t-P:196.30.31.100  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1432  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:30 (30.0 b)  TX bytes:37 (37.0 b)
root@ubuntu:/home/davide #

This is my resolv.conf
nameserver 196.30.31.193
nameserver 196.46.70.1

I can't ping any address (not even using the IP address).

Anyone with suggestions, The same setup works on the same machine under windowsXP (using a dual boot system)??

---

### Post by Skrewdriver on 2005-10-26
Not sure exactly, but try changing DNSTYPE to SERVER

---

