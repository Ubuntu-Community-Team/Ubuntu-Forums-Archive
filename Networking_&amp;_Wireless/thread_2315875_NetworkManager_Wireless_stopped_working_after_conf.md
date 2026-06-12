---
title: "NetworkManager Wireless stopped working after configuring wpa_supplicant"
date: 2016-03-03
forum: Networking &amp; Wireless
---

### Post by martinoberndorfer on 2016-03-03
Hey Guys, I'm new to this forum and have a question for you. Hope you can help me. :)

NetworkManager has stopped working with wireless connections since i started using wpa_supplicant for connection to an EAP network.
The NetworkManager applet says "Device is not ready" at wireless connections.

I guess it has something to do with this:

```

==> /var/log/syslog <==
Mar  3 11:21:09 lenovo NetworkManager[927]: <warn> Trying to remove a non-existant call id.
Mar  3 11:21:09 lenovo dbus[568]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Mar  3 11:21:09 lenovo wpa_supplicant[11545]: dbus: Could not request service name: org.freedesktop.DBus.Error.AccessDenied Connection ":1.274876" is not allowed to own the service "fi.w1.wpa_supplicant1" due to security policies in the configuration file
Mar  3 11:21:09 lenovo wpa_supplicant[11545]: Failed to initialize wpa_supplicant
Mar  3 11:21:09 lenovo dbus[568]: [system] Activated service 'fi.w1.wpa_supplicant1' failed: Launch helper exited with unknown return code 255
Mar  3 11:21:09 lenovo NetworkManager[927]: <error> [1457000469.435692] [nm-supplicant-interface.c:997] interface_add_cb(): (wlan0): error adding interface: Launch helper exited with unknown return code 255
Mar  3 11:21:09 lenovo NetworkManager[927]: dbus_g_proxy_cancel_call: assertion 'pending != NULL' failed
Mar  3 11:21:09 lenovo NetworkManager[927]: <info> (wlan0): supplicant interface state: starting -> down
Mar  3 11:21:09 lenovo NetworkManager[927]: <warn> Trying to remove a non-existant call id.
Mar  3 11:21:09 lenovo dbus[568]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)

```

I already tried uninstalling and reinstalling wpasupllicant and networkmanager and also the wifi driver. Nothing solved the problem.
My wireless has the RTL8723be chipset and I'm using the driver from here: [https://github.com/lwfinger/rtlwifi_new](https://github.com/lwfinger/rtlwifi_new)

EDIT: 
My wireless connection IS WORKING its just that i can't manage it with the network manager. I manually configure the wpa_supplicant.conf file and added the following lines to* **rc.local ***so it connects on login: 
```

sudo wpa_supplicant -i wlan0 -c /etc/wpa_supplicant/wpa_supplicant.conf -B
sudo dhcpcd wlan0

```

