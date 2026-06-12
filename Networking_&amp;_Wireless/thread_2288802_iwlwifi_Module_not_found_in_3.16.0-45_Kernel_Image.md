---
title: "iwlwifi Module not found in 3.16.0-45 Kernel Image"
date: 2015-07-30
forum: Networking &amp; Wireless
---

### Post by sdlcrohns on 2015-07-30
I'm trying to get wireless networking installed on my new laptop with an Intel Wireless 7265 adapter. I do have the firmware for it installed as evidenced by the iwlwifi-7265-12.ucode file (and lots of others) included in /lib/firmware.

I know that the proper driver for this card is iwlwifi and that you should be able to launch iwlwifi using modprobe, but running modprobe results in the following:

```

modprobe iwlwifi
modprobe: ERROR: ../libkmod/libkmod-module.c:809 kmod_module_insert_module() could not find module by name='iwlwifi'
modprobe: ERROR: could not insert 'iwlwifi': Function not implemented 
```

And likewise modinfo:

```

modinfo iwlwifi
modinfo: ERROR: Module iwlwifi not found. 
```

Searching the modules directory for the the kernel release I have yields nothing. From looking at another machine I have access to (with an older kernel version or I would just copy the file), the module should be included as:
/lib/modules/3.16.0-45-generic/kernel/net/wireless/iwlwifi/iwlwifi.ko

But I don't have a /lib/modules/3.16.0-45-generic/kernel/net/wireless/ folder.

From what I can tell, the module should be included in the linux-image-3.16.0-45-generic package but uninstalling and re-installing that package yields nothing (likewise with the corresponding linux-header package). 

I'm not really sure where to go from here other than asking a friend with the same kernel version to give me the file. I would appreciate any advice.

---

### Post by chili555 on 2015-07-30
Something is seriously wrong here!

Please check:```
sudo dpkg -s linux-generic
```It ought to say:> Status: install ok installedIf not, install it:```
sudo apt-get install linux-generic
```Please do the same with:

* linux-image-generic

* linux-headers-generic

* linux-image-extra-`uname -r`

Those backticks are on the left side of my US keyboard on the same key with ~.

One of these is going to uncover a missing part that will then get installed. After a reboot, you should be all good.

---

### Post by sdlcrohns on 2015-07-30
Turns out I was missing the linux-generic package. Not sure how I managed to not have that installed... Oh well. It also fixed a similar issue I was having with my sound card. Everything is fixed now, thank you!

---

