---
title: "network fails using smp kernel"
date: 2005-06-19
forum: Networking &amp; Wireless
---

### Post by neo75903 on 2005-06-19
Hi,

i have recentl installed ubuntu 5.04. After install network works fine. 
But network doesnt work anymore when i installed and boot into a smp kernel (Dual Athlon). The boot screen hangs for about a minute at "Configuring network interfaces, the a few lines later i got "Temporary failure in name resolution".
From devices, the network card is recognised properly.

Any idea why it works fine under single cpu kernel and not anymore under smp kernel?

Thx.

---

### Post by blind0wl on 2005-06-20
Check that the correct DNS servers your using (assuming youve got a static IP) are entered in the /etc/resolv.conf file.  If your running DHCP to get you IP credentials, this should be done automatically.

Let me know

Cheers

Blindy

---

### Post by sgenchev on 2005-06-20
Presuming that nothng else have changed except for the kernel (I assume that you have tried to boot back into non-smp kernel and everything works fine), this points to the driver.  If you cannot get an IP while booting to old kernel, something else have changed and it has nothing to do with the kernel.
 You do not say what driver does your card use. Most drivers work just on Debian(ish) but some require binary firmware to work properly. Debian dully removes binary-only firmware from stock kernels to be "free as in GNU".
 Ubuntu has package "linux-restricted-modules-Your-Kernel-Version". Try to install this package corresponding to your kernel - probably linux-restricted-modules-2.6.10-5-k7-smp and see if it helps.
 You have to go online for it but you did not remove old kernel yet, did you?

---

