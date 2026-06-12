---
title: "Broadcom BCM43142: Ubuntu 14.04, wifi connectivity issues"
date: 2014-08-22
forum: Networking &amp; Wireless
---

### Post by zlyspl on 2014-08-22
Having problems with my wifi connecting to any websites that require username and passwords including ubuntu forums. Also having problems with yahoo, hotmail, gmail, youtube etc.,etc.. If anyone can figure out a solution, please let me know. Thanks in advance.


```

======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


Superfristic 3.13.0-34-generic x86_64,  Ubuntu 14.04.1 LTS, trusty


CPU    : Intel(R) Core(TM) i5-4200H CPU @ 2.80GHz
Memory : 3836 MB
Uptime : 09:24:14 up  1:19,  2 users,  load average: 0.45, 0.40, 0.49




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


03:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
	Subsystem: Lite-On Communications Inc Device [11ad:6605]
	Kernel driver in use: wl
--
04:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
	Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
	Kernel driver in use: r8169




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:57b4 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 04ca:2006 Lite-On Technology Corp. 
Bus 001 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11abg  ESSID:"ssbs-316"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC C-01 ssbs-316>   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          




rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface               Soft blocked  Hard blocked
0: asus-wlan: Wireless LAN        no            no
1: asus-bluetooth: Bluetooth      no            no
2: phy0: Wireless LAN             no            no
3: brcmwl-0: Wireless LAN         no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


rt61pci                32115  0 
rt2x00pci              13287  1 rt61pci
rt2x00mmio             13603  1 rt61pci
rt2x00lib              55307  3 rt61pci,rt2x00pci,rt2x00mmio
mac80211              630653  2 rt2x00lib,rt2x00pci
eeprom_93cx6           13344  1 rt61pci
crc_itu_t              12707  1 rt61pci
wl                   4207846  0 
asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
lib80211               14381  2 wl,lib80211_crypt_tkip
cfg80211              484040  3 wl,mac80211,rt2x00lib
mxm_wmi                13021  1 nouveau
wmi                    19177  3 mxm_wmi,nouveau,asus_wmi
video                  19476  3 i915,nouveau,asus_wmi




module parameters ~~~~~~~~~~~~~~~~~~


asus_nb_wmi   (1): wapf=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rt61pci       (1): nohwcrypt=Y
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: connected (global)
=====================o=============o========o=====  ========o=========o===========o==============o====  =======
 Interface & ID      | Type        | Driver | State       | Default | Speed     | Support      | HW Addr   
=====================o=============o========o=====  ========o=========o===========o==============o====  =======
 eth0                | Wired       | r8169  | unavailable | no      |           |              | <MAC eth0>
---------------------+-------------+--------+-------------+---------+-----------+--------------+-----------
 wlan0  [ssbs-316 1] | 802.11 WiFi | wl     | connected   | yes     | 19 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>


    IP-COM:          Infra, <MAC C-NA IP-COM 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 45
    *ssbs-316:       Infra, <MAC C-01 ssbs-316>, Freq 2412 MHz, Rate 54 Mb/s, Strength 71 WPA WPA2


    Address:         192.168.1.126
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             202.96.209.133
    DNS:             202.96.209.5
---------------------+-------------+--------+-------------+---------+-----------+--------------+-----------




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


ssbs-316             : ssid=ssbs-316 | ipv4=auto | ipv6=auto 
ssbs-316 1           : ssid=ssbs-316 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~


nameserver 127.0.1.1




Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 tun0
10.119.8.0      0.0.0.0         255.255.248.0   U     0      0        0 tun0
69.50.200.241   192.168.1.1     255.255.255.255 UGH   0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : zh_CN.UTF-8)
country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS




iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     26 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)
          Channel 36 (5.18 GHz)
          Channel 38 (5.19 GHz)
          Channel 40 (5.2 GHz)
          Channel 42 (5.21 GHz)
          Channel 44 (5.22 GHz)
          Channel 46 (5.23 GHz)
          Channel 48 (5.24 GHz)
          Channel 149 (5.745 GHz)
          Channel 153 (5.765 GHz)
          Channel 157 (5.785 GHz)
          Channel 161 (5.805 GHz)
          Channel 165 (5.825 GHz)


          Current Frequency:2.412 GHz (Channel 1)




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 ssbs-316>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"ssbs-316"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK




blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[rt61pci]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/rt2x00/rt61pci.ko
firmware:       rt2661.bin
firmware:       rt2561s.bin
firmware:       rt2561.bin
version:        2.3.0
srcversion:     CF4E6C5B3BC64AAF193A5A5
depends:        rt2x00lib,rt2x00mmio,rt2x00pci,eeprom_93cx6,crc-itu-t
parm:           nohwcrypt:Disable hardware encryption. (bool)


[rt2x00pci]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
version:        2.3.0
srcversion:     9B9D0D0D0F8571AF43705FD
depends:        rt2x00lib,mac80211


[rt2x00mmio]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
version:        2.3.0
srcversion:     07530604F5CE4EF69872C75
depends:        rt2x00lib


[rt2x00lib]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
version:        2.3.0
srcversion:     CC69EE39E7D673974A21C0A
depends:        mac80211,cfg80211


[mac80211]
filename:       /lib/modules/3.13.0-34-generic/kernel/net/mac80211/mac80211.ko
srcversion:     8ADA881D348148A3358334C
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[eeprom_93cx6]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/misc/eeprom/eeprom_93cx6.ko
version:        1.0
srcversion:     215D8C1284A3C33B4A5A1C5
depends:        


[crc_itu_t]
filename:       /lib/modules/3.13.0-34-generic/kernel/lib/crc-itu-t.ko
srcversion:     57DB184B6F722970048006C
depends:        


[wl]
filename:       /lib/modules/3.13.0-34-generic/updates/dkms/wl.ko
srcversion:     FF25FE784DC6BDFF69DAFCB
depends:        cfg80211,lib80211
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string


[asus_nb_wmi]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/platform/x86/asus-nb-wmi.ko
srcversion:     67514DF02FC4A206C47D0F5
depends:        asus-wmi
parm:           wapf:WAPF value (uint)


[asus_wmi]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/platform/x86/asus-wmi.ko
srcversion:     222BD5E26B3EE82CC433FF2
depends:        sparse-keymap,wmi,video


[lib80211]
filename:       /lib/modules/3.13.0-34-generic/kernel/net/wireless/lib80211.ko
srcversion:     84DEF767F03D28E373F18E5
depends:        


[cfg80211]
filename:       /lib/modules/3.13.0-34-generic/kernel/net/wireless/cfg80211.ko
srcversion:     E786D076B61F97809B04B64
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[mxm_wmi]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/platform/x86/mxm-wmi.ko
srcversion:     62CBD37DE87DF0C4CD7FBA3
depends:        wmi


[wmi]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


[video]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/acpi/video.ko
srcversion:     274A2250DEAB415D412A67C
depends:        
parm:           brightness_switch_enabled:bool
parm:           allow_duplicates:bool
parm:           use_native_backlight:int




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x14e4:0x4365 (wl)
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


BOOT_IMAGE=/vmlinuz-3.13.0-34-generic.efi.signed root=UUID=b0aecd0f-5d9d-466c-a221-eb72a52eb991 ro quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    0.500135] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.500339] audit: initializing netlink socket (disabled)
[    0.649695] wmi: Mapper loaded
[    0.661312] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    6.646292] asus_wmi: ASUS WMI generic driver loaded
[    6.795584] asus_wmi: Initialization: 0x1
[    6.795620] asus_wmi: BIOS WMI version: 7.9
[    6.795661] asus_wmi: SFUN value: 0x4a0877
[    6.796493] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input21
[    6.802033] asus_wmi: Backlight controlled by ACPI video driver
[    6.881936] wl: module license 'MIXED/Proprietary' taints kernel.
[    6.883627] wl: module verification failed: signature and/or  required key missing - tainting kernel
[    6.913160] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[    7.049740] wlan0: Broadcom BCM4365 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)
[   16.548229] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[ 4749.455165] ERROR @wl_dev_intvar_get : error (-1)
[ 4749.455172] ERROR @wl_cfg80211_get_tx_power : error (-1)


	======== Done ========

```

