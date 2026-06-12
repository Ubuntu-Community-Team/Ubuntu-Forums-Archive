---
title: "ASUS X205TA netbook -- &quot;No network devices are available&quot;"
date: 2017-11-25
forum: Networking &amp; Wireless
---

### Post by weyland42 on 2017-11-25
I've installed Ubuntu 17.04 Mate and most of it works fine except the wifi.

This is the output from **bapoumba**'s advice in the FAQ:

```


    ======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


X205TAW 4.14.0-041400-generic x86_64,  Ubuntu 17.04, zesty


CPU    : Intel(R) Atom(TM) CPU  Z3735F @ 1.33GHz
Memory : 1925 MB
Uptime : 09:32:16 up 5 min,  1 user,  load average: 0.53, 0.31, 0.14




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~






lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 1d57:0008 Xenta 
Bus 001 Device 005: ID 090c:1000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) Flash Drive
Bus 001 Device 003: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 001 Device 002: ID 0bda:57b5 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~






rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface     Soft blocked  Hard blocked
0: hci0: Bluetooth      no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


snd_soc_sst_cht_bsw_rt5645    20480  2
brcmfmac              315392  0
brcmutil               16384  1 brcmfmac
cfg80211              614400  1 brcmfmac
asus_nb_wmi            28672  0
asus_wmi               28672  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
snd_soc_rt5645        147456  2 snd_soc_sst_cht_bsw_rt5645
snd_soc_rl6231         16384  1 snd_soc_rt5645
snd_soc_sst_match      16384  2 snd_soc_sst_cht_bsw_rt5645,snd_intel_sst_acpi
snd_soc_core          229376  4 snd_soc_tlv320aic31xx,snd_soc_sst_cht_bsw_rt5645,s  nd_soc_sst_atom_hifi2_platform,snd_soc_rt5645
snd_pcm                98304  7 snd_hdmi_lpe_audio,snd_pcm_dmaengine,snd_soc_tlv32  0aic31xx,snd_soc_sst_cht_bsw_rt5645,snd_soc_sst_at  om_hifi2_platform,snd_soc_rt5645,snd_soc_core
wmi                    24576  1 asus_wmi
video                  40960  3 asus_wmi,int3406_thermal,i915




module parameters ~~~~~~~~~~~~~~~~~~


asus_nb_wmi   (1): wapf=0
brcmfmac      (3): 
cfg80211      (3): bss_entries_limit=1000 | cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
snd_pcm       (2): maximum_substreams=4 | preallocate_dma=1
snd_soc_rt5645  (1): quirk=4294967295
video         (6): allow_duplicates=N | brightness_switch_enabled=Y | device_id_scheme=N | disable_backlight_sysfs_if=-1 | only_lcd=N | report_key_events=-1
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
plugins=ifupdown,keyfile


[ifupdown]
managed=false




NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~
 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~




nameserver 127.0.0.53




Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


--- 127.0.0.53 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1027ms
rtt min/avg/max/mdev = 0.101/0.104/0.108/0.010 ms




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : "en_GB.UTF-8")
global
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)






iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~


           - 




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~






blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[snd_soc_sst_cht_bsw_rt5645]
filename:       /lib/modules/4.14.0-041400-generic/kernel/sound/soc/intel/boards/snd-soc-sst-cht-bsw-rt5645.ko
srcversion:     5163ED5D20904FE88F44654
depends:        snd-soc-core,snd-soc-rt5645,snd-soc-sst-match,snd-pcm


[brcmfmac]
filename:       /lib/modules/4.14.0-041400-generic/kernel/drivers/net/wireless/broadcom/brcm80211/brcmfmac/brcmfmac.ko
firmware:       brcm/brcmfmac4373-sdio.bin
firmware:       brcm/brcmfmac4356-sdio.bin
firmware:       brcm/brcmfmac4354-sdio.bin
firmware:       brcm/brcmfmac43455-sdio.bin
firmware:       brcm/brcmfmac43430-sdio.bin
firmware:       brcm/brcmfmac43430a0-sdio.bin
firmware:       brcm/brcmfmac4339-sdio.bin
firmware:       brcm/brcmfmac43362-sdio.bin
firmware:       brcm/brcmfmac4335-sdio.bin
firmware:       brcm/brcmfmac43340-sdio.bin
firmware:       brcm/brcmfmac4334-sdio.bin
firmware:       brcm/brcmfmac4330-sdio.bin
firmware:       brcm/brcmfmac4329-sdio.bin
firmware:       brcm/brcmfmac43241b5-sdio.bin
firmware:       brcm/brcmfmac43241b4-sdio.bin
firmware:       brcm/brcmfmac43241b0-sdio.bin
firmware:       brcm/brcmfmac43143-sdio.bin
firmware:       brcm/brcmfmac4373.bin
firmware:       brcm/brcmfmac43569.bin
firmware:       brcm/brcmfmac43242a.bin
firmware:       brcm/brcmfmac43236b.bin
firmware:       brcm/brcmfmac43143.bin
firmware:       brcm/brcmfmac4371-pcie.bin
firmware:       brcm/brcmfmac4366c-pcie.bin
firmware:       brcm/brcmfmac4366b-pcie.bin
firmware:       brcm/brcmfmac4365c-pcie.bin
firmware:       brcm/brcmfmac4365b-pcie.bin
firmware:       brcm/brcmfmac4359-pcie.bin
firmware:       brcm/brcmfmac4358-pcie.bin
firmware:       brcm/brcmfmac43570-pcie.bin
firmware:       brcm/brcmfmac4356-pcie.bin
firmware:       brcm/brcmfmac4350c2-pcie.bin
firmware:       brcm/brcmfmac4350-pcie.bin
firmware:       brcm/brcmfmac43602-pcie.bin
srcversion:     A717E9FBFC1F3CD772070C8
depends:        brcmutil,cfg80211
parm:           txglomsz:Maximum tx packet chain size [SDIO] (int)
parm:           debug:Level of debug output (int)
parm:           p2pon:Enable legacy p2p management functionality (int)
parm:           feature_disable:Disable features (int)
parm:           alternative_fw_path:Alternative firmware path (string)
parm:           fcmode:Mode of firmware signalled flow control (int)
parm:           roamoff:Do not use internal roaming engine (int)


[brcmutil]
filename:       /lib/modules/4.14.0-041400-generic/kernel/drivers/net/wireless/broadcom/brcm80211/brcmutil/brcmutil.ko
srcversion:     389318E018771B5453D0B02
depends:        


[cfg80211]
filename:       /lib/modules/4.14.0-041400-generic/kernel/net/wireless/cfg80211.ko
srcversion:     784748F60B5390682360B5B
depends:        
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[asus_nb_wmi]
filename:       /lib/modules/4.14.0-041400-generic/kernel/drivers/platform/x86/asus-nb-wmi.ko
srcversion:     EFAEA05A7B63FEF79202AB2
depends:        asus-wmi
parm:           wapf:WAPF value (uint)


[asus_wmi]
filename:       /lib/modules/4.14.0-041400-generic/kernel/drivers/platform/x86/asus-wmi.ko
srcversion:     78A01AABF15FB31C7D98CE1
depends:        video,wmi,sparse-keymap


[snd_soc_rt5645]
filename:       /lib/modules/4.14.0-041400-generic/kernel/sound/soc/codecs/snd-soc-rt5645.ko
srcversion:     34C06D71C005A4B3DE1BA9A
depends:        snd-pcm,snd-soc-core,snd-soc-rl6231
parm:           quirk:RT5645 pdata quirk override (uint)


[snd_soc_rl6231]
filename:       /lib/modules/4.14.0-041400-generic/kernel/sound/soc/codecs/snd-soc-rl6231.ko
srcversion:     93EFBCB1B1EB1E2C6C9ACDA
depends:        


[snd_soc_sst_match]
filename:       /lib/modules/4.14.0-041400-generic/kernel/sound/soc/intel/common/snd-soc-sst-match.ko
srcversion:     D01809A3466D08BBB1D0D9E
depends:        


[snd_soc_core]
filename:       /lib/modules/4.14.0-041400-generic/kernel/sound/soc/snd-soc-core.ko
srcversion:     04E629A1EB742FC6B315EBE
depends:        snd-pcm,snd-pcm-dmaengine,snd,snd-compress,ac97_bus
parm:           pmdown_time:DAPM stream powerdown time (msecs) (int)


[snd_pcm]
filename:       /lib/modules/4.14.0-041400-generic/kernel/sound/core/snd-pcm.ko
srcversion:     A0D901D3C6E2411A8C50D02
depends:        snd,snd-timer
parm:           preallocate_dma:Preallocate DMA memory when the PCM devices are initialized. (int)
parm:           maximum_substreams:Maximum substreams with preallocated DMA memory. (int)


[wmi]
filename:       /lib/modules/4.14.0-041400-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     05EE945754B33DCD0B491F9
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


[video]
filename:       /lib/modules/4.14.0-041400-generic/kernel/drivers/acpi/video.ko
srcversion:     ED19F1AE9203CB1482B1A60
depends:        
parm:           brightness_switch_enabled:bool
parm:           allow_duplicates:bool
parm:           disable_backlight_sysfs_if:int
parm:           report_key_events:0: none, 1: output changes, 2: brightness changes, 3: all (int)
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


BOOT_IMAGE=/boot/vmlinuz-4.14.0-041400-generic.efi.signed root=/dev/mapper/ubuntu--mate--vg-root ro quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    2.147379] audit: initializing netlink subsys (disabled)
[    6.018441] rt5645 i2c-10EC5648:00: i2c-10EC5648:00 supply avdd not found, using dummy regulator
[    6.018475] rt5645 i2c-10EC5648:00: i2c-10EC5648:00 supply cpvdd not found, using dummy regulator
[    6.045731] asus_wmi: ASUS WMI generic driver loaded
[    6.084888] asus_wmi: Initialization: 0x1
[    6.085023] asus_wmi: BIOS WMI version: 7.9
[    6.085120] asus_wmi: SFUN value: 0x37
[    6.088606] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input10
[    6.096109] asus_wmi: Number of fans: 1
[    6.370177] brcmfmac: brcmf_fw_map_chip_to_name: using brcm/brcmfmac43340-sdio.bin for chip 0x00a94c(43340) rev 0x000002
[    6.379056] brcmfmac mmc0:0001:1: Direct firmware load for brcm/brcmfmac43340-sdio.txt failed with error -2
[    6.860776] cht-bsw-rt5645 cht-bsw-rt5645: BIOS Routing: AIF2 connected
[    6.860781] cht-bsw-rt5645 cht-bsw-rt5645: quirk SSP0_AIF2 enabled
[    6.879236] cht-bsw-rt5645 cht-bsw-rt5645: snd-soc-dummy-dai <-> media-cpu-dai mapping ok
[    6.879307] cht-bsw-rt5645 cht-bsw-rt5645: snd-soc-dummy-dai <-> deepbuffer-cpu-dai mapping ok
[    6.879650] cht-bsw-rt5645 cht-bsw-rt5645: rt5645-aif2 <-> ssp0-port mapping ok
[    6.939633] input: chtrt5645 Headset as /devices/platform/80860F28:00/cht-bsw-rt5645/sound/card1/input14
[    7.421364] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    9.386253] brcmfmac: brcmf_sdio_htclk: HT Avail timeout (1000000): clkctl 0x50
[   10.393322] brcmfmac: brcmf_sdio_htclk: HT Avail timeout (1000000): clkctl 0x50


    ======== Done ========
```

