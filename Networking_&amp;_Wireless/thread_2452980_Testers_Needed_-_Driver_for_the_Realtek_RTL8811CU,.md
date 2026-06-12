---
title: "Testers Needed - Driver for the Realtek RTL8811CU, RTL8821CU and RTL8831AU Chipsets"
date: 2020-10-31
forum: Networking &amp; Wireless
---

### Post by morrownr on 2020-10-31
The driver is located at:

[https://github.com/morrownr/8821cu](https://github.com/morrownr/8821cu)

I have added a feature to this driver that I can't test currently as I don't have the hardware. My 8811cu device does not have an LED and I added the capability to control the LED. I would appreciate anyone with adapters based on any of the WiFi chipsets listed in the title to test and report.

Features that I have added:

- LED control. You are now able to control the operation of the LED without recompiling the driver.
- Log level. You are now able to control the log level without recompiling the driver.

Of note: This driver is based on source code very recently released by Realtek and it is feature rich, works on all released Linux kernels through v5.9 and I'm not finding any bugs.

I would appreciate any feedback regarding this driver. Are the installation instructions clear? Is the information provided in the README adequate? Etc?

Thanks.

---

### Post by bobsuncle on 2020-11-05
> **morrownr said:**
> Of note: This driver is based on source code very recently released by Realtek and it is feature rich, works on all released Linux kernels through v5.9 and I'm not finding any bugs.

This sounds great!  Do you mind posting a link to where you found the Realtek 5.8.1.7 source code?

---

