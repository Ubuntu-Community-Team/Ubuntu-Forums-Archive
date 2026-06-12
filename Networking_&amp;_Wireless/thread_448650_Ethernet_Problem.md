---
title: "Ethernet Problem"
date: 2007-05-19
forum: Networking &amp; Wireless
---

### Post by adilfulara on 2007-05-19
Hi. I have a dell latitude d620. I use wired internet. It all worked fine when i installed 6.06.
Ever since i have upgraded to 6.10, i cannot access the internet. The network properties seem to be fine as there is an IP address assigned to my machine but i just cannot access any website. The wireless seems to be working fine.

Any pointers on how to go about getting back to normal usage on ubuntu... ? i hate coming back to windows now especially after i am getting used to the beryl effects on ubuntu. 

Thank You,

Adil

---

### Post by alastair on 2007-05-19
So - wired internet not working but wireless OK?

What is the output of the shell commands :

ifconfig -a
route -n

Plus :

cat /etc/network/interfaces

This is a wired link to ...? A DSL modem/router? ISP gateway?
Describe the network layout a bit.

---

