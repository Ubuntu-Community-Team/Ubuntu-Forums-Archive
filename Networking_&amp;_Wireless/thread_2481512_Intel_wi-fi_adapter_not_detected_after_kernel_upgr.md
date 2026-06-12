---
title: "Intel wi-fi adapter not detected after kernel upgrade today"
date: 2022-12-01
forum: Networking &amp; Wireless
---

### Post by jsvidyad on 2022-12-01
Hello,
    My intel wifi adapter is not working after a kernel upgrade from the ubuntu repos. I am running ubuntu 22.04. The output of some commands are given below:
$ lspci | grep -i network
0000:00:14.3 Network controller: Intel Corporation Wi-Fi 6 AX201 (rev 30)
$ uname -r
5.15.0-56-generic

---

### Post by chili555 on 2022-12-01
Please run these terminal commands and post the result:

```
sudo modprobe iwlwifi
sudo dmesg | grep iwl
sudo dpkg -s linux-modules-extra-$(uname -r) | grep Status
```

---

### Post by jsvidyad on 2022-12-01
'sudo modprobe iwlwifi' gives no output.

$sudo dmesg | grep iwl
[    2.387820] Loading modules backported from iwlwifi
[    2.387821] iwlwifi-stack-public:master:9858:4c7cba27
[    2.417358] iwlwifi 0000:00:14.3: enabling device (0000 -> 0002)
[    2.423841] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-QuZ-a0-hr-b0-73.ucode failed with error -2
[    2.424281] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-QuZ-a0-hr-b0-72.ucode failed with error -2
[    2.425960] iwlwifi 0000:00:14.3: api flags index 2 larger than supported by driver
[    2.425975] iwlwifi 0000:00:14.3: TLV_FW_FSEQ_VERSION: FSEQ Version: 89.3.35.37
[    2.426324] iwlwifi 0000:00:14.3: loaded firmware version 71.058653f6.0 QuZ-a0-hr-b0-71.ucode op_mode iwlmvm
[    2.530995] iwlwifi 0000:00:14.3: Detected Intel(R) Wi-Fi 6 AX201 160MHz, REV=0x351
[    2.693343] iwlwifi 0000:00:14.3: Detected RF HR B5, rfid=0x10a100
[    2.759056] iwlwifi 0000:00:14.3: base HW address: bc:6e:e2:29:d5:e7
[    2.829495] iwlwifi 0000:00:14.3 wlp0s20f3: renamed from wlan0

$sudo dpkg -s linux-modules-extra-$(uname -r) | grep Status
Status: install ok installed

---

### Post by chili555 on 2022-12-01
Nothing there looks remarkable; i.e. wrong and fixable; yet you say it isn't working. Please explain.

Does is scan and see networks?

```
nmcli device wifi list
```Is the airplane mode switch set to enable wireless? ```
rfkill list all
```When you click the Network Manager icon and try to connect, what happens? Does it try to connect? Does it ask for your password? Sparks? Smoke? Funny noises? ```
sudo dmesg | grep wlp
```What, exactly, is not working?

---

### Post by jsvidyad on 2022-12-10
$ nmcli device wifi list
IN-USE  BSSID  SSID  MODE  CHAN  RATE  SIGNAL  BARS  SECURITY

$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

$sudo dmesg | grep wlp
[    3.304414] iwlwifi 0000:00:14.3 wlp0s20f3: renamed from wlan0

Network Manager does not show any wireless networks.

---

