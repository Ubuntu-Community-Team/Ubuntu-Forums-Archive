---
title: "How do I tunnel mms traffic through ssh ?"
date: 2006-08-13
forum: Networking &amp; Wireless
---

### Post by mosaic on 2006-08-13
Hello,

I had to reboot to windows cause I am trying to tunnel mms streaming (microsoft media services?) through ssh, but having problems to establish connection. (another question - any idea how to watch mms streaming under ubuntu?)

What I have found out, there are at least 2 dst ports in use: 554 and 1755. Source ports are changing everytime I try to connect.

- I sit in "LAN" which denies communication to these dst ports.
- But I can access my outside machine with ssh server, so there is no problem to make a tunnel outside the LAN through SSH.
- So what I do need is to tunnel mms traffic to my outside server which would hopefully forward it to the destination mms server and then back to my computer in "LAN".
- In MS windows media player I could configure proxy or socks settings.

Does anybody have an idea how to set up the ssh tunnel to allow this traffic ?

I have tried setting up the ssh tunnel with D5555 forwarding and Win Media player with socks setting 127.0.0.1:5555 for mms traffic. So I think all mms traffic from WMP should be forwarded to 127.0.0.0:5555 which should then forward it to my outside ssh server right ? But how do I reach the final mms destination server ?

I would appreciate any ideas!!

Thanks

mosaic

---

