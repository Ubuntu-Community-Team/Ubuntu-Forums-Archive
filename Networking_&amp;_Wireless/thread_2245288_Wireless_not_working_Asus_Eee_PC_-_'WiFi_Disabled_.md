---
title: "Wireless not working Asus Eee PC - 'WiFi Disabled by hardware switch'"
date: 2014-09-22
forum: Networking &amp; Wireless
---

### Post by RichDavey on 2014-09-22
Hi there,

I've recently installed Ubuntu 14.04 and since this the wireless has stopped working. On the connection drop down list, it says WiFi disabled by hardware switch, however there is no switch on the laptop. These are the wireless script logs generated:
```

########## wireless info START ##########

Report from: 22 Sep 2014 18:25 BST +0100

Booted last: 22 Sep 2014 17:56 BST +0100

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:01 UTC 2014 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: AzureWave AW-NE785 / AW-NE785H 802.11bgn Wireless Full or Half-size Mini PCIe Card [1a3b:1089]
    Kernel driver in use: ath9k

04:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8468]
    Kernel driver in use: atl1c

##### lsusb #############################

Bus 001 Device 002: ID 13d3:5711 IMC Networks 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

eeepc_wmi              12983  0 
asus_wmi               23495  1 eeepc_wmi
sparse_keymap          13708  1 asus_wmi
ath9k                 144602  0 
ath9k_common           13359  1 ath9k
ath9k_hw              438205  2 ath9k_common,ath9k
ath                    23922  3 ath9k_common,ath9k,ath9k_hw
mac80211              546051  1 ath9k
cfg80211              409394  3 ath,ath9k,mac80211
wmi                    18673  1 asus_wmi
video                  18903  2 gma500_gfx,asus_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.12  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::ca60:ff:fe51:10c3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2649 errors:0 dropped:0 overruns:0 frame:0
          TX packets:873 errors:0 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000 
          RX bytes:489238 (489.2 KB)  TX bytes:113338 (113.3 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.12
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
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

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Hotspot]] (600 root)
[connection] id=Hotspot | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=rich-X101CH | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=shared
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

wlan0     Interface doesn't support scanning : Network is down

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

##### module infos ######################

[ath9k]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     DF02272C2FA4678C49046E5
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A2:8D:B5:FD:6E:29:9C:CE:49:47:DA:CA:A6:6F:45:9D:B4:AC:CE:24
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[ath9k_common]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A2:8D:B5:FD:6E:29:9C:CE:49:47:DA:CA:A6:6F:45:9D:B4:AC:CE:24
sig_hashalgo:   sha512

[ath9k_hw]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     4809F3842A0542CD6B556D3
depends:        ath
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A2:8D:B5:FD:6E:29:9C:CE:49:47:DA:CA:A6:6F:45:9D:B4:AC:CE:24
sig_hashalgo:   sha512

[ath]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A2:8D:B5:FD:6E:29:9C:CE:49:47:DA:CA:A6:6F:45:9D:B4:AC:CE:24
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-35-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     D491AB7C521706DA5F4BE7C
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A2:8D:B5:FD:6E:29:9C:CE:49:47:DA:CA:A6:6F:45:9D:B4:AC:CE:24
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-35-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A2:8D:B5:FD:6E:29:9C:CE:49:47:DA:CA:A6:6F:45:9D:B4:AC:CE:24
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 0
ps_enable: 0

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

[/etc/modprobe.d/asus.conf]
options asus_nb_wmi wapf=1

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

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1969:0x2062 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x002b (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   17.906413] ath: phy0: ASPM enabled: 0x42
[   17.906425] ath: EEPROM regdomain: 0x60
[   17.906431] ath: EEPROM indicates we should expect a direct regpair map
[   17.906440] ath: Country alpha2 being used: 00
[   17.906445] ath: Regpair used: 0x60
[   21.236579] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

########## wireless info END ############

```
Any help that you can give would be greatly appreciated as I am a bit of a novice!
Cheers.

PS: WiFI is: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express)

---

### Post by praseodym on 2014-09-22
Please run

```
echo "options asus_nb_wmi wapf=1" | sudo tee /etc/modprobe.d/asus.conf 
```
Reboot and check the buttons.

---

### Post by TheFu on 2014-09-22
Does Fn+F2 not toggle the wifi?

---

