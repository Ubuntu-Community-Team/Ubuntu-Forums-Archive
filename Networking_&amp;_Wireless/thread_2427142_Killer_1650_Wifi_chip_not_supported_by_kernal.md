---
title: "Killer 1650 Wifi chip not supported by kernal"
date: 2019-09-18
forum: Networking &amp; Wireless
---

### Post by makitso on 2019-09-18
Have a 2019 Dell XPS 15 that has a Killer 1650 Wireless-AC adapter.  Running with Ubuntu Budgie 19.04, the kernel does not support his adapter and I need to build it manually and copy to the /lib/firmware/ folder.

I would assume that the 2019 XPS 13 that Dell sells with Ubuntu installed has the same driver.  So, why doesn't the kernel support this wifi hardware?

---

### Post by uRock on 2019-09-18
Do the steps listed here for 16.04 work for your system? [https://support.killernetworking.com/knowledge-base/installing-the-killer-1535-1525-1435-in-ubuntu-debian/](https://support.killernetworking.com/knowledge-base/installing-the-killer-1535-1525-1435-in-ubuntu-debian/)

The XPS 13 has a different model of that brand card and it comes with 18.04. I am not sure if they add the driver themselves or if it is supported by default. [https://www.dell.com/en-us/work/shop/dell-laptops-and-notebooks/xps-13-developer-edition/spd/xps-13-9380-laptop/cax13w10p1c701subuntu](https://www.dell.com/en-us/work/shop/dell-laptops-and-notebooks/xps-13-developer-edition/spd/xps-13-9380-laptop/cax13w10p1c701subuntu)

---

### Post by makitso on 2019-09-18
Yes, I followed this process to get the laptop to support wifi.  My question is, shouldn't the Linux kernal support this driver?

---

### Post by makitso on 2019-09-18
[h=2]Actually, the XPS 15 7590 WiFi issue is with the  Killer Wireless 1650 driver.
[/h]

[COLOR=#7A7A7A][FONT=FontAwesome][/FONT][/COLOR]

---

### Post by Yellow Pasque on 2019-09-18
Quite simply, Intel has not sent the the necessary changes to the upstream kernel yet. Boring technical details about the iwlwifi development cycles: [https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi/core_release](https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi/core_release)

This PPA should make your life easier (i.e. you won't have to manually build iwlwifi-backport after every kernel update): [https://launchpad.net/~canonical-hwe-team/+archive/ubuntu/backport-iwlwifi](https://launchpad.net/~canonical-hwe-team/+archive/ubuntu/backport-iwlwifi)
Hopefully, the PPA is integrated into official Ubuntu 19.10 repos: [https://bugs.launchpad.net/ubuntu/+bug/1835858](https://bugs.launchpad.net/ubuntu/+bug/1835858)

> I am not sure if they add the driver themselves or if it is supported by default.
Dell does make some modifications to their OEM Ubuntu versions.

---

### Post by jeremy31 on 2019-09-18
> **Yellow Pasque said:**
> 

Dell does make some modifications to their OEM Ubuntu versions.

Yes, including their own repo with drivers to make these devices work as they have some iwlwifi dkms package.

A bug report could be filed against the kernel because it doesn't support this device and they might be able to backport the changes into the 4.15 kernels and maybe even the 5.0 kernel used by 19.04

Moved to Network and Wireless

---

### Post by makitso on 2019-09-22
[COLOR=#000000]If your running on 18.04, there is a proposed kernel that solves the wifi driver problem.[/COLOR]

[COLOR=#000000]sudo add-apt-repository ppa:canonical-kernel-team/ppa[/COLOR]
[COLOR=#000000]sudo apt-get update[/COLOR]
[COLOR=#000000]sudo apt-get install linux-oem-osp1[/COLOR]

---

