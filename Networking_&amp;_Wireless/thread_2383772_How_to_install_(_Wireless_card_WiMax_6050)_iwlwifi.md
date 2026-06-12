---
title: "How to install ( Wireless card WiMax 6050) iwlwifi-6050-5.ucode??"
date: 2018-01-29
forum: Networking &amp; Wireless
---

### Post by tongmengwan on 2018-01-29
Ubuntu 16.04
The wireless card is: [COLOR=#000000][FONT=Lucida Grande]Intel Centrino Advanced N6250 AGN[/FONT][/COLOR]

I download this file from: [https://www.intel.com/content/www/us...etworking.html]("https://www.intel.com/content/www/us/en/support/articles/000005511/network-and-i-o/wireless-networking.html")

[iwlwifi-6050-ucode-41.28.5.1.tgz]("http://wireless.kernel.org/en/users/Drivers/iwlwifi?action=AttachFile&do=get&target=iwlwifi-6050-ucode-41.28.5.1.tgz")

And I expand it to get this file: 

iwlwifi-6050-5.ucode

Then I got stuck here. How to install it? I searched around but I failed. 

Thank you for help.

---

### Post by jeremy31 on 2018-01-29
It should already be installed, open a terminal window and enter
```
locate iwlwifi-6050-5.ucode
```
One result should be in /lib/firmware

---

### Post by tongmengwan on 2018-01-29
I used 
locate iwlwifi-6050-5.ucode


/lib/firmware/iwlwifi-6050-5.ucode

What does this mean?

---

### Post by chili555 on 2018-01-29
> **tongmengwan said:**
> I used 
locate iwlwifi-6050-5.ucode


/lib/firmware/iwlwifi-6050-5.ucode

What does this mean?That means that your wireless troubles, whatever they are, are not a result of missing firmware. Please tell us what's wrong.

You might get some clues from:```
dmesg | grep iwl
rfkill list all
```

---

### Post by tongmengwan on 2018-01-29
tongmengwan@tongmengwan-Precision-M6500:~$ dmesg | grep iwl
[    4.317571] iwlwifi 0000:0c:00.0: can't disable ASPM; OS doesn't have ASPM control
[    4.336274] iwlwifi 0000:0c:00.0: loaded firmware version 41.28.5.1 build 33926 op_mode iwldvm
[    4.385728] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    4.385732] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    4.385734] iwlwifi 0000:0c:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    4.385736] iwlwifi 0000:0c:00.0: Detected Intel(R) Centrino(R) Advanced-N + WiMAX 6250 AGN, REV=0x84
[    4.385832] iwlwifi 0000:0c:00.0: L1 Enabled - LTR Disabled
[    4.477110] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[    4.586059] iwlwifi 0000:0c:00.0 wlp12s0: renamed from wlan0
[    5.610431] iwlwifi 0000:0c:00.0: L1 Enabled - LTR Disabled
[    5.610635] iwlwifi 0000:0c:00.0: L1 Enabled - LTR Disabled
[    5.610720] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
[    5.844384] iwlwifi 0000:0c:00.0: L1 Enabled - LTR Disabled
[    5.844597] iwlwifi 0000:0c:00.0: L1 Enabled - LTR Disabled
[    5.844677] iwlwifi 0000:0c:00.0: Radio type=0x1-0x2-0x0
tongmengwan@tongmengwan-Precision-M6500:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
4: i2400m-usb:2-1.8:1.0: WiMAX
	Soft blocked: yes
	Hard blocked: no
tongmengwan@tongmengwan-Precision-M6500:~$

---

### Post by chili555 on 2018-01-29
Looks fine to me. What's happening or not happening as expected? Details! We need details!!

---

### Post by tongmengwan on 2018-01-29
Dual system. Win 7 and Ubuntu 16.04. [COLOR=#000000]The wireless card is: [/COLOR][COLOR=#000000][COLOR=#000000][FONT=&quot]Intel Centrino Advanced N6250 AGN. Dell M6500 [/FONT][/COLOR][/COLOR]
1. In windows, the speed is about 60mbps. Other similar laptop is about 100mbps.
2. In Linux, the speed is about 35 mbps. 

I do not know where it is wrong. Thank you !

---

### Post by Hadaka on 2018-01-29
Hi, while connected with the wireless unit you are having difficulty with,
Please COPY and Paste these commands.
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info
```

```
cat wireless-info.txt | nc termbin.com 9999
```

This will have an output that looks this...
[http://termbin.com/xxyy](http://termbin.com/xxyy) <- It wont say 'xxyy' it will be something else
copy and paste the link to your reply.
Thank you

---

