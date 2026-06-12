---
title: "Testers Needed - Driver for the Realtek RTL8812BU and RTL8822BU Chipsets"
date: 2020-10-19
forum: Networking &amp; Wireless
---

### Post by morrownr on 2020-10-19
I posted an updated version of the driver for USB WiFi adapters with the Realtek RTL8812BU and RTL8822BU Chipsets today.

My testing is showing big increases in performance vs. the last released version. Realtek has put a lot of work into this new version and
it appears to be a very good driver. Here is a short iperf3 clip from my box that has an adapter with a 8812bu chipset:

Transfer         Bitrate                Retr
66.2 MBytes   556 Mbits/sec    0
62.5 MBytes   524 Mbits/sec    0
67.5 MBytes   566 Mbits/sec    0
66.2 MBytes   556 Mbits/sec    0
65.0 MBytes   545 Mbits/sec    0
67.5 MBytes   566 Mbits/sec    0

That is an average of 552 Mbps.

Location: [https://github.com/morrownr/88x2bu](https://github.com/morrownr/88x2bu)

If you have time to test and have a system with the appropriate chipsets, I would appreciate it and it would help many Ubuntu users. Please uninstall previously installed driver and read the README.md on the site. Reports can be made on the site by selecting Issues.

Thanks.

---

### Post by morrownr on 2020-10-28
Thanks to everyone that has taken the time to test this driver and provide feedback.

Based on that feedback, I have been at work adding some features and making some options easier to change. Here is a short list:

- LED control. You are now able to control the operation of the LED if your adapter has one. 
- Log level. You are now able to control the log level.
- USB 3 mode. You are now able to easily control whether the driver goes into USB 3 mode.

I'd appreciate anyone with a USB WiFi adapter that uses RTL8812bu or RTL8822bu chipsets to try the driver and provide feedback:

[COLOR=#000000]Location: [/COLOR][https://github.com/morrownr/88x2bu](https://github.com/morrownr/88x2bu)

---

