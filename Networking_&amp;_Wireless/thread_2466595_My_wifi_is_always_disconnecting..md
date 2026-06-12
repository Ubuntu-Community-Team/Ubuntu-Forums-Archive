---
title: "My wifi is always disconnecting."
date: 2021-08-31
forum: Networking &amp; Wireless
---

### Post by pallabkumar547 on 2021-08-31
I recently dual booted Ubuntu 20.04.3 with Windows 10 with around 60 GB partition storage in HDD. Everything seems fine but there is a major problem with wifi connection. First 15-20 mins the wifi connection will seem just fine but then the wifi starts randomly disconnecting. It is really a major productivity killer for me. i tried a few solutions but none of them worked for me. The wifi is fully functional in Windows 10. 
The wifi works for a minute or so if i restart the wifi with the code below:
```

$ nmcli radio wifi off
$ nmcli radio wifi on

```
Again i want to add that my brother also installed Ubuntu with dual boot windows 10, but he seems to have no problem with the wifi connection.

Wireless card info:

*-network
       description: Wireless interface
       product: QCA9377 802.11ac Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 31
       serial: 18:47:3d:45:19:7d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath10k_pci driverversion=5.10.0-1044-oem firmware=WLAN.TF.2.1-00021-QCARMSWP-1 ip=192.168.0.5 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:129 memory:91000000-911fffff

Kindly help me :( ...

---

### Post by morrownr on 2021-09-01
If I happened to be seeing a problem like this, I would first look at wifi ap/routers settings. That may not fix the issue but it is where I would start. Here is a list I maintain:

Recommended WiFi Router/ Access Point Settings


Note: These are general recommendations, some of which may not apply to your specific situation.


Security: Set WPA2-AES. Do not set WPA2 mixed mode or WPA or TKIP.


Channel width for 2.4G: Set 20 MHz fixed width. Do not use 40 MHz or 20/40 automatic.


Channels for 2.4G: Set channel 1 or 6 or 11 depending on the congestion at your location. Do not set automatic channel selection.


Mode for 2.4G: For best performance, set "N only" if you no longer use B or G capable devices.


Network names: Do not set the 2.4G Network and the 5G Network to the same name. Note: Unfortunately many routers come with both networks set to the same name.


Channels for 5G: Not all devices are capable of using DFS channels. It may be necessary to set a fixed channel in the range of 36 to 48 or 149 to 161 in order for all of your devices to work on 5g. (for US, other countries may vary)


Best location for the wifi router/ access point: Near center of apartment or house, at least a couple of feet away from walls, in an elevated location.


Check congestion: There are apps available for smart phones that allow you to check the congestion levels on wifi channels. The apps generally go by the name of WiFi Analyzer or something similar.


After making and saving changes, reboot the router.

---

### Post by pallabkumar547 on 2021-09-02
Hey thanks for replying but there is no problem with the router because the there is no issue in the Windows 10 os in my laptop. 
Again, the Ubuntu in my brother's laptop also has no issue with the connection.

I've also tried a neighbors wifi connection but the problem still occurs.
Again, thanks for replying.

---

### Post by morrownr on 2021-09-02
> **pallabkumar547 said:**
> Hey thanks for replying but there is no problem with the router because the there is no issue in the Windows 10 os in my laptop. 
Again, the Ubuntu in my brother's laptop also has no issue with the connection.

I've also tried a neighbors wifi connection but the problem still occurs.


While that may seem like sound logic, it is not but it is your call.

Another option you could consider is installing the Hardware Enablement Stack which currently would take you up to kernel 5.11 which could provide a more recent driver:

```
sudo apt install linux-generic-hwe-20.04
```

Also, there is a wireless info script mentioned in the following post:

[https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

You might want to run the script and post the results.

---

