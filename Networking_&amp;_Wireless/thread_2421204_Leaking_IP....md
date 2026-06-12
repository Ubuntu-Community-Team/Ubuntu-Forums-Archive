---
title: "Leaking IP..."
date: 2019-06-18
forum: Networking &amp; Wireless
---

### Post by easytorememberusername on 2019-06-18
So I got a problem with leaking IP that I can’t seem to fix in Ubuntu 18.04, or in fresh install of Ubuntu 19.04.
 Using a VPN and trying whatsmyip.com it has my country but different city, whatismyipaddress.com has both my city and country. A common theme observed is ipv6 seems to be the culprit, but despite changing media.peerconnection.enabled to false in firefox, disabling ipv6 in Ubuntu, and installing dnscrypt, these two websites still leak my IP. I read it best to do a fresh install to use dnscrypt, tried but no use. Cellphone don’t leak IP, says ipv6 not detected thats why thinking must be ipv6 related. Odd thing some IP leak test websites don’t reveal leak, others do.
 What more steps can I take to stop my real IP leaking?

---

### Post by crip720 on 2019-06-18
Just want to check on a few things, does your IP address changed with using VPN, when using VPN do you see your IP address you get from your ISP?  Can also check with 'ipleak.net'.  Is it a paid or free VPN?

---

### Post by easytorememberusername on 2019-06-18
Ipleak.net shows both my VPN assigned IP and my actual IP together. At the bottom of that page under IP details it has a really long IP which another IP checker had displayed under ipv6. I paid for the VPN.

---

