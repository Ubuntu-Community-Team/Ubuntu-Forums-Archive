---
title: "Cannot share Wireless through Ethernet connection anymore after 17.04 install"
date: 2017-04-27
forum: Networking &amp; Wireless
---

### Post by sortengel on 2017-04-27
In Ubuntu 16.04 and 16.10 it worked sharing my wifi through ethernet. In  network manager and changed the IPv4 Settings tab, Method: "Shared to  other computers" 
After upgrading to 17.04 it stopped working, so did a clean install, but  still not able to share. My ethernet (wired) connection just turns  itself off. 
Anyone have a solution?

---

### Post by gorgooger on 2017-08-23
Well from [https://askubuntu.com/questions/909318/cannot-share-my-ethernet-connection-anymore-after-17-04-install](https://askubuntu.com/questions/909318/cannot-share-my-ethernet-connection-anymore-after-17-04-install) I learned that it is "just" a missing dependency
sudo apt-get install dnsmasq-base
should do the trick

---

