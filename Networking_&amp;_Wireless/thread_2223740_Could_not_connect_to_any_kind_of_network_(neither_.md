---
title: "Could not connect to any kind of network (neither wlan,nor ethernet)"
date: 2014-05-12
forum: Networking &amp; Wireless
---

### Post by cryingamer on 2014-05-12
Hello,
im new in using linux i just installed it on my desktop pc and running it beside windows.
But when i try to connect to the internet (via wlan or ethernet) im getting into a loop where the system says nearly almost all 30 seconds "Disconnectet ethernet/Wlan connection, you are now offline" or something like that.
I tried to use wicd as a network manager but with this my ethernet connection wont optain an ip-address and i cant set a wlan password for my wlan network (i cant close the wicd diloge it seemed like its buggy).
Can please anybody tell me to try something? I dont know what to do. I already searched a lot in other threads or forums but i found no clue for my problem.
I thank everybody who has a more or less useful answere kindly.

EDIT:Im running on Ubuntu Desktop 14.04 lts.
EDITno2: Everything works on Windows.

---

### Post by Hadaka on 2014-05-12
hi, ,does the wired and wireless still work on the windows?
please open a terminal   ctrl/alt/t then COPY and paste...
```
lspci -n | egrep '0200|0280' | awk '{print $3}'
```
post the results.
thanks.

---

### Post by cryingamer on 2014-05-12
Yes it both works fine on windows(Sorry i will add this to the original post) and the output of the command is:
```
168c:002d
10ec:8168
```

---

### Post by Hadaka on 2014-05-12
please post the output of..
```
sudo modprobe -rf ath9k
sudo modprobe -v ath9k
```
did it wake up?
```
dmesg | grep ath9
```
thanks

---

### Post by cryingamer on 2014-05-13
After entering all three commands this was the output:
```

lukas@luke:~$ sudo modprobe -v ath9k
insmod /lib/modules/3.13.0-24-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.13.0-24-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/ath.ko 
insmod /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko 
insmod /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko 
insmod /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko 
lukas@luke:~$ dmesg | grep ath9
[   74.001727] Modules linked in: rfcomm bnep bluetooth snd_usb_audio snd_usbmidi_lib snd_hda_codec_hdmi hid_generic usbhid hid arc4 snd_hda_codec_realtek mxm_wmi snd_seq_midi snd_hda_intel snd_seq_midi_event ath9k snd_hda_codec ath9k_common ath9k_hw snd_hwdep snd_pcm kvm_amd ath radeon mac80211 snd_rawmidi snd_seq kvm snd_seq_device cfg80211 serio_raw snd_page_alloc edac_core k10temp edac_mce_amd snd_timer snd ttm drm_kms_helper sp5100_tco i2c_piix4 soundcore drm i2c_algo_bit wmi mac_hid parport_pc ppdev lp parport pata_acpi firewire_ohci r8169 firewire_core mii crc_itu_t pata_atiixp ahci libahci
[   82.538684] ath9k: ath9k: Driver unloaded
[   99.249701] ath9k: ath9k: Driver unloaded
lukas@luke:~$


```

---

### Post by cryingamer on 2014-05-17
Hey, is anybody out there who can help me?

---

### Post by Hadaka on 2014-05-17
hi, sorry i am late getting back to you.
please do..
```
echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
```
boot.
any change?

---

### Post by cryingamer on 2014-05-17
No problem i just thought i had been forgotten ;D
But for my problem: No change after entering and rebooting.

Maybe should i completely disable WICD? It always says that there is something wrong with something d-bus thing. Could this change something?

---

### Post by Hadaka on 2014-05-17
yes..unload wicd and reload networkmgr.. then do and post
```
sudo modprobe -r ath9k
sudo modprobe -v ath9k
dmesg | egrep 'wlan|ath9k'
rfkill list all
```
thanks

---

### Post by cryingamer on 2014-05-18
I checked via ```
sudo status network-manager
```if it is running and it is.
So now here the output for your commands:
```
lukas@luke:~$ sudo modprobe -r ath9k
[sudo] password for lukas: 
lukas@luke:~$ sudo modprobe -v ath9k
insmod /lib/modules/3.13.0-24-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.13.0-24-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/ath.ko 
insmod /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko 
insmod /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko 
insmod /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko nohwcrypt=1 
lukas@luke:~$ dmesg | egrep 'wlan|ath9k'
[   18.236524] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.239569] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  261.187710] ath9k: ath9k: Driver unloaded
[  267.945779] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  267.948811] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
lukas@luke:~$ rfkill list all
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
lukas@luke:~$
```

---

### Post by Hadaka on 2014-05-18
hi, please do..
```
nm-tool
cat /var/log/syslog | grep ath | tail -n25
```
thanks

---

### Post by cryingamer on 2014-05-18
This is what i got(still doesnt work,i dont know if it should):
```
lukas@luke:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        74:D4:35:53:4E:88

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        A0:F3:C1:B4:FA:41

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    WLAN-6AEE29:     Infra, 00:12:BF:6A:EE:7E, Freq 2417 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    WLAN-6AEE29:     Infra, 10:FE:ED:DC:AF:8B, Freq 2417 MHz, Rate 54 Mb/s, Strength 52 WPA WPA2


lukas@luke:~$ cat /var/log/syslog | grep ath | tail -n25
May 18 12:18:46 luke NetworkManager[767]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:15.0/0000:05:00.0/net/eth0, iface: eth0)
May 18 12:18:46 luke NetworkManager[767]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:15.0/0000:05:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
May 18 12:18:46 luke NetworkManager[767]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
May 18 12:18:46 luke NetworkManager[767]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
May 18 12:18:46 luke NetworkManager[767]: <info> rfkill0: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:14.4/0000:04:06.0/ieee80211/phy0/rfkill0) (driver ath9k)
May 18 12:18:46 luke NetworkManager[767]: <info> (wlan0): new 802.11 WiFi device (driver: 'ath9k' ifindex: 3)
May 18 12:18:47 luke whoopsie[862]: Using lock path: /var/lock/whoopsie/lock
May 18 21:26:02 luke kernel: [    1.221043] Loaded X.509 cert 'Magrathea: Glacier signing key: 00a5a65759de474bc5c43120880c1b94a539f431'
May 18 21:26:02 luke kernel: [   12.650534] ath: EEPROM regdomain: 0x809c
May 18 21:26:02 luke kernel: [   12.650537] ath: EEPROM indicates we should expect a country code
May 18 21:26:02 luke kernel: [   12.650538] ath: doing EEPROM country->regdmn map search
May 18 21:26:02 luke kernel: [   12.650539] ath: country maps to regdmn code: 0x52
May 18 21:26:02 luke kernel: [   12.650541] ath: Country alpha2 being used: CN
May 18 21:26:02 luke kernel: [   12.650542] ath: Regpair used: 0x52
May 18 21:26:02 luke kernel: [   18.125158] type=1400 audit(1400441162.368:22): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/telepathy/mission-control-5" pid=724 comm="apparmor_parser"
May 18 21:26:02 luke kernel: [   18.125165] type=1400 audit(1400441162.368:23): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/telepathy/telepathy-*" pid=724 comm="apparmor_parser"
May 18 21:26:04 luke NetworkManager[1026]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:14.4/0000:04:06.0/net/wlan0, iface: wlan0)
May 18 21:26:04 luke NetworkManager[1026]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:14.4/0000:04:06.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
May 18 21:26:04 luke NetworkManager[1026]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:15.0/0000:05:00.0/net/eth0, iface: eth0)
May 18 21:26:04 luke NetworkManager[1026]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:15.0/0000:05:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
May 18 21:26:04 luke NetworkManager[1026]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
May 18 21:26:04 luke NetworkManager[1026]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
May 18 21:26:04 luke whoopsie[862]: Using lock path: /var/lock/whoopsie/lock
May 18 21:26:04 luke NetworkManager[1026]: <info> rfkill0: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:14.4/0000:04:06.0/ieee80211/phy0/rfkill0) (driver ath9k)
May 18 21:26:04 luke NetworkManager[1026]: <info> (wlan0): new 802.11 WiFi device (driver: 'ath9k' ifindex: 3)
lukas@luke:~$ 
```

---

### Post by Hadaka on 2014-05-18
are you running this in virtual mode?

It looks like your wired side is running.
its also makeing a note about rfkill...but i dont see that on your last report.
confusing.. please do..
```
cat /etc/modules
cat /etc/network/interfaces
rfkill list all
```
thanks

---

### Post by cryingamer on 2014-05-18
This is what i got(what is Virtual mode?):
```
lukas@luke:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.

lp
rtc
lukas@luke:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
lukas@luke:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
lukas@luke:~$

```

---

### Post by cryingamer on 2014-05-22
I think, i can push this without getting anyone angry :)