---

### Post by zlyspl on 2014-08-24
Can someone help me with this? I need this laptop working for work. Thanks

---

### Post by chili555 on 2014-08-24
Why is *rt61pci* loading? > rt61pci                32115  0 
rt2x00pci              13287  1 rt61pci
rt2x00mmio             13603  1 rt61pci
rt2x00lib              55307  3 rt61pci,rt2x00pci,rt2x00mmio
mac80211              630653  2 rt2x00lib,rt2x00pci
eeprom_93cx6           13344  1 rt61pci
crc_itu_t              12707  1 rt61pci
wl                   4207846  0 
asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
lib80211               14381  2 wl,lib80211_crypt_tkip
cfg80211              484040  3 wl,mac80211,rt2x00lib
mxm_wmi                13021  1 nouveau
wmi                    19177  3 mxm_wmi,nouveau,asus_wmi
video                  19476  3 i915,nouveau,asus_wmi
Is it called in /etc/modules? ```
cat /etc/modules
```Anything you'd like to confess to the doctor under strict patient-linuxian confidentiality?> Having problems with my wifi connecting to any websites that require username and passwords including ubuntu forums. Also having problems with yahoo, hotmail, gmail, youtube etc.,etc.. What exactly happens or not?

Is the firewall interfering?```
sudo status ufw
```

---

### Post by zlyspl on 2014-08-24
Hmm, I am not sure why r61pci is loading. in cat /etc/modules, the only thing listed are lp and rtc.

I would like to confess that I am using Broadcom 802.11 Linux STA wireless drivers from bcmwl-kernel source even though I am not sure if it is compatible with my wifi. However if I do not use this, I unable to connect to any wifi.

When I try to connect to hotmail, enter my usrname and password, I keep getting ERR_Connection_RESET. When I try to login to ubuntu, I get ERR_EMPTY_RESPONSE, when I go to yahoo.com website, it takes forever to load and when it finish, there is broken flash and all links are on the left hand side.

---

### Post by chili555 on 2014-08-24
I think that *rt61pci* and its conflicting 80211 system is part of the problem. We need to find out how it is getting loaded and stop it and reboot and then, if needed, troubleshoot from there. May we see:```
ls /etc/modprobe.d
cat /etc/rc.local
```>  I am using Broadcom 802.11 Linux STA wireless drivers from bcmwl-kernel source even though I am not sure if it is compatible with my wifi.It is quite correct.

Thanks.

---

### Post by zlyspl on 2014-08-24
```
[TABLE="width: 100%"]
[TR]
[TD="class: body"]ls /etc/modprobe.d
alsa-base.conf               blacklist-watchdog.conf
blacklist-ath_pci.conf       dkms.conf
blacklist-bcm43.conf         fbdev-blacklist.conf
blacklist.conf               iwlwifi.conf
blacklist-firewire.conf      mlx4.conf
blacklist-framebuffer.conf   nvidia-340_hybrid.conf
blacklist-modem.conf         [COLOR=#0000ff]nvidia-graphics-drivers.conf[/COLOR]
[COLOR=#0000ff]blacklist-oss.conf[/COLOR]           vmwgfx-fbdev.conf
blacklist-rare-network.conf


cat /etc/rc.local
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
[/TD]
[/TR]
[/TABLE]

```