EDIT2:
Here is the result of wireless-info script:
```



########## wireless info START ##########


Report from: 04 Mar 2016 14:05 CET +0100


Booted last: 04 Mar 2016 13:45 CET +0100


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.4 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.19.0-51-generic #58~14.04.1-Ubuntu SMP Fri Feb 26 22:02:58 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


08:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
	Subsystem: Lenovo Device [17aa:b736]
	Kernel driver in use: rtl8723be


09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: Lenovo Device [17aa:380d]
	Kernel driver in use: r8169


##### lsusb #############################


Bus 004 Device 002: ID 8087:8000 Intel Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 8087:8008 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:b728 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 5986:055e Acer, Inc 
Bus 001 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


rtl8723be             143360  0 
btcoexist             413696  1 rtl8723be
rtl_pci                40960  1 rtl8723be
rtlwifi               135168  3 btcoexist,rtl_pci,rtl8723be
mac80211              712704  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              524288  2 mac80211,rtlwifi
ideapad_laptop         24576  0 
sparse_keymap          16384  1 ideapad_laptop
wmi                    20480  0 


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.250  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:44548 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24466 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:63050365 (63.0 MB)  TX bytes:2042865 (2.0 MB)


vmnet1    Link encap:Ethernet  HWaddr <MAC 'vmnet1' [IF]>  
          inet addr:172.16.1.1  Bcast:172.16.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'vmnet1' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:145 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


vmnet8    Link encap:Ethernet  HWaddr <MAC 'vmnet8' [IF]>  
          inet addr:172.16.105.1  Bcast:172.16.105.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'vmnet8' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:146 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.15  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:103 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1012 (1.0 KB)  TX bytes:20216 (20.2 KB)


##### iwconfig ##########################


eth0      no wireless extensions.


vmnet1    no wireless extensions.


vmnet8    no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"UPC0047311"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'UPC0047311' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-34 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 wlan0
172.16.1.0      0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
172.16.105.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


##### resolv.conf #######################


nameserver 195.34.133.21
nameserver 212.186.211.21
nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root       930     1 10 13:45 ?        00:02:03 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: eth0  [Kabelnetzwerkverbindung 1] ------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.0.250
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             8.8.8.8
    DNS:             8.8.4.4


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 


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


no-auto-default=<MAC 'eth0' [IF]>,


[ifupdown]
managed=true


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/3WebCube3E00 1]] (600 root)
[connection] id=3WebCube3E00 1 | type=802-11-wireless
[802-11-wireless] ssid=3WebCube3E00 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/UPC0047311]] (600 root)
[connection] id=UPC0047311 | type=802-11-wireless
[802-11-wireless] ssid=UPC0047311 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore


[[/etc/NetworkManager/system-connections/3WebCube3E00]] (600 root)
[connection] id=3WebCube3E00 | type=802-11-wireless
[802-11-wireless] ssid=3WebCube3E00 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Vienna (based on set time zone)


country AT:
	(2402 - 2482 @ 40), (N/A, 20)
	(5170 - 5250 @ 40), (N/A, 20)
	(5250 - 5330 @ 40), (N/A, 20), DFS
	(5490 - 5710 @ 40), (N/A, 27), DFS
	(57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR


##### iwlist channels ###################


eth0      no frequency information.


vmnet1    no frequency information.


vmnet8    no frequency information.


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


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


vmnet1    Interface doesn't support scanning.


vmnet8    Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      2   APs on   Frequency:2.412 GHz (Channel 1)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'UPC0047311' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"UPC0047311"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000354c9dd826
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'UPC Wi-Free' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-26 dBm  
                    Encryption key:on
                    ESSID:"UPC Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000354c9f603d
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x


##### module infos ######################


[rtl8723be]
filename:       /lib/modules/3.19.0-51-generic/updates/dkms/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         PageHe	<page_he@realsil.com.cn>
srcversion:     03124063245DA6DF009C61D
depends:        rtl_pci,rtlwifi,btcoexist,mac80211
vermagic:       3.19.0-51-generic SMP mod_unload modversions 
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
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)
parm:           ant_sel:Set to 1 or 2 to force antenna number (default 0)
 (int)


[rtl_pci]
filename:       /lib/modules/3.19.0-51-generic/updates/dkms/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     FB5152C16B54885EE27E3CA
depends:        mac80211,rtlwifi
vermagic:       3.19.0-51-generic SMP mod_unload modversions 


[rtlwifi]
filename:       /lib/modules/3.19.0-51-generic/updates/dkms/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     F1626659AE2FC6355721878
depends:        mac80211,cfg80211
vermagic:       3.19.0-51-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/3.19.0-51-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1261743510839D352D1D895
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E0:D6:4E:73:6E:B3:B1:A2:3E:2E:4A:9E:A9:B2:F2:73:99:A4:1C:AF
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.19.0-51-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     EF182B558008C23DD85EF03
depends:        
intree:         Y
vermagic:       3.19.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E0:D6:4E:73:6E:B3:B1:A2:3E:2E:4A:9E:A9:B2:F2:73:99:A4:1C:AF
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rtl8723be]
ant_sel: 0
debug: 1
disable_watchdog: N
fwlps: N
ips: N
msi: N
swenc: Y
swlps: N


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


lp
rtc


##### modprobe options ##################


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


[/etc/modprobe.d/rtl8723be.conf]
options rtl8723be swenc=1 fwlps=0 ips=0


[/etc/modprobe.d/vmware-fuse.conf]
alias char-major-10-229 fuse


##### rc.local ##########################


ifdown wlan0
ifup wlan0
sudo wpa_supplicant -i wlan0 -c /etc/wpa_supplicant/wpa_supplicant.conf -B
sudo dhcpcd wlan0
exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[    8.709623] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    8.726052] r8169 0000:09:00.0 eth0: link down (repeated 2 times)
[    8.726110] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   11.046647] wlan0: authenticate with <MAC 'UPC0047311' [AC1]>
[   11.068439] wlan0: send auth to <MAC 'UPC0047311' [AC1]> (try 1/3)
[   11.099537] wlan0: authenticated
[   11.102489] wlan0: associate with <MAC 'UPC0047311' [AC1]> (try 1/3)
[   11.107260] wlan0: RX AssocResp from <MAC 'UPC0047311' [AC1]> (capab=0x411 status=0 aid=2)
[   11.107811] wlan0: associated
[   11.107833] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   11.164876] bridge-wlan0: device is wireless, enabling SMAC
[   11.164877] bridge-wlan0: up
[   11.164879] bridge-wlan0: attached
[   11.316700] r8169 0000:09:00.0 eth0: link up
[   11.316707] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   12.339215] bridge-wlan0: disabling the bridge
[   12.363927] bridge-wlan0: down
[   12.363933] bridge-wlan0: detached
[   12.363999] bridge-eth0: up
[   12.364002] bridge-eth0: attached


########## wireless info END ############

```


