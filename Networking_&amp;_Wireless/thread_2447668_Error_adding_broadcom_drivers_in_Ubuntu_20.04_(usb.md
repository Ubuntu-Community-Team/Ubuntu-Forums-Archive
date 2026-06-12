---
title: "Error adding broadcom drivers in Ubuntu 20.04 (usb installation)"
date: 2020-07-23
forum: Networking &amp; Wireless
---

### Post by herraizcat on 2020-07-23
Hi there!

I'm having some trouble to configure the wifi in ubuntu. I've installed ubuntu 20.04 in a 32 gb pendrive on a macbook air. Everything works fine, except I haven't been able to set the wifi properly.

I tried to add the driver from the ISO as well as downloaded and install the broadcom drivers. I've been following some tips on the Internet (it seems a common issue), but I haven't been able to fix the issue so far.

This is the error message I'm getting:

[ATTACH=CONFIG]286523[/ATTACH]

And this is de output file (wireless-info.txt):

```




########## wireless info START ##########


Report from: 22 Jul 2020 16:03 CEST +0200


Booted last: 22 Jul 2020 00:00 CEST +0200


Script from: 22 Oct 2018 03:34 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 20.04 LTS
Release:    20.04
Codename:    focal


##### kernel ############################


Linux 5.4.0-26-generic #30-Ubuntu SMP Mon Apr 20 16:58:30 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


03:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM4360 802.11ac Wireless Network Adapter [14e4:43a0] (rev 03)
    Subsystem: Apple Inc. BCM4360 802.11ac Wireless Network Adapter [106b:0117]
    Kernel driver in use: bcma-pci-bridge


##### lsusb #############################


Bus 002 Device 003: ID 05ac:8406 Apple, Inc. Card Reader
Bus 002 Device 002: ID 0930:1408 Toshiba Corp. USB FLASH DRIVE
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 05ac:0291 Apple, Inc. Apple Internal Keyboard / Trackpad
Bus 001 Device 007: ID 05ac:828f Apple, Inc. BRCM20702 Hub
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 002: ID 090c:1000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### secure boot #######################


This system doesn't support Secure Boot


##### lsmod #############################


b43                   417792  0
cordic                 16384  1 b43
mac80211              843776  1 b43
cfg80211              704512  2 b43,mac80211
ssb                    73728  1 b43
libarc4                16384  1 mac80211
bcma                   65536  1 b43


##### interfaces ########################


##### ifconfig ##########################


1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever


##### iwconfig ##########################


lo        no wireless extensions.


##### route #############################


##### resolv.conf #######################


[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']


nameserver 127.0.0.53
options edns0


##### network managers ##################


Installed:


    NetworkManager


Running:


root         744       1  0 16:01 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


##### NetworkManager.state ##############


cat: /var/lib/NetworkManager/NetworkManager.state: Permission denied


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
unmanaged-devices=*,except:type:wifi,except:type:gsm,except:type:cdma


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


Region: Europe/Madrid (based on set time zone)


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


##### iwlist scan #######################


lo        Interface doesn't support scanning.


##### module infos ######################


[b43]
filename:       /lib/modules/5.4.0-26-generic/kernel/drivers/net/wireless/broadcom/b43/b43.ko
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
vermagic:       5.4.0-26-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         Build time autogenerated kernel key
sig_key:        2E:1C:6B:CE:DF:4D:6E:F0:5B:25:79:E8:B6:0E:F2:9A:9A:01:CB:AF
sig_hashalgo:   sha512
signature:      48:C6:4F:F9:FE:B0:D7:16:B3:F2:5D:51:BB:7F:41:B4:42:BE:75:46:
        DF:AC:FE:B5:3A:DF:82:1D:41:FF:D0:01:46:24:27:02:92:2D:F2:11:
        CB:A4:A6:CB:54:B9:A1:8E:F2:D6:7D:17:4E:D8:51:C0:28:D8:78:70:
        33:FE:21:BE:E1:53:F5:A6:ED:5E:4B:A6:7E:F7:40:CF:57:7F:7D:B3:
        51:74:84:37:58:C3:31:19:6A:F7:AF:C2:44:01:D2:17:33:8D:11:3D:
        E3:95:28:96:4B:5E:D8:F6:CA:69:02:60:3D:9A:A2:61:05:F2:ED:F2:
        0E:1A:44:C8:F1:61:4F:0F:04:B0:C2:39:92:1B:27:0A:9D:BF:17:98:
        FF:06:B5:43:86:0F:0D:8E:F2:39:1D:71:94:E1:9F:C5:AF:0F:57:EE:
        1A:7B:55:2F:95:79:BA:22:9B:AB:A2:CE:C2:97:2B:8D:9A:CA:0A:41:
        2D:F7:F0:6C:C0:15:59:93:3D:CB:96:A4:A3:81:47:3A:9E:D7:01:41:
        9A:5B:8A:58:B5:C6:79:50:13:EB:88:EC:EF:6B:D8:24:DD:1F:D4:47:
        19:D9:D8:3A:3E:8F:6E:E4:F1:69:B7:68:01:CB:76:C7:13:2C:25:B5:
        3B:C5:BA:EC:CB:B5:D9:34:9F:82:E3:3A:20:41:F6:50:D0:8C:8C:C9:
        B8:62:27:74:81:E1:98:8F:55:A1:01:71:66:1B:79:2D:3B:5E:53:E0:
        86:9D:B4:7F:09:B3:F9:90:30:55:8A:5E:E7:D4:55:74:77:AB:DD:F4:
        C5:AD:ED:B3:A2:FD:20:3A:23:9A:F9:B3:23:97:CF:ED:F1:32:80:B2:
        E9:19:39:8B:09:67:3D:86:0F:18:18:E5:30:CB:58:38:D0:E9:70:B8:
        B5:9B:D3:1F:89:10:82:41:46:B2:B8:BD:15:F5:A3:78:AD:05:CA:BE:
        52:FB:52:62:11:40:78:32:70:7A:DA:E0:99:D4:C5:A5:CE:99:FB:61:
        8B:D5:D6:56:D0:45:93:A0:03:D7:B8:44:74:E0:72:34:3C:CD:DB:84:
        41:CC:5E:E9:93:03:2A:51:2F:B6:E0:CF:68:6D:AA:6A:CF:BC:8C:C7:
        FB:B5:12:4E:61:A1:5F:21:D7:D9:8C:37:51:59:75:A4:0A:D5:FB:4B:
        38:B6:62:0F:FF:02:D7:DD:49:04:2B:7F:07:17:2C:69:48:B5:DC:A5:
        69:75:E5:0B:AC:A1:2D:79:80:B1:94:C1:79:79:94:25:CA:1A:6B:37:
        A6:01:9E:40:0E:F0:1F:EA:04:36:86:36:47:10:F4:74:92:8C:AD:D5:
        49:B6:08:84:F4:BD:D6:33:E6:0D:EF:69
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


[mac80211]
filename:       /lib/modules/5.4.0-26-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     903F9DC753D67350BFBEC9F
depends:        cfg80211,libarc4
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       5.4.0-26-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         Build time autogenerated kernel key
sig_key:        2E:1C:6B:CE:DF:4D:6E:F0:5B:25:79:E8:B6:0E:F2:9A:9A:01:CB:AF
sig_hashalgo:   sha512
signature:      2B:5C:FC:D8:EF:9D:04:F8:88:28:B5:A8:60:84:B4:59:A5:EE:F1:0B:
        D2:92:A2:2D:62:67:99:35:2C:99:1A:8A:B5:CE:9E:C9:09:49:26:1D:
        B0:12:5C:28:EE:89:BF:BC:CB:65:A1:1C:17:25:C8:31:04:77:27:6D:
        A6:68:C9:F0:13:77:8A:7E:4F:7A:68:A5:17:EE:A2:9C:0D:96:0A:3D:
        47:09:0A:E0:26:FF:5E:98:C6:B5:39:B6:DB:B7:69:26:56:4D:A8:20:
        42:A9:79:9D:06:98:8F:29:D5:24:84:91:3D:BF:D9:DF:01:D7:DD:D5:
        ED:5B:E1:F6:FC:A1:46:E3:89:CC:3C:B0:80:D2:8D:F2:DE:E5:1B:C0:
        EA:AA:3B:B2:75:A8:1A:0B:E3:88:F4:36:4A:DD:C6:4F:FB:73:A9:E4:
        12:C1:FE:30:42:C1:53:A1:2D:22:80:7A:20:4F:D9:B2:3B:FD:C8:61:
        35:B8:4A:41:CB:D4:BC:86:94:F3:D3:C1:D5:A4:DE:9E:C8:D7:92:6A:
        D4:56:F9:8A:35:6C:22:25:88:43:4D:47:13:63:26:AE:5C:D1:64:EA:
        39:55:D7:D9:F1:08:C2:A4:76:39:5D:6B:91:41:6A:10:41:34:8C:C3:
        06:A6:EE:81:61:F8:00:CA:97:A8:39:8D:00:E9:A2:7C:29:A2:BF:C9:
        0C:2C:2C:9D:66:43:6D:53:B3:ED:EA:16:C3:8E:EF:22:0D:FE:20:5E:
        CD:B7:9B:BC:9A:B0:F3:4A:D8:D2:A9:22:A8:9A:D4:F6:80:EF:9F:FC:
        73:3B:EC:A7:7D:E5:1B:0D:DC:FB:E8:08:31:97:E7:7D:FE:87:7C:3A:
        04:31:F6:67:E0:9E:BB:E0:48:75:D2:AB:53:2B:92:A7:84:67:A0:11:
        06:0A:7A:1C:04:E7:B0:BF:B2:CD:B9:41:65:71:6A:46:2F:B4:D5:CD:
        49:0D:C5:96:30:AC:A1:D0:2D:6F:AA:1C:9B:D8:5F:C2:2C:30:7C:43:
        CE:E0:E6:3B:40:E2:73:EF:C0:B3:92:61:8E:2D:A2:32:28:B9:41:56:
        B7:BE:58:43:81:10:31:CE:43:99:F6:51:26:64:0D:CC:75:95:F4:68:
        02:B4:A2:A2:A9:C9:D7:64:8A:CE:92:80:D8:05:8B:CD:D1:94:97:56:
        54:3F:9C:24:8F:A5:82:43:A7:C9:DA:0D:99:4F:66:43:6D:D2:72:F3:
        2A:6B:5C:5A:3E:7E:25:BC:53:9B:D9:A2:CE:B3:ED:E0:80:8F:82:D3:
        ED:0C:E9:95:6B:D1:B9:BC:1C:9B:4A:2F:A0:18:66:AD:69:9C:AF:A1:
        C1:90:0C:96:AC:C7:1E:17:C5:CC:70:1A
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/5.4.0-26-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     8795FC14A499B3F7A2F6AD8
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       5.4.0-26-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         Build time autogenerated kernel key
sig_key:        2E:1C:6B:CE:DF:4D:6E:F0:5B:25:79:E8:B6:0E:F2:9A:9A:01:CB:AF
sig_hashalgo:   sha512
signature:      2B:BE:F5:0E:F8:79:0A:5A:28:AA:E7:CD:D2:DA:FE:D8:D3:EF:7F:A2:
        2F:0D:AD:65:F1:AD:D9:74:29:73:54:B8:C7:7D:9E:6C:EC:46:6F:1D:
        7F:12:C6:DF:95:3C:52:3A:1A:47:12:40:B8:66:48:F3:FF:49:28:44:
        2A:ED:96:AD:07:48:7A:F7:19:D4:10:F9:A5:4E:90:A8:FD:8A:02:14:
        AA:31:06:91:5E:2C:58:DA:3D:8F:20:2F:D3:21:99:2C:B7:CF:4E:53:
        33:3E:F5:45:7D:8C:23:71:24:8B:7D:61:87:55:60:B7:72:FA:0C:08:
        D1:B0:0B:BF:D3:DC:56:22:F9:94:7D:C6:F8:8B:35:27:8B:A3:14:B7:
        90:15:B8:93:C7:A8:3F:B5:69:24:4B:D7:27:50:4B:A5:D5:D1:45:85:
        AB:0C:4E:84:9D:33:B1:BC:E0:31:C5:92:73:90:46:17:AB:0C:4C:31:
        49:C2:0D:AC:52:88:9F:5D:7A:2B:EF:75:1D:D1:9D:92:D2:FD:88:0D:
        74:D8:C7:41:0D:54:67:D6:66:E9:C5:C8:3F:94:E0:86:2B:D5:38:D7:
        07:95:B8:3B:A5:96:F9:20:D6:2C:BC:DA:22:C4:97:DD:FB:1C:8B:ED:
        15:EC:33:95:65:FE:36:7B:93:44:6B:1D:57:91:C4:C4:31:EE:2D:17:
        2D:FD:E8:2F:50:C3:48:3A:0A:0D:F1:1B:53:D1:A3:9E:5B:A8:1C:56:
        99:79:BE:1B:E0:F1:5B:BD:28:96:2B:A6:F8:DD:34:05:84:9E:04:D3:
        26:58:24:64:9C:0D:CC:46:A2:3E:27:1D:35:F3:81:E1:98:78:89:07:
        D1:09:63:80:D0:79:48:21:95:84:62:17:32:3B:C9:67:98:22:D2:26:
        3E:B5:3A:25:EF:BE:42:CE:99:A1:50:D0:4D:70:28:94:31:9D:63:DA:
        78:5A:BD:8A:8B:78:76:DA:40:33:3E:D8:9D:D5:C7:CF:6B:5F:05:47:
        E2:30:AE:2A:C8:42:36:14:21:5E:93:B9:70:3B:16:00:49:F9:28:A6:
        23:76:A2:03:1A:A1:CE:42:08:55:E7:FD:39:62:50:E9:E1:73:58:60:
        75:B9:44:7E:4F:17:CF:1A:19:20:56:A4:43:38:FC:9F:2C:7E:C0:C2:
        FE:C2:AF:73:C7:8F:76:8E:CB:72:D9:FD:1C:9D:06:1B:30:99:3B:5C:
        6F:2B:DC:CB:71:3F:FC:C3:4F:DF:CE:B4:77:F2:A9:9E:8D:5D:90:A9:
        52:02:1A:EE:B3:D1:ED:6E:19:81:FC:3A:2E:48:BA:26:E8:F8:52:D7:
        62:5C:AE:7C:88:2B:29:87:0C:60:A3:23
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[ssb]
filename:       /lib/modules/5.4.0-26-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     571863F88D3D9D6896EF515
depends:        
retpoline:      Y
intree:         Y
name:           ssb
vermagic:       5.4.0-26-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         Build time autogenerated kernel key
sig_key:        2E:1C:6B:CE:DF:4D:6E:F0:5B:25:79:E8:B6:0E:F2:9A:9A:01:CB:AF
sig_hashalgo:   sha512
signature:      37:F0:E1:7E:88:B6:34:C5:20:67:70:6B:D3:D3:80:30:89:FC:1E:4E:
        C9:69:C5:62:95:63:4D:80:5A:ED:71:4D:72:FE:86:56:D1:5A:D2:AB:
        CF:11:2E:A8:93:2F:12:B4:6F:41:13:9C:98:69:42:A4:CD:6A:34:C8:
        2E:21:54:F7:62:0C:22:A8:EB:4C:D9:CF:18:84:80:BE:DB:8E:5C:BD:
        77:90:15:CC:55:11:E2:11:C1:0B:51:B2:4E:A7:08:59:92:77:3D:30:
        B9:6A:FC:93:7F:5F:28:57:9C:1A:35:94:20:D2:2F:78:1D:FF:58:09:
        79:12:09:3C:D0:81:77:56:A2:53:CD:1D:D8:F6:20:79:DD:3F:78:8D:
        91:44:82:9A:32:D5:B4:D1:29:AB:04:40:89:7D:D7:F7:9A:4E:CA:C7:
        D8:4E:ED:17:46:1A:81:78:05:36:90:75:87:30:83:D4:2E:2C:CF:26:
        DC:75:47:5F:EA:FC:57:5A:DC:EB:5D:5D:64:64:8C:11:FE:F3:4D:CF:
        7B:6D:BD:E9:95:C7:6C:C2:8C:3E:36:34:43:2B:2A:1D:5C:F8:57:75:
        83:8C:0A:BF:EB:4C:1C:31:C8:DC:BF:A1:87:5E:29:85:1A:CE:18:F6:
        6C:D6:8F:D8:2E:09:F4:37:4C:06:90:68:7F:4A:35:7D:43:C9:D1:BB:
        68:69:83:45:1B:4B:69:70:4A:B5:9E:69:0B:EA:6E:0F:01:59:83:7D:
        B5:1C:0A:CB:D2:89:AD:B3:4B:E1:86:35:88:93:94:9D:45:D9:7C:0B:
        4F:CC:FA:25:35:60:39:0E:8D:1E:0C:C5:6C:52:BE:B8:13:55:DE:23:
        E4:C7:6F:76:0C:C5:2C:74:56:D2:82:8E:56:65:E6:EB:86:8F:44:2E:
        9F:C3:E6:20:6F:85:49:1F:91:34:29:D5:84:36:09:35:83:8E:FB:88:
        79:39:70:8C:F9:5B:9C:76:8D:9C:50:EC:1A:36:E1:D1:A4:94:2A:C6:
        9E:5D:7C:35:5C:14:07:25:55:BF:28:49:5D:BC:BB:76:6F:03:F8:DD:
        AB:BE:40:C4:3F:04:5D:DB:4B:CF:52:13:08:2A:EE:D4:78:D2:5E:93:
        47:36:37:94:E3:47:AE:DE:14:C0:D9:45:E1:A4:4C:F2:9E:37:8A:A1:
        D7:23:FE:56:6B:2A:A9:FD:79:59:5A:67:93:9A:72:B2:D6:66:89:E2:
        A2:BC:AE:6E:6C:04:53:F7:0D:2A:D8:06:4D:C0:97:1F:78:B6:DB:0B:
        B9:88:49:23:4D:E9:28:10:37:8B:7B:A5:C0:22:4D:EC:D9:79:93:AA:
        09:C9:71:1C:5E:C2:14:25:1C:B3:93:AA


[bcma]
filename:       /lib/modules/5.4.0-26-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     28BC6D6DBB15EC3F0F53EA3
depends:        
retpoline:      Y
intree:         Y
name:           bcma
vermagic:       5.4.0-26-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         Build time autogenerated kernel key
sig_key:        2E:1C:6B:CE:DF:4D:6E:F0:5B:25:79:E8:B6:0E:F2:9A:9A:01:CB:AF
sig_hashalgo:   sha512
signature:      32:3E:B1:75:A3:40:6A:1B:0E:D6:BB:47:74:CB:43:C7:6D:B6:02:AA:
        49:50:1A:66:B8:3E:07:F9:F4:F9:6B:4B:0E:5B:20:29:94:F9:88:FC:
        15:9E:25:4B:4B:F0:5C:5F:34:1A:32:54:7E:E1:CB:AC:74:C3:A8:64:
        4B:AE:6D:7B:98:ED:7B:A7:CA:71:B0:73:01:24:26:59:00:27:08:8A:
        CD:42:19:44:68:FB:1A:8D:6E:B6:2C:81:AB:49:27:8C:DA:3F:FC:F0:
        C9:3D:60:12:0B:86:F7:E5:BF:DB:F4:9C:50:52:EF:17:BC:44:8D:72:
        14:B4:23:4E:B8:9D:2D:27:A1:CE:0E:CF:63:DA:64:F7:47:EE:21:6B:
        0B:A0:A8:58:88:B9:88:AC:9F:3B:B9:21:BD:8B:EB:BE:3A:D0:BD:92:
        5F:30:22:E7:D7:E0:34:9C:25:69:AC:9C:81:0E:21:E1:9E:BA:2C:18:
        E0:62:E3:AB:74:DB:5A:51:A6:6D:55:41:26:1E:57:33:A9:38:8A:5C:
        C8:A7:53:AD:D5:1D:1B:CA:B2:5E:1F:39:FC:B2:8B:AD:6B:80:DE:E2:
        EA:E1:3D:46:05:E4:2C:CE:F1:2F:F7:2C:25:E3:B3:E9:B3:69:78:D5:
        BE:73:DE:6D:22:DE:3C:0F:5E:18:16:3C:1F:43:C2:6B:95:43:E4:5F:
        89:9E:5F:53:BC:DC:55:C2:71:70:B6:46:12:C1:1B:69:95:71:FB:35:
        82:D6:B0:30:71:A7:C3:CA:DA:02:DD:FC:AE:A9:4A:36:21:7B:7A:32:
        A2:7E:F2:5F:8E:22:FF:FA:34:CC:1A:77:D6:26:EC:E0:C3:EA:86:E0:
        0A:3D:58:0C:6A:43:E4:2C:F5:DD:97:C0:7B:AD:A3:5B:19:41:E5:D0:
        BF:D7:A5:BA:44:F9:38:69:E8:F9:32:22:39:A5:3C:2D:8B:D5:CC:AA:
        9B:92:5C:11:72:22:D4:3A:A1:DF:86:6A:E7:7D:5D:69:1A:52:EF:EA:
        9D:D2:8D:0F:B5:2F:24:6D:C9:81:62:65:01:99:20:B3:70:C1:CF:94:
        72:CE:50:42:7A:3E:21:AB:18:29:0A:42:7A:14:EB:27:D7:D9:1D:F5:
        8B:09:01:99:5C:C2:D3:BA:0E:88:23:66:56:63:85:35:0F:0E:1F:BB:
        75:6A:64:9F:A9:45:C7:59:71:0F:6F:2E:F1:FE:3C:34:7C:CD:DF:69:
        EC:38:66:B1:C0:0B:CC:5F:79:F6:49:9F:DC:74:83:D4:7E:49:4F:F9:
        21:BF:F9:A1:80:46:9F:58:6E:90:8E:09:D5:5F:42:0B:F3:C8:42:0C:
        EA:95:19:4D:A1:FA:34:8C:31:50:C4:D1


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


[    5.399708] b43-phy0: Broadcom 4360 WLAN found (core revision 42)
[    5.400132] b43-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 12, Type 11 (AC), Revision 1)
[    5.400142] b43: probe of bcma0:1 failed with error -95


########## wireless info END ############


```




Thanks you! Any help will be much appreciated!!

---

### Post by herraizcat on 2020-07-24
Fixed. Here I share some resources just in case someone has the same issue:


[URL="https://itsfoss.com/fix-no-wireless-network-ubuntu/"]https://itsfoss.com/fix-no-wireless-network-ubuntu/

[/URL][https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)[URL="https://itsfoss.com/fix-no-wireless-network-ubuntu/"]
[/URL]
[https://ubuntu.pkgs.org/20.04/ubuntu-restricted-amd64/bcmwl-kernel-source_6.30.223.271+bdcom-0ubuntu5_amd64.deb.html](https://ubuntu.pkgs.org/20.04/ubuntu-restricted-amd64/bcmwl-kernel-source_6.30.223.271+bdcom-0ubuntu5_amd64.deb.html)

---

