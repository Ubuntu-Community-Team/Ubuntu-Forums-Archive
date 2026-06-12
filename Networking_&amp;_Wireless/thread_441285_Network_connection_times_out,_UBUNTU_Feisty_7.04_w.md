---
title: "Network connection times out, UBUNTU Feisty 7.04 with VMWARE 6.0.0 build 45731"
date: 2007-05-12
forum: Networking &amp; Wireless
---

### Post by kRoNnos on 2007-05-12
I'm having some problems with UBUNTU Feisty 7.04 and VMware 6. I did a fresh installation of UBUNTU Feisty 7.04, installed the latest vmware tools and everything worked fine. After a while i noticed that i was loosing connectivity to the internet.

The problem seems to happen when the vm is on an idle state and only the interface that is configured with dhcp (int that goes to the internet) seems to be affected. The problem gets resolved by restarting the networking services. If i leave an extended ping running on the background and leave there is no problem, seems to be only when there is no activity. I have another interface configured with static ip and no problems at all.

I'm wondering if this is something related to ubuntu itself, vmware6 or something i'm doing wrong. If someone has heard about this please let me know.

Thanks.

---

