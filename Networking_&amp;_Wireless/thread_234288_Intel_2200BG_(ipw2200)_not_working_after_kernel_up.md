---
title: "Intel 2200BG (ipw2200) not working after kernel update"
date: 2006-08-11
forum: Networking &amp; Wireless
---

### Post by NiklasV on 2006-08-11
Hi

I installed Ubuntu on my brothers laptop (Toshiba Dynabook VX/470LS), and the wireless network was working great, until I updated the kernel.
It updated to kernel 2.6.15.26-386 from 2.6.15.23-386. The wireless card no longer shows up in the network settings and neither iwconfig or ifconfig has any record of it.

It's an Intel 2200BG, and as far as I know, it used the ipw2200 driver.

I tried booting with the old kernel, but I still had the same problem.

I grepped /var/log/messages and /var/log/dmesg:

**grep ipw2200 /var/log/messages:**
Aug 11 13:37:12 localhost kernel: [17179588.396000] ipw2200: Intel(R) PRO/Wirele ss 2200/2915 Network Driver, 1.1.1
Aug 11 13:37:12 localhost kernel: [17179588.396000] ipw2200: Copyright(c) 2003-2 006 Intel Corporation
Aug 11 13:37:12 localhost kernel: [17179588.396000] Warning: PCI driver ipw2200 has a struct device_driver shutdown method, please update!
Aug 11 13:37:12 localhost kernel: [17179588.920000] ipw2200: Detected Intel PRO/ Wireless 2200BG Network Connection
Aug 11 13:37:12 localhost kernel: [17179594.696000] ipw2200: probe of 0000:05:04 .0 failed with error -5
Aug 11 13:46:37 localhost kernel: [4294686.278000] ipw2200: Intel(R) PRO/Wireles s 2200/2915 Network Driver, 1.1.1
Aug 11 13:46:37 localhost kernel: [4294686.278000] ipw2200: Copyright(c) 2003-20 06 Intel Corporation
Aug 11 13:46:37 localhost kernel: [4294686.278000] Warning: PCI driver ipw2200 h as a struct device_driver shutdown method, please update!
Aug 11 13:46:37 localhost kernel: [4294686.278000] ipw2200: Detected Intel PRO/W ireless 2200BG Network Connection
Aug 11 13:46:37 localhost kernel: [4294692.422000] ipw2200: probe of 0000:05:04. 0 failed with error -5
Aug 11 13:51:18 localhost kernel: [17179591.132000] ipw2200: Intel(R) PRO/Wirele ss 2200/2915 Network Driver, 1.1.1
Aug 11 13:51:18 localhost kernel: [17179591.132000] ipw2200: Copyright(c) 2003-2 006 Intel Corporation
Aug 11 13:51:18 localhost kernel: [17179591.132000] Warning: PCI driver ipw2200 has a struct device_driver shutdown method, please update!
Aug 11 13:51:18 localhost kernel: [17179591.132000] ipw2200: Detected Intel PRO/ Wireless 2200BG Network Connection
Aug 11 13:51:18 localhost kernel: [17179596.924000] ipw2200: probe of 0000:05:04 .0 failed with error -5

**grep ipw2200 /var/log/dmesg:**
[17179591.132000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.1
[17179591.132000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17179591.132000] Warning: PCI driver ipw2200 has a struct device_driver shutdown method, please update!
[17179591.132000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[17179592.460000] ipw2200: Failed to send TX_POWER: Command timed out.
[17179593.576000] ipw2200: Failed to send TX_POWER: Command timed out.
[17179594.692000] ipw2200: Failed to send TX_POWER: Command timed out.
[17179595.808000] ipw2200: Failed to send TX_POWER: Command timed out.
[17179596.924000] ipw2200: Failed to send TX_POWER: Command timed out.
[17179596.924000] ipw2200: Unable to initialize device after 5 attempts.
[17179596.924000] ipw2200: failed to register network device
[17179596.924000] ipw2200: probe of 0000:05:04.0 failed with error -5

Any help with this would be greatly appreciated.

/Niklas

---

