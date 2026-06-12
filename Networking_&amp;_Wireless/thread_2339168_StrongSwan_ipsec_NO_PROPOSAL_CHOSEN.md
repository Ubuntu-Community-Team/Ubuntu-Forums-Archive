---
title: "StrongSwan ipsec NO_PROPOSAL_CHOSEN"
date: 2016-10-05
forum: Networking &amp; Wireless
---

### Post by wyrkos on 2016-10-05
Hi


It has a problem with the connection between the vpn ipsec strongswan and Cisco vpn gateway.


Does anyone know what the problem might be? I tried to set up a connection already with two different hosts. Since my partner on the right side I have information that the phase 1 start properly. The problem occurs with phase 2. On the device is running dozens of other connections ipsec. On my website host is peer. Interface eth0 is set to an external address. On my side there's no NAT, all firewalls disabled. We have tried all sorts of encryption, hashing and groups pfs, psk certainly agree because the phase 1 start properly


When trying to connect I still have a problem:


```

ipsec up plus
initiating Main Mode IKE_SA plus[3] to yyy.yyy.yyy.yyy
generating ID_PROT request 0 [ SA V V V V ]
sending packet: from xxx.xxx.xxx.xxx[500] to yyy.yyy.yyy.yyy[500] (228 bytes)
received packet: from yyy.yyy.yyy.yyy[500] to xxx.xxx.xxx.xxx[500] (108 bytes)
parsed ID_PROT response 0 [ SA V ]
received NAT-T (RFC 3947) vendor ID
generating ID_PROT request 0 [ KE No NAT-D NAT-D ]
sending packet: from xxx.xxx.xxx.xxx[500] to yyy.yyy.yyy.yyy[500] (308 bytes)
received packet: from yyy.yyy.yyy.yyy[500] to xxx.xxx.xxx.xxx[500] (368 bytes)
parsed ID_PROT response 0 [ KE No V V V V NAT-D NAT-D ]
received Cisco Unity vendor ID
received DPD vendor ID
received unknown vendor ID: a5:02:d6:33:67:9c:f2:89:91:08:80:93:36:7d:01:ab
received XAuth vendor ID
generating ID_PROT request 0 [ ID HASH N(INITIAL_CONTACT) ]
sending packet: from xxx.xxx.xxx.xxx[500] to yyy.yyy.yyy.yyy[500] (108 bytes)
received packet: from yyy.yyy.yyy.yyy[500] to xxx.xxx.xxx.xxx[500] (76 bytes)
parsed ID_PROT response 0 [ ID HASH ]
IKE_SA plus[3] established between xxx.xxx.xxx.xxx[xxx.xxx.xxx.xxx]...yyy.yyy.yyy.yyy[yyy.yyy.yyy.yyy]
scheduling reauthentication in 85809s
maximum IKE_SA lifetime 86349s
generating QUICK_MODE request 1917731353 [ HASH SA No KE ID ID ]
sending packet: from xxx.xxx.xxx.xxx[500] to yyy.yyy.yyy.yyy[500] (380 bytes)
received packet: from yyy.yyy.yyy.yyy[500] to xxx.xxx.xxx.xxx[500] (92 bytes)
parsed INFORMATIONAL_V1 request 2124355898 [ HASH N(NO_PROP) ]
received NO_PROPOSAL_CHOSEN error notify
establishing connection 'plus' failed

```


my ipsec.conf


```



# ipsec.conf - strongSwan IPsec configuration file


# basic configuration


config setup
    # strictcrlpolicy=yes
    # uniqueids = no


# Add connections here.


# Sample VPN connections


conn plus
    type=tunnel
    leftauth=psk
    rightauth=psk
    ike=3des-md5;modp1024
    esp=3des-md5;modp1024!
    left=xxx.xxx.xxx.xxx
    leftsubnet=xxx.xxx.xxx.xxx/32
    right=yyy.yyy.yyy.yyy
    rightsubnet=zzz.zzz.zzz.zzz/32
    auto=start
    keyingtries=999
    keyexchange=ikev1
    ikelifetime=86400
    keylife=3600
    compress=no


    

```


