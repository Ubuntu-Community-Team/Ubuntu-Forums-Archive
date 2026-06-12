---
title: "Bionic cloud OVA image not sending traffic"
date: 2018-05-29
forum: Networking &amp; Wireless
---

### Post by kingttx2 on 2018-05-29
We are using VMware Integrated OpenStack, so I'm trying to set up a Bionic image for our users. 

I have problems with cloud-init growpart and resizefs showing disabled, so I've turned to the official cloud OVA image. 

When I spin up a new instance, the OS is not sending any traffic. The security group is wide open. I do see eth0 was renamed to ens190 but either the instance is hanging at the BTRFS message or it is switching to console redirect and I don't see anything else. 

Ultimately, I cannot tell if the instance is simply not booting or it is booting but not sending traffic. What should I look for?

---

