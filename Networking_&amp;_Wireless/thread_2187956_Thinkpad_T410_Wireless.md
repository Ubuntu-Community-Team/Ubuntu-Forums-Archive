---
title: "Thinkpad T410 Wireless"
date: 2013-11-14
forum: Networking &amp; Wireless
---

### Post by neumaster456 on 2013-11-14
Im looking for help with an unstable connection on my Thinkpad t410 with the Broadcom (intel) Centrino Ultimate-N 6300. I was trying to disable wireless N and now i cannot connect to a network at all. Is it possible to reinstall the driver? Thanks, Andy

---

### Post by chili555 on 2013-11-14
There is no connection between Broadcom and Intel. I suggest we confirm your device as well as gather some other diagnostics. Please open a terminal and run and post:```
lspci -nn | grep 0280
lsb_release -d
cat /etc/modprobe.d/iwlwifi.conf
dmesg | grep iwl
```

---

### Post by neumaster456 on 2013-11-16
lspci -nn | grep 0280: Network controller [0280]: Intel Corporation Centrino Ultimate-N 6300 [8086:4238] (rev 35)  lsb_release -d: Ubuntu 12.04 LTS  cat /etc/modprobe.d/iwlwifi.conf: options  iwlwifi 11n_disable=0 (i had this disabled at one point without sucsess but id still retry it)  dmesg | grep iwl  [   25.231776] iwlwifi 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 [   25.231814] iwlwifi 0000:03:00.0: setting latency timer to 64 [   25.231867] iwlwifi 0000:03:00.0: pci_resource_len = 0x00002000 [   25.231870] iwlwifi 0000:03:00.0: pci_resource_base = ffffc900110b0000 [   25.231873] iwlwifi 0000:03:00.0: HW Revision ID = 0x35 [   25.232031] iwlwifi 0000:03:00.0: irq 44 for MSI/MSI-X [   25.232119] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Ultimate-N 6300 AGN, REV=0x74 [   25.232357] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S [   25.248626] iwlwifi 0000:03:00.0: device EEPROM VER=0x436, CALIB=0x6 [   25.248631] iwlwifi 0000:03:00.0: Device SKU: 0X1f0 [   25.248633] iwlwifi 0000:03:00.0: Valid Tx ant: 0X7, Valid Rx ant: 0X7 [   25.248748] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels [   25.445915] iwlwifi 0000:03:00.0: loaded firmware version 9.221.4.1 build 25532 [   25.448608] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs' [   26.737751] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S [   26.744349] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1 [   26.986719] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S [   26.993350] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1 [   40.116128] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S [   40.122736] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1 [   40.803257] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S [   40.809898] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1 [   42.927426] iwlwifi 0000:03:00.0: Error sending REPLY_ADD_STA: time out after 2000ms. [   42.927430] iwlwifi 0000:03:00.0: Current CMD queue read_ptr 13 write_ptr 14 [   42.927433] iwlwifi 0000:03:00.0: Adding station ff:ff:ff:ff:ff:ff failed. [   42.937451] iwlwifi 0000:03:00.0: ACTIVATE a non DRIVER active station id 15 addr ff:ff:ff:ff:ff:ff [   42.937777] iwlwifi 0000:03:00.0: HCMD_ACTIVE already clear for command REPLY_QOS_PARAM [   43.289678] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S [   43.296380] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1 [   43.541252] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S [   43.547941] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1 [   45.676183] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S [   45.682828] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1 [   53.240310] iwlwifi 0000:03:00.0: Queue 2 stuck for 2000 ms. [   53.240317] iwlwifi 0000:03:00.0: Current read_ptr 98 write_ptr 55 [   53.240321] iwlwifi 0000:03:00.0: On demand firmware reload [   53.244813] iwlwifi 0000:03:00.0: Failing on timeout while stopping DMA channel 1 [0x07fd0001] [   53.245517] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S [   53.252093] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1 [   79.795746] iwlwifi 0000:03:00.0: Queue 2 stuck for 2000 ms. [   79.795751] iwlwifi 0000:03:00.0: Current read_ptr 6 write_ptr 223 [   79.795753] iwlwifi 0000:03:00.0: On demand firmware reload [   79.800261] iwlwifi 0000:03:00.0: Failing on timeout while stopping DMA channel 1 [0x07fd0001] [   79.801020] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S [   79.807630] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1 [   92.439837] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S [   92.446439] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1 [   92.836751] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S [   92.843369] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1 [  109.274590] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S [  109.281216] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1 [  109.608300] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S [  109.614996] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1 [  110.325653] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S [  110.332369] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1 [  110.861397] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S [  110.868073] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1 [  112.945485] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S [  112.952340] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1 [ 2644.894163] iwlwifi 0000:03:00.0: RF_KILL bit toggled to disable radio. [ 2644.894467] iwlwifi 0000:03:00.0: Not sending command - RF KILL [ 2644.894532] iwlwifi 0000:03:00.0: Error sending REPLY_QOS_PARAM: enqueue_hcmd failed: -5 [ 2644.894539] iwlwifi 0000:03:00.0: Failed to update QoS [ 2644.894545] iwlwifi 0000:03:00.0: Not sending command - RF KILL [ 2644.894549] iwlwifi 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5 [ 2644.894553] iwlwifi 0000:03:00.0: Error clearing ASSOC_MSK on BSS (-5) [ 2644.894576] iwlwifi 0000:03:00.0: Not sending command - RF KILL [ 2644.894580] iwlwifi 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5 [ 2644.894584] iwlwifi 0000:03:00.0: Error clearing ASSOC_MSK on BSS (-5) [ 2644.920677] iwlwifi 0000:03:00.0: Not sending command - RF KILL [ 2644.920686] iwlwifi 0000:03:00.0: Error sending REPLY_ADD_STA: enqueue_hcmd failed: -5 [ 2644.932906] iwlwifi 0000:03:00.0: Not sending command - RF KILL [ 2644.932910] iwlwifi 0000:03:00.0: Error sending REPLY_ADD_STA: enqueue_hcmd failed: -5 [ 2644.932949] iwlwifi 0000:03:00.0: Not sending command - RF KILL [ 2644.932953] iwlwifi 0000:03:00.0: Error sending REPLY_REMOVE_STA: enqueue_hcmd failed: -5 [ 2644.932956] iwlwifi 0000:03:00.0: Error removing station a0:f3:c1:83:c8:f2 [ 2644.936962] iwlwifi 0000:03:00.0: Not sending command - RF KILL [ 2644.936966] iwlwifi 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5 [ 2644.936969] iwlwifi 0000:03:00.0: Error clearing ASSOC_MSK on BSS (-5) [ 2644.937016] iwlwifi 0000:03:00.0: Not sending command - RF KILL [ 2644.937019] iwlwifi 0000:03:00.0: Error sending REPLY_LEDS_CMD: enqueue_hcmd failed: -5 [ 2644.937025] iwlwifi 0000:03:00.0: Not sending command - RF KILL [ 2644.937028] iwlwifi 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5 [ 2644.937031] iwlwifi 0000:03:00.0: Error clearing ASSOC_MSK on BSS (-5) [ 2644.952618] iwlwifi 0000:03:00.0: Not sending command - RF KILL [ 2644.952627] iwlwifi 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5 [ 2644.952636] iwlwifi 0000:03:00.0: Error clearing ASSOC_MSK on BSS (-5) [ 2648.302988] iwlwifi 0000:03:00.0: RF_KILL bit toggled to enable radio. [ 2648.306651] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S [ 2648.313319] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1 [ 2662.216072] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S [ 2662.222758] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1 [ 2662.746679] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S [ 2662.753340] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1 [ 2663.202609] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S [ 2663.209279] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1 [ 2663.604252] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S [ 2663.610887] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1 [ 2665.652678] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S [ 2665.659307] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1 [ 3034.349147] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S [ 3034.355774] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1 [ 3034.636272] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S [ 3034.642884] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1 [ 3048.746539] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S [ 3048.753198] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1 [ 3049.335023] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S [ 3049.341689] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1 [ 3049.754907] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S [ 3049.761569] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1 [ 3050.117194] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S [ 3050.123870] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1 [ 3052.407100] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S [ 3052.413739] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1

