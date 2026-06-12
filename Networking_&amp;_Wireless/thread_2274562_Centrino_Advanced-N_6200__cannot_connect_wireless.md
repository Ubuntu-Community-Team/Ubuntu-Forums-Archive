---
title: "Centrino Advanced-N 6200 | cannot connect wireless"
date: 2015-04-20
forum: Networking &amp; Wireless
---

### Post by piratejackus2 on 2015-04-20
Hi folks,

For a couple of hours i tried to connect to router via wireless from a fresh installed ubuntu 14.04 on a HP EliteBook 8440p. Unfortunately i am not succeed. From my google searches nor similar posts/threads; nothing worked for me. 
Here is some info on my system:[B]

PC[/B]

```

atlas@yotbavodaka:~$ **sudo lshw -C network**
  *-network               
       description: Ethernet interface
       product: 82577LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 06
       serial: 70:5a:b6:a2:9d:c7
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k duplex=full firmware=0.12-3 ip=192.168.1.9 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:45 memory:d7400000-d741ffff memory:d7425000-d7425fff ioport:6020(size=32)
  *-network DISABLED
       description: Wireless interface
       product: Centrino Advanced-N 6200
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:44:00.0
       logical name: wlan0
       version: 35
       serial: 00:23:14:40:1f:f8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-48-generic firmware=9.221.4.1 build 25532 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:47 memory:d3200000-d3201fff

```

```

atlas@yotbavodaka:~$** lsusb**
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 04f2:b15e Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 138a:0007 Validity Sensors, Inc. VFS451 Fingerprint Reader
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
```

sudo vim /etc/modprobe.d/iwlwifi.conf

# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

```





**ROUTER** **(Huawei HG522e)**

i have access to router admin panel. Here is some router configuration:

**Mode:** 802.11 b/g/n
**11N bandwidth:** 20 MHZ
**Security:** WPA-PSK/WPA2-PSK
**WPA Keyring:** TKIP+AES
**WPS:** Disabled



1) I tried to disable N option in iwlwifi.conf file: 

```
11n_disable=1
```

and restarted but it didn't work.

2) Disabling wireless security didn't work.

3) I can connect to mobile device's hotspot.



Hope there is still hope for me (: 
Thanks in advance.

---

### Post by chili555 on 2015-04-20
> *-network DISABLED
       description: Wireless interface
       product: Centrino Advanced-N 6200
       vendor: Intel Corporation'Disabled' generally means that the wireless switch or key combination is set to turn off the wireless. You can confirm this with:```
rfkill list all
```Is the wireless hard blocked? Find and switch the switch.

---

### Post by piratejackus2 on 2015-04-20
Hi,

It was disabled as i connected to modem by wire. This is another situation but not important for now (related thread: [http://ubuntuforums.org/showthread.php?t=1621768](http://ubuntuforums.org/showthread.php?t=1621768))
Normally (without ethernet cable plugged) i can see available wifi connections and as i mentioned before, i can connect to an iphone's hotspot.

I executed lshw when ethernet cable was unplugged and here is the result:

```

atlas@yotbavodaka:~$ **sudo lshw -C network**
  *-network               
       description: Ethernet interface
       product: 82577LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 06
       serial: 70:5a:b6:a2:9d:c7
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e latency=0 multicast=yes
       resources: irq:20 memory:d7400000-d741ffff memory:d7425000-d7425fff ioport:6020(size=32)
  *-network
       description: Wireless interface
       product: Centrino Advanced-N 6200
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:44:00.0
       logical name: wlan0
       version: 35
       serial: 00:23:14:40:1f:f8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-48-generic firmware=9.221.4.1 build 25532 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:47 memory:d3200000-d3201fff

```

---

### Post by chili555 on 2015-04-20
> 1) I tried to disable N option in iwlwifi.conf file:

Code:

11n_disable=1

May we see?```
cat /etc/modprobe.d/iwlwifi.conf
dmesg | grep iwl
```When you try to connect, are you challenged for the encryption key? What happens thereafter?

---

### Post by piratejackus2 on 2015-04-20
```

