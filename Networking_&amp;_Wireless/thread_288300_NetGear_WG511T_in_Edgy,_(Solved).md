---
title: "NetGear WG511T in Edgy, (Solved)"
date: 2006-10-29
forum: Networking &amp; Wireless
---

### Post by eldaria on 2006-10-29
Ok, after a lot of searching I found out why my Netgear WG511T with the AR5212 chipset, did not work after I upgraded from Dapper to Edgy.

In Dapper It installed Restricted modules by default, and in Edgy it did not.
After installing restricted-modules and unplug, replug the card. it now works.

---

### Post by GaryH on 2006-11-01
Hi elderia,
I have the same problem. I used the command uname -a, and observed my kernel version to be 2.6.17.13 so I looked for linux-restricted-2.6.17-13-386 in the repository and couldn't find it. Which restricted modules did you install?
Thanks,
GaryH

---

### Post by eldaria on 2006-11-01
First make sure you have the universe repository enabled, otherwise you wont see the restricted modules.

don't install a specific kernel version of the restricted modules, then it will break next time the kernel is updated.

open adept, and type in linux-image
Then you will see which one was installed for you, there will be some kernel versions but look for the one without a version number, but more a platform, in my case it is the linux-image-generic.
If you have the same, then now search for restricted, and select the same one.
So in my case it was linux-restricted-modules-generic.

---

### Post by GaryH on 2006-11-01
Hi eldaria,
Thanks for responding to my last. Using lsmod, I observed that the wg511t drivers (atheros) are not loaded. Curiously enough my modem driver (ltmodem, ltserial) isn't loaded either and of course my modem doesn't work. Note that ltmodem and ltserial are also restricted. If I go back a version using grub, then the appropriate modules are in the list and everything works okay. **You are definetely correct, restricted modules are missing from the module list in Edgy!**  Using the synaptic package manager (I'm using the gnome GUI), I tried installing inux-restricted-modules-generic with no success. They installed okay but I still don't seen them in the module list. I'm going to tinker some more and I'll let you know how I make out. 

Do you happen to know if I can safely load the subject drivers using insmod. I'm worried that the drivers were rebuilt between dapper and edgy and may lock up or destroy my system if I insert them.

Thanks again eldaria,
GaryH

fyi my wife and I love amsterdam

---

### Post by eldaria on 2006-11-02
> 
Do you happen to know if I can safely load the subject drivers using insmod. I'm worried that the drivers were rebuilt between dapper and edgy and may lock up or destroy my system if I insert them.


This I have no idea about, I'm pretty new to linux my self, so I'm experimenting also. :-)
I actually re-installed my laptop from scratch, since the upgrade left me with no GUI.
And I found out that If I leave the network card in while installing, I can't get it to work at all, only if I insert it after installation is done could I get it to work, (After installing restricted modules)


> 
fyi my wife and I love amsterdam


I like it too, although I'm originally from Sweden. :-)

---

### Post by dannyboy79 on 2007-02-08
edgy and wg511t is not good out of the box supposedly per this link. [http://madwifi.org/ticket/1016](http://madwifi.org/ticket/1016)
madwifi fixed this issue around 2/6/07 for the wg511t, Gnome NetworkManager (using wpa_supplicant, using madwifi-ng, using ath_pci).

---

