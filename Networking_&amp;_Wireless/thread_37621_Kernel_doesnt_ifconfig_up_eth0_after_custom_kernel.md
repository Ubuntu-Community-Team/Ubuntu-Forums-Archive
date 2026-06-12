---
title: "Kernel doesnt ifconfig up eth0 after custom kernel compile"
date: 2005-05-27
forum: Networking &amp; Wireless
---

### Post by The_Universe on 2005-05-27
Hello all, I installed a custom kernel for my machine 2.6.11-9 because the stock kernels do not handle the non standard controller chips in my external firewire harddrive.  This exact kernel also works perfectly in debian testing. Now when i boot the kernel i get the following error message at boot:
"ror: temporary failure in name resolution"
and the light on my ethernet card remains off.  Once it has booted i have to manually
go into the shell and do:
'sudo ifconfig eth0 up; dhclient'
and then the network comes up.
Does anyone know how I can set this up so that it is handled in the boot sequence?  Why does it not work for my custom kernel but works for the stock kernel?
I dont know if this matters but in my custom kernel the driver for my nic is hard compiled into the kernel.   Any insight into this would be appreciated.

Thanks

---

