---
title: "Ethernet not working"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by Dawei87 on 2008-11-26
I have been having trouble connecting to encrypted routers wirelessly, so i have been connecting with an ethernet cable instead. It has been woking fine and all of a sudden when I connect the cable wicd cannot pick up the newtork. I have not changed any settings and lshw -C network still says all my adapters are claimed and working fine. Can anyone help?

---

### Post by Dawei87 on 2008-11-26
OK. With a quick adjustment I can now see the network, but it won't obtain an IP address, so I still can't connect. Does anyone know whats up?

---

### Post by prshah on 2008-11-26
> **Dawei87 said:**
> OK. With a quick adjustment I can now see the network, but it won't obtain an IP address, so I still can't connect.

Open a terminal (Applications-Accessories-Terminal) and post back the output of the following commands, which will act as both additional information as well as a possible diagnostic```
sudo mii-tool eth0
sudo dhclient eth0
ifconfig eth0

```

Replace eth0 with the actual network device alias.

---

### Post by Dawei87 on 2008-11-26
When I run the command sudo mii-tool eth0, it comes back "SIOCGMIIPHY on 'eth0' failed: Operation not supported"
When I run the command sudo dhclient eth0, it comes back at the end
"No DHCPOFFERS received.
No working leases in persistent database - sleeping."
When I run the command ifconfig etho, it comes back
"etho     Link encap:Ethernet   HWaddr nn:nn:nn:nn:nn
          UP BROADCAST MULTICAST   MTU:1500   Metric:1
          RX packets:258 errors:0 dropped:431613275574 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:22264 (22.2 KB)   TX bytes:0 (0.0 B)
          Interrupt:252"

---

### Post by prshah on 2008-11-26
> **Dawei87 said:**
> 
sudo mii-tool eth0, it comes back "SIOCGMIIPHY on 'eth0' failed: Operation not supported"

Try ```

sudo ethtool eth0
```

---