atlas@yotbavodaka:~$ **cat /etc/modprobe.d/iwlwifi.conf**
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
options 11n_disable=1
atlas@yotbavodaka:~$ **dmesg | grep iwl**
[   16.109844] iwlwifi 0000:44:00.0: can't disable ASPM; OS doesn't have ASPM control
[   16.109915] iwlwifi 0000:44:00.0: irq 47 for MSI/MSI-X
[   16.257513] iwlwifi 0000:44:00.0: Direct firmware load failed with error -2
[   16.257515] iwlwifi 0000:44:00.0: Falling back to user helper
[   16.448253] iwlwifi 0000:44:00.0: Direct firmware load failed with error -2
[   16.448256] iwlwifi 0000:44:00.0: Falling back to user helper
[   16.550346] iwlwifi 0000:44:00.0: loaded firmware version 9.221.4.1 build 25532 op_mode iwldvm
[   16.582177] iwlwifi 0000:44:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   16.582178] iwlwifi 0000:44:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   16.582178] iwlwifi 0000:44:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   16.582180] iwlwifi 0000:44:00.0: Detected Intel(R) Centrino(R) Advanced-N 6200 AGN, REV=0x74
[   16.582239] iwlwifi 0000:44:00.0: L1 Disabled - LTR Disabled
[   16.582435] iwlwifi 0000:44:00.0: RF_KILL bit toggled to disable radio.
[   16.601377] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   20.481489] iwlwifi 0000:44:00.0: RF_KILL bit toggled to enable radio.
[   20.672889] iwlwifi 0000:44:00.0: L1 Disabled - LTR Disabled
[   20.673042] iwlwifi 0000:44:00.0: Radio type=0x1-0x3-0x1
[   20.882803] iwlwifi 0000:44:00.0: L1 Disabled - LTR Disabled
[   20.882958] iwlwifi 0000:44:00.0: Radio type=0x1-0x3-0x1
[   22.845317] iwlwifi 0000:44:00.0: RF_KILL bit toggled to disable radio.
[   22.917162] iwlwifi 0000:44:00.0: Not sending command - RF KILL

```


When i try to connect my wireless modem:

```

atlas@yotbavodaka:~$ **tail -f /var/log/syslog**
Apr 21 00:53:43 yotbavodaka NetworkManager[749]: <info> Activation (wlan0) starting connection 'yuvam'
Apr 21 00:53:43 yotbavodaka NetworkManager[749]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Apr 21 00:53:43 yotbavodaka NetworkManager[749]: <info> NetworkManager state is now CONNECTING
Apr 21 00:53:43 yotbavodaka NetworkManager[749]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 21 00:53:43 yotbavodaka NetworkManager[749]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 21 00:53:43 yotbavodaka NetworkManager[749]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 21 00:53:43 yotbavodaka NetworkManager[749]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 21 00:53:43 yotbavodaka NetworkManager[749]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 21 00:53:43 yotbavodaka NetworkManager[749]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Apr 21 00:53:43 yotbavodaka NetworkManager[749]: <info> (wlan0): preparing device.
Apr 21 00:53:43 yotbavodaka NetworkManager[749]: <info> **Activation (wlan0/wireless): connection 'yuvam' has security, and secrets exist.  No new secrets needed.**
Apr 21 00:53:43 yotbavodaka NetworkManager[749]: <info> Config: added 'ssid' value 'yuvam'
Apr 21 00:53:43 yotbavodaka NetworkManager[749]: <info> Config: added 'scan_ssid' value '1'
Apr 21 00:53:43 yotbavodaka NetworkManager[749]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Apr 21 00:53:43 yotbavodaka NetworkManager[749]: <info> Config: added 'auth_alg' value 'OPEN'
Apr 21 00:53:43 yotbavodaka NetworkManager[749]: <info> Config: added 'psk' value '<omitted>'
Apr 21 00:53:43 yotbavodaka NetworkManager[749]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 21 00:53:43 yotbavodaka NetworkManager[749]: <info> Config: set interface ap_scan to 1
Apr 21 00:53:36 yotbavodaka wpa_supplicant[868]: wlan0: CTRL-EVENT-SCAN-STARTED 
Apr 21 00:53:43 yotbavodaka wpa_supplicant[868]: wlan0: SME: Trying to authenticate with 14:b9:68:4e:03:58 (SSID='yuvam' freq=2452 MHz)
Apr 21 00:53:43 yotbavodaka kernel: [  336.725139] wlan0: authenticate with 14:b9:68:4e:03:58
Apr 21 00:53:43 yotbavodaka kernel: [  336.748833] wlan0: direct probe to 14:b9:68:4e:03:58 (try 1/3)
Apr 21 00:53:43 yotbavodaka NetworkManager[749]: <info> (wlan0): supplicant interface state: inactive -> authenticating
Apr 21 00:53:43 yotbavodaka kernel: [  336.948943] wlan0: direct probe to 14:b9:68:4e:03:58 (try 2/3)
Apr 21 00:53:44 yotbavodaka kernel: [  337.152880] wlan0: direct probe to 14:b9:68:4e:03:58 (try 3/3)
Apr 21 00:53:44 yotbavodaka kernel: [  337.356781] wlan0: authentication with 14:b9:68:4e:03:58 timed out
Apr 21 00:53:44 yotbavodaka NetworkManager[749]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Apr 21 00:53:44 yotbavodaka wpa_supplicant[868]: wlan0: CTRL-EVENT-SCAN-STARTED 
Apr 21 00:53:44 yotbavodaka NetworkManager[749]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Apr 21 00:54:08 yotbavodaka NetworkManager[749]: **<warn> Activation (wlan0/wireless): association took too long, failing activation.**
Apr 21 00:54:08 yotbavodaka NetworkManager[749]: **<info> (wlan0): device state change: config -> failed (reason 'SSID not found') [50 120 53]**
Apr 21 00:54:08 yotbavodaka NetworkManager[749]: **<info> NetworkManager state is now DISCONNECTED**
Apr 21 00:54:08 yotbavodaka NetworkManager[749]: **<warn> Activation (wlan0) failed for connection 'yuvam'**
Apr 21 00:54:08 yotbavodaka NetworkManager[749]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Apr 21 00:54:08 yotbavodaka NetworkManager[749]: <info> (wlan0): deactivating device (reason 'none') [0]
Apr 21 00:54:08 yotbavodaka NetworkManager[749]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Apr 21 00:54:08 yotbavodaka wpa_supplicant[868]: message repeated 3 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Apr 21 00:54:08 yotbavodaka wpa_supplicant[868]: wlan0: Reject scan trigger since one is already pending
Apr 21 00:54:08 yotbavodaka NetworkManager[749]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Apr 21 00:54:11 yotbavodaka NetworkManager[749]: <info> (wlan0): supplicant interface state: scanning -> inactive

