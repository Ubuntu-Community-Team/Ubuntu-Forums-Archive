---
title: "no wifi adapter found ubuntu 18.04"
date: 2018-07-08
forum: Networking &amp; Wireless
---

### Post by gugra on 2018-07-08
script result :[http://paste.ubuntu.com/p/dHC8F3Gby9/](http://paste.ubuntu.com/p/dHC8F3Gby9/)
my WiFi adapter Qualcomm Atheros QCA9565/AR9565 Wireless Network Adapter.
 Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036]
dual boot with windows 10
works fine in windows 10
the WiFi worked while Ubuntu was installing stopped working after the reboot.

---

### Post by deadflowr on 2018-07-08
*Thread moved to **Networking and Wireless***

---

### Post by chili555 on 2018-07-09
Old Doc Chili doesn't like this one bit! > [   53.099346] ath9k 0000:03:00.0: PCI INT A: not connected
[   53.099395] ath9k 0000:03:00.0: request_irq failed
[   53.099413] ath9k: probe of 0000:03:00.0 failed with error -107
Would you please check in the BIOS of the computer and make sure that IRQs are set to auto-select or available? Reserved, disabled or unavailable are all not recommended.

In fact, you may probably be able to reset the BIOS to defaults. [https://i2.wp.com/neosmart.net/wiki/wp-content/uploads/sites/5/2015/03/reset-bios-1.jpg](https://i2.wp.com/neosmart.net/wiki/wp-content/uploads/sites/5/2015/03/reset-bios-1.jpg)

---

### Post by gugra on 2018-07-09
IRQ is not a option on the BIOS but I reset the BIOS to default also I don't know if it is a related issue but my computer doesn't turn off it gets stuck in the ubuntu logo.

---

### Post by chili555 on 2018-07-09
> I don't know if it is a related issue but my computer doesn't turn off it gets stuck in the ubuntu logo.
It may well be related. I suggest that you debug that issue first. Please ask here: [https://ubuntuforums.org/forumdisplay.php?f=331](https://ubuntuforums.org/forumdisplay.php?f=331)

---

### Post by gugra on 2018-07-11
found IRQ setting in BIOS there is only two options quiet or continuous which do I choose

---

### Post by chili555 on 2018-07-12
> **gugra said:**
> found IRQ setting in BIOS there is only two options quiet or continuous which do I chooseIt seems obvious to me. Try one setting and reboot. Check:```
dmesg | grep ath
```Are the messages still there?> [ 53.099346] ath9k 0000:03:00.0: PCI INT A: not connected
[ 53.099395] ath9k 0000:03:00.0: request_irq failed
[ 53.099413] ath9k: probe of 0000:03:00.0 failed with error -107Or are they gone?

If the error messages are still there, go back into the BIOS and try the other setting, reboot and check again.

Our hope is, of course, that one setting or the other will stop the error and start the wireless. 

Tha ath9k driver is usually pretty solid and trouble-free.

---

### Post by praseodym on 2018-07-12
One could try "iommu=soft" as boot parameter

---

### Post by gugra on 2018-07-14
dmesg | grep ath 
doesn't show anything now

---

### Post by chili555 on 2018-07-14
> **gugra said:**
> dmesg | grep ath 
doesn't show anything nowHow about:```
sudo modprobe ath9k && dmesg | grep ath
```

---

### Post by gugra on 2018-07-14
also nothing

---

### Post by gugra on 2018-07-21
well, I give up

---

### Post by praseodym on 2018-07-22
Did you try the boot parameter? Open that file
```

gksudo gedit /etc/default/grub
```

Look for that line

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

and change it to

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash iommu=soft"
```
Proofread carefully, save, close the editor and run
```

sudo update-grub
```
Reboot

---

