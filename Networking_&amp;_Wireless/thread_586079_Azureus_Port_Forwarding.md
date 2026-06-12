---
title: "Azureus Port Forwarding"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by Redscare on 2007-10-21
So I was trying to get Azureus set up today, and I got through the installation but cannot get ports ot work. I have successfully made a static IP as 192.168.x.xxx (x's are for privacy). I then forwarded port 51463 in my Netgear WGR614v5 router, and in Firestarter I added an inbound policy on port 51463 for everyone. I then use this port in Azureus and get this error in the test tool:
```
Testing port 51463 ... 
NAT Error - Connect attempt to xx.xx.xx.168:51463 (your computer) timed out after 20 seconds. This means your port is probably closed. 
```
Please note that the last 3 numbers of that IP ( 168 ) do not match the last three numbers of my static IP. Please tell me what I am doing wrong. Thank you in advance.

---

### Post by Redscare on 2007-10-22
Sorry for the bump, but this question seems relatively simple and I need a reply as soon as possible. Thanks again.

---

### Post by Redscare on 2007-10-22
fixed it...had to power off then power on teh router.

---

