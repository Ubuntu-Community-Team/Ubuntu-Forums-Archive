---
title: "[ubuntu] Wireless connection disappears after while"
date: 2014-09-10
forum: Networking &amp; Wireless
---

### Post by Jakub_Nowak on 2014-09-10
My wireless connection disappears after while. It starts working after reboot and again disappears. I have looked for solutions, bu haven't found any working. Here are logs from script from Forum:

```



########## wireless info START ##########


Report from: 10 Sep 2014 19:44 CEST +0200


Script from: 05 Sep 2014 22:42 UTC +0000


##### release #####


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty


##### kernel #####


Linux 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:42 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop #####


Ubuntu


##### lspci #####


08:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
	Subsystem: Lenovo Device [17aa:b736]
	Kernel driver in use: rtl8723be


09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: Lenovo Device [17aa:380d]
	Kernel driver in use: r8169


##### lsusb #####


Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 006: ID 046d:c526 Logitech, Inc. Nano Receiver
Bus 003 Device 005: ID 0bda:b728 Realtek Semiconductor Corp. 
Bus 003 Device 004: ID 5986:055e Acer, Inc 
Bus 003 Device 003: ID 0fce:0193 Sony Ericsson Mobile Communications AB 
Bus 003 Device 002: ID 13ba:0017 PCPlay PS/2 Keyboard+Mouse Adapter
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info #####


##### rfkill #####


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### lsmod #####


rtl8723be              85118  0 
btcoexist              50304  1 rtl8723be
rtl8723_common         23361  1 rtl8723be
rtl_pci                26690  1 rtl8723be
rtlwifi                63475  2 rtl_pci,rtl8723be
mac80211              630653  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              484040  2 mac80211,rtlwifi
mxm_wmi                13021  1 nouveau
wmi                    19177  2 mxm_wmi,nouveau


##### interfaces #####


auto lo
iface lo inet loopback


##### ifconfig #####


eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr <MAC addr wlan0>  
          inet addr:192.168.1.17  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::9248:9aff:fec9:653f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32189 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21063 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:41592205 (41.5 MB)  TX bytes:2793098 (2.7 MB)


##### iwconfig #####


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"Livebox-DBE5"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC addr Livebox-DBE5>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=30/70  Signal level=-80 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:128   Missed beacon:0


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #####


nameserver 127.0.1.1
search home


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC addr eth0>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


- Device: wlan0  [Livebox-DBE5] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             connected
  Default:           yes
  HW Address:        <MAC addr wlan0>


  Capabilities:
    Speed:           72 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    Orange_FunSpot:  Infra, <MAC addr Orange_FunSpot>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100
    *Livebox-DBE5:   Infra, <MAC addr Livebox-DBE5>, Freq 2412 MHz, Rate 54 Mb/s, Strength 95 WPA WPA2


  IPv4 Settings:
    Address:         192.168.1.17
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1


##### NetworkManager.state #####


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf #####


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### iw reg get #####


country PL:
	(2402 - 2482 @ 40), (N/A, 20)
	(5170 - 5250 @ 40), (N/A, 20)
	(5250 - 5330 @ 40), (N/A, 20), DFS
	(5490 - 5710 @ 40), (N/A, 27), DFS
	(57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR


##### iwlist channels #####


eth0      no frequency information.


lo        no frequency information.


wlan0     13 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)


##### iwlist scan #####


Channel occupancy:


     2   WLAPs on   Frequency:2.412 GHz (Channel 1)


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC addr Livebox-DBE5>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"Livebox-DBE5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000069e6e107
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC addr Orange_FunSpot>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=30 dBm  
                    Encryption key:off
                    ESSID:"Orange_FunSpot"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000006a114a2c
                    Extra: Last beacon: 8ms ago


##### module infos #####


[rtl8723be]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         PageHe	<page_he@realsil.com.cn>
srcversion:     0D59E0301AAA6E5A93400BB
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B1:41:4A:E9:6C:1B:0E:BB:7C:14:1F:A4:05:C1:F6:C9:8E:8A:66:F0
sig_hashalgo:   sha512
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)


[rtl8723_common]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
srcversion:     D1807280DBDC9B8A7EBDAB7
depends:        
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B1:41:4A:E9:6C:1B:0E:BB:7C:14:1F:A4:05:C1:F6:C9:8E:8A:66:F0
sig_hashalgo:   sha512


[rtl_pci]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     D5E4890DC428FA5A1BF92DF
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B1:41:4A:E9:6C:1B:0E:BB:7C:14:1F:A4:05:C1:F6:C9:8E:8A:66:F0
sig_hashalgo:   sha512


[rtlwifi]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     E1F4663325225EE8DBA54CA
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B1:41:4A:E9:6C:1B:0E:BB:7C:14:1F:A4:05:C1:F6:C9:8E:8A:66:F0
sig_hashalgo:   sha512


##### module parameters #####


[rtl8723be]
debug: 0
fwlps: Y
ips: Y
msi: N
swenc: N
swlps: N


##### /etc/modules #####


lp
rtc


##### blacklists #####


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


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


##### rc.local #####


exit 0


##### udev rules #####


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #####


[    4.958946] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
[    4.965124] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    4.965289] rtlwifi: wireless switch is on
[    5.696186] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[    6.585643] wlan0: authenticate with <MAC addr Livebox-DBE5>
[    6.599256] wlan0: send auth to <MAC addr Livebox-DBE5> (try 1/3)
[    6.601335] wlan0: authenticated
[    6.602971] wlan0: associate with <MAC addr Livebox-DBE5> (try 1/3)
[    6.607441] wlan0: RX AssocResp from <MAC addr Livebox-DBE5> (capab=0x411 status=0 aid=1)
[    6.607588] wlan0: associated
[    6.607611] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[    6.613264] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC addr Livebox-DBE5>


########## wireless info END ############

```

