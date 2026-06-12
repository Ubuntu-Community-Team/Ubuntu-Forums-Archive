---
title: "No wireless installing from alternate CD"
date: 2006-11-06
forum: Networking &amp; Wireless
---

### Post by greenmaze on 2006-11-06
After installing Edgy using the alternate CD, my wireless NIC is not detected. I know it works under Edgy, because when I had Dapper  installed and then upgraded to Edgy, the wireless card worked fine.

Is there some way to detect my wireless card?

Edit: The card is a Intel 3945ABG according to Windows XP.

---

### Post by andreas64 on 2006-11-07
Hi,

you need to install the restricted-modules for your kernel. After that, your wireless NIC will be detected.

Andreas

---

### Post by greenmaze on 2006-11-07
I've downloaded the .deb that I think I need:

```
linux-restricted-modules-2.6.17-10-generic_2.6.17.5-11_i386.deb
```

When I try to install it, the installer tries to download a few more packages. Being that I'm not hooked up to the internet (see no wireless), I get stuck.

Is there a way to find out what other packages are being installed?

Thanks

---

### Post by andreas64 on 2006-11-19
hi,

sorry for my late answer...

...why don't you use synaptic to install the restricted modules? It's more painless because all other needed packages will be installed too.

Andreas

---

