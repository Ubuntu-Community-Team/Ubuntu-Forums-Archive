---
title: "Ubuntu Server, VMWare port redirection"
date: 2008-08-01
forum: Networking &amp; Wireless
---

### Post by toetagtw on 2008-08-01
We are currently in the process of dumping windows.  However, we intensively use DNN currently for website hosting.  The server currently being used for windows and DNN hosting is becoming unstable.

A plan of action is to setup vmware on the Ubuntu server and load an image of a clean windows server with the DNN sites.  Is there a way to "redirect" the ubuntu port to the hosted images port 80?

Or can anyone suggest a better course of action?

---

### Post by superprash2003 on 2008-08-01
yes possible through iptables.. but if you configure vmware to bridged/NAT then you could forward the traffic from the router itself, as then windows would get its own unique ip..

---

### Post by toetagtw on 2008-08-01
The vmware Image can't be given it's own IP.  The ubuntu server will have the only public IP address.

Using iptables will i need to use something like rinetd?

---

