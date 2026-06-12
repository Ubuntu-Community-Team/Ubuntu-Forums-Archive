---
title: "WUSB54G without ndiswrapper?"
date: 2008-06-20
forum: Networking &amp; Wireless
---

### Post by Brian96 on 2008-06-20
I have a Linksys WUSB54Gv2 that is apparently not being detected in Hardy.

All of the threads I have found on here relating to this driver talk about using ndiswrapper. Is it possible to get the card working without ndiswrapper? (I know with my BCM43xx on my laptop many instructions called for ndiswrapper, but I found the proprietary drivers available through the Restricted Driver Manager worked, but I don't see an option for restricted drivers with this adapter.)

Thanks in advance.

---

### Post by cariboo on 2008-06-21
It looks like there are no linux modules for your device. Ndiswrapper is quite easy to implement with the correct Windows drivers.

What you will need:

```
ndiswrapper-utils
ndiswrapper-common
ndisgtk
Windows XP drivers
```

I've never used the gui to load the drivers but if that is easier for you use it. To do it in a terminal

```
ndiswrapper -i driver.inf
ndiswrapper -l to check the status
ndiswrapper -m to write the code to /etc/modprobe.d
depmod -a to check for errors
modprobe ndiswrapper
```

You will probably have to run the commands as root so add sudo to each command.

Jim

---

