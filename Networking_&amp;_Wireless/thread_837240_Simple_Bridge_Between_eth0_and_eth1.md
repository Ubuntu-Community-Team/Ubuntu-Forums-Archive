---
title: "Simple Bridge Between eth0 and eth1"
date: 2008-06-22
forum: Networking &amp; Wireless
---

### Post by ProgenitorVirus on 2008-06-22
I've downloaded bridge-utils on my new 64-bit system, and have read up on how to utilize the program!

I just installed Ubuntu around 1 AM Last night, and everything is up, except that one last thing.

Could anybody give me step-by-step directions to how to make a bridge between eth0 and eth1?

Thank you!!

---

### Post by kevdog on 2008-06-22
Some like this from the command line: Of course it could be modified to go into the /etc/network/interfaces file as well:


sudo brctl addbr br0
sudo brctl addif br0 eth0
sudo brctl addif br0 eth1
sudo ifconfig eth0 0.0.0.0 promisc
sudo ifconfig eth1 0.0.0.0 promisc
sudo dhclient br0

(if you require a static IP on the bridge address the last line would be this:
sudo ifconfig br0 192.168.0.4  <--Use appropriate IP address as this is an example
)

You may also need to set a gateway:
sudo route add default gw 192.168.0.1  <--Use appropriate IP address here.

---