### Post by RichDavey on 2014-09-22
HI there,
Thanks for your replies; I tried the code and reboot, but still no joy - it came up with aeroplane mode on and wifi hotspot, but it couldn't connect to anything. Have tried fn+f2, but also no joy unfortunately.

---

### Post by TheFu on 2014-09-22
Really?  Fn-F2 worked on my Eee 1008H with lxde. I don't recall having to do anything extra to make it "just work".  I don't have 14,04 on that box - it was retired for a newer machine last March, so I can't check it easily, but with 10.04 and 12.04, it just worked.

**rfkill unblock** doesn't work either? RTFM to get the options correct. That isn't the entire command.

---

### Post by jeremy31 on 2014-09-22
I wonder if ```
sudo modprobe -rv eeepc_wmi
``````
rfkill unblock all
```
it might work as I didn't see the asus_nb_wmi in the results of the script

---

### Post by ajusco on 2014-09-22
I had a very similar problem with an EEEPC 1000HE, Atheros AR928X controller, now rulling lubuntu 14.04. And it's recurrent across several installs. I had a version of Mint 14 installed and the machine suddenly could not recognize wifi signals. I did a fresh install of Mint 17 Cinnamon KDE and it worked fine but was slow. So I did a fresh install again with lubuntu. Again, it worked great. Until suddenly it didn't (occurred while I was trying to configure a VPN). When I ran it off the live disk, it works fine.

Running rfkill list showed the wlan soft blocked but not hard blocked.

Then running rfkill unblock all changes that, showed it unblocked. Finally went to the network connections, right clicked hit enable wifi and it registered.

---

### Post by RichDavey on 2014-09-23
Thanks for your suggestions - will try them all when I finish work. Also - before I installed I ran from USB which worked fine on wireless, this only occurred after install and Win 7 Starter removal.

---

### Post by varunendra on 2014-09-23
Are you trying to use the wifi in Hotspot mode intentionally? It may not be related to the hardblock, but you won't be able to scan other networks and connect to them while it is in Hotspot mode.

The hotspot mode is supposed to work in conjunction with the cable network. It simply gets the internet from the ethernet cable, and broadcasts it via the wifi card working as a hotspot. If you don't want this, I suggest you remove the hotspot profile. If you can't do it via the GUI (gave a system freeze in a recent case), you can simply remove the file that stores that profile -
```
sudo mv /etc/NetworkManager/system-connections/Hotspot ./
```
The above command will move the hotspot file to your home directory.

---

### Post by RichDavey on 2014-09-23
> **jeremy31 said:**
> I wonder if ```
sudo modprobe -rv eeepc_wmi
``````
rfkill unblock all
```
it might work as I didn't see the asus_nb_wmi in the results of the script
Tried both of these but still no joy: rfkill list all shows this: 
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no

Also noticed in sytem settings that Aeroplane mode was truned on and that it was set up as a wireless hotspot (?) turned these off and tried fn+f2 again and even clicked on the wireless button in settings but nothing happens.

---

### Post by RichDavey on 2014-09-23
> **varunendra said:**
> Are you trying to use the wifi in Hotspot mode intentionally? It may not be related to the hardblock, but you won't be able to scan other networks and connect to them while it is in Hotspot mode.

The hotspot mode is supposed to work in conjunction with the cable network. It simply gets the internet from the ethernet cable, and broadcasts it via the wifi card working as a hotspot. If you don't want this, I suggest you remove the hotspot profile. If you can't do it via the GUI (gave a system freeze in a recent case), you can simply remove the file that stores that profile -
```
sudo mv /etc/NetworkManager/system-connections/Hotspot ./
```
The above command will move the hotspot file to your home directory.
Ran the command and rebooted- still nothing. Click to turn wireless on and it just flashes on/off really quick.

---

### Post by varunendra on 2014-09-23
Please show us a fresh report of the wireless_script, plus the outputs of -
```
lsmod
egrep -i 'phy|switch|wlan|rfkill|wmi|ath' /var/log/syslog
```

