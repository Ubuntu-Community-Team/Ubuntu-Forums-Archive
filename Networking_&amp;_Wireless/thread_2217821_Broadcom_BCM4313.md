---
title: "Broadcom BCM4313"
date: 2014-04-18
forum: Networking &amp; Wireless
---

### Post by Navneet_Kumar on 2014-04-18
How to update my broadcomm wireless driver in 13.10,using BCM4313 card...........and default driver..........

---

### Post by monkeybrain20122 on 2014-04-18
Why do you need to update the driver if it is working? I am using a bcm4313 and the default driver (brcmsmac), it works great.

---

### Post by praseodym on 2014-04-18
And the brcmsmac driver in 14.04 was significantly improved

---

### Post by monkeybrain20122 on 2014-04-18
> **praseodym said:**
> And the brcmsmac driver in 14.04 was significantly improved

Actually over here it works great on both 13.10 and 14.04.

Edited: but the closed wl driver which you have to take the trouble to install bcmwl-kernel-sources to activate is horrible, it actually killed the wifi.

---

### Post by Navneet_Kumar on 2014-04-19
i have already installed the kernel source driver but there is no brcmsmac driver on my machine..........can you you please tell me the right place to get it.......:D

---

### Post by praseodym on 2014-04-19
The driver is part of the kernel, but if you installed the STA driver its blacklisted:
```

grep brcm /etc/modprobe.d/*
locate brcmsmac.ko | grep lib
```

---

### Post by Navneet_Kumar on 2014-04-19
yes its there in the output of first command.what do you mean that it is blacklisted,there is no way to install it or it should not be installed......???

---

### Post by praseodym on 2014-04-19
bcmwl-kernel-source installs the proprietary Broadcom-STA driver, module name "wl"

Check:
```

sudo apt-get install linux-firmware-nonfree
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
sudo sed -i "s/blacklist b43/#blacklist b43/g" $(egrep -lo 'blacklist b43' /etc/modprobe.d/*)
sudo sed -i "s/blacklist ssb/#blacklist ssb/g" $(egrep -lo 'blacklist ssb' /etc/modprobe.d/*)
sudo sed -i "s/blacklist bcma/#blacklist bcma/g" $(egrep -lo 'blacklist bcma' /etc/modprobe.d/*) 
```
Reboot

---

### Post by Navneet_Kumar on 2014-04-19
i did that and after reboot wifi is working as before.no significant changes are observed

---

### Post by praseodym on 2014-04-19
Now check
```

lsmod
dmesg | grep brcm
iwlist chan
sudo iwlist scan
iwconfig
ifconfig -a
```

---

### Post by Navneet_Kumar on 2014-04-19
thanxx its working.

---

