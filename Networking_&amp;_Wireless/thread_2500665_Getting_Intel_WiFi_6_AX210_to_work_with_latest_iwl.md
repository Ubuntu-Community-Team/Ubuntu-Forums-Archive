---
title: "Getting Intel WiFi 6 AX210 to work with latest iwlwifi firmare on Ubuntu 22.04"
date: 2024-09-08
forum: Networking &amp; Wireless
---

### Post by linux-berlin on 2024-09-08
Hey everyone!

I'm currently trying to get my Intel WiFi 6 AX210 network card (WiFi + Bluetooth) to work with the latest iwlwifi firmware (**iwlwifi-ty-a0-gf-a0-89.ucode**). This is included in the kernel 6.10+, but Ubuntu 22.04 currently only supports kernel 6.8+ (HWE, which I am running).

Manually copying **iwlwifi-ty-a0-gf-a0-89.ucode **into /lib/firmware/ sadly does not work, as the system won't accept it - even when renamed to **iwlwifi-ty-a0-gf-a0-86.ucode **(the latest version currently supported by kernel 6.8+). 
The error message from the command "[FONT=arial]dmesg | grep iwlwifi[/FONT]" is: ```
Driver unable to support your firmware API. Driver supports v86, firmware is v89.
```

Can someone please point me in the right direction? I would be so glad, since some Bluetooth features seem to be only supported by the newest driver.

Greetings!

---

