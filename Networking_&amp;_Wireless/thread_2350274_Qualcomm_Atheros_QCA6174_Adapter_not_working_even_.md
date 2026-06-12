---
title: "Qualcomm Atheros QCA6174 Adapter not working even with ath10k_pci in use"
date: 2017-01-23
forum: Networking &amp; Wireless
---

### Post by drew-rohskopf on 2017-01-23
Hello,

I just did a clean Ubuntu 16.04 install on a new Lenovo Yoga 710. I've searched the web for hours and followed the instructions at this post [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

I attached the tar file with my WiFi report results. I can't seem to any issues nor any cases that match mine exactly.

I am able to use WiFi, but it won't connect to any networks (it just keeps asking for the password even though it's correct).

Any help or pointers in the right direction are greatly appreciated.

Thanks for your time.

---

### Post by praseodym on 2017-01-23
If you are located in the US the country code settings are wrong (13 channels in the 2,4 GHz region instead of 11).

Change it via:
```

sudo sed -i "s/REGDOMAIN=/REGDOMAIN=US/g" /etc/default/crda 
```
Reboot.

> ```
[   46.086497] wlp1s0: deauthenticated from <MAC 'GTother' [AC8]> (Reason: 15=4WAY_HANDSHAKE_TIMEOUT)
```

It takes too long to connect. The ESSID "GTother" is available many times. Which "Cell" is yours you want to connect to? Take that MAC address and add it to the **BSSID** section in the profile.

After rebooting, please show:
```

dmesg | egrep 'ath10k_pci|firm'
iwlist chan
```

---