---

### Post by Hadaka on 2014-05-22
Hi, lets take a more extensive look
please do..
```
http://ubuntuforums.org/showthread.php?t=2224209&p=13024222#post13024222
```
thanks.

---

### Post by cryingamer on 2014-05-22
If i should do this wireless_script thing then here we go:
```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

luke 3.13.0-24-generic x86_64,  Ubuntu 14.04 LTS, trusty

CPU    : AMD Phenom(tm) II X4 955 Processor
Memory : 8030 MB
Uptime : 20:18:06 up 6 min,  1 user,  load average: 0,08, 0,13, 0,08


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

04:06.0 Network controller [0280]: Qualcomm Atheros AR9227 Wireless Network Adapter [168c:002d] (rev 01)
    Subsystem: Qualcomm Atheros Device [168c:0300]
    Kernel driver in use: ath9k
--
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 003: ID 1532:001c Razer USA, Ltd RZ01-0036 Optical Gaming Mouse [Abyssus]
Bus 008 Device 002: ID 2109:3431  
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

mxm_wmi                13021  0 
ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              626489  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211
wmi                    19177  1 mxm_wmi


module parameters ~~~~~~~~~~~~~~~~~~

ath9k         (5): blink=0 | bt_ant_diversity=0 | btcoex_enable=0 | nohwcrypt=1 | ps_enable=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: disconnected
================o=============o========o==============o=========o===========o==============o===========
 Interface & ID | Type        | Driver | State        | Default | Speed     | Support      | HW Addr   
================o=============o========o==============o=========o===========o==============o===========
 eth0           | Wired       | r8169  | unavailable  | no      |           |              | <MAC eth0>
----------------+-------------+--------+--------------+---------+-----------+--------------+-----------
 wlan0          | 802.11 WiFi | ath9k  | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    WLAN-6AEE29:     Infra, <MAC C-NA WLAN-6AEE29 1>, Freq 2417 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    WLAN-6AEE29:     Infra, <MAC C-NA WLAN-6AEE29 2>, Freq 2417 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
----------------+-------------+--------+--------------+---------+-----------+--------------+-----------


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

no-auto-default=<MAC eth0>,

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~
 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~



Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : de_DE.UTF-8)
country CN:
    (2402 - 2482 @ 40), (N/A, 20)
    (5735 - 5835 @ 40), (N/A, 30)
    (57240 - 59400 @ 2160), (N/A, 28)
    (59400 - 63720 @ 2160), (N/A, 44)
    (63720 - 65880 @ 2160), (N/A, 28)


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

No way to aquire root rights found.


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[ath9k]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
srcversion:     BAF225EEB618908380B28DA
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[ath9k_common]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw

[ath9k_hw]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
srcversion:     4809F3842A0542CD6B556D3
depends:        ath

[ath]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-24-generic/kernel/net/mac80211/mac80211.ko
srcversion:     C0F95BBF832E05DEFD722F4
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-24-generic/kernel/net/wireless/cfg80211.ko
srcversion:     8B3D642D1F2E6406EF33F74
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0x002d (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
ath9k.conf        : options ath9k nohwcrypt=1
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=a1da53f8-6af6-46f2-9f3d-d4103ed75223 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.873250] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.873463] audit: initializing netlink socket (disabled)
[    1.270528] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   10.919996] wmi: Mapper loaded
[   11.286923] ath: EEPROM regdomain: 0x809c
[   11.286925] ath: EEPROM indicates we should expect a country code
[   11.286927] ath: doing EEPROM country->regdmn map search
[   11.286928] ath: country maps to regdmn code: 0x52
[   11.286929] ath: Country alpha2 being used: CN
[   11.286930] ath: Regpair used: 0x52
[   13.282547] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.170493] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.173533] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

    ======== Done ========

```

