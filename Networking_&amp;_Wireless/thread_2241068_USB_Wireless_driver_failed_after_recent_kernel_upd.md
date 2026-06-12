---
title: "USB Wireless driver failed after recent kernel update"
date: 2014-08-24
forum: Networking &amp; Wireless
---

### Post by risva on 2014-08-24
Hello all,

i'm having a pressario 2200 laptop with celerom M procesor, running lubuntu 14.04

initially i had trouble installing my usb wifi, but with help from forum:
[h=1][SIZE=3][installed 14.04  but Wifi does not connect after suspend, ralink RT5370]("http://ubuntuforums.org/showthread.php?t=2218445")[/SIZE]   [SIZE=2]at[/SIZE][/h]_[http://ubuntuforums.org/showthread.php?t=2218445](http://ubuntuforums.org/showthread.php?t=2218445)_

it worked perfectly well.

after recent lubuntu kernel update, the wifi has stopped working. 

i tried the previous steps, but the driver earlier available at, _media.cdn.ubuntu-de.org/forum/attachments/13/16/4365112-Ralink_5370sta-2.5.0.3_dkms.tar.gz_ doesnt seems to be available any more.

please suggest reliable source of said driver, or some other way of resolving my problem.

thanx.

---

### Post by risva on 2014-08-24
Hello all,

the ouput of running the popular wireless script is as under:

```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

john-Presario-2200-PR557PC-UUF 3.13.0-34-generic i686,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Celeron(R) M processor         1400MHz
Memory : 715 MB
Uptime : 10:22:36 up 55 min,  2 users,  load average: 0.40, 0.51, 0.58


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)
    Subsystem: Hewlett-Packard Company Device [103c:3084]
    Kernel driver in use: 8139too


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 002: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

wmi                    18673  0 


module parameters ~~~~~~~~~~~~~~~~~~

wmi           (2): 


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
===============================o=======o=========o===========o=========o===========o==============o===========
 Interface & ID                | Type  | Driver  | State     | Default | Speed     | Support      | HW Addr   
===============================o=======o=========o===========o=========o===========o==============o===========
 eth0  [Ethernet connection 1] | Wired | 8139too | connected | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         192.168.1.101
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1
-------------------------------+-------+---------+-----------+---------+-----------+--------------+-----------


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

DIAT_GUEST           : ssid=DIAT_GUEST | ipv6=auto | ipv4=auto 
Wi-Fi connection 1   : ssid=JOHN-PC_Network | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.289/0.296/0.303/0.007 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.064/0.065/0.066/0.001 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_IN")


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

           - 


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~



blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist rt2800usb
blacklist rt2870sta
blacklist rt2x00
blacklist rt2800usb

[/etc/modprobe.d/blaclist.conf]
blacklist rt2800usb
blacklist rt2870sta 

[/etc/modprobe.d/libpisock9.conf]
blacklist visor


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[wmi]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x:0x (rt2800usb)
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

[/etc/pm/config.d/config]
SUSPEND_MODULES="RT2800USB"


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-34-generic root=UUID=7d5b7dd7-0daf-451c-adbf-764c73286e22 ro forcepae quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[   19.740658] Modules linked in: snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   19.741065] Modules linked in: snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   19.741471] Modules linked in: snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   19.741875] Modules linked in: snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   19.804207] Modules linked in: snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   19.804834] Modules linked in: snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   19.805385] Modules linked in: snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   19.805935] Modules linked in: snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   19.806482] Modules linked in: snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   19.856193] Modules linked in: snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   19.856744] Modules linked in: snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   19.857229] Modules linked in: snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   19.857714] Modules linked in: snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   19.858196] Modules linked in: snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   21.458169] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.604185] Modules linked in: rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   23.604799] Modules linked in: rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   23.605350] Modules linked in: rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   23.605900] Modules linked in: rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   23.606446] Modules linked in: rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   23.684189] Modules linked in: rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   23.684734] Modules linked in: rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   23.685221] Modules linked in: rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   23.685705] Modules linked in: rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   23.686185] Modules linked in: rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   23.752303] Modules linked in: rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   23.752920] Modules linked in: rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   23.753472] Modules linked in: rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   23.754021] Modules linked in: rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   23.754568] Modules linked in: rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   23.832180] Modules linked in: rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   23.832726] Modules linked in: rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   23.833212] Modules linked in: rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   23.833695] Modules linked in: rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   23.834174] Modules linked in: rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   46.104182] Modules linked in: pci_stub vboxpci(OF) vboxnetadp(OF) vboxnetflt(OF) vboxdrv(OF) rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   46.104742] Modules linked in: pci_stub vboxpci(OF) vboxnetadp(OF) vboxnetflt(OF) vboxdrv(OF) rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   46.105242] Modules linked in: pci_stub vboxpci(OF) vboxnetadp(OF) vboxnetflt(OF) vboxdrv(OF) rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   46.105740] Modules linked in: pci_stub vboxpci(OF) vboxnetadp(OF) vboxnetflt(OF) vboxdrv(OF) rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   46.106235] Modules linked in: pci_stub vboxpci(OF) vboxnetadp(OF) vboxnetflt(OF) vboxdrv(OF) rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   46.164224] Modules linked in: pci_stub vboxpci(OF) vboxnetadp(OF) vboxnetflt(OF) vboxdrv(OF) rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   46.164716] Modules linked in: pci_stub vboxpci(OF) vboxnetadp(OF) vboxnetflt(OF) vboxdrv(OF) rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   46.165143] Modules linked in: pci_stub vboxpci(OF) vboxnetadp(OF) vboxnetflt(OF) vboxdrv(OF) rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   46.165569] Modules linked in: pci_stub vboxpci(OF) vboxnetadp(OF) vboxnetflt(OF) vboxdrv(OF) rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii
[   46.165991] Modules linked in: pci_stub vboxpci(OF) vboxnetadp(OF) vboxnetflt(OF) vboxdrv(OF) rfcomm bnep bluetooth snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer yenta_socket joydev snd pcmcia_rsrc serio_raw i915 soundcore pcmcia_core lpc_ich drm_kms_helper shpchp drm video wmi mac_hid i2c_algo_bit parport_pc ppdev lp parport 8139too firewire_ohci psmouse 8139cp firewire_core crc_itu_t mii

    ======== Done ========

```
#

---

### Post by varunendra on 2014-08-29
Since the previous driver (proprietary one) was installed with 'dkms', it should have automatically compiled/installed with each kernel upgrade, without requiring you to do anything manually. If it broke, then it probably will need further patching to successfully build again. But I am not much familiar with dkms based driver installations, so can't offer much help with that.

I suggest you test the native driver again and let us know how good or bad it performs. The rt2800usb driver has been changed a lot, and I hope the changes are mostly positive.

To try the native one, all you need to do is to simply remove the driver from blacklist entries -
```
sudo sed -i '/^blacklist rt2/ d' /etc/modprobe.d/blacklist.conf
```
..and delete the following file altogether -
```
sudo rm /etc/modprobe.d/blaclist.conf
```

Also, the "RT2800USB" entry in your /etc/pm/config.d/config file is not correct. First, the driver name should be in small letters, secondly, I think the recommended name for this file is 'modules'. So, please run these commands to delete the current file and create a new one with correct entry -
```
sudo rm /etc/pm/config.d/config
echo **"**SUSPEND_MODULES=\**[COLOR="#B22222"]"[/COLOR]**rt2800usb\**[COLOR="#B22222"]"[/COLOR]"** | sudo tee /etc/pm/config.d/modules
```
Please note there are TWO consequent double-quotes immediately after the second backslash (\) in the second command. I suggest you copy-paste the commands into terminal to avoid typing mistakes.

Reboot after this, and see if your wifi works again. If not, or if there are problems like frequent disconnection etc., report back and we'll troubleshoot it accordingly.

---

### Post by risva on 2014-08-29
Thanks a lot Dear Varunendra,

the wifi is up and running now!!

the ubuntu forum rocks!!

---

### Post by varunendra on 2014-08-29
> **risva said:**
> the ubuntu forum rocks!!

Indeed it does!! \\:D/

---