My ipsec.secrets


```
    


# This file holds shared secrets or RSA private keys for authentication.


# RSA private key for this host, authenticating it to any other host
# which knows the public part.  Suitable public keys, for ipsec.conf, DNS,
# or configuration of other implementations, can be extracted conveniently
# with "ipsec showhostkey".


yyy.yyy.yyy.yyy xxx.xxx.xxx.xxx : PSK "my psk"

```


ipsec statusall


```

ipsec statusall
Status of IKE charon daemon (strongSwan 5.3.5, Linux 4.4.0-22-generic, x86_64):
  uptime: 3 minutes, since Oct 05 09:26:10 2016
  malloc: sbrk 2568192, mmap 0, used 360384, free 2207808
  worker threads: 10 of 16 idle, 6/0/0/0 working, job queue: 0/0/0/0, scheduled: 1
  loaded plugins: charon test-vectors aes rc2 sha1 sha2 md4 md5 random nonce x509 revocation constraints pubkey pkcs1 pkcs7 pkcs8 pkcs12 pgp dnskey sshkey pem openssl fips-prf gmp agent xcbc hmac gcm attr kernel-netlink resolve socket-default connmark stroke updown
Listening IP addresses:
  xxx.xxx.xxx.xxx
  2a01:4f8:172:31a3::2
  192.168.10.11
  192.168.56.1
Connections:
        plus:  xxx.xxx.xxx.xxx...yyy.yyy.yyy.yyy  IKEv1
        plus:   local:  [xxx.xxx.xxx.xxx] uses pre-shared key authentication
        plus:   remote: [yyy.yyy.yyy.yyy] uses pre-shared key authentication
        plus:   child:  xxx.xxx.xxx.xxx/32 === zzz.zzz.zzz.zzz/32 TUNNEL
Security Associations (0 up, 1 connecting):
        plus[1]: CONNECTING, xxx.xxx.xxx.xxx[%any]...yyy.yyy.yyy.yyy[%any]
        plus[1]: IKEv1 SPIs: 6fe3e9edaf9a3c4c_i* 0000000000000000_r
        plus[1]: Tasks queued: QUICK_MODE QUICK_MODE
        plus[1]: Tasks active: ISAKMP_VENDOR ISAKMP_CERT_PRE MAIN_MODE ISAKMP_CERT_POST ISAKMP_NATD

```

cisco config


edit


```



crypto isakmp key "my psk" address xxx.xxx.xxx.xxx
!
crypto isakmp peer address xxx.xxx.xxx.xxx
!
ip access-list extended ipsec-12110


permit ip host zzz.zzz.zzz.zzz host xxx.xxx.xxx.xxx
!
crypto map internet 12110 ipsec-isakmp
  description ****     *** 
  set peer xxx.xxx.xxx.xxx
  set transform-set plus-3des-md5
  set pfs group2
  match address ipsec-12110
  reverse-route static
exit
router static
address-family ipv4 unicast
xxx.xxx.xxx.xxx/32 yyy.yyy.yyy.yyy description ipsec-12110
 
 
Phase 1 (isakmp)
Protection suite
encryption algorithm:   Three key triple DES
hash algorithm:        Message Digest 5
authentication method:  Pre-Shared Key
Diffie-Hellman group:   #2 (1024 bit)
lifetime:               86400 seconds, no volume limit


Phase 2 (ipsec)
encryption algorithm:   Three key triple DES
hash algorithm:        Message Digest 5
PFS - Diffie-Hellman group:   #2 (1024 bit)
Security association lifetime: 4608000 kilobytes/3600 seconds

```

Edit

The problem solved disabling pfs in phase 2 on the right side

---

