---
title: "BLOCKING PORTS IN Ubuntu Server"
date: 2011-07-13
forum: New to Ubuntu
---

### Post by sunil@redhat on 2011-07-13
Please suggest ..:(
how many option to  block ports in ubuntu server while
it has only command line support. 

i will be very thankful for any support......

---

### Post by mcduck on 2011-07-13
I'd recommend UFW, the included firewall configuration tool.

[https://help.ubuntu.com/community/UFW]("https://help.ubuntu.com/community/UFW")

---

### Post by 3rdalbum on 2011-07-13
I'm a bit confused. Ubuntu Server only listens to ports that correspond to server processes that you are running. For instance, if you only have Apache installed, then your computer will only be listening to port 80. If you use a firewall to block port 80, then nothing will be able to request data from Apache and your server will be useless.

If you know that your server is listening to an incoming port, and you want the program to remain on your server and listening to that port but not be able to receive any data from any other computers... then use UFW to block the port. Otherwise, either remove the process that is listening, or configure it to stop listening.

---

### Post by Dangertux on 2011-07-13
For server implentation I would skip UFW entirely and edit iptables directly. 

A lot more options, many of which are useful in a server environment. Just my 2 cents.

---

