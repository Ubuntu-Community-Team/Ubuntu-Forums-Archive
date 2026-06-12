---
title: "VPN, Strongswan"
date: 2014-09-26
forum: Networking &amp; Wireless
---

### Post by dorsey_eric on 2014-09-26
Help a noob please. I'm attempting to setup a vpn connection with Strongswan (IPsec is required) and each try to connect, a popup says the connection failed because the vpn service unexpectically stops. Below is the syslog output.  I've attempted to find what error 66 is but no luck so far. Any Ideas

   Sep 26 15:40:06 server NetworkManager[544]: <info> Starting VPN service 'strongswan'... 
 Sep 26 15:40:06 server NetworkManager[544]: <info> VPN service 'strongswan' started (org.freedesktop.NetworkManager.strongswan), PID 2200 
 Sep 26 15:40:06 server charon: 00[DMN] Starting IKE charon daemon (strongSwan 5.2.0, Linux 3.5.0-54-generic, x86_64) 
 Sep 26 15:40:06 server charon: 00[CFG] loading ca certificates from '/usr/local/etc/ipsec.d/cacerts' 
 Sep 26 15:40:06 server charon: 00[CFG] loading aa certificates from '/usr/local/etc/ipsec.d/aacerts' 
 Sep 26 15:40:06 server charon: 00[CFG] loading ocsp signer certificates from '/usr/local/etc/ipsec.d/ocspcerts' 
 Sep 26 15:40:06 server charon: 00[CFG] loading attribute certificates from '/usr/local/etc/ipsec.d/acerts' 
 Sep 26 15:40:06 server charon: 00[CFG] loading crls from '/usr/local/etc/ipsec.d/crls' 
 Sep 26 15:40:06 server charon: 00[CFG] loading secrets from '/usr/local/etc/ipsec.secrets' 
 Sep 26 15:40:06 server charon: 00[CFG]   loaded RSA private key from '/usr/local/etc/ipsec.d/private/myKey.der' 
 Sep 26 15:40:06 server charon: 00[LIB] loaded plugins: charon aes des rc2 sha1 sha2 md5 random nonce x509 revocation constraints pubkey pkcs1 pkcs7 pkcs8 pkcs12 pgp dnskey sshkey pem fips-prf gmp xcbc cmac hmac attr kernel-netlink resolve socket-default stroke updown xauth-generic 
 Sep 26 15:40:06 server charon: 00[LIB] unable to load 6 plugin features (6 due to unmet dependencies) 
 Sep 26 15:40:06 server charon: 00[DMN] charon already running ("/var/run/charon.pid" exists) 
 Sep 26 15:40:06 server NetworkManager[544]: <warn> VPN service 'strongswan' exited with error: 66 
 Sep 26 15:40:06 server NetworkManager[544]: <info> Policy set 'ethernet' (eth0) as default for IPv4 routing and DNS. 

thanks!

---

