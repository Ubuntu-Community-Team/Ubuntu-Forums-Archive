---
title: "no network after resume from suspend"
date: 2008-02-22
forum: Networking &amp; Wireless
---

### Post by julien-1993 on 2008-02-22
after a fresh Ubuntu 7.10 gutsy server minimal desktop install I finally managed to have suspend and resume working correctly.

however when i resume from suspend the network is not working......

search the forum and google for it but did not find anything about that.

network is wired and network card is onboard of a gigabyte Motherboard with nvidia chipset.

any help very appreciated.
thank you
Julien

---

### Post by jeantasse on 2008-02-22
it maybe not much, but have you tried a simple command like:

sudo /etc/init.d/networking restart

until there a bug fix, instead of rebooting try that comment

---

### Post by julien-1993 on 2008-02-23
tryed your suggestion but even that did not work.

in fact when i enter ifconfig
eth0 is not even there.

anyway I will surrender on that because making suspend and resume work cause to have no agp and this is worst for me than no suspend.

I will make another thread about that.

linux overtaking the pc world is not yet.....
slowly but surely....i hope

---

### Post by BassKozz on 2008-03-04
I am having the same EXACT problems... When I resume no network...
I've tried jeantasse's suggestion```
sudo /etc/init.d/networking restart
```
And not even that fixes it...
I am on a home built rig that uses Abit IP35-Pro Mobo w/ dual Gigabit ports (Realtek 8110SC Gigabit Lan), I am running my network on eth1 (instead of eth0), I don't know if that makes a difference, I also am running multiple VM's using VMware that use br0 which is tethered to eth1 (I believe), and I am running Ubuntu 7.10 64-bit (I hope all this added info helps)...
Anyways I found this bug report at launch pad: [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/25614](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/25614)
Hopefully someone can find a fix soon, for now it's no standby or hibernate for me :(

---

