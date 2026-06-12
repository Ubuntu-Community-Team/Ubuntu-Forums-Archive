---
title: "WiFi Problem"
date: 2017-01-17
forum: Networking &amp; Wireless
---

### Post by milanbl2 on 2017-01-17
I have a problem with wifi, on my laptop Toshiba satellite p55w, ubuntu 14.04. I also tried this on 16.04, no success.

When I boot my laptop, I have a message "no network devices available". I sometimes solve this by restarting laptop several times. 

I tried lot of solutions from this forum, stackoverflow, etc. But without success. I upgraded kernel, installed driver....

Does anyone have idea what can be a problem?

---

### Post by ajgreeny on 2017-01-17
See **Wireless-info** in my signature below and follow the instructions to run the script and then paste the report you get back here.

---

### Post by milanbl2 on 2017-01-19
Hi,

here is my result.

```



########## wireless info START ##########


Report from: 19 Jan 2017 08:06 CET +0100


Booted last: 19 Jan 2017 08:05 CET +0100


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.5 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 4.4.0-59-generic #80~14.04.1-Ubuntu SMP Fri Jan 6 18:02:02 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


##### lsusb #############################


Bus 001 Device 002: ID 8087:8001 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 04f2:b446 Chicony Electronics Co., Ltd 
Bus 002 Device 004: ID 04f3:20d6 Elan Microelectronics Corp. 
Bus 002 Device 003: ID 048d:8350 Integrated Technology Express, Inc. 
Bus 002 Device 002: ID 03f0:a407 Hewlett-Packard 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: Toshiba Bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


toshiba_wmi            16384  0 
snd_soc_rt5640        114688  0 
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          212992  2 snd_soc_rt5640,snd_soc_ssm4567
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_pcm_dmaengine,snd_hda_core
sparse_keymap          16384  2 toshiba_wmi,toshiba_acpi
wmi                    20480  2 toshiba_wmi,toshiba_acpi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


##### iwconfig ##########################


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #######################


##### network managers ##################


Installed:


	NetworkManager


Running:


root       888     1  0 08:05 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: disconnected


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/Ela1]] (600 root)
[connection] id=Ela1 | type=802-11-wireless
[802-11-wireless] ssid=Ela1 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Strahilo]] (600 root)
[connection] id=Strahilo | type=802-11-wireless
[802-11-wireless] ssid=Strahilo | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Jovicic]] (600 root)
[connection] id=Jovicic | type=802-11-wireless
[802-11-wireless] ssid=Jovicic | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/BLVET]] (600 root)
[connection] id=BLVET | type=802-11-wireless
[802-11-wireless] ssid=BLVET | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Tenda]] (600 root)
[connection] id=Tenda | type=802-11-wireless
[802-11-wireless] ssid=Tenda | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/WIFI - E]] (600 root)
[connection] id=WIFI - E | type=802-11-wireless
[802-11-wireless] ssid=WIFI - E | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/MILANBL 01]] (600 root)
[connection] id=MILANBL 01 | type=802-11-wireless
[802-11-wireless] ssid=MILANBL 01 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Belgrade (based on set time zone)


country 00:
	(2402 - 2472 @ 40), (6, 20)
	(2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN
	(2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN
	(5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN
	(5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN
	(5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN
	(5735 - 5835 @ 80), (6, 20), PASSIVE-SCAN
	(57240 - 63720 @ 2160), (N/A, 0)


##### iwlist channels ###################


lo        no frequency information.


##### iwlist scan #######################


lo        Interface doesn't support scanning.


##### module infos ######################


##### module parameters #################


##### /etc/modules ######################


lp
rtc


##### modprobe options ##################


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


iwconfig wlan0 power off
exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x095a (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


########## wireless info END ############



```

---

### Post by wildmanne39 on 2017-01-19
*Thread moved to **Networking & Wireless**.*

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by praseodym on 2017-01-19
Check in your BIOS if wireless is acive. Eventually resetting the BIOS to default.

---

### Post by milanbl2 on 2017-01-23
I tried to reset BIOS but without success

---

### Post by RobGoss on 2017-01-23
Have you tried installing proprietary drivers that are provided by Ubuntu's software & updates?

You will need to have a wired connection to search for the appropriate drivers

---

### Post by milanbl2 on 2017-01-23
Well, I'm not sure it's a problem with driver, because I can connect sometimes. For example, I restart laptop several times and then wifi is enabled. I regularly update software and all drivers.

---

### Post by praseodym on 2017-01-23
Please run the script again if its working

---

### Post by milanbl2 on 2017-01-23
Here is my results

---

### Post by praseodym on 2017-01-23
First: There is a Broadcom driver installed:
```

sudo modprobe -rfv wl
sudo apt-get remove --purge bcmwl-kernel-source
```
Second: Your ESSID is doubled: One in the 2,4 and one in the 5 GHz band. Choose the stronger signal and add the respective MAC address in the network-managers BSSID section. Reboot.

---

### Post by milanbl2 on 2017-02-02
I tried this, but this didn't solved my problem :(

---

