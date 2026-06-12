---
title: "Dell Inspiron 3542 WIfi Not Working After New Installation"
date: 2016-06-15
forum: Networking &amp; Wireless
---

### Post by Akintunde on 2016-06-15
Hello Everyone. 

I installed ubuntu studio on my external hard drive and i did the  partition correctly. Now that i booted my pc from my externel hard  drive,

My wifi is not working again,

While i doing research on what coursed it. i found a script here that will collect information concerning the hardware devices,

Here is the information i got from a script i got here on the forum. ```
  
    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

bekbek-Dell-Inspiron-3542-Notebook-PC 4.4.0-21-lowlatency i686,  Ubuntu 16.04 LTS, xenial

CPU    : Intel(R) Core(TM) i3-4005U CPU @ 1.70GHz
Memory : 3946 MB
Uptime : 06:28:18 up 16 min,  1 user,  load average: 0.38, 0.63, 0.61


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

06:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Dell Wireless 1704 802.11n + BT 4.0 [1028:0016]
    Kernel driver in use: bcma-pci-bridge
--
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Dell RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [1028:0651]
    Kernel driver in use: r8169
    Kernel modules: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 006: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 005: ID 0a5c:21d7 Broadcom Corp. BCM43142 Bluetooth 4.0
Bus 001 Device 004: ID 0bda:5756 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 1058:0820 Western Digital Technologies, Inc. My Passport Ultra (WDBMWV, WDBZFP)
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 12d1:14db Huawei Technologies Co., Ltd. E353/E3131
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface             Soft blocked  Hard blocked
0: dell-rbtn: Wireless LAN      no            no
1: hci0: Bluetooth              no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

dell_wmi               16384  0
sparse_keymap          16384  1 dell_wmi
snd_soc_rt5640         81920  0
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          192512  1 snd_soc_rt5640
snd_pcm                94208  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd  _hda_codec,snd_hda_intel,snd_pcm_dmaengine,snd_hda  _core
bcma                   49152  0
wmi                    20480  2 dell_led,dell_wmi
video                  36864  3 i915,dell_wmi,dell_laptop


module parameters ~~~~~~~~~~~~~~~~~~

snd_pcm       (2): maximum_substreams=4 | preallocate_dma=1
video         (5): allow_duplicates=N | brightness_switch_enabled=Y | device_id_scheme=N | disable_backlight_sysfs_if=-1 | only_lcd=N
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


================o======o========o========o========  =o===========o==============o===========
 Interface & ID | Type | Driver | State  | Default | Speed     | Support      | HW Addr   
================o======o========o========o========  =o===========o==============o===========
                |      |        |        |         |           |              |           
----------------+------+--------+--------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


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


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.8.1     0.0.0.0         UG    100    0        0 enx0c5b8f279a64
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enx0c5b8f279a64
192.168.8.0     0.0.0.0         255.255.255.0   U     100    0        0 enx0c5b8f279a64

--- 192.168.8.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 26.865/27.536/28.208/0.691 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.027/0.028/0.030/0.005 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

           - 


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~



blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[dell_wmi]
filename:       /lib/modules/4.4.0-21-lowlatency/kernel/drivers/platform/x86/dell-wmi.ko
srcversion:     FDD089E9C00D3F33D3BDAE6
depends:        wmi,sparse-keymap,video

[snd_soc_rt5640]
filename:       /lib/modules/4.4.0-21-lowlatency/kernel/sound/soc/codecs/snd-soc-rt5640.ko
srcversion:     A6D6540909F257E51262AC3
depends:        snd-pcm,snd-soc-core,snd-soc-rl6231

[snd_soc_rl6231]
filename:       /lib/modules/4.4.0-21-lowlatency/kernel/sound/soc/codecs/snd-soc-rl6231.ko
srcversion:     B13C9238112378D4A5BE0A2
depends:        

[snd_soc_core]
filename:       /lib/modules/4.4.0-21-lowlatency/kernel/sound/soc/snd-soc-core.ko
srcversion:     4A948A7C95514236A73EACA
depends:        snd-pcm,snd-pcm-dmaengine,snd,snd-compress,ac97_bus
parm:           pmdown_time:DAPM stream powerdown time (msecs) (int)

[snd_pcm]
filename:       /lib/modules/4.4.0-21-lowlatency/kernel/sound/core/snd-pcm.ko
srcversion:     5B63C9977586A34681BC335
depends:        snd,snd-timer
parm:           preallocate_dma:Preallocate DMA memory when the PCM devices are initialized. (int)
parm:           maximum_substreams:Maximum substreams with preallocated DMA memory. (int)

[bcma]
filename:       /lib/modules/4.4.0-21-lowlatency/kernel/drivers/bcma/bcma.ko
srcversion:     C5CB08F60A0C6A00FBF57B0
depends:        

[wmi]
filename:       /lib/modules/4.4.0-21-lowlatency/kernel/drivers/platform/x86/wmi.ko
srcversion:     742495B9B598D29925E37F8
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)

[video]
filename:       /lib/modules/4.4.0-21-lowlatency/kernel/drivers/acpi/video.ko
srcversion:     41A518299C75FE6E97C4C2B
depends:        
parm:           brightness_switch_enabled:bool
parm:           allow_duplicates:bool
parm:           disable_backlight_sysfs_if:int
parm:           device_id_scheme:bool
parm:           only_lcd:bool


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


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

BOOT_IMAGE=/vmlinuz-4.4.0-21-lowlatency root=UUID=64eacf90-b073-45bf-a358-c3054dddf2e2 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.019121] Initializing cgroup subsys net_cls
[    0.019126] Initializing cgroup subsys net_prio
[    1.045142] audit: initializing netlink subsys (disabled)
[    1.094297] microcode: Microcode Update Driver: v2.01 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.501075] wmi: Mapper loaded
[    1.524740] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   11.294288] bcma: bus0: Found chip with id 43142, rev 0x01 and package 0x08
[   11.294314] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x28, class 0x0)
[   11.294333] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x21, class 0x0)
[   11.294369] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x16, class 0x0)
[   11.294412] bcma: bus0: Core 3 found: UNKNOWN (manuf 0x43B, id 0x368, rev 0x00, class 0x0)
[   11.312018] bcma: bus0: Bus registered
[   13.054795] hid-rmi 0018:06CB:2985.0001: firmware id: 1567123
[   13.514224] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2
[   13.514230] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[   29.206022] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  584.676014] cdc_ether 2-1:1.0 eth0: register 'cdc_ether' at usb-0000:00:14.0-1, CDC Ethernet Device, <MAC ID removed>

    ======== Done ========
```

Kindly go through it and let me know how i could solve the issue.

Thanks 

I look forward to your responses

---

### Post by vanadium on 2016-06-15
You have a broadcom wireless internet card, which has been trouble for some time. I thought it was now supported with the current kernel. Maybe try this: [https://sites.google.com/site/easylinuxtipsproject/internet#TOC-Broadcom:-install-the-right-driver](https://sites.google.com/site/easylinuxtipsproject/internet#TOC-Broadcom:-install-the-right-driver)

---

### Post by ajgreeny on 2016-06-15
Also worth looking at [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

---