---

### Post by neumaster456 on 2013-11-16
I apologize but whenever i try to post it turns into one line.

---

### Post by chili555 on 2013-11-16
> cat /etc/modprobe.d/iwlwifi.conf: options iwlwifi 11n_disable=0I'd switch this back to 11n_disable=1.> [ 2644.920677] iwlwifi 0000:03:00.0: Not sending command - RF KILL
[ 2644.920686] iwlwifi 0000:03:00.0: Error sending REPLY_ADD_STA: enqueue_hcmd failed: -5Ouch! What does this tell us?```
rfkill list all
```And what is the position of this little switch? [https://lh4.googleusercontent.com/-KmM8G-kKqzA/TYqxLyTS5OI/AAAAAAAADN0/7te05atqMEc/s400/Screen+shot+2011-03-23+at+9.39.36+PM.png](https://lh4.googleusercontent.com/-KmM8G-kKqzA/TYqxLyTS5OI/AAAAAAAADN0/7te05atqMEc/s400/Screen+shot+2011-03-23+at+9.39.36+PM.png)

---

### Post by neumaster456 on 2013-11-16
I should clarify that after some work i now am able to get internet acsess; however, it is very finiky and tempermental.  SUDO rfkill list all  0: tpacpi_bluetooth_sw: Bluetooth 	Soft blocked: no 	Hard blocked: no 2: phy0: Wireless LAN 	Soft blocked: no 	Hard blocked: no 3: hci0: Bluetooth 	Soft blocked: no 	Hard blocked: no

---

### Post by chili555 on 2013-11-16
> after some work What, specifically? Did you change the conf file and reboot?

---

### Post by neumaster456 on 2013-11-16
No, I reinstalled iwlwifi. And it dose work. but it's still not right. certain pages won't load or takes a long time to load, it dropps connection, and has difficulty connecting to ap's.

---

### Post by chili555 on 2013-11-16
> **neumaster456 said:**
> No, I reinstalled iwlwifi. And it dose work. but it's still not right. certain pages won't load or takes a long time to load, it dropps connection, and has difficulty connecting to ap's.How did you reinstall iwlwifi? And did you change to 11n_disable=1?

---

### Post by neumaster456 on 2013-11-17
Yes I changed it back, not really sure if its making a difference but im not having any issues thus far. install may not have been the best description. I followed this and after that the wireless works, but its still not right.         [https://wiki.debian.org/iwlwifi](https://wiki.debian.org/iwlwifi)

---

### Post by chili555 on 2013-11-17
I'll be happy to help you in any way I can, but this implies all is well now:>  im not having any issues thus far. ...but this implies you are *still* having trouble:> after that the wireless works, but its still not right.Before you make any other changes, please test for a day or so and tell us in detail what's happening.

---

### Post by antonio-aloisio on 2014-06-05
Hi,
the wifi doesn't work AT ALL with my T410 running ubuntu 14.04.
As described here the only way to get it working has been to disable the N.
So there is a bug in the driver I guess.. or at least a bug in the driver shipped with the latest ubuntu version.
In the previous one (13.10) the wireless was randomly not working.

---

### Post by chili555 on 2014-06-05
In my T410i, my Intel wireless works perfectly, so whatever the bug, it may be responsive to a few tweaks. Let's verify a few things:```
lspci -nn | grep 0280
dmesg | grep iwl
```Thanks.

---

