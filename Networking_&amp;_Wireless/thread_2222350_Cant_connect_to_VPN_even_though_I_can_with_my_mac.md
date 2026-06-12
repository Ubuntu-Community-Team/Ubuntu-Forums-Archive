---
title: "Cant connect to VPN even though I can with my mac"
date: 2014-05-06
forum: Networking &amp; Wireless
---

### Post by pellefantus on 2014-05-06
Hello,

We have a VPN connection at work setup from where people with OSX have got it to work. But I cant get it to work on ubuntu Ubuntu  12.04.4 LTS.

On OSX the settings that work are: Server: 123.123.123.123, accountname: pelle, password: pwd_pelle, with a shared key: pwd_group (and empty group name). [as a cisco vpn tunnel]

This is my /etc/ipsec.conf
```
# /etc/ipsec.conf - Openswan IPsec configuration file
# $Id$

# Manual: ipsec.conf(5)

# Created: Tue Mar 25 09:08:06 2014
#      by: The L2TP IPsec VPN Manager application version 1.0.6
#
# WARNING! All changes made in this file will be lost!

version    2.0    # conforms to second version of ipsec.conf specification

config setup
    # plutodebug="parsing emitting control private"
    plutodebug=none
    strictcrlpolicy=no
    nat_traversal=yes
    interfaces=%defaultroute
    oe=off
    # which IPsec stack to use. netkey,klips,mast,auto or none
    protostack=netkey

conn %default
    keyingtries=3
    pfs=no
    rekey=yes
    type=transport
    left=%defaultroute
    leftprotoport=17/1701
    rightprotoport=17/1701

# Add connections here.


conn Work
  leftid=@VPN_Group_2
  leftxauthusername=pelle
    left=%defaultroute
    right=123.123.123.123
  keyexchange=ike
  auto=start
  auth=esp
  authby=secret
  ikelifetime=28800s
  esp=3des-sha1;modp1024
  ike=3des-sha1,aes128-sha1;modp1024
  pfs=yes
  compress=no
  forceencaps=yes
  remote_peer_type=cisco
  rightxauthserver=yes
```

And this is my ipsec.secrets
```
# /etc/ipsec.secrets - secrets for IKE/IPsec authentication
# $Id$

# Manual: ipsec.secrets(5)

# Created: Tue Mar 25 09:08:06 2014
#      by: The L2TP IPsec VPN Manager application version 1.0.6
#
# WARNING! All changes made in this file will be lost!
#
#
# This file holds shared secrets or RSA private keys for inter-Pluto
# authentication.  See ipsec_pluto(8) manpage, and HTML documentation.

# RSA private key for this host, authenticating it to any other host
# which knows the public part.  Suitable public keys, for ipsec.conf, DNS,
# or configuration of other implementations, can be extracted conveniently
# with "ipsec showhostkey".
#
%any : PSK "pwd_group" 
@pelle : XAUTH "pwd_pelle" 


```


I get this while connecting:
```

root at pc:~# ipsec auto --add Work
root at pc:~# ipsec auto --up Work
104 "Work" #4: STATE_MAIN_I1: initiate
003 "Work" #4: received Vendor ID payload [RFC 3947] method set to=109 
003 "Work" #4: received Vendor ID payload [Dead Peer Detection]
003 "Work" #4: ignoring unknown Vendor ID payload [8299031757a36082c6a621de000500b3]
106 "Work" #4: STATE_MAIN_I2: sent MI2, expecting MR2
003 "Work" #4: NAT-Traversal: Result using RFC 3947 (NAT-Traversal): both are NATed
108 "Work" #4: STATE_MAIN_I3: sent MI3, expecting MR3
010 "Work" #4: STATE_MAIN_I3: retransmission; will wait 20s for response
010 "Work" #4: STATE_MAIN_I3: retransmission; will wait 40s for response
031  "Work" #4: max number of retransmissions (2) reached STATE_MAIN_I3.    Possible authentication failure: no acceptable response to our first   encrypted message
000 "Work" #4: starting keying attempt 2 of at most 3, but releasing whack


```

And these are the settings in the fortigate 111c web-UI as seen from the people who set up the tunnel.

at this URL:
[http://i.imgur.com/BKSyvRg.jpg](http://i.imgur.com/BKSyvRg.jpg)

Note: using vpnc with cisco vpn does not work either. My settings are:
root at pc:~# cat /etc/vpnc/myvpn.conf 
```
IPSec gateway  123.123.123.123
IPSec secret pwd_group
IKE Authmode psk
Xauth username pelle
Xauth password pwd_pelle
Debug 200
IKE DH Group dh2

```

---

### Post by spynappels on 2014-05-19
Is this a standard Cisco VPN?

If it is, you could try using the Cisco VPN plugin for Network Manager.

---

### Post by pellefantus on 2014-05-22
Hi, I tried with cisco, but it also fails, and its not a standard cisco vpn, but a fortigate "special"

---

