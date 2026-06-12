---
title: "Atheros AR242x / AR542x: ath5k: failed to wakeup the MAC Chip, Ubuntu 14.04.1 LTS"
date: 2014-09-30
forum: Networking &amp; Wireless
---

### Post by stager2 on 2014-09-30
Wireless works oly some second after login
```


    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

stager-Satellite-L40 3.13.0-36-generic i686,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Celeron(R) M CPU        520  @ 1.60GHz
Memory : 993 MB
Uptime : 14:05:06 up 4 min,  2 users,  load average: 3,01, 1,91, 0,78


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Askey Computer Corp. WLL3141 (Toshiba PA3613U-1MPC) 802.11bg Wireless Mini PCIe Card [144f:7128]
    Kernel driver in use: ath5k
--
05:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)
    Subsystem: Toshiba America Info Systems Device [1179:ff40]
    Kernel driver in use: 8139too


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255


iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

ath5k                 134977  0 
ath                    23922  1 ath5k
mac80211              546051  1 ath5k
cfg80211              409394  3 ath,ath5k,mac80211


module parameters ~~~~~~~~~~~~~~~~~~

ath5k         (3): e=&#1045;.0 | e=&#1045; | fastchanswitch=N | nohwcrypt=N | no_hw_rfkill_switch=N
cfg80211      (2): e=&#1045;.0 | e=&#1045; | cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): e=&#1045;.0 | e=&#1045; | beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: disconnected
================o=============o=========o==============o=========o===========o==============o===========
 Interface & ID | Type        | Driver  | State        | Default | Speed     | Support      | HW Addr   
================o=============o=========o==============o=========o===========o==============o===========
 eth0           | Wired       | 8139too | unavailable  | no      |           |              | <MAC eth0>
----------------+-------------+---------+--------------+---------+-----------+--------------+-----------
 wlan0          | 802.11 WiFi | ath5k   | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    ASUSrt:          Infra, <MAC C-NA ASUSrt 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 60 WPA
    bubaeee_Wi-Fi:   Infra, <MAC C-NA bubaeee_Wi-Fi 1>, Freq 2452 MHz, Rate 54 Mb/s, Strength 54 WPA2
    default:         Infra, <MAC C-NA default 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    pro100mayki:     Infra, <MAC C-NA pro100mayki 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    Hip-Hop:         Infra, <MAC C-NA Hip-Hop 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    home16:          Infra, <MAC C-NA home16 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 12 WPA2
----------------+-------------+---------+--------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=true


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

AndroidAP            : ssid=AndroidAP | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
StagerHome           : ssid=StagerHome | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
&#1052;&#1086;&#1103; &#1055;&#1088;&#1088;&#1077;&#1083;&#1077;&#1089;&#1090;&#1100;~ : ssid=208;156;208;190;209;143;32;208;159;209;128;209;128;208;181;208;187;208;181;209;129;209;130;209;140;126; | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~



Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

&#1058;&#1072;&#1073;&#1083;&#1080;&#1094;&#1072; &#1084;&#1072;&#1088;&#1096;&#1091;&#1090;&#1080;&#1079;&#1072;&#1094;&#1080;&#1080; &#1103;&#1076;&#1088;&#1072; &#1087;&#1088;&#1086;&#1090;&#1086;&#1082;&#1086;&#1083;&#1072; IP
Destination Gateway Genmask Flags Metric Ref Use Iface


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : ru_RU.UTF-8)
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     No scan results


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[ath5k]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
srcversion:     F36818A2F0BCB2B0CC9BB8C
depends:        mac80211,cfg80211,ath
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)

[ath]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-36-generic/kernel/net/mac80211/mac80211.ko
srcversion:     B822641624778B987844F6F
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-36-generic/kernel/net/wireless/cfg80211.ko
srcversion:     C2478077E22138832B71659
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1e.0/0000:05:07.0 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0 (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# USB device 0x:0x (dm9601)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth1>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# USB device 0x:0x (dm9601)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth2>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Not Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modules]
loop

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
                    options iwlwifi 11n_disable=1
iwlwifi.conf~     : options iwlwifi 11n_disable=1
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-36-generic root=UUID=1d0f8417-f52d-42bc-9ea0-bb1b1514c9a8 ro splash quiet


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.699003] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.699453] audit: initializing netlink socket (disabled)
[    1.481588] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.551355] 8139too: 8139too Fast Ethernet driver 0.9.28
[   22.205932] ath5k 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[   22.206072] ath5k 0000:02:00.0: registered as 'phy0'
[   23.154114] ath: EEPROM regdomain: 0x65
[   23.154119] ath: EEPROM indicates we should expect a direct regpair map
[   23.154123] ath: Country alpha2 being used: 00
[   23.154125] ath: Regpair used: 0x65
[   23.272697] ath5k: phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[  120.349430] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  123.801065] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  123.801785] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  126.297509] wlan0: authenticate with <MAC ID removed>
[  126.307442] wlan0: send auth to <MAC ID removed> (try 1/3)
[  126.308599] wlan0: authenticated
[  126.310774] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  126.310782] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  126.312213] wlan0: associate with <MAC ID removed> (try 1/3)
[  126.320379] wlan0: RX AssocResp from <MAC ID removed> (capab=0x431 status=0 aid=1)
[  126.320622] wlan0: associated
[  126.320656] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  126.477705] wlan0: deauthenticating from <MAC ID removed> by local choice (reason=2)
[  126.479571] wlan0: authenticate with <MAC ID removed>
[  126.479790] wlan0: send auth to <MAC ID removed> (try 1/3)
[  126.481002] wlan0: authenticated
[  126.482808] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  126.482815] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  126.484081] wlan0: associate with <MAC ID removed> (try 1/3)
[  126.491739] wlan0: RX AssocResp from <MAC ID removed> (capab=0x431 status=0 aid=1)
[  126.491977] wlan0: associated
[  148.939524] ath5k: phy0: failed to wakeup the MAC Chip
[  148.939533] ath5k: phy0: can't reset hardware (-5)
[  149.059935] ath5k: phy0: failed to wakeup the MAC Chip
[  149.059942] ath5k: phy0: can't reset hardware (-5)
[  149.180343] ath5k: phy0: failed to wakeup the MAC Chip
[  149.180351] ath5k: phy0: can't reset hardware (-5)
[  149.305774] ath5k: phy0: failed to wakeup the MAC Chip
[  149.305783] ath5k: phy0: can't reset hardware (-5)
[  149.428499] ath5k: phy0: failed to wakeup the MAC Chip
[  149.428507] ath5k: phy0: can't reset hardware (-5)
[  150.396733] wlan0: authenticate with <MAC ID removed>
[  150.611184] wlan0: send auth to <MAC ID removed> (try 1/3)
[  151.820039] wlan0: send auth to <MAC ID removed> (try 2/3)
[  152.820077] wlan0: send auth to <MAC ID removed> (try 3/3)
[  153.820035] wlan0: authentication with <MAC ID removed> timed out
[  154.442866] net_ratelimit: 16 callbacks suppressed
[  154.442874] ath5k: phy0: failed to wakeup the MAC Chip
[  154.442878] ath5k: phy0: can't reset hardware (-5)
[  154.563090] ath5k: phy0: failed to wakeup the MAC Chip
[  154.563097] ath5k: phy0: can't reset hardware (-5)
[  154.684856] ath5k: phy0: failed to wakeup the MAC Chip
[  154.684864] ath5k: phy0: can't reset hardware (-5)
[  154.805308] ath5k: phy0: failed to wakeup the MAC Chip
[  154.805315] ath5k: phy0: can't reset hardware (-5)
[  154.926256] ath5k: phy0: failed to wakeup the MAC Chip
[  154.926263] ath5k: phy0: can't reset hardware (-5)
[  161.034452] net_ratelimit: 16 callbacks suppressed
[  161.034460] ath5k: phy0: failed to wakeup the MAC Chip
[  161.034465] ath5k: phy0: can't reset hardware (-5)
[  161.157144] ath5k: phy0: failed to wakeup the MAC Chip
[  161.157154] ath5k: phy0: can't reset hardware (-5)
[  161.280119] ath5k: phy0: failed to wakeup the MAC Chip
[  161.280127] ath5k: phy0: can't reset hardware (-5)
[  161.407626] ath5k: phy0: failed to wakeup the MAC Chip
[  161.407635] ath5k: phy0: can't reset hardware (-5)
[  161.595116] ath5k: phy0: failed to wakeup the MAC Chip
[  161.595125] ath5k: phy0: can't reset hardware (-5)
[  166.737807] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  166.948304] net_ratelimit: 16 callbacks suppressed
[  166.948312] ath5k: phy0: failed to wakeup the MAC Chip
[  166.948317] ath5k: phy0: can't reset hardware (-5)
[  167.074015] ath5k: phy0: failed to wakeup the MAC Chip
[  167.074024] ath5k: phy0: can't reset hardware (-5)
[  167.194070] ath5k: phy0: failed to wakeup the MAC Chip
[  167.194079] ath5k: phy0: can't reset hardware (-5)
[  167.317315] ath5k: phy0: failed to wakeup the MAC Chip
[  167.317323] ath5k: phy0: can't reset hardware (-5)
[  167.445827] ath5k: phy0: failed to wakeup the MAC Chip
[  167.445836] ath5k: phy0: can't reset hardware (-5)
[  193.128889] net_ratelimit: 42 callbacks suppressed
[  193.128897] ath5k: phy0: failed to wakeup the MAC Chip
[  193.128901] ath5k: phy0: can't reset hardware (-5)
[  193.250916] ath5k: phy0: failed to wakeup the MAC Chip
[  193.250924] ath5k: phy0: can't reset hardware (-5)
[  193.372316] ath5k: phy0: failed to wakeup the MAC Chip
[  193.372326] ath5k: phy0: can't reset hardware (-5)
[  193.492514] ath5k: phy0: failed to wakeup the MAC Chip
[  193.492522] ath5k: phy0: can't reset hardware (-5)
[  193.613815] ath5k: phy0: failed to wakeup the MAC Chip
[  193.613823] ath5k: phy0: can't reset hardware (-5)
[  226.130647] net_ratelimit: 16 callbacks suppressed
[  226.130654] ath5k: phy0: failed to wakeup the MAC Chip
[  226.130658] ath5k: phy0: can't reset hardware (-5)
[  226.252325] ath5k: phy0: failed to wakeup the MAC Chip
[  226.252333] ath5k: phy0: can't reset hardware (-5)
[  226.375480] ath5k: phy0: failed to wakeup the MAC Chip
[  226.375488] ath5k: phy0: can't reset hardware (-5)
[  226.497199] ath5k: phy0: failed to wakeup the MAC Chip
[  226.497205] ath5k: phy0: can't reset hardware (-5)
[  226.620850] ath5k: phy0: failed to wakeup the MAC Chip
[  226.620859] ath5k: phy0: can't reset hardware (-5)
[  249.314575] net_ratelimit: 16 callbacks suppressed
[  249.314583] ath5k: phy0: failed to wakeup the MAC Chip
[  249.314587] ath5k: phy0: can't reset hardware (-5)
[  249.464868] ath5k: phy0: failed to wakeup the MAC Chip
[  249.464877] ath5k: phy0: can't reset hardware (-5)
[  249.586796] ath5k: phy0: failed to wakeup the MAC Chip
[  249.586804] ath5k: phy0: can't reset hardware (-5)
[  249.707109] ath5k: phy0: failed to wakeup the MAC Chip
[  249.707116] ath5k: phy0: can't reset hardware (-5)
[  249.830768] ath5k: phy0: failed to wakeup the MAC Chip
[  249.830776] ath5k: phy0: can't reset hardware (-5)

    ======== Done ========

```

