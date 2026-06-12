---
title: "can't connect to internet at all after installing ubuntu 16.04"
date: 2018-01-27
forum: Networking &amp; Wireless
---

### Post by whomaniac on 2018-01-27
Hello,
I tried fixing the problem myself using threads on this forum and others, but only managed to make the situation worse!!!

I started from having no wifi to having no internet even if I use a wired connection!!

I have a ThinkPad A475 (amd).
There is no hardware problem because when I had windows installed wifi worked!

Since I am doing more damage by trying to figure this out on my own I decided to ask for some help.

lspci | grep -i net:
```

01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0e)

```

ifconfig:
```

lo        Link encap:Local Loopback            inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:17604 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17604 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1311637 (1.3 MB)  TX bytes:1311637 (1.3 MB)



```

iwconfig:
```

lo        no wireless extensions.

wwp0s18u1u2i12  no wireless extensions.

```

The second weird interface (wwp0s18u1u2i12 ) came from changing some file. I don't remember how I did it.

sudo lshw -C network:
```

  *-network UNCLAIMED
       description: Ethernet controller
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 0e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list
       configuration: latency=0
       resources: ioport:2400(size=256) memory:f0d14000-f0d14fff memory:f0d00000-f0d03fff
  *-network DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: wwp0s18u1u2i12
       serial: 36:96:57:9f:69:da
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_mbim driverversion=22-Aug-2005 firmware=CDC MBIM link=no multicast=yes

```

cat /etc/network/interfaces:
```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


auto eth0
iface eth0 inet dhcp 

```

I added eth0 myself...

cat /etc/NetworkManager/NetworkManager.conf:
```

[main]plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false

```

cat /etc/NetworkManager/NetworkManager.state:
```

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

```



Please Help!!!!!

---