```


**yuvam** is my modem's ssid. &#304; tried wpa also but it didn't work either. What is you ropinion?

---

### Post by chili555 on 2015-04-20
> When i try to connect my wireless modem:I'm not sure I understand. Are you referring to the Intel 6200 or something else? I thought we were working on the Intel.> [   22.845317] iwlwifi 0000:44:00.0: RF_KILL bit toggled to disable radio.
[   22.917162] iwlwifi 0000:44:00.0: Not sending command - RF KILLIt's useless to try to troubleshoot the Intel with the switch set to disable the wireless.

I'm not sure I can be of any help.> options 11n_disable=1This is supposed to be:```
options iwlwifi 11n_disable=1
```Please correct.

---

### Post by piratejackus2 on 2015-04-20
I'm very sorry, it is my mistake. But i already tried with the right option in iwlwifi

```

atlas@yotbavodaka:~$ **cat /etc/modprobe.d/iwlwifi.conf**
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
options iwlwifi 11n_disable=1

```


I have some issues with my wireless card not my router. The problem is that i cannot connect to my home wireless modem despite of the modifications that i made on modem admin panel.
I hope there's not any misunderstanding. If i'm not clear in any point please tell me.

---

### Post by chili555 on 2015-04-20
Here are some things you might try on the router. I own and use successfully two Intel wireless devices. I have honed a few techniques in several years and thousands of forum posts.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

Then let us hear the results.

---

### Post by piratejackus2 on 2015-04-20
encryption, bandwith, channel, speed.. all done and router is restarted. (screenshot of router preferences page is attached)


```

atlas@yotbavodaka:~$ cat /etc/default/crda
# Set REGDOMAIN to a ISO/IEC 3166-1 alpha2 country code so that iw(8) may set
# the initial regulatory domain setting for IEEE 802.11 devices which operate
# on this system.
#
# Governments assert the right to regulate usage of radio spectrum within
# their respective territories so make sure you select a ISO/IEC 3166-1 alpha2
# country code suitable for your location or you may infringe on local
# legislature. See `/usr/share/zoneinfo/zone.tab' for a table of timezone
# descriptions containing ISO/IEC 3166-1 alpha2 country codes.

REGDOMAIN=TR

