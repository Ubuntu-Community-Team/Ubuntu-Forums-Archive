---
title: "connecting a name to a webserver"
date: 2007-09-29
forum: Networking &amp; Wireless
---

### Post by cbrands on 2007-09-29
I have an apache webserver installed on one computer and succesfully conected to it from another computer on the same network by typing de ip address in the browser. So far so good.

The webserver is not and will never be accessible from outside the local network.

I would like to give the webserver a name so that I can type myserver in the browser instead of 192.168.0.2.

How do I do this :confused:

---

### Post by NickFury on 2007-09-29
Its all about the /etc/hosts file.

do a:

```
 bash#> sudo nano /etc/hosts 
```

in the terminal and edit away.

just do <IP> then <hostname> , save it and your done.


this is all assuming your web server is on a static IP, otherwise if your IP for your webserver changes, you will have to re-edit the /etc/hosts file again.

---

### Post by cbrands on 2007-09-29
Thanks for your answer.
The problem is that the ip adresses are not static. The ip's are handed out by the router using DHCP. So the adresses could be different the next time the network is started up.
Is there a way to make the ubuntu machines detect each other names or ip's?

---

### Post by Treebeard on 2007-09-29
If possible, you could setup your router/dhcp server to always allocate same IP address to your PC running the webserver, based on the MAC address.
Most basic routers have this feature..

---

