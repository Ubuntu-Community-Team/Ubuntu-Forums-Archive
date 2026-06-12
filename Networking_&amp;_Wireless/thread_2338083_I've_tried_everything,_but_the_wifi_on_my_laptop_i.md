---
title: "I've tried everything, but the wifi on my laptop it's not working"
date: 2016-09-24
forum: Networking &amp; Wireless
---

### Post by kayters on 2016-09-24
[COLOR=#333333][FONT=Ubuntu]Hi guys,
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]here is the details of my wireless card:
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Chip ID: BCM43142 
PCI-ID: 14e4:4365 
Kernel Driver: bcma-pci-bridge

[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]For some reasons, Ubuntu can't find any wifi network on my laptop (HP).[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]I've connected it to the Internet with a LAN cable and I followed this steps: [https://askubuntu.com/questions/671251/installing-broadcom-wireless-drivers-for-ubuntu-15-04](https://askubuntu.com/questions/671251/installing-broadcom-wireless-drivers-for-ubuntu-15-04)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Everything went well, but the wifi is still not working. What the problem might be?[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]
Thank you![/FONT][/COLOR]

---

### Post by jeremy31 on 2016-09-24
What happens when you ```
sudo modprobe -v wl
```

---

### Post by kayters on 2016-09-24
This happens:

> insmod /lib/modules/4.4.0-38-generic/updates/dkms/wl.ko
modprobe: ERROR: could not insert 'wl' : Required key not available

---

### Post by jeremy31 on 2016-09-24
You could try disabling Secure Boot in BIOS as then the key isn't required

---

### Post by kayters on 2016-09-24
> **jeremy31 said:**
> You could try disabling Secure Boot in BIOS as then the key isn't required

Wow! Now it's working! I just disabled the Secure Boot in Bios and it worked instantly.

Thank you so much!

---

### Post by jeremy31 on 2016-09-24
Feel free to use the Thread Tools menu near the top of the page to mark as solved

---

### Post by kayters on 2016-09-24
Done! Thank you.

---