---

### Post by varunendra on 2014-09-10
Welcome to the forums Jakub_Nowak !

Please open a terminal (Ctrl-Alt-T) and run the following code in it (you may copy-paste it to avoid typo) -
```
echo "options rtl8723be fwlps=N ips=N" | sudo tee /etc/modprobe.d/rtl8723be.conf
```
Then either reboot, or manually reload the driver -
```
sudo modprobe -rv rtl8723be
sudo modprobe -v rtl8723be
```
Does it remain stable now?

As an additional measure to improve your connection quality, it is highly recommended that you should change the encryption type in your router/access-point to pure WPA2-PSK with AES (CCMP). Currently it is using WPA/WPA2 mixed mode with TKIP which should be avoided as long as possible.

---

### Post by Jakub_Nowak on 2014-09-13
Thank You very much. Everything has been working properly since I applied your fix. Also thanks to your advice with router configuration.

---

### Post by varunendra on 2014-09-13
Awesome!! I was very-very-very eagerly waiting for a confirmation regarding this, at least three threads I have been following that are waiting for a fix! :D

Please mark the thread as [SOLVED] using "Thread Tools" link above the top post. Thanks!

---

### Post by k100rs on 2015-03-20
thanks a lot for solving this severe problem, you made me very, very happy dear Varun [[COLOR=#DD4814][varunendra]("http://ubuntuforums.org/member.php?u=1043629")][/COLOR]!! 
you're AweSome !

---

### Post by tlue on 2015-04-15
after long suffering I finally found this post and it seems to have worked for me too. Thanks! :)

my output of lspci also shows a Realtek > RTL8723BE PCIe Wireless Network Adapter

.....@.... Lenovo-Flex-2-15:~$ lspci
00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 0b)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 0b)
00:14.0 USB controller: Intel Corporation Lynx Point-LP USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation Lynx Point-LP HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation Lynx Point-LP HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 1 (rev e4)
00:1c.2 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 3 (rev e4)
00:1c.3 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 4 (rev e4)
00:1c.4 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 5 (rev e4)
00:1f.0 ISA bridge: Intel Corporation Lynx Point-LP LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Lynx Point-LP SMBus Controller (rev 04)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)
04:00.0 3D controller: NVIDIA Corporation GF117M [GeForce 610M/710M/820M / GT 620M/625M/630M/720M] (rev a1)

---

### Post by bob_smith3 on 2015-04-21
Hi Varunendra,
I have a simillar issue, with Lenovo G50-45 laptop. I recently installed Ubuntu 14.04.2 and the wireless connectivity seems to last maximum 10 minutes. After that, webpages start to slow down and finally it will say that the connection is lost. Turning off the wi-fi and turning it back on does not resolve the issue. The only solution is to reboot the computer. Internet works fine with a wired connection.  I assume it is an issue with the wireless drivers? If so, how can I make the wireless connection stable?
Thank you so much!

---

### Post by Vladlenin5000 on 2015-04-21
@bob_smith3 - So, here you are again this time hijacking an old thread... 

I already posted what you should do in your own thread. Please neither open another for the same issue nor hijack other people's threads and follow up in yours. Thank you.

---

### Post by coffeecat on 2015-04-22
Thread closed to prevent further thread hijacks.

If anyone needs help with a similar issue, please start your own thread - just one will do!

---

