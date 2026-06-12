---
title: "Reconfig Networking Support in Kernel - INET_ESP and so on.."
date: 2006-11-02
forum: Networking &amp; Wireless
---

### Post by VPNR on 2006-11-02
Hi

I am trying to setup IPsec using Ubuntu with the native IPsec and user-space tools, racoon and setkey.

Does anyone know if the below networking options are enabled by defualt in Ubuntu DD. If not, how do I enable them? If I need to reconfig the kernel, how do i do this.

Thanks.

Paul
VPNR
  
  PF_KEY sockets (NET_KEY) [
  IP: AH transformation (INET_AH) 
  IP: ESP transformation (INET_ESP) 
  IP: IPsec user configuration interface (XFRM_USER) 

Cryptographic API (CRYPTO) 
  HMAC support (CRYPTO_HMAC) 
  Null algorithms (CRYPTO_NULL) 
  MD5 digest algorithm (CRYPTO_MD5) 
  SHA1 digest algorithm (CRYPTO_SHA1) 
  DES and Triple DES EDE cipher algorithms (CRYPTO_DES)  y
  AES cipher algorithms (CRYPTO_AES) [Y/n/m/?] y

---

