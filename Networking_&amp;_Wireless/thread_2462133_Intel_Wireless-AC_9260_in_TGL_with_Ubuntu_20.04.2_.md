---
title: "Intel Wireless-AC 9260 in TGL with Ubuntu 20.04.2 LTS, BT work, Wi-Fi cannot work"
date: 2021-05-14
forum: Networking &amp; Wireless
---

### Post by ginousi on 2021-05-14
My question is when I use Intel Wireless-AC 9260 in "Whiskey Lake platform" with Ubuntu 20.04.2 LTS,
no issue, Wi-Fi & BT work normal.

If I use Intel Wireless-AC 9260 in "Tiger Lake platform" with Ubuntu 20.04.2 LTS, 
only BT work, Wi-Fi cannot work.

#lspci | grep "Wireless"
02:00.0 Network controller: Intel Corporation Wiress-AC 9260 (rev ff)
# sudo dmesg | grep iwl
[    6.158681] iwlwifi 0000:02:00.0: can't change power state from D3cold to D0 (Config space inaccessible)
[    6.158696] iwlwifi 0000:02:00.0: can't change power state from D3hot to D0 (Config space inaccessible)
[    6.158942] iwlwifi 0000:02:00.0: HW_REV=0xFFFFFFFF, PCI issues?
[    6.196885] iwlwifi: probe of 0000:02:00.0 failed with error -5

Could you help to check above debug message, and give us some suggestion for this issue?

And if use Intel Wireless-AC 9260 with Ubuntu 18.04.2 LTS, after do
# sudo apt-get update
# sudo apt-get dist-upgrade
then Wi-Fi can work fine.


Thanks & Regards.
USIGino

---

### Post by chili555 on 2021-05-14
Does this help?  [https://askubuntu.com/questions/1204683/intel-3165-not-working-on-ubuntu-19-10](https://askubuntu.com/questions/1204683/intel-3165-not-working-on-ubuntu-19-10)

---

### Post by ginousi on 2021-05-18
> **chili555 said:**
> Does this help?  [https://askubuntu.com/questions/1204683/intel-3165-not-working-on-ubuntu-19-10](https://askubuntu.com/questions/1204683/intel-3165-not-working-on-ubuntu-19-10)

Disabled "ACPI D3Cold Support" in BIOS menu, Wi-Fi module can work fine.
BIOS team will investigate "Disabled ACPI D3Cold Support" has any side effect.


Thanks & Regards.
USIGino

---