Preferably, upload the outputs to [http://pastebin.ubuntu.com/](http://pastebin.ubuntu.com/) , and give us the link to the pastebin upload.

---

### Post by RichDavey on 2014-09-23
Thanks to everyone for all your help so far! 

The results of the reports are [here]("http://pastebin.ubuntu.com/8413549/") and [here]("http://paste.ubuntu.com/8413600/").

The wireless script report is as follows:
```
########## wireless info START ##########

Report from: 23 Sep 2014 22:08 BST +0100

Booted last: 23 Sep 2014 20:25 BST +0100

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:01 UTC 2014 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

GNOME Flashback (Metacity)

##### lspci #############################

02:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: AzureWave AW-NE785 / AW-NE785H 802.11bgn Wireless Full or Half-size Mini PCIe Card [1a3b:1089]
    Kernel driver in use: ath9k

04:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8468]
    Kernel driver in use: atl1c

##### lsusb #############################

Bus 001 Device 002: ID 13d3:5711 IMC Networks 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

##### lsmod #############################

ath9k                 144602  0 
eeepc_wmi              12983  0 
asus_wmi               23495  1 eeepc_wmi
ath9k_common           13359  1 ath9k
sparse_keymap          13708  1 asus_wmi
ath9k_hw              438205  2 ath9k_common,ath9k
ath                    23922  3 ath9k_common,ath9k,ath9k_hw
mac80211              546051  1 ath9k
cfg80211              409394  3 ath,ath9k,mac80211
video                  18903  2 gma500_gfx,asus_wmi
wmi                    18673  1 asus_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::ca60:ff:fe51:10c3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:69731 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61081 errors:0 dropped:0 overruns:0 carrier:9
          collisions:0 txqueuelen:1000 
          RX bytes:50238307 (50.2 MB)  TX bytes:8950731 (8.9 MB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
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

[ifupdown]
managed=false

##### NetworkManager profiles ###########

##### iw reg get ########################

Region: Europe/London (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

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

wlan0     Interface doesn't support scanning : Network is down

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

##### module infos ######################

[ath9k]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     DF02272C2FA4678C49046E5
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A2:8D:B5:FD:6E:29:9C:CE:49:47:DA:CA:A6:6F:45:9D:B4:AC:CE:24
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[ath9k_common]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A2:8D:B5:FD:6E:29:9C:CE:49:47:DA:CA:A6:6F:45:9D:B4:AC:CE:24
sig_hashalgo:   sha512

[ath9k_hw]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     4809F3842A0542CD6B556D3
depends:        ath
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A2:8D:B5:FD:6E:29:9C:CE:49:47:DA:CA:A6:6F:45:9D:B4:AC:CE:24
sig_hashalgo:   sha512

[ath]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A2:8D:B5:FD:6E:29:9C:CE:49:47:DA:CA:A6:6F:45:9D:B4:AC:CE:24
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-35-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     D491AB7C521706DA5F4BE7C
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A2:8D:B5:FD:6E:29:9C:CE:49:47:DA:CA:A6:6F:45:9D:B4:AC:CE:24
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-35-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A2:8D:B5:FD:6E:29:9C:CE:49:47:DA:CA:A6:6F:45:9D:B4:AC:CE:24
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 0
ps_enable: 0

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

[/etc/modprobe.d/asus.conf]
rfkill unblock all


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

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1969:0x2062 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x002b (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   19.093918] ath: phy0: ASPM enabled: 0x42
[   19.093931] ath: EEPROM regdomain: 0x60
[   19.093936] ath: EEPROM indicates we should expect a direct regpair map
[   19.093944] ath: Country alpha2 being used: 00
[   19.093949] ath: Regpair used: 0x60
[   21.533707] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

########## wireless info END ############
```

---

### Post by praseodym on 2014-09-23
Please try
```

sudo modprobe -rfv ath9k
sudo rfkill unblock all
sudo modprobe -v ath9k
```
Check:
```

iwconfig
rfkill list
dmesg | egrep 'radio|kill|switch|wlan|ath|asus'
```

---

### Post by TheFu on 2014-09-23
Looks to me like the wifi will work and isn't because the wired connection is plugged in, so the wired routing takes precedence. Unplug the network cable, enable the wifi, see if that works.

I use wicd-curse to manage wifi connections, but have to disconnect the ethernet cable or the routing gets munged.

---

### Post by varunendra on 2014-09-23
> **TheFu said:**
> Looks to me like the wifi will work and isn't because the wired connection is plugged in, so the wired routing takes precedence. Unplug the network cable, enable the wifi, see if that works.
+1

Not precisely the routing issue (it is possible, but it doesn't 'hard-block' the cards), but some BIOS are programmed to do this automatically as soon as an Ethernet connection is detected.

You might also have to wait for a couple of minutes after unplugging the cable (or even reboot without the cable plugged-in) before the Hard block is gone.

---

### Post by RichDavey on 2014-09-24
> **praseodym said:**
> Please try
```

sudo modprobe -rfv ath9k
sudo rfkill unblock all
sudo modprobe -v ath9k
```
Check:
```

iwconfig
rfkill list
dmesg | egrep 'radio|kill|switch|wlan|ath|asus'
```
iwconfig creates this:
```
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

eth0      no wireless extensions.
```

Output of dmseg is as follows:
```
[    2.292348] Console: switching to colour frame buffer device 100x37
[    2.428602] Loaded X.509 cert 'Magrathea: Glacier signing key: a28db5fd6e299cce4947dacaa66f459db4acce24'
[    3.635612] Console: switching to colour dummy device 80x25
[    4.003141] Console: switching to colour frame buffer device 128x37
[   18.219764] ath: phy0: ASPM enabled: 0x42
[   18.219778] ath: EEPROM regdomain: 0x60
[   18.219783] ath: EEPROM indicates we should expect a direct regpair map
[   18.219791] ath: Country alpha2 being used: 00
[   18.219796] ath: Regpair used: 0x60
[   18.690888] asus_wmi: ASUS WMI generic driver loaded
[   18.722928] asus_wmi: Initialization: 0x0
[   18.723044] asus_wmi: BIOS WMI version: 0.9
[   18.723269] asus_wmi: SFUN value: 0x0
[   18.752080] asus_wmi: Disabling ACPI video driver
[   19.759047] init: failsafe main process (596) killed by TERM signal
[   20.484440] init: cups main process (630) killed by HUP signal
[   20.974304] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

rfkill list shows this: 
```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

The codes before this came up with:
Code 1:
```
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/asus.conf line 2: ignoring bad line starting with 'rfkill'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/asus.conf line 4: ignoring bad line starting with ''
rmmod ath9k
rmmod mac80211
rmmod ath9k_common
rmmod ath9k_hw
rmmod ath
rmmod cfg80211
```
Code 3: ```
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/asus.conf line 2: ignoring bad line starting with 'rfkill'
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/asus.conf line 4: ignoring bad line starting with ''
insmod /lib/modules/3.13.0-35-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.13.0-35-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/ath/ath.ko 
insmod /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko 
insmod /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko 
insmod /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko 
```

Still no change as yet.

---

### Post by varunendra on 2014-09-24
Not a solution yet, but the "rfkill unblock all" command was not supposed to be saved in the 'asus.conf' file, it was supposed to be run in the terminal. Please delete that file as it is useless, only causing distracting errors -
```
sudo rm /etc/modprobe.d/asus.conf
```

And since we have no solid clues yet, I think you should upload your entire syslog file (/var/log/syslog) to pastebin, and give us its link for a more detailed information of whatever is happening in the background. It is recommended to check this file yourself before uploading to make sure it doesn't contain any _sensitive info_ that you don't want to publish on the internet. Although it shouldn't contain any such info unless you have created custom scripts etc. that contain such info in plain text and can be logged by the kernel. Some files that contain such info in plain text and exist in the system by default are omitted (or the sensitive parts are omitted) automatically in syslog.

---

### Post by RichDavey on 2014-09-25
The syslog info is [here]("http://paste.ubuntu.com/8428008/")

Have also removed that asus.conf file. 

Also, have had a few issues where the screen will suddenly go black and the laptop is unresponsive until I press and hold power button to turn off. Don't think its related but should I open another thread or wait until this is resolved?

---

### Post by varunendra on 2014-09-25
> **RichDavey said:**
> Also, have had a few issues where the screen will suddenly go black and the laptop is unresponsive until I press and hold power button to turn off. Don't think its related but should I open another thread or wait until this is resolved?

When that happens, reboot and check the syslog file to see the last few messages when it happened (the messages will have date and timestamp). If the fresh syslog file (/var/log/syslog) doesn't contain the previous session's messages, the "syslog.1" file will have them. If the messages contain references to anything other than networking, you should start a new thread with reference to those error messages. Sounds like a kernel panic, but it can be caused by many things, and usually that shows error messages on the screen before freezing completely. So not sure about it.

Taking a look at the syslog, shall post back if found something worth posting.

---

### Post by varunendra on 2014-09-25
So far, I couldn't notice anything very promising, although this was certainly interesting -
```
Sep 25 21:17:22 rich-X101CH NetworkManager[736]: <info> rfkill0: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/ieee80211/phy0/rfkill0) (driver ath9k)
Sep 25 21:17:22 rich-X101CH NetworkManager[736]: <info> rfkill1: found WiFi radio killswitch (at /sys/devices/platform/eeepc-wmi/rfkill/rfkill1) (platform driver eeepc-wmi)
Sep 25 21:17:22 rich-X101CH NetworkManager[736]: <info> **WiFi disabled by radio killswitch**; enabled by state file
Sep 25 21:17:22 rich-X101CH NetworkManager[736]: <info> WWAN enabled by radio killswitch; enabled by state file
....<snip>....
Sep 25 21:17:25 rich-X101CH NetworkManager[736]: <info> **[COLOR="#006400"]WiFi hardware radio set enabled[/COLOR]**
Sep 25 21:17:26 rich-X101CH dbus[436]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Sep 25 21:17:26 rich-X101CH dbus[436]: [system] Successfully activated service 'org.freedesktop.systemd1'
```

For now, please try this -
```
echo "options eeepc_wmi hotplug_wireless=Y" | sudo tee /etc/modprobe.d/eeepc_wmi.conf
```
Reboot and check -
```
rfkill list
```
If it still appears to be hard-blocked, try the Fn+ toggle switch and let us know if it works now.

---

### Post by RichDavey on 2014-09-26
> **varunendra said:**
> For now, please try this -
```
echo "options eeepc_wmi hotplug_wireless=Y" | sudo tee /etc/modprobe.d/eeepc_wmi.conf
```
Reboot and check -
```
rfkill list
```
If it still appears to be hard-blocked, try the Fn+ toggle switch and let us know if it works now.

Tried this and no joy - but have noticed that when I use fn+f2 (which ued to be the wifi toggle) it just turns aeroplane mode on and off.

---

### Post by praseodym on 2014-09-26
Please check with "lsmod" if the module asus_nb_wmi is loaded at all

---

### Post by RichDavey on 2014-09-26
> **praseodym said:**
> Please check with "lsmod" if the module asus_nb_wmi is loaded at all
Just checked lsmod - there's an 'asus_wmi' but not 'asus_nb_wmi'

---

### Post by praseodym on 2014-09-26
Lets try:
```

sudo modprobe -v asus_nb_wmi
sudo rfill unblock all
rfkill list
dmesg | egrep 'asus|wlan|radio|kill|switch'
```

---

### Post by varunendra on 2014-09-26
> **RichDavey said:**
> Tried this and no joy - but have noticed that when I use fn+f2 (which ued to be the wifi toggle) it just turns aeroplane mode on and off.
And does "rfkill list" still shows the 'phy0' interface as 'hard blocked'?

Considering one of your previous posts -
> **RichDavey said:**
> ....this only occurred after install and **Win 7 Starter removal**.
..and the fact that usual tricks are not working, I wonder if this is yet another "made for windows only" BIOS bug. If so, I'm afraid you *may* have to install windows once again to just enable wifi again. Was it enabled when/AFTER you removed Windows?

I think you should also try, if what is suggested here doesn't help, various boot options related to pci and acpi suggested **[here]("https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options")**, especially "acpi_osi=" (nothing after "=") or "acpi_osi=linux". How to try them in temporary/permanent mode has also been mentioned on the same page (and [here]("http://ubuntuforums.org/showthread.php?t=1613132")).

---

### Post by RichDavey on 2014-09-26
rfkill list does show phy0 as hard blocked and wifi was enabled when I removed win; will try praseodym's coding when i get home and will also try the boot options as suggested. Trouble with installing windows is that the laptop doesn't have a dvd and even if it did i haven't got a copy of windows anyway - Skills! Will post when I've tried these suggestions. Starting to think I may have to buy a usb wifi adaptor!

---

### Post by RichDavey on 2014-09-29
Hi there, have tried the coding suggestions but still nothing changing - have also used the boot options (acpi_osi=, noapic, nolapic). Hasn't made a real difference although I've noticed the black screen freeze occurring slightly more frequently now - is there a way to reset the boot options to default or remove options?

---

### Post by LUyJO on 2014-09-29
I have the 14.04 LTS version on an ASUS EEE pc . After an update today,  wireless stopped working too.
I've tried unsucessfully all previous commands of this topic.

rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no

dmesg | egrep 'asus|wlan|radio|kill|switch'
[    1.130451] Console: switching to colour frame buffer device 100x37
[   16.671553] Console: switching to colour dummy device 80x25
[   17.660586] Console: switching to colour frame buffer device 128x37
[   18.952622] asus_wmi: ASUS WMI generic driver loaded
[   19.044657] asus_wmi: Initialization: 0x0
[   19.044782] asus_wmi: BIOS WMI version: 0.6
[   19.045028] asus_wmi: SFUN value: 0x0
[   19.270191] asus_wmi: BIOS says wireless lan is blocked, but the pci device is present
[   19.270201] asus_wmi: skipped wireless hotplug as probably inappropriate for this model
[   19.270208] asus_wmi: Backlight controlled by ACPI video driver
[   19.344410] systemd-udevd[288]: renamed network interface wlan0 to wlan2
[   20.828336] init: failsafe main process (461) killed by TERM signal
[   24.060441] init: cups main process (620) killed by HUP signal
[   24.512250] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  150.141376] asus_wmi: BIOS says wireless lan is blocked, but the pci device is present
[  150.141391] asus_wmi: skipped wireless hotplug as probably inappropriate for this model
[  150.576986] asus_wmi: BIOS says wireless lan is blocked, but the pci device is present
[  150.576996] asus_wmi: skipped wireless hotplug as probably inappropriate for this model
[  150.937510] asus_wmi: BIOS says wireless lan is blocked, but the pci device is present
[  150.937527] asus_wmi: skipped wireless hotplug as probably inappropriate for this model
[  151.300969] asus_wmi: BIOS says wireless lan is blocked, but the pci device is present
[  151.300979] asus_wmi: skipped wireless hotplug as probably inappropriate for this model
[  151.660969] asus_wmi: BIOS says wireless lan is blocked, but the pci device is present
[  151.660979] asus_wmi: skipped wireless hotplug as probably inappropriate for this model
[  152.021082] asus_wmi: BIOS says wireless lan is blocked, but the pci device is present
[  152.021092] asus_wmi: skipped wireless hotplug as probably inappropriate for this model
[  152.373383] asus_wmi: BIOS says wireless lan is blocked, but the pci device is present
[  152.373398] asus_wmi: skipped wireless hotplug as probably inappropriate for this model
[  152.729361] asus_wmi: BIOS says wireless lan is blocked, but the pci device is present
[  152.729378] asus_wmi: skipped wireless hotplug as probably inappropriate for this model
[  153.097334] asus_wmi: BIOS says wireless lan is blocked, but the pci device is present
[  153.097349] asus_wmi: skipped wireless hotplug as probably inappropriate for this model
[  153.124950] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  153.461379] asus_wmi: BIOS says wireless lan is blocked, but the pci device is present
[  153.461395] asus_wmi: skipped wireless hotplug as probably inappropriate for this model
[  153.593778] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  153.825707] asus_wmi: BIOS says wireless lan is blocked, but the pci device is present
[  153.825719] asus_wmi: skipped wireless hotplug as probably inappropriate for this model
[  154.185291] asus_wmi: BIOS says wireless lan is blocked, but the pci device is present
[  154.185306] asus_wmi: skipped wireless hotplug as probably inappropriate for this model
[  154.242133] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  154.573301] asus_wmi: BIOS says wireless lan is blocked, but the pci device is present
[  154.573317] asus_wmi: skipped wireless hotplug as probably inappropriate for this model
[  154.937039] asus_wmi: BIOS says wireless lan is blocked, but the pci device is present
[  154.937051] asus_wmi: skipped wireless hotplug as probably inappropriate for this model
[  155.316873] asus_wmi: BIOS says wireless lan is blocked, but the pci device is present
[  155.316883] asus_wmi: skipped wireless hotplug as probably inappropriate for this model
[  155.369228] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  155.693344] asus_wmi: BIOS says wireless lan is blocked, but the pci device is present
[  155.693360] asus_wmi: skipped wireless hotplug as probably inappropriate for this model
[  155.804390] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  156.073104] asus_wmi: BIOS says wireless lan is blocked, but the pci device is present
[  156.073116] asus_wmi: skipped wireless hotplug as probably inappropriate for this model
[  156.449296] asus_wmi: BIOS says wireless lan is blocked, but the pci device is present
[  156.449311] asus_wmi: skipped wireless hotplug as probably inappropriate for this model
[  156.510927] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  156.821330] asus_wmi: BIOS says wireless lan is blocked, but the pci device is present
[  156.821345] asus_wmi: skipped wireless hotplug as probably inappropriate for this model
[  156.939446] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  157.205020] asus_wmi: BIOS says wireless lan is blocked, but the pci device is present
[  157.205028] asus_wmi: skipped wireless hotplug as probably inappropriate for this model
[  157.573282] asus_wmi: BIOS says wireless lan is blocked, but the pci device is present
[  157.573297] asus_wmi: skipped wireless hotplug as probably inappropriate for this model
[  157.630209] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  157.937365] asus_wmi: BIOS says wireless lan is blocked, but the pci device is present
[  157.937380] asus_wmi: skipped wireless hotplug as probably inappropriate for this model
[  158.060659] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  158.317155] asus_wmi: BIOS says wireless lan is blocked, but the pci device is present
[  158.317166] asus_wmi: skipped wireless hotplug as probably inappropriate for this model
[  158.692880] asus_wmi: BIOS says wireless lan is blocked, but the pci device is present
[  158.692889] asus_wmi: skipped wireless hotplug as probably inappropriate for this model
[  158.754165] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  159.065301] asus_wmi: BIOS says wireless lan is blocked, but the pci device is present
[  159.065317] asus_wmi: skipped wireless hotplug as probably inappropriate for this model
[  159.188667] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  159.449904] asus_wmi: BIOS says wireless lan is blocked, but the pci device is present
[  159.449915] asus_wmi: skipped wireless hotplug as probably inappropriate for this model
[  159.821396] asus_wmi: BIOS says wireless lan is blocked, but the pci device is present
[  159.821411] asus_wmi: skipped wireless hotplug as probably inappropriate for this model
[  159.879226] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  160.209369] asus_wmi: BIOS says wireless lan is blocked, but the pci device is present
[  160.209384] asus_wmi: skipped wireless hotplug as probably inappropriate for this model
[  160.348826] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  160.478024] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  160.596729] asus_wmi: BIOS says wireless lan is blocked, but the pci device is present
[  160.596739] asus_wmi: skipped wireless hotplug as probably inappropriate for this model
[  161.153039] asus_wmi: BIOS says wireless lan is blocked, but the pci device is present
[  161.153048] asus_wmi: skipped wireless hotplug as probably inappropriate for this model
[  161.228717] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  161.848917] asus_wmi: BIOS says wireless lan is blocked, but the pci device is present
[  161.848928] asus_wmi: skipped wireless hotplug as probably inappropriate for this model
[  161.910633] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready

