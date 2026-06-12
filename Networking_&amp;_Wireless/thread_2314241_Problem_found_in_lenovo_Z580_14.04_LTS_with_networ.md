---
title: "Problem found in lenovo Z580 14.04 LTS with network adapters"
date: 2016-02-19
forum: Networking &amp; Wireless
---

### Post by satyathesatyakam on 2016-02-19
Problem found in lenovo Z580 14.04 LTS with broadcom wifi inbuilt adapter (which I am unable to enable in additional drivers ). I am unable to run NetworkManager manually as well. Basically I can not get internet in Ubuntu and hence posting from age old windows 7.
After browsing through various ubuntu forums I came across and have executed the cult script. Here is the output :-
```



########## wireless info START ##########




Report from: 11 Feb 2016 02:07 IST +0530




Booted last: 11 Feb 2016 01:29 IST +0530




Script from: 27 Sep 2015 00:34 UTC +0000




##### release ###########################




Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty




##### kernel ############################




Linux 3.16.0-60-generic #80~14.04.1-Ubuntu SMP Wed Jan 20 13:37:48 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux




Parameters: ro, quiet, splash, vt.handoff=7




##### desktop ###########################




Ubuntu




##### lspci #############################




02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Lenovo Device [17aa:3975]
    Kernel driver in use: r8169




03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:0587]
    Kernel driver in use: bcma-pci-bridge




##### lsusb #############################




Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0bda:0139 Realtek Semiconductor Corp. RTS5139 Card Reader Controller
Bus 001 Device 003: ID 1058:0740 Western Digital Technologies, Inc. My Passport Essential (WDBACY)
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 0489:e032 Foxconn / Hon Hai Broadcom BCM20702 Bluetooth
Bus 003 Device 002: ID 04f2:b2e2 Chicony Electronics Co., Ltd 
Bus 003 Device 005: ID 04e8:6860 Samsung Electronics Co., Ltd Galaxy (MTP)
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




##### PCMCIA card info ##################




##### rfkill ############################




0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no




##### lsmod #############################




brcmsmac              563061  0 
cordic                 12574  1 brcmsmac
brcmutil               15579  1 brcmsmac
b43                   396480  0 
mac80211              652777  2 b43,brcmsmac
cfg80211              498458  3 b43,brcmsmac,mac80211
ssb                    62352  1 b43
bcma                   52320  3 b43,brcmsmac
wmi                    19193  0 
ideapad_laptop         18278  0 
sparse_keymap          13948  1 ideapad_laptop




##### interfaces ########################




auto lo
iface lo inet loopback




auto eth0
iface eth0 inet static




auto wlan0
iface wlan0 inet dhcp




##### ifconfig ##########################




eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)




wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)




wlan0:avahi Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:169.254.9.118  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1




##### iwconfig ##########################




eth0      no wireless extensions.




lo        no wireless extensions.




wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=27 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          




##### route #############################




Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         0.0.0.0         0.0.0.0         U     1003   0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 wlan0




##### resolv.conf #######################




##### network managers ##################




Installed:




    NetworkManager




Running:




    None found.




##### NetworkManager info ###############




** (process:2802): WARNING **: Could not initialize NMClient /org/freedesktop/NetworkManager: The name org.freedesktop.NetworkManager was not provided by any .service files




** (process:2802): WARNING **: error: could not connect to NetworkManager




NetworkManager Tool




State: unknown




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
managed=false




nm-system-settings.conf (used up to Ubuntu 10.04):




##### NetworkManager profiles ###########




[[/etc/NetworkManager/system-connections/SancharizInternet]] (600 root)
[connection] id=SancharizInternet | type=802-11-wireless
[802-11-wireless] ssid=SancharizInternet | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto




[[/etc/NetworkManager/system-connections/sanchari's internet]] (600 root)
[connection] id=sanchari's internet | type=802-11-wireless
[802-11-wireless] ssid=sanchari's internet | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto




##### iw reg get ########################




Region: Asia/Kolkata (based on set time zone)




country US:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)
    (57240 - 63720 @ 2160), (N/A, 40)




##### iwlist channels ###################




eth0      no frequency information.




lo        no frequency information.




wlan0     11 channels in total; available frequencies :
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




##### iwlist scan #######################




eth0      Interface doesn't support scanning.




lo        Interface doesn't support scanning.




Channel occupancy:




      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.417 GHz (Channel 2)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      3   APs on   Frequency:2.462 GHz (Channel 11)




wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Akamal' [AC1]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"Akamal"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000002825cff05
                    Extra: Last beacon: 24ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Anmol' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"Anmol"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001abf01fd8
                    Extra: Last beacon: 24ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Reliance Wi-Pod-137' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"Reliance Wi-Pod-137"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000a6f0dd83
                    Extra: Last beacon: 24ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'MBLAZE-AC3633R2-5D12' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"MBLAZE-AC3633R2-5D12"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001eb51bc95
                    Extra: Last beacon: 24ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'SancharizInternet' [AC5]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key:on
                    ESSID:"SancharizInternet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000028231fa99
                    Extra: Last beacon: 24ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'aditya' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"aditya"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001597ee187
                    Extra: Last beacon: 68ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'Tata-Photon-Max-Wi-Fi-CAA1' [AC7]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Tata-Photon-Max-Wi-Fi-CAA1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000486d514e4
                    Extra: Last beacon: 24ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK




##### module infos ######################




[brcmsmac]
filename:       /lib/modules/3.16.0-60-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     21EC7461BC4D6521DBDCA51
depends:        bcma,mac80211,brcmutil,cfg80211,cordic
intree:         Y
vermagic:       3.16.0-60-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        BE:C0:E2:4C:6C:15:79:A9:A8:E8:83:45:2F:3F:21:D7:73:D1:FE:BD
sig_hashalgo:   sha512




[brcmutil]
filename:       /lib/modules/3.16.0-60-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     A0783053E3D218C552A3D06
depends:        
intree:         Y
vermagic:       3.16.0-60-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        BE:C0:E2:4C:6C:15:79:A9:A8:E8:83:45:2F:3F:21:D7:73:D1:FE:BD
sig_hashalgo:   sha512




[b43]
filename:       /lib/modules/3.16.0-60-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     A11EA44C59A05A9A025A03F
depends:        bcma,ssb,mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-60-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        BE:C0:E2:4C:6C:15:79:A9:A8:E8:83:45:2F:3F:21:D7:73:D1:FE:BD
sig_hashalgo:   sha512
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)




[mac80211]
filename:       /lib/modules/3.16.0-60-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     6960FE598160A2BE736A5B1
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-60-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        BE:C0:E2:4C:6C:15:79:A9:A8:E8:83:45:2F:3F:21:D7:73:D1:FE:BD
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)




[cfg80211]
filename:       /lib/modules/3.16.0-60-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     046346857FD53951C911443
depends:        
intree:         Y
vermagic:       3.16.0-60-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        BE:C0:E2:4C:6C:15:79:A9:A8:E8:83:45:2F:3F:21:D7:73:D1:FE:BD
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)




[ssb]
filename:       /lib/modules/3.16.0-60-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     2055C3093DA2EE9DEB5572C
depends:        
intree:         Y
vermagic:       3.16.0-60-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        BE:C0:E2:4C:6C:15:79:A9:A8:E8:83:45:2F:3F:21:D7:73:D1:FE:BD
sig_hashalgo:   sha512




[bcma]
filename:       /lib/modules/3.16.0-60-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     D52E980A55E0AC3C372382C
depends:        
intree:         Y
vermagic:       3.16.0-60-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        BE:C0:E2:4C:6C:15:79:A9:A8:E8:83:45:2F:3F:21:D7:73:D1:FE:BD
sig_hashalgo:   sha512




##### module parameters #################




[b43]
allhwsupport: 0
bad_frames_preempt: 0
btcoex: 1
hwpctl: 0
hwtkip: 0
nohwcrypt: 0
pio: 0
qos: 1
verbose: 2




[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
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




[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1




##### rc.local ##########################




exit 0




##### pm-utils ##########################




##### udev rules ########################




[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"




##### dmesg #############################




[ 1829.895113] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1829.895129] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[ 1829.895804] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready




########## wireless info END ############
```