This is what I get from ls /etc/modprobe.d and cat /etc/rc.local

Also when I try to reply to posts here in Ubuntu, even though I typed in a lot more than 1 char's using my laptop, it still pops up saying I need to type more than 1 char to post. Sometimes when I post with code quotes, the code does not appear in the code box just a blank code box shows.

---

### Post by varunendra on 2014-08-25
> **zlyspl said:**
> Sometimes when I post with code quotes, the code does not appear in the code box just a blank code box shows.

Happening here with me as well since this morning (now is 8:10 pm). This is most probably happening due to the server sync issue that we were notified about a few days ago - something like "..in the process of changing server layout, users may experience a few minor glitches/problems due to the delay in the syncing of the two forum servers - bilberry and lingonberry.."

There are other problems like unintentional multi-posting as well, I hope it's all just temporary issue that will solve itself as soon as the forum layout change is finished.

By the way, posting just to keep track of the original issue about wifi, not to discuss the above ones. ;)

---

### Post by chili555 on 2014-08-25
I see no other reasons that rt61pci is loading. Is there a listing for it here?```
cat /etc/udev/rules.d/70-persistent-net.rules
```Something like:```
# PCI device 0x8086:0xblah [COLOR="#FF0000"](rt61pci)[/COLOR]
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="58:94:6b:99:55:a0", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
```If so, I suggest you remove the file and immediately reboot:```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```Then check again:```
lsmod | grep -e rt61pci -e rt2x
```If they are all gone now, how is the wireless working?

---

### Post by zlyspl on 2014-08-25
I did as you asked, deleted the file and rebooted the computer.