---

### Post by LUyJO on 2014-09-29
**lsmod**
Module                  Size  Used by
rfcomm                 53664  0 
bnep                   18895  2 
bluetooth             342208  10 bnep,rfcomm
eeepc_wmi              12983  0 
asus_wmi               23495  1 eeepc_wmi
sparse_keymap          13708  1 asus_wmi
uvcvideo               71309  0 
snd_hda_codec_realtek    55163  1 
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_memops       13170  1 videobuf2_vmalloc
snd_hda_intel          42730  3 
videobuf2_core         39258  1 uvcvideo
arc4                   12536  2 
videodev              108503  2 uvcvideo,videobuf2_core
snd_hda_codec         164067  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
ath9k                 144602  0 
ath9k_common           13359  1 ath9k
snd_rawmidi            25135  1 snd_seq_midi
ath9k_hw              438205  2 ath9k_common,ath9k
joydev                 17101  0 
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
ath                    23922  3 ath9k_common,ath9k,ath9k_hw
serio_raw              13230  0 
coretemp               13195  0 
mac80211              546051  1 ath9k
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
lpc_ich                16864  0 
snd_timer              28584  2 snd_pcm,snd_seq
cfg80211              409394  3 ath,ath9k,mac80211
snd                    60939  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12600  1 snd
i915                  705659  3 
drm_kms_helper         47182  1 i915
drm                   244037  4 i915,drm_kms_helper
mac_hid                13037  0 
i2c_algo_bit           13197  1 i915
video                  18903  2 i915,asus_wmi
parport_pc             31981  0 
wmi                    18673  1 asus_wmi
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
ahci                   25579  2 
psmouse                91329  0 
libahci                27214  1 ahci
atl1c                  40949  0

