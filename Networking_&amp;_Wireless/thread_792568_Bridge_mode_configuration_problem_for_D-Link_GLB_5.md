---
title: "Bridge mode configuration problem for D-Link GLB 502T"
date: 2008-05-13
forum: Networking &amp; Wireless
---

### Post by madhusudancs on 2008-05-13
Hi all, 
        I am on Hardy Heron 32-bit version. Its a fresh install. I have broadband connection which I have configured in PPPoE mode. And my modem/router is D-Link GLB-502T. Off late I am not getting good speeds in torrents even after port forwarding the port Azureus uses. Port check on that port says its open but still I am not getting good speeds. So I thought of using bridge mode. I just set the bridge mode in my modem's WAN page and when I run 
```
sudo pppoeconf
```
it says 

Sorry, I scanned 1 interface, but the Access Concentrator of your provider did not respond. Please check your network and modem cables. Another reason for the scan failure may also be another running pppoe process which controls the modem. 

Please help me. Thanks in advance.

---

### Post by adityakavoor on 2008-05-13
You are running the wrong command.

try this

```
 sudo pppoeconf
```

---

### Post by madhusudancs on 2008-05-13
**** sorry typo. Thanks for that. Have changed it.

---

### Post by adityakavoor on 2008-06-01
CONFIGURE THE ROUTER FOR BRIDGE CONNECTION.

1. Access the web configuration of the router through a web browser

WITH 192.168.1.1 IN ADRESS BAR PUT USER NAME -admin PASSWORD- admin


2. Click on Setup - New Connection.

3. Specify a name to the connection. -> dataone.

4. NAT and Firewall are checked.

5. Select the type as bridge, and disable sharing.

6. In the PVC settings, verify the following :
PVC - New
VPI - 0
VCI - 35
QoS - UBR.

7. Click on Apply.

8. Click on Tools - System Commands - Save All, followed by Restart.

---

### Post by madhusudancs on 2008-06-01
> **adityakavoor said:**
> CONFIGURE THE ROUTER FOR BRIDGE CONNECTION.

1. Access the web configuration of the router through a web browser

WITH 192.168.1.1 IN ADRESS BAR PUT USER NAME -admin PASSWORD- admin


2. Click on Setup - New Connection.

3. Specify a name to the connection. -> dataone.

4. NAT and Firewall are checked.

5. Select the type as bridge, and disable sharing.

6. In the PVC settings, verify the following :
PVC - New
VPI - 0
VCI - 35
QoS - UBR.

7. Click on Apply.

8. Click on Tools - System Commands - Save All, followed by Restart.

Hey this is what I have done as this guide is present elsewhere on the internet. This is all ok and common to all modems/routers but its failing at pppoeconf as I have said above. You have probably got my question wrong. pppoeconf says no access concentrator. What to do? Please help

Thanks for the reply

---