Not getting anything from : ```
[COLOR=#000000][FONT=Ubuntu Mono]lsmod | grep -e rt61pci -e rt2x[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]

Typed in [/FONT][/COLOR]```
[COLOR=#000000][FONT=Ubuntu Mono]cat /etc/udev/rules.d/70-persistent-net.rules[/FONT][/COLOR]
``` again and I get

```
[COLOR=#000000][FONT=lucida Grande]PCI device 0x10ec:0x8168 (r8169)[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="54:a0:50:0b:8b:6d", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"[/FONT][/COLOR]

[COLOR=#000000][FONT=lucida Grande]PCI device 0x14e4:0x4365 (wl)[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="18:cf:5e:bf:0c:4d", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"[/FONT][/COLOR]
```

Still encountering the same problems

---

### Post by varunendra on 2014-08-25
I was surprised to see **rt61pci** myself, since there is no hint in the usual places (covered in the script report) that are used to load a module forcibly. Does it load everytime automatically or did you load it manually? Maybe following some irrelevant guide just before generating that report?

I suggest you reboot, then without doing anything fancy, simply run -
```
lsmod | grep rt6
```
Does it (rt61pci) show up again? If not, please generate a fresh wireless_script report and post it here. If it does show up, take a look at syslog for hints on why is it loading -
```
grep rt6 /var/log/syslog
```

And as an attempt to get rid of it, try to blacklist it -
```
echo "blacklist rt61pci" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot after this, and see if the wifi works now.

---

### Post by zlyspl on 2014-08-26
Checked by using ```
lsmod | grep rt6
``` nothing shows up

Generated a new report 

```
[COLOR=#000000][FONT=lucida Grande]======== Wireless-Info START ========[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]System-Info ~~~~~~~~~~~~~~~~~~~~~~~~[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]Superfristic 3.13.0-34-generic x86_64,  Ubuntu 14.04.1 LTS, trusty[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]CPU    : Intel(R) Core(TM) i5-4200H CPU @ 2.80GHz[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]Memory : 3836 MB[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]Uptime : 13:35:48 up  5:09,  2 users,  load average: 0.28, 0.35, 0.28[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]03:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]	Subsystem: Lite-On Communications Inc Device [11ad:6605][/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]	Kernel driver in use: wl[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]--[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]04:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]	Subsystem: ASUSTeK Computer Inc. Device [1043:200f][/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]	Kernel driver in use: r8169[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]Bus 001 Device 005: ID 0bda:57b4 Realtek Semiconductor Corp.[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]Bus 001 Device 004: ID 04ca:2006 Lite-On Technology Corp.[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]Bus 001 Device 003: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]Bus 001 Device 002: ID 154b:005b PNY[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]wlan0     IEEE 802.11abg  ESSID:"ssbs-316"  [/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC C-01 ssbs-316>  [/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]          Retry  long limit:7   RTS thr:off   Fragment thr:off[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]          Power Management:off[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]         [/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]      Interface               Soft blocked  Hard blocked[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]0: asus-wlan: Wireless LAN        no            no[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]1: asus-bluetooth: Bluetooth      no            no[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]2: phy0: Wireless LAN             no            no[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]3: brcmwl-0: Wireless LAN         no            no[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]wl                   4207846  0[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]asus_nb_wmi            16990  0[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]asus_wmi               24191  1 asus_nb_wmi[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]sparse_keymap          13948  1 asus_wmi[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]mxm_wmi                13021  0[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]lib80211               14381  2 wl,lib80211_crypt_tkip[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]cfg80211              484040  1 wl[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]wmi                    19177  2 mxm_wmi,asus_wmi[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]video                  19476  2 i915,asus_wmi[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]module parameters ~~~~~~~~~~~~~~~~~~[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]asus_nb_wmi   (1): wapf=0[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]wmi           (2): debug_dump_wdg=N | debug_event=N[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]State: connected (global)[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]=====================o=============o========o=====  ========o=========o===========o==============o====  =======[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande] Interface & ID      | Type        | Driver | State       | Default | Speed     | Support      | HW Addr  [/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]=====================o=============o========o=====  ========o=========o===========o==============o====  =======[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande] eth0                | Wired       | r8169  | unavailable | no      |           |              | <MAC eth0>[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]---------------------+-------------+--------+-------------+---------+-----------+--------------+-----------[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande] wlan0  [ssbs-316 1] | 802.11 WiFi | wl     | connected   | yes     | 72 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]    *ssbs-316:       Infra, <MAC C-01 ssbs-316>, Freq 2412 MHz, Rate 54 Mb/s, Strength 63 WPA WPA2[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]    SSBS:            Infra, <MAC C-NA SSBS 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA2[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]    IP-COM:          Infra, <MAC C-02 IP-COM>, Freq 2437 MHz, Rate 54 Mb/s, Strength 35[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]    IP-COM:          Infra, <MAC C-NA IP-COM 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 14[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]    Address:         192.168.1.126[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]    Prefix:          24 (255.255.255.0)[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]    Gateway:         192.168.1.1[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]    DNS:             202.96.209.133[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]    DNS:             202.96.209.5[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]---------------------+-------------+--------+-------------+---------+-----------+--------------+-----------[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]NetworkManager.state ~~~~~~~~~~~~~~~[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande][main][/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]NetworkingEnabled=true[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]WirelessEnabled=true[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]WWANEnabled=true[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]WimaxEnabled=true[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]NetworkManager.conf ~~~~~~~~~~~~~~~~[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande][main][/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]plugins=ifupdown,keyfile,ofono[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]dns=dnsmasq[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande][ifupdown][/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]managed=false[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]ssbs-316             : ssid=ssbs-316 | ipv4=auto | ipv6=auto[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]ssbs-316 1           : ssid=ssbs-316 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]TP-LINK_wwt          : ssid=TP-LINK_wwt | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]# interfaces(5) file used by ifup(8) and ifdown(8)[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]auto lo[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]iface lo inet loopback[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]nameserver 127.0.1.1[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]Kernel IP routing table[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]Destination     Gateway         Genmask         Flags Metric Ref    Use Iface[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 tun0[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]10.119.8.0      0.0.0.0         255.255.248.0   U     0      0        0 tun0[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]69.50.200.241   192.168.1.1     255.255.255.255 UGH   0      0        0 wlan0[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande](Region : en_US.UTF-8)[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]country 00:[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]	(2402 - 2472 @ 40), (3, 20)[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]wlan0     26 channels in total; available frequencies :[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]          Channel 01 (2.412 GHz) - 14 (2.484 GHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]          Channel 36 (5.18 GHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]          Channel 38 (5.19 GHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]          Channel 40 (5.2 GHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]          Channel 42 (5.21 GHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]          Channel 44 (5.22 GHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]          Channel 46 (5.23 GHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]          Channel 48 (5.24 GHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]          Channel 149 (5.745 GHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]          Channel 153 (5.765 GHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]          Channel 157 (5.785 GHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]          Channel 161 (5.805 GHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]          Channel 165 (5.825 GHz)[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]          Current Frequency:2.412 GHz (Channel 1)[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]wlan0     Scan completed :[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]          Cell 01 - Address: <MAC C-01 ssbs-316>[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]                    Channel:1[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]                    Frequency:2.412 GHz (Channel 1)[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]                    Quality=50/70  Signal level=-60 dBm  [/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]                    Encryption key:on[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]                    ESSID:"ssbs-316"[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]                              9 Mb/s; 12 Mb/s; 18 Mb/s[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]                    Mode:Master[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]                    Extra:tsf=0000000000000000[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]                    Extra: Last beacon: 96ms ago[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]                    IE: IEEE 802.11i/WPA2 Version 1[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]                        Group Cipher : CCMP[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]                        Pairwise Ciphers (1) : CCMP[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]                        Authentication Suites (1) : PSK[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]                    IE: WPA Version 1[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]                        Group Cipher : CCMP[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]                        Pairwise Ciphers (1) : CCMP[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]                        Authentication Suites (1) : PSK[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]          Cell 02 - Address: <MAC C-02 IP-COM>[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]                    Channel:6[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]                    Frequency:2.437 GHz (Channel 6)[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]                    Quality=36/70  Signal level=-74 dBm  [/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]                    Encryption key:off[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]                    ESSID:"IP-COM"[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]                              18 Mb/s; 36 Mb/s; 54 Mb/s[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]                    Mode:Master[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]                    Extra:tsf=0000000000000000[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]                    Extra: Last beacon: 96ms ago[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]          Cell 03 - Address: <MAC C-03 IP-COM>[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]                    Channel:6[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]                    Frequency:2.437 GHz (Channel 6)[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]                    Quality=20/70  Signal level=-90 dBm  [/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]                    Encryption key:off[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]                    ESSID:"IP-COM"[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]                              18 Mb/s; 36 Mb/s; 54 Mb/s[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]                    Mode:Master[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]                    Extra:tsf=0000000000000000[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]                    Extra: Last beacon: 96ms ago[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande][/etc/modprobe.d/blacklist-ath_pci.conf][/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]blacklist ath_pci[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande][/etc/modprobe.d/blacklist-bcm43.conf][/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]blacklist b43[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]blacklist b43legacy[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]blacklist ssb[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]blacklist brcm80211[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]blacklist brcmfmac[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]blacklist brcmsmac[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]blacklist bcma[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande][wl][/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]filename:       /lib/modules/3.13.0-34-generic/updates/dkms/wl.ko[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]srcversion:     FF25FE784DC6BDFF69DAFCB[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]depends:        cfg80211,lib80211[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]parm:           wl_txq_thresh:int[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]parm:           oneonly:int[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]parm:           piomode:int[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]parm:           instance_base:int[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]parm:           nompc:int[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]parm:           intf_name:string[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande][asus_nb_wmi][/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/platform/x86/asus-nb-wmi.ko[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]srcversion:     67514DF02FC4A206C47D0F5[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]depends:        asus-wmi[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]parm:           wapf:WAPF value (uint)[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande][asus_wmi][/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/platform/x86/asus-wmi.ko[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]srcversion:     222BD5E26B3EE82CC433FF2[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]depends:        sparse-keymap,wmi,video[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande][mxm_wmi][/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/platform/x86/mxm-wmi.ko[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]srcversion:     62CBD37DE87DF0C4CD7FBA3[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]depends:        wmi[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande][lib80211][/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]filename:       /lib/modules/3.13.0-34-generic/kernel/net/wireless/lib80211.ko[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]srcversion:     84DEF767F03D28E373F18E5[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]depends:        [/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande][cfg80211][/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]filename:       /lib/modules/3.13.0-34-generic/kernel/net/wireless/cfg80211.ko[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]srcversion:     E786D076B61F97809B04B64[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]depends:        [/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande][wmi][/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/platform/x86/wmi.ko[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]srcversion:     CED5410F008DC70DF5F064B[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]depends:        [/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]parm:           debug_event:Log WMI Events [0/1] (bool)[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande][video][/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/acpi/video.ko[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]srcversion:     274A2250DEAB415D412A67C[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]depends:        [/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]parm:           brightness_switch_enabled:bool[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]parm:           allow_duplicates:bool[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]parm:           use_native_backlight:int[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]# PCI device 0x10ec:0x8168 (r8169)[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]# PCI device 0x14e4:0x4365 (wl)[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]Custom files/entries ~~~~~~~~~~~~~~~[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]/etc/modules        : Default[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]/etc/rc.local       : Default[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]/etc/modprobe.d     : Not Default[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]/etc/pm/(cnf|pw|sl) : Default[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande][/etc/modprobe.d][/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]iwlwifi.conf      : remove iwlwifi \[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]                    && /sbin/modprobe -r mac80211[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]mlx4.conf         : softdep mlx4_core post: mlx4_en[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]Kernel boot line ~~~~~~~~~~~~~~~~~~~[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]BOOT_IMAGE=/vmlinuz-3.13.0-34-generic.efi.signed root=UUID=b0aecd0f-5d9d-466c-a221-eb72a52eb991 ro quiet splash vt.handoff=7[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande][    0.493240] microcode: Microcode Update Driver: v2.00 <[EMAIL="tigran@aivazian.fsnet.co.uk"]tigran@aivazian.fsnet.co.uk[/EMAIL]>, Peter Oruba[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande][    0.493446] audit: initializing netlink socket (disabled)[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande][    0.598823] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande][    5.746389] wmi: Mapper loaded[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande][    6.782241] asus_wmi: ASUS WMI generic driver loaded[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande][    6.853613] asus_wmi: Initialization: 0x1[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande][    6.853651] asus_wmi: BIOS WMI version: 7.9[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande][    6.853695] asus_wmi: SFUN value: 0x4a0877[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande][    6.854466] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input16[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande][    6.859654] asus_wmi: Backlight controlled by ACPI video driver[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande][    7.574154] wl: module license 'MIXED/Proprietary' taints kernel.[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande][    7.575820] wl: module verification failed: signature and/or  required key missing - tainting kernel[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande][    7.606285] INFO @wl_cfg80211_attach : Registered CFG80211 phy[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande][    7.735484] wlan0: Broadcom BCM4365 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande][   17.418269] Bluetooth: BNEP (Ethernet Emulation) ver 1.3[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande][12393.715857] ERROR @wl_dev_intvar_get : error (-1)[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande][12393.715860] ERROR @wl_cfg80211_get_tx_power : error (-1)[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]	======== Done ========[/FONT][/COLOR]

```

Still having the same issues.

---

### Post by varunendra on 2014-08-26
Okay, so it seems to me that you probably loaded rt61pci manually last time.

Are you having the said problem with all routers/access-points or just the one you are currently using? Your current one, "ssbs-316", is using WPA/WPA2 mixed mode and many Linux drivers can have problems with this combination. Please log into your router/AP, and change it to pure WPA2-PSK with AES (CCMP). Also fix the channel to 1 or 11 if it is set to "auto". Save the changes and reboot the router. Now try to connect and browse/log-into the problematic sites. Is it any better now?

If not, please post back the output of -
```
dmesg | tail -40
```
..when it fails to login.

Is the browsing otherwise fine?

---

### Post by zlyspl on 2014-08-26
Yeah... you hit the bull's eye. Apparently it is the router at work screwing with me. Unfortunately, I don't have the authority to change my office's router settings. I could ask my IT although it would be very unlikely they be willing to change to WPA2-PSK with AES (CCMP).


Is there any other way of fixing this problem on my end instead of fixing it externally? Another question, I would have the same problems using SSBS-316 with a hardwire connection instead of wifi right? Since they are using MIX WPA/WPA2?

---

### Post by varunendra on 2014-08-26
> **zlyspl said:**
> Is there any other way of fixing this problem on my end instead of fixing it externally?
The proprietary driver you are using doesn't provide many options to alter or optimize the way it works. There are a few other things that we can try internally, but they don't deal with the encryption settings.

The things you can try are -
[indent]**1)** Set "IPv6" in Network Manager to "Ignore". It can sometimes improve the performance in slow connection problems.

**2)** Explicitly set the country code for regdomain settings, and hope the router starts liking the driver -
```
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda
sudo iw reg set US
```
If you are in a country other than US, replace 'US' with the appropriate country code. Basically, you have to match the country code with that in the router, and when we can't check that setting in the router, we assume it must be same as the country it was sold in. To find out the country code for your country, please refer to this table : [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Decoding_table](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Decoding_table)

**3)** See if you have more than one version of the driver available -
```
apt-cache show bcmwl-kernel-source | grep Version
```
If you see more than one version, we may try the other one.