---

### Post by LUyJO on 2014-09-29
Meanwhile I executed 
echo "options asus_nb_wmi wapf=1" | sudo tee /etc/modprobe.d/asus.conf
And could enable wireless now.
I'll reboot and see what happens

---

### Post by LUyJO on 2014-09-29
Yeah! It's OK now!

   **rfkill list **

 0: phy0: Wireless LAN 
 	Soft blocked: no 
 	Hard blocked: no 
 1: asus-wlan: Wireless LAN 
 	Soft blocked: no 
 	Hard blocked: no

---

### Post by G3u5 on 2014-09-30
Hi there people... I am experiencing the same deal. It appeared to be working some months ago, but now no connection whatsoever... I advised on getting this Asus Wireless PCE-N15 to a friend who has this old beat up puppu minitower desktop thing goin on.... headaches. please advize on way forwar! Throw PC out the window? I might kill someone ;-)

---

### Post by RichDavey on 2014-10-01
> **LUyJO said:**
> Meanwhile I executed 
echo "options asus_nb_wmi wapf=1" | sudo tee /etc/modprobe.d/asus.conf
And could enable wireless now.
I'll reboot and see what happens

Tried this and wireless still disabled. Is there anything else I could try?

---

### Post by varunendra on 2014-10-01
> **RichDavey said:**
> is there a way to reset the boot options to default or remove options?
Assuming you made them permanent by adding the options to "/etc/default/grub" file, simply remove the additional options. If you did it using 'Boot-Repair' program, it does the same thing - adds the options to the said file, and updates grub. Basically, check your kernel boot line first to make sure there are indeed additional options -
```
cat /proc/cmdline
```
If you see the acpi or pci related options, check the /etc/default/grub file -
```
cat /etc/default/grub
```
The line "GRUB_CMDLINE_LINUX_DEFAULT" should only have "quiet" and "splash" by default. It should look like -
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
If you see additional options there, simply delete them using your GUI text editor (opened with root privilege), or use this command -
```
sudo sed -i 's/GRUB_CMDLINE_LINUX_DEFAULT=.*/GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"/' /etc/default/grub
```
To make the change effective, run 'update-grub' -
```
sudo update-grub
```
This should all be pretty easy if you use Boot-Repair by the way.