---

### Post by chili555 on 2014-05-23
I think you might have better luck if Wicd and Network Manager were not conflicting. I suggest you remove Wicd:```
sudo apt-get purge wicd*
```Reboot.

Now do you see networks listed when you click the Network Manager icon? [http://www.oulu.fi/it/graphics/nmgui.png](http://www.oulu.fi/it/graphics/nmgui.png) What happens when you click on yours and try to connect?

---

### Post by cryingamer on 2014-05-23
I think you missed the problem i have.
I could see the network i want to connect to all the time but if i try to connect then i get into a loop where the system says (every 15seconds) "WLAN disconnected, you are now offline".
After completely removeing WICD there's still the same problem as mansioned in my startup post.

---

### Post by chili555 on 2014-05-24
I didn't miss the problem at all. I believe, however, that installing a conflicting network management program, in your case Wicd, does nothing to help and probably everything to hurt your ability to connect. Please note you said:> i cant close the wicd diloge it seemed like its buggyAnd also:> Maybe should i completely disable WICD? It always says that there is something wrong with something d-bus thing. Could this change something?You didn't remove or in any way disable Network Manager. 

My intent was to get Wicd and its problems out of the picture *first* and then proceed. Let's try a few things. 

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router.

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or vim if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close gedit.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

Is there any improvement?

---

### Post by cryingamer on 2014-05-24
I couldnt use ```
gksudo gedit ...
``` so i just used ```
sudo gedit ...
``` with that i could change the code.
If i used the correct code (DE for germany i think) then i got no errors or something but there is no improvement with my connection.

---

### Post by chili555 on 2014-05-24
DE is correct for Germany. Let's see what the system said previously:> ath: Country alpha2 being used: CNIt thought you were in China!

Let's see if there is any clue in the logs. Please reboot so we have a clean slate and the let us see:```
dmesg | grep ath
cat /var/log/syslog | grep -e wlan -e etwork | tail -n25
```Maybe we can see what Network Manager is doing behind the scenes.

---

### Post by cryingamer on 2014-05-24
Now im confused.
I got this Code:```
lukas@luke:~$ dmesg | grep ath
[    1.224828] Loaded X.509 cert 'Magrathea: Glacier signing key: 00a5a65759de474bc5c43120880c1b94a539f431'
[   11.307772] ath: EEPROM regdomain: 0x809c
[   11.307775] ath: EEPROM indicates we should expect a country code
[   11.307776] ath: doing EEPROM country->regdmn map search
[   11.307777] ath: country maps to regdmn code: 0x52
[   11.307778] ath: Country alpha2 being used: CN    <-------This line confuses me because i looked up the /crda file and there was REGDOMAIN=DE
[   11.307779] ath: Regpair used: 0x52
[   25.374944] ath9k 0000:04:06.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   25.374947] ath9k 0000:04:06.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
lukas@luke:~$ cat /var/log/syslog | grep -e -wlan -e etwork | tail -n25
May 24 22:12:07 luke NetworkManager[947]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May 24 22:12:07 luke NetworkManager[947]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May 24 22:12:07 luke NetworkManager[947]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May 24 22:12:07 luke NetworkManager[947]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
May 24 22:12:07 luke NetworkManager[947]: <info> Activation (wlan0/wireless): access point 'WLAN-6AEE29' has security, but secrets are required.
May 24 22:12:07 luke NetworkManager[947]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
May 24 22:12:07 luke NetworkManager[947]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May 24 22:12:07 luke NetworkManager[947]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
May 24 22:12:07 luke NetworkManager[947]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
May 24 22:12:07 luke NetworkManager[947]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
May 24 22:12:07 luke NetworkManager[947]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May 24 22:12:07 luke NetworkManager[947]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May 24 22:12:07 luke NetworkManager[947]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May 24 22:12:07 luke NetworkManager[947]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
May 24 22:12:07 luke NetworkManager[947]: <info> Activation (wlan0/wireless): connection 'WLAN-6AEE29' has security, and secrets exist.  No new secrets needed.
May 24 22:12:07 luke NetworkManager[947]: <info> Config: added 'ssid' value 'WLAN-6AEE29'
May 24 22:12:07 luke NetworkManager[947]: <info> Config: added 'scan_ssid' value '1'
May 24 22:12:07 luke NetworkManager[947]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
May 24 22:12:07 luke NetworkManager[947]: <info> Config: added 'auth_alg' value 'OPEN'
May 24 22:12:07 luke NetworkManager[947]: <info> Config: added 'psk' value '<omitted>'
May 24 22:12:07 luke NetworkManager[947]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May 24 22:12:07 luke NetworkManager[947]: <info> Config: set interface ap_scan to 1
May 24 22:12:07 luke NetworkManager[947]: <info> (wlan0): supplicant interface state: inactive -> authenticating
May 24 22:12:07 luke NetworkManager[947]: <info> (wlan0): supplicant interface state: authenticating -> associating
May 24 22:12:07 luke NetworkManager[947]: <info> (wlan0): supplicant interface state: associating -> 4-way handshake
lukas@luke:~$ 