Maybe you have an idea and can help me. Thank you very much.

Martin

---

### Post by txcrittr on 2016-03-03
Have you tried
```
sudo service network-manager restart
```
?

My wifi connection does not work at boot, but restarting the network-manager fixes the problem.

---

### Post by martinoberndorfer on 2016-03-03
Yes I've already tried restarting Network Manager. The only thing that happens is that I loose my wireless connection and have to reinitialize it manaually with
```

sudo wpa_supplicant -i wlan0 -c /etc/wpa_supplicant/wpa_supplicant.conf -B
sudo dhcpcd wlan0

```

---

### Post by martinoberndorfer on 2016-03-04
I just checked the forum guidelines and ran the wireless-info script. Here are the results:

```



########## wireless info START ##########


Report from: 04 Mar 2016 14:05 CET +0100


Booted last: 04 Mar 2016 13:45 CET +0100


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.4 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.19.0-51-generic #58~14.04.1-Ubuntu SMP Fri Feb 26 22:02:58 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


08:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
	Subsystem: Lenovo Device [17aa:b736]
	Kernel driver in use: rtl8723be


09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: Lenovo Device [17aa:380d]
	Kernel driver in use: r8169


##### lsusb #############################


Bus 004 Device 002: ID 8087:8000 Intel Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 8087:8008 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:b728 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 5986:055e Acer, Inc 
Bus 001 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


rtl8723be             143360  0 
btcoexist             413696  1 rtl8723be
rtl_pci                40960  1 rtl8723be
rtlwifi               135168  3 btcoexist,rtl_pci,rtl8723be
mac80211              712704  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              524288  2 mac80211,rtlwifi
ideapad_laptop         24576  0 
sparse_keymap          16384  1 ideapad_laptop
wmi                    20480  0 


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.250  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:44548 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24466 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:63050365 (63.0 MB)  TX bytes:2042865 (2.0 MB)


vmnet1    Link encap:Ethernet  HWaddr <MAC 'vmnet1' [IF]>  
          inet addr:172.16.1.1  Bcast:172.16.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'vmnet1' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:145 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


vmnet8    Link encap:Ethernet  HWaddr <MAC 'vmnet8' [IF]>  
          inet addr:172.16.105.1  Bcast:172.16.105.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'vmnet8' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:146 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.15  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:103 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1012 (1.0 KB)  TX bytes:20216 (20.2 KB)


##### iwconfig ##########################


eth0      no wireless extensions.


vmnet1    no wireless extensions.


vmnet8    no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"UPC0047311"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'UPC0047311' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-34 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 wlan0
172.16.1.0      0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
172.16.105.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


##### resolv.conf #######################


nameserver 195.34.133.21
nameserver 212.186.211.21
nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root       930     1 10 13:45 ?        00:02:03 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: eth0  [Kabelnetzwerkverbindung 1] ------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.0.250
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             8.8.8.8
    DNS:             8.8.4.4


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 


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


no-auto-default=<MAC 'eth0' [IF]>,


[ifupdown]
managed=true


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/3WebCube3E00 1]] (600 root)
[connection] id=3WebCube3E00 1 | type=802-11-wireless
[802-11-wireless] ssid=3WebCube3E00 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/UPC0047311]] (600 root)
[connection] id=UPC0047311 | type=802-11-wireless
[802-11-wireless] ssid=UPC0047311 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore


[[/etc/NetworkManager/system-connections/3WebCube3E00]] (600 root)
[connection] id=3WebCube3E00 | type=802-11-wireless
[802-11-wireless] ssid=3WebCube3E00 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Vienna (based on set time zone)


country AT:
	(2402 - 2482 @ 40), (N/A, 20)
	(5170 - 5250 @ 40), (N/A, 20)
	(5250 - 5330 @ 40), (N/A, 20), DFS
	(5490 - 5710 @ 40), (N/A, 27), DFS
	(57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR


##### iwlist channels ###################


eth0      no frequency information.


vmnet1    no frequency information.


vmnet8    no frequency information.


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


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


vmnet1    Interface doesn't support scanning.


vmnet8    Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      2   APs on   Frequency:2.412 GHz (Channel 1)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'UPC0047311' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"UPC0047311"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000354c9dd826
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'UPC Wi-Free' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-26 dBm  
                    Encryption key:on
                    ESSID:"UPC Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000354c9f603d
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x


##### module infos ######################


[rtl8723be]
filename:       /lib/modules/3.19.0-51-generic/updates/dkms/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         PageHe	<page_he@realsil.com.cn>
srcversion:     03124063245DA6DF009C61D
depends:        rtl_pci,rtlwifi,btcoexist,mac80211
vermagic:       3.19.0-51-generic SMP mod_unload modversions 
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
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)
parm:           ant_sel:Set to 1 or 2 to force antenna number (default 0)
 (int)


[rtl_pci]
filename:       /lib/modules/3.19.0-51-generic/updates/dkms/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     FB5152C16B54885EE27E3CA
depends:        mac80211,rtlwifi
vermagic:       3.19.0-51-generic SMP mod_unload modversions 


[rtlwifi]
filename:       /lib/modules/3.19.0-51-generic/updates/dkms/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     F1626659AE2FC6355721878
depends:        mac80211,cfg80211
vermagic:       3.19.0-51-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/3.19.0-51-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1261743510839D352D1D895
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E0:D6:4E:73:6E:B3:B1:A2:3E:2E:4A:9E:A9:B2:F2:73:99:A4:1C:AF
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.19.0-51-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     EF182B558008C23DD85EF03
depends:        
intree:         Y
vermagic:       3.19.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E0:D6:4E:73:6E:B3:B1:A2:3E:2E:4A:9E:A9:B2:F2:73:99:A4:1C:AF
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rtl8723be]
ant_sel: 0
debug: 1
disable_watchdog: N
fwlps: N
ips: N
msi: N
swenc: Y
swlps: N


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


lp
rtc


##### modprobe options ##################


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


[/etc/modprobe.d/rtl8723be.conf]
options rtl8723be swenc=1 fwlps=0 ips=0


[/etc/modprobe.d/vmware-fuse.conf]
alias char-major-10-229 fuse


##### rc.local ##########################


ifdown wlan0
ifup wlan0
sudo wpa_supplicant -i wlan0 -c /etc/wpa_supplicant/wpa_supplicant.conf -B
sudo dhcpcd wlan0
exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[    8.709623] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    8.726052] r8169 0000:09:00.0 eth0: link down (repeated 2 times)
[    8.726110] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   11.046647] wlan0: authenticate with <MAC 'UPC0047311' [AC1]>
[   11.068439] wlan0: send auth to <MAC 'UPC0047311' [AC1]> (try 1/3)
[   11.099537] wlan0: authenticated
[   11.102489] wlan0: associate with <MAC 'UPC0047311' [AC1]> (try 1/3)
[   11.107260] wlan0: RX AssocResp from <MAC 'UPC0047311' [AC1]> (capab=0x411 status=0 aid=2)
[   11.107811] wlan0: associated
[   11.107833] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   11.164876] bridge-wlan0: device is wireless, enabling SMAC
[   11.164877] bridge-wlan0: up
[   11.164879] bridge-wlan0: attached
[   11.316700] r8169 0000:09:00.0 eth0: link up
[   11.316707] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   12.339215] bridge-wlan0: disabling the bridge
[   12.363927] bridge-wlan0: down
[   12.363933] bridge-wlan0: detached
[   12.363999] bridge-eth0: up
[   12.364002] bridge-eth0: attached


########## wireless info END ############

```[ATTACH=CONFIG]267635[/ATTACH]

---

