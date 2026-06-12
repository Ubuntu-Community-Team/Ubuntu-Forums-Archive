---
title: "Restart networking services on-failure"
date: 2018-05-23
forum: Networking &amp; Wireless
---

### Post by jeremie56100 on 2018-05-23
Hi everyone, I am looking for a solution to restart networking services when something wrong occurs at start up. To be clear I am using socketcan with two can transceiver on SPI0 and SPI1 and sometime the device tree seems to be not loaded properly (can0 is not discovered (RTNETLINK answers: no such device)

I know that in system there's Restart=on-failure parameter but I don't know if I can use it for network configuration.

Any idea about how to achieve this?

---

