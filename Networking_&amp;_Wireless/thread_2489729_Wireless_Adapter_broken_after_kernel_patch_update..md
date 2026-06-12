---
title: "Wireless Adapter broken after kernel patch update."
date: 2023-08-09
forum: Networking &amp; Wireless
---

### Post by vvignesh6 on 2023-08-09
Hello Everyone! ,

We are facing an issue with the WiFi adaptor breaking after the Kernel Linux Kernel Vulnerabilities - Ubuntu 20.04 - Kernel Versionedpackage (amd64) patch update). Every month, we are facing this issue when users receive this kernel vulnerability patch. We were able to fix the issues by running the command earlier.

sudo apt install firmware-b43-installer
sudo apt install --reinstall backport-iwlwifi-dkms

But now the above command is not working, and we have tried a few more commands to reload the wifi driver, but still the wifi is not working, We are requesting that someone help us resolve this issue.


sudo modprobe iwlwifi gives the following:
modprobe: ERROR ../libkmod/libkmod-module.c:838 kmod_module_insert_module() could not find module by name='iwlwifi'
modprobe: ERROR could not insert 'iwlwifi': Unknown symbol in module, or unknown parameter (see dmesg)

---

### Post by TheFu on 2023-08-10
Every time there is a kernel update, all the modules used need to be relinked to the new kernel code. That's the good and the bad of Linux kernels and modules.  Normally, DKMS handles that aspect well.  If it isn't working for you and you know which kernel modules are required, wait to update the kernel until the new driver is available.

For most people, the immediate solution after a failure is to boot from the prior kernel.  The grub boot menu, Advanced, in the boot screen will show the available prior kernels that are installed.

If the devices are wifi only, you run into a problem if the wireless doesn't work, then it is difficult to connect to a network to get any updates.  This means being very careful about patching.  I think the driver/module you need is included in the kernel sources, so all the needed files should already be on the system.  If you have the wrong module/driver, it is very possible that new code is necessary. We see this with Realtek wifi drivers on very new systems all-the-time here.

So, when you do get this working, best to do the research to ensure you know the driver/module needed and ensure you have setup a way to rebuild and load those automatically for the systems involved.

---

### Post by chili555 on 2023-08-10
> sudo apt install firmware-b43-installer
sudo apt install --reinstall backport-iwlwifi-dkmsOne is for Broadcom wireless devices and the other is for Intel. I doubt that you have both. As well, the iwlwifi-backport package installs its own versions of cfg80211 and mac80211 which do not work with, for instance, b43 ('b' is for Broadcom).

Let's find out what you really have and fix it from there. Please run and post:

```
lspci -nnk | grep 0280 -A3
sudo dkms status
sudo dmesg | grep iwl
```

---

### Post by vvignesh6 on 2023-08-17
Thank you all for response. 

[COLOR=#252525]Nothing has worked; finally, I have booted with the prior kernel from the GRUB advance option to fix this issue, but I am still wondering if we resume the patch (Linux Kernel Vulnerabilities, Ubuntu 20.04, Kernel Versioned Package (amd64)) deployment, will users start facing the same issue or not?[/COLOR]

my laptop has Intel wifi device.

---

### Post by vvignesh6 on 2023-08-17
[COLOR=#252525]We have only the wifi option and do not have a wired connection, but in this case, we have tried with a wired connection but Ethernet status is showing disabled in the lshw -C network output. We have tried to enable it in all possible ways but finally went with reverting to the old kernel from GRUB.

Can you please help me how to include the driver in the kernel sources and how to prevent such issues in the coming patch updates?[/COLOR]

---

### Post by TheFu on 2023-08-17
If you don't provide the data requested, nobody will help you.

---