```

Restarted PC but still can not connect.

Last step, ignored IPv6 in network manager but no goal...

Thanks for suggestions, but no result yet...

---

### Post by chili555 on 2015-04-20
> (wlan0): device state change: config -> failed (reason 'SSID not found') Does 'yuvam' actually appear in:```
sudo iwlist wlan0 scan
```Are there any clues here?```
cat /var/log/syslog | grep -e wlan -e etwork | tail -n20
```

---

### Post by piratejackus2 on 2015-04-21
My wifi **'yuvam'** appears on the list of **network manager icon** but **not on wlan0 scan** results:

```

atlas@yotbavodaka:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 20:08:ED:8D:2F:C9
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"Performance"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000018900d1eb
                    Extra: Last beacon: 72ms ago
                    IE: Unknown: 000B506572666F726D616E6365
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030103
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1603000000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD800050F204104A0001101044000102103B00010310470010B7A5C416433155FD80782E5D7B3CD13C1021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000A42726F6164636F6D4150100800020000103C0001011049000600372A000120
                    IE: Unknown: DD090010180200F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: 18:28:61:02:BF:4F
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"OlvMusteriWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004d5fa55755
                    Extra: Last beacon: 72ms ago
                    IE: Unknown: 000E4F6C764D75737465726957696669
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6E181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D16060F1600000000000000000000000000000000000000
                    IE: Unknown: DDB10050F204104A0001101049001E007FC5100018968391FAD4C2EDE5255CCDB99449444130303030303337371044000102103B000103104700109384E0B5FF9750929A42632AF2C341AE102100194169725469657320576972656C657373204E6574776F726B73102300074169723433343010240007312E372E302E371042000F4154303933313130323030333432301054000800060050F20400011011000741697234333430100800020084103C000103
                    IE: Unknown: DD09001018020BF0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336E181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34060F1600000000000000000000000000000000000000
          Cell 03 - Address: 00:1C:7B:FD:62:25
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"TOLAY"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000057c4808063
                    Extra: Last beacon: 72ms ago
                    IE: Unknown: 0005544F4C4159
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030109
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: 18:28:61:F1:B0:13
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"SUPERONLINE_Wi-Fi_1187"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000a3658e594
                    Extra: Last beacon: 72ms ago
                    IE: Unknown: 001653555045524F4E4C494E455F57692D46695F31313837
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DDB60050F204104A0001101049001E007FC51000185F82052B7025F280AA729E5F18A5D4C330303030303030311044000101103B00010310470010759D61260A875DE6BD36FB3435F0D146102100194169725469657320576972656C657373204E6574776F726B731023000941697236333732534F10240008312E302E302E35321042000F4154313039313431303031313138371054000800060050F20400011011000941697236333732534F100800020084103C000103
                    IE: Unknown: DD090010180201F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 05 - Address: 00:1A:2B:88:1F:4B
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"CBV704W-80F6"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003afb210ec4
                    Extra: Last beacon: 72ms ago
                    IE: Unknown: 000C434256373034572D38304636
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 06 - Address: E8:DE:27:66:DD:4B
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"BBRMR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000057e0ac733e
                    Extra: Last beacon: 7304ms ago
                    IE: Unknown: 00054242524D52
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706545220010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F20201018E0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0E0050F204104A0001101044000101
                    IE: Unknown: DD050050F20500
          Cell 07 - Address: 40:4A:03:7C:2D:5B
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"ZyXEL8403sne"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000ca1c2f984
                    Extra: Last beacon: 7296ms ago
                    IE: Unknown: 000C5A7958454C38343033736E65
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706545220010D14
                    IE: Unknown: 200100
                    IE: Unknown: 2A0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
          Cell 08 - Address: 1A:28:61:B8:8D:DF
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"AirTies_Air5341_2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000af63e718b
                    Extra: Last beacon: 6992ms ago
                    IE: Unknown: 0011416972546965735F416972353334315F32
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010D
                    IE: Unknown: 050402030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D160D080400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0B001CA8500101B88DDE2B0D
                    IE: Unknown: DD090010180202F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 09 - Address: FC:4A:E9:2A:1A:8B
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"buyise"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001ce1d712f7
                    Extra: Last beacon: 72ms ago
                    IE: Unknown: 0006627579697365
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFE181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D16010D1600000000000000000000000000000000000000
                    IE: Unknown: DD090010180203F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 10 - Address: E8:94:F6:FA:95:6D
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"kahraman"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001b8a640183
                    Extra: Last beacon: 1292ms ago
                    IE: Unknown: 00086B616872616D616E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030109
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 0B0500000F0000
                    IE: Unknown: 2D1AFE1817FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D16090F1100000000000000000000000000000000000000
                    IE: Unknown: 7F03000008
                    IE: Unknown: DD180050F204104A00011010440001021049000600372A000120
                    IE: Unknown: DD090010180200040C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

