---
title: "Wireless Realtek RTL8723BE"
date: 2014-07-08
forum: Networking &amp; Wireless
---

### Post by Gregor_s on 2014-07-08
Hi,
My wireless is not working and I need help. This is as far as I got:

dmesg | grep -i RTL
[    1.305191] r8169 0000:03:00.0 eth0: RTL8106e at 0xffffc90000636000, 20:25:64:91:a7:a0, XID 04900000 IRQ 105
[    6.092503] rtl8723be 0000:04:00.0: enabling device (0000 -> 0003)
[    6.167675] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
[    6.173643] rtl8723be 0000:04:00.0: Direct firmware load failed with error -2
[    6.173649] rtl8723be 0000:04:00.0: Falling back to user helper
[    6.428815] rtlwifi: Firmware rtlwifi/rtl8723befw.bin not available


Thanks

---

### Post by Gregor_s on 2014-07-08
Forgot to add OS - Ubuntu 14.04

---

### Post by chili555 on 2014-07-08
> [ 6.428815] rtlwifi: Firmware rtlwifi/rtl8723befw.bin not availableThe firmware referred to is included in the latest version of linux-firmware. Which version do you have?```
sudo dpkg -s linux-firmware | grep -i version
```I hope you get Version: 1.127.4 where it is included. 

If not, then:```
sudo apt-get update && sudo apt-get -y upgrade
```Firmware should be one of the things updated. A reboot and you should be all set.

---

### Post by Gregor_s on 2014-07-09
I had an old version. After the update wireless started to work normaly.

Thanks

---

### Post by chili555 on 2014-07-09
> **Gregor_s said:**
> I had an old version. After the update wireless started to work normaly.

ThanksGlad it's working. Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

