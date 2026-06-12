---
title: "Wi-FI Stops Working upon Boot When Being Disconnected From Power While Turned Off"
date: 2014-10-08
forum: Networking &amp; Wireless
---

### Post by nenad6 on 2014-10-08
So the problem is fairly described in the title. The routine goes like this:
  -I turn off the computer. The power cord makes a beeping sound, so i  disconnect it from the laptop before going to sleep. The battery is  present this whole time. -I plug the power in, and when Ubuntu boots, wifi doesn't work. The only  way to turn it on is to do a hard reset, with pulling the battery out.  Simple reboot doesn't cut it. It simply doesn't show wifi as an option  in network manager. -It works upon new boot.
  So, i have an atheros wifi card, with the driver ath5k supporting it.  I can't turn on and off wifi with manual keyboard hotkeys, since that  never worked on linux. It just says it's on the whole time (even when it  doesn't  work).
  So, i used to have a similar problem before in Debian Squeeze, and this command did it for me:
  echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
  ...but it doesn't work now on ubuntu 14.04. Any way i could revert the change i did with this command? Any other solutions?
  Thanks.

---

### Post by varunendra on 2014-10-08
Please follow the instructions in this post to download and run 'wireless_script' (alternative version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by nenad6 on 2014-10-13
Thank you, will do as soon as the problem reappears.

---

### Post by nenad6 on 2014-10-25
Hi there.

So, the problem didn't reappear until today. here's the output to your wireless script:

```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

ubuntu 3.13.0-37-generic x86_64,  Ubuntu 14.04.1 LTS, trusty

CPU    : Pentium(R) Dual-Core CPU       T4300  @ 2.10GHz
Memory : 3886 MB
Uptime : 17:07:00 up  8:46,  2 users,  load average: 0,82, 0,82, 0,59


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 02)
    Subsystem: Fujitsu Technology Solutions Device [1734:113f]
    Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 008 Device 002: ID 05b8:3166 Agiler, Inc. 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 04f2:b09c Chicony Electronics Co., Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface                 Soft blocked  Hard blocked
2: acer-wireless: Wireless LAN      no            no
3: hci0: Bluetooth                  no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

acer_wmi               32522  0 
sparse_keymap          13948  1 acer_wmi
ath5k                 149924  0 
ath                    28698  1 ath5k
mac80211              630653  1 ath5k
cfg80211              484040  3 ath,ath5k,mac80211
wmi                    19177  1 acer_wmi
video                  19476  2 i915,acer_wmi


module parameters ~~~~~~~~~~~~~~~~~~

acer_wmi      (5): brightness=-1 | ec_raw_mode=N | force_series=0 | mailled=-1 | threeg=-1
ath5k         (3): fastchanswitch=N | nohwcrypt=N | no_hw_rfkill_switch=N
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: disconnected
================o=======o========o=============o==  =======o===========o==============o===========
 Interface & ID | Type  | Driver | State       | Default | Speed     | Support      | HW Addr   
================o=======o========o=============o==  =======o===========o==============o===========
 eth0           | Wired | r8169  | unavailable | no      |           |              | <MAC eth0>
----------------+-------+--------+-------------+---------+-----------+--------------+-----------


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

Zelod                : ssid=Zelod | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~



Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "sl_SI.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

           - 


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~



blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[acer_wmi]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/platform/x86/acer-wmi.ko
srcversion:     15371DC0E403E93954B38E5
depends:        wmi,sparse-keymap,video
parm:           mailled:Set initial state of Mail LED (int)
parm:           brightness:Set initial LCD backlight brightness (int)
parm:           threeg:Set initial state of 3G hardware (int)
parm:           force_series:Force a different laptop series (int)
parm:           ec_raw_mode:Enable EC raw mode (bool)

[ath5k]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
srcversion:     F36818A2F0BCB2B0CC9BB8C
depends:        mac80211,cfg80211,ath
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)

[ath]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-37-generic/kernel/net/mac80211/mac80211.ko
srcversion:     B822641624778B987844F6F
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-37-generic/kernel/net/wireless/cfg80211.ko
srcversion:     C2478077E22138832B71659
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[wmi]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)

[video]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/acpi/video.ko
srcversion:     FBDB15F61F4F35FB6EE9AC8
depends:        
parm:           brightness_switch_enabled:bool
parm:           allow_duplicates:bool
parm:           use_native_backlight:int


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0x001c (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-37-generic root=UUID=1d753fed-8330-44c0-a7d7-883f9e2dd233 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.616940] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.617259] audit: initializing netlink socket (disabled)
[    1.116491] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   10.994509] wmi: Mapper loaded
[   11.266255] ath5k 0000:04:00.0: can't disable ASPM; OS doesn't have ASPM control
[   11.266406] ath5k 0000:04:00.0: registered as 'phy0'
[   11.950798] ath: EEPROM regdomain: 0x60
[   11.950798] ath: EEPROM indicates we should expect a direct regpair map
[   11.950800] ath: Country alpha2 being used: 00
[   11.950801] ath: Regpair used: 0x60
[   11.958997] ath5k: phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   11.976594] acer_wmi: Acer Laptop ACPI-WMI Extras
[   11.977636] acer_wmi: Brightness must be controlled by acpi video driver
[   15.219881] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.306996] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.307474] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.425323] wlan0: authenticate with <MAC ID removed>
[   18.432795] wlan0: send auth to <MAC ID removed> (try 1/3)
[   18.436528] wlan0: authenticated
[   18.440082] wlan0: associate with <MAC ID removed> (try 1/3)
[   18.442710] wlan0: RX AssocResp from <MAC ID removed> (capab=0x431 status=0 aid=1)
[   18.442945] wlan0: associated
[   18.442984] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   18.473721] wlan0: deauthenticating from <MAC ID removed> by local choice (reason=2)
[   18.474027] wlan0: authenticate with <MAC ID removed>
[   18.474231] wlan0: send auth to <MAC ID removed> (try 1/3)
[   18.476687] wlan0: authenticated
[   18.480470] wlan0: associate with <MAC ID removed> (try 1/3)
[   18.483094] wlan0: RX AssocResp from <MAC ID removed> (capab=0x431 status=0 aid=1)
[   18.483321] wlan0: associated
[   18.498473] ath: EEPROM regdomain: 0x8348
[   18.498478] ath: EEPROM indicates we should expect a country code
[   18.498480] ath: doing EEPROM country->regdmn map search
[   18.498481] ath: country maps to regdmn code: 0x3a
[   18.498483] ath: Country alpha2 being used: US
[   18.498484] ath: Regpair used: 0x3a
[   18.498486] ath: regdomain 0x8348 dynamically updated by country IE
[12194.567341] wlan0: deauthenticating from <MAC ID removed> by local choice (reason=3)
[12197.220055] ath5k 0000:04:00.0: Refused to change power state, currently in D3

    ======== Done ========
```

For any type of help regarding my issue i'll be very grateful.

Kind regards,

---

