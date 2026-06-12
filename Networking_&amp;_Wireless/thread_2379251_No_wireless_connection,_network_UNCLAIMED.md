---
title: "No wireless connection, network UNCLAIMED"
date: 2017-12-03
forum: Networking &amp; Wireless
---

### Post by girand0 on 2017-12-03
Hi,
I have some troubles with wireless connection and need help. I'd be gratefult, thanks! 


My first trouble was WiFi disconnecting for few seconds/minutes ~once an hour. I found [this]("https://medium.com/@elmaxx/rtl8821ae-wifi-drivers-in-ubuntu-16-04-4c1286524afa") thread and installed drivers. After that i have no possibilities to connect wireless.
I find network UNCLAIMED. I also did [this]("https://ubuntuforums.org/showthread.php?t=1314693"), no result.


Some extra information:
- i tried to figure out the problem on my own, looking for answers on forums, but the more i find the more i'm stuck,
- i am a newbie at Linux


my system: **Ubuntu 16.04 LTS**
my kernel: [B]4.10.0.-40-generic
[/B]my network hardware: **Realtek RTL8821AE**


When i type:** sudo modprobe rtl8821ae**
i get the response: ```
**modprobe: ERROR: could not insert 'rtl8821ae': Required key not availible**
```


```
sudo lshw -C network


  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: enp1s0
       version: 10
       serial: c8:5b:76:f9:f6:ef
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-3_0.0.1 04/23/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:127 ioport:5000(size=256) memory:a4104000-a4104fff memory:a4100000-a4103fff
  *-network UNCLAIMED
       description: Network controller
       product: RTL8821AE 802.11ac PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: ioport:4000(size=256) memory:a4000000-a4003fff
  *-network
       description: Ethernet interface
       physical id: 3
       logical name: enp0s20f0u2
       serial: f6:90:77:b8:c6:41
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.76 link=yes multicast=yes
```




```
ifconfig


enp0s20f0u2 Link encap:Ethernet  HWaddr f6:90:77:b8:c6:41  
          inet addr:192.168.42.76  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::21cf:b53d:a1ac:67da/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7110 errors:2 dropped:0 overruns:0 frame:2
          TX packets:7340 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4347255 (4.3 MB)  TX bytes:1738971 (1.7 MB)


enp1s0    Link encap:Ethernet  HWaddr c8:5b:76:f9:f6:ef  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1802 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1802 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:139916 (139.9 KB)  TX bytes:139916 (139.9 KB)
```



```
lsmod

Module                  Size  Used by
rndis_host             16384  0
cdc_ether              16384  1 rndis_host
usbnet                 45056  2 rndis_host,cdc_ether
rfcomm                 77824  0
bnep                   20480  2
nls_iso8859_1          16384  1
rtsx_usb_ms            20480  0
memstick               16384  1 rtsx_usb_ms
uvcvideo               90112  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
videodev              172032  3 uvcvideo,videobuf2_core,videobuf2_v4l2
media                  40960  2 uvcvideo,videodev
snd_hda_codec_hdmi     49152  1
snd_hda_codec_conexant    24576  1
snd_hda_codec_generic    73728  1 snd_hda_codec_conexant
snd_soc_skl            65536  0
snd_soc_skl_ipc        49152  1 snd_soc_skl
snd_soc_sst_ipc        16384  1 snd_soc_skl_ipc
snd_soc_sst_dsp        28672  1 snd_soc_skl_ipc
snd_hda_ext_core       24576  1 snd_soc_skl
snd_soc_sst_match      16384  1 snd_soc_skl
intel_rapl             20480  0
snd_soc_core          233472  1 snd_soc_skl
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
snd_compress           20480  1 snd_soc_core
coretemp               16384  0
ac97_bus               16384  1 snd_soc_core
snd_pcm_dmaengine      16384  1 snd_soc_core
snd_hda_intel          36864  3
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_codec_generic
kvm                   593920  0
snd_hda_core           81920  7 snd_hda_intel,snd_hda_codec_conexant,snd_hda_codec,snd_hda_ext_core,snd_soc_skl,snd_hda_codec_hdmi,snd_hda_codec_generic
snd_hwdep              16384  1 snd_hda_codec
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
snd_pcm               102400  8 snd_hda_intel,snd_hda_codec,snd_pcm_dmaengine,snd_hda_ext_core,snd_hda_core,snd_soc_skl,snd_hda_codec_hdmi,snd_soc_core
pcbc                   16384  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
aesni_intel           167936  0
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
input_leds             16384  0
joydev                 20480  0
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
serio_raw              16384  0
snd_timer              32768  2 snd_seq,snd_pcm
snd                    77824  19 snd_compress,snd_hda_intel,snd_hwdep,snd_hda_codec_conexant,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_soc_core,snd_pcm
mac80211              782336  0
soundcore              16384  1 snd
cfg80211              602112  1 mac80211
mei_me                 40960  0
btusb                  45056  0
shpchp                 36864  0
mei                   102400  1 mei_me
btrtl                  16384  1 btusb
intel_pch_thermal      16384  0
ucsi                   16384  0
hci_uart               98304  0
btbcm                  16384  2 hci_uart,btusb
btqca                  16384  1 hci_uart
btintel                16384  2 hci_uart,btusb
bluetooth             557056  33 btrtl,hci_uart,btintel,btqca,bnep,btbcm,rfcomm,btusb
ideapad_laptop         28672  0
sparse_keymap          16384  1 ideapad_laptop
intel_lpss_acpi        16384  0
intel_lpss             16384  1 intel_lpss_acpi
tpm_crb                16384  0
mac_hid                16384  0
acpi_pad              180224  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
autofs4                40960  2
rtsx_usb_sdmmc         28672  0
rtsx_usb               20480  2 rtsx_usb_sdmmc,rtsx_usb_ms
hid_generic            16384  0
usbhid                 53248  0
nouveau              1601536  1 
i915                 1449984  148
mxm_wmi                16384  1 nouveau
ttm                    98304  1 nouveau
i2c_algo_bit           16384  2 nouveau,i915
drm_kms_helper        151552  2 nouveau,i915
psmouse               139264  0
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   352256  9 nouveau,i915,ttm,drm_kms_helper
ahci                   36864  3
r8169                  81920  0
libahci                32768  1 ahci
mii                    16384  2 r8169,usbnet
video                  40960  3 nouveau,i915,ideapad_laptop
wmi                    16384  3 mxm_wmi,nouveau,ideapad_laptop
pinctrl_sunrisepoint    28672  0
i2c_hid                20480  0
pinctrl_intel          20480  1 pinctrl_sunrisepoint
hid                   118784  3 i2c_hid,hid_generic,usbhid
fjes                   77824  0
```

---

### Post by Yellow Pasque on 2017-12-04
[https://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules](https://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules)

---

