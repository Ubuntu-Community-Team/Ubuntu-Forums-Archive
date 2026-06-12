---
title: "Ubuntu 15.04 L2TP Client VPN"
date: 2015-07-11
forum: Networking &amp; Wireless
---

### Post by Ashish Meena on 2015-07-11
Hi,

I have been trying to connect to VPN server of my company using Ubuntu 15.04. I have come to understand that it can be done using strongswan and xl2tpd. I have tried various methods described over websites but nothing has worked so far. Here is what I have done

    Install strongswan, xl2tpd

    Here goes my ipsec.conf

    config setup
    virtual_private=%v4:10.0.0.0/8,%v4:192.168.0.0/16,%v4:172.16.0.0/12
    nat_traversal=yes

    conn L2TP-PSK
    authby=secret
    pfs=no
    auto=add
    keyexchange=ikev1
    keyingtries=3
    dpdaction=clear
    rekey=no
    type=transport
    left=192.168.43.39
    leftnexthop=%defaultroute
    leftprotoport=17/%any
    (have also tried leftprotoport=17/1701 but no luck)
    right=IPOFVPNSERVER
    rightprotoport=17/1701

    Here goes my /etc/ipsec.secrets

    192.168.43.39 IPOFVPNSERVER : PSK "SHAREDKEY"

    Here goes my /etc/xl2tpd.conf

    [global]
    debug avp = no
    debug network = no
    debug packet = no
    debug state = no
    debug tunnel = no

    [lac vpn-connection]
    lns = IPOFVPNSERVER
    ppp debug = yes
    pppoptfile = /etc/ppp/options.l2tpd.client
    length bit = yes

    Here goes my /etc/ppp/options.l2tpd.client

    ipcp-accept-local
    ipcp-accept-remote
    refuse-eap
    require-pap
    noccp
    nodefaultroute
    idle 1800
    mtu 1410
    mru 1410
    defaultroute
    usepeerdns
    debug
    lock
    connect-delay 5000
    name MYUSERID
    password MYPASSWORD

    Here is how I try to connect

    systemctl restart strongswan
    systemctl restart xl2tpd
    ipsec up L2TP-PSK

    On Doing this connection fails and I see this error at VPN server END (Meraki)

    msg: phase1 negotiation failed.
    msg: failed to pre-process ph1 packet (side: 1, status 1).
    msg: failed to get valid proposal.
    msg: no suitable proposal found.
    msg: invalid life duration.

Any of on this is greatly appreciated.

---

