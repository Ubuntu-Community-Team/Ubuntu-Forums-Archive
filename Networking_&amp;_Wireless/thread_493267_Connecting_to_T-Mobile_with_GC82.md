---
title: "Connecting to T-Mobile with GC82"
date: 2007-07-05
forum: Networking &amp; Wireless
---

### Post by 4partee on 2007-07-05
Here is what is working for me.  I posted this with a GC82 and the 19.99 T-mobile Internet plan.

Two files:

#/etc/ppp/peers/gc82
# 
#
:10.10.10.10
hide-password 
noauth
connect "/usr/sbin/chat -v -f /etc/chatscripts/gc82"
debug
/dev/ttyS2
115200
defaultroute
noipdefault 
user ""
remotename gc82
ipparam gc82

usepeerdns

#prevent disconnects after 2 minutes
lcp-echo-failure 1
lcp-echo-interval 0



#/etc/chatscripts/gc82
SAY 'trying to connect...\n'
SAY '\n'

ABORT 'NO DIAL TONE' ABORT 'NO ANSWER' ABORT DELAYED

SAY 'Initializing modem\n'

#Must be done first to set GC82 to accept AT commands!
"" AT+cfun=1
OK AT+cfun=1
OK AT+cgreg=1
OK AT

"" AT+CSQ

SAY '\n'
SAY 'Setting APN\n'

# this context string came straight from t-mobile tier 3 tech support.
# The APN (internet2.voicestream.com) may be internet3 if your account is set
# up for public IP addresses.  Mine isn't, so here we are.
OK AT+CGDCONT=1,"IP","internet2.voicestream.com"

SAY '\n'
SAY 'Dialing...\n'

OK ATDT*99***1#
CONNECT " "

As root, run:
 poff;sleep 9;pon gc82; watch "route -n"

and you should see:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.10.10.10     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0

---

