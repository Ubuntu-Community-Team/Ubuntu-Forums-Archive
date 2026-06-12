---
title: "KXStudio won't connect to wireless"
date: 2015-04-30
forum: Networking &amp; Wireless
---

### Post by henrique8 on 2015-04-30
Hello everybody!

So, I've just installed KXStudio 14.04, and I'm pretty new to it and to Ubuntu itself.

My problem seems to be quite simple, but I don't know for sure. When I first logged in on the KXStudio, I was able to connect to the internet normally, via wireless. Suddenly, I lost the connection and when I tried to reconnect, I couldn't.
I still can see the connection on my toolbar, but when I click the 'connect' button, nothing happens.

Any ideas?

Thanks in advance!

Henrique

---

### Post by michi1983 on 2015-04-30
Hi Henrique,

please be so kind and follow these instructions from the [sticky post]("http://ubuntuforums.org/showthread.php?t=370108") and provide us with with the output of the file so we can see what's going on.

Greetz

---

### Post by henrique8 on 2015-04-30
Hello michi1983, thank you for the advice! I should had take a look on the post you've mentioned before posting this one.

So, I've upgraded my system and run the wireless script and this is what I got:

```

########## wireless info START ##########

Report from: 30 Apr 2015 20:57 BRT -0300

Booted last: 30 Apr 2015 20:42 BRT -0300

Script from: 06 Apr 2015 17:23 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-51-lowlatency #84-Ubuntu SMP PREEMPT Wed Apr 15 12:35:09 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

default

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Toshiba America Info Systems Device [1179:fc30]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8184]
    Kernel driver in use: rtl8192ce

##### lsusb #############################

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b1d6 Chicony Electronics Co., Ltd CNF9055 Toshiba Webcam
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

./wireless_script: line 176: rfkill: command not found

##### lsmod #############################

rtl8192ce              53550  0 
rtl_pci                26690  1 rtl8192ce
rtlwifi                63475  2 rtl_pci,rtl8192ce
rtl8192c_common        53172  1 rtl8192ce
mac80211              638949  3 rtl_pci,rtlwifi,rtl8192ce
cfg80211              496328  2 mac80211,rtlwifi
wmi                    19177  1 toshiba_acpi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.42  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fdf4:22ef:e281:1:b5ba:a3f0:18fe:6d80/64 Scope:Global
          inet6 addr: fdf4:22ef:e281:1:9093:f9ff:fee9:9c04/64 Scope:Global
          inet6 addr: 2804:431:9718:19e5:9093:f9ff:fee9:9c04/64 Scope:Global
          inet6 addr: 2804:431:9718:19e5:b5ba:a3f0:18fe:6d80/64 Scope:Global
          inet6 addr: fe80::9093:f9ff:fee9:9c04/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15403 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11528 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15836919 (15.8 MB)  TX bytes:1453050 (1.4 MB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

./wireless_script: line 189: iwconfig: command not found

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search home

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    tijupa:          Infra, <MAC 'tijupa' [AN1]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 100 WPA2
    Linksys:         Infra, <MAC 'Linksys' [AN2]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 50
    Tenda_119C18:    Infra, <MAC 'Tenda_119C18' [AN3]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 17 WPA
    Borracha:        Infra, <MAC 'Borracha' [AN4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    CLARO-WIFI2:     Infra, <MAC 'CLARO-WIFI2' [AN5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0
    Fabiana_Rocha:   Infra, <MAC 'Fabiana_Rocha' [AN6]>, Freq 2437 MHz, Rate 11 Mb/s, Strength 60 WPA WPA2
    NET-VIRTUA-WIFI: Infra, <MAC 'NET-VIRTUA-WIFI' [AN7]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0
    virus:           Infra, <MAC 'virus' [AN8]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    CLARO-WIFI:      Infra, <MAC 'CLARO-WIFI' [AN9]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 50 WPA2 Enterprise
    BordoVermelho:   Infra, <MAC 'BordoVermelho' [AN10]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    BordoVermelho-convidado: Infra, <MAC 'BordoVermelho-convidado' [AN11]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 24

- Device: eth0  [New 802-3-ethernet connection] --------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.42
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

  IPv6 Settings:
    Address:         2804:431:9718:19e5:b5ba:a3f0:18fe:6d80
    Prefix:          64
    Gateway:         fe80::feb0:c4ff:fe62:63a8

    Address:         2804:431:9718:19e5:9093:f9ff:fee9:9c04
    Prefix:          64
    Gateway:         fe80::feb0:c4ff:fe62:63a8

    Address:         fdf4:22ef:e281:1:b5ba:a3f0:18fe:6d80
    Prefix:          64
    Gateway:         fe80::feb0:c4ff:fe62:63a8

    Address:         fdf4:22ef:e281:1:9093:f9ff:fee9:9c04
    Prefix:          64
    Gateway:         fe80::feb0:c4ff:fe62:63a8

    Address:         fe80::9093:f9ff:fee9:9c04
    Prefix:          64
    Gateway:         fe80::feb0:c4ff:fe62:63a8

    DNS:             fdf4:22ef:e281:1:feb0:c4ff:fe62:63a8

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=false
WimaxEnabled=true
WiMAXEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/dlink]] (600 root)
[connection] id=dlink | type=802-11-wireless | permissions=user:henrique:;
[802-11-wireless] ssid=dlink | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/virus]] (600 root)
[connection] id=virus | type=802-11-wireless | permissions=user:henrique:;
[802-11-wireless] ssid=virus | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NET-VIRTUA-WIFI]] (600 root)
[connection] id=NET-VIRTUA-WIFI | type=802-11-wireless | permissions=user:henrique:;
[802-11-wireless] ssid=NET-VIRTUA-WIFI | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

##### iw reg get ########################

Region: America/Sao_Paulo (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

./wireless_script: line 250: iwlist: command not found

##### iwlist scan #######################

Acquisition of admin privileges failed.

##### module infos ######################

[rtl8192ce]
filename:       /lib/modules/3.13.0-51-lowlatency/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     A5286D03221770A227ABC5B
depends:        rtlwifi,rtl_pci,rtl8192c-common,mac80211
intree:         Y
vermagic:       3.13.0-51-lowlatency SMP preempt mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        88:14:89:6F:51:B1:14:D8:E2:06:8C:4D:1D:90:61:30:F2:86:E8:36
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

[rtl_pci]
filename:       /lib/modules/3.13.0-51-lowlatency/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     D5E4890DC428FA5A1BF92DF
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.13.0-51-lowlatency SMP preempt mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        88:14:89:6F:51:B1:14:D8:E2:06:8C:4D:1D:90:61:30:F2:86:E8:36
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.13.0-51-lowlatency/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     730FEE1A7696EA37A982482
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-51-lowlatency SMP preempt mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        88:14:89:6F:51:B1:14:D8:E2:06:8C:4D:1D:90:61:30:F2:86:E8:36
sig_hashalgo:   sha512

[rtl8192c_common]
filename:       /lib/modules/3.13.0-51-lowlatency/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     32F826C623BC49F764F7974
depends:        
intree:         Y
vermagic:       3.13.0-51-lowlatency SMP preempt mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        88:14:89:6F:51:B1:14:D8:E2:06:8C:4D:1D:90:61:30:F2:86:E8:36
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-51-lowlatency/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     29A87AE7782ED3657631C32
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-51-lowlatency SMP preempt mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        88:14:89:6F:51:B1:14:D8:E2:06:8C:4D:1D:90:61:30:F2:86:E8:36
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-51-lowlatency/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     176113E009F723E69BE9BAB
depends:        
intree:         Y
vermagic:       3.13.0-51-lowlatency SMP preempt mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        88:14:89:6F:51:B1:14:D8:E2:06:8C:4D:1D:90:61:30:F2:86:E8:36
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8192ce]
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
snd-aloop

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

[/etc/modprobe.d/blacklist-pcspkr.conf]
blacklist pcspkr

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

[/etc/modprobe.d/snd-seq-dummy_16.conf]
options snd-seq-dummy ports=16

##### rc.local ##########################

echo 2048 > /sys/class/rtc/rtc0/max_user_freq
exit 0

##### pm-utils ##########################

[/etc/pm/sleep.d/10_kill-alsa-bridge] (755 root)
case "$1" in
        hibernate|suspend)
                killall -KILL alsa_in alsa_out zita-a2j zita-j2a || true
                ;;
esac

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8176 (rtl8192ce)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[   12.118597] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[   12.567252] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   12.567463] rtlwifi: wireless switch is on
[   19.658630] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)

########## wireless info END ############


```

