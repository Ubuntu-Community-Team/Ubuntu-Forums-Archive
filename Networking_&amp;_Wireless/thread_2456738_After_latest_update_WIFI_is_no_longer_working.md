---
title: "After latest update WIFI is no longer working"
date: 2021-01-18
forum: Networking &amp; Wireless
---

### Post by stevep12 on 2021-01-18
I updated via Live Update a couple weeks ago and after rebooting there was no WIFI, nor was it listed in Settings. I use Timeshift so I just reverted to before the update and everything works as expected. I hoped there was an issue with that update and waited a couple weeks and today, prompted by Live Update, I decided to try it again, and got the same results, no WIFI. 

In the Software & Updates app, under the Additional Drivers tab is shows the proprietary Broadcom 802.11 Linux STA wireless driver source from bcmwl-kernel-source is being used. 

I have used the following troubleshooting guide to no avail: [https://www.maketecheasier.com/fix-wi-fi-not-working-ubuntu/](https://www.maketecheasier.com/fix-wi-fi-not-working-ubuntu/)

I am running Ubuntu 20.04.1 on a Mid-2012 Macbook Pro 13 which uses the Broadcom 4331 WIFI controller. 

If anybody has an idea on how to solve this problem it would be greatly appreciated! I am heading off to work now so I will not be able to respond for a few hours so don't think I'm ignoring your help, I'll be back!

Thank you

Edit for more details:

Running "sudo lshw -C network" in the terminal gives the following response: 

  *-network
       description: Network controller
       product: BCM4331 802.11a/b/g/n
       vendor: Broadcom Inc. and subsidiaries
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:17 memory:a0600000-a0603fff

---

### Post by CelticWarrior on 2021-01-18
Welcome.

[https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by stevep12 on 2021-01-18
> **CelticWarrior said:**
> Welcome.

[https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

I actually tried that one earlier before I posted my above question and it didn't work, upon going through it a second time on your advice I noticed something I missed the first time:

> And then reboot.

LOL

Thank you for your reply, it is likely I wouldn't have found my mistake had you not posted!

---