```




and about the syslog:

```

atlas@yotbavodaka:~$ cat /var/log/syslog | grep -e wlan -e etwork | tail -n20
Apr 21 10:16:31 yotbavodaka NetworkManager[803]: <info> Activation (eth0) Stage 5 of 5 (IPv6 Commit) complete.
Apr 21 10:16:34 yotbavodaka NetworkManager[803]: <info> WiFi hardware radio set enabled
Apr 21 10:18:02 yotbavodaka NetworkManager[803]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
Apr 21 10:18:02 yotbavodaka NetworkManager[803]: <info> WiFi now enabled by radio killswitch
Apr 21 10:18:02 yotbavodaka NetworkManager[803]: <info> (wlan0): bringing up device.
Apr 21 10:18:02 yotbavodaka kernel: [  121.021805] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr 21 10:18:02 yotbavodaka NetworkManager[803]: <info> (wlan0) supports 5 scan SSIDs
Apr 21 10:18:02 yotbavodaka NetworkManager[803]: <info> (wlan0): supplicant interface state: starting -> ready
Apr 21 10:18:02 yotbavodaka NetworkManager[803]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Apr 21 10:18:02 yotbavodaka NetworkManager[803]: <warn> Trying to remove a non-existant call id.
Apr 21 10:18:02 yotbavodaka NetworkManager[803]: <info> (wlan0): supplicant interface state: ready -> disconnected
Apr 21 10:18:02 yotbavodaka NetworkManager[803]: <info> (wlan0) supports 5 scan SSIDs
Apr 21 10:18:02 yotbavodaka wpa_supplicant[1078]: wlan0: Reject scan trigger since one is already pending
Apr 21 10:18:02 yotbavodaka wpa_supplicant[1078]: wlan0: CTRL-EVENT-SCAN-STARTED 
Apr 21 10:18:04 yotbavodaka NetworkManager[803]: <info> (wlan0): supplicant interface state: disconnected -> inactive
Apr 21 10:18:06 yotbavodaka NetworkManager[803]: <info> (eth0): device state change: activated -> unavailable (reason 'carrier-changed') [100 20 40]
Apr 21 10:18:06 yotbavodaka NetworkManager[803]: <info> (eth0): deactivating device (reason 'carrier-changed') [40]
Apr 21 10:18:07 yotbavodaka NetworkManager[803]: <info> (eth0): canceled DHCP transaction, DHCP client pid 1108
Apr 21 10:18:07 yotbavodaka NetworkManager[803]: <info> Writing DNS information to /sbin/resolvconf
Apr 21 10:18:07 yotbavodaka NetworkManager[803]: <info> NetworkManager state is now DISCONNECTED

```

---

### Post by chili555 on 2015-04-21
> My wifi 'yuvam' appears on the list of network manager icon but not on wlan0 scan results:Very weird. Let's see:```
nm-tool
sudo iwlist wlan0 chan
ls /etc/NetworkManager/system-connections
```

---

### Post by piratejackus2 on 2015-04-21
I agree with you, it's a little bit weird.

```

atlas@yotbavodaka:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             disconnected
  Default:           no
  HW Address:        00:23:14:40:1F:F8

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Performance:     Infra, 20:08:ED:8D:2F:C9, Freq 2422 MHz, Rate 54 Mb/s, Strength 87 WPA WPA2
    OlvMusteriWifi:  Infra, 18:28:61:02:BF:4F, Freq 2437 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2
    CBV704W-80F6:    Infra, 00:1A:2B:88:1F:4B, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WPA
    ASTTRAFK:        Infra, 4C:5E:0C:87:EC:D1, Freq 5280 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    buyise:          Infra, FC:4A:E9:2A:1A:8B, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA2
    yuvam:           Infra, 14:B9:68:4E:03:58, Freq 2452 MHz, Rate 54 Mb/s, Strength 100 WPA2
    TTNET_ZyXEL_VXWC:Infra, 28:28:5D:58:80:45, Freq 2447 MHz, Rate 54 Mb/s, Strength 69 WPA WPA2
    TOLAY:           Infra, 00:1C:7B:FD:62:25, Freq 2452 MHz, Rate 54 Mb/s, Strength 45 WPA2
    Aktas:           Infra, FC:F5:28:F8:8C:5D, Freq 2432 MHz, Rate 54 Mb/s, Strength 42 WPA
    EEO:             Infra, 00:C0:49:FB:1B:95, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    kahraman:        Infra, E8:94:F6:FA:95:6D, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA2
    SUPERONLINE_Wi-Fi_1187: Infra, 18:28:61:F1:B0:13, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    enki:            Infra, 94:0C:6D:B3:42:5C, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WPA
    BBRMRMain:       Infra, 00:23:69:B5:A6:03, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WEP
    BBRMR:           Infra, E8:DE:27:66:DD:4B, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WEP
    Mert7:           Infra, 00:1A:2B:93:D2:4F, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WEP


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        70:5A:B6:A2:9D:C7

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off