Hope you can find out what is wrong!

Thanks,
Henrique

---

### Post by michi1983 on 2015-05-01
Try a```
sudo apt-get install wireless-tools
```and then reboot your machine, unplug your ethernet cable and see if your wifi comes up.

---

### Post by henrique8 on 2015-05-01
I've what you suggested and it still don't connect.
Let me try to explain better what is going on... I still can see the connections available for wifi, but when I click the 'connect' button, it seems to be no function assigned for the button, it do nothing!
[ATTACH=CONFIG]261697[/ATTACH]

Any other ideas?

---

### Post by michi1983 on 2015-05-01
Okay please go into a terminal and try
```

sudo iwconfig wlan0 essid CLARO-WIFI key $password

```
$password = your wifi key

and see if it connects.

---

### Post by henrique8 on 2015-05-01
It still doesn't connect. There are no outputs for this command, and it seems to run ok, but no connetion :(

And by the way, my network is the "virus" one 

The strange thing is that when I first logged in, the wi-fi was ok... And I didn't do anything that could possibly break it.

Any more ideas?

---

### Post by praseodym on 2015-05-01
Deactivate IPv6 in the network-manager settings, then run
```

echo "options rtl8192ce swlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8192ce.conf
sudo modprobe -rfv rtl8192ce
sudo modprobe -v rtl8192ce
```
Then show
```
rfkill list
iwconfig
sudo iwlist scan
iwlist chan
route -n
```

---

### Post by henrique8 on 2015-05-01
Guys,

I'm a little bit ashamed right now... I was not able to set the password before, but then I entered in the connection settings and set the password via network manager and it all went fine. I'm truly sorry to make you all waste your time on that issue! Maybe I need to get more confident and try search for the solution on my own a little bit. In that case, it was kind of obvius...

Again, I'm sorry!!

Thank you all!

---

