---
title: "Ubuntu DNS Setup for Smart DNS Proxy"
date: 2018-10-13
forum: Networking &amp; Wireless
---

### Post by rev4370 on 2018-10-13
I am using Ubuntu 18.4 and trying to config the DNS. Smart DNS Proxy (I have an account with them) has a help page but is seems to be out of date (Ubuntu 14. something). I have been on this for a long time, and read through many pages of fixes - but due to being a Newby I have come to a standstill. I have wireless connection through a HP Touchsmart tx2 laptop - going to use it for a Kodi setup on my TV. 

DNS Setup for Smart DNS Proxy is (Ubuntu 14. Something)

[http://support.smartdnsproxy.com/customer/portal/articles/1675839-ubuntu-dns-setup-for-smart-dns-proxy](http://support.smartdnsproxy.com/customer/portal/articles/1675839-ubuntu-dns-setup-for-smart-dns-proxy)

What I have done:-

In wireless connections I have 

- set in IVP4 DNS to 54.66.128.66,54.94.226.225 (closest to where I am)
- Disabled IPV6

Not sure what is going on - can someone please point me in a direction....

Thank you

---

### Post by wildmanne39 on 2018-10-13
*Thread moved to **Networking & Wireless for a more appropriate fit**.*

---

### Post by nixonrm on 2019-01-25
Dear Rev4370,

Disable IPV6. Under IPV4 settings leave Automatic (DCHP) selected.  Under DNS turn off automatic selection tab. Put in your closest IP's [COLOR=#000000]54.66.128.66,54.94.226.225 under DNS. Click apply. Restart. You should then be good to go. Best :)[/COLOR]

---

