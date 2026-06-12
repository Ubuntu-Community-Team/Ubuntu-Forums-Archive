---
title: "Broadcom BCM4313 WiFi Not Working 12.04"
date: 2013-10-06
forum: Networking &amp; Wireless
---

### Post by graemepmail-subscriptions on 2013-10-06
When visiting UK this summer I upgraded my mother's HP Mini 210-1100 to Ubuntu 12.04 but couldn't get the WiFi working (it was at the time the Ubuntu forums were down because user accounts were compromised).  I remembered having trouble with an earlier version of Ubuntu but did previously get WiFi working.  After upgrading to 12.04, WiFi connected when unencrypted but would not connect when using WPA2.  It seems like there was issue with Network Manager and so more recently I installed Wicd as suggested in some posts.

Now, I am in the USA troubleshooting using VNC via a wired connection.  Obviously this creates some challenges.  My mother is not technically savvy - she is limited to following simple instructions like turning power on/off or removing/replacing the Ethernet cable.

It would be great if there was some way I can work on getting the WiFi running while still connected via Ethernet.

I've tried a number of drivers but have never had a stable connection and have to admit that I'm now a bit lost as to where to go next.  I could really do with some help.

Here are some details (I've snipped out areas that seem largely unrelated to the problem) obtained using the network troubleshooting code from [https://help.ubuntu.com/community/WirelessTroubleshootingProcedure](https://help.ubuntu.com/community/WirelessTroubleshootingProcedure)...

```
doreen@doreen-netbook:~$ sudo apt-get update; sudo apt-get install hwinfo grep rfkill; sudo lshw -C network; rfkill list; sudo iwlist scan | egrep -i 'chan|ssid'; cat /etc/network/interfaces; cat 

/etc/lsb-release; lspci -nnk | grep -iA2 net; lsusb; nmcli nm status; sudo lshw -short; uname -a; sudo updatedb; dmesg | egrep '02:00|80211|acx|at76|ath|b43|bcm|brcm|CX|eth|ipw|ireless|irmware|isl|lbtf|

orinoco|ndiswrapper|NPE|ound|p54|prism|rror|rtl|RTL|rt2|RT2|rt3|RT3|rt5|RT5|rt6|RT6|rt7|RT7|usb|witch|wl';sudo dmidecode|egrep 'anufact|roduct|erial|elease'; iwconfig; cat /etc/modprobe.d/* | egrep 

'80211|acx|at76|ath|b43|bcm|brcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|wmi|witch|wl'; cat /var/lib/NetworkManager/NetworkManager.state; sudo hwinfo --netcard ; 

ps -aux|egrep 'wpa|icd|etwork'; netstat -rn ; cat /etc/resolv.conf; ls -lia /boot; grep tmpfs /etc/fstab; ubuntu-support-status; sudo lsmod
[sudo] password for doreen: 




  *-network
       description: Wireless interface
       product: BCM4313 802.11bgn Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth2
       version: 01
       serial: 00:26:82:9e:be:a0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:17 memory:56000000-56003fff
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    ESSID:"DoreenNet"
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    ESSID:"TALKTALK-E8661B"
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    ESSID:"BTWiFi-with-FON"
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    ESSID:"BTHub3-95K3"
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    ESSID:"BTWiFi"
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    ESSID:"TALKTALK-4A5E27"
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    ESSID:"SKYD1343"
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    ESSID:"SKY855F0"
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    ESSID:"TALKTALK-224E74"
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    ESSID:"BTWiFi-with-FON"
auto lo
iface lo inet loopback

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.3 LTS"


--
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:145c]
    Kernel driver in use: wl


The program 'nmcli' is currently not installed.  You can install it by typing:
sudo apt-get install network-manager

H/W path        Device     Class       Description
==================================================
                           system      HP Mini 210-1100 (WQ584UA#ABA)

/0/100/1c/0     eth0       network     RTL8101E/RTL8102E PCI Express Fast Ethern

/0/100/1c.1/0   eth2       network     BCM4313 802.11bgn Wireless Network Adapte

Linux doreen-netbook 3.5.0-41-generic #64~precise1-Ubuntu SMP Thu Sep 12 17:01:55 UTC 2013 i686 i686 i386 GNU/Linux
[    0.000000] DMI: Hewlett-Packard HP Mini 210-1100/3660, BIOS F.22 05/24/2010
[    0.140398] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored

[   12.323292] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.501745] lp: driver loaded but no devices found
[   12.507895] lib80211: common routines for IEEE802.11 drivers
[   12.507907] lib80211_crypt: registered algorithm 'NULL'
[   12.521304] cfg80211: Calling CRDA to update world regulatory domain
[   12.521521] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   12.551209] wl: module license 'MIXED/Proprietary' taints kernel.
[   12.618912] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   12.618925] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   12.618933] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   12.618940] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   12.618947] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   12.618955] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   12.618962] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   12.618969] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   12.618975] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   12.618983] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   12.618989] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   12.618997] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   12.619003] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   12.619010] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   12.619017] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   12.619025] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   12.619032] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   12.619040] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   12.619047] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   12.619054] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   12.619061] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   12.619069] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   12.619076] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   12.619083] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   12.619090] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   12.619098] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   12.619105] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   12.619112] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
[   12.619118] cfg80211: Disabling freq 5170 MHz
[   12.619125] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[   12.619132] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   12.619138] cfg80211: Updating information on frequency 5190 MHz for a 20 MHz width channel with regulatory rule:
[   12.619146] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   12.619153] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[   12.619161] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   12.619169] cfg80211: Updating information on frequency 5210 MHz for a 20 MHz width channel with regulatory rule:
[   12.619176] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   12.619184] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[   12.619191] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   12.619199] cfg80211: Updating information on frequency 5230 MHz for a 20 MHz width channel with regulatory rule:
[   12.619207] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   12.619215] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[   12.619223] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   12.619229] cfg80211: Disabling freq 5260 MHz
[   12.619234] cfg80211: Disabling freq 5280 MHz
[   12.619240] cfg80211: Disabling freq 5300 MHz
[   12.619245] cfg80211: Disabling freq 5320 MHz
[   12.619252] cfg80211: Disabling freq 5500 MHz
[   12.619258] cfg80211: Disabling freq 5520 MHz
[   12.619263] cfg80211: Disabling freq 5540 MHz
[   12.619268] cfg80211: Disabling freq 5560 MHz
[   12.619273] cfg80211: Disabling freq 5580 MHz
[   12.619279] cfg80211: Disabling freq 5600 MHz
[   12.619284] cfg80211: Disabling freq 5620 MHz
[   12.619289] cfg80211: Disabling freq 5640 MHz
[   12.619295] cfg80211: Disabling freq 5660 MHz
[   12.619300] cfg80211: Disabling freq 5680 MHz
[   12.619305] cfg80211: Disabling freq 5700 MHz
[   12.619313] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
[   12.619321] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   12.619328] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
[   12.619336] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   12.619344] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
[   12.619351] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   12.619359] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
[   12.619367] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   12.619374] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
[   12.619381] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   12.619387] cfg80211: Disabling freq 5920 MHz
[   12.619394] cfg80211: Disabling freq 5940 MHz
[   12.619399] cfg80211: Disabling freq 5960 MHz
[   12.619405] cfg80211: Disabling freq 5980 MHz
[   12.619411] cfg80211: Disabling freq 6000 MHz
[   12.619416] cfg80211: Disabling freq 6020 MHz
[   12.619422] cfg80211: Disabling freq 6040 MHz
[   12.619427] cfg80211: Disabling freq 6060 MHz
[   12.619433] cfg80211: Disabling freq 6080 MHz
[   12.628100] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   12.649396] lib80211_crypt: registered algorithm 'TKIP'
[   12.745880] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 6.20.155.1 (r326264)
[   13.554523] Console: switching to colour frame buffer device 128x37
[   13.680995] lpc_ich: Resource conflict(s) found affecting iTCO_wdt
[   13.681049] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   13.742515] uvcvideo: Found UVC 1.00 device HP Webcam-50 (5986:0182)
[   13.749895] input: HP Webcam-50 as /devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/input/input6
[   13.754103] usbcore: registered new interface driver uvcvideo
[   13.765100] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   13.765409] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   14.154074] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   14.154087] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.154095] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   14.154103] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.154111] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   14.154118] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.154126] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   14.154133] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.154141] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   14.154148] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.154155] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   14.154163] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.154171] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   14.154179] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.154186] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   14.154194] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.154200] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   14.154208] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.154216] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   14.154223] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.154230] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   14.154238] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.154245] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   14.154253] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.154260] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   14.154268] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.154275] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   14.154283] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.154290] cfg80211: Disabling freq 5170 MHz
[   14.154297] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[   14.154305] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.154312] cfg80211: Updating information on frequency 5190 MHz for a 20 MHz width channel with regulatory rule:
[   14.154320] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.154327] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[   14.154335] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.154341] cfg80211: Updating information on frequency 5210 MHz for a 20 MHz width channel with regulatory rule:
[   14.154349] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.154356] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[   14.154364] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.154371] cfg80211: Updating information on frequency 5230 MHz for a 20 MHz width channel with regulatory rule:
[   14.154378] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.154386] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[   14.154393] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.154399] cfg80211: Disabling freq 5260 MHz
[   14.154404] cfg80211: Disabling freq 5280 MHz
[   14.154410] cfg80211: Disabling freq 5300 MHz
[   14.154415] cfg80211: Disabling freq 5320 MHz
[   14.154421] cfg80211: Disabling freq 5500 MHz
[   14.154426] cfg80211: Disabling freq 5520 MHz
[   14.154432] cfg80211: Disabling freq 5540 MHz
[   14.154437] cfg80211: Disabling freq 5560 MHz
[   14.154443] cfg80211: Disabling freq 5580 MHz
[   14.154448] cfg80211: Disabling freq 5600 MHz
[   14.154454] cfg80211: Disabling freq 5620 MHz
[   14.154459] cfg80211: Disabling freq 5640 MHz
[   14.154464] cfg80211: Disabling freq 5660 MHz
[   14.154470] cfg80211: Disabling freq 5680 MHz
[   14.154475] cfg80211: Disabling freq 5700 MHz
[   14.154482] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
[   14.154490] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.154497] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
[   14.154505] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.154513] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
[   14.154520] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.154528] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
[   14.154535] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.154542] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
[   14.154550] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.154556] cfg80211: Disabling freq 5920 MHz
[   14.154562] cfg80211: Disabling freq 5940 MHz
[   14.154568] cfg80211: Disabling freq 5960 MHz
[   14.154574] cfg80211: Disabling freq 5980 MHz
[   14.154580] cfg80211: Disabling freq 6000 MHz
[   14.154586] cfg80211: Disabling freq 6020 MHz
[   14.154591] cfg80211: Disabling freq 6040 MHz
[   14.154597] cfg80211: Disabling freq 6060 MHz
[   14.154601] cfg80211: Disabling freq 6080 MHz
[   14.154615] cfg80211: World regulatory domain updated:
[   14.154620] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   14.154628] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.154634] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.154642] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.154649] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.154655] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.055030] r8169 0000:01:00.0: eth0: link down
[   22.055065] r8169 0000:01:00.0: eth0: link down
[   22.061720] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.718744] r8169 0000:01:00.0: eth0: link up
[   23.719304] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   24.937281] r8169 0000:01:00.0: eth0: link down
[   24.937298] r8169 0000:01:00.0: eth0: link down
[   24.941016] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.306412] r8169 0000:01:00.0: eth0: link down
[   25.307026] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.885455] r8169 0000:01:00.0: eth0: link up
[   26.885991] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 7158.076307] ERROR @wl_dev_intvar_get : error (-1)
[ 7158.076329] ERROR @wl_cfg80211_get_tx_power : error (-1)
[ 9752.412192] ERROR @wl_dev_intvar_get : error (-1)
[ 9752.412214] ERROR @wl_cfg80211_get_tx_power : error (-1)
[106279.030754] ERROR @wl_dev_intvar_get : error (-1)
[106279.030769] ERROR @wl_cfg80211_get_tx_power : error (-1)
    Release Date: 05/24/2010
    Manufacturer: Hewlett-Packard
    Product Name: HP Mini 210-1100
    Serial Number: CNF025D6R0
    Manufacturer: Hewlett-Packard
    Product Name: 3660
    Serial Number: CNF025D6R0
    Manufacturer: Hewlett-Packard
    Serial Number: None
    Manufacturer: 13-54
    SBDS Serial Number: 0235
    SBDS Manufacture Date: 2010-06-03
    Manufacturer: 802C
    Serial Number: 33F6DE20
    Manufacturer: Intel(R) Corporation
    Serial Number: Not Specified
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# which ath5k cannot recover. To prevent this condition, stop
blacklist ath_pci
# Warning: This file is autogenerated by bcmwl. All changes to this file will be lost.
blacklist b43
blacklist b43legacy
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist b43
blacklist b43legacy
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist b43
blacklist b43legacy
blacklist bcma
blacklist ndiswrapper
blacklist wl
blacklist uart6850
blacklist twl4030_wdt
# wl module from Broadcom conflicts with ssb
blacklist b43legacy
blacklist b43
blacklist brcm80211
blacklist brcmsmac
install wl /sbin/modprobe --ignore-install wl $CMDLINE_OPTS
alias pci:v000014E4d00004311sv00001363sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004311sv00001364sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004311sv00001365sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004311sv00001374sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004311sv00001375sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004311sv00001376sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004311sv00001377sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004311sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv0000135Fsd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv00001360sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv00001361sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv00001362sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv00001370sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv00001371sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv00001372sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv00001373sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004315sv0000137Csd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004315sv0000137Dsd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004315sv00001507sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004315sv00001508sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004315sv0000365Esd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004315sv0000365Fsd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004315sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004318sv00001355sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004318sv00001356sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004318sv00001357sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004318sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004319sv00001358sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004319sv00001359sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004319sv0000135Asd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004319sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv000000E7sd00000E11bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv000012F4sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv000012F8sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv000012FAsd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv000012FBsd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004324sv000012F9sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004324sv000012FCsd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004324sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004328sv00001366sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004328sv00001367sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004328sv00001368sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004328sv00001369sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004328sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d0000432Bsv0000137Fsd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d0000432Bsv00001380sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d0000432Bsv00001509sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d0000432Bsv00001510sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d0000432Bsv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004353sv00001509sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004353sv00001510sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004353sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004357sv00000570sd000014E4bc*sc*i* ndiswrapper
alias pci:v000014E4d00004357sv0000145Esd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004357sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004359sv000005E2sd000014E4bc*sc*i* ndiswrapper
alias pci:v000014E4d00004359sv0000182Csd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004359sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004727sv0000145Csd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004727sv00001483sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004727sv00001795sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000014E4d00004727sv*sd*bc*sc*i* ndiswrapper
cat: /var/lib/NetworkManager/NetworkManager.state: No such file or directory
> hal.1: read hal dataprocess 8592: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 282.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
23: PCI 100.0: 0200 Ethernet controller                         
  [Created at pci.318]
  Unique ID: rBUF.rEkSMo6jgd7
  Parent ID: z8Q3.toiunV5DoYF
  SysFS ID: /devices/pci0000:00/0000:00:1c.0/0000:01:00.0
  SysFS BusID: 0000:01:00.0
  Hardware Class: network
  Model: "Realtek RTL8101E/RTL8102E PCI Express Fast Ethernet controller"
  Vendor: pci 0x10ec "Realtek Semiconductor Co., Ltd."
  Device: pci 0x8136 "RTL8101E/RTL8102E PCI Express Fast Ethernet controller"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x3660 
  Revision: 0x02
  Driver: "r8169"
  Driver Modules: "r8169"
  Device File: eth0
  I/O Ports: 0x5000-0x5fff (rw)
  Memory Range: 0x50010000-0x50010fff (ro,non-prefetchable)
  Memory Range: 0x50000000-0x5000ffff (ro,non-prefetchable)
  Memory Range: 0x50020000-0x5002ffff (ro,non-prefetchable,disabled)
  IRQ: 42 (351714 events)
  HW Address: c8:0a:a9:c7:66:4c
  Link detected: yes
  Module Alias: "pci:v000010ECd00008136sv0000103Csd00003660bc02sc00i00"
  Driver Info #0:
    Driver Status: r8169 is active
    Driver Activation Cmd: "modprobe r8169"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #12 (PCI bridge)

24: PCI 200.0: 0282 WLAN controller
  [Created at pci.318]
  Unique ID: mY_N.3Bbj30Yicg4
  Parent ID: qTvu.vdbOleKdrJ0
  SysFS ID: /devices/pci0000:00/0000:00:1c.1/0000:02:00.0
  SysFS BusID: 0000:02:00.0
  Hardware Class: network
  Model: "Broadcom WLAN controller"
  Vendor: pci 0x14e4 "Broadcom"
  Device: pci 0x4727 
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x145c 
  Revision: 0x01
  Driver: "wl"
  Driver Modules: "wl"
  Device File: eth2
  Features: WLAN
  Memory Range: 0x56000000-0x56003fff (rw,non-prefetchable)
  IRQ: 17 (268 events)
  HW Address: 00:26:82:9e:be:a0
  Link detected: yes
  WLAN channels: 1 2 3 4 5 6 7 8 9 10 11 12 13 14 36 38 40 42 44 46 48 149 153 157 161 165
  WLAN frequencies: 2.412 2.417 2.422 2.427 2.432 2.437 2.442 2.447 2.452 2.457 2.462 2.467 2.472 2.484 5.18 5.19 5.2 5.21 5.22 5.23 5.24 5.745 5.765 5.785 5.805 5.825
  WLAN encryption modes: WEP40 WEP104 TKIP CCMP
  WLAN authentication modes: open sharedkey wpa-psk wpa-eap
  Module Alias: "pci:v000014E4d00004727sv0000103Csd0000145Cbc02sc80i00"
  Driver Info #0:
    Driver Status: bcma is not active
    Driver Activation Cmd: "modprobe bcma"
  Driver Info #1:
    Driver Status: wl is active
    Driver Activation Cmd: "modprobe wl"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #13 (PCI bridge)
Warning: bad ps syntax, perhaps a bogus '-'? See http://procps.sf.net/faq.html
root       976  0.4  0.8  26300  8612 ?        S    Oct05   7:17 /usr/bin/python -O /usr/share/wicd/daemon/wicd-daemon.py
root      1020  0.2  0.7  15268  7568 ?        S    Oct05   4:17 /usr/bin/python -O /usr/share/wicd/daemon/monitor.py
doreen    1477  0.0  1.5  64180 15520 ?        Sl   Oct05   0:00 /usr/bin/python -O /usr/share/wicd/gtk/wicd-client.py --tray
doreen    8606  0.0  0.0   4384   824 pts/0    S+   00:47   0:00 egrep --color=auto wpa|icd|etwork
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG        0 0          0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 192.168.2.1
search DoreenNet
```

---

### Post by airplanesimen on 2013-10-07
Hmm, do you say that it's only WPA2 networks it refuses to connect to? Referring to: > [COLOR=#000000] WiFi connected when unencrypted but would not connect when using WPA2. It seems like there was issue with Network Manager and so more recently I installed Wicd as suggested in some posts.[/COLOR]

If you remember the name of the network (ssid), you may try to show the output of:
```
sudo cat /etc/NetworkManager/system-connections/"name of network"
``` 

It will help out alot if it is what i am suspecting.

---

### Post by graemepmail-subscriptions on 2013-10-07
Note that I replaced Network Manager with Wicd.  The following might be remnants of that installation.

Here you go (I obscured the PSK - it was correct)...
```

doreen@doreen-netbook:~$ sudo cat /etc/NetworkManager/system-connections/"DoreenNet"
[sudo] password for doreen: 

[connection]
id=DoreenNet
uuid=1e940485-84c8-4d8c-a830-578d14541e49
type=802-11-wireless

[802-11-wireless]
ssid=DoreenNet
mode=infrastructure
mac-address=00:26:82:9E:BE:A0
security=802-11-wireless-security

[802-11-wireless-security]
key-mgmt=wpa-psk
psk=xxxxxxxx

[ipv4]
method=auto

[ipv6]
method=auto

```

Here's the content of /etc/wicd/wireless-settings.conf
```

[EC:1A:59:45:A2:44]
afterscript = None
dhcphostname = doreen-netbook
bssid = EC:1A:59:45:A2:44
postdisconnectscript = None
dns_domain = None
gateway = None
use_global_dns = 0
encryption = True
ip = None
beforescript = None
hidden = False
channel = 7
mode = Master
never = 0
netmask = None
usedhcphostname = 0
predisconnectscript = None
enctype = wpa-psk
dns3 = None
dns2 = None
dns1 = None
use_settings_globally = 0
use_static_dns = 0
apsk = xxxxxxxx
encryption_method = WPA2
essid = DoreenNet
automatic = 1
search_domain = None

```

---

### Post by airplanesimen on 2013-10-08
Sorry, i am out of luck already. It looks like the computer can't retrieve enough information from the network to establish the connection. 
I am sorry, I hope there is anyone else who knows more here.

---

