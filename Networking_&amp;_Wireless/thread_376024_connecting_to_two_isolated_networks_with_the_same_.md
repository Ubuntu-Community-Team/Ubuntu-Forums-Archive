---
title: "connecting to two isolated networks with the same server with two nics"
date: 2007-03-04
forum: Networking &amp; Wireless
---

### Post by pr0f1t on 2007-03-04
Greetings All,   

                      I am loosing my mind trying to figure out what is wrong with my setup. I have a 6.06LTS box with two nic's installed. One nic is up and working with a static address from my private address space (10.0.0.X) and this interface can talk to the rest of the machines in this address space, as well as pass traffc out the NAT gateway to the internet. The second nic is configured with a routable static ip from my /29 subnet provided by my isp (xxx.xxx.xxx.240/29) This is where things go to pot. The subnet is provided through a L2 adsl bridge connected to a hub. The nic on the ubuntu server is also connected to this hub. I can talk to the ubuntu box from other machines in my subnet(.240/29) on this hub, but cannot talk to my gateway or the internet. I assumed that this was a missing default route but when I add one things get worse and the nic shows up with an autoconfig 169.254 ip. I am so very confused. This works fine on another machine running windows server 2003.

---

### Post by pr0f1t on 2007-03-04
perhaps I should begin in a different way. I have a 6.06 machine with two network interfaces. One of them(eth0) is on my private network and acts as internal dns among other things so it needs to be reachable locally on my private range. There is also a second network interface(eth1) and it has been assigned a public routable address from a /29 subnet I have with my non PPPoE adsl service. If I turn on eth1 I loose connectivity to eth0 from the private network. I have found others with the same problem but I have yet to find anything that would explain it. Can someone shed some light here? I am happy to post my routing tables and ifconfig info if this will help. Any assistance would be greatl;y appreciated.

---

