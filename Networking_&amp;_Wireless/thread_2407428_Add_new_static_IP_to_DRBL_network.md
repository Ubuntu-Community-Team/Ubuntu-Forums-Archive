---
title: "Add new static IP to DRBL network"
date: 2018-12-04
forum: Networking &amp; Wireless
---

### Post by aldo3 on 2018-12-04
Greetings Users,

I am quite new to setting up a more complex network so I am asking some help from you. I got a small cluster, configured with a master node with Ub 16.04 installed, which is handling few slave nodes through DRBL in headless mode (i.e. the OS is not copied onto the nodes). Now I would like to add to the cluster a NAS unit, for which ideally I would like to give a static IP address, and then add the corresponding line to fstab. My question then is: how can I add the static IP address to the master node so that it is associated with the NAS when I hook it up to the switch?

Thank you in advance,

Aldo

---

### Post by mitesh.agrwl on 2018-12-04
[Check this thread]("https://unix.stackexchange.com/questions/281484/nas-share-not-mounting-on-linux-boot-through-etc-fstab"), here it has been suggested to edit /etc/fstab file to add the static IP of NAS so it can mount automatically when network is enabled. Please check other options mentioned there according to your need. the details of the options can be found in 'man mount'.

---

### Post by aldo3 on 2018-12-05
Thank you for the answer. Actually I found out that I do not need to change anything on the master: I was guessing that the server needed to be configured in order to assign the same address requested from the nas unit, but the solution is much simpler. I just set the correct IP on the new unit and everything was fine.

---

