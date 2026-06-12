---
title: "new kernel new wireless problem"
date: 2005-05-27
forum: Networking &amp; Wireless
---

### Post by stepore on 2005-05-27
sorry for posting this in 2 sections, but since it's a networking and laptop issue i wasn't sure what was the proper forum? what's the proper etiquette on multi-posting across multiple sections in this forum?

i've got a netgear WG511 that was working great with Prism54 and WEP until this morning.

last night i ran apt-get update and upgrade and it upgraded a few things plus a latest kernel upgrade to 2.6.10-5-386. not sure what the upgrade was, exactly. it seems like i was using the 2.6.10-5-386 for quite a while now, but i know for certain that it was upgraded using the security repository. i saw it upgrading and setting up the new kernel.

anyway after rebooting this morning it no longer recognizes eth1. during boot, it comes up as eth1 failed and couldn't connect to ntpdate. i've tried /etc/init.d/network restart and tried playing around with the settings in /etc/networking/interfaces, but nothing works.

i've had to go back to kernel 2.6.8.1-4-386 during boot. which is where i am now posting this.

does anyone know what's happened with the kernel upgrade, and how i can get the card to work and the system to recognize eth1?

---

