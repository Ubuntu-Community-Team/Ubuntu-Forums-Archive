---
title: "Lenovo  G50-70 wireless problems"
date: 2015-03-17
forum: Networking &amp; Wireless
---

### Post by Daniel_Chamberlain on 2015-03-17
Hi guys very new to all of this and have tried a few things to solve. apparantly I should include this file so someone can help me faster, many thanks.

Basically I can use wired but not wireless, none of my networks show up 

[COLOR=#000080][B]
    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

santa-Lenovo-G50-70 3.16.0-30-generic x86_64,  Ubuntu 14.04.2 LTS, trusty

CPU    : Intel(R) Core(TM) i5-4210U CPU @ 1.70GHz
Memory : 3845 MB
Uptime : 17:06:47 up 9 min,  2 users,  load average: 1,07, 1,01, 0,57


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 08)
    Subsystem: Lenovo Device [17aa:380a]
    Kernel driver in use: r8169
02:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Lenovo Device [17aa:0621]
    Kernel driver in use: bcma-pci-bridge


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 105b:e065  
Bus 002 Device 003: ID 0bda:579a Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface                  Soft blocked  Hard blocked
0: ideapad_wlan: Wireless LAN        no            no
1: ideapad_bluetooth: Bluetooth      yes           no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

bcma                   52320  0 
ideapad_laptop         18278  0 
sparse_keymap          13948  1 ideapad_laptop
snd_soc_rt5640         93042  0 
snd_soc_rl6231         13037  1 snd_soc_rt5640
snd_soc_core          200204  1 snd_soc_rt5640
snd_pcm               104112  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine


module parameters ~~~~~~~~~~~~~~~~~~

ideapad_laptop  (1): no_bt_rfkill=N
snd_pcm       (2): maximum_substreams=4 | preallocate_dma=1


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=======o========o===========o=========o===========o==============o===========
 Interface & ID             | Type  | Driver | State     | Default | Speed     | Support      | HW Addr   
============================o=======o========o===========o=========o===========o==============o===========
 eth0  [Wired connection 1] | Wired | r8169  | connected | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         192.168.1.79
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254
    DNS:             192.168.1.254
----------------------------+-------+--------+-----------+---------+-----------+--------------+-----------


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
search home


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 192.168.1.254 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.770/0.810/0.851/0.049 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.018/0.021/0.025/0.005 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "ca_ES.UTF-8")
country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN
    (5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

           - 


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~



blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[bcma]
filename:       /lib/modules/3.16.0-30-generic/kernel/drivers/bcma/bcma.ko
srcversion:     D52E980A55E0AC3C372382C
depends:        

[ideapad_laptop]
filename:       /lib/modules/3.16.0-30-generic/kernel/drivers/platform/x86/ideapad-laptop.ko
srcversion:     3C69F59A7004A946EA51B4C
depends:        sparse-keymap
parm:           no_bt_rfkill:No rfkill for bluetooth. (bool)

[snd_soc_rt5640]
filename:       /lib/modules/3.16.0-30-generic/kernel/sound/soc/codecs/snd-soc-rt5640.ko
srcversion:     D9784021D8C822AC71D3297
depends:        snd-pcm,snd-soc-core,snd-soc-rl6231

[snd_soc_rl6231]
filename:       /lib/modules/3.16.0-30-generic/kernel/sound/soc/codecs/snd-soc-rl6231.ko
srcversion:     A9A4828818D1BE4F6603399
depends:        

[snd_soc_core]
filename:       /lib/modules/3.16.0-30-generic/kernel/sound/soc/snd-soc-core.ko
srcversion:     A808BD5FEF2FBADB4B1FB63
depends:        snd-pcm,snd-pcm-dmaengine,snd,snd-compress
parm:           pmdown_time:DAPM stream powerdown time (msecs) (int)

[snd_pcm]
filename:       /lib/modules/3.16.0-30-generic/kernel/sound/core/snd-pcm.ko
srcversion:     CAFAB0DF7563356E447F07C
depends:        snd,snd-timer
parm:           preallocate_dma:Preallocate DMA memory when the PCM devices are initialized. (int)
parm:           maximum_substreams:Maximum substreams with preallocated DMA memory. (int)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


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
modesetting.conf  : options cirrus modeset=1
                    options mgag200 modeset=1


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.16.0-30-generic.efi.signed root=UUID=58d9c0fc-5254-432d-9352-223171cc4158 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.039541] Initializing cgroup subsys net_cls
[    0.039553] Initializing cgroup subsys net_prio
[    0.687850] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.688391] audit: initializing netlink subsys (disabled)
[    0.825970] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   10.212514] bcma: bus0: Found chip with id 0xA886, rev 0x01 and package 0x08
[   10.212537] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x28, class 0x0)
[   10.212555] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x21, class 0x0)
[   10.212590] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x16, class 0x0)
[   10.212633] bcma: bus0: Core 3 found: UNKNOWN (manuf 0x43B, id 0x368, rev 0x00, class 0x0)
[   10.226639] bcma: bus0: Bus registered
[   14.312542] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.673628] audit: type=1400 audit(1426607862.393:68): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1091 comm="nm-dhcp-client." lport=57752 family="inet" sock_type="dgram" protocol=17
[   17.673639] audit: type=1400 audit(1426607862.393:69): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1091 comm="nm-dhcp-client." lport=53642 family="inet6" sock_type="dgram" protocol=17
[   18.640375] audit: type=1400 audit(1426607863.353:70): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1136 comm="nm-dhcp-client." lport=57752 family="inet" sock_type="dgram" protocol=17
[   18.640388] audit: type=1400 audit(1426607863.353:71): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1136 comm="nm-dhcp-client." lport=53642 family="inet6" sock_type="dgram" protocol=17

    ======== Done ========[/B][/COLOR]

---

