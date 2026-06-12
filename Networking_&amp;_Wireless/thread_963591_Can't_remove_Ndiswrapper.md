---
title: "Can't remove Ndiswrapper"
date: 2008-10-30
forum: Networking &amp; Wireless
---

### Post by Telémakhos on 2008-10-30
Hi, I've uninstalled ndiswrapper from my system and it isn't in synaptic but this is what I get doing a lsmod.


```
loyx@Apollo:~$ lsmod | grep ndis
ndiswrapper           196380  0 
usbcore               148848  5 ndiswrapper,usbhid,uhci_hcd,ehci_hcd

```

Can anyone explain me why is this module loaded?

---

### Post by Ayuthia on 2008-10-30
> **Telémakhos said:**
> Hi, I've uninstalled ndiswrapper from my system and it isn't in synaptic but this is what I get doing a lsmod.


```
loyx@Apollo:~$ lsmod | grep ndis
ndiswrapper           196380  0 
usbcore               148848  5 ndiswrapper,usbhid,uhci_hcd,ehci_hcd

```

Can anyone explain me why is this module loaded?

Ubuntu does come with the ndiswrapper module.  Even if you uninstall ndiswrapper, the ndiswrapper.ko file is still there (it is packaged in linux-ubuntu-modules if I recall correctly).

Is ndiswrapper listed in /etc/modules?  That could cause it to load.

---

### Post by Telémakhos on 2008-10-30
No, it's not listed there... it's weird

---

### Post by Ayuthia on 2008-10-30
You can always blacklist it.

I am not for sure if you have to run update-initramfs -u or not.  It might be something that is still loading because it is in the initramfs (it is used as the root file system by the kernel while booting).

---

