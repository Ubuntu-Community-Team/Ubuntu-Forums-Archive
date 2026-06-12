---
title: "ndiswrapper from source and kernel upgrades"
date: 2005-09-14
forum: Networking &amp; Wireless
---

### Post by d_1 on 2005-09-14
Hello, I'm a long time debian user, but new to ubuntu. Very nice experience so far, but I have one problem.

I built the newer version of ndiswrapper from source to get the wirless nic working on my girlfriend's laptop, and now I'm getting an error when apt tries to update the kernel image to linux-image-2.6.10-5-386. I get the following:

> E: /var/cache/apt/archives/linux-image-2.6.10-5-386_2.6.10-34.5_i386.deb:  trying to overwrite `/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko', which is also in package ndiswrapper-modules-2.6.10-5-386

How do I resolve this? When I built the source, I didn't remove the already installed package. I just followed this HowTo:
[SetupNdiswrapperHowTo](https://wiki.ubuntu.com/SetupNdiswrapperHowto?highlight=%28ndiswrapper%29)

---

### Post by mlomker on 2005-09-15
Two options:

1) Backup that .ko file, force the upgrade, and then copy your file back.
2) Don't upgrade the kernel (go into Synaptic and set the lock option).

Force:

```

su
cp /lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko /lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko.bak
apt-get upgrade --force-yes
cp /lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko.bak /lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko

```

---

