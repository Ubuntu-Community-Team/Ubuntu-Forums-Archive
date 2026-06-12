---
title: "ath0 and eth1"
date: 2007-09-30
forum: Networking &amp; Wireless
---

### Post by cmnorton on 2007-09-30
Since upgrading to Feisty, when my system boots, initially my system has no dns connectivity -- ubuntuforums.org -- but can ping a wan address outside my wireless router. My eth1 is a Linksys card configured to talk to my linksys wireless router. The ath0 interface always stays unconfigured but in roaming mode. 

Yesterday, I fixed it with something I could not repeat today; that is disabling a wired eth0 interface I was not using. This morning, I went into /etc/network/interfaces -- after making a copy -- and removed all interfaces I was not using. Then I got my connectivity back, evidenced by writing this post.

1) What is the relationship between ath0 and eth1? I know ath0 has to do with a chipset -- my Acer laptop has it, but ath0 itself is asking to be configured.

2) Even after saving a working interface in System->Administration->Networks Home, the next time I reboot, I am likely to have this problem -- no initial connectivity, and

3) What can I do about it?

Wired eth0 connectivy is no problem when I get to work. I basically disable the wireless device, because I don't use it in that environment.

Any thoughts or pointers to appropriate posts would be appreciated.

---

### Post by conjur3r on 2007-09-30
Your first paragraph shouts out DNS problems.  The file you should be looking at and monitoring is **/etc/resolv.conf**

Take a copy of this file after it is working ok, and have a look at it again when it's not working.  This file is populated with DNS servers as provided in an automatic DHCP network setup.

At work, our DLink router's DNS translation was poor at the best so these settings were overridden with the ISP's DNS servers.  No problems since.

1) Probably no relationship.  ATHx is usually a NIC using the Atheros chipset.

3) As a last ditch effort, you can disable any Atheros kernel modules from loading up which will effectively disable it.  But you shouldn't need to do this.

---

