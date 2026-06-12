---
title: "Wi-Fi not working on HP g70 laptop (ubuntu 14.04)"
date: 2014-06-22
forum: Networking &amp; Wireless
---

### Post by Eugene_Donaghy on 2014-06-22
Hi

Have installed unbuntu 14.04 on my hp g70 laptop but wi-fi is not working as advised in other threads I have done this


```
    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

eugene-HP-G70-Notebook-PC 3.13.0-24-generic x86_64,  Ubuntu 14.04 LTS, trusty

CPU    : Intel(R) Core(TM)2 Duo CPU     T5800  @ 2.00GHz
Memory : 3007 MB
Uptime : 00:31:58 up 30 min,  2 users,  load average: 0.32, 0.28, 0.17


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:360b]
    Kernel driver in use: r8169
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:137b]
    Kernel driver in use: ath5k


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 007: ID 18a5:0302 Verbatim, Ltd 32GB Flash Drive
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04f2:b091 Chicony Electronics Co., Ltd Webcam
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
ath5k                 149924  0 
ath                    28698  1 ath5k
mac80211              626489  1 ath5k
mxm_wmi                13021  1 nouveau
cfg80211              484040  3 ath,ath5k,mac80211
wmi                    19177  3 hp_wmi,mxm_wmi,nouveau


module parameters ~~~~~~~~~~~~~~~~~~

ath5k         (3): fastchanswitch=N | nohwcrypt=N | no_hw_rfkill_switch=N
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: asleep
================o=============o========o==============o=========o===========o==============o===========
 Interface & ID | Type        | Driver | State        | Default | Speed     | Support      | HW Addr   
================o=============o========o==============o=========o===========o==============o===========
 wlan0          | 802.11 WiFi | ath5k  | unmanaged    | no      |           | WEP/WPA/WPA2 | <MAC wlan0>
----------------+-------------+--------+--------------+---------+-----------+--------------+-----------
 eth0           | Wired       | r8169  | unmanaged    | no      |           |              | <MAC eth0>
----------------+-------------+--------+--------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=false
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

Wi-Fi connection 1   : ssid=BTHub4-3WQ8 | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~



Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_GB.UTF-8")
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



blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[ath5k]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
srcversion:     F36818A2F0BCB2B0CC9BB8C
depends:        mac80211,cfg80211,ath
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)

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

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0x001c (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Not Default

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en

[/etc/pm/power.d/wireless]
#!/bin/sh
/sbin/iwconfig wlan power off



Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=bb6c6e21-7861-41ef-9dce-cae88bed5652 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.623755] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.624166] audit: initializing netlink socket (disabled)
[    1.479968] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   26.079435] wmi: Mapper loaded
[   26.399559] ath5k 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[   26.399718] ath5k 0000:03:00.0: registered as 'phy0'
[   27.478260] ath: EEPROM regdomain: 0x67
[   27.478261] ath: EEPROM indicates we should expect a direct regpair map
[   27.478263] ath: Country alpha2 being used: 00
[   27.478263] ath: Regpair used: 0x67
[   27.510595] ath5k: phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   28.330882] Bluetooth: BNEP (Ethernet Emulation) ver 1.3

    ======== Done ========


```

I did try to add the wireless router manually but no joy wi-fi adaptor is built into laptop 


any ideas on how to fix this please

---

### Post by paulmagarey on 2014-06-23
I've got a similar problem with my HP Compaq 6910p. I've installed ubuntu 14.04 but can't get Wireless working via any means. The little blue wireless hardware button flashes when I start up, but then doesn't show up. Nothing in what I've bot of BIOS or equivalent seems to have any relevance.

Output from various commands as follows:

   lspci -v  

 

 ….
 

 10:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)  
 	Subsystem: Intel Corporation Vaio VGN-SZ79SN_C  
 	Flags: bus master, fast devsel, latency 0, IRQ 48  
 	Memory at d8000000 (64-bit, non-prefetchable) [size=8K]  

 	Capabilities: <access denied>  
 	Kernel driver in use: iwl4965  
 
[Note that [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) says this card should be detected automatically]

 

 nm-tool
 

 NetworkManager Tool 
  
 State: connected (global) 
  
 - Device: wlan0 ---------------------------------------------------------------- 
   Type:              802.11 WiFi 
   Driver:            iwl4965 
   State:             unavailable 
   Default:           no 
   HW Address:        00:21:5C:06:C2:33 
  
   Capabilities: 
  
   Wireless Properties 
     WEP Encryption:  yes 
     WPA Encryption:  yes 
     WPA2 Encryption: yes 
  
   Wireless Access Points  
 

 lspci -nnk | grep -A2 0280 

 10:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [8086:4229] (rev 61) 
 	Subsystem: Intel Corporation Vaio VGN-SZ79SN_C [8086:1100] 
 	Kernel driver in use: iwl4965 
 

 

 rfkill list 

 0: phy0: Wireless LAN 
 	Soft blocked: no 
 	Hard blocked: yes 
 paul@paul-HP-Compaq-6910p:~$ rfkill unblock 0 
 paul@paul-HP-Compaq-6910p:~$ rfkill list 
 0: phy0: Wireless LAN 
 	Soft blocked: no 
 	Hard blocked: yes 

Any assistance would be greatly appreciated.

---