```


```

atlas@yotbavodaka:~$ sudo iwlist wlan0 chan
wlan0     21 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz

```


```

atlas@yotbavodaka:~$ ls /etc/NetworkManager/system-connections
Auto Ethernet  Bingul  buyise  emre  furkan  iPhone  NetMASTER Uydunet-1C90  yuvam

```

---

### Post by chili555 on 2015-04-21
> Wireless Access Points 
    Performance:     Infra, 20:08:ED:8D:2F:C9, Freq 2422 MHz, Rate 54 Mb/s, Strength 87 WPA WPA2
    OlvMusteriWifi:  Infra, 18:28:61:02:BF:4F, Freq 2437 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2
    CBV704W-80F6:    Infra, 00:1A:2B:88:1F:4B, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WPA
    ASTTRAFK:        Infra, 4C:5E:0C:87:EC:D1, Freq 5280 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    buyise:          Infra, FC:4A:E9:2A:1A:8B, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA2
    [COLOR="#FF0000"]yuvam:           Infra, 14:B9:68:4E:03:58, Freq 2452 MHz, Rate 54 Mb/s, Strength 100 WPA2[/COLOR]
    TTNET_ZyXEL_VXWC:Infra, 28:28:5D:58:80:45, Freq 2447 MHz, Rate 54 Mb/s, Strength 69 WPA WPA2
    TOLAY:           Infra, 00:1C:7B:FD:62:25, Freq 2452 MHz, Rate 54 Mb/s, Strength 45 WPA2
    Aktas:           Infra, FC:F5:28:F8:8C:5D, Freq 2432 MHz, Rate 54 Mb/s, Strength 42 WPA
    EEO:             Infra, 00:C0:49:FB:1B:95, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    kahraman:        Infra, E8:94:F6:FA:95:6D, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA2
    SUPERONLINE_Wi-Fi_1187: Infra, 18:28:61:F1:B0:13, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    enki:            Infra, 94:0C:6D:B3:42:5C, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WPA
    BBRMRMain:       Infra, 00:23:69:B5:A6:03, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WEP
    BBRMR:           Infra, E8:DE:27:66:DD:4B, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WEP
    Mert7:           Infra, 00:1A:2B:93:D2:4F, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WEP
It shows there. Do you see t in the Network Manager icon? Can you click and try to connect?

---

### Post by piratejackus2 on 2015-04-21
Yes, i see it in the network manager icon but i cannot connect to it. Tis is the problem actually.

In older posts, i already paste the *syslog* when the pc tries to connect **'yuvam'** wifi.
Here it comes again (:

```

