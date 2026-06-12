---
title: "Ubuntu VPN connection dropped unexpetedly"
date: 2017-09-18
forum: Networking &amp; Wireless
---

### Post by str34m on 2017-09-18
Hello!

I am using ubuntu 17.04 on my desktop mashine. It connects to FreeBSD vpn server through IPSec L2TP protocol. On my client mashine I use xl2tpd and strongswan.
I use the same MTU\MRU setting on my server-side and clients-side.
Everything works, until I trying to fetch videostream from client mashine. During a couple of seconds VPN connection drops without any log messages. 
When I trying do the same from FreeBSD client mashine - everything works fine. It seems, that some Ubuntu-like settings should be tuned.
Here is my Ubuntu VPN client config files

Strongswan config
```

# ipsec.conf - strongSwan IPsec configuration file
# basic configuration
config setup
# strictcrlpolicy=yes
# uniqueids = no
# Add connections here.
# Sample VPN connections
conn %default
        #ikelifetime=60m
        #keylife=20m
        #rekeymargin=3m
        #keyingtries=1
        #keyexchange=ikev1
        authby=secret
        ike=aes128-sha1-modp1024,3des-sha1-modp1024!
        esp=aes128-sha1-modp1024,3des-sha1-modp1024!
conn myvpn
        keyexchange=ikev1
        left=%defaultroute
        auto=add
        authby=secret
        type=transport
        leftprotoport=17/1701
        rightprotoport=17/1701
        right=1.2.3.4
        rightid=%any



```

xl2tpd config

```

[lac myvpn]
lns = 1.2.3.4
ppp debug = yes
pppoptfile = /etc/ppp/options.l2tpd.client
length bit = yes



```


ppp config

```

ipcp-accept-local
ipcp-accept-remote
refuse-eap
require-mschap-v2
noccp
nodeflate
noauth
idle 1800
mtu 1280
mru 1280
defaultroute
debug
connect-delay 5000
name user
password password



```

Also, ssh to client and from clientr mashine works fine and there is no firewall blocking rules

on Ubuntu in logs I have only

```

Sep 18 11:45:58 candy xl2tpd[29238]: control_finish: Connection closed to *, serial 1 ()
Sep 18 11:45:58 candy pppd[29241]: Modem hangup
Sep 18 11:45:58 candy pppd[29241]: Connect time 764.0 minutes.
Sep 18 11:45:58 candy pppd[29241]: Sent 4061783 bytes, received 3896879 bytes.
Sep 18 11:45:58 candy charon: 11[KNL] interface ppp1 deactivated
Sep 18 11:45:58 candy charon: 07[KNL] 172.16.1.2 disappeared from ppp1
Sep 18 11:45:58 candy pppd[29241]: Script /etc/ppp/ip-down started (pid 3811)
Sep 18 11:45:58 candy pppd[29241]: Connection terminated.
Sep 18 11:45:58 candy charon: 14[KNL] interface ppp1 deleted
Sep 18 11:45:58 candy avahi-daemon[430]: Withdrawing workstation service for ppp1.
Sep 18 11:45:58 candy pppd[29241]: Waiting for 1 child processes...
Sep 18 11:45:58 candy pppd[29241]:   script /etc/ppp/ip-down, pid 3811
Sep 18 11:45:58 candy pppd[29241]: Hangup (SIGHUP)
Sep 18 11:45:58 candy pppd[29241]: sending SIGTERM to process 3811
Sep 18 11:45:58 candy pppd[29241]: Exit.



```

What should I check?

---

### Post by str34m on 2017-09-19
Adding in xl2rpd config bps = 1000000 particaly soved. Now disconnect appear after 10 MB transfered... Keep searching

---

### Post by str34m on 2017-09-20
It seems like some QoS tuning needed.. Really stucked

---

