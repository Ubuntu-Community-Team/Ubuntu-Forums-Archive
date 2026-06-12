---
title: "Need Help loading gnome"
date: 2011-08-28
forum: New to Ubuntu
---

### Post by SpoonZie on 2011-08-28
i installed Ubuntu 11.04 via my windows 64 bit os, 
installed using wubi -> with the acpi workaround
sat through the "install screen" rebooted the laptop when it said to and now im stuck.

Laptop now has grub loader however when i load Ubuntu or Ubuntu recovery alll i see is a wall of text up until 

18.473991 ADDRCONF (NETDEV_UP) : wlan0: link is not ready

i've searched for the last 3 hours for a solution and am even more confused now than i was when i began.

i cannot access the console, tried ctrl+alt+f2 however i cannot type in this window. (cannot type in recovery mode -> ctrl+alt+f2 either) 

any help would be appreciated (im a complete beginner)

---

### Post by snip3r8 on 2011-08-28
It seems to me that your wubi installation went horribly wrong.

Maybe you should try a more solid approach like setting up a dedicated Linux partition.I am of-coarse assuming that your windows can still boot,In which case you should uninstall the wubi installation on windows first.

---

### Post by SpoonZie on 2011-08-28
thanks for the advice, will give the Dedicated reinstall a go.

---

### Post by SpoonZie on 2011-08-28
ok, so i've got a Ubuntu partition now.
however i am having problems installing from USB.

on regular install the error i seem to get is:
```
[ 10.087228 ]  ---[end trace e0473c8e15ab55ec] ---
udevd-work[105]: '/sbin/modprobe -bv pci:v000010DEd00001211sv00001558sd00005102b
c03sc00i00'  unexpected exit with status 0x0009
```

i have since been looking at how to install ACPI = off via usb.

there is no advanced options section on my installer, and i went to help -> then typed acpi=off and got the error 
could not find kernal image acpi = off.

---

### Post by sanderd17 on 2011-08-28
See my sig for setting boot options

---