**4)** You may try different DNS servers that are faster/more efficient for your area. To change the DNS servers, you need to change the "Method" under "IPv4" in Network Manager from "Automatic (DHCP)" to "Automatic (DHCP) address only". Choosing this option will make the "DNS Servers" field editable, where you can define your preferred DNS servers. An example of what to put in the "DNS Servers" field is -
```
8.8.8.8, 8.8.4.4
```
..where 8.8.8.8 and 8.8.4.4 are Google's open DNS servers. Save and close the settings, then disconnect/reconnect for the change to take effect.[/indent]

> Another question, I would have the same problems using SSBS-316 with a hardwire connection instead of wifi right? Since they are using MIX WPA/WPA2?
No, the encryption settings are only meant for wireless communication. The wired connection is not affected by wireless encryption settings, so it should work right away. If you face the _same_ problems with a wired connection too, then the problem is almost certainly the firewall settings of your office.

---

### Post by zlyspl on 2014-08-27
> **varunendra said:**
> 
No, the encryption settings are only meant for wireless communication. The wired connection is not affected by wireless encryption settings, so it should work right away. If you face the _same_ problems with a wired connection too, then the problem is almost certainly the firewall settings of your office.


Got my IT to install a hardwire, it is even worse than the wifi unless I haven't installed the drivers for my Asus ethernet card correctly? If it is the firewall settings, what would the IT have to change?