```

---

### Post by chili555 on 2014-05-24
Let's see:```
cat /etc/default/crda
cat /etc/rc.local
dmesg | grep -i -e alpha -e crda
iw reg get
```Weird!

---

### Post by cryingamer on 2014-05-24
Here we go:
```
lukas@luke:~$ cat /etc/default/crda
# Set REGDOMAIN to a ISO/IEC 3166-1 alpha2 country code so that iw(8) may set
# the initial regulatory domain setting for IEEE 802.11 devices which operate
# on this system.
#
# Governments assert the right to regulate usage of radio spectrum within
# their respective territories so make sure you select a ISO/IEC 3166-1 alpha2
# country code suitable for your location or you may infringe on local
# legislature. See `/usr/share/zoneinfo/zone.tab' for a table of timezone
# descriptions containing ISO/IEC 3166-1 alpha2 country codes.

REGDOMAIN=DE
lukas@luke:~$ cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0
lukas@luke:~$ dmesg | grep -i -e alpha -e crda
[   10.780191] cfg80211: Calling CRDA to update world regulatory domain
[   11.139387] ath: Country alpha2 being used: CN
[   11.144045] cfg80211: Calling CRDA for country: CN
[   11.208709] cfg80211: Calling CRDA for country: DE
lukas@luke:~$ iw reg get
country DE:
    (2400 - 2483 @ 40), (N/A, 20)
    (5150 - 5250 @ 40), (N/A, 20), NO-OUTDOOR
    (5250 - 5350 @ 40), (N/A, 20), NO-OUTDOOR, DFS
    (5470 - 5725 @ 40), (N/A, 26), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR
