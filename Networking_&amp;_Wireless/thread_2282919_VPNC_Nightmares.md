---
title: "VPNC Nightmares"
date: 2015-06-17
forum: Networking &amp; Wireless
---

### Post by luke_3 on 2015-06-17
So I have been trying on and off for 2 months to get my VPNC clients working on ubuntu, but no such luck. I run a Ipsec Xauth VPN server for around 30 clients. OSX, Windows, iOS and Android all connect fine, however trying to connect ubuntu is not working.

So here is the VPNC configuration exported by the VPN server (and the config file Windows machine use)

```

n:version:2 
s:network-host:000.000.000.000 
n:network-ike-port:500 
s:client-auto-mode:pull 
s:client-iface:virtual 
n:client-addr-auto:1 
n:network-mtu-size:1380 
s:network-natt-mode:enable 
n:network-natt-port:4500 
n:network-natt-rate:20 
s:network-frag-mode:disable 
n:network-dpd-enable:1 
n:network-notify-enable:1 
n:client-banner-enable:0 
n:client-wins-used:1 
n:client-wins-auto:1 
n:client-dns-used:1 
n:client-dns-auto:1 
n:client-splitdns-used:1 
n:client-splitdns-auto:1 
s:auth-method:mutual-psk-xauth 
b:auth-mutual-psk:PSKGOESHERE 
s:ident-client-type:ufqdn 
s:ident-client-data:IpsecVPN 
s:ident-server-type:any 
s:phase1-exchange:aggressive 
s:phase1-cipher:3des 
s:phase1-hash:sha1 
n:phase1-dhgroup:1 
n:phase1-life-secs:86400 
n:vendor-chkpt-enable:0 
s:phase2-transform:esp-aes 
n:phase2-keylen:256 
s:phase2-hmac:sha1 
n:phase2-pfsgroup:1 
n:phase2-life-secs:28800 
n:phase2-life-kbytes:128000 
s:ipcomp-transform:disabled 
s:policy-level:auto 
n:policy-nailed:0 
n:policy-list-auto:1

```

And here is my vpnc.conf
```

IPSec gateway 000.000.000.000
IPSec ID IpsecVPN
IPSec secret PSKHERE
IKE Authmode psk
Xauth username luke
Xauth password PASSWORD

```

I first tried connecting with

```

luke@xps:~$ sudo vpnc --local-port 0
vpnc: xauth SET message rejected:  (ISAKMP_N_INVALID_PAYLOAD_TYPE)(1)

```
Debug logs: [https://gist.github.com/crooksey/8efa6e90550b62062498](https://gist.github.com/crooksey/8efa6e90550b62062498)


If have added a full debug print for both above commands to my post (using external gist link as to large to attach), I would really appreciate please help me as this is driving me crazy!

---

