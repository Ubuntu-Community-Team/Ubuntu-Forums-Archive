---
title: "Xubuntu 18.10 wifi tl-wn821n shows SSIDs but can not connect. Unplug and plug works"
date: 2019-02-04
forum: Networking &amp; Wireless
---

### Post by raullopezgn on 2019-02-04
Hi, recently I have installed Xubuntu 18.10 (dual boot with Windows). At start the dongle tp-link tl-wn821n shows SSIDs and if I click on my wifi it can not connect to Internet. But if I unplug the dongle and I plug in it again it connects to my wifi :o

I try to install Xubuntu 18.04, Lubuntu 18.10, 18.04 and 16.10 and always the same problem. I will paste all the info that you may be will need to help me.
**Important!!** The code of the command _dmesg_ it could have relevant info.

Thank you in advance for all your responses!!
------------------------------------------------------

**lsusb**
** It doesn't appear any description of the dongle :(
```
Bus 002 Device 002: ID 8087:8001 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8009 Intel Corp. 
Bus 003 Device 004: ID 2357:0107  
Bus 003 Device 003: ID 046d:c05a Optical Mouse
Bus 003 Device 002: ID 1c4f:0026  Micro Keyboard
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

**iwconfig**
```

lo           no wireless extensions.
enp3s0    no wireless extensions.

wlx503eaa3a0282  IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off    Power Management:off
```

**inxi -Fnn** 
** If I unplug the dongle and I plug in it again, the _"state: down" changes to "state: up"_;
When I discovered that before I unplugged the dongle I tried:
[I]ifconfig wlx503eaa3a0282 up
service network-manager restart
[/I]
But it didn't work :(

```

Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  driver: r8169 
  IF: enp3s0 state: down mac: 74:d4:35:a9:d2:4a 
  IF-ID-1: wlx503eaa3a0282 state: down mac: 50:3e:aa:3a:02:82
```

**lshw -C network** 
**When I unplug the dongle and I plug in again, the "_link=no" option change to "link=yes"_ and it also appears ip=xxx.xxx.x.xxx
```

*-network
       descripción: Interfaz inalámbrica
       id físico: 2
       información del bus: usb@3:9
       nombre lógico: wlx503eaa3a0282
       serie: 50:3e:aa:3a:02:82
       capacidades: ethernet physical wireless
       configuración: broadcast=yes driver=rtl8xxxu driverversion=4.18.0-13-generic firmware=N/A
       link=no multicast=yes wireless=IEEE 802.11

```

**dmesg (part 1/2)**
** This code appear before the dongle is unplugged. _Below this code I paste the code after I unplug and plug the dongle again_
```

[    0.698373] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.698379] r8169 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[    0.698868] r8169 0000:03:00.0 eth0: RTL8168evl/8111evl, 74:d4:35:a9:d2:4a, XID 2c900800, IRQ 30
[    0.698870] r8169 0000:03:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]

[    8.618510] usb 3-9: rtl8192eu_rx_iqk_path_b: Path B RX IQK failed!
[    8.642215] usb 3-9: rtl8192eu_rx_iqk_path_b: Path B RX IQK failed!
[    8.704814] usb 3-9: rtl8192eu_rx_iqk_path_b: Path B RX IQK failed!
[    8.728522] usb 3-9: rtl8192eu_rx_iqk_path_b: Path B RX IQK failed!
[    8.787041] usbcore: registered new interface driver rtl8xxxu

[    8.823662] rtl8xxxu 3-9:1.0 wlx503eaa3a0282: renamed from wlan0

[   16.701150] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[   16.873359] r8169 0000:03:00.0 enp3s0: link down
[   16.873431] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[   16.875521] IPv6: ADDRCONF(NETDEV_UP): wlx503eaa3a0282: link is not ready
[   16.881216] IPv6: ADDRCONF(NETDEV_UP): wlx503eaa3a0282: link is not ready
[   17.339945] IPv6: ADDRCONF(NETDEV_UP): wlx503eaa3a0282: link is not ready
[   19.667838] wlx503eaa3a0282: authenticate with b8:bc:1b:22:d1:24
[   19.671795] wlx503eaa3a0282: send auth to b8:bc:1b:22:d1:24 (try 1/3)
[   19.872046] wlx503eaa3a0282: send auth to b8:bc:1b:22:d1:24 (try 2/3)
[   20.076076] wlx503eaa3a0282: send auth to b8:bc:1b:22:d1:24 (try 3/3)
[   20.280103] wlx503eaa3a0282: authentication with b8:bc:1b:22:d1:24 timed out

