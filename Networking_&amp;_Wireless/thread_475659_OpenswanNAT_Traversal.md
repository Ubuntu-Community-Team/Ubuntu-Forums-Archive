---
title: "Openswan/NAT Traversal"
date: 2007-06-16
forum: Networking &amp; Wireless
---

### Post by RickKnight on 2007-06-16
I'm trying to get a VPN connection between my home PC and my work firewall. Using Openswan, I can allmost get there. The problem seems to be in NAT-Traversal. I've enabled NAT-T in my Openswan/IPSEC configuration, but it still doesn't seem to work. I've checked my kernel to see if it has support for NAT-T and it doesn't seem to so I'm trying to build a new kernel with NAT-T. When I use make-kpkg --added-patches openswan --config configure, the command fails with a message about the kernel already containing the patch but when I ran make xconfig prior to make-kpkg, there were no NAT-T options. Also, the patch did succeed in adding KLIPS, but subsequent attempts to run make xconfig (or make menuconfig) fail with the error "can't open file net/ipsec/Kconfig".I've checked, that file does not exist.  Has anyone been able to apply this patch sucessfully or get Openswan and NAT-T working?

I'm running Feisty Fawn with kernel 2.6.20-16-generic.
I've installed the Openswan kernel patch and the kernel source and header packages.

Thanks,
Rick Knight

---

