---
title: "IPSec tunnel with Strongswan using IKEv2 (PSK+EAP)"
date: 2014-04-15
forum: Networking &amp; Wireless
---

### Post by mariogar1001 on 2014-04-15
Hi all,

I'm trying to establish an IPSec tunnel from my virtualbox Ubuntu image to a SeGW.
I'm using preshared key to identify myself against SeGW, which is supposed to ask EAP autentication after this.

This is my ipsec.conf file:

```
conn connname
        esp=3des,sha1,modp1024
        left=%any
        leftauth=psk
        leftsendcert=never
        leftid=id@myid.com
        leftsourceip=%config4,%config6
        ike=3des,sha1,modp1024
        keyexchange=ikev2
        type=tunnel
        right=x.x.x.x
        rightauth=eap-md5
        auto=add
        forceencaps=yes
        mobike=no
        eap_identity=%any
```

I'm able to go through the first step (IKE_SA_INIT) but I'm stuck with IKE_AUTH.

The IKE_AUTH that I'm sending is something like this:
```
generating IKE_AUTH request 1 [ IDi N(INIT_CONTACT) IDr AUTH CPRQ(ADDR ADDR6 DNS DNS6) SA TSi TSr N(MOBIKE_SUP) N(NO_ADD_ADDR) N(EAP_ONLY) ]
```

For some reason, it is including the AUTH payload in IKE_AUTH package. Nevertheless, according to SeGW specification and [RFC 4306]("http://tools.ietf.org/html/rfc4306#section-2.16"), the AUTH payload sould be sent by the SeGW in EAP request.


Could you help me?

Thanks in advance.

---

### Post by ecdsa on 2014-04-24
> **mariogar1001 said:**
> 
I'm using preshared key to identify myself against SeGW, which is supposed to ask EAP autentication after this.


It's not possible to only authenticate the responder with EAP. Either both peers use EAP (with a mutual EAP method like EAP-TLS) or only the initiator uses EAP, while the responder uses a public-key-signature-based authentication. Using PSK authentication with EAP is therefore not [RFC 5996]("http://tools.ietf.org/html/rfc5996#section-2.16") compliant (it is supported by strongSwan, though - but only if the initiator authenticates with EAP).

> **mariogar1001 said:**
> 
The IKE_AUTH that I'm sending is something like this:
```
generating IKE_AUTH request 1 [ IDi N(INIT_CONTACT) IDr AUTH CPRQ(ADDR ADDR6 DNS DNS6) SA TSi TSr N(MOBIKE_SUP) N(NO_ADD_ADDR) N(EAP_ONLY) ]
```

For some reason, it is including the AUTH payload in IKE_AUTH package. Nevertheless, according to SeGW specification and [RFC 4306]("http://tools.ietf.org/html/rfc4306#section-2.16"), the AUTH payload sould be sent by the SeGW in EAP request.


This is absolutely correct. The initiator is configured to do PSK authentication (*leftauth=psk*) so an AUTH payload is included. As explained above it's not possible for only the responder to authenticate with EAP, as it's the initiator who has to demand the use of EAP, by not including an AUTH payload in the IKE_AUTH request.

If you want to use EAP authentication you either have to use a mutual method (like EAP-TLS, with both peers using a certificate - which is basically is the same as using certificates in the first place) or you decide on clear roles for each peer and then let the initiator authenticate with EAP (so in this case either reverse the authentication methods or let only the SeGW initiate the authentication).

---

### Post by mariogar1001 on 2014-04-30
Hi ecdsa,

First of all, thanks for your answer.

After several tries and after talking with people in charge of the SeGW, I realized that I was using a wrong IP in the right party.

I've made a few modifications to my ipsec.conf file and now it looks as follows:

```
conn connname
        left=x.x.x.x
        leftauth=eap-md5
        leftsendcert=never
        leftid=id@myid.com
        leftsourceip=%config4,%config6
        eap_identity=%any
        ike=3des,sha1,modp1024
        keyexchange=ikev2
        type=tunnel
        right=y.y.y.y
        rightauth=psk
        rightsubnet=0.0.0.0/0
        auto=add
        mobike=no
```

With this configuration, my first IKE_AUTH looks fine since it is not including the AUTH payload.
I receive a response from SeGW asking for EAP authentication and in logs I can see that PSK authentication was successfull.
I sent a new IKE_AUTH (request 2) including EAP_IDENTITY, but SeGW responds with AUTH_FAILED.

This is my log file:

