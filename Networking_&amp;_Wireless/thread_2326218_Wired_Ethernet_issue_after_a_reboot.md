---
title: "Wired Ethernet issue after a reboot"
date: 2016-05-29
forum: Networking &amp; Wireless
---

### Post by 3-gary-0 on 2016-05-29
Hi,

I have an issue that I am having a difficult time figuring out. I am running 16.04 on a System76 Oryx pro, whenever I reboot the machine the wired Ethernet card gets stuck in a "connecting" state if set to DHCP and will not obtain an IP. If a static IP is applied and I reboot, NetworkManager will show the Wired as connected but it can not ping anything other than itself. If I do a full shut-down when the machine is started back up all is well. I can repeat this at will all I need to do is reboot instead of shutdown.

When it is in this state, I have attempted to kill NetworkManager and restart NM. Tried different ports on differet switches all with the same result. However after a full shutdown and power on everything is back to working.

When set to dhcp, I can see that the unit does send DHCP requests to the DHCP server, the server sees the request and offers a DHCP offer, however it is never received by the oryx. If the wired interface is set to static the oryx continually sends out arp request for the gateway and never gets an answer. If a ping is attempted, the oryx only sends arp requests for the IP address to ping, the end station does attempt to answer the request but the oryx never sees it. It appears the oryx can not build an arp table, arp -a shows only incomplete entries.

Below is some info that may/may-not be helpful...

lspci for the network controllers..

```
02:00.1 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 12)
03:00.0 Network controller: Intel Corporation Wireless 8260 (rev 3a)
```

ifconfig for the wired interface.
```
enp2s0f1  Link encap:Ethernet  HWaddr aa:aa:aa:aa:aa:aa  
          inet addr:1.1.1.99  Bcast:1.1.1.255  Mask:255.255.255.0
          inet6 addr: fe80::aaaa:aaaa:aaaa:aaaa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1067 errors:0 dropped:141 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:53205 (53.2 KB)
```

I am not sure of next steps to take, as if I simply shutdown and start things function correctly.

Thank you in advance for any assistance!

---

### Post by houstonbofh on 2016-05-30
What happens if you disable and enable networking in NM?

---

### Post by 3-gary-0 on 2016-05-31
If I kill or stop NM and start NM the issue remains until I do a complete shutdown of the machine.

---

### Post by houstonbofh on 2016-05-31
In this case, I would try and get support from System76, both on the website and in the system76 section on this forum.  It sounds like an issue they can fix easily.

---