[  282.005339] IPv6: ADDRCONF(NETDEV_UP): wlx503eaa3a0282: link is not ready
[  395.308499] r8169 0000:03:00.0: invalid large VPD tag 7f at offset 0
[  583.057931] wlx503eaa3a0282: authenticate with b8:bc:1b:22:d1:24
[  583.067051] wlx503eaa3a0282: send auth to b8:bc:1b:22:d1:24 (try 1/3)
[  583.268108] wlx503eaa3a0282: send auth to b8:bc:1b:22:d1:24 (try 2/3)
[  583.472144] wlx503eaa3a0282: send auth to b8:bc:1b:22:d1:24 (try 3/3)
[  583.676107] wlx503eaa3a0282: authentication with b8:bc:1b:22:d1:24 timed out
```

**dmesg (part 2/2)**
** _Code after I have unplugged and I have plugged the dongle again_
```

[ 3373.894299] usb 3-9: USB disconnect, device number 4
[ 3373.979145] usb 3-9: rtl8192eu_active_to_emu: Disabling MAC timed out
[ 3373.979147] usb 3-9: disconnecting
[ 3378.728117] usb 3-9: new high-speed USB device number 5 using xhci_hcd
[ 3378.876619] usb 3-9: New USB device found, idVendor=2357, idProduct=0107, bcdDevice= 2.00
[ 3378.876624] usb 3-9: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 3378.876627] usb 3-9: Product: 802.11n NIC 
[ 3378.876630] usb 3-9: Manufacturer: Realtek 
[ 3378.876633] usb 3-9: SerialNumber: 00e04c000001
[ 3378.878481] usb 3-9: This Realtek USB WiFi dongle (0x2357:0x0107) is untested!
[ 3378.936446] usb 3-9: Vendor: Realtek
[ 3378.936448] usb 3-9: Product: 802.11n NI
[ 3378.936450] usb 3-9: Serial: 
[ 3378.936453] usb 3-9: rtl8192eu_parse_efuse: dumping efuse (0x200 bytes):

[ 3378.936581] usb 3-9: RTL8192EU rev B (SMIC) 2T2R, TX queues 3, WiFi=1, BT=0, GPS=0, HI PA=0
[ 3378.936583] usb 3-9: RTL8192EU MAC: 50:3e:aa:3a:02:82
[ 3378.936585] usb 3-9: rtl8xxxu: Loading firmware rtlwifi/rtl8192eu_nic.bin
[ 3378.936684] usb 3-9: Firmware revision 19.0 (signature 0x92e1)
[ 3379.743896] usb 3-9: rtl8192eu_rx_iqk_path_b: Path B RX IQK failed!
[ 3379.856691] rtl8xxxu 3-9:1.0 wlx503eaa3a0282: renamed from wlan0
[ 3379.879639] IPv6: ADDRCONF(NETDEV_UP): wlx503eaa3a0282: link is not ready
[ 3379.885182] IPv6: ADDRCONF(NETDEV_UP): wlx503eaa3a0282: link is not ready
[ 3379.927114] IPv6: ADDRCONF(NETDEV_UP): wlx503eaa3a0282: link is not ready
[ 3380.993015] wlx503eaa3a0282: authenticate with b8:bc:1b:22:d1:24
[ 3380.996876] wlx503eaa3a0282: send auth to b8:bc:1b:22:d1:24 (try 1/3)
[ 3380.998294] wlx503eaa3a0282: authenticated
[ 3381.004019] wlx503eaa3a0282: associate with b8:bc:1b:22:d1:24 (try 1/3)
[ 3381.007078] wlx503eaa3a0282: RX AssocResp from b8:bc:1b:22:d1:24 (capab=0x411 status=0 aid=3)
[ 3381.007620] usb 3-9: rtl8xxxu_bss_info_changed: HT supported
[ 3381.008157] wlx503eaa3a0282: associated
[ 3381.051685] IPv6: ADDRCONF(NETDEV_CHANGE): wlx503eaa3a0282: link becomes ready
```

**lsmod**
```

