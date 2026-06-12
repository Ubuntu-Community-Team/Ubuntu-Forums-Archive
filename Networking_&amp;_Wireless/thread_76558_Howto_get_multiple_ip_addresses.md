---
title: "Howto get multiple ip addresses"
date: 2005-10-15
forum: Networking &amp; Wireless
---

### Post by Apreche on 2005-10-15
I've got an ubuntu server currently running hoary. I am using etherconf to manage it's sing static ip address. I want to add more ip addresses to it in the fashion of eth1:0 eth1:1, etc. 

How do I do this in Ubuntu with etherconf? I know how to do it in non-debian distros. Thanks

---

### Post by f-bomb on 2005-10-15
you can always use ifconfig, then change the network startup scripts

> sudo ifconfig eth1:1 192.168.1.5

i believe that's the correct command off the top of my head.  someone correct me if i'm wrong

---

### Post by Apreche on 2005-10-15
I know that. I'm wondering exactly how to change the scripts. And how to change them properly under etherconf. What syntax to use and which files to edit.

---

