---
title: "Acer Qualcomm QCA9377 wireless issue"
date: 2016-05-07
forum: Networking &amp; Wireless
---

### Post by koen6 on 2016-05-07
Hello,

Using 16.04 on my acer E5-573 I installed the driver from Kalle Valo [https://github.com/kvalo/ath10k-firmware.git](https://github.com/kvalo/ath10k-firmware.git), the board was recognized but he speed is extremely low and the network not reliable.
In fact it was impossible to maintain a good connection.
As temporary solution I am now using a netgear A6100 USB card, to be connected.

wireless-info.txt.tar.gz has been added.

Any solutions for this?

---

### Post by jeremy31 on 2016-05-08
Power management is enabled on the Atheros wifi but not on the USB
See if ```
sudo iwconfig wlp3s0 power off
```

Changes the ```
iwconfig
``` results

It may also help to go into Network Manager and change IPv6 to ignore

UFW is blocking some traffic to the router that appears to be mDNS

---

### Post by koen6 on 2016-05-08
Hello,

power management off : no change, or for whatever reason I can not connect at the moment, as the network seems too low in signal.
IPv6 switched off : no change.

---

### Post by jeremy31 on 2016-05-08
Can you check the wifi card itself and see if the antennas are connected?  Latest report still shows power management: on in the ```
iwconfig
``` results

I have an external wifi that I test from time to time and the signal strength is a little better with the external antenna on it but it has never had 2x the signal strength like yours shows

---

