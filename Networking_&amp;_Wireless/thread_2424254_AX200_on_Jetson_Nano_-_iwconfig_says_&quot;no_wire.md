---
title: "AX200 on Jetson Nano - iwconfig says &quot;no wireless extensions&quot;"
date: 2019-08-05
forum: Networking &amp; Wireless
---

### Post by meatwad650 on 2019-08-05
The needful pastebin is [here]("http://paste.ubuntu.com/p/FgNSKcGv27/").

This is an odd corner case which may or may not be relevant.  I've got an Intel AX200 on the Jetson Nano, and I compiled the core 45 release of the iwlwifi driver as follows:

```
[COLOR=#333333][FONT=&amp]git clone --single-branch --branch release/core45 https://git.kernel.org/pub/scm/linux/kernel/git/iwlwifi/backport-iwlwifi.git
[/FONT][/COLOR]make defconfig-iwlwifi-public
sed -i 's/CPTCFG_IWLMVM_VENDOR_CMDS=y/# CPTCFG_IWLMVM_VENDOR_CMDS is not set/' .config
make -j4 [COLOR=#333333][FONT=&amp]sudo make install[/FONT][/COLOR]
```

And the card does work.  iw commands see it, and I was able to somewhat get it in monitor mode.  Definitely was able to pass traffic with it.

However, iwconfig can't talk to it.  It says "no wireless extensions" and I'm not sure why or what to troubleshoot.  (I'm trying to get Kismet working, and I suspect/wonder if this issue is why Kismet is unhappy.)  

Does it look like I've done anything obviously wrong?

---

### Post by meatwad650 on 2019-08-05
Also, I did update to the latest firmware ([iwlwifi-cc-a0-48.ucode]("https://git.kernel.org/pub/scm/linux/kernel/git/iwlwifi/linux-firmware.git/tree/iwlwifi-cc-a0-48.ucode?h=iwlwifi-fw-2019-07-20&id=327d752f242ae15ddccc7458ee5c936cfa5331e2")) if that helps.

---

### Post by chili555 on 2019-08-06
I've read your very long and very interesting list of GRUB command options and this appears twice, as do several other parameters:```

net.ifnames=0

```I suggest that you thoroughly examine your GRUB commands and after you eliminate duplicates, that you change this:```
net.ifnames=0

```To this:```
net.ifnames=0 biosdevname=0 

```Reboot and tell us if there is any improvement.

---

### Post by meatwad650 on 2019-08-06
This platform doesn't really have grub, given that it's embedded.  So I'll have to investigate how it does that.

---

### Post by chili555 on 2019-08-07
> **meatwad650 said:**
> This platform doesn't really have grub, given that it's embedded.  So I'll have to investigate how it does that.
What does this report?```
cat /etc/default/grub

```

---

### Post by julyighor on 2019-12-01
> **chili555 said:**
> What does this report?```
cat /etc/default/grub

```

This file does not exists on the Jetson Nano.


Any solution on this?

---

### Post by chili555 on 2019-12-01
I'm out of useful suggestions, however, these links may help: [https://devtalk.nvidia.com/default/topic/763150/jetson-tk1-command-line-boot-/](https://devtalk.nvidia.com/default/topic/763150/jetson-tk1-command-line-boot-/)  and:  [https://devtalk.nvidia.com/default/topic/747933/embedded-systems/is-it-possible-to-boot-from-sd-or-usb-hdd-and-how-jetson-tk1-/](https://devtalk.nvidia.com/default/topic/747933/embedded-systems/is-it-possible-to-boot-from-sd-or-usb-hdd-and-how-jetson-tk1-/)

---

