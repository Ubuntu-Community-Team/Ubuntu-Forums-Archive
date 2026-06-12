---
title: "Wifi stops working after random time intervals"
date: 2017-08-29
forum: Networking &amp; Wireless
---

### Post by michael-titze on 2017-08-29
Hello everyone,

My ubuntu 17.04 64bit is giving me trouble with my wifi.

It will connect after boot, but after a (seemingly) random time simply disconnect and not reconnect anymore.
Even turning off and on Wifi as well as networking in the toolbar does not make it work again, the only "fix" is a reboot which is really annoying.

I have seen at least one more person with a similar issue on here ([https://ubuntuforums.org/showthread.php?t=2198911](https://ubuntuforums.org/showthread.php?t=2198911)) but the fix seems to be related to his wificard and he needs to modify iwldvm/iwlwifi which both do not exist on my system.

Output from
```
lspci -nnk | grep -iA2 net

```
```
Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: ASRock Incorporation Motherboard (one of many) [1849:8168]
    Kernel driver in use: r8169
--
05:01.0 Network controller [0280]: Ralink corp. RT3060 Wireless 802.11n 1T/1R [1814:3060]
    Subsystem: Ralink corp. RT3060 Wireless 802.11n 1T/1R [1814:3060]
    Kernel driver in use: rt2800pci
```
Right now the Wifi is working.

---

### Post by praseodym on 2017-08-30
Hi,

there is a bug in 17.04:

```
echo -e "\n[device]\nwifi.scan-rand-mac-address=no" | sudo tee -a /etc/NetworkManager/NetworkManager.conf
sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Reboot

---

### Post by michael-titze on 2017-08-30
Hi praseodym,

Would you mind explaining what this code does?
Also, will this fix it forever?

Thanks!

---

### Post by praseodym on 2017-08-31
Forever? You can easily revert the changes, when necessary. Until then: Yes

First command stops the random re-naming of the MAC addresses, second one deactivates the power management of the network-manager.

---

### Post by michael-titze on 2017-09-01
I copied your code, but I still have the issue.

Could it be something else?
Is there anything I can try when it happens to diagnose the problem?

---

### Post by praseodym on 2017-09-01
Try deactivating the hardware encryption of the driver.

On the fly:
```

sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci nohwcrypt=1
```
Works? Then make it permanent
```

echo "options rt2800pci nohwcrypt=1" | sudo tee /etc/modprobe.d/rt2800pci.conf
```

---

### Post by michael-titze on 2017-09-16
Hello, sorry for the late response, went on vacation :D

Now that I'm back on my desktop I have the same problem again and tried your suggestion, but found that again after some time the wifi will stop working.

However, your code seems to restart the wifi-module in a way that if i run your two lines, it will start working again.
Is there a way that I could make an alias/bash-script that I can run (or even automatically run everytime the wifi crashes?) as a temporary fix?

Thanks again for your help

---

### Post by praseodym on 2017-09-17
Lets try loading the driver per force every time on boot-up:
```

echo rt2800pci | sudo tee -a /etc/modules
```

---

### Post by michael-titze on 2017-09-23
Alright, I added the rt2800pci as you said.

It seems to be stable now!

Thanks alot, is there some internet points I can give you for helping me through this?

---