lukas@luke:~$
```

Some random times,if i try to connect directly to my router, i can see just the title of the configuration app of the router but it doesn't load.

---

### Post by chili555 on 2014-05-26
I think it takes a reboot to get the CRDA to stick. Please do and then:```
dmesg | grep -i -e alpha -e crda
```

---

### Post by cryingamer on 2014-05-26
It seems like i can connect now via wlan without problem. But when i wanto to call a Website or my Router Config App then still nothing happens (if this could be useful).
Here the output:
```
lukas@luke:~$ dmesg | grep -i -e alpha -e crda
[   10.870745] cfg80211: Calling CRDA to update world regulatory domain
[   11.220251] ath: Country alpha2 being used: CN
[   11.400479] cfg80211: Calling CRDA for country: CN
[   12.073448] cfg80211: Calling CRDA for country: DE
lukas@luke:~$
```

---

### Post by Hadaka on 2014-05-26
Hi, I think the CN setting is what is blocking the web access
lets try to delete that and see if it makes a difference, please do
```
sudo sed -i 's/REGDOMAIN=CN/REGDOMAIN=/' /etc/default/crda
```
BOOT 
then do and post
```
dmesg | grep -i -e alpha -e crda
```
```
iw reg get
cat /etc/default/crda
```
thanks

---

### Post by cryingamer on 2014-05-26
Here we go:
```
lukas@luke:~$ dmesg | grep -i -e alpha -e crda
[   10.958045] cfg80211: Calling CRDA to update world regulatory domain
[   11.302126] ath: Country alpha2 being used: CN
[   11.307449] cfg80211: Calling CRDA for country: CN
[   11.364562] cfg80211: Calling CRDA for country: DE
lukas@luke:~$ iw reg get
country DE:
    (2400 - 2483 @ 40), (N/A, 20)
    (5150 - 5250 @ 40), (N/A, 20), NO-OUTDOOR
    (5250 - 5350 @ 40), (N/A, 20), NO-OUTDOOR, DFS
    (5470 - 5725 @ 40), (N/A, 26), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR
