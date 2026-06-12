---
title: "WIFI card detected, module loaded but the device doesnt appear under iwconfig"
date: 2020-05-25
forum: Networking &amp; Wireless
---

### Post by tlarroucau on 2020-05-25
Hi, 

This is my first time posting in the Ubuntu forums. Im using Ubuntu 20.04 in a DELL Inspiron-5559. After doing a manual ```
fsck 
```the computer does not connect to any network. WIFI card is detected, the module is loaded, but the device doesn't appear under ```
iwconfig
``` . [COLOR=#4A4A4A][FONT=&amp]I have tried booting from a USB with Ubuntu 20.04, and the computer connects properly to the WIFI network.
The output of ```
lspci
``` (just pasting the part of the networks) is:
```

02:00.0 Network controller: Intel Corporation Wireless 3160 (rev 83)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL810xE PCI Express Fast Ethernet controller (rev 07)

```
and the  output of ```
iwconfig
``` is  

[/FONT][/COLOR]```
lo            no wireless extensions.
enp3s0   no wireless extensions.

```

Thanks in advance!

---

### Post by chili555 on 2020-05-25
What is the response to the terminal command:

```
sudo modprobe iwlwifi && dmesg | grep iwl

```
Thanks.

---

### Post by tlarroucau on 2020-05-25
Thanks for the suggestion. The output is the following:

```

[   29.346284] iwlwifi 0000:02:00.0: enabling device (0000 -> 0002)
[   29.346284] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-3160-17.ucode failed with error -2
[   29.346284] iwlwifi 0000:02:00.0: no suitable firmware found!
[   29.346284] iwlwifi 0000:02:00.0: iwlwifi-3160-17 is required
[   29.346284] iwlwifi 0000:02:00.0: check git://it.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git

```

---

### Post by chili555 on 2020-05-25
> 
no suitable firmware found!Please hook up that ethernet and run:

```
sudo apt update
sudo apt install --reinstall linux-firmware
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi
```

Your wireless should now be working.

---

### Post by tlarroucau on 2020-05-25
It worked!

Thanks a lot!

---

