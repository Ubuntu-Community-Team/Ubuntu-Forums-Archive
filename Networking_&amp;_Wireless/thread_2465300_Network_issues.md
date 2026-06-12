---
title: "Network issues"
date: 2021-07-29
forum: Networking &amp; Wireless
---

### Post by dinohrnd on 2021-07-29
Network issues.
 
Hello, we have a problem on ubuntu 18.4 if anyone has the idea please.
Ubuntus 18.4 VM in vmware which has two network card: one in the DMZ and one in the local network, the server can be reached from the internet from the DMZ card IP by port forwarding and can be reached from the local network from the other network card. The problem is after a while the server is no longer reachable and you have to restart.
thank you in advance for your help .

---

### Post by TheFu on 2021-07-29
What do the log files say?
What troubleshooting have you already done?
Has the switch been ruled out? How?
Has the router been ruled out? How?
Has the cable been ruled out? How?
Has the software config been ruled out? How?
Has the NIC hardware been ruled out? How?
Are both halves of the NIC affected? 
Has VMware been ruled out? How?   BTW, VMware makes 6 different virtual machine products. Which is involved would really help someone knowledgeable to respond.

Any chance either the hypervisor or VM is going into standby mode?

Hard to help without basic information.  The answers to the questions above AND basic information - driver, settings, routing, firewalls, ... stuff that any network admin would know.

---

