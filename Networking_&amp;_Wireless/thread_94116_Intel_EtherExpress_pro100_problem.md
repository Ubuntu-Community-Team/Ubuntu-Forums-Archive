---
title: "Intel EtherExpress pro100 problem"
date: 2005-11-23
forum: Networking &amp; Wireless
---

### Post by ambo on 2005-11-23
Did a bit of a search on the forums to see if anyone else had the same problem as me - but it seems they haven't...

I have an onboard EtherExpress pro100 NIC and a clean install of Hoary 5.04.
The system appears to have detected the device - and the problem that some others mentioned of having 2 modules loaded for the one does not appear to be a problem on my system.
There is a link light on both the NIC and the hub and "sudo mii-tool" returns: "eth0: negotiated 100baseTx-FD flow-control, link ok"

However, the box was unable to connect to the DHCP to obtain a lease. So I set static IP, gw and DNS.
Despite this i cannot ping in or out and theres no sign of the box connecting to the internet gateway and it can't connect to any external resources.

Now this is where it really gets weird - i opened "Network Servers" and the firewall on my doz box began detecting samba packets coming in.
And yet "ifconfig eth0" indicates "RX packets:0..... TX packets:0"

This is my first Ubuntu installation - and i have no idea what is going on...

Any ideas??

---

