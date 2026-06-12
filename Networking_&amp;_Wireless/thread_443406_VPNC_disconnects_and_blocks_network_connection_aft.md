---
title: "VPNC disconnects and blocks network connection after 15-20 minutes"
date: 2007-05-14
forum: Networking &amp; Wireless
---

### Post by hansdan on 2007-05-14
I have VPNC working fine but it disconnects after about 15-20 minutes regardless if the connection is idle or not. When that happens all network traffic is blocked.

If I run vpnc-disconnect it kills the process and after that my network works again. I can re-connect my VPN without problem. 

Does anyone have an ideas what this can be? Could it be the firewall I'm connecting to? It happens both at home and at work.

Cheers,

Hans

---

### Post by OrkanSpec on 2007-05-31
I had the same problem with vpnc in Dapper and Edgy. It is even worse in Feisty: it loses connection in a minute.
I think this is caused by firewall or Cisco concentrator configuration, as vpnc is working well for most of the people.

You can use the original client by Cisco: vpnclient-linux-4.8.00.0490-k9 for 32bit or vpnclient-linux-x86_64-4.8.00.0490-k9 for 64bit system. It connects without problems in Dapper and Edgy. There have been some kernel changes in Feisty, so vpnclient sources have to be modified before installation on this version.

Regards,

---

### Post by hansdan on 2007-07-08
I finally got around and tried this. It worked great.

Thanks

---

