---
title: "Wifi disconnect after suspend in 16.04. No solutions have worked!"
date: 2016-11-07
forum: Networking &amp; Wireless
---

### Post by silverblade1010 on 2016-11-07
I am a new Ubuntu user and have so far really enjoyed it. However, I spent around 5 hours this weekend trying to get my wifi to resume after my laptop wakes from sleep mode (it works if i reboot). I have scoured message boards and all the links on google are purple 3 or 4 pages in for every search result on this matter. Therefore, I don't think this question will be a repeat.
I have

[LIST]
[*]A Dell Inspiron 15
[*]AMD A6-6310
[*]Ubuntu A6-6310
[*]My wireless card is labeled as (device) wlp3s0 (driver) ath9k
[/LIST]

```
########## wireless info START ##########


Report from: 07 Nov 2016 13:53 CET +0100


Booted last: 07 Nov 2016 00:00 CET +0100


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.1 LTS
Release:	16.04
Codename:	xenial


##### kernel ############################


Linux 4.4.0-45-generic #66-Ubuntu SMP Wed Oct 19 14:12:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Dell RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [1028:0657]
	Kernel driver in use: r8169


03:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
	Subsystem: Dell QCA9565 / AR9565 Wireless Network Adapter [1028:020c]
	Kernel driver in use: ath9k


##### lsusb #############################


Bus 002 Device 005: ID 1bcf:2b8b Sunplus Innovation Technology Inc. 
Bus 002 Device 004: ID 04f3:034e Elan Microelectronics Corp. 
Bus 002 Device 006: ID 0cf3:0036 Atheros Communications, Inc. 
Bus 002 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no


##### lsmod #############################


ath9k                 143360  0
ath9k_common           36864  1 ath9k
ath9k_hw              466944  2 ath9k_common,ath9k
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
dell_wmi               16384  0
sparse_keymap          16384  1 dell_wmi
mac80211              737280  1 ath9k
ath3k                  20480  0
cfg80211              565248  4 ath,ath9k_common,ath9k,mac80211
bluetooth             520192  30 bnep,ath3k,btbcm,btrtl,btusb,rfcomm,btintel
dell_laptop            20480  0
dcdbas                 16384  1 dell_laptop
wmi                    20480  2 dell_led,dell_wmi
video                  40960  2 dell_wmi,dell_laptop
```



and I have tried the following:
I have put these into a config folder in /config.d
SUSPEND_MODULES="$SUSPEND_MODULES ath9k"

SUSPEND_MODULES="ath9k"
I have created executable files in /sleep.d such as:
```
#!/bin/sh
#Tell Network Manager that resume was successful
case "$1" in
thaw)
/usr/bin/nmcli nm sleep false
;;
esac
```

```
#!/bin/sh

case "${1}" in
resume|thaw)
nmcli r wifi off && nmcli r wifi on ;;
esac
```
and many other variants thereof.
Also, this restarts the NetworkManager but does not connect wifi again:
sudo service network-manager restart
There are a couple other things I have tried that I can't exactly remember with commands like nmcli d wifi on, or something. They didnt work.
Now, I may be wrong, but I think the problem might lie in this:
sudo nmcli nm sleep false
Now, my terminal does NOT recognize "nm" and says:
sudo nmcli nm sleep false
and when I pull up the menu for nmcli, nm is nowhere in the object list. I feel like this might be the key to the problem. So, is there anything that I haven't done that I should do and is there any way to "fix" the "nm" problem? Thanks in advance!

---

### Post by ealgiros on 2017-01-26
Same problem here, but on Ubuntu 16.10, driver also ath9k (qualcomm atheros ar1005)

---

### Post by wildmanne39 on 2017-01-26
> **ealgiros said:**
> Same problem here, but on Ubuntu 16.10, driver also ath9k (qualcomm atheros ar1005)

Please start your own thread in networking with a descriptive title and run and post the results from the wireless script in my signature.

---

