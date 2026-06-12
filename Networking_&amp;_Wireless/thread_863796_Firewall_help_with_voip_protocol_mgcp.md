---
title: "Firewall help with voip protocol mgcp"
date: 2008-07-18
forum: Networking &amp; Wireless
---

### Post by supergumby on 2008-07-18
Hi everyone,

Here is my setup, I use my laptop (hardy) to share internet on my network, this part works fine. My problem is I can't get my Dlink dvg-1120 voip gateway to connect to primustel servers. (This also works fine when I'm on my windows xp partition and using nat32e to route traffic, voip works) I believe I might miss something in my firewall setup, I've opened port 2427 as primus recommend ( [http://www.dslreports.com/faq/primustbb/2._INSTALLATION#12357](http://www.dslreports.com/faq/primustbb/2._INSTALLATION#12357) ), I'm monitoring network activity with Etherape and Wireshark and I can see the requests coming on port 2427 using mgcp protocol but it doesn't seem to go thru... I've attached my iptables if someone wanna have a look. My voip gateway is ending with 200 and the ones starting with 216 are primus servers. Any suggestions, ideas will be appreciated! Thanks.

---