And this is **inxi -Fi**:

```
[Sat 2017-11-25 15:23:28]~>> inxi -FiSystem:    Host: X205TAW Kernel: 4.14.0-041400-generic x86_64 (64 bit)
           Desktop: MATE 1.18.0  Distro: Ubuntu 17.04
Machine:   Device: laptop System: ASUSTeK product: X205TAW v: 1.0
           Mobo: ASUSTeK model: X205TAW v: 1.0
           UEFI: American Megatrends v: X205TAW.201 date: 09/18/2015
Battery    BATC: charge: 22.7 Wh 51.3% condition: 44.2/50.0 Wh (88%)
CPU:       Quad core Intel Atom Z3735F (-MCP-) cache: 1024 KB 
           clock speeds: max: 1832 MHz 1: 1332 MHz 2: 1332 MHz 3: 1332 MHz
           4: 1332 MHz
Graphics:  Card: Intel Atom Processor Z36xxx/Z37xxx Series Graphics & Display
           Display Server: X.Org 1.19.3 drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1366x768@60.06hz
           GLX Renderer: Mesa DRI Intel Bay Trail GLX Version: 3.0 Mesa 17.0.3
Audio:     Card-1 Intel HDMI/DP LPE Audio driver: HdmiLpeAudio
           Card-2 chtrt5645 driver: chtrt5645
           Sound: Advanced Linux Sound Architecture v: k4.14.0-041400-generic
Network:   Card: Failed to Detect Network Card!
Drives:    HDD Total Size: 31.5GB (21.8% used)
           ID-1: /dev/mmcblk1 model: N/A size: 31.3GB
           ID-2: USB /dev/sda model: Flash_Disk size: 31.5GB
Partition: ID-1: / size: 27G used: 4.6G (19%) fs: ext4 dev: /dev/dm-0
           ID-2: swap-1 size: 2.07GB used: 0.00GB (0%) fs: swap dev: /dev/dm-1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 30.0C mobo: N/A
           Fan Speeds (in rpm): cpu: 0
Info:      Processes: 178 Uptime: 1 min Memory: 339.8/1925.4MB
           Client: Shell (bash) inxi: 2.3.8 
```

---

### Post by jeremy31 on 2017-11-25
Can you post results for ```
ls /sys/firmware/efi/efivars/ | grep nvram
```

---

### Post by weyland42 on 2017-11-25
[Sat 2017-11-25 16:49:11]**~>> ls /sys/firmware/efi/efivars | grep nvram**
**nvram-74b00bd9-805a-4d61-b51f-43268123d113**

---

### Post by jeremy31 on 2017-11-25
```
sudo cp /sys/firmware/efi/efivars/nvram-74b00bd9-805a-4d61-b51f-43268123d113   /lib/firmware/brcm/brcmfmac43340-sdio.txt
```

Reboot and see how it works

---

### Post by weyland42 on 2017-11-25
YES! Thank you so much, Jeremy. I have wifi now. Haven't done anything with it yet.

Thanks again.

---

