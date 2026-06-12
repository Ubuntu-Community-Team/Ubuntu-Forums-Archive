---
title: "Unable to enable Wireless on Lenovo L340"
date: 2019-12-16
forum: Networking &amp; Wireless
---

### Post by scaryterry2903 on 2019-12-16
Hi,
I have a Lenovo L340-15IWL laptop running Ubuntu 18.04.03. 
```
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.3 LTS
Release:    18.04
Codename:    bionic

```
Some days ago, my trackpad magically stopped working. It just refused to recognise the track-pad. So I googled around a bit and found a post saying upgrading the kernel will help. So I upgraded my kernel to ```
4.19.15-041915-generic
```.

But after this, although my trackpad started working, the wireless module completely stopped working. It started showing "No Wi-Fi adapter Found" in the wireless tab in settings.
Since I already had Windows sideloaded on this, I fired that up and confirmed that wireless works fine. The device manager there shows "Intel 9462" is the wireless module. 

lshw -C network shows this as a description for wireless.
```
  *-network UNCLAIMED       
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 14.3
       bus info: pci@0000:00:14.3
       version: 30
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: memory:a1218000-a121bfff

```

I tried copying firmware from intel's website [https://www.intel.com/content/www/us/en/support/articles/000005511/network-and-io/wireless-networking.html](https://www.intel.com/content/www/us/en/support/articles/000005511/network-and-io/wireless-networking.html) and pasting it to ```
/lib/firmware/
``` but that only made the wireless adapter constantly switch on and off. As of now, I have removed all files with iwl*.ucode from the /lib/firmware/ folder and moved them elsewhere. So the wireless adapter switching on/off has stopped and my system now says that I have no wireless adapter.

Could anyone help me with finding the right driver for this wireless adapter and the procedure to fix the issue please?

---

### Post by chili555 on 2019-12-16
The driver will not ever work without proper firmware. Please move the firmware back and reboot. Next, run and post:```
sudo modprobe iwlwifi
dmesg | grep iwl
lspci -nnk | grep 0280 -A3
```

---

### Post by scaryterry2903 on 2019-12-17
> **chili555 said:**
> The driver will not ever work without proper firmware. Please move the firmware back and reboot. Next, run and post:```
sudo modprobe iwlwifi
dmesg | grep iwl
lspci -nnk | grep 0280 -A3
```

This is the list of firmware I have in my /lib/firmware location
```

-Lenovo-IdeaPad-L340-15IWL:/lib/firmware$ ls iwl*.ucode
iwlwifi-1000-5.ucode   iwlwifi-3168-29.ucode    iwlwifi-7260-9.ucode    iwlwifi-8000C-13.ucode             iwlwifi-9000-pu-b0-jf-b0-41.ucode
iwlwifi-100-5.ucode    iwlwifi-3945-2.ucode     iwlwifi-7265-10.ucode   iwlwifi-8000C-16.ucode             iwlwifi-9000-pu-b0-jf-b0-43.ucode
iwlwifi-105-6.ucode    iwlwifi-4965-2.ucode     iwlwifi-7265-12.ucode   iwlwifi-8000C-21.ucode             iwlwifi-9260-th-b0-jf-b0-33.ucode
iwlwifi-135-6.ucode    iwlwifi-5000-5.ucode     iwlwifi-7265-13.ucode   iwlwifi-8000C-22.ucode             iwlwifi-9260-th-b0-jf-b0-34.ucode
iwlwifi-2000-6.ucode   iwlwifi-5150-2.ucode     iwlwifi-7265-16.ucode   iwlwifi-8000C-27.ucode             iwlwifi-9260-th-b0-jf-b0-38.ucode
iwlwifi-2030-6.ucode   iwlwifi-6000-4.ucode     iwlwifi-7265-17.ucode   iwlwifi-8000C-31.ucode             iwlwifi-9260-th-b0-jf-b0-41.ucode
iwlwifi-3160-10.ucode  iwlwifi-6000g2a-5.ucode  iwlwifi-7265-8.ucode    iwlwifi-8000C-34.ucode             iwlwifi-9260-th-b0-jf-b0-43.ucode
iwlwifi-3160-12.ucode  iwlwifi-6000g2a-6.ucode  iwlwifi-7265-9.ucode    iwlwifi-8000C-36.ucode             iwlwifi-9260-th-b0-jf-b0-46.ucode
iwlwifi-3160-13.ucode  iwlwifi-6000g2b-6.ucode  iwlwifi-7265D-10.ucode  iwlwifi-8265-21.ucode              iwlwifi-cc-a0-46.ucode
iwlwifi-3160-16.ucode  iwlwifi-6050-5.ucode     iwlwifi-7265D-12.ucode  iwlwifi-8265-22.ucode              iwlwifi-cc-a0-48.ucode
iwlwifi-3160-17.ucode  iwlwifi-7260-10.ucode    iwlwifi-7265D-13.ucode  iwlwifi-8265-27.ucode              iwlwifi-Qu-b0-hr-b0-48.ucode
iwlwifi-3160-7.ucode   iwlwifi-7260-12.ucode    iwlwifi-7265D-16.ucode  iwlwifi-8265-31.ucode              iwlwifi-Qu-b0-jf-b0-48.ucode
iwlwifi-3160-8.ucode   iwlwifi-7260-13.ucode    iwlwifi-7265D-17.ucode  iwlwifi-8265-34.ucode              iwlwifi-Qu-c0-hr-b0-48.ucode
iwlwifi-3160-9.ucode   iwlwifi-7260-16.ucode    iwlwifi-7265D-21.ucode  iwlwifi-8265-36.ucode              iwlwifi-Qu-c0-jf-b0-48.ucode
iwlwifi-3168-21.ucode  iwlwifi-7260-17.ucode    iwlwifi-7265D-22.ucode  iwlwifi-9000-pu-b0-jf-b0-33.ucode  iwlwifi-QuZ-a0-hr-b0-48.ucode
iwlwifi-3168-22.ucode  iwlwifi-7260-7.ucode     iwlwifi-7265D-27.ucode  iwlwifi-9000-pu-b0-jf-b0-34.ucode  iwlwifi-QuZ-a0-jf-b0-48.ucode
iwlwifi-3168-27.ucode  iwlwifi-7260-8.ucode     iwlwifi-7265D-29.ucode  iwlwifi-9000-pu-b0-jf-b0-38.ucode

