---
title: "Ugrade Sometimes Breaks Wifi"
date: 2019-06-24
forum: Networking &amp; Wireless
---

### Post by electrosteam on 2019-06-24
Lubuntu 18.04 LTS
Wifi EDUP EP-AC1607 USB adapter.
Driver rtl8812au-dkms installed using Synaptic Package Manager.

A a couple of recent offered upgrades, the Wifi stopped working.
Used Synaptic Package Manager to re-install each time.

Not an onerous task, but does this signify something wrong with my installation ?
If most reliable way forward is to re-install as necessary, then that is Ok.

The only real concern, is that the WiFi is used to download all the upgrade packages.
Am I missing any final tidy-up steps that were attempted after Wifi failure during the upgrade process ?

John.

---

### Post by jeremy31 on 2019-06-25
Something changed in dkms starting with Ubuntu 16.04, to fix the package so it works correctly with a kernel update

```
sudo -H gedit /usr/src/rtl8812au-4.3.8.12175.20140902+dfsg/dkms.conf
```

Replace 
MAKE="'make' all"
with

MAKE[0]="'make' all KVER=${kernelver}"
Save and exit gedit

---

