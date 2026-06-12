---
title: "Unstable wireless on Ubuntu 14.04 LTS"
date: 2015-02-22
forum: Networking &amp; Wireless
---

### Post by billyjean2 on 2015-02-22
I have problems with my wireless on Ubuntu 14.04 LTS, running on my Lenovo T440s. Often the following occurs:

 - On start-up my computer doesn't always connect to my wireless
 - When connected, at some time suddenly the connection is lost

I was advised in a different forum to run the script described [here]("http://ubuntuforums.org/showthread.php?t=2224209&p=13024222#post13024222"), the contents are:


```
    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

laptop-t440s 3.13.0-45-generic x86_64,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Core(TM) i5-4200U CPU @ 1.60GHz
Memory : 11740 MB
Uptime : 22:01:39 up  1:11,  2 users,  load average: 0.15, 0.35, 0.59


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I218-V [8086:1559] (rev 04)
    Subsystem: Lenovo Device [17aa:2214]
    Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b2] (rev 83)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:c270]
    Kernel driver in use: iwlwifi


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 04f2:b39a Chicony Electronics Co., Ltd 
Bus 002 Device 003: ID 138a:0017 Validity Sensors, Inc. 
Bus 002 Device 002: ID 0bdb:193e Ericsson Business Mobile Networks BV 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11abgn  ESSID:"TeliaGatewayA4-B1-E9-52-10-80"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC C-NA *TeliaGatewayA4-B1-E9-52-10-80 1>   
          Bit Rate=130 Mb/s   Tx-Power=22 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:107   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface                    Soft blocked  Hard blocked
0: tpacpi_bluetooth_sw: Bluetooth      yes           no
1: tpacpi_wwan_sw: Wireless WAN        no            no
2: phy0: Wireless LAN                  no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

iwlmvm                189813  0 
mac80211              630669  1 iwlmvm
iwlwifi               169932  1 iwlmvm
cfg80211              484040  3 iwlwifi,mac80211,iwlmvm
wmi                    19177  0 


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
iwlmvm        (2): init_dbg=N | power_scheme=2
iwlwifi      (11): 11n_disable=0 | amsdu_size_8K=0 | antenna_coupling=0 | bt_coex_active=Y | fw_restart=Y | led_mode=0 | nvm_file=(null) | power_level=0 | power_save=N | swcrypto=0 | wd_disable=1
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
========================================o=============o=========o=============o=========o===========o==============o===========
 Interface & ID                         | Type        | Driver  | State       | Default | Speed     | Support      | HW Addr   
========================================o=============o=========o=============o=========o===========o==============o===========
 wlan0  [TeliaGatewayA4-B1-E9-52-10-80] | 802.11 WiFi | iwlwifi | connected   | yes     | 130 Mb/s  | WEP/WPA/WPA2 | <MAC wlan0>

    *TeliaGatewayA4-B1-E9-52-10-80: Infra, <MAC C-NA *TeliaGatewayA4-B1-E9-52-10-80 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 68 WPA WPA2

    Address:         192.168.1.65
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1
----------------------------------------+-------------+---------+-------------+---------+-----------+--------------+-----------
 eth0                                   | Wired       | e1000e  | unavailable | no      |           |              | <MAC eth0>
----------------------------------------+-------------+---------+-------------+---------+-----------+--------------+-----------


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
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~
 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1
search lan


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.557/1.982/2.407/0.425 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.033/0.042/0.051/0.009 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     32 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)
          Channel 36 (5.18 GHz)
          Channel 40 (5.2 GHz)
          Channel 44 (5.22 GHz)
          Channel 48 (5.24 GHz)
          Channel 52 (5.26 GHz)
          Channel 56 (5.28 GHz)
          Channel 60 (5.3 GHz)
          Channel 64 (5.32 GHz)
          Channel 100 (5.5 GHz)
          Channel 104 (5.52 GHz)
          Channel 108 (5.54 GHz)
          Channel 112 (5.56 GHz)
          Channel 116 (5.58 GHz)
          Channel 120 (5.6 GHz)
          Channel 124 (5.62 GHz)
          Channel 128 (5.64 GHz)
          Channel 132 (5.66 GHz)
          Channel 136 (5.68 GHz)
          Channel 140 (5.7 GHz)

          Current Frequency:2.412 GHz (Channel 1)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

No way to aquire root rights found.


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[iwlmvm]
filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
version:        in-tree:
srcversion:     412FF07DA992AAD938A30BE
depends:        iwlwifi,mac80211,cfg80211
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)

[mac80211]
filename:       /lib/modules/3.13.0-45-generic/kernel/net/mac80211/mac80211.ko
srcversion:     385697223F8285F67C93A06
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
version:        in-tree:
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265-7.ucode
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     B81BA270CF5925E724426BD
depends:        cfg80211
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)

[cfg80211]
filename:       /lib/modules/3.13.0-45-generic/kernel/net/wireless/cfg80211.ko
srcversion:     C2478077E22138832B71659
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[wmi]
filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x8086:0x1559 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x08b2 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Not Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/rc.local]
rfkill block bluetooth
exit 0

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-45-generic root=UUID=866d43f0-b9b2-4976-b39c-b563e7d4b069 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.146869] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.147458] audit: initializing netlink socket (disabled)
[    3.128928] wmi: Mapper loaded
[    3.144415] iwlwifi 0000:03:00.0: irq 61 for MSI/MSI-X
[    3.268368] iwlwifi 0000:03:00.0: loaded firmware version 22.24.8.0 op_mode iwlmvm
[    3.297960] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[    3.298478] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[    3.298975] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[    3.423588] thinkpad_acpi: http://ibm-acpi.sf.net/
[    3.425880] thinkpad_acpi: Unsupported brightness interface, please contact ibm-acpi-devel@lists.sourceforge.net
[    3.504074] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    5.176456] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    5.614451] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[    5.614947] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[    5.632251] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    5.632513] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    7.262925] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   32.327606] wlan0: authenticate with <MAC C-NA *TeliaGatewayA4-B1-E9-52-10-80 1>
[   32.331744] wlan0: send auth to <MAC C-NA *TeliaGatewayA4-B1-E9-52-10-80 1> (try 1/3)
[   32.336951] wlan0: authenticated
[   32.337130] wlan0: associate with <MAC C-NA *TeliaGatewayA4-B1-E9-52-10-80 1> (try 1/3)
[   32.341155] wlan0: RX AssocResp from <MAC C-NA *TeliaGatewayA4-B1-E9-52-10-80 1> (capab=0x411 status=0 aid=2)
[   32.345428] wlan0: associated
[   32.345456] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1995.773364] wlan0: authenticate with <MAC C-NA *TeliaGatewayA4-B1-E9-52-10-80 1>
[ 1995.777500] wlan0: send auth to <MAC C-NA *TeliaGatewayA4-B1-E9-52-10-80 1> (try 1/3)
[ 1995.782376] wlan0: authenticated
[ 1995.784551] wlan0: associate with <MAC C-NA *TeliaGatewayA4-B1-E9-52-10-80 1> (try 1/3)
[ 1995.788390] wlan0: RX AssocResp from <MAC C-NA *TeliaGatewayA4-B1-E9-52-10-80 1> (capab=0x411 status=0 aid=2)
[ 1995.790209] wlan0: associated
[ 3793.008755] wlan0: authenticate with <MAC C-NA *TeliaGatewayA4-B1-E9-52-10-80 1>
[ 3793.013740] wlan0: send auth to <MAC C-NA *TeliaGatewayA4-B1-E9-52-10-80 1> (try 1/3)
[ 3793.138233] wlan0: send auth to <MAC C-NA *TeliaGatewayA4-B1-E9-52-10-80 1> (try 2/3)
[ 3793.245172] wlan0: send auth to <MAC C-NA *TeliaGatewayA4-B1-E9-52-10-80 1> (try 3/3)
[ 3793.335654] wlan0: authentication with <MAC C-NA *TeliaGatewayA4-B1-E9-52-10-80 1> timed out
[ 3804.750104] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3866.130144] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[ 3866.130749] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[ 3866.149290] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3873.016329] wlan0: authenticate with <MAC C-NA *TeliaGatewayA4-B1-E9-52-10-80 1>
[ 3873.021339] wlan0: send auth to <MAC C-NA *TeliaGatewayA4-B1-E9-52-10-80 1> (try 1/3)
[ 3873.129322] wlan0: send auth to <MAC C-NA *TeliaGatewayA4-B1-E9-52-10-80 1> (try 2/3)
[ 3873.133207] wlan0: authenticated
[ 3873.135716] wlan0: associate with <MAC C-NA *TeliaGatewayA4-B1-E9-52-10-80 1> (try 1/3)
[ 3873.145985] wlan0: RX AssocResp from <MAC C-NA *TeliaGatewayA4-B1-E9-52-10-80 1> (capab=0x411 status=0 aid=2)
[ 3873.149555] wlan0: associated
[ 3873.149592] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3873.162564] wlan0: deauthenticating from <MAC C-NA *TeliaGatewayA4-B1-E9-52-10-80 1> by local choice (reason=2)
[ 3873.167054] wlan0: authenticate with <MAC C-NA *TeliaGatewayA4-B1-E9-52-10-80 1>
[ 3873.170928] wlan0: send auth to <MAC C-NA *TeliaGatewayA4-B1-E9-52-10-80 1> (try 1/3)
[ 3873.173295] wlan0: authenticated
[ 3873.175666] wlan0: associate with <MAC C-NA *TeliaGatewayA4-B1-E9-52-10-80 1> (try 1/3)
[ 3873.181195] wlan0: RX AssocResp from <MAC C-NA *TeliaGatewayA4-B1-E9-52-10-80 1> (capab=0x411 status=0 aid=2)
[ 3873.188050] wlan0: associated

    ======== Done ========
```