rtl8xxxu              122880  0
mac80211              794624  1 rtl8xxxu
r8169                  86016  0
arc4                   16384  2
snd_soc_rt5640        126976  0
snd_hda_codec_realtek   106496  1
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          229376  1 snd_soc_rt5640
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
snd_hda_codec_hdmi     49152  1
snd_compress           20480  1 snd_soc_core
ac97_bus               16384  1 snd_soc_core
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
snd_hda_intel          40960  4
radeon               1462272  11
snd_hda_codec         126976  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
kvm_intel             208896  0
ttm                   106496  1 radeon
snd_hda_core           81920  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
joydev                 20480  0
snd_pcm_dmaengine      16384  1 snd_soc_core
snd_seq_midi           16384  0
kvm                   622592  1 kvm_intel
input_leds             16384  0
cfg80211              663552  1 mac80211
snd_seq_midi_event     16384  1 snd_seq_midi
drm_kms_helper        172032  1 radeon
snd_hwdep              20480  1 snd_hda_codec
snd_rawmidi            32768  1 snd_seq_midi
snd_pcm                98304  7 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_soc_rt5640,snd_soc_core,snd_hda_core,snd_pcm_dmaengine
mei_me                 40960  0
snd_seq                65536  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              32768  2 snd_seq,snd_pcm
drm                   458752  13 drm_kms_helper,radeon,ttm
i2c_algo_bit           16384  1 radeon
fb_sys_fops            16384  1 drm_kms_helper
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
snd                    81920  21 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_compress,snd_soc_core,snd_pcm,snd_rawmidi
mei                    98304  1 mei_me
crc32_pclmul           16384  0
soundcore              16384  1 snd
video                  45056  0
ghash_clmulni_intel    16384  0
pcbc                   16384  0
acpi_pad              180224  0
mac_hid                16384  0
aesni_intel           200704  0
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
glue_helper            16384  1 aesni_intel
intel_cstate           20480  0
intel_rapl_perf        16384  0
sch_fq_codel           20480  6
parport_pc             36864  1
ppdev                  20480  0
lp                     20480  0
parport                49152  3 parport_pc,lp,ppdev
ip_tables              24576  0
x_tables               40960  1 ip_tables
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
hid                   126976  2 usbhid,hid_generic
gpio_ich               16384  0
i2c_i801               28672  0
ahci                   40960  3
libahci                32768  1 ahci
lpc_ich                24576  0
mii                    16384  1 r8169

```

**ifconfig**
```

wlx503eaa3a0282: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 50:3e:aa:3a:02:82  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

--------END---------

---

### Post by chili555 on 2019-02-04
After a boot try if this gets it working without a re-plug:
```
sudo modprobe -r rtl8xxxu
sudo modprobe rtl8xxxu
```Thanks.

-------------------
Possible reference: [https://forums.linuxmint.com/viewtopic.php?t=274947](https://forums.linuxmint.com/viewtopic.php?t=274947)

> 
my guess is the driver isn't waiting for the hardware to be fully initialized and thus it doesn't set the device up correctly the first time it gets loaded. 


---

### Post by raullopezgn on 2019-02-04
@chili555 it worked!! Thank you very much, I have spent so many hours looking for other post.... :(

After I have tested your suggestion (x2-3 times) I have read the post you have mentioned. _In order to apply the workaround permanently. The solution is_:

```

printf '#!/bin/sh\nmodprobe -r rtl8xxxu\nmodprobe rtl8xxxu\n' | sudo tee /etc/rc.local
sudo chmod +x /etc/rc.local

```

> 
PS: This overwrites an existing /etc/rc.local file - don't use should you have created one yourself already, just append the workaround to the existing file then.

---