lukas@luke:~$ cat /etc/default/crda
# Set REGDOMAIN to a ISO/IEC 3166-1 alpha2 country code so that iw(8) may set
# the initial regulatory domain setting for IEEE 802.11 devices which operate
# on this system.
#
# Governments assert the right to regulate usage of radio spectrum within
# their respective territories so make sure you select a ISO/IEC 3166-1 alpha2
# country code suitable for your location or you may infringe on local
# legislature. See `/usr/share/zoneinfo/zone.tab' for a table of timezone
# descriptions containing ISO/IEC 3166-1 alpha2 country codes.

REGDOMAIN=DE
lukas@luke:~$ 
```

---

### Post by Hadaka on 2014-05-26
let's try setting both to null and see if that clears CN
please do
```
sudo iw reg set 00
sudo sed -i 's/REGDOMAIN=DE/REGDOMAIN=/' /etc/default/crda
```
BOOT
then post
```
iw reg get
cat /etc/default/crda
dmesg | grep -i -e alpha -e crda
```

---

### Post by cryingamer on 2014-05-26
Here we go:
```
lukas@luke:~$ iw reg get
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
lukas@luke:~$ cat /etc/default/crda
# Set REGDOMAIN to a ISO/IEC 3166-1 alpha2 country code so that iw(8) may set
# the initial regulatory domain setting for IEEE 802.11 devices which operate
# on this system.
#
# Governments assert the right to regulate usage of radio spectrum within
# their respective territories so make sure you select a ISO/IEC 3166-1 alpha2
# country code suitable for your location or you may infringe on local
# legislature. See `/usr/share/zoneinfo/zone.tab' for a table of timezone
# descriptions containing ISO/IEC 3166-1 alpha2 country codes.