---

### Post by Hadaka on 2015-02-22
Hi, please do..
```
[COLOR=#000000]sudo modprobe -rf iwlwifi
sudo modprobe [/COLOR]iwlwifi 11n_disable=8
```
then.
```
sudo iw reg set US
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda 
```
and this should really help
```
sudo iwconfig wlan0 power off
```
thanks.

---

### Post by jsabath on 2015-02-22
Hey.  I just installed Ubuntu 14 on my Lenovo x131e.  I had Windows 7 Professional on it before installation, and I am a first time Ubuntu user, so I don't know much.  Upon installing Ubuntu, I found that I can not turn on Wi-Fi.  The button to turn it on in system settings does not work or even switch to on.  I can only hook up to the internet through ethernet, which is really irritating.  What should I do to allow Wi-Fi to run from the minute I turn on my computer?  I really need help here.  The forums I have looked into have been of no help.  Your help would be much appreciated.

---

### Post by Hadaka on 2015-02-22
@jsbath...please start your own thread
as hijaking this one will not likely get your problem fixed
thanks.

---

### Post by billyjean2 on 2015-02-23
> **Hadaka said:**
> Hi, please do..
```
[COLOR=#000000]sudo modprobe -rf iwlwifi
sudo modprobe [/COLOR]iwlwifi 11n_disable=8
```
then.
```
sudo iw reg set US
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda 
```
and this should really help
```
sudo iwconfig wlan0 power off
```
thanks.

