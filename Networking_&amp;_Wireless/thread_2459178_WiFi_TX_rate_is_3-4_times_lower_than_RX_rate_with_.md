---
title: "WiFi TX rate is 3-4 times lower than RX rate with Intel AX200 adapter"
date: 2021-03-12
forum: Networking &amp; Wireless
---

### Post by thesaver on 2021-03-12
Hello everyone,


I made the jump to Ubuntu from Windows 10. However, I have an issue that I have not been able to fix.

My WiFi experience is noticeably slower on Ubuntu than on Windows 10. When I download the speed is very quick, however, when I send it is 3-4 times slower.

I tried to look into it as best as I could, as I just switched to Ubuntu from Windows 10, and found the following while running wavemon which was quite interesting:
```
rx rate: 520.0 Mbit/s VHT-MCS 3 160MHz short GI VHT-NSS 2, tx rate: 130.0 Mbit/s VHT-MCS 3 80MHz short GI VHT-NSS 1
```

I tried to look into people's suggestions only on how to fix it, but I have been unable to and therefore I decided to write this thread.
Some threads suggested to disable power management which I did, but with no noticeable result (copied from wavemon):
```
power mgt: off,  tx-power: 22 dBm (158.49 mW)
```

I have tried to use the newest firmware version 59 (iwlwifi-cc-a0-59.ucode), but it doesn't load even though I put it into /lib/firmware
```
$ dmesg | grep iwlwifi
[    3.780671] iwlwifi 0000:06:00.0: enabling device (0000 -> 0002)
[    3.784628] iwlwifi 0000:06:00.0: Direct firmware load for iwlwifi-cc-a0-56.ucode failed with error -2
[    3.786304] iwlwifi 0000:06:00.0: api flags index 2 larger than supported by driver
[    3.786313] iwlwifi 0000:06:00.0: TLV_FW_FSEQ_VERSION: FSEQ Version: 89.3.35.22
[    3.786315] iwlwifi 0000:06:00.0: Found debug destination: EXTERNAL_DRAM
[    3.786316] iwlwifi 0000:06:00.0: Found debug configuration: 0
[    3.786526] iwlwifi 0000:06:00.0: loaded firmware version 55.d9698065.0 cc-a0-55.ucode op_mode iwlmvm
[    3.786703] iwlwifi 0000:06:00.0: Direct firmware load for iwl-debug-yoyo.bin failed with error -2
[    3.933074] iwlwifi 0000:06:00.0: Detected Intel(R) Wi-Fi 6 AX200 160MHz, REV=0x340
[    4.108804] iwlwifi 0000:06:00.0: base HW address: dc:fb:48:28:cb:a7
[    4.416875] iwlwifi 0000:06:00.0 wlp6s0: renamed from wlan0
```


In my /etc/modprobe.d/iwlwifi.conf file I also tried to add the following line which I found in several threads without any difference:
```
options iwlwifi 11n_disable=8 swcrypto=1 power_save=0 bt_coex_active=0

```

This is the version I am currently running:
```
uname -r
5.8.0-44-generic
```

How can I make the TX speed as fast as the RX speed?

Thank you for reading this

---

