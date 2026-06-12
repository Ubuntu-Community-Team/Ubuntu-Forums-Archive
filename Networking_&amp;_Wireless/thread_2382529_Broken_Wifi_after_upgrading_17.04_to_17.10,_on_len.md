---
title: "Broken Wifi after upgrading 17.04 to 17.10, on lenovo yoga 710"
date: 2018-01-14
forum: Networking &amp; Wireless
---

### Post by yurkaz on 2018-01-14
Wireless interface go down after approx 9 min. Turning WiFi off/on fixes the issue... but only for next 9 minutes... 
 
**The firmware file updating solve this issue:**
[LIST]
[*]download new firmware [https://github.com/kvalo/ath10k-firmware/blob/master/QCA6174/hw3.0/4.4.1.c1/firmware-6.bin_RM.4.4.1.c1-00035-QCARMSWP-1](https://github.com/kvalo/ath10k-firmware/blob/master/QCA6174/hw3.0/4.4.1.c1/firmware-6.bin_RM.4.4.1.c1-00035-QCARMSWP-1)
[*]replace /lib/firmware/ath10k/QCA6174/hw3.0/firmware-6.bin with downloaded file
[*]reload wifi module:
[/LIST]
```

# rmmod ath10k_pci
# modprobe ath10k_pci

```

---

### Post by andrebrait on 2018-01-15
> **yurkaz said:**
> Wireless interface go down after approx 9 min. Turning WiFi off/on fixes the issue... but only for next 9 minutes... 
 
**The firmware file updating solve this issue:**
[LIST]
[*]download new firmware [https://github.com/kvalo/ath10k-firmware/blob/master/QCA6174/hw3.0/4.4.1.c1/firmware-6.bin_RM.4.4.1.c1-00035-QCARMSWP-1](https://github.com/kvalo/ath10k-firmware/blob/master/QCA6174/hw3.0/4.4.1.c1/firmware-6.bin_RM.4.4.1.c1-00035-QCARMSWP-1)
[*]replace /lib/firmware/ath10k/QCA6174/hw3.0/firmware-6.bin with downloaded file
[*]reload wifi module:
[/LIST]
```

# rmmod ath10k_pci
# modprobe ath10k_pci

```

The firmware version you linked might not fix the issue completely. Please refer to a better solution here: [https://ubuntuforums.org/showthread.php?t=2382607](https://ubuntuforums.org/showthread.php?t=2382607)

---