### Post by whomaniac on 2018-01-27
Very Important:
[https://pastebin.ubuntu.com/26471296/](https://pastebin.ubuntu.com/26471296/)

---

### Post by praseodym on 2018-01-27
Please run
```

echo -e "auto lo\niface lo inet loopback" | sudo tee /etc/network/interfaces
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
echo r8168 | sudo tee -a /etc/modules
```
Reboot (does LAN work?) and show
```

lspci -nnk
usb-devices
lsmod
iwconfig
sudo iwlist scan
```

---

### Post by whomaniac on 2018-01-27
No LAN still...

lspci -nnk
```

00:00.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:1576]
    Subsystem: Advanced Micro Devices, Inc. [AMD] Device [1022:1576]
00:00.2 IOMMU [0806]: Advanced Micro Devices, Inc. [AMD] Device [1022:1577]
    Subsystem: Advanced Micro Devices, Inc. [AMD] Device [1022:1577]
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Carrizo [1002:9874] (rev c9)
    Subsystem: Lenovo Carrizo [17aa:511e]
    Kernel driver in use: amdgpu
    Kernel modules: amdgpu
00:01.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Kabini HDMI/DP Audio [1002:9840]
    Subsystem: Lenovo Kabini HDMI/DP Audio [17aa:511e]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
00:02.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:157b]
00:02.2 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Device [1022:157c]
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:02.3 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Device [1022:157c]
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:02.4 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Device [1022:157c]
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:03.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:157b]
00:08.0 Encryption controller [1080]: Advanced Micro Devices, Inc. [AMD] Device [1022:1578]
    Subsystem: Advanced Micro Devices, Inc. [AMD] Device [1022:1578]
00:09.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:157d]
00:09.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD] Device [1022:157a]
    Subsystem: Lenovo Device [17aa:511e]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
00:10.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller [1022:7914] (rev 20)
    Subsystem: Lenovo FCH USB XHCI Controller [17aa:511e]
    Kernel driver in use: xhci_hcd
00:11.0 SATA controller [0106]: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] [1022:7901] (rev 49)
    Subsystem: Lenovo FCH SATA Controller [AHCI mode] [17aa:511e]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:12.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller [1022:7908] (rev 49)
    Subsystem: Lenovo FCH USB EHCI Controller [17aa:511e]
    Kernel driver in use: ehci-pci
00:14.0 SMBus [0c05]: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller [1022:790b] (rev 4a)
    Subsystem: Lenovo FCH SMBus Controller [17aa:511e]
    Kernel modules: i2c_piix4, sp5100_tco
00:14.3 ISA bridge [0601]: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge [1022:790e] (rev 11)
    Subsystem: Lenovo FCH LPC Bridge [17aa:511e]
00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:1570]
00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:1571]
00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:1572]
00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:1573]
    Kernel driver in use: k10temp
    Kernel modules: k10temp
00:18.4 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:1574]
    Kernel driver in use: fam15h_power
    Kernel modules: fam15h_power
00:18.5 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:1575]
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0e)
    Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:511e]
    Kernel modules: r8168
01:00.1 Serial controller [0700]: Realtek Semiconductor Co., Ltd. Device [10ec:816a] (rev 0e)
    Subsystem: Lenovo Device [17aa:511e]
01:00.2 Serial controller [0700]: Realtek Semiconductor Co., Ltd. Device [10ec:816b] (rev 0e)
    Subsystem: Lenovo Device [17aa:511e]
01:00.3 IPMI SMIC interface [0c07]: Realtek Semiconductor Co., Ltd. Device [10ec:816c] (rev 0e)
    Subsystem: Lenovo Device [17aa:511e]
    Kernel driver in use: ipmi_si
    Kernel modules: ipmi_si
01:00.4 USB controller [0c03]: Realtek Semiconductor Co., Ltd. Device [10ec:816d] (rev 0e)
    Subsystem: Lenovo Device [17aa:511e]
    Kernel driver in use: ehci-pci
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS522A PCI Express Card Reader [10ec:522a] (rev 01)
    Subsystem: Lenovo RTS522A PCI Express Card Reader [17aa:511e]
    Kernel driver in use: rtsx_pci
    Kernel modules: rtsx_pci
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:b822]
    Subsystem: Lenovo Device [17aa:b023]

```

usb-devices
```
T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=04.13
S:  Manufacturer=Linux 4.13.0-31-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:12.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0438 ProdID=7900 Rev=00.18
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=01 Lev=02 Prnt=02 Port=01 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1199 ProdID=9079 Rev=00.06
S:  Manufacturer=Sierra Wireless, Incorporated
S:  Product=Sierra Wireless EM7455 Qualcomm Snapdragon X7 LTE-A
S:  SerialNumber=LF73410285041020
C:  #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=02(commc) Sub=0e Prot=00 Driver=cdc_mbim
I:  If#= 0 Alt= 1 #EPs= 2 Cls=0a(data ) Sub=00 Prot=02 Driver=cdc_mbim


T:  Bus=01 Lev=02 Prnt=02 Port=02 Cnt=02 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=04f2 ProdID=b5ab Rev=00.10
S:  Manufacturer=SunplusIT Inc
S:  Product=Integrated Camera
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo


T:  Bus=01 Lev=02 Prnt=02 Port=03 Cnt=03 Dev#=  5 Spd=480 MxCh= 3
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=02 MxPS=64 #Cfgs=  1
P:  Vendor=05e3 ProdID=0610 Rev=60.52
S:  Product=USB2.0 Hub
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 1 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=02 Driver=hub


T:  Bus=01 Lev=03 Prnt=05 Port=00 Cnt=01 Dev#=  6 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=ff(vend.) Sub=10 Prot=ff MxPS= 8 #Cfgs=  1
P:  Vendor=138a ProdID=0097 Rev=01.64
S:  SerialNumber=cfab841954ca
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 5 Cls=ff(vend.) Sub=00 Prot=00 Driver=(none)


T:  Bus=01 Lev=03 Prnt=05 Port=02 Cnt=02 Dev#=  8 Spd=12  MxCh= 0
D:  Ver= 2.01 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=058f ProdID=9540 Rev=01.20
S:  Manufacturer=Generic
S:  Product=EMV Smartcard Reader
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=50mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=0b(scard) Sub=00 Prot=00 Driver=(none)


T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 1
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=04.13
S:  Manufacturer=Linux 4.13.0-31-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:01:00.4
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=04.13
S:  Manufacturer=Linux 4.13.0-31-generic xhci-hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:10.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=03 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0e8f ProdID=00fb Rev=00.01
S:  Manufacturer=YSTEK
S:  Product=USB Mouse
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid


T:  Bus=03 Lev=01 Prnt=01 Port=03 Cnt=02 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0781 ProdID=5567 Rev=01.00
S:  Manufacturer=SanDisk
S:  Product=Cruzer Blade
S:  SerialNumber=4C531001501027118423
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=224mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage


T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 4
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev=04.13
S:  Manufacturer=Linux 4.13.0-31-generic xhci-hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:10.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

```

lsmod
```

Module                  Size  Used by
uas                    24576  0
usb_storage            69632  2 uas
bnep                   20480  2
uvcvideo               90112  0
btusb                  45056  0
btrtl                  16384  1 btusb
videobuf2_vmalloc      16384  1 uvcvideo
btbcm                  16384  1 btusb
videobuf2_memops       16384  1 videobuf2_vmalloc
cdc_mbim               16384  0
btintel                16384  1 btusb
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
qcserial               20480  0
bluetooth             544768  11 btrtl,btintel,bnep,btbcm,btusb
cdc_wdm                20480  2 cdc_mbim
videodev              172032  3 uvcvideo,videobuf2_core,videobuf2_v4l2
usb_wwan               20480  1 qcserial
cdc_ncm                36864  1 cdc_mbim
media                  40960  2 uvcvideo,videodev
usbnet                 45056  2 cdc_mbim,cdc_ncm
ecdh_generic           24576  1 bluetooth
usbserial              45056  2 qcserial,usb_wwan
mii                    16384  1 usbnet
msr                    16384  0
nls_iso8859_1          16384  2
edac_mce_amd           28672  0
kvm                   585728  0
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
pcbc                   16384  0
aesni_intel           188416  0
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
snd_hda_codec_realtek    94208  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
input_leds             16384  0
joydev                 20480  0
snd_hda_codec_hdmi     49152  1
serio_raw              16384  0
snd_hda_intel          40960  5
wmi_bmof               16384  0
thinkpad_acpi          94208  1
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_seq_midi           16384  0
fam15h_power           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
nvram                  16384  1 thinkpad_acpi
k10temp                16384  0
snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_rawmidi            32768  1 snd_seq_midi
snd_hwdep              20480  1 snd_hda_codec
i2c_piix4              24576  0
snd_pcm                98304  4 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi
rtsx_pci_ms            20480  0
ipmi_si                57344  0
ipmi_devintf           20480  0
memstick               16384  1 rtsx_pci_ms
ipmi_msghandler        45056  2 ipmi_devintf,ipmi_si
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_seq,snd_pcm
snd                    81920  22 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,thinkpad_acpi,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_pcm
shpchp                 36864  0
ucsi_acpi              16384  0
typec_ucsi             28672  1 ucsi_acpi
typec                  24576  1 typec_ucsi
soundcore              16384  1 snd
i2c_scmi               16384  0
8250_dw                16384  0
tpm_crb                16384  0
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  2 hid_generic,usbhid
amdkfd                188416  1
amd_iommu_v2           20480  1 amdkfd
amdgpu               2019328  49
i2c_algo_bit           16384  1 amdgpu
ttm                    94208  1 amdgpu
rtsx_pci_sdmmc         24576  0
drm_kms_helper        167936  1 amdgpu
ahci                   36864  3
psmouse               143360  0
libahci                32768  1 ahci
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   356352  6 amdgpu,ttm,drm_kms_helper
rtsx_pci               57344  2 rtsx_pci_sdmmc,rtsx_pci_ms
wmi                    24576  1 wmi_bmof
video                  40960  1 thinkpad_acpi

```

iwconfig
```

lo        no wireless extensions.


wwp0s18u1u2i12  no wireless extensions.

```

I think that second interface is my fault, shouldn't be there, I added it by mistake.

```

lo        Interface doesn't support scanning.


wwp0s18u1u2i12  Interface doesn't support scanning.

```

---

### Post by praseodym on 2018-01-27
No wireless card shown, except USB-WWAN. Driver for LAN is not loaded, so deactivate SecureBoot in your (U)EFI and reboot

---

### Post by whomaniac on 2018-01-27
secure boot is already disabled...
I double checked now.

I disabled it for TLP.

Perhaps I need to reinstall the driver again?
I remind you that I may have messed things up seriously when I tried to fix the problem myself...

---

### Post by whomaniac on 2018-01-27
when I do:

[COLOR=#000000]lspci | grep -i net:[/COLOR]
[COLOR=#000000]Code:
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0e)[/COLOR]
ain't this the network card?? I am a confused...

---

### Post by linuchsan on 2018-01-27
I added eth0 myself.... oeps...are you sure it is eth0?!
What does: **ip link show** say?

---

### Post by praseodym on 2018-01-27
Its the LAN card. Run
```

sudo modprobe -v r8168
```

```
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:b822]
```
This is wireless. Run
```

sudo modprobe -v rtl8822be
```

---

### Post by whomaniac on 2018-01-28
> **linuchsan said:**
> I added eth0 myself.... oeps...are you sure it is eth0?!
What does: **ip link show** say?

Not sure at all
I messed up the whole config

```

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: wwp0s18u1u2i12: <BROADCAST,MULTICAST,NOARP> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000
    link/ether 36:96:57:9f:69:da brd ff:ff:ff:ff:ff:ff

```

---

### Post by whomaniac on 2018-01-28
> **praseodym said:**
> Its the LAN card. Run
```

sudo modprobe -v r8168
```

```
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:b822]
```
This is wireless. Run
```

sudo modprobe -v rtl8822be
```

[CODE]
modprobe: FATAL: Module rtl882be not found in directory /lib/modules/4.13.0-31-generic
[\CODE]

[CODE]
modprobe: FATAL: Module r8168 not found in directory /lib/modules/4.13.0-31-generic
[\CODE]

---

### Post by praseodym on 2018-01-28
Lets check
```

dpkg -l linux-image-* | grep ii
dpkg -l linux-headers-* | grep ii
locate r8168.ko | grep lib
locate rtl8822be.ko | grep lib
```

---

### Post by whomaniac on 2018-01-28
linux image:
```

ii  linux-image-4.10.0-28-generic       4.10.0-28.32~16.04.2 amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-4.10.0-42-generic       4.10.0-42.46~16.04.1 amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-4.13.0-26-generic       4.13.0-26.29~16.04.2 amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
ii  linux-image-4.13.0-31-generic       4.13.0-31.34~16.04.1 amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
ii  linux-image-extra-4.10.0-28-generic 4.10.0-28.32~16.04.2 amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-extra-4.10.0-42-generic 4.10.0-42.46~16.04.1 amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
ii  linux-image-extra-4.13.0-26-generic 4.13.0-26.29~16.04.2 amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
ii  linux-image-extra-4.13.0-31-generic 4.13.0-31.34~16.04.1 amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
ii  linux-image-generic-hwe-16.04       4.13.0.31.51         amd64        Generic Linux kernel image

```

linux headers:
```

ii  linux-headers-4.10.0-28         4.10.0-28.32~16.04.2 all          Header files related to Linux kernel version 4.10.0
ii  linux-headers-4.10.0-28-generic 4.10.0-28.32~16.04.2 amd64        Linux kernel headers for version 4.10.0 on 64 bit x86 SMP
ii  linux-headers-4.10.0-42         4.10.0-42.46~16.04.1 all          Header files related to Linux kernel version 4.10.0
ii  linux-headers-4.10.0-42-generic 4.10.0-42.46~16.04.1 amd64        Linux kernel headers for version 4.10.0 on 64 bit x86 SMP
ii  linux-headers-4.13.0-26         4.13.0-26.29~16.04.2 all          Header files related to Linux kernel version 4.13.0
ii  linux-headers-4.13.0-26-generic 4.13.0-26.29~16.04.2 amd64        Linux kernel headers for version 4.13.0 on 64 bit x86 SMP
ii  linux-headers-4.13.0-31         4.13.0-31.34~16.04.1 all          Header files related to Linux kernel version 4.13.0
ii  linux-headers-4.13.0-31-generic 4.13.0-31.34~16.04.1 amd64        Linux kernel headers for version 4.13.0 on 64 bit x86 SMP
ii  linux-headers-generic-hwe-16.04 4.13.0.31.51         amd64        Generic Linux kernel headers

```


The 2 other commands didn't output anything... even without the pipe to grep... nothing :cry:

---

### Post by jeremy31 on 2018-01-28
What about results for ```
dkms status
```

---

### Post by praseodym on 2018-01-28
Ok, download these files (somehow) and save them in "Downloads":

[http://de.archive.ubuntu.com/ubuntu/pool/universe/r/r8168/r8168-dkms_8.045.08-1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/universe/r/r8168/r8168-dkms_8.045.08-1_all.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-2ubuntu11.5_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-2ubuntu11.5_all.deb)

Installation

```
sudo dpkg -i ~/Downloads/*.deb
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
Reboot. If LAN works, install the wireless driver via

```
sudo apt-get install git build-essential dkms linux-headers-$(uname -r)
git clone -b extended https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
sudo cp /usr/src/rtlwifi-new-0.6/firmware/rtlwifi/* /lib/firmware/rtlwifi/ 
```
Reboot with SecureBoot deaktivated

---

### Post by linuchsan on 2018-01-28
Try Ukuu to upgrade your kernel. This could solve your problem.

---

### Post by whomaniac on 2018-02-01
Thank you so much!!!

It is alive! alive!!!!

---