Thanks for this suggestion, I tried it out. Can I ask what it does?

---

### Post by kevin149 on 2015-02-23
I was having the same problem on my Lenovo laptop until this was suggested for me and it has worked fine since then.

Code:
echo "options rtl8723be fwlps=0 swlps=0 swenc=1" | sudo tee /etc/modprobe.d/rtl8723be.conf

---

### Post by Hadaka on 2015-02-23
@kevin149

billyjean2 has an intel card.

03:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b2] (rev 83)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:c270]
    Kernel driver in use: iwlwifi[COLOR=#ff0000] <-   You dont

Code:
echo "options rtl8723be fwlps=0 swlps=0 swenc=1" | sudo tee /etc/modprobe.d/rtl8723be.conf 








[/COLOR][COLOR=#000000][/COLOR][COLOR=#000000][/COLOR][COLOR=#000000][/COLOR][COLOR=#000000][/COLOR][COLOR=#000000][/COLOR][COLOR=#000000][/COLOR]

---

### Post by billyjean2 on 2015-02-25
I ran the update manager, after which my wireless stopped working (!). Then I tried to re-type the commands in post #2 by Hadaka, after which it worked again. 

But this apparently means that every time I update or run *sudo apt-get update* I will have to run the commands. Is there a way to make the wireless-settings permanent?

---

