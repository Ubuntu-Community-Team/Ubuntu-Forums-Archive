---
title: "Shrew Soft VPN Client L2TP/IPSEC"
date: 2016-06-07
forum: Networking &amp; Wireless
---

### Post by nethompson on 2016-06-07
I'm having trouble connecting to my Ubuntu VPN server with Shrew Soft on Ubuntu. I can connect to my server with my Android phone all day long. I'm able to get connected with the IPSEC side of Shrew Soft but not xl2tp. Can anyone help me with getting connected to the L2TP side of my server? I've attached my server config files to the post.

_options.xl2tp_

```

ipcp-accept-local
ipcp-accept-remote
require-mschap-v2
ms-dns 192.168.2.1
mtu 1200
mru 1200
asyncmap 0
auth
crtscts
lock
hide-password
modem
debug
name server
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
login

```


_IPSEC.SECRETS_

```

# This file holds shared secrets or RSA private keys for inter-Pluto
# authentication.  See ipsec_pluto(8) manpage, and HTML documentation.

# RSA private key for this host, authenticating it to any other host
# which knows the public part.  Suitable public keys, for ipsec.conf, DNS,
# or configuration of other implementations, can be extracted conveniently
# with "ipsec showhostkey".

# this file is managed with debconf and will contain the automatically created RSA keys
include /var/lib/openswan/ipsec.secrets.inc
192.168.2.1    %any:    PSK "1234"

```


[U]IPSEC.CONF

[/U]```

version    2.0

config setup
    dumpdir=/var/run/pluto/
    nat_traversal=yes
    virtual_private=%v4:192.168.0.0/16,%v6:fd00::/8,%v6:fe80::/10
    oe=off
    protostack=netkey
    force_keepalive=yes
    keep_alive=60

conn L2TP-PSK-NAT
    rightsubnet=vhost:%priv
    also=L2TP-PSK-noNAT

conn L2TP-PSK-noNAT
      authby=secret
      pfs=no
      auto=add
      keyingtries=3
      ikelifetime=8h
      keylife=1h
      type=transport
      left=192.168.2.1
      leftprotoport=17/1701
      right=%any
      rightprotoport=17/%any
      dpddelay=10
      dpdtimeout=20
      dpdaction=clear

```

_xl2tpd.conf_

```

 [global]
ipsec saref = yes
saref refinfo = 30

 [lns default]
ip range = 12.0.1.10-12.0.1.15
local ip = 12.0.1.1
refuse pap = yes
refuse chap = yes
require authentication = yes
pppoptfile = /etc/ppp/options.xl2tp
length bit = yes      

```

---

### Post by nethompson on 2016-06-08
Anyone...? Bump...?

---

### Post by nethompson on 2016-06-15
Bump

---

