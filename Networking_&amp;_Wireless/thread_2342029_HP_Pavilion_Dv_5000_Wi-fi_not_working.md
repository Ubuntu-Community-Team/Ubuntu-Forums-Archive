---
title: "HP Pavilion Dv 5000 Wi-fi not working"
date: 2016-11-03
forum: Networking &amp; Wireless
---

### Post by andb93 on 2016-11-03
Hello everybody,

I'm a neophyte of Ubuntu and I installed XUbuntu 16.04 on a HP Pavilion DV 5000.
From the network manager I can't use Wi-Fi, even enable it.
```

lspci -nn | grep -i net
06:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
08:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VE Network Connection [8086:1092] (rev 01)

```

I used the following commands:

```

sudo apt-get install build-essential

wget https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v4.4.2/backports-4.4.2-1.tar.gz

tar -zxvf backports-4.4.2-1.tar.gz

cd backports-*

make defconfig-iwlwifi

make

sudo make install

sudo modprobe iwlwifi

```
but nothing seems to be changed.
Does anybody ever dealt with this problem?

Thank you in advance for any advices.

---

### Post by jeremy31 on 2016-11-03
I would uninstall the backports ```
cd backports-4.4.2-1
sudo make uninstall
```

Reboot, go into BIOS and see if wireless is enabled there.  Look for a switch or button that may enable wireless.  If you find nothing see the wireless script link in my signature and post your results

Your wireless should use the iwlegacy and iwl3945 modules not the iwlwifi

---

### Post by andb93 on 2016-11-03
By uninstalling the backports and enabling the wireless from BIOS I got the wireless working.
Thank you very much!:D

---

### Post by jeremy31 on 2016-11-03
Great, use the thread tools menu at the top/right side of the page to mark as solved

---

