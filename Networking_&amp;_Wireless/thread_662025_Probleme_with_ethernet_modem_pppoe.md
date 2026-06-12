---
title: "Probleme with ethernet modem pppoe"
date: 2008-01-08
forum: Networking &amp; Wireless
---

### Post by tchaka on 2008-01-08
Hello,

I have an external Ethernet modem  Siemens Plus und I am using Ubuntu Gutsy.
I have a problem to establish connection to Internet. When I was on Feisty, I was no problem, everything was fine, but since I have installed Gutsy, the connection doesnt work.

I used pppoeconf to configure the pppoe connection. So a file in /etc.ppp/peers has been created.



```
1) sudo vi /etc/ppp/peers/dsl-provider

# Minimalistic default options file for DSL/PPPoE connections

noipdefault
defaultroute
replacedefaultroute
hide-password
#lcp-echo-interval 30
#lcp-echo-failure 4
noauth
persist
#mtu 1492
#persist
#maxfail 0
#holdoff 20

plugin rp-pppoe.so eth0
user "MyTelephonnumber@alice-dsl.de"
usepeerdns
```

Here is also my "chap-secrets" file:

```
2) sudo vi /etc/ppp/chap-secrets

# Secrets for authentication using CHAP
# client        server  secret                  IP addresses


"MyTelephonnumber@alice-dsl.de" * "" * 
```

Thus with these both files, the connection doesn't  work.

```
3) sudo pon dsl-provider
Plugin rp-pppoe.so loaded.
```

Actually there is appearently one problem with CHAP protocol:

```
4) sudo plog

Jan  7 22:40:49 thib-laptop pppd[5956]: Plugin rp-pppoe.so loaded.
Jan  7 22:40:49 thib-laptop pppd[5958]: pppd 2.4.4 started by root, uid 0
Jan  7 22:40:50 thib-laptop pppd[5958]: PPP session is 654
Jan  7 22:40:50 thib-laptop pppd[5958]: Using interface ppp0
Jan  7 22:40:50 thib-laptop pppd[5958]: Connect: ppp0 <--> eth0
Jan  7 22:40:50 thib-laptop pppd[5958]: **CHAP authentication failed: Request Denied**
Jan  7 22:40:50 thib-laptop pppd[5958]: **CHAP authentication failed**
Jan  7 22:40:50 thib-laptop pppd[5958]: Connection terminated.
```

and the "pap-secrets" file:

```

sudo vi /etc/ppp/pap-secrets

#
# /etc/ppp/pap-secrets
#
# This is a pap-secrets file to be used with the AUTO_PPP function of
# mgetty. mgetty-0.99 is preconfigured to startup pppd with the login option
# which will cause pppd to consult /etc/passwd (and /etc/shadow in turn)
# after a user has passed this file. Don't be disturbed therefore by the fact
# that this file defines logins with any password for users. /etc/passwd
# (again, /etc/shadow, too) will catch passwd mismatches.
#
# This file should block ALL users that should not be able to do AUTO_PPP.
# AUTO_PPP bypasses the usual login program so it's necessary to list all
# system userids with regular passwords here.
#
# ATTENTION: The definitions here can allow users to login without a
# password if you don't use the login option of pppd! The mgetty Debian
# package already provides this option; make sure you don't change that.

# INBOUND connections

# Every regular user can use PPP and has to use passwords from /etc/passwd
*       hostname        ""      *

# UserIDs that cannot use PPP at all. Check your /etc/passwd and add any
# other accounts that should not be able to use pppd!
guest   hostname        "*"     -
master  hostname        "*"     -
root    hostname        "*"     -
support hostname        "*"     -
stats   hostname        "*"     -

# OUTBOUND connections

# Here you should add your userid password to connect to your providers via
# PAP. The * means that the password is to be used for ANY host you connect
# to. Thus you do not have to worry about the foreign machine name. Just
# replace password with your password.
# If you have different providers with different passwords then you better
# remove the following line.

#       *       password


"MyTelephonnumber@alice-dsl.de" * "" 

```

Finally the file with the interfaces:

```
auto lo
iface lo inet loopback

auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual 
```

I have no idea why my connection is not working,  especially because on Windows the connection with the modem ethernet is working fine with WAN-Miniport (PPPoE).

Anyone has any idea?

Thanks for your help.

---

