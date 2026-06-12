---
title: "Newbie tries to install drivers"
date: 2020-03-04
forum: Networking &amp; Wireless
---

### Post by VampireSilence on 2020-03-04
Hello everyone!

I finally took the step to ubuntu (coming from windows 7) and now i want to install the drivers for my computer. I want to start with my WiFi driver, but i got some questions here.

I managed to google some drivers for my **Intel(R) PRO/Wireless 3945ABG**. The first one is "ipw3945-1.2.2.tgz" and the second one is "iwlwifi-3945-ucode-15.32.2.9.tgz". I dont know which one to choose, but i tried them both and after extracting them, no file was included which i could manage to open.

So i googled again and found this tutorial: [https://www.pendrivelinux.com/how-to-install-intel-pro-ipw3945-wireless-drivers/](https://www.pendrivelinux.com/how-to-install-intel-pro-ipw3945-wireless-drivers/)

The problem with that is, that it needs a working internet connection, which makes no sense to me. If it would work i wont need to install it. Quite confusing to me atm.

The second tutorial i found was this one: [https://itsfoss.com/install-additional-drivers-ubuntu/](https://itsfoss.com/install-additional-drivers-ubuntu/)

But when i open "Software & Updates", my downloaded files are not mentioned to be able to get installed and when i try to add their path to "Other Software" the button stays grey and wont let me add it.

The question is, which program do i need to open/install the driver files?

Thanks in advance >.<

---

### Post by CelticWarrior on 2020-03-04
Yoiu shouldn't need drivers for an Intel WiFi.

---

### Post by VampireSilence on 2020-03-04
Well it tells me that no WiFi adapters were found, so i thought a driver would help me out.

---

### Post by jeremy31 on 2020-03-04
Please see the wireless script link in my signature and post results

---

### Post by VampireSilence on 2020-03-05
Ok, first of all, i confused it. Its a Broadcom Wifi i got here.

Now the results:

```

########## wireless info START ##########

Report from: 30 Jan 2018 05:06 EST -0500

Booted last: 30 Jan 2018 00:00 EST -0500

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.4 LTS
Release:    18.04
Codename:    bionic

##### kernel ############################

Linux 5.3.0-28-generic #30~18.04.1-Ubuntu SMP Fri Jan 17 06:14:09 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

sed: can't read /home/pc/.dmrc: No such file or directory

Could not be determined.

##### lspci #############################

00:14.0 Bridge [0680]: NVIDIA Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
    Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
    Kernel driver in use: forcedeth

03:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM4311 802.11a/b/g [14e4:4312] (rev 01)
    Subsystem: Hewlett-Packard Company Broadcom 802.11a/b/g WLAN [103c:1361]
    Kernel driver in use: b43-pci-bridge

##### lsusb #############################

Bus 001 Device 003: ID 0781:5567 SanDisk Corp. Cruzer Blade
Bus 001 Device 002: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

##### secure boot #######################

'mokutil' is not installed (package "mokutil").

##### lsmod #############################

b43                   413696  0
cordic                 16384  1 b43
bcma                   61440  1 b43
mxm_wmi                16384  1 nouveau
mac80211              847872  1 b43
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
wmi_bmof               16384  0
cfg80211              704512  2 b43,mac80211
libarc4                16384  1 mac80211
ssb_hcd                16384  0
ssb                    73728  2 b43,ssb_hcd
wmi                    32768  4 hp_wmi,wmi_bmof,mxm_wmi,nouveau

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp0s20: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether <MAC 'enp0s20' [IF1]> brd <MAC address>

##### iwconfig ##########################

lo        no wireless extensions.

enp0s20   no wireless extensions.

##### route #############################

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0

##### network managers ##################

Installed:

    NetworkManager

Running:

root       698     1  0 05:00 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp0s20
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         NVIDIA Corporation
GENERAL.PRODUCT:                        MCP51 Ethernet Controller (Presario V6133CL)
GENERAL.DRIVER:                         forcedeth
GENERAL.DRIVER-VERSION:                 0.64
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enp0s20' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/net/enp0s20
GENERAL.IP-IFACE:                       --
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager config #############

[[/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf]]
[connection]
wifi.powersave = 3

[[/etc/NetworkManager/NetworkManager.conf]]
[main]
plugins=ifupdown,keyfile
[ifupdown]
managed=false
[device]
wifi.scan-rand-mac-address=no

[[/usr/lib/NetworkManager/conf.d/10-dns-resolved.conf]]
[main]
dns=systemd-resolved

[[/usr/lib/NetworkManager/conf.d/10-globally-managed-devices.conf]]
[keyfile]
unmanaged-devices=*,except:type:wifi,except:type:wwan

[[/usr/lib/NetworkManager/conf.d/20-connectivity-ubuntu.conf]]
[connectivity]
uri=http://connectivity-check.ubuntu.com/

[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-mac-addr-change-wifi]
match-device=driver:rtl8723bs,driver:rtl8189es,driver:r8188eu,driver:8188eu,driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no
wifi.cloned-mac-address=preserve
ethernet.cloned-mac-address=preserve

##### NetworkManager profiles ###########

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: America/New_York (based on set time zone)

global
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (N/A, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp0s20   no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp0s20   Interface doesn't support scanning.

##### module infos ######################

[b43]
filename:       /lib/modules/5.3.0-28-generic/kernel/drivers/net/wireless/broadcom/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode42.fw
firmware:       b43/ucode40.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode30_mimo.fw
firmware:       b43/ucode33_lcn40.fw
firmware:       b43/ucode29_mimo.fw
firmware:       b43/ucode26_mimo.fw
firmware:       b43/ucode25_mimo.fw
firmware:       b43/ucode25_lcn.fw
firmware:       b43/ucode24_lcn.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode16_lp.fw
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
srcversion:     41D3ACA1C3C72C8F16113E5
depends:        mac80211,ssb,bcma,cfg80211,cordic
retpoline:      Y
intree:         Y
name:           b43
vermagic:       5.3.0-28-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
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

[bcma]
filename:       /lib/modules/5.3.0-28-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     9FF0F781F456EC613F149E3
depends:        
retpoline:      Y
intree:         Y
name:           bcma
vermagic:       5.3.0-28-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[mac80211]
filename:       /lib/modules/5.3.0-28-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     6E0E397891117C00B7DB9BA
depends:        cfg80211,libarc4
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       5.3.0-28-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/5.3.0-28-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     7A4BDDDDFBDE4DDDB63AAE3
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       5.3.0-28-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb_hcd]
filename:       /lib/modules/5.3.0-28-generic/kernel/drivers/usb/host/ssb-hcd.ko
license:        GPL
description:    Common USB driver for SSB Bus
author:         Hauke Mehrtens
srcversion:     D1CBD34E5A02BE2CD8EFC4E
depends:        ssb
retpoline:      Y
intree:         Y
name:           ssb_hcd
vermagic:       5.3.0-28-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[ssb]
filename:       /lib/modules/5.3.0-28-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     374918DBFF9ECC7A359C43F
depends:        
retpoline:      Y
intree:         Y
name:           ssb
vermagic:       5.3.0-28-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

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
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode

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

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   10.797326] forcedeth 0000:00:14.0 enp0s20: no link during initialization

########## wireless info END ############

```

---

### Post by CelticWarrior on 2020-03-05
Broadcom indeed, so we follow this tutorial: [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

Supposedly it's something like this:

```
sudo apt purge b43-pci-bridge
sudo apt install firmware-b43-installer
```

We need an alternative internet connection, of course.

---

### Post by chili555 on 2020-03-05
> 
sudo apt purge b43-pci-bridge
There is no package *b43-pci-bridge* to remove or purge. You may safely omit this step.

---

### Post by CelticWarrior on 2020-03-05
> **chili555 said:**
> There is no package *b43-pci-bridge* to remove or purge. You may safely omit this step.

Thank you.

I guess that's why it isn't mentioned in the sticky thread you created :P.

---

### Post by VampireSilence on 2020-03-05
It worked. Thanks a lot!

---

