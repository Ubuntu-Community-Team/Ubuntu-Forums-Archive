---
title: "Looking for a HowTo on bridged firewall"
date: 2007-07-30
forum: Networking &amp; Wireless
---

### Post by jeff7360 on 2007-07-30
I'm looking for a How-To on building an invisible firewall. I want to monitor traffic via snort on a firewall thats bridged to make the device invisible. I want to set up a honeypot/test system. Can anyone point me in the right direction?

---

### Post by PaulFr on 2007-07-31
Have you looked at **[https://help.ubuntu.com/community/NetworkMonitoringBridge](https://help.ubuntu.com/community/NetworkMonitoringBridge)** ?

---

### Post by jeff7360 on 2007-07-31
That article is very informative, but I would like the bridged firewall to have no IP address. Completely untouchable unless you have a physical connection to the machine itself. (IE monitor,keyboard,mouse hooked up to the device) {unless i am reading the guide incorrectly, which could very likely be true.}

---

### Post by t4thfavor on 2007-07-31
If you read up on bridging more, you will find a way to do exactly that. I don't remember how it works, but I once set up an ap so that you had to physically console into it in order to manage it. It was running the same principal. (I think it was like a layer 2 link instead of a layer 3 link meaning the br0 interface had no ip address.)

---

### Post by jeff7360 on 2007-07-31
Exactly! I have been reading around. The bridge is configured with no IP. I just have no clue how to set it up that way. I'll keep looking. If anyone can point me in the direction of the information please do!

---

### Post by PaulFr on 2007-08-01
What you want is the following:```
sudo apt-get update
sudo apt-get install bridge-utils

sudo ifconfig eth0 0.0.0.0
sudo ifconfig eth1 0.0.0.0
...
sudo ifconfig ethn 0.0.0.0

sudo brctl addbr bridge0

sudo brctl addif bridge0 eth0
sudo brctl addif bridge0 eth1 
...
sudo brctl addif bridge0 ethn

sudo ifconfig bridge0 up
```Replace eth0,eth1..ethn with your interface names (look through **ifconfig** output or **/var/log/messages** to find your interface names). More details at: **[http://linux-net.osdl.org/index.php/Bridge](http://linux-net.osdl.org/index.php/Bridge)** and **[http://www.tldp.org/HOWTO/BRIDGE-STP-HOWTO/set-up-the-bridge.html](http://www.tldp.org/HOWTO/BRIDGE-STP-HOWTO/set-up-the-bridge.html)**

---

### Post by jeff7360 on 2007-08-01
Sweet, Thanks! After cross referencing the ubuntu network monitoring bridge guide and another how-to i was getting close. But was unsure if it would work. Thanks again! I'm going to set one up and post back what happens.

---

