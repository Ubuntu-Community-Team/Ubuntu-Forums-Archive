---
title: "Intel Wireless AC 9560 not being detected"
date: 2018-05-23
forum: Networking &amp; Wireless
---

### Post by hyunkim95 on 2018-05-23
Currently using Ubuntu 18.04

The following is the log:
[https://pastebin.com/MWEFMMCq](https://pastebin.com/MWEFMMCq)

Any help is appreciated

---

### Post by jeremy31 on 2018-05-23
I would try ```
cd /lib/firmware
sudo wget https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/iwlwifi-9000-pu-b0-jf-b0-33.ucode
```
Reboot

---

### Post by hyunkim95 on 2018-05-23
I have installed the driver but that didn't work either - any other suggestions? Or logs I could provide that would help?

---

### Post by jeremy31 on 2018-05-23
Post results for ```
dmesg | grep iwl
```

---

### Post by hyunkim95 on 2018-05-23
```

[    6.152449] Loading modules backported from iwlwifi
[    6.152450] iwlwifi-stack-public:master:6988:0d8892f2
[    6.186773] iwlwifi 0000:00:14.3: enabling device (0000 -> 0002)
[    6.205617] iwlwifi 0000:00:14.3: Direct firmware load for iwl-dbg-cfg.ini failed with error -2
[    6.205630] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-9000-pu-b0-jf-b0-39.ucode failed with error -2
[    6.205636] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-9000-pu-b0-jf-b0-38.ucode failed with error -2
[    6.205641] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-9000-pu-b0-jf-b0-37.ucode failed with error -2
[    6.205646] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-9000-pu-b0-jf-b0-36.ucode failed with error -2
[    6.205651] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-9000-pu-b0-jf-b0-35.ucode failed with error -2
[    6.407161] iwlwifi 0000:00:14.3: loaded firmware version 34.0.0 op_mode iwlmvm
[    6.686875] iwlwifi 0000:00:14.3: Detected Intel(R) Dual Band Wireless AC 9560, REV=0x318
[    7.708118] iwlwifi 0000:00:14.3: SecBoot CPU1 Status: 0x3, CPU2 Status: 0x2459
[    7.708121] iwlwifi 0000:00:14.3: Failed to start INIT ucode: -110
[    7.720208] iwlwifi 0000:00:14.3: Failed to run INIT ucode: -110

```

---

