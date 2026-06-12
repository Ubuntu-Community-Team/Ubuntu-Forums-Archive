---
title: "Realtek Wifi 8180 can't scan or connect manually"
date: 2015-09-02
forum: Networking &amp; Wireless
---

### Post by Vladimir_R on 2015-09-02
Hello,

Did a full upgrade, update, installed ndiswrapper with Windows 98 drivers, removed nm-manager and installed wcid to no avail. Please help.

```

########## wireless info START ##########

Report from: 02 Sep 2015 21:42 CEST +0200

Booted last: 02 Sep 2015 20:37 CEST +0200

Script from: 14 Jul 2015 17:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-62-generic #102-Ubuntu SMP Tue Aug 11 14:28:35 UTC 2015 i686 i686 i686 GNU/Linux

Parameters: ro, forcepae, quiet, splash, vt.handoff=7

##### desktop ###########################

Lubuntu

##### lspci #############################

01:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC [10ec:8180] (rev 20)
    Subsystem: Billionton Systems Inc Device [14cb:0201]
    Kernel driver in use: rtl8180

01:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)
    Subsystem: Packard Bell B.V. Device [1631:c002]
    Kernel driver in use: 8139too

##### lsusb #############################

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8180                35544  0 
mac80211              546118  1 rtl8180
cfg80211              409394  2 mac80211,rtl8180
eeprom_93cx6           13168  1 rtl8180

##### interfaces ########################

auto lo
iface lo inet loopback

iface wlan0 inet dhcp
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid alice_RJCDZQ

auto wlan0

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.12  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29103 errors:0 dropped:1 overruns:0 frame:0
          TX packets:25196 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24290001 (24.2 MB)  TX bytes:2975639 (2.9 MB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.254   0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0

##### resolv.conf #######################

nameserver 212.27.40.241
nameserver 212.27.40.240

##### network managers ##################

Installed:

    Wicd

Running:

    None found.

##### NetworkManager info ###############

NetworkManager is not installed (package "network-manager").

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

[[/etc/NetworkManager/system-connections/Connexion Wi-Fi 1]] (600 root)
[connection] id=Connexion Wi-Fi 1 | type=802-11-wireless
[802-11-wireless] ssid=alice_RJCDZQ
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

'iw' is not installed (package "iw").

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

wlan0     14 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

##### module infos ######################

[rtl8180]
filename:       /lib/modules/3.13.0-62-generic/kernel/drivers/net/wireless/rtl818x/rtl8180/rtl8180.ko
license:        GPL
description:    RTL8180 / RTL8185 PCI wireless driver
author:         Andrea Merello <andrea.merello@gmail.com>
author:         Michael Wu <flamingice@sourmilk.net>
srcversion:     55981B6920CC72BDE7D0933
depends:        mac80211,eeprom_93cx6,cfg80211
intree:         Y
vermagic:       3.13.0-62-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        80:79:21:E4:56:D3:66:42:6F:FD:40:1F:8C:D7:36:72:BA:8D:42:88
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-62-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     8D081A0C2EE28771C5194E1
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-62-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        80:79:21:E4:56:D3:66:42:6F:FD:40:1F:8C:D7:36:72:BA:8D:42:88
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-62-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     695424C2F5CD23A91B67E25
depends:        
intree:         Y
vermagic:       3.13.0-62-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        80:79:21:E4:56:D3:66:42:6F:FD:40:1F:8C:D7:36:72:BA:8D:42:88
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

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

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0x8180 (rtl8180)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   16.223147] intel_rng: don't want to disable this in firmware setup, and if
[   18.752191] rtl8180 0000:01:01.0: enabling device (0116 -> 0117)
[   26.783465] init: network-manager main process (608) terminated with status 127
[   26.783497] init: network-manager main process ended, respawning
[   52.724119] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 4 times)

########## wireless info END ############


```

---

### Post by chili555 on 2015-09-02
> auto lo
iface lo inet loopback

iface wlan0 inet dhcp
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid alice_RJCDZQYikes!!!

You haven't declared the key. I suggest you amend the file to:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-ssid alice_RJCDZQ
wpa-psk <your_secret_key>
```Re-read the file:```
sudo ifdown wlan0 && sudo ifup -v wlan0
```
Test:```
ping -c3 www.ubuntu.com
```

---

### Post by Vladimir_R on 2015-09-03
I have a wpa key inserted, tried manually adding two networks without success. What bugs me most is that wcid or nm-manger before it can't scan and find any network in the area. Have loaded in ndiswrapper Windows XP driver but still doesn't work either.

---

### Post by chili555 on 2015-09-03
May I assume that, as of now, ndiswrapper is not installed and potentially interfering?

Let's have a look at the message log:```
dmesg | grep -e rtl -e 01:01
```Thanks.

---

### Post by Vladimir_R on 2015-09-03
First thank you for helping!

I have reinstalled from scratch Lunbuntu. Reverted to version 14.04 with nonpae (forcepae parameter) processor support because it is a Celeron M. Aside from that I have added nm-applet to the autostart ... again :-)

Nota: I'm missing the connections tab from menu>system tools>network parameters

Everything is stock now so let's see:
```
[    0.096546] pci 0000:01:01.0: [10ec:8180] type 00 class 0x020000
[    0.096566] pci 0000:01:01.0: reg 0x10: [io  0xc100-0xc1ff]
[    0.096578] pci 0000:01:01.0: reg 0x14: [mem 0xe0000100-0xe00001ff]
[    0.096643] pci 0000:01:01.0: supports D1 D2
[    0.096647] pci 0000:01:01.0: PME# supported from D1 D2 D3hot D3cold
[   19.728893] rtl8180 0000:01:01.0: enabling device (0116 -> 0117)
```

---

### Post by chili555 on 2015-09-03
Since you reinstalled, the wireless_info above is no longer valid. May I see:```
iwconfig
rfkill list all
sudo iwlist wlan0 scan
```I see nothing wrong and therefor fixable so far.

---

### Post by Vladimir_R on 2015-09-03
```
audrey@audrey-EasyNote:~$ iwconfig
wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

eth0      no wireless extensions.

audrey@audrey-EasyNote:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

audrey@audrey-EasyNote:~$ sudo iwlist wlan0 scan
wlan0     No scan results


```

---

### Post by chili555 on 2015-09-03
I don't see anything wrong. I suggest you try a live DVD for Ubuntu 15.04. See if the performance improves. If so, of course, install it.

---

### Post by Vladimir_R on 2015-09-03
I would have gladely but I can't man because the laptop is 8 years old and has only 512MB of RAM. Can you walk me through installing ndiswrapper (blaklisting the open source driver etc.)?

---

### Post by chili555 on 2015-09-04
If you got 14.04 to install, I'm quite confident that 15.04 will install, too. You will probably have better luck with a lightweight version such as Lubuntu or Xubuntu.

ndiswrapper requires XP driver files, not 98. Do you have them or can you find them?

---

### Post by Vladimir_R on 2015-09-06
Installed 15.04.04 from scratch.

Found drivers there [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=26&PFid=5&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=26&PFid=5&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true)

There's also a utility program, can we try to make it work through Wine?

---

### Post by Hadaka on 2015-09-06
Hi, the driver you need should be part of the new kernel 15.04 that you loaded.
please copy and paste, then post the output of..
```
modinfo rtl8180 | grep -i 8180
```

and just in case..please do..
```
sudo modprobe rtl8180
```
and see if it wakes up.
thanks.

---