---

### Post by varunendra on 2014-08-27
Let's first see your wired connection status. Please show us the outputs of -
```
sudo lshw -C network
ifconfig
```

Unless the problem is 'exactly same', or at least reasonably similar, we can't blame it on the firewall.

---

### Post by zlyspl on 2014-08-27
Found this on another solved link and I was wondering if this driver would work better? The person got a [COLOR=#000000] Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
[/COLOR]The link to the post is [http://ubuntuforums.org/showthread.php?t=2224920](http://ubuntuforums.org/showthread.php?t=2224920)

```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get update
sudo apt-get install linux-firmware-nonfree
```

---

### Post by varunendra on 2014-08-27
Whenever we have even the slightest hint that the native b43 driver *might* work, we try that first. As far as I know, your card is not yet supported by that. So the thread you found is useless, unless the b43 driver has been updated beyond my knowledge.

---

### Post by chili555 on 2014-08-27
> **varunendra said:**
> Whenever we have even the slightest hint that the native b43 driver *might* work, we try that first. As far as I know, your card is not yet supported by that. So the thread you found is useless, unless the b43 driver has been updated beyond my knowledge.Your device is:> Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)Per the sticky, the correct driver is bcmwl-kernel-source, which you have installed now.

---

### Post by zlyspl on 2014-08-27
This is what I get for [COLOR=#000000][FONT=Ubuntu Mono]sudo lshw -C network
[/FONT][/COLOR]
```
[COLOR=#000000][FONT=lucida Grande]-network DISABLED      [/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]       description: Wireless interface[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]       product: BCM43142 802.11b/g/n[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]       vendor: Broadcom Corporation[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]       physical id: 0[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]       bus info: pci@0000:03:00.0[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]       logical name: wlan0[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]       version: 01[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]       serial: 18:cf:5e:bf:0c:4d[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]       width: 64 bits[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]       clock: 33MHz[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.141 (r415941) latency=0 multicast=yes wireless=IEEE 802.11abg[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]       resources: irq:18 memory:f7900000-f7907fff[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande] -network[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]       description: Ethernet interface[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]       vendor: Realtek Semiconductor Co., Ltd.[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]       physical id: 0.1[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]       bus info: pci@0000:04:00.1[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]       logical name: eth0[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]       version: 12[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]       serial: 54:a0:50:0b:8b:6d[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]       size: 100Mbit/s[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]       capacity: 1Gbit/s[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]       width: 64 bits[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]       clock: 33MHz[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8411-2_0.0.1 07/08/13 ip=192.168.1.128 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]       resources: irq:49 ioport:d000(size=256) memory:f7814000-f7814fff memory:f7810000-f7813fff[/FONT][/COLOR]
```
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]This is for ifconfig.

```
[COLOR=#000000][FONT=lucida Grande]ifconfig[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]eth0      Link encap:Ethernet  HWaddr 54:a0:50:0b:8b:6d  [/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]          inet addr:192.168.1.128  Bcast:192.168.1.255  Mask:255.255.255.0[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]          inet6 addr: fe80::56a0:50ff:fe0b:8b6d/64 Scope:Link[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]          RX packets:2189 errors:0 dropped:0 overruns:0 frame:0[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]          TX packets:2756 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]          collisions:0 txqueuelen:1000[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]          RX bytes:1251025 (1.2 MB)  TX bytes:412917 (412.9 KB)[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]
[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]lo        Link encap:Local Loopback  [/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]          inet addr:127.0.0.1  Mask:255.0.0.0[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]          inet6 addr: ::1/128 Scope:Host[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]          UP LOOPBACK RUNNING  MTU:65536  Metric:1[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]          RX packets:1925 errors:0 dropped:0 overruns:0 frame:0[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]          TX packets:1925 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]          collisions:0 txqueuelen:0[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]          RX bytes:170278 (170.2 KB)  TX bytes:170278 (170.2 KB)[/FONT][/COLOR]
```

I disabled the wifi before I use the hardwire to test it.

---

### Post by zlyspl on 2014-08-27
> **chili555 said:**
> Your device is:Per the sticky, the correct driver is bcmwl-kernel-source, which you have installed now.

Appreciate the confirmation. Thanks.

---

### Post by varunendra on 2014-08-28
> **zlyspl said:**
> ```
       configuration: autonegotiation=on .... duplex=full ... **[COLOR="#0000CD"]ip=192.168.1.128[/COLOR]** latency=0 link=yes ... speed=100Mbit/s
       resources: irq:49 ioport:d000(size=256) memory:f7814000-f7814fff memory:f7810000-f7813fff
```

Everything looks pretty solid with Ethernet. What is the ping result? That is -
```
ping -c4 192.168.1.1
ping -c4 8.8.8.8
```

And you never answered this -
> Is the browsing otherwise fine?
..means, if you browse a site that doesn't require login, just any random website, is the browsing fine then?

---

### Post by zlyspl on 2014-08-28
> **varunendra said:**
> if you browse a site that doesn't require login, just any random website, is the browsing fine then?

Well, it is fine for most websites. I have problems with yahoo.com, popsci.com for some reason. Unfortunately I do not know the reason why. I can connect to those websites as well as websites that require username/password fine with my home wifi.

---

### Post by varunendra on 2014-08-28
Once more, you answered only half of my post. The ping replies might (or might not) have shed some more light on the issue. And..
> **zlyspl said:**
> Well, it is fine for most websites.... I can connect to those websites as well as websites that require username/password fine with my home wifi.
..once more, I am inclined to believe it is a firewall issue.

Could you ask your IT guys to temporarily connect your Ethernet connection directly to the router bypassing the firewall (assuming the firewall is separate than the router)? If they have added some custom firewall policies within the router, can they temporarily disable them on your request? This will just be a test of whether the issue is indeed the firewall or something else. After it is confirmed, they can put you back on the regular connection. If they agree to do that test, make sure they reboot the router (if the policies are defined within the router) while you reboot your laptop to allow a fresh attempt with the changed configuration.

If it actually turns out to be their firewall policies, it is upto them how they sort it out. I do have some experience with enterprise class firewall, but complex fw policies can go beyond my level of expertise about them.

---

### Post by zlyspl on 2014-08-29
> **varunendra said:**
> I am inclined to believe it is a firewall issue.

Could you ask your IT guys to temporarily connect your Ethernet connection directly to the router bypassing the firewall (assuming the firewall is separate than the router)? If they have added some custom firewall policies within the router, can they temporarily disable them on your request? This will just be a test of whether the issue is indeed the firewall or something else. After it is confirmed, they can put you back on the regular connection. If they agree to do that test, make sure they reboot the router (if the policies are defined within the router) while you reboot your laptop to allow a fresh attempt with the changed configuration.

If it actually turns out to be their firewall policies, it is upto them how they sort it out. I do have some experience with enterprise class firewall, but complex fw policies can go beyond my level of expertise about them.

I wasn't able to get my IT guy to bypass the firewall (security reasons). However I was able to tests other computers (windows) (Apple) also cellphones and none of them have any problems with username/passwords websites or the websites I mentioned above. 

P.S. I apologize for sometimes answering half a post. I cannot reliably use Ubuntu forums at work because of the wifi reasons so I have to do so at home but by then I wasn't able to do any pings or other troubleshooting. I'll try to get them ASAP.

---

### Post by varunendra on 2014-08-29
> **zlyspl said:**
> I cannot reliably use Ubuntu forums at work because of the wifi reasons so I have to do so at home but by then I wasn't able to do any pings or other troubleshooting. I'll try to get them ASAP.

Oh, sorry about that comment then, I though you (accidentally) just ignored the ping part.

Frankly, I'm almost out of ideas. Those I still have don't logically fit very well. I might have missed/skipped some obvious things to check/test/tweak, but then it is not uncommon for me to post in a hurry these days.

So let's just summarize the current status to save us the time of going through all the previous posts. Please either confirm or correct these, and obviously add anything that you consider to be a significant/important observation -

[indent]**1)** The problem is that you can not browse/log into those websites correctly that require you to login with a username/password (Plus "yahoo.com and popsci.com" which you named explicitly ?).