_**Update:**_
Executed following commands after suggestions in a thread :-
```

sudo apt-get update
sudo iw reg set IN
sudo sed -i 's/^REG.*=$/&IN/' /etc/default/crda
sudo rm -rf b43
sudo rm -rf ssb
echo -e "blacklist b43\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -rf brcmsmac
sudo modprobe -v brcmsmac

```
Which did not help. The ethernet interface looks up but is actually not and could not connect to the gateway even by setting static IP / gateway / dns

---

### Post by chili555 on 2016-02-19
This declaration in the NetworkManager.conf file means that NM will NOT manage any interfaces which are declared in /etc/network/interfaces:> [main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq




no-auto-default=<MAC 'eth0' [IF]>,




[ifupdown]
[COLOR="#FF0000"]managed=false[/COLOR] The latter file includes a faulty listing for wlan0:```
auto lo
iface lo inet loopback




auto eth0
iface eth0 inet static




auto wlan0
iface wlan0 inet dhcp
```Your ethernet listing is faulty because it declares that eth0 will take a static IP address and then doesn't specify one! I suggest that you change it. I will suggest a file arrangement in a few moments.

The wlan0 listing is also faulty. No wireless will ever connect without an SSID being named and, in most cases, the WPA2 password being given.

Since Network Manager is usually the best method to manage these interfaces, I suggest you open a terminal and do:```
sudo gedit /etc/network/interfaces
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the file to:```
auto lo
iface lo inet loopback
```Proofread carefully, save and close the text editor.

Reboot.

Now does your network appear in Network Manager?

---

### Post by satyathesatyakam on 2016-02-21
Thank you for your response but that did not help in statring the NM :-
```

satyakam@satyakam-Lenovo-Z580:~$ sudo vi /etc/network/interfaces
[sudo] password for satyakam: 
satyakam@satyakam-Lenovo-Z580:~$ 
satyakam@satyakam-Lenovo-Z580:~$ 
satyakam@satyakam-Lenovo-Z580:~$ 
satyakam@satyakam-Lenovo-Z580:~$ 
satyakam@satyakam-Lenovo-Z580:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
satyakam@satyakam-Lenovo-Z580:~$ sudo service networking 
force-reload  reload        restart       start         stop
satyakam@satyakam-Lenovo-Z580:~$ sudo service networking restart
stop: Job failed while stopping
start: Job is already running: networking
satyakam@satyakam-Lenovo-Z580:~$ NetworkManager 
You must be root to run NetworkManager!
satyakam@satyakam-Lenovo-Z580:~$ sudo NetworkManager 

(NetworkManager:3003): GLib-WARNING **: GError set over the top of a previous GError or uninitialized memory.
This indicates a bug in someone's code. You must ensure an error is NULL before it's set.
The overwriting error message was: Key file does not have group 'connectivity'
satyakam@satyakam-Lenovo-Z580:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 08:9e:01:db:90:51  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0:avahi Link encap:Ethernet  HWaddr 08:9e:01:db:90:51  
          inet addr:169.254.8.7  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:536 errors:0 dropped:0 overruns:0 frame:0
          TX packets:536 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:40832 (40.8 KB)  TX bytes:40832 (40.8 KB)

wlan0     Link encap:Ethernet  HWaddr f4:b7:e2:f5:1e:87  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr f4:b7:e2:f5:1e:87  
          inet addr:169.254.9.118  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

satyakam@satyakam-Lenovo-Z580:~$ 
satyakam@satyakam-Lenovo-Z580:~$ 

```
After this I rebooted the machine to see that ifconfig displays information only about loopback interface. Furthermore, NM still is absent and does not start manually.

---

### Post by chili555 on 2016-02-21
What is the exact response to:```
sudo service network-manager restart
```And this:```
sudo iwlist wlan0 scan
rfkill list all
```

---

### Post by satyathesatyakam on 2016-02-24
Here is the output :-
```

satyakam@satyakam-Lenovo-Z580:~$ sudo service network-manager restart
stop: Unknown instance: 
network-manager start/running, process 2125
satyakam@satyakam-Lenovo-Z580:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Network is down

satyakam@satyakam-Lenovo-Z580:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
satyakam@satyakam-Lenovo-Z580:~$ 
satyakam@satyakam-Lenovo-Z580:~$ ps -aef | grep 2125
satyakam  2219  1993  0 15:14 pts/12   00:00:00 grep --color=auto 2125
satyakam@satyakam-Lenovo-Z580:~$ 

```

---

### Post by chili555 on 2016-02-24
Please try:```
sudo -i
modprobe -r b43
modprobe -r ssb
echo "blacklist b43"  >>  /etc/modprobe.d/blacklist.conf
echo "blacklist ssb"  >>  /etc/modprobe.d/blacklist.conf
exit
```Any improvement? Does it scan:```
sudo iwlist wlan0 scan
```Is NM running?```
ps aux | grep Network
```It may take a reboot.

---

### Post by satyathesatyakam on 2016-02-25
I did as you asked me to (and rebooted) after which I saw this:-

```


root@satyakam-Lenovo-Z580:~# sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Network is down

root@satyakam-Lenovo-Z580:~# ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2456 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2456 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:196840 (196.8 KB)  TX bytes:196840 (196.8 KB)

root@satyakam-Lenovo-Z580:~# 
root@satyakam-Lenovo-Z580:~# 

```
Then I did this and then that happen :-
```

root@satyakam-Lenovo-Z580:~# ifconfig wlan0 up
root@satyakam-Lenovo-Z580:~# sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 0A:27:22:B7:99:0B
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"Byron-6"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00c80ec25e6efe14
                    Extra: Last beacon: 552ms ago
                    IE: Unknown: 00074279726F6E2D36
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 3204B048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 331AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080C00000000000000000000000000000000000000
                    IE: Unknown: 341601080C00000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 02 - Address: 06:27:22:B7:99:0B
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"Admin"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000ec25e6ef3bf
                    Extra: Last beacon: 600ms ago
                    IE: Unknown: 000541646D696E
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 3204B048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 331AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080C00000000000000000000000000000000000000
                    IE: Unknown: 341601080C00000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 03 - Address: 00:24:B2:49:EC:A0
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"CPACambs"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000027020c2184
                    Extra: Last beacon: 612ms ago
                    IE: Unknown: 000843504143616D6273
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 05040001000E
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A0C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001300000000000000000000000000000000000000
                    IE: Unknown: DD090010180203F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C330C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001300000000000000000000000000000000000000
          Cell 04 - Address: 0A:27:22:B7:98:D6
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"Byron-2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000a660d1541bf
                    Extra: Last beacon: 284ms ago
                    IE: Unknown: 00074279726F6E2D32
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030106
                    IE: Unknown: 0504000100C0
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 3204B048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080C00000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD1300156D00010100010202E58106002722B698D6
          Cell 05 - Address: C2:9F:DB:87:F7:F4
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption key:on
                    ESSID:"Admin"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00c8029072e68569
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 000541646D696E
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 3204B048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 331AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080C00000000000000000000000000000000000000
                    IE: Unknown: 341606080C00000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 06 - Address: C6:9F:DB:87:F7:F4
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"Byron-4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000029072e697d3
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 00074279726F6E2D34
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 3204B048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 331AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080C00000000000000000000000000000000000000
                    IE: Unknown: 341606080C00000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 07 - Address: 30:91:8F:10:56:77
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"TNCAP105677"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 000B544E434150313035363737
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A1E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D16060F0000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180200000C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 08 - Address: C8:3A:35:FC:53:E0
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"Nobleo"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000022d3a183
                    Extra: Last beacon: 348ms ago
                    IE: Unknown: 00064E6F626C656F
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AF0181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080000000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F00C0000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 09 - Address: 06:27:22:B7:98:D6
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"Admin"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000a660d13a830
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 000541646D696E
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 3204B048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 331AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080C00000000000000000000000000000000000000
                    IE: Unknown: 341606080C00000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 10 - Address: 06:27:22:57:6E:79
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"Admin"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000ff0b28b75d8
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 000541646D696E
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 3204B048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 331AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080C00000000000000000000000000000000000000
                    IE: Unknown: 34160B080C00000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 11 - Address: 0A:27:22:57:6E:79
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"Byron-3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00c80ff0b28b89a5
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 00074279726F6E2D33
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 3204B048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 331AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080C00000000000000000000000000000000000000
                    IE: Unknown: 34160B080C00000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 12 - Address: 44:E9:DD:AC:96:7A
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"Byron-1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000d07bc71919f
                    Extra: Last beacon: 84ms ago
                    IE: Unknown: 00074279726F6E2D31
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400030000
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080000000000000000000000000000000000000000
                    IE: Unknown: DD180050F204104A00011010440001021049000600372A000120
                    IE: Unknown: DD090010180200F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 13 - Address: F0:92:1C:A0:9B:E3
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:off
                    ESSID:"HP-Print-E3-Deskjet 3520 series"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001870257142
                    Extra: Last beacon: 344ms ago
                    IE: Unknown: 001F48502D5072696E742D45332D4465736B6A6574203335323020736572696573
                    IE: Unknown: 010802040B0C12161824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A0055010200050039010400580200007B01040058020000330102
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D1606080000000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 14 - Address: FA:8F:CA:7D:47:7C
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000187023e142
                    Extra: Last beacon: 296ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050401020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A2C1103FF00000000000000000000000000000000000000000000
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D1606080000000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 15 - Address: 0A:27:22:57:6F:07
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Byron-10"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000e8481571dc0
                    Extra: Last beacon: 44ms ago
                    IE: Unknown: 00084279726F6E2D3130
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010068
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 3204B048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080C00000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD1300156D00010100010202E58106002722566F07

root@satyakam-Lenovo-Z580:~# 
root@satyakam-Lenovo-Z580:~# 

```

Even though that felt good but my network was still down and so was the Network Manager:-
```

root@satyakam-Lenovo-Z580:~# ps aux | grep -i Network
satyakam  1976  0.0  0.3 201196  5812 ?        Sl   12:50   0:00 /usr/lib/glib-networking/glib-pacrunner
root      2203  0.0  0.1  15944  2272 pts/2    S+   13:15   0:00 grep --color=auto -i Network
root@satyakam-Lenovo-Z580:~# 

```

---

### Post by chili555 on 2016-02-25
Would you rather start the process of tracking down why Network Manager isn't starting on boot or skip to setting up your wireless in /etc/network/interfaces?

NM is preferrable if you need to connect at the library, university, etc. The latter is just fine if this is a stay-at-home computer.

In case the answer is the latter, I'd amend /etc/network/interfaces to something like this:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-ssid <your_router>
wpa-psk <your_wpa_key>
```Get the system to read and use the changes:

```
sudo ifdown wlan0 && sudo ifup -v wlan0

```
Did you connect?

```
ping -c3 192.168.1.1  [COLOR="#FF0000"]<--or whatever your router's IP address is[/COLOR]
ping -c3 www.ubuntu.com

```

If you'd rather get NM going instead, please run and post:```
cat /var/log/syslog | grep etwork | tail -n20
```

---

### Post by satyathesatyakam on 2016-02-25
Problem resolved in lenevo Z580 14.04 LTS with network adapters :D
You did put me in a dilemma when asked about wither to use network interfaces or to use the network manager. Hence, I chose both (one after another)!
1. added ssid / password to interfaces -> ifup / down -> got the connection
2. did apt-get update + upgrade
3. NM upgraded -> removed the interfaces configuration
4. rebooted
5. posted in the thread with the ubuntu and lenovo couple saying many thanks to you!

---