```

Output of grep iwl I have attached in the text file.


```
lspci -nnk | grep 0280 -A300:14.3 Network controller [0280]: Intel Corporation Device [8086:9df0] (rev 30)
    Subsystem: Intel Corporation Device [8086:02a4]
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi

```

---

### Post by chili555 on 2019-12-17
This will be a little bit of a long shot because your device is so new, detailed information, bug reports, forum posts, etc. are sparse.

With a working internet connection by ethernet, tethered or whatever means possible, please do:

```
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.183_all.deb
sudo dpkg -i linux*.deb
sudo apt update
sudo apt install linux-oem-osp1
```Reboot and show us:```
dmesg | grep iwl
```

---

### Post by scaryterry2903 on 2019-12-18
> **chili555 said:**
> 
Reboot and show us:```
dmesg | grep iwl
```

It worked!

uname -r shows kernel version  ```
5.0.0-1030-oem-osp1
```

Output as below: 
```

Lenovo-IdeaPad-L340-15IWL:~$ dmesg | grep iwl
[   11.780046] iwlwifi 0000:00:14.3: Found debug destination: EXTERNAL_DRAM
[   11.780048] iwlwifi 0000:00:14.3: Found debug configuration: 0
[   11.780457] iwlwifi 0000:00:14.3: loaded firmware version 46.6bf1df06.0 op_mode iwlmvm
[   12.185189] iwlwifi 0000:00:14.3: Detected Intel(R) Dual Band Wireless AC 9462, REV=0x318
[   12.192645] iwlwifi 0000:00:14.3: Applying debug destination EXTERNAL_DRAM
[   12.192987] iwlwifi 0000:00:14.3: Allocated 0x00400000 bytes for firmware monitor.
[   12.234147] iwlwifi 0000:00:14.3: base HW address: XX:XX:XX:XX:XX:XX
[   12.410448] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   12.581222] iwlwifi 0000:00:14.3 wlp0s20f3: renamed from wlan0
[   41.924305] iwlwifi 0000:00:14.3: Applying debug destination EXTERNAL_DRAM
[   42.016713] iwlwifi 0000:00:14.3: Applying debug destination EXTERNAL_DRAM
[   42.082485] iwlwifi 0000:00:14.3: FW already configured (0) - re-configuring
[   42.093149] iwlwifi 0000:00:14.3: Conflict between TLV & NVM regarding enabling LAR (TLV = enabled NVM =disabled)
[   42.100163] iwlwifi 0000:00:14.3: BIOS contains WGDS but no WRDS
[   46.696206] iwlwifi 0000:00:14.3 wlp0s20f3: disabling HT as WMM/QoS is not supported by the AP
[   46.696210] iwlwifi 0000:00:14.3 wlp0s20f3: disabling VHT as WMM/QoS is not supported by the AP
[  507.070454] iwlwifi 0000:00:14.3: Applying debug destination EXTERNAL_DRAM
[  507.167279] iwlwifi 0000:00:14.3: Applying debug destination EXTERNAL_DRAM
[  507.232672] iwlwifi 0000:00:14.3: FW already configured (0) - re-configuring
[  507.242867] iwlwifi 0000:00:14.3: Conflict between TLV & NVM regarding enabling LAR (TLV = enabled NVM =disabled)
[  507.250280] iwlwifi 0000:00:14.3: BIOS contains WGDS but no WRDS
[  510.769539] iwlwifi 0000:00:14.3 wlp0s20f3: disabling HT as WMM/QoS is not supported by the AP
[  510.769541] iwlwifi 0000:00:14.3 wlp0s20f3: disabling VHT as WMM/QoS is not supported by the AP
[  511.135488] iwlwifi 0000:00:14.3: Unhandled alg: 0x707
[  512.056075] iwlwifi 0000:00:14.3: Unhandled alg: 0x707
[  518.917891] iwlwifi 0000:00:14.3: Unhandled alg: 0x707
[  519.122302] iwlwifi 0000:00:14.3: Unhandled alg: 0x707
[  519.839906] iwlwifi 0000:00:14.3: Unhandled alg: 0x707
[  520.248019] iwlwifi 0000:00:14.3: Unhandled alg: 0x707

```

Wireless is up, can detect and connect to networks, trackpad is working too. 

Thank you!

---

### Post by chili555 on 2019-12-18
Awesome! Glad it’s working. The searchers will appreciate your report.

---

### Post by chili555 on 2019-12-20
Please note in your dmesg:

> [  510.769539] iwlwifi 0000:00:14.3 wlp0s20f3: disabling HT as WMM/QoS is not supported by the AP
[  510.769541] iwlwifi 0000:00:14.3 wlp0s20f3: disabling VHT as WMM/QoS is not supported by the APHT is high throughput and VHT is very high throughput; that is, high speeds are disabled.

I suggest that you check in the configuration settings of the router and enable WMM (WiFi Multimedia) and/or QOS (Quality of Service). Reboot the router by power-cycling and enjoy better speeds.

---