Apr 21 17:52:51 yotbavodaka NetworkManager[746]: <info> Activation (wlan0) starting connection 'yuvam'
Apr  21 17:52:51 yotbavodaka NetworkManager[746]: <info> (wlan0):  device state change: disconnected -> prepare (reason 'none') [30 40  0]
Apr 21 17:52:51 yotbavodaka NetworkManager[746]: <info> NetworkManager state is now CONNECTING
Apr 21 17:52:51 yotbavodaka NetworkManager[746]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 21 17:52:51 yotbavodaka NetworkManager[746]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 21 17:52:51 yotbavodaka NetworkManager[746]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 21 17:52:51 yotbavodaka NetworkManager[746]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 21 17:52:51 yotbavodaka NetworkManager[746]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr  21 17:52:51 yotbavodaka NetworkManager[746]: <info> (wlan0):  device state change: prepare -> config (reason 'none') [40 50 0]
Apr 21 17:52:51 yotbavodaka NetworkManager[746]: <info> (wlan0): preparing device.
Apr  21 17:52:51 yotbavodaka NetworkManager[746]: <info> Activation  (wlan0/wireless): connection 'yuvam' has security, and secrets exist.   No new secrets needed.
Apr 21 17:52:51 yotbavodaka NetworkManager[746]: <info> Config: added 'ssid' value 'yuvam'
Apr 21 17:52:51 yotbavodaka NetworkManager[746]: <info> Config: added 'scan_ssid' value '1'
Apr 21 17:52:51 yotbavodaka NetworkManager[746]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Apr 21 17:52:51 yotbavodaka NetworkManager[746]: <info> Config: added 'psk' value '<omitted>'
Apr 21 17:52:51 yotbavodaka NetworkManager[746]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 21 17:52:51 yotbavodaka NetworkManager[746]: <info> Config: set interface ap_scan to 1
Apr 21 17:52:51 yotbavodaka NetworkManager[746]: <info> (wlan0): supplicant interface state: inactive -> scanning
Apr 21 17:52:51 yotbavodaka wpa_supplicant[776]: wlan0: CTRL-EVENT-SCAN-STARTED 
Apr  21 17:52:52 yotbavodaka wpa_supplicant[776]: wlan0: SME: Trying to  authenticate with 14:b9:68:4e:03:58 (SSID='yuvam' freq=2452 MHz)
Apr 21 17:52:52 yotbavodaka kernel: [  283.913563] wlan0: authenticate with 14:b9:68:4e:03:58
Apr 21 17:52:52 yotbavodaka NetworkManager[746]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Apr 21 17:52:52 yotbavodaka kernel: [  283.937757] wlan0: direct probe to 14:b9:68:4e:03:58 (try 1/3)
Apr 21 17:52:52 yotbavodaka kernel: [  284.140197] wlan0: direct probe to 14:b9:68:4e:03:58 (try 2/3)
Apr 21 17:52:53 yotbavodaka kernel: [  284.344187] wlan0: direct probe to 14:b9:68:4e:03:58 (try 3/3)
Apr 21 17:52:53 yotbavodaka kernel: [  284.548184] wlan0: authentication with 14:b9:68:4e:03:58 timed out
Apr  21 17:52:53 yotbavodaka NetworkManager[746]: <info> (wlan0):  supplicant interface state: authenticating -> disconnected
Apr 21 17:52:53 yotbavodaka wpa_supplicant[776]: wlan0: CTRL-EVENT-SCAN-STARTED 
Apr 21 17:52:53 yotbavodaka NetworkManager[746]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Apr 21 17:53:06 yotbavodaka wpa_supplicant[776]: message repeated 2 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Apr  21 17:53:07 yotbavodaka wpa_supplicant[776]: wlan0: SME: Trying to  authenticate with 14:b9:68:4e:03:58 (SSID='yuvam' freq=2452 MHz)
Apr 21 17:53:07 yotbavodaka kernel: [  298.949087] wlan0: authenticate with 14:b9:68:4e:03:58
Apr 21 17:53:07 yotbavodaka kernel: [  298.952286] wlan0: direct probe to 14:b9:68:4e:03:58 (try 1/3)
Apr 21 17:53:07 yotbavodaka NetworkManager[746]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Apr 21 17:53:07 yotbavodaka kernel: [  299.153665] wlan0: direct probe to 14:b9:68:4e:03:58 (try 2/3)
Apr 21 17:53:08 yotbavodaka kernel: [  299.357750] wlan0: direct probe to 14:b9:68:4e:03:58 (try 3/3)
Apr 21 17:53:08 yotbavodaka kernel: [  299.561670] wlan0: authentication with 14:b9:68:4e:03:58 timed out
Apr  21 17:53:08 yotbavodaka NetworkManager[746]: <info> (wlan0):  supplicant interface state: authenticating -> disconnected
Apr 21 17:53:08 yotbavodaka wpa_supplicant[776]: wlan0: CTRL-EVENT-SCAN-STARTED 
Apr 21 17:53:08 yotbavodaka NetworkManager[746]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Apr  21 17:53:10 yotbavodaka wpa_supplicant[776]: wlan0: SME: Trying to  authenticate with 14:b9:68:4e:03:58 (SSID='yuvam' freq=2452 MHz)
Apr 21 17:53:10 yotbavodaka kernel: [  301.462874] wlan0: authenticate with 14:b9:68:4e:03:58
Apr 21 17:53:10 yotbavodaka NetworkManager[746]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Apr 21 17:53:10 yotbavodaka kernel: [  301.466198] wlan0: direct probe to 14:b9:68:4e:03:58 (try 1/3)
Apr 21 17:53:10 yotbavodaka kernel: [  301.669868] wlan0: direct probe to 14:b9:68:4e:03:58 (try 2/3)
Apr 21 17:53:10 yotbavodaka kernel: [  301.873912] wlan0: direct probe to 14:b9:68:4e:03:58 (try 3/3)
Apr 21 17:53:10 yotbavodaka kernel: [  302.077919] wlan0: authentication with 14:b9:68:4e:03:58 timed out
Apr  21 17:53:10 yotbavodaka NetworkManager[746]: <info> (wlan0):  supplicant interface state: authenticating -> disconnected
Apr 21 17:53:11 yotbavodaka wpa_supplicant[776]: wlan0: CTRL-EVENT-SCAN-STARTED 
Apr 21 17:53:11 yotbavodaka NetworkManager[746]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Apr  21 17:53:13 yotbavodaka wpa_supplicant[776]: wlan0: SME: Trying to  authenticate with 14:b9:68:4e:03:58 (SSID='yuvam' freq=2452 MHz)
Apr 21 17:53:13 yotbavodaka kernel: [  304.401139] wlan0: authenticate with 14:b9:68:4e:03:58
Apr 21 17:53:13 yotbavodaka kernel: [  304.404985] wlan0: direct probe to 14:b9:68:4e:03:58 (try 1/3)
Apr 21 17:53:13 yotbavodaka NetworkManager[746]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Apr 21 17:53:13 yotbavodaka kernel: [  304.606222] wlan0: direct probe to 14:b9:68:4e:03:58 (try 2/3)
Apr 21 17:53:13 yotbavodaka kernel: [  304.810196] wlan0: direct probe to 14:b9:68:4e:03:58 (try 3/3)
Apr 21 17:53:13 yotbavodaka kernel: [  305.014174] wlan0: authentication with 14:b9:68:4e:03:58 timed out
Apr  21 17:53:13 yotbavodaka wpa_supplicant[776]: wlan0:  CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="yuvam" auth_failures=1  duration=10
Apr 21 17:53:13 yotbavodaka NetworkManager[746]:  <info> (wlan0): supplicant interface state: authenticating ->  disconnected
Apr 21 17:53:16 yotbavodaka NetworkManager[746]:  <warn> Activation (wlan0/wireless): association took too long,  failing activation.
Apr 21 17:53:16 yotbavodaka NetworkManager[746]:  <info> (wlan0): device state change: config -> failed (reason  'SSID not found') [50 120 53]
Apr 21 17:53:16 yotbavodaka NetworkManager[746]: <info> NetworkManager state is now DISCONNECTED
Apr 21 17:53:16 yotbavodaka NetworkManager[746]: <warn> Activation (wlan0) failed for connection 'yuvam'
Apr  21 17:53:16 yotbavodaka NetworkManager[746]: <info> (wlan0):  device state change: failed -> disconnected (reason 'none') [120 30  0]
Apr 21 17:53:16 yotbavodaka NetworkManager[746]: <info> (wlan0): deactivating device (reason 'none') [0]
Apr 21 17:53:16 yotbavodaka wpa_supplicant[776]: wlan0: CTRL-EVENT-SCAN-STARTED 
Apr 21 17:53:18 yotbavodaka NetworkManager[746]: <info> (wlan0): supplicant interface state: disconnected -> inactive

```

---

### Post by redmorning on 2015-04-22
Hi chili555,
I was wondering if you may have any idea after my last comment?

---

### Post by chili555 on 2015-04-23
Sorry for the delay in my reply.

When I see this:> (wlan0): device state change: config -> failed (reason 'SSID not found') And this:> My wifi 'yuvam' appears on the list of network manager icon but not on wlan0 scan results:And this:> wlan0: authentication with 14:b9:68:4e:03:58 timed outIt makes me wonder if there is a problem in the router. Do other devices, phones, iPads, etc. connect and stay connected easily?

Can you connect if you power cycle the router? Power cycling refers to unplugging the router, waiting 30 seconds, and then plugging it back in to let it reboot.

---

### Post by redmorning on 2015-04-23
No problem with your delay, i was just afraid of that you gave up (:

All the devices at home (ipad, mobile devices, laptops) can connect without any problem; so yes.
I turn off the modem before i sleep so it is being "power cycled" every day. (Anyway, i tried to power cycle modem right now but nothing changes).

---