```
initiating IKE_SA connname[1] to y.y.y.ygenerating IKE_SA_INIT request 0 [ SA KE No N(NATD_S_IP) N(NATD_D_IP) ]
sending packet: from x.x.x.x[500] to y.y.y.y[500] (768 bytes)
received packet: from y.y.y.y[500] to x.x.x.x[500] (300 bytes)
parsed IKE_SA_INIT response 0 [ SA KE No N(NATD_S_IP) N(NATD_D_IP) ]
local host is behind NAT, sending keep alives
establishing CHILD_SA connname
generating IKE_AUTH request 1 [ IDi N(INIT_CONTACT) IDr CPRQ(ADDR ADDR6 DNS DNS6) SA TSi TSr N(EAP_ONLY) ]
sending packet: from x.x.x.x[4500] to y.y.y.y[4500] (412 bytes)
received packet: from y.y.y.y[4500] to x.x.x.x[4500] (108 bytes)
parsed IKE_AUTH response 1 [ IDr AUTH EAP/REQ/ID ]
authentication of 'y.y.y.y' with pre-shared key successful
server requested EAP_IDENTITY (id 0x01), sending 'id@myid.com'
generating IKE_AUTH request 2 [ EAP/RES/ID ]
sending packet: from x.x.x.x[4500] to y.y.y.y[4500] (92 bytes)
received packet: from y.y.y.y[4500] to x.x.x.x[4500] (76 bytes)
parsed IKE_AUTH response 2 [ EAP/FAIL N(AUTH_FAILED) ]
received AUTHENTICATION_FAILED notify error
establishing connection 'connname' failed
```

Any idea?

Thanks in advance.

---

### Post by ecdsa on 2014-05-02
> **mariogar1001 said:**
> 
```

server requested EAP_IDENTITY (id 0x01), sending 'id@myid.com'
generating IKE_AUTH request 2 [ EAP/RES/ID ]
sending packet: from x.x.x.x[4500] to y.y.y.y[4500] (92 bytes)
received packet: from y.y.y.y[4500] to x.x.x.x[4500] (76 bytes)
parsed IKE_AUTH response 2 [ EAP/FAIL N(AUTH_FAILED) ]
```

Looks like the server doesn't like your EAP identity. Are you sure it's the same as the IKE identity (*leftid*)? Otherwise you might have to configure a different EAP identity with the *eap_identity* option.

---

### Post by mariogar1001 on 2014-05-05
> **ecdsa said:**
> Looks like the server doesn't like your EAP identity. Are you sure it's the same as the IKE identity (*leftid*)? Otherwise you might have to configure a different EAP identity with the *eap_identity* option.
You were right. I was using the same id for IKE and EAP, and it was wrong.
After setting my eap_identity and my EAP secret in ipsec.secrets I finally get the tunnel working on.


Thank you so much! =d>=d>=d>

```
root@ubuntu:/etc# ipsec up connname
initiating IKE_SA connname[1] to y.y.y.y
generating IKE_SA_INIT request 0 [ SA KE No N(NATD_S_IP) N(NATD_D_IP) ]
sending packet: from x.x.x.x[500] to y.y.y.y[500] (768 bytes)
received packet: from y.y.y.y[500] to x.x.x.x[500] (300 bytes)
parsed IKE_SA_INIT response 0 [ SA KE No N(NATD_S_IP) N(NATD_D_IP) ]
local host is behind NAT, sending keep alives
establishing CHILD_SA connname
generating IKE_AUTH request 1 [ IDi N(INIT_CONTACT) IDr CPRQ(ADDR ADDR6 DNS DNS6) SA TSi TSr N(EAP_ONLY) ]
sending packet: from x.x.x.x[4500] to y.y.y.y[4500] (412 bytes)
received packet: from y.y.y.y[4500] to x.x.x.x[4500] (108 bytes)
parsed IKE_AUTH response 1 [ IDr AUTH EAP/REQ/ID ]
authentication of 'y.y.y.y' with pre-shared key successful
server requested EAP_IDENTITY (id 0x01), sending 'eap-identity@id.com'
generating IKE_AUTH request 2 [ EAP/RES/ID ]
sending packet: from x.x.x.x[4500] to y.y.y.y[4500] (92 bytes)
received packet: from y.y.y.y[4500] to x.x.x.x[4500] (92 bytes)
parsed IKE_AUTH response 2 [ EAP/REQ/MD5 ]
server requested EAP_MD5 authentication (id 0x02)
generating IKE_AUTH request 3 [ EAP/RES/MD5 ]
sending packet: from x.x.x.x[4500] to y.y.y.y[4500] (84 bytes)
received packet: from y.y.y.y[4500] to x.x.x.x[4500] (68 bytes)
parsed IKE_AUTH response 3 [ EAP/SUCC ]
EAP method EAP_MD5 succeeded, no MSK established
authentication of 'left-id@id.com' (myself) with EAP
generating IKE_AUTH request 4 [ AUTH ]
sending packet: from x.x.x.x[4500] to y.y.y.y[4500] (84 bytes)
received packet: from y.y.y.y[4500] to x.x.x.x[4500] (204 bytes)
parsed IKE_AUTH response 4 [ AUTH CPRP(ADDR MASK DNS) SA TSi TSr ]
authentication of 'y.y.y.y' with EAP successful
IKE_SA connname[1] established between x.x.x.x[left-id@id.com]...y.y.y.y[y.y.y.y]
scheduling reauthentication in 10028s
maximum IKE_SA lifetime 10568s
handling INTERNAL_IP4_NETMASK attribute failed
installing DNS server dns.server via resolvconf
installing new virtual IP new.ip
connection 'connname' established successfully
```

---

