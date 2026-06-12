---
title: "Lenovo v310 WIFI problem with Intel Dual Band 3165 on 16.04"
date: 2017-03-22
forum: Networking &amp; Wireless
---

### Post by ozzie28 on 2017-03-22
I bought new Lenovo laptop and I can't get wifi to work. Ethernet works fine.

I'd  be very thankful for an help.

```
edward@edward-lenovo:~$ uname -r
4.8.0-41-generic

edward@edward-lenovo:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial


edward@edward-lenovo:~$ lspci
00:00.0 Host bridge: Intel Corporation Device 5904 (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Device 5916 (rev 02)
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI (rev 21)
00:17.0 SATA controller: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] (rev 21)
00:1c.0 PCI bridge: Intel Corporation Device 9d10 (rev f1)
00:1c.4 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port (rev f1)
00:1c.5 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port (rev f1)
00:1f.0 ISA bridge: Intel Corporation Device 9d58 (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Device 9d71 (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
03:00.0 Network controller: Intel Corporation Intel Dual Band Wireless-AC 3165 Plus Bluetooth (rev 99)



edward@edward-lenovo:~$ dmesg | grep iwl
[    3.713872] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-7265D-24.ucode failed with error -2
[    3.713891] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-7265D-23.ucode failed with error -2
[    3.725940] iwlwifi 0000:03:00.0: loaded firmware version 22.361476.0 op_mode iwlmvm
[    3.776974] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 3165, REV=0x210
[    3.778256] iwlwifi 0000:03:00.0: L1 Disabled - LTR Disabled
[    3.778422] iwlwifi 0000:03:00.0: L1 Disabled - LTR Disabled
[    3.847296] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    3.965692] iwlwifi 0000:03:00.0 wlp3s0: renamed from wlan0


```

---

### Post by jeremy31 on 2017-03-22
Check ```
rfkill list all
```

If it shows ideapad-wifi or something similar as hard block: yes, try
```
echo "blacklist ideapad-laptop" | sudo tee /etc/modprobe.d/ideapad-blacklist.conf
```

Reboot

---

### Post by ozzie28 on 2017-03-22
Hell yeah ! 

I don't know what has happened but it worked like a charm. 


Thank you very much.

---

### Post by stangeday72 on 2017-03-24
Thanks. Also worked on Lenovo V510 for me!

---