**2)** Browsing other websites, downloading etc. is fine.

**3)** The problem occurs ONLY in your OFFICE network, not in home (anywhere else?)

**4)** The problem is SAME (?) for both WIFI and ETHERNET (you only said "It is worse" for Ethernet in post #15. **Please describe the behaviour of Ethernet (cable) connection if it is not SAME** for both WIFI and EHTERNET).[/indent]

And the only idea for now, could you test the network in a Live session? Means boot your laptop with a Live DVD/USB and check the network behaviour (both WIFI and ETHERNET, one after other, if possible). The WiFi should work without installing anything on a Live session, and so should the Ethernet. If you can do this test, please post the wireless_script report from that session for reference.

---

### Post by zlyspl on 2014-08-29
> **varunendra said:**
> 
And the only idea for now, could you test the network in a Live session? Means boot your laptop with a Live DVD/USB and check the network behaviour (both WIFI and ETHERNET, one after other, if possible). The WiFi should work without installing anything on a Live session, and so should the Ethernet. If you can do this test, please post the wireless_script report from that session for reference.

I''ll try this once this weekend is over and see if there is a difference. As for the rest, here's the rundown.

**1)** The problem is that you can not browse/log into those websites correctly that require you to login with a username/password yahoo.com and popsci.com" which you named explicitly 
***      Yes, I get a ERR_CONNECTION_RESET or ERR_NOREPONSE_SERVER Page. As for "some" websites like Ubuntuforums, it sometimes logs in, it sometimes just get an extra long waiting for website message. Other times for Ubuntuforums, I can hit the stop load page on my browser and everything popups up immediately.***