---

### Post by varunendra on 2014-10-01
Welcome to the forums stager2!

Looks like an old bug resurrected : [https://bugs.launchpad.net/bugs/432353](https://bugs.launchpad.net/bugs/432353)

Please add yourself to the "Affects Me" list of the above bug and add your comments confirming its 'still exists' status.

In the meanwhile, please try -
```
echo "options ath5k nohwcrypt=Y" | sudo tee /etc/modprobe.d/ath5k.conf
```
..followed by a reboot. Does this help?

---

### Post by stager2 on 2014-10-02
> **varunendra said:**
> 

Looks like an old bug resurrected : [https://bugs.launchpad.net/bugs/432353](https://bugs.launchpad.net/bugs/432353)

Please add yourself to the "Affects Me" list of the above bug and add your comments confirming its 'still exists' status.

Ok.
> **varunendra said:**
> 
In the meanwhile, please try -
```
echo "options ath5k nohwcrypt=Y" | sudo tee /etc/modprobe.d/ath5k.conf
```
..followed by a reboot. Does this help?
No, of course. It is a old recipe :-)

---

### Post by varunendra on 2014-10-02
Just a pointer - the developers or debugging guys at launchpad probably won't like the script report. I guess they would prefer full logs without the additional filters and formatting that we do in the script for our convenience here.

I think one of the proper ways to get the relevant logs to attach there is running 'apport-bug' command, but you may have to specify a specific package or PID with it in some cases. A comprehensive guide on filing bug reports effectively : [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Anyway, can you boot into an older kernel and check if the wifi is working okay there? You may have to press 'Shift' key ('Esc' on some systems) during the boot-time splash screen to get the grub menu if it doesn't show up by default. There you can see if there are older kernels available to boot into.

Or, you may choose to try a newer, backported driver to see if it works better. But if you have older kernels installed (or if you can try a Live DVD/USB of 12.04 containing an older kernel), it would be a good way to confirm whether this issue is limited to the current kernel or not.

---

### Post by stager2 on 2014-10-03
This problem is present in all kernels in Ubuntu 14.04
This was not in Ubuntu 13.10

---

### Post by varunendra on 2014-10-03
And how does it behave with a backported driver? Method to install :

With the wired connection, please install the basic packages first -
```
sudo apt-get install linux-headers-generic build-essential
```
Then -

**1)** Download the "backports-3.16.2-1" package from here : [http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/](http://drvbp1.linux-foundation.org/~mcgrof/rel-html/backports/)

**2)** Right-click the downloaded package > click "Extract here". This will extract the contents into a directory of same name.

**3)** Open a terminal (Ctrl-Alt-T), and assuming the above extracted directory is in the "**Downloads**" directory in your Home, run the following commands to compile and install the driver -
```
cd Downloads/backports-3.16.2-1
make defconfig-ath5k
make
sudo make install
```
Watch out for errors and report back if there are any, although there shouldn't be.

Reboot after the installation is successfully finished, and let us know whether it works or not.

Alternatively, you may choose to install a whole new kernel, assuming the problem could be with the kernel instead of the driver, although it is highly unlikely.

---

### Post by d.a.eliseev on 2014-10-04
Thanks! It's good for me

---

### Post by varunendra on 2014-10-04
> **d.a.eliseev said:**
> Thanks! It's good for me

What is? The nohwcrypt parameter or the backported driver? Did you have the same problem that one of these fixed?

Welcome to the forums by the way. :)

---

