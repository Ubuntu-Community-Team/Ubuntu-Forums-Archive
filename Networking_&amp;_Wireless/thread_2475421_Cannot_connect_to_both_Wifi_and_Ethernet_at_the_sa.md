---
title: "Cannot connect to both Wifi and Ethernet at the same time"
date: 2022-05-26
forum: Networking &amp; Wireless
---

### Post by rotycha on 2022-05-26
Hello, I am farily new to using Ubuntu.  I have three pc's running it, and on one of them I am unable to connect to both wifi and Ethernet at the same time.  I need to be able to becuase I am running a cloudflared tunnel out of it and it needs to connect to both the cloudflare web servers and my local instance of grafana.   I am eventually able to run the tunnel when I disconnect from wifi while I wait for the tunnel to be set up and than reconnect to access grafana.  This is obviously not a very good long term solution however because it needs to to be able to restart on its own if it ever power cycles.

---

### Post by frm77000 on 2022-05-27
Hi Rotycha

We need to understant if this is a layer 2 probem or layer 3.
once connected with 2 interfaces you have to manage DNS, local routes and default route with cauton.

use ethtool and iwlist to get your interfaces status and send us content of your resolv.con, resolvevtl and ip route show.

Regards

---

