---
title: "use pkcs12 with network-manager-openvpn"
date: 2007-03-30
forum: Networking &amp; Wireless
---

### Post by Daferra on 2007-03-30
Hi Guys,

I have a working pkcs12 certificate for openvpn what i can start from the command-line perfectly. No i want to control that with network-manager-openvpn, only the require an "ca file" "certificate"  and a "key"... So i read some post on converting "extracting" and so one...

--------------------------------------------------------------------------------------------------------
-- convert pkcs#12 -> private key & certificate (PEM) --

> openssl pkcs12 -in client.p12 -out client.pem
  -> from a single pkcs12 file, extract CA cert, client cert and private key
     to a single PEM file

> openssl pkcs12 -in client.p12 -out client.crt -clcerts -nokeys
  -> from a single pkcs12 file, extract client cert to client.cer.
     (no private key or CA cert)

> openssl pkcs12 -in client.p12 -out client.key -nocerts
  -> from a single pkcs12 file, extract client private key to client.key
     (no certs)
--------------------------------------------------------------------------------------------------------

So this is sure not the one i need to do, is there somebody that can tel me the write  openssl commands and the use within network-manager-openvpn.

Greets
Daferra

---

