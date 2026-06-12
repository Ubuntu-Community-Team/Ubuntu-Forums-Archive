---
title: "Two VM's behind NAT"
date: 2014-09-07
forum: Networking &amp; Wireless
---

### Post by bewareofthephog on 2014-09-07
I have two VM's running.  One server running OpenVPN and the other is Ubuntu.  I'd like to test that I can connect to OpenVPN from Ubuntu but both of these VM's are behind NAT which is leaving me confused.  I've setup port forwarding rules to both of them so I can SSH but I can't seem to SSH from one VM to the other since they both have the same IP's (at least that's what I'm guessing)

Any help is appreciated!

---

### Post by Tadaen_Sylvermane on 2014-09-07
Need to know what software you are using to run the vms. If virtualbox then change from nat networking to bridged ( will put on your lan ) or internal network ( will create mini lan between the 2 vms ). They shouldn't have the same ip. To get the ip just sudo ifconfig.

---