> **G3u5 said:**
> Hi there people... I am experiencing the same deal. It appeared to be working some months ago, but now no connection whatsoever... I advised on getting this Asus Wireless PCE-N15 to a friend who has this old beat up puppu minitower desktop thing goin on....
Welcome to the forums G3u5,
Regardless of how similar the symptoms may appear, wireless troubles are mostly very subjective - means the reasons and solutions may differ from person to person. Please start your own thread in this very section, give it a descriptive title, and post back the details of the problem along with the [wireless_script]("http://ubuntuforums.org/showpost.php?p=13024222") report in it.

> **RichDavey said:**
> Tried this and wireless still disabled. Is there anything else I could try?
The "asus_nb_wmi" driver is not used at all in eeepc. What ***LUyJO*** experienced must have been a coincidence. His dmesg part suggested that the wireless adapter was probably turned off within the BIOS, maybe they tried resetting the BIOS. In any case, experimenting with 'asus_nb_wmi' with an Asus EeePC is not going to help, since they don't use this module at all.

---

### Post by RichDavey on 2014-10-02
Hi all,
After much hair pulling and frustration, the wifi is finally fixed! This was probably a rookie mistake - but I got to the BIOS menu and looked at the on board components and saw wlan was disabled - enabled it and working fine! I'm a bit of a novce with this sort of thing so apologies as this could've been fixed ages ago without much fuss. Thank you for all your help though.

---

### Post by varunendra on 2014-10-02
At least we can have a good laugh now. :p

Please mark the thread as [SOLVED] using "Thread Tools" link above the top post.

---