REGDOMAIN=
lukas@luke:~$ dmesg | grep -i -e alpha -e crda
[   11.049234] cfg80211: Calling CRDA to update world regulatory domain
[   11.379378] ath: Country alpha2 being used: CN
[   11.384317] cfg80211: Calling CRDA for country: CN
[   46.049464] cfg80211: Calling CRDA to update world regulatory domain
[   89.113778] cfg80211: Calling CRDA to update world regulatory domain
lukas@luke:~$ 
```

---

### Post by Hadaka on 2014-05-26
hi, here is a link related to your REGDOMAIN issue
[http://wireless.kernel.org/en/users/Drivers/ath](http://wireless.kernel.org/en/users/Drivers/ath)

it is alot of reading but allows you to get an idea of how this works and what may be going on.
toward the bottom of the page is another link about "hidden" ath requests. I have no idea how
you came to have CN written to your EEPROM on your wireless card. Given the country code all
reasons i can think of are not good ones. Please do and post this..
```
dmesg | grep ath | egrep "regdomain|Country"
```
If this returns CN and not 00, I would consider getting a new wireless card. I dont have the skills
or knowledge to get into the EEPROM code level and make changes.

---

### Post by cryingamer on 2014-05-28
It seems like ive got a problem:
```
lukas@luke:~$ dmesg | grep ath | egrep "regdomain|Country"
[   11.451607] ath: EEPROM regdomain: 0x809c
[   11.451613] ath: Country alpha2 being used: CN
lukas@luke:~$
```
But whats about the ethernet connection which still doesnt work? What should i do with it?

---

### Post by chili555 on 2014-05-28
Let's see if we can coax the ethernet to life. So we don't have any conflicts, use the switch or key combination to disable the wireless. 

Now hook up the ethernet and see what if anything happens:```
lsmod | grep r8169
```If the driver is not loaded, load it:```
sudo modprobe r8169
```Is an interface created, ideally eth0?```
ifconfig
```What do the logs report?```
dmesg | grep -e r8169 -e eth0
```

---

### Post by cryingamer on 2014-05-28
```
lukas@luke:~$ lsmod | grep r8169
r8169                  67581  0 
mii                    13934  1 r8169
lukas@luke:~$ sudo modprobe r8169
lukas@luke:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 74:d4:35:53:4e:88  
          inet6 addr: fe80::76d4:35ff:fe53:4e88/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:47 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:60 (60.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:39 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4065 (4.0 KB)  TX bytes:4065 (4.0 KB)

lukas@luke:~$ dmesg | grep -e -r8169 -e eth0
[    1.268821] r8169 0000:05:00.0 eth0: RTL8168evl/8111evl at 0xffffc90000c78000, 74:d4:35:53:4e:88, XID 0c900800 IRQ 73
[    1.268823] r8169 0000:05:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[   12.021066] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.663810] r8169 0000:05:00.0 eth0: link down
[   19.663864] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.664128] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.915381] r8169 0000:05:00.0 eth0: link up
[   21.915389] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   22.318161] r8169 0000:05:00.0 eth0: link down
[   24.015566] r8169 0000:05:00.0 eth0: link up
[   84.018370] NETDEV WATCHDOG: eth0 (r8169): transmit queue 0 timed out
[   84.024886] r8169 0000:05:00.0 eth0: link up
lukas@luke:~$ 
```

---

### Post by chili555 on 2014-05-28
This is an old trick that sometimes helps:```
sudo ethtool -s eth0 speed 100 duplex full autoneg off
sudo service network-manager restart
```Now does it connect? If so, we'll amend one file and make it persistent.

---

### Post by cryingamer on 2014-06-01
it doesnt work.

---

### Post by jeremy31 on 2014-06-01
This thread is making my head hurt.  Cryingamer, have you gone into settings/time and date to verify the correct timezone?

---

### Post by cryingamer on 2014-06-08
Yes of course i did. And what does the time settings change on my wireless card network settings?

---

### Post by jeremy31 on 2014-06-08
> **cryingamer said:**
> Yes of course i did. And what does the time settings change on my wireless card network settings?

I was trying to think where it came up with China.  Have you hacked your router, or perhaps buy it on ebay

---

### Post by cryingamer on 2014-06-09
Nope, Standard Telecom Router.

---

### Post by cryingamer on 2014-07-10
i finally solved this problem and it was the dumbest thing that ever happend to me,i think. I just downloaded an driver from the realtek website and now it works perfect. BUT when i update ubuntu and dont disable network updates that rewrite this driver then it wont work again and i have to reinstall the downloaded driver. 
Thanks to everyone who posted something in here and wanted to help me.

---

