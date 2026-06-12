---
title: "Slow wifi with Qualcomm Atheros after update to Ubuntu 24.04 from 22.04"
date: 2024-08-31
forum: Networking &amp; Wireless
---

### Post by rinzewind on 2024-08-31
Hi everybody,

I used to enjoy fast wifi speeds with my Ubuntu 22.04 and my Qualcomm Atheros (ath10k, qca9377) after adding this to /etc/modprobe.d/ath10k.conf:

```
options ath10k nohwcrypt=1
```

It made a huge difference.

With the update to Ubuntu 24.04, I can see that the wifi speed is again slow (around 30 Mbps, which is not the end of the world, but not the performance I was getting with the previous version) and that module is not loaded anymore:

```

$ lsmod | grep ath
ath10k_pci             61440  0
ath10k_core           757760  1 ath10k_pci
ath                    40960  1 ath10k_core
mac80211             1720320  1 ath10k_core
cfg80211             1323008  3 ath,mac80211,ath10k_core
```

I can see that ath10k_core has an option that look like the old one I was using:

```

# sudo modinfo ath10k_core | grep crypt
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)
```

However, when I try to set cryptmode=1, I get the following error during startup:

```

[   20.005291] ath10k_pci 0000:02:00.0: qca9377 hw1.1 target 0x05020001 chip_id 0x003821ff sub 1028:1810
[   20.005305] ath10k_pci 0000:02:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[   20.005978] ath10k_pci 0000:02:00.0: firmware ver WLAN.TF.2.1-00021-QCARMSWP-1 api 6 features wowlan,ignore-otp crc32 42e41877
[   20.059740] sof-audio-pci-intel-cnl 0000:00:1f.3: DSP detected with PCI class/subclass/prog-if info 0x040380
[   20.074459] ath10k_pci 0000:02:00.0: board_file api 2 bmi_id N/A crc32 8aedfa4a
[   20.074510] ath10k_pci 0000:02:00.0: cryptmode > 0 requires raw mode support from firmware      <------------------ here
[   20.074542] ath10k_pci 0000:02:00.0: fatal problem with firmware features: -22
[   20.074972] ath10k_pci 0000:02:00.0: could not probe fw (-22)
```

As far as I've been able to find, there's no other option I can use. The firmware is up to date, and I don't know where to keep looking. Any help is appreciated.

Thanks.

---

### Post by jeremy31 on 2024-09-01
See [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108) and post results

---

### Post by rinzewind on 2024-09-01
Here it is: [https://termbin.com/rmsw](https://termbin.com/rmsw)

---

