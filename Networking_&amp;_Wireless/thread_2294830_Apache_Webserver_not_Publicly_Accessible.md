---
title: "Apache Webserver not Publicly Accessible"
date: 2015-09-13
forum: Networking &amp; Wireless
---

### Post by Maxattax97 on 2015-09-13
I am trying to setup a simple web server, and have installed a LAMP package to get started. I have a simple index.php page setup that provides current server stats. I am able to access it internally from my network (192.168.1.200), but am unable to access it from my network's public IP address (71.46.83.4) despite forwarding port 80 on my router.

I have tried configuring my listening ports in [FONT=lucida console]apache2.conf[/FONT], which is set to [FONT=lucida console]Listen 80[/FONT]. I've also tried setting up my iptables, although I feel that's not doing anything since they are all open by default (at least I think). My iptables are as follows:
```

[FONT=lucida console]Chain INPUT (policy ACCEPT)
target  prot opt source      destination
ACCEPT  tcp  --  anywhere    anywhere    tcp dpt:http
ACCEPT  all  --  anywhere    anywhere    ctstate RELATED,ESTABLISHED
ACCEPT  tcp  --  anywhere    anywhere    tcp dpt:ssh

Chain FORWARD (policy ACCEPT)
[FONT=lucida console]target  prot opt source      destination
[/FONT]
Chain OUTPUT (policy ACCEPT)
[/FONT][FONT=lucida console]target  prot opt source      destination[/FONT]

```

I am a Linux Novice. I would be happy to provide debug information. Thanks in advance!

---

### Post by SeijiSensei on 2015-09-13
Try forwarding a different port, say 8080, back to the server's port 80 and see if that works better.  Some ISPs block inbound traffic on port 80 to enforce their "no-servers" policy which is common on residential connections.

---

### Post by Maxattax97 on 2015-09-13
> Try forwarding a different port, say 8080, back to the server's port 80  and see if that works better.  Some ISPs block inbound traffic on port  80 to enforce their "no-servers" policy which is common on residential  connections.
I set Apache to listen on port 8080, altered my iptables to include port 8080, and included the port on my router (forgot to mention I had already added them both, [80, 8080]), and now it responds to intranet requests with an FTP-like interface when requesting on port 80. When I give the browser the URL 192.168.1.200:8080 it responds as expected; with the proper web page. However, still no dice with external requests, on both 71.46.83.4:8080 and 71.46.83.4:80.

---

### Post by Maxattax97 on 2015-09-16
I've finally gotten to the bottom of this and the answer is that with the information provided, I did everything right.
  The catch was that my network is funky. My router is linked to a  modem, as most networks probably are. However, my modem doubles as a  router. What had happened was all of the ports were being blocked by my  "modem". I forwarded all of the ports on my modem to my actual router,  and things are running just fine now. I've also fixed a lot of other  problems related to this.
Thanks for trying to help, I really appreciate it.

---

