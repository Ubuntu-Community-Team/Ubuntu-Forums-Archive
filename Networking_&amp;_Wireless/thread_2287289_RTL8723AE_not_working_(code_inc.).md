---
title: "RTL8723AE not working (code inc.)"
date: 2015-07-18
forum: Networking &amp; Wireless
---

### Post by warren3 on 2015-07-18
Hi.

Sorry to open two threads.  My other thread is about the intel 7260 which is now in the draw after I was having problems with it and changed it with a RTL8723AE.  Now this is giving my problems after only a day just like the 7260.  I am pulling my hair out.

The connection works for a short time then stops or slows to a crawl. 

I am running 14.04.2.

I tried this:

sudo modprobe -rv rtl8723ae
sudo modprobe -v rtl8723ae swenc=1 ips=0 fwlps=0

But got no joy and I take it this command disappears after reboot?

Here is my code for the wireless script.

```


########## wireless info START ##########

Report from: 18 Jul 2015 12:30 BST +0100

Booted last: 18 Jul 2015 12:10 BST +0100

Script from: 14 Jul 2015 17:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-43-generic #58~14.04.1-Ubuntu SMP Mon Jun 22 10:21:20 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter [10ec:8723]
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0723]
    Kernel driver in use: rtl8723ae

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 0930:021d Toshiba Corp. 
Bus 002 Device 002: ID 062a:4101 Creative Labs 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8723ae              81799  0 
rtl8723_common         23361  1 rtl8723ae
rtl_pci                26690  1 rtl8723ae
rtlwifi                64255  2 rtl_pci,rtl8723ae
mac80211              652777  3 rtl_pci,rtlwifi,rtl8723ae
cfg80211              494362  2 mac80211,rtlwifi
snd_soc_rt5640         93042  0 
snd_soc_rl6231         13037  1 snd_soc_rt5640
snd_soc_core          200204  1 snd_soc_rt5640
snd_pcm               104112  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan1     Link encap:Ethernet  HWaddr <MAC 'wlan1' [IF]>  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan1' [IF]>/64 Scope:Link
          inet6 addr: fde2:f42b:506e:0:<IP6 'wlan1' [IF]>/64 Scope:Global
          inet6 addr: fde2:f42b:506e:0:4981:340c:4c9e:5e46/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33478 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23226 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:42068510 (42.0 MB)  TX bytes:2658341 (2.6 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:"SKYDBE00"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'SKYDBE00' [AC1]>   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=26 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:760   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan1
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan1

##### resolv.conf #######################

nameserver 127.0.1.1
search Home

##### network managers ##################

Installed:

    NetworkManager

Running:

root       851     1  0 12:10 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: wlan1  [SKYDBE00 1] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723ae
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan1' [IF]>

  Capabilities:
    Speed:           18 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *SKYDBE00:       Infra, <MAC 'SKYDBE00' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 72 WPA2

  IPv4 Settings:
    Address:         192.168.0.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

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

[[/etc/NetworkManager/system-connections/SKYDBE00 1]] (600 root)
[connection] id=SKYDBE00 1 | type=802-11-wireless
[802-11-wireless] ssid=SKYDBE00 | mac-address=<MAC 'wlan1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/SKYDBE00]] (600 root)
[connection] id=SKYDBE00 | type=802-11-wireless
[802-11-wireless] ssid=SKYDBE00 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/London (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan1     13 channels in total; available frequencies :
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
          Current Frequency:2.462 GHz (Channel 11)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.462 GHz (Channel 11)

wlan1     Scan completed :
          Cell 01 - Address: <MAC 'SKYDBE00' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:on
                    ESSID:"SKYDBE00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000004df84187
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8723ae]
filename:       /lib/modules/3.16.0-43-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723ae/rtl8723ae.ko
firmware:       rtlwifi/rtl8723fw_B.bin
firmware:       rtlwifi/rtl8723fw.bin
description:    Realtek 8723E 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     5FDB4D618B8E6F42C4EA3C8
depends:        rtlwifi,rtl8723-common,rtl_pci,mac80211
intree:         Y
vermagic:       3.16.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B9:68:43:D5:33:87:3C:28:09:11:67:45:21:94:7A:04:B9:74:2E:72
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl8723_common]
filename:       /lib/modules/3.16.0-43-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     7410431A59C24B1BC33226E
depends:        
intree:         Y
vermagic:       3.16.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B9:68:43:D5:33:87:3C:28:09:11:67:45:21:94:7A:04:B9:74:2E:72
sig_hashalgo:   sha512

[rtl_pci]
filename:       /lib/modules/3.16.0-43-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     3273ECD6028617EFD27E4F4
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.16.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B9:68:43:D5:33:87:3C:28:09:11:67:45:21:94:7A:04:B9:74:2E:72
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.16.0-43-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     8362106E96F806A9DBAE565
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B9:68:43:D5:33:87:3C:28:09:11:67:45:21:94:7A:04:B9:74:2E:72
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.16.0-43-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     315DCE1E2614AE1F38132D3
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B9:68:43:D5:33:87:3C:28:09:11:67:45:21:94:7A:04:B9:74:2E:72
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.16.0-43-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     33ED2C1448F5AEDBE7AF59E
depends:        
intree:         Y
vermagic:       3.16.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B9:68:43:D5:33:87:3C:28:09:11:67:45:21:94:7A:04:B9:74:2E:72
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723ae]
debug: 0
fwlps: Y
ips: Y
swenc: N
swlps: N

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
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x08b1 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# PCI device 0x10ec:0x8723 (rtl8723ae)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

[    3.480542] rtl8723ae 0000:02:00.0: enabling device (0000 -> 0003)
[    3.519066] rtl8723ae: Using firmware rtlwifi/rtl8723fw_B.bin
[    3.557658] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    3.558025] rtlwifi: wireless switch is on
[    3.862766] systemd-udevd[329]: renamed network interface wlan0 to wlan1
[    4.504882] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[    5.539427] wlan1: authenticate with <MAC 'SKYDBE00' [AC1]>
[    5.555658] wlan1: send auth to <MAC 'SKYDBE00' [AC1]> (try 1/3)
[    5.557521] wlan1: authenticated
[    5.562873] wlan1: associate with <MAC 'SKYDBE00' [AC1]> (try 1/3)
[    5.567231] wlan1: RX AssocResp from <MAC 'SKYDBE00' [AC1]> (capab=0x411 status=0 aid=2)
[    5.567491] wlan1: associated
[    5.567521] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   72.683598] [UFW BLOCK] IN=wlan1 OUT= MAC=<MAC 'wlan1' [IF]>:90:01:3b:6d:be:00:08:00 SRC=108.160.169.175 DST=192.168.0.2 LEN=329 TOS=0x00 PREC=0x00 TTL=56 ID=26821 DF PROTO=TCP SPT=443 DPT=35962 WINDOW=73 RES=0x00 ACK PSH URGP=0 
[  173.244996] wlan1: deauthenticating from <MAC 'SKYDBE00' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  174.260804] wlan1: authenticate with <MAC 'SKYDBE00' [AC1]>
[  174.292877] wlan1: send auth to <MAC 'SKYDBE00' [AC1]> (try 1/3)
[  174.295308] wlan1: authenticated
[  174.300452] wlan1: associate with <MAC 'SKYDBE00' [AC1]> (try 1/3)
[  174.303392] wlan1: RX AssocResp from <MAC 'SKYDBE00' [AC1]> (capab=0x411 status=0 aid=2)
[  174.303650] wlan1: associated
[  193.017144] [UFW BLOCK] IN=wlan1 OUT= MAC=<MAC 'wlan1' [IF]>:90:01:3b:6d:be:00:08:00 SRC=108.160.169.175 DST=192.168.0.2 LEN=329 TOS=0x00 PREC=0x00 TTL=56 ID=26822 DF PROTO=TCP SPT=443 DPT=35962 WINDOW=73 RES=0x00 ACK PSH URGP=0 
[  313.445073] [UFW BLOCK] IN=wlan1 OUT= MAC=<MAC 'wlan1' [IF]>:90:01:3b:6d:be:00:08:00 SRC=108.160.169.175 DST=192.168.0.2 LEN=329 TOS=0x00 PREC=0x00 TTL=56 ID=26823 DF PROTO=TCP SPT=443 DPT=35962 WINDOW=73 RES=0x00 ACK PSH URGP=0 
[  433.756661] [UFW BLOCK] IN=wlan1 OUT= MAC=<MAC 'wlan1' [IF]>:90:01:3b:6d:be:00:08:00 SRC=108.160.169.175 DST=192.168.0.2 LEN=329 TOS=0x00 PREC=0x00 TTL=56 ID=26824 DF PROTO=TCP SPT=443 DPT=35962 WINDOW=73 RES=0x00 ACK PSH URGP=0 
[  554.127791] [UFW BLOCK] IN=wlan1 OUT= MAC=<MAC 'wlan1' [IF]>:90:01:3b:6d:be:00:08:00 SRC=108.160.169.175 DST=192.168.0.2 LEN=329 TOS=0x00 PREC=0x00 TTL=56 ID=26825 DF PROTO=TCP SPT=443 DPT=35962 WINDOW=73 RES=0x00 ACK PSH URGP=0 
[  674.659700] [UFW BLOCK] IN=wlan1 OUT= MAC=<MAC 'wlan1' [IF]>:90:01:3b:6d:be:00:08:00 SRC=108.160.169.175 DST=192.168.0.2 LEN=329 TOS=0x00 PREC=0x00 TTL=56 ID=26826 DF PROTO=TCP SPT=443 DPT=35962 WINDOW=73 RES=0x00 ACK PSH URGP=0 
[  795.234178] [UFW BLOCK] IN=wlan1 OUT= MAC=<MAC 'wlan1' [IF]>:90:01:3b:6d:be:00:08:00 SRC=108.160.169.175 DST=192.168.0.2 LEN=329 TOS=0x00 PREC=0x00 TTL=56 ID=26827 DF PROTO=TCP SPT=443 DPT=35962 WINDOW=73 RES=0x00 ACK PSH URGP=0 

########## wireless info END ############


```

Thanks

---

### Post by praseodym on 2015-07-18
You are using a firewall? If yes:

```
sudo apt-get remove --purge ufw gufw
sudo iptables -t filter -n -L -v
sudo iptables -F
sudo iptables -X
```

---

### Post by warren3 on 2015-07-18
I'm using Uncomplicated Firewall (UFW).

What does that code do?

Thanks.

---

### Post by praseodym on 2015-07-19
It uninstalls it. If the firewall in your router is activated it is enough. Obviously, the connection is blocked, see the "dmesg" output of the script

---

### Post by warren3 on 2015-07-19
I see.  It is strange that all of a sudden this happens after using the FW with no problems since I installed Ubuntu.

I don't really want to use the RTL8723AE tbh because I was using an Intel 7260 and then I got these problems and switched over to the RTL8723AE because I had one spare to hand.  Do you think the FW problem could of been affecting the 7260 as well?

If I put the 7260 back in and do a wireless script could you have a look at it for me?

Thanks.

---