**2)** Browsing other websites, downloading etc. is fine.
   ***_Downloading is fine as long as it is not from sourcenet. Wikipedia, msn.com works perfectly._***

**3)** The problem occurs ONLY in your OFFICE network, not in home (anywhere else?)
   ***_Correct. I'll see if I get a chance to test the wifi at my local Starbucks to if there is any problems._***

**4)** The problem is SAME (?) for both WIFI and ETHERNET (you only said "It is worse" for Ethernet in post #15. **Please describe the behaviour of Ethernet (cable) connection if it is not SAME** for both WIFI and EHTERNET).
   [B][I][U]The ethernet cable is slower than the wifi, more websites does not load at all where as wifi loads non-troubled pages at a normal decent pace. Ubuntu forums does not work at all with ethernet while it works at times for wifi.    Unfortunately the same problem occurs with the ethernet when compared to the wifi. 

[/U][/I][/B][COLOR=#0000ff]One thing I forgot to add or mention is that I had downloaded a VPN that is compatible for Ubuntu which installs Cisco IPSEC by typing 
[/COLOR]```
[COLOR=#555555][FONT=Lucida Grande]sudo apt-get install network-manager-vpnc -y[/FONT][/COLOR]
```
[COLOR=#0000ff]
Not sure if this would anyway affect my ethernet or wifi.[/COLOR]

---

### Post by varunendra on 2014-08-29
In your next post, I would like to see the outputs of -
```
sudo lshw -C network
nm-tool
ifconfig
sudo ethtool eth0
```
..while you are using the Ethernet connection.

We have been (surprisingly) noticing a series of ethernet related problems recently, especially slow speeds and failure in connection. I wonder if the problem you experienced is a similar one, not anything that is causing the trouble with the WiFi. Possible just a bad coincidence of two independent problems (?).

---

### Post by zlyspl on 2014-08-30
[TABLE="width: 100%"]
[TR]
[TD="class: body"]```
ping -c4 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.139 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.153 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.168 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=0.160 ms


--- 192.168.1.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 0.139/0.155/0.168/0.010 ms

```

```
ping -c4 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=43 time=60.4 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=43 time=56.8 ms


--- 8.8.8.8 ping statistics ---
4 packets transmitted, 2 received, 50% packet loss, time 3011ms
rtt min/avg/max/mdev = 56.851/58.639/60.427/1.788 ms
```


```
network              
       description: Wireless interface
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 18:cf:5e:bf:0c:4d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.141 (r415941) latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:18 memory:f7900000-f7907fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.1
       bus info: pci@0000:04:00.1
       logical name: eth0
       version: 12
       serial: 54:a0:50:0b:8b:6d
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8411-2_0.0.1 07/08/13 ip=192.168.1.128 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:49 ioport:d000(size=256) memory:f7814000-f7814fff memory:f7810000-f7813fff
```


```
nm-tool
NetworkManager Tool
State: connected (global)
- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        54:A0:50:0B:8B:6D


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.128
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             202.96.209.133
    DNS:             202.96.209.5
```



```
Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        18:CF:5E:BF:0C:4D


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points
    Physics:         Infra, 00:36:76:22:25:2E, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    IP-COM:          Infra, 00:B0:C6:01:7E:58, Freq 2437 MHz, Rate 54 Mb/s, Strength 29
    ssbs-316:        Infra, A8:15:4D:FC:55:D6, Freq 2412 MHz, Rate 54 Mb/s, Strength 62 WPA WPA2

```



```
ifconfig
eth0      Link encap:Ethernet  HWaddr 54:a0:50:0b:8b:6d  
          inet addr:192.168.1.128  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::56a0:50ff:fe0b:8b6d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1688 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1274 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:566903 (566.9 KB)  TX bytes:137545 (137.5 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1583 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1583 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:132411 (132.4 KB)  TX bytes:132411 (132.4 KB)


wlan0     Link encap:Ethernet  HWaddr 18:cf:5e:bf:0c:4d  
          inet6 addr: fe80::1acf:5eff:febf:c4d/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:758 errors:0 dropped:0 overruns:0 frame:4544
          TX packets:899 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:469321 (469.3 KB)  TX bytes:117557 (117.5 KB)
          Interrupt:18
```


```
sudo ethtool eth0
Settings for eth0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full
                            100baseT/Half 100baseT/Full
                            1000baseT/Half 1000baseT/Full
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full
                            100baseT/Half 100baseT/Full
                            1000baseT/Full
    Advertised pause frame use: Symmetric Receive-only
    Advertised auto-negotiation: Yes
    Link partner advertised link modes:  10baseT/Half 10baseT/Full
                                         100baseT/Half 100baseT/Full
    Link partner advertised pause frame use: Symmetric Receive-only
    Link partner advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000033 (51)
                   drv probe ifdown ifup
    Link detected: yes
```
[/TD]
[/TR]
[/TABLE]

---

### Post by varunendra on 2014-09-01
zlyspl,

Did you post any reply to this ? -
> **chili555 said:**
> Is the firewall interfering?```
sudo status ufw
```

I think the question got lost in distractions. We are talking about firewalls, but did we check the internal one? Sorry if I missed your already posted answer, please post it (again, if you already did) to confirm.

The only thing I can think of now, besides external factors, is trying a lower MTU (Maximum Transmission Unit) value. In Network Manager, try MTU values 1492 or 1392 instead of 'Automatic'.

---

### Post by zlyspl on 2014-11-07
Sorry for the lack of updates on this problem. This problem have been resolved, the office where I work fixed the problem by using a different router now. So your initial prediction it was the router is 100% correct. I appreciate the help and hopefully this would help others.

---