### Post by stager2 on 2014-10-04
> **varunendra said:**
> And how does it behave with a backported driver?
No effect :-(

---

### Post by varunendra on 2014-10-04
Let's have a look at current report of the wireless script.

---

### Post by stager2 on 2014-10-04
> **varunendra said:**
> Let's have a look at current report of the wireless script.

```


    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

stager-Satellite-L40 3.13.0-36-generic i686,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Celeron(R) M CPU        520  @ 1.60GHz
Memory : 993 MB
Uptime : 01:46:59 up  4:56,  2 users,  load average: 0,71, 0,45, 0,35


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Askey Computer Corp. WLL3141 (Toshiba PA3613U-1MPC) 802.11bg Wireless Mini PCIe Card [144f:7128]
    Kernel driver in use: ath5k
--
05:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)
    Subsystem: Toshiba America Info Systems Device [1179:ff40]
    Kernel driver in use: 8139too


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255


iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

ath5k                 134808  0 
ath                    24182  1 ath5k
mac80211              486135  1 ath5k
cfg80211              430577  3 ath,ath5k,mac80211
compat                 13617  3 cfg80211,ath5k,mac80211


module parameters ~~~~~~~~~~~~~~~~~~

ath5k         (3): e=&#1045;.0 | e=&#1045; | fastchanswitch=N | nohwcrypt=Y | no_hw_rfkill_switch=N
cfg80211      (2): e=&#1045;.0 | e=&#1045; | cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
compat        (3): e=&#1045;.0 | e=&#1045;
mac80211      (5): e=&#1045;.0 | e=&#1045; | beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: disconnected
================o=============o=========o==============o=========o===========o==============o===========
 Interface & ID | Type        | Driver  | State        | Default | Speed     | Support      | HW Addr   
================o=============o=========o==============o=========o===========o==============o===========
 eth0           | Wired       | 8139too | unavailable  | no      | 100 Mb/s  |              | <MAC eth0>
----------------+-------------+---------+--------------+---------+-----------+--------------+-----------
 wlan0          | 802.11 WiFi | ath5k   | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>
----------------+-------------+---------+--------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=true


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

AndroidAP            : ssid=AndroidAP | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
StagerHome           : ssid=StagerHome | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
&#1052;&#1086;&#1103; &#1055;&#1088;&#1088;&#1077;&#1083;&#1077;&#1089;&#1090;&#1100;~ : ssid=208;156;208;190;209;143;32;208;159;209;128;209;128;208;181;208;187;208;181;209;129;209;130;209;140;126; | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~



Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

&#1058;&#1072;&#1073;&#1083;&#1080;&#1094;&#1072; &#1084;&#1072;&#1088;&#1096;&#1091;&#1090;&#1080;&#1079;&#1072;&#1094;&#1080;&#1080; &#1103;&#1076;&#1088;&#1072; &#1087;&#1088;&#1086;&#1090;&#1086;&#1082;&#1086;&#1083;&#1072; IP
Destination Gateway Genmask Flags Metric Ref Use Iface


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : ru_RU.UTF-8)
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     No scan results


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[ath5k]
filename:       /lib/modules/3.13.0-36-generic/updates/drivers/net/wireless/ath/ath5k/ath5k.ko
version:        backported from Linux (v3.16.2-0-g62de88e) using backports v3.16.2-1-0-g9d017dd
srcversion:     E66ED980090C8A7ACB06086
depends:        mac80211,compat,cfg80211,ath
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)

[ath]
filename:       /lib/modules/3.13.0-36-generic/updates/drivers/net/wireless/ath/ath.ko
srcversion:     C9BEC05AD7C1101B3411B15
depends:        cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-36-generic/updates/net/mac80211/mac80211.ko
version:        backported from Linux (v3.16.2-0-g62de88e) using backports v3.16.2-1-0-g9d017dd
srcversion:     498475E7EA38A1D570E3DDA
depends:        cfg80211,compat
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-36-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (v3.16.2-0-g62de88e) using backports v3.16.2-1-0-g9d017dd
srcversion:     45258D27D2689FBA5E42894
depends:        compat
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[compat]
filename:       /lib/modules/3.13.0-36-generic/updates/compat/compat.ko
version:        backported from Linux (v3.16.2-0-g62de88e) using backports v3.16.2-1-0-g9d017dd
srcversion:     13E4000F1322A602EC4401E
depends:        
parm:           backported_kernel_name:The kernel tree name that was used for this backport (Linux) (charp)
parm:           backported_kernel_version:The kernel version that was used for this backport (v3.16.2-0-g62de88e) (charp)
parm:           backports_version:The git version of the backports tree used to generate this backport (v3.16.2-1-0-g9d017dd) (charp)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1e.0/0000:05:07.0 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0 (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# USB device 0x:0x (dm9601)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth1>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# USB device 0x:0x (dm9601)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth2>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Not Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modules]
loop

[/etc/modprobe.d]
ath5k.conf        : options ath5k nohwcrypt=Y
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
                    options iwlwifi 11n_disable=1
iwlwifi.conf~     : options iwlwifi 11n_disable=1
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-36-generic root=UUID=1d0f8417-f52d-42bc-9ea0-bb1b1514c9a8 ro splash quiet


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
I'm adding log from start:
Oct  4 15:29:30 stager-Satellite-L40 avahi-daemon[527]: Network interface enumeration completed.
Oct  4 15:29:30 stager-Satellite-L40 avahi-daemon[527]: Registering HINFO record with values 'I686'/'LINUX'.
Oct  4 15:29:30 stager-Satellite-L40 avahi-daemon[527]: Server startup complete. Host name is stager-Satellite-L40.local. Local service cookie is 1945092735.
Oct  4 15:29:30 stager-Satellite-L40 avahi-daemon[527]: Service "stager-Satellite-L40" (/services/udisks.service) successfully established.
Oct  4 15:29:30 stager-Satellite-L40 kernel: [   28.050803] cfg80211: World regulatory domain updated:
Oct  4 15:29:30 stager-Satellite-L40 kernel: [   28.050810] cfg80211:  DFS Master region: unset
Oct  4 15:29:30 stager-Satellite-L40 kernel: [   28.050813] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Oct  4 15:29:30 stager-Satellite-L40 kernel: [   28.050817] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Oct  4 15:29:30 stager-Satellite-L40 kernel: [   28.050821] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Oct  4 15:29:30 stager-Satellite-L40 kernel: [   28.050824] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
Oct  4 15:29:30 stager-Satellite-L40 kernel: [   28.050827] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Oct  4 15:29:30 stager-Satellite-L40 kernel: [   28.050831] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Oct  4 15:29:30 stager-Satellite-L40 kernel: [   28.327472] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af:
Oct  4 15:29:30 stager-Satellite-L40 kernel: [   28.328824]  excluding 0x170-0x177 0x1f0-0x1f7 0x250-0x25f 0x370-0x377
Oct  4 15:29:30 stager-Satellite-L40 kernel: [   28.329688] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff:
Oct  4 15:29:30 stager-Satellite-L40 kernel: [   28.329990]  excluding 0x3f0-0x3f7 0x400-0x41f 0x480-0x4bf 0x4d0-0x4d7
Oct  4 15:29:30 stager-Satellite-L40 kernel: [   28.330267] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff:
Oct  4 15:29:30 stager-Satellite-L40 kernel: [   28.330513]  excluding 0x820-0x87f
Oct  4 15:29:30 stager-Satellite-L40 kernel: [   28.330746] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7:
Oct  4 15:29:30 stager-Satellite-L40 kernel: [   28.331512]  clean.
Oct  4 15:29:30 stager-Satellite-L40 kernel: [   28.331536] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff:
Oct  4 15:29:30 stager-Satellite-L40 kernel: [   28.331541]  excluding 0xc0000-0xc7fff 0xcc000-0xcffff 0xe0000-0xfffff
Oct  4 15:29:30 stager-Satellite-L40 kernel: [   28.331575] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff:
Oct  4 15:29:30 stager-Satellite-L40 kernel: [   28.331596]  clean.
Oct  4 15:29:30 stager-Satellite-L40 kernel: [   28.331616] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff:
Oct  4 15:29:30 stager-Satellite-L40 kernel: [   28.331636]  clean.
Oct  4 15:29:30 stager-Satellite-L40 kernel: [   28.331655] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff:
Oct  4 15:29:30 stager-Satellite-L40 kernel: [   28.341496]  clean.
Oct  4 15:29:30 stager-Satellite-L40 kernel: [   28.359707] ath: EEPROM regdomain: 0x65
Oct  4 15:29:30 stager-Satellite-L40 kernel: [   28.359712] ath: EEPROM indicates we should expect a direct regpair map
Oct  4 15:29:30 stager-Satellite-L40 kernel: [   28.359716] ath: Country alpha2 being used: 00
Oct  4 15:29:30 stager-Satellite-L40 kernel: [   28.359718] ath: Regpair used: 0x65
Oct  4 15:29:30 stager-Satellite-L40 kernel: [   28.404460] init: cups main process (499) killed by HUP signal
Oct  4 15:29:30 stager-Satellite-L40 kernel: [   28.404483] init: cups main process ended, respawning
Oct  4 15:29:30 stager-Satellite-L40 kernel: [   28.405514] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
Oct  4 15:29:30 stager-Satellite-L40 kernel: [   28.406128] ath5k: phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
Oct  4 15:29:31 stager-Satellite-L40 kernel: [   28.784713] init: failsafe main process (546) killed by TERM signal
Oct  4 15:29:31 stager-Satellite-L40 kernel: [   29.386717] init: Failed to obtain startpar-bridge instance: Unknown parameter: INSTANCE
Oct  4 15:29:31 stager-Satellite-L40 statd-pre-start: virtual-filesystems started
Oct  4 15:29:31 stager-Satellite-L40 sm-notify[692]: Version 1.2.8 starting
Oct  4 15:29:32 stager-Satellite-L40 rpc.statd[697]: Version 1.2.8 starting
Oct  4 15:29:32 stager-Satellite-L40 rpc.statd[697]: Flags: TI-RPC 
Oct  4 15:29:33 stager-Satellite-L40 ModemManager[651]: <info>  ModemManager (version 1.0.0) starting...
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]: <info> NetworkManager (version 0.9.8.8) is starting...
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]: <info> WEXT support is enabled
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]: <info> VPN: loaded org.freedesktop.NetworkManager.vpnc
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]: <info> DNS: loaded plugin dnsmasq
Oct  4 15:29:34 stager-Satellite-L40 dbus[373]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Oct  4 15:29:34 stager-Satellite-L40 polkitd[727]: started daemon version 0.105 using authority implementation `local' version `0.105'
Oct  4 15:29:34 stager-Satellite-L40 dbus[373]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]:    SCPlugin-Ifupdown: init!
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]:    SCPlugin-Ifupdown: update_system_hostname
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]:       interface-parser: parsing file /etc/network/interfaces
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]:       interface-parser: finished parsing file /etc/network/interfaces
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]:    SCPluginIfupdown: management mode: managed
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0, iface: wlan0)
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:05:07.0/net/eth0, iface: eth0)
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:05:07.0/net/eth0, iface: eth0): no ifupdown configuration found.
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]:    SCPlugin-Ifupdown: end _init.
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]:    SCPlugin-Ofono: Acquired D-Bus service com.canonical.NMOfono
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]:    SCPlugin-Ofono: init!
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]:    SCPlugin-Ofono: end _init.
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]: <info> Loaded plugin (null): (null)
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]:    SCPlugin-Ifupdown: (158986592) ... get_connections.
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]:    SCPlugin-Ifupdown: (158986592) connections count: 0
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]:    keyfile: parsing StagerHome ... 
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]:    keyfile:     read connection 'StagerHome'
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]:    keyfile: parsing AndroidAP ... 
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]:    keyfile:     read connection 'AndroidAP'
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]:    keyfile: parsing VPN-&#1089;&#1086;&#1077;&#1076;&#1080;&#1085;&#1077;&#1085;&#1080;&#1077; 1 ... 
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]:    keyfile:     read connection 'VPN-&#1089;&#1086;&#1077;&#1076;&#1080;&#1085;&#1077;&#1085;&#1080;&#1077; 1'
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]:    SCPlugin-Ofono: (158858384) ... get_connections.
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]:    SCPlugin-Ofono: (158858384) connections count: 0
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]: <info> monitoring kernel firmware directory '/lib/firmware'.
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]: <info> rfkill0: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/ieee80211/phy0/rfkill0) (driver ath5k)
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]: <info> WiFi enabled by radio killswitch; enabled by state file
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]: <info> WWAN enabled by radio killswitch; enabled by state file
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]: <info> WiMAX enabled by radio killswitch; enabled by state file
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]: <info> Networking is enabled by state file
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]: <info> (wlan0): using nl80211 for WiFi device control
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]: <info> (wlan0): driver supports Access Point (AP) mode
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]: <info> (wlan0): new 802.11 WiFi device (driver: 'ath5k' ifindex: 3)
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]: <info> (wlan0): bringing up device.
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]: <info> (wlan0): preparing device.
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]: <info> (wlan0): deactivating device (reason 'managed') [2]
Oct  4 15:29:34 stager-Satellite-L40 dbus[373]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Oct  4 15:29:34 stager-Satellite-L40 kernel: [   32.460797] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct  4 15:29:34 stager-Satellite-L40 kernel: [   32.461425] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]: <warn> failed to allocate link cache: (-12) Object not found
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]: <info> (eth0): carrier is OFF
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]: <info> (eth0): new Ethernet device (driver: '8139too' ifindex: 2)
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]: <info> (eth0): bringing up device.
Oct  4 15:29:34 stager-Satellite-L40 kernel: [   32.471585] 8139too 0000:05:07.0 eth0: link down
Oct  4 15:29:34 stager-Satellite-L40 kernel: [   32.471709] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]: <info> (eth0): preparing device.
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]: <info> (eth0): deactivating device (reason 'managed') [2]
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]: <info> Added default wired connection '&#1055;&#1088;&#1086;&#1074;&#1086;&#1076;&#1085;&#1086;&#1077; &#1089;&#1086;&#1077;&#1076;&#1080;&#1085;&#1077;&#1085;&#1080;&#1077; 1' for /sys/devices/pci0000:00/0000:00:1e.0/0000:05:07.0/net/eth0
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Oct  4 15:29:34 stager-Satellite-L40 kernel: [   32.472508] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]: <info> urfkill disappeared from the bus
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]: <info> ModemManager available in the bus
Oct  4 15:29:34 stager-Satellite-L40 dbus[373]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]: <info> wpa_supplicant started
Oct  4 15:29:34 stager-Satellite-L40 wpa_supplicant[735]: Successfully initialized wpa_supplicant
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]: <info> (wlan0) supports 4 scan SSIDs
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]: <warn> Trying to remove a non-existant call id.
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]: <info> (wlan0): supplicant interface state: starting -> ready
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]: <info> (wlan0): supplicant interface state: ready -> disconnected
Oct  4 15:29:34 stager-Satellite-L40 NetworkManager[718]: <info> (wlan0) supports 4 scan SSIDs
Oct  4 15:29:34 stager-Satellite-L40 wpa_supplicant[736]: wlan0: CTRL-EVENT-SCAN-STARTED 
Oct  4 15:29:35 stager-Satellite-L40 NetworkManager[718]: <info> Auto-activating connection 'StagerHome'.
Oct  4 15:29:35 stager-Satellite-L40 NetworkManager[718]: <info> Activation (wlan0) starting connection 'StagerHome'
Oct  4 15:29:35 stager-Satellite-L40 NetworkManager[718]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Oct  4 15:29:35 stager-Satellite-L40 NetworkManager[718]: <info> NetworkManager state is now CONNECTING
Oct  4 15:29:35 stager-Satellite-L40 NetworkManager[718]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Oct  4 15:29:35 stager-Satellite-L40 NetworkManager[718]: <info> (wlan0): supplicant interface state: disconnected -> inactive
Oct  4 15:29:35 stager-Satellite-L40 NetworkManager[718]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Oct  4 15:29:35 stager-Satellite-L40 NetworkManager[718]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Oct  4 15:29:35 stager-Satellite-L40 NetworkManager[718]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Oct  4 15:29:35 stager-Satellite-L40 NetworkManager[718]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Oct  4 15:29:35 stager-Satellite-L40 NetworkManager[718]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Oct  4 15:29:35 stager-Satellite-L40 NetworkManager[718]: <info> Activation (wlan0/wireless): connection 'StagerHome' has security, and secrets exist.  No new secrets needed.
Oct  4 15:29:35 stager-Satellite-L40 NetworkManager[718]: <info> Config: added 'ssid' value 'StagerHome'
Oct  4 15:29:35 stager-Satellite-L40 NetworkManager[718]: <info> Config: added 'scan_ssid' value '1'
Oct  4 15:29:35 stager-Satellite-L40 NetworkManager[718]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Oct  4 15:29:35 stager-Satellite-L40 NetworkManager[718]: <info> Config: added 'auth_alg' value 'OPEN'
Oct  4 15:29:35 stager-Satellite-L40 NetworkManager[718]: <info> Config: added 'psk' value '<omitted>'
Oct  4 15:29:35 stager-Satellite-L40 NetworkManager[718]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Oct  4 15:29:35 stager-Satellite-L40 NetworkManager[718]: <info> Config: set interface ap_scan to 1
Oct  4 15:29:36 stager-Satellite-L40 ModemManager[651]: <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0': not supported by any plugin
Oct  4 15:29:36 stager-Satellite-L40 ModemManager[651]: <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:1e.0/0000:05:07.0': not supported by any plugin
Oct  4 15:29:35 stager-Satellite-L40 wpa_supplicant[736]: wlan0: CTRL-EVENT-SCAN-STARTED 
Oct  4 15:29:36 stager-Satellite-L40 wpa_supplicant[736]: wlan0: SME: Trying to authenticate with 00:21:91:0b:c1:5b (SSID='StagerHome' freq=2472 MHz)
Oct  4 15:29:36 stager-Satellite-L40 kernel: [   34.261403] wlan0: authenticate with 00:21:91:0b:c1:5b
Oct  4 15:29:36 stager-Satellite-L40 NetworkManager[718]: <info> (wlan0): supplicant interface state: inactive -> authenticating
Oct  4 15:29:36 stager-Satellite-L40 kernel: [   34.269360] wlan0: send auth to 00:21:91:0b:c1:5b (try 1/3)
Oct  4 15:29:36 stager-Satellite-L40 wpa_supplicant[736]: wlan0: Trying to associate with 00:21:91:0b:c1:5b (SSID='StagerHome' freq=2472 MHz)
Oct  4 15:29:36 stager-Satellite-L40 kernel: [   34.272897] wlan0: authenticated
Oct  4 15:29:36 stager-Satellite-L40 kernel: [   34.274622] ath5k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
Oct  4 15:29:36 stager-Satellite-L40 kernel: [   34.274629] ath5k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
Oct  4 15:29:36 stager-Satellite-L40 kernel: [   34.276187] wlan0: associate with 00:21:91:0b:c1:5b (try 1/3)
Oct  4 15:29:36 stager-Satellite-L40 NetworkManager[718]: <info> (wlan0): supplicant interface state: authenticating -> associating
Oct  4 15:29:36 stager-Satellite-L40 wpa_supplicant[736]: wlan0: Associated with 00:21:91:0b:c1:5b
Oct  4 15:29:36 stager-Satellite-L40 kernel: [   34.284400] wlan0: RX AssocResp from 00:21:91:0b:c1:5b (capab=0x431 status=0 aid=6)
Oct  4 15:29:36 stager-Satellite-L40 kernel: [   34.284504] wlan0: associated
Oct  4 15:29:36 stager-Satellite-L40 kernel: [   34.284516] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Oct  4 15:29:36 stager-Satellite-L40 NetworkManager[718]: <info> (wlan0): supplicant interface state: associating -> 4-way handshake
Oct  4 15:29:36 stager-Satellite-L40 wpa_supplicant[736]: wlan0: WPA: Key negotiation completed with 00:21:91:0b:c1:5b [PTK=CCMP GTK=CCMP]
Oct  4 15:29:36 stager-Satellite-L40 wpa_supplicant[736]: wlan0: CTRL-EVENT-CONNECTED - Connection to 00:21:91:0b:c1:5b completed [id=0 id_str=]
Oct  4 15:29:36 stager-Satellite-L40 NetworkManager[718]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Oct  4 15:29:36 stager-Satellite-L40 NetworkManager[718]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'StagerHome'.
Oct  4 15:29:36 stager-Satellite-L40 NetworkManager[718]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Oct  4 15:29:36 stager-Satellite-L40 NetworkManager[718]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Oct  4 15:29:36 stager-Satellite-L40 NetworkManager[718]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Oct  4 15:29:36 stager-Satellite-L40 NetworkManager[718]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct  4 15:29:36 stager-Satellite-L40 NetworkManager[718]: <info> dhclient started with pid 768
Oct  4 15:29:36 stager-Satellite-L40 NetworkManager[718]: <info> Activation (wlan0) Beginning IP6 addrconf.
Oct  4 15:29:36 stager-Satellite-L40 NetworkManager[718]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Oct  4 15:29:36 stager-Satellite-L40 dhclient: Internet Systems Consortium DHCP Client 4.2.4
Oct  4 15:29:36 stager-Satellite-L40 dhclient: Copyright 2004-2012 Internet Systems Consortium.
Oct  4 15:29:36 stager-Satellite-L40 dhclient: All rights reserved.
Oct  4 15:29:36 stager-Satellite-L40 dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct  4 15:29:36 stager-Satellite-L40 dhclient: 
Oct  4 15:29:36 stager-Satellite-L40 NetworkManager[718]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Oct  4 15:29:36 stager-Satellite-L40 dhclient: Listening on LPF/wlan0/00:1b:9e:49:54:22
Oct  4 15:29:36 stager-Satellite-L40 dhclient: Sending on   LPF/wlan0/00:1b:9e:49:54:22
Oct  4 15:29:36 stager-Satellite-L40 dhclient: Sending on   Socket/fallback
Oct  4 15:29:36 stager-Satellite-L40 dhclient: DHCPREQUEST of 192.168.10.106 on wlan0 to 255.255.255.255 port 67 (xid=0x38bb9d5e)
Oct  4 15:29:36 stager-Satellite-L40 kernel: [   34.517746] init: samba-ad-dc main process (739) terminated with status 1
Oct  4 15:29:36 stager-Satellite-L40 dhclient: DHCPNAK from 192.168.10.1 (xid=0x38bb9d5e)
Oct  4 15:29:36 stager-Satellite-L40 NetworkManager[718]: <info> (wlan0): DHCPv4 state changed preinit -> expire
Oct  4 15:29:36 stager-Satellite-L40 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 (xid=0x793e7df)
Oct  4 15:29:36 stager-Satellite-L40 NetworkManager[718]: <info> (wlan0): DHCPv4 state changed expire -> preinit
Oct  4 15:29:36 stager-Satellite-L40 dhclient: DHCPREQUEST of 192.168.10.106 on wlan0 to 255.255.255.255 port 67 (xid=0x793e7df)
Oct  4 15:29:36 stager-Satellite-L40 dhclient: DHCPOFFER of 192.168.10.106 from 192.168.10.6
Oct  4 15:29:36 stager-Satellite-L40 dhclient: DHCPACK of 192.168.10.106 from 192.168.10.6
Oct  4 15:29:36 stager-Satellite-L40 NetworkManager[718]: <info> (wlan0): DHCPv4 state changed preinit -> bound
Oct  4 15:29:36 stager-Satellite-L40 NetworkManager[718]: <info>   address 192.168.10.106
Oct  4 15:29:36 stager-Satellite-L40 NetworkManager[718]: <info>   prefix 24 (255.255.255.0)
Oct  4 15:29:36 stager-Satellite-L40 NetworkManager[718]: <info>   gateway 192.168.10.1
Oct  4 15:29:36 stager-Satellite-L40 NetworkManager[718]: <info>   nameserver '192.168.10.1'
Oct  4 15:29:36 stager-Satellite-L40 NetworkManager[718]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Oct  4 15:29:36 stager-Satellite-L40 NetworkManager[718]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Oct  4 15:29:36 stager-Satellite-L40 avahi-daemon[527]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.10.106.
Oct  4 15:29:36 stager-Satellite-L40 avahi-daemon[527]: New relevant interface wlan0.IPv4 for mDNS.
Oct  4 15:29:36 stager-Satellite-L40 avahi-daemon[527]: Registering new address record for 192.168.10.106 on wlan0.IPv4.
Oct  4 15:29:36 stager-Satellite-L40 dhclient: bound to 192.168.10.106 -- renewal in 84754 seconds.
Oct  4 15:29:37 stager-Satellite-L40 ntpdate[830]: Can't find host ntp.ubuntu.com: Name or service not known (-2)
Oct  4 15:29:37 stager-Satellite-L40 ntpdate[830]: no servers can be used, exiting
Oct  4 15:29:37 stager-Satellite-L40 NetworkManager[718]: <info> (wlan0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Oct  4 15:29:37 stager-Satellite-L40 NetworkManager[718]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Oct  4 15:29:37 stager-Satellite-L40 NetworkManager[718]: <info> (wlan0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Oct  4 15:29:38 stager-Satellite-L40 NetworkManager[718]: <info> NetworkManager state is now CONNECTED_GLOBAL
Oct  4 15:29:38 stager-Satellite-L40 NetworkManager[718]: <info> Policy set 'StagerHome' (wlan0) as default for IPv4 routing and DNS.
Oct  4 15:29:38 stager-Satellite-L40 NetworkManager[718]: <info> DNS: starting dnsmasq...
Oct  4 15:29:38 stager-Satellite-L40 NetworkManager[718]: <warn> dnsmasq not available on the bus, can't update servers.
Oct  4 15:29:38 stager-Satellite-L40 NetworkManager[718]: <error> [1412422178.150272] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Oct  4 15:29:38 stager-Satellite-L40 NetworkManager[718]: <warn> DNS: plugin dnsmasq update failed
Oct  4 15:29:38 stager-Satellite-L40 NetworkManager[718]: <info> Writing DNS information to /sbin/resolvconf
Oct  4 15:29:38 stager-Satellite-L40 avahi-daemon[527]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::21b:9eff:fe49:5422.
Oct  4 15:29:38 stager-Satellite-L40 avahi-daemon[527]: New relevant interface wlan0.IPv6 for mDNS.
Oct  4 15:29:38 stager-Satellite-L40 avahi-daemon[527]: Registering new address record for fe80::21b:9eff:fe49:5422 on wlan0.*.
Oct  4 15:29:38 stager-Satellite-L40 dnsmasq[836]: started, version 2.68 cache disabled
Oct  4 15:29:38 stager-Satellite-L40 dnsmasq[836]: compile time options: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack ipset auth
Oct  4 15:29:38 stager-Satellite-L40 dnsmasq[836]: DBus support enabled: connected to system bus
Oct  4 15:29:38 stager-Satellite-L40 dnsmasq[836]: warning: no upstream servers configured
Oct  4 15:29:39 stager-Satellite-L40 NetworkManager[718]: <info> Activation (wlan0) successful, device activated.
Oct  4 15:29:39 stager-Satellite-L40 dbus[373]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Oct  4 15:29:39 stager-Satellite-L40 NetworkManager[718]: <warn> dnsmasq appeared on DBus: :1.13
Oct  4 15:29:39 stager-Satellite-L40 NetworkManager[718]: <info> Writing DNS information to /sbin/resolvconf
Oct  4 15:29:39 stager-Satellite-L40 dnsmasq[836]: setting upstream servers from DBus
Oct  4 15:29:39 stager-Satellite-L40 dnsmasq[836]: using nameserver 192.168.10.1#53
Oct  4 15:29:39 stager-Satellite-L40 dbus[373]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Oct  4 15:29:40 stager-Satellite-L40 anacron[1104]: Anacron 2.3 started on 2014-10-04
Oct  4 15:29:40 stager-Satellite-L40 acpid: starting up with netlink and the input layer
Oct  4 15:29:40 stager-Satellite-L40 cron[1037]: (CRON) INFO (pidfile fd = 3)
Oct  4 15:29:40 stager-Satellite-L40 /usr/sbin/irqbalance: Balancing is ineffective on systems with a single cache domain.  Shutting down
Oct  4 15:29:40 stager-Satellite-L40 cron[1123]: (CRON) STARTUP (fork ok)
Oct  4 15:29:40 stager-Satellite-L40 cron[1123]: (CRON) INFO (Running @reboot jobs)
Oct  4 15:29:40 stager-Satellite-L40 anacron[1104]: Normal exit (0 jobs run)
Oct  4 15:29:41 stager-Satellite-L40 whoopsie[1088]: whoopsie 0.2.24.6 starting up.
Oct  4 15:29:41 stager-Satellite-L40 whoopsie[1088]: Using lock path: /var/lock/whoopsie/lock
Oct  4 15:29:41 stager-Satellite-L40 whoopsie[1151]: online
Oct  4 15:29:41 stager-Satellite-L40 acpid: 9 rules loaded
Oct  4 15:29:41 stager-Satellite-L40 acpid: waiting for events: event logging is off
Oct  4 15:29:45 stager-Satellite-L40 NetworkManager[718]: <info> WiFi hardware radio set enabled
Oct  4 15:29:45 stager-Satellite-L40 dbus[373]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Oct  4 15:29:46 stager-Satellite-L40 accounts-daemon[1368]: started daemon version 0.6.35
Oct  4 15:29:46 stager-Satellite-L40 dbus[373]: [system] Successfully activated service 'org.freedesktop.Accounts'
Oct  4 15:29:46 stager-Satellite-L40 ntpdate[961]: adjust time server 91.189.94.4 offset 0.392165 sec
Oct  4 15:29:46 stager-Satellite-L40 acpid: client connected from 1365[0:0]
Oct  4 15:29:46 stager-Satellite-L40 acpid: 1 client rule loaded
Oct  4 15:29:46 stager-Satellite-L40 kernel: [   44.479546] init: plymouth-upstart-bridge main process ended, respawning
Oct  4 15:29:46 stager-Satellite-L40 kernel: [   44.517237] init: plymouth-upstart-bridge main process ended, respawning
Oct  4 15:29:50 stager-Satellite-L40 dbus[373]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Oct  4 15:29:50 stager-Satellite-L40 dbus[373]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Oct  4 15:29:50 stager-Satellite-L40 dbus[373]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Oct  4 15:29:50 stager-Satellite-L40 rtkit-daemon[1571]: Successfully called chroot.
Oct  4 15:29:50 stager-Satellite-L40 rtkit-daemon[1571]: Successfully dropped privileges.
Oct  4 15:29:50 stager-Satellite-L40 rtkit-daemon[1571]: Successfully limited resources.
Oct  4 15:29:50 stager-Satellite-L40 rtkit-daemon[1571]: Running.
Oct  4 15:29:50 stager-Satellite-L40 rtkit-daemon[1571]: Successfully made thread 1569 of process 1569 (n/a) owned by '110' high priority at nice level -11.
Oct  4 15:29:50 stager-Satellite-L40 rtkit-daemon[1571]: Watchdog thread running.
Oct  4 15:29:50 stager-Satellite-L40 rtkit-daemon[1571]: Supervising 1 threads of 1 processes of 1 users.
Oct  4 15:29:50 stager-Satellite-L40 rtkit-daemon[1571]: Canary thread running.
Oct  4 15:29:51 stager-Satellite-L40 dbus[373]: [system] Successfully activated service 'org.freedesktop.UPower'
Oct  4 15:29:51 stager-Satellite-L40 rtkit-daemon[1571]: Successfully made thread 1597 of process 1569 (n/a) owned by '110' RT at priority 5.
Oct  4 15:29:51 stager-Satellite-L40 rtkit-daemon[1571]: Supervising 2 threads of 1 processes of 1 users.
Oct  4 15:29:51 stager-Satellite-L40 rtkit-daemon[1571]: Successfully made thread 1599 of process 1569 (n/a) owned by '110' RT at priority 5.
Oct  4 15:29:51 stager-Satellite-L40 rtkit-daemon[1571]: Supervising 3 threads of 1 processes of 1 users.
Oct  4 15:29:51 stager-Satellite-L40 rtkit-daemon[1571]: Successfully made thread 1607 of process 1607 (n/a) owned by '110' high priority at nice level -11.
Oct  4 15:29:51 stager-Satellite-L40 rtkit-daemon[1571]: Supervising 4 threads of 2 processes of 1 users.
Oct  4 15:29:51 stager-Satellite-L40 pulseaudio[1607]: [pulseaudio] pid.c: Daemon already running.
Oct  4 15:29:51 stager-Satellite-L40 dbus[373]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Oct  4 15:29:51 stager-Satellite-L40 dbus[373]: [system] Successfully activated service 'org.freedesktop.systemd1'
Oct  4 15:29:52 stager-Satellite-L40 anacron[1684]: Anacron 2.3 started on 2014-10-04
Oct  4 15:29:52 stager-Satellite-L40 anacron[1684]: Normal exit (0 jobs run)
Oct  4 15:29:52 stager-Satellite-L40 dbus[373]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
Oct  4 15:29:52 stager-Satellite-L40 colord: Using config file /etc/colord.conf
Oct  4 15:29:52 stager-Satellite-L40 colord: Using mapping database file /var/lib/colord/mapping.db
Oct  4 15:29:52 stager-Satellite-L40 colord: Using device database file /var/lib/colord/storage.db
Oct  4 15:29:52 stager-Satellite-L40 colord: loaded plugin libcd_plugin_scanner.so
Oct  4 15:29:52 stager-Satellite-L40 colord: plugin /usr/lib/i386-linux-gnu/colord-plugins/libcd_plugin_sane.so not loaded: plugin refused to load
Oct  4 15:29:52 stager-Satellite-L40 colord: loaded plugin libcd_plugin_camera.so
Oct  4 15:29:52 stager-Satellite-L40 colord: Daemon ready for requests
Oct  4 15:29:52 stager-Satellite-L40 dbus[373]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Oct  4 15:29:52 stager-Satellite-L40 colord: Profile added: icc-14c5ddbb0abd000deb198c68bb185dc3
Oct  4 15:29:52 stager-Satellite-L40 colord: Profile added: icc-02dddef23fc9bc71b96f945d3ebead72
Oct  4 15:29:53 stager-Satellite-L40 colord: Profile added: icc-32428f7e3612a76f4428f54306449131
Oct  4 15:29:53 stager-Satellite-L40 colord: Profile added: icc-e729b445abc89051fe8ba7c6d8e9b127
Oct  4 15:29:53 stager-Satellite-L40 colord: Profile added: icc-9c6d34a5ada445f6146d98b0510c126d
Oct  4 15:29:53 stager-Satellite-L40 colord: Profile added: icc-45dabde250dbbc2b4ab1ddaab1380892
Oct  4 15:29:53 stager-Satellite-L40 colord: Profile added: icc-d9873cac720cb96c7c9b60bf38e9cb84
Oct  4 15:29:53 stager-Satellite-L40 colord: Profile added: icc-29f83ddeaff255ae7842fae4ca83390d
Oct  4 15:29:53 stager-Satellite-L40 colord: Profile added: icc-aaafa3414484eb7d6a63b27b9d77223c
Oct  4 15:29:53 stager-Satellite-L40 colord: Profile added: icc-db4e323398cbf65b3dbe8e218b341544
Oct  4 15:29:53 stager-Satellite-L40 colord: Profile added: icc-fcfc111014da77bf28e1a62012edcfdb
Oct  4 15:29:53 stager-Satellite-L40 colord: Profile added: icc-f3e0aad931efae878c9eba9125dc758f
Oct  4 15:29:53 stager-Satellite-L40 colord: Profile added: icc-71190e50549b40fd8fd2c1b6d407f0a9
Oct  4 15:29:53 stager-Satellite-L40 colord: Profile added: icc-bca21a6afa3a4b5cef9ca8e91565c1b7
Oct  4 15:29:53 stager-Satellite-L40 colord: Profile added: icc-39af39921ee5bd26bdf97e0154014d75
Oct  4 15:29:53 stager-Satellite-L40 colord: Profile added: icc-fa354010a03bb6e606d2fe88447a5669
Oct  4 15:29:53 stager-Satellite-L40 colord: Profile added: icc-34562abf994ccd066d2c5721d0d68c5d
Oct  4 15:29:53 stager-Satellite-L40 colord: Profile added: icc-40e2a2d10e23e2777853990e7c80dbd6
Oct  4 15:29:53 stager-Satellite-L40 colord: Profile added: icc-0bf2ede138b0272421b629b6c8c4deaf
Oct  4 15:29:53 stager-Satellite-L40 colord: Profile added: icc-1d3fda2edb4a89ab60a23c5f7c7d81dd
Oct  4 15:29:53 stager-Satellite-L40 colord: Profile added: icc-a392a74919c54455cf25f7400b2319ac
Oct  4 15:29:53 stager-Satellite-L40 colord: Profile added: icc-1a00a956a836388ae20968e84f57d211
Oct  4 15:29:53 stager-Satellite-L40 colord: Profile added: icc-c62d711cf39488a1fc60e8be18a9d6d7
Oct  4 15:29:53 stager-Satellite-L40 colord: Profile added: icc-998fbb5d3614ac87e52abf701c11462f
Oct  4 15:29:53 stager-Satellite-L40 colord: Profile added: icc-186b88621ed8da652865e3e84836f85b
Oct  4 15:29:53 stager-Satellite-L40 colord: Profile added: icc-c95bd637e95d8a3b0df38f99c1320389
Oct  4 15:29:53 stager-Satellite-L40 colord: Profile added: icc-2c98a16695257d5213906e0402c0eac9
Oct  4 15:29:53 stager-Satellite-L40 colord: Profile added: icc-d7a4f55b86a346c2cbf8cc2ee6b460d9
Oct  4 15:29:53 stager-Satellite-L40 colord: Profile added: icc-22186d7b3e188b46f7a396d5f0246ad8
Oct  4 15:29:53 stager-Satellite-L40 colord: Profile added: icc-e798cc1d9f659a6155ac35ad9ac383bb
Oct  4 15:29:53 stager-Satellite-L40 colord: Profile added: icc-7e1795c2bf10a86a6ad9b20f7f0db073
Oct  4 15:29:53 stager-Satellite-L40 colord: Profile added: icc-35db7968bf0904e9317ca9780d871bc3
Oct  4 15:29:53 stager-Satellite-L40 colord: Profile added: icc-c90203802db7875c010cf0875c3ecac1
Oct  4 15:29:53 stager-Satellite-L40 colord: Profile added: icc-d38c63ceac57b372f0c2c393a746a678
Oct  4 15:29:53 stager-Satellite-L40 colord: Profile added: icc-07000710072007300740075007600770
Oct  4 15:29:53 stager-Satellite-L40 colord: Profile added: icc-4328644330f86626b573ec9807b4706d
Oct  4 15:29:53 stager-Satellite-L40 colord: Profile added: icc-7fb30d688bf82d32a0e748daf3dba95d
Oct  4 15:29:54 stager-Satellite-L40 colord: Profile added: icc-416cdeed9a79d7bbf6e72df8fb849c03
Oct  4 15:29:54 stager-Satellite-L40 colord: Profile added: icc-296f10aadb0eba217aa824dc712c8a07
Oct  4 15:29:54 stager-Satellite-L40 colord: Profile added: icc-035006ce074f99ef4a3bdc9f7bd78677
Oct  4 15:29:54 stager-Satellite-L40 colord: Profile added: icc-a71f743c68b0bf74d37a601835ca05cf
Oct  4 15:29:54 stager-Satellite-L40 colord: Profile added: icc-b0ddeb99aea00b3e6527017fe5b73803
Oct  4 15:29:54 stager-Satellite-L40 colord: Profile added: icc-2ee6b6114ddeed0d4f61e0211c23427b
Oct  4 15:29:54 stager-Satellite-L40 colord: Profile added: icc-c3e6382fa9b2d31b01b736f6f97aac3a
Oct  4 15:29:54 stager-Satellite-L40 colord: Profile added: icc-288a6f2c3bb54a1d2a29221c9caf5011
Oct  4 15:29:54 stager-Satellite-L40 colord: Profile added: icc-56cc29b73a685afb027a630b6d5057dc
Oct  4 15:29:54 stager-Satellite-L40 colord: Profile added: icc-523e494bc2f53c53d51d0758b07f4879
Oct  4 15:29:54 stager-Satellite-L40 colord: Profile added: icc-6a245ab2d8892e2e56232af93cd48b81
Oct  4 15:29:54 stager-Satellite-L40 colord: Profile added: icc-3c54e22f77a8f6175941c3f39f1029f9
Oct  4 15:29:54 stager-Satellite-L40 colord: Profile added: icc-0383c34650771ce95ef93fe916867725
Oct  4 15:29:54 stager-Satellite-L40 colord: Profile added: icc-fb41735d46e9e2c5b7dfa641160c3393
Oct  4 15:29:54 stager-Satellite-L40 colord: Profile added: icc-654b99c87e67edb1c1cfb0dcb7fa9d04
Oct  4 15:29:54 stager-Satellite-L40 colord: Profile added: icc-a10be98be58460669fcdc6946939b7cf
Oct  4 15:29:54 stager-Satellite-L40 colord: Profile added: icc-fd79463e1808f0d8ea7a8f7eefd3256b
Oct  4 15:29:54 stager-Satellite-L40 colord: Profile added: icc-8b73141bce6d164037dd46000bafb2a2
Oct  4 15:29:54 stager-Satellite-L40 colord: Profile added: icc-72f5b1cba915b68ea75cc843e270df5a
Oct  4 15:29:54 stager-Satellite-L40 colord: Profile added: icc-3a34aa6c3d1fb1ef63ff41e04ee00979
Oct  4 15:29:54 stager-Satellite-L40 colord: Profile added: icc-b2016991d9b9c2cf940a251d1441c7fc
Oct  4 15:29:54 stager-Satellite-L40 colord: Profile added: icc-6ad6d63767ce0393245528ada92f1cb2
Oct  4 15:29:54 stager-Satellite-L40 colord: Profile added: icc-b0701c2ccf059287d0b067464df8bda9
Oct  4 15:29:54 stager-Satellite-L40 colord: Profile added: icc-c227f46f246694ba9971f270cb61a0c1
Oct  4 15:29:54 stager-Satellite-L40 colord: Profile added: icc-353a6bcabda00f04b6988f89126ce6f5
Oct  4 15:29:54 stager-Satellite-L40 colord: Profile added: icc-94ec9a8cbcf45963ef9bfbe80b33e02f
Oct  4 15:29:54 stager-Satellite-L40 colord: Profile added: icc-ccebee4c2d6eddc597c1425ac2f128b1
Oct  4 15:29:54 stager-Satellite-L40 colord: Profile added: icc-50e7bd95c5a7d850b2051ad93a63906d
Oct  4 15:29:54 stager-Satellite-L40 colord: Profile added: icc-82f5d16fcef1fbd987b6a82c94104464
Oct  4 15:29:54 stager-Satellite-L40 colord: Profile added: icc-459092a016bf36cb991d22e0731f564c
Oct  4 15:29:54 stager-Satellite-L40 colord: Profile added: icc-7d49c9fa009b69e181b1930fc94bb396
Oct  4 15:29:54 stager-Satellite-L40 colord: Device added: xrandr-LG Philips
Oct  4 15:29:54 stager-Satellite-L40 colord: Automatic metadata add icc-20bc5361b737e564beca41994ab9b341 to xrandr-LG Philips
Oct  4 15:29:54 stager-Satellite-L40 colord: Profile added: icc-20bc5361b737e564beca41994ab9b341
Oct  4 15:29:55 stager-Satellite-L40 colord: device removed: xrandr-LG Philips
Oct  4 15:29:55 stager-Satellite-L40 colord: Profile removed: icc-20bc5361b737e564beca41994ab9b341
Oct  4 15:29:57 stager-Satellite-L40 NetworkManager[718]: <info> (wlan0): IP6 addrconf timed out or failed.
Oct  4 15:29:57 stager-Satellite-L40 NetworkManager[718]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Oct  4 15:29:57 stager-Satellite-L40 NetworkManager[718]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Oct  4 15:29:57 stager-Satellite-L40 NetworkManager[718]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Oct  4 15:29:58 stager-Satellite-L40 wpa_supplicant[736]: wlan0: CTRL-EVENT-SCAN-STARTED 
Oct  4 15:30:00 stager-Satellite-L40 dbus[373]: [system] Activating service name='org.freedesktop.UDisks2' (using servicehelper)
Oct  4 15:30:00 stager-Satellite-L40 udisksd[2026]: udisks daemon version 2.1.3 starting
Oct  4 15:30:00 stager-Satellite-L40 rtkit-daemon[1571]: Successfully made thread 2051 of process 2051 (n/a) owned by '1001' high priority at nice level -11.
Oct  4 15:30:00 stager-Satellite-L40 rtkit-daemon[1571]: Supervising 4 threads of 2 processes of 2 users.
Oct  4 15:30:00 stager-Satellite-L40 dbus[373]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Oct  4 15:30:00 stager-Satellite-L40 rtkit-daemon[1571]: Successfully made thread 2063 of process 2051 (n/a) owned by '1001' RT at priority 5.
Oct  4 15:30:00 stager-Satellite-L40 rtkit-daemon[1571]: Supervising 5 threads of 2 processes of 2 users.
Oct  4 15:30:00 stager-Satellite-L40 rtkit-daemon[1571]: Successfully made thread 2129 of process 2051 (n/a) owned by '1001' RT at priority 5.
Oct  4 15:30:00 stager-Satellite-L40 rtkit-daemon[1571]: Supervising 6 threads of 2 processes of 2 users.
Oct  4 15:30:00 stager-Satellite-L40 dbus[373]: [system] Successfully activated service 'org.freedesktop.UDisks2'
Oct  4 15:30:00 stager-Satellite-L40 udisksd[2026]: Acquired the name org.freedesktop.UDisks2 on the system message bus
Oct  4 15:30:00 stager-Satellite-L40 dbus[373]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
Oct  4 15:30:03 stager-Satellite-L40 kernel: [   61.294270] NFS: Registering the id_resolver key type
Oct  4 15:30:03 stager-Satellite-L40 kernel: [   61.294289] Key type id_resolver registered
Oct  4 15:30:03 stager-Satellite-L40 kernel: [   61.294291] Key type id_legacy registered
Oct  4 15:30:09 stager-Satellite-L40 dbus[373]: [system] Activating service name='org.mate.SettingsDaemon.DateTimeMechanism' (using servicehelper)
Oct  4 15:30:09 stager-Satellite-L40 dbus[373]: [system] Successfully activated service 'org.mate.SettingsDaemon.DateTimeMechanism'
Oct  4 15:30:20 stager-Satellite-L40 automount[1135]: key "rlg-storage" not found in map source(s).
Oct  4 15:33:43 stager-Satellite-L40 kernel: [  281.102172] perf samples too long (2505 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
Oct  4 15:41:53 stager-Satellite-L40 kernel: [  771.044388] RPC: AUTH_GSS upcall failed. Please check user daemon is running.
Oct  4 15:48:39 stager-Satellite-L40 kernel: [ 1177.217068] perf samples too long (5009 > 5000), lowering kernel.perf_event_max_sample_rate to 25000
Oct  4 15:54:24 stager-Satellite-L40 kernel: [ 1522.103842] RPC: AUTH_GSS upcall failed. Please check user daemon is running.
Oct  4 16:06:54 stager-Satellite-L40 kernel: [ 2272.011861] RPC: AUTH_GSS upcall failed. Please check user daemon is running.
Oct  4 16:17:02 stager-Satellite-L40 CRON[2867]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct  4 16:19:24 stager-Satellite-L40 kernel: [ 3022.012158] RPC: AUTH_GSS upcall failed. Please check user daemon is running.
Oct  4 16:31:54 stager-Satellite-L40 kernel: [ 3772.040664] RPC: AUTH_GSS upcall failed. Please check user daemon is running.
Oct  4 16:44:24 stager-Satellite-L40 kernel: [ 4522.011858] RPC: AUTH_GSS upcall failed. Please check user daemon is running.
Oct  4 16:56:55 stager-Satellite-L40 kernel: [ 5273.013539] RPC: AUTH_GSS upcall failed. Please check user daemon is running.
Oct  4 17:00:28 stager-Satellite-L40 kernel: [ 5486.000276] Monitor-Mwait will be used to enter C-3 state
Oct  4 17:01:13 stager-Satellite-L40 kernel: [ 5531.632521] ath5k: phy0: failed to wakeup the MAC Chip
Oct  4 17:01:13 stager-Satellite-L40 kernel: [ 5531.632530] ath5k: phy0: can't reset hardware (-5)
Oct  4 17:01:13 stager-Satellite-L40 kernel: [ 5531.632742] cfg80211: Calling CRDA to update world regulatory domain
Oct  4 17:00:50 stager-Satellite-L40 wpa_supplicant[736]: message repeated 47 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Oct  4 17:01:14 stager-Satellite-L40 wpa_supplicant[736]: wlan0: CTRL-EVENT-DISCONNECTED bssid=00:21:91:0b:c1:5b reason=4 locally_generated=1
Oct  4 17:01:14 stager-Satellite-L40 NetworkManager[718]: <warn> Connection disconnected (reason -4)
Oct  4 17:01:14 stager-Satellite-L40 wpa_supplicant[736]: wlan0: CTRL-EVENT-SCAN-STARTED 
Oct  4 17:01:14 stager-Satellite-L40 NetworkManager[718]: <info> (wlan0): supplicant interface state: completed -> scanning
Oct  4 17:01:14 stager-Satellite-L40 kernel: [ 5532.293534] ath5k: phy0: failed to wakeup the MAC Chip
Oct  4 17:01:14 stager-Satellite-L40 kernel: [ 5532.293542] ath5k: phy0: can't reset hardware (-5)
Oct  4 17:01:14 stager-Satellite-L40 kernel: [ 5532.415763] ath5k: phy0: failed to wakeup the MAC Chip
Oct  4 17:01:14 stager-Satellite-L40 kernel: [ 5532.415772] ath5k: phy0: can't reset hardware (-5)
Oct  4 17:01:15 stager-Satellite-L40 kernel: [ 5532.535907] ath5k: phy0: failed to wakeup the MAC Chip
Oct  4 17:01:15 stager-Satellite-L40 kernel: [ 5532.535915] ath5k: phy0: can't reset hardware (-5)
Oct  4 17:01:15 stager-Satellite-L40 kernel: [ 5532.659489] ath5k: phy0: failed to wakeup the MAC Chip
Oct  4 17:01:15 stager-Satellite-L40 kernel: [ 5532.659498] ath5k: phy0: can't reset hardware (-5)
Oct  4 17:01:15 stager-Satellite-L40 kernel: [ 5533.252449] cfg80211: World regulatory domain updated:
Oct  4 17:01:15 stager-Satellite-L40 kernel: [ 5533.252456] cfg80211:  DFS Master region: unset
Oct  4 17:01:15 stager-Satellite-L40 kernel: [ 5533.252458] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Oct  4 17:01:15 stager-Satellite-L40 kernel: [ 5533.252463] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Oct  4 17:01:15 stager-Satellite-L40 kernel: [ 5533.252467] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Oct  4 17:01:15 stager-Satellite-L40 kernel: [ 5533.252471] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
Oct  4 17:01:15 stager-Satellite-L40 kernel: [ 5533.252474] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Oct  4 17:01:15 stager-Satellite-L40 kernel: [ 5533.252477] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Oct  4 17:01:16 stager-Satellite-L40 kernel: [ 5533.817938] wlan0: authenticate with 00:21:91:0b:c1:5b
Oct  4 17:01:16 stager-Satellite-L40 wpa_supplicant[736]: wlan0: SME: Trying to authenticate with 00:21:91:0b:c1:5b (SSID='StagerHome' freq=2472 MHz)
Oct  4 17:01:16 stager-Satellite-L40 kernel: [ 5534.154902] wlan0: send auth to 00:21:91:0b:c1:5b (try 1/3)
Oct  4 17:01:16 stager-Satellite-L40 NetworkManager[718]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Oct  4 17:01:17 stager-Satellite-L40 NetworkManager[718]: <info> (wlan0): roamed from BSSID 00:21:91:0B:C1:5B (StagerHome) to (none) ((none))
Oct  4 17:01:17 stager-Satellite-L40 kernel: [ 5535.004044] wlan0: send auth to 00:21:91:0b:c1:5b (try 2/3)
Oct  4 17:01:18 stager-Satellite-L40 kernel: [ 5536.004084] wlan0: send auth to 00:21:91:0b:c1:5b (try 3/3)
Oct  4 17:01:19 stager-Satellite-L40 kernel: [ 5537.004048] wlan0: authentication with 00:21:91:0b:c1:5b timed out
Oct  4 17:01:19 stager-Satellite-L40 kernel: [ 5537.124588] net_ratelimit: 20 callbacks suppressed
Oct  4 17:01:19 stager-Satellite-L40 kernel: [ 5537.124595] ath5k: phy0: failed to wakeup the MAC Chip
Oct  4 17:01:19 stager-Satellite-L40 kernel: [ 5537.124600] ath5k: phy0: can't reset hardware (-5)
Oct  4 17:01:19 stager-Satellite-L40 NetworkManager[718]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Oct  4 17:01:19 stager-Satellite-L40 wpa_supplicant[736]: wlan0: CTRL-EVENT-SCAN-STARTED 
Oct  4 17:01:20 stager-Satellite-L40 NetworkManager[718]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Oct  4 17:01:20 stager-Satellite-L40 kernel: [ 5537.755147] ath5k: phy0: failed to wakeup the MAC Chip
Oct  4 17:01:20 stager-Satellite-L40 kernel: [ 5537.755156] ath5k: phy0: can't reset hardware (-5)
Oct  4 17:01:20 stager-Satellite-L40 kernel: [ 5537.879144] ath5k: phy0: failed to wakeup the MAC Chip
Oct  4 17:01:20 stager-Satellite-L40 kernel: [ 5537.879153] ath5k: phy0: can't reset hardware (-5)
Oct  4 17:01:20 stager-Satellite-L40 kernel: [ 5538.005878] ath5k: phy0: failed to wakeup the MAC Chip
Oct  4 17:01:20 stager-Satellite-L40 kernel: [ 5538.005885] ath5k: phy0: can't reset hardware (-5)
Oct  4 17:01:20 stager-Satellite-L40 kernel: [ 5538.130156] ath5k: phy0: failed to wakeup the MAC Chip
Oct  4 17:01:20 stager-Satellite-L40 kernel: [ 5538.130162] ath5k: phy0: can't reset hardware (-5)
Oct  4 17:01:26 stager-Satellite-L40 kernel: [ 5544.377593] net_ratelimit: 18 callbacks suppressed
Oct  4 17:01:26 stager-Satellite-L40 kernel: [ 5544.377601] ath5k: phy0: failed to wakeup the MAC Chip
Oct  4 17:01:26 stager-Satellite-L40 kernel: [ 5544.377605] ath5k: phy0: can't reset hardware (-5)
Oct  4 17:01:26 stager-Satellite-L40 kernel: [ 5544.502422] ath5k: phy0: failed to wakeup the MAC Chip
Oct  4 17:01:26 stager-Satellite-L40 kernel: [ 5544.502431] ath5k: phy0: can't reset hardware (-5)
......
[ 5282.635234] ath5k: phy0: failed to wakeup the MAC Chip
[ 5282.635245] ath5k: phy0: can't reset hardware (-5)
[ 5345.123562] net_ratelimit: 16 callbacks suppressed
.....
[17813.404269] ath5k: phy0: failed to wakeup the MAC Chip
[17813.404277] ath5k: phy0: can't reset hardware (-5)
[17813.524309] ath5k: phy0: failed to wakeup the MAC Chip
[17813.524315] ath5k: phy0: can't reset hardware (-5)
[17813.644979] ath5k: phy0: failed to wakeup the MAC Chip
[17813.644988] ath5k: phy0: can't reset hardware (-5)
[17813.765094] ath5k: phy0: failed to wakeup the MAC Chip
[17813.765100] ath5k: phy0: can't reset hardware (-5)

    ======== Done ========

```

---

### Post by varunendra on 2014-10-05
Can you try installing an entire new kernel? Be aware that this has the potential to break some functionality.

If you want to give it a go, download the 'linux-image-<version of your choice>-generic....' and respective 'linux-headers-<same version>..all.deb' and 'linux-headers-<same version>...generic...' packages from here : [http://archive.ubuntu.com/ubuntu/pool/main/l/linux/](http://archive.ubuntu.com/ubuntu/pool/main/l/linux/)

You should be able to install them with double-click, or with 'dpkg -i *' command.

By the way, did you submit a new bug report as Christopher suggested on the current bug report page? I would like to follow it if you did.

---

### Post by stager2 on 2014-10-05
> **varunendra said:**
> Can you try installing an entire new kernel?
If you tell us how to return old kernel if troubles.

> **varunendra said:**
> By the way, did you submit a new bug report as Christopher suggested on the current bug report page? I would like to follow it if you did.
Now yes: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1377609](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1377609)

---

### Post by varunendra on 2014-10-05
> **stager2 said:**
> If you tell us how to return old kernel if troubles.
I don't have personal experience of this kind, but should be as easy as booting into the older kernel from Grub menu, then run 'apt-get purge <packages>' or 'dpkg -P <packages>'.

But if you want a guarantee, it would be best to take your OS partition's image using clonezilla or something similar. Although I'm sure most of the experienced users would call it security paranoia, which I feel like agreeing with. :|

---

### Post by the_doctor2 on 2014-10-18
> **varunendra said:**
> Welcome to the forums stager2!

Looks like an old bug resurrected : [https://bugs.launchpad.net/bugs/432353](https://bugs.launchpad.net/bugs/432353)

Please add yourself to the "Affects Me" list of the above bug and add your comments confirming its 'still exists' status.

In the meanwhile, please try -
```
echo "options ath5k nohwcrypt=Y" | sudo tee /etc/modprobe.d/ath5k.conf
```
..followed by a reboot. Does this help?

I just registered to simply thank you. I was pulling my hair out because of this non-sense POS Atheros wireless adapter and then I found your solution... and it worked !

So, thanks :)

---

### Post by varunendra on 2014-10-22
Welcome to the forums the_doctor2! Glad it could help you. :)

---

