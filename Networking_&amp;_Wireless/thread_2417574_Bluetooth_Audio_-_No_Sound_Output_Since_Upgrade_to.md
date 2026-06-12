---
title: "Bluetooth Audio - No Sound Output Since Upgrade to 19.04"
date: 2019-04-24
forum: Networking &amp; Wireless
---

### Post by gwinston99 on 2019-04-24
Here is some info:

gregg@Gregg-HP-Laptop:~$ service bluetooth status
&#9679; bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
   Active: active (running) since Tue 2019-04-23 17:14:37 EDT; 18h ago
     Docs: man:bluetoothd(8)
 Main PID: 1042 (bluetoothd)
   Status: "Running"
    Tasks: 1 (limit: 4915)
   Memory: 2.2M
   CGroup: /system.slice/bluetooth.service
           &#9492;&#9472;1042 /usr/lib/bluetooth/bluetoothd

Apr 23 17:14:37 Gregg-HP-Laptop systemd[1]: Starting Bluetooth service...
Apr 23 17:14:37 Gregg-HP-Laptop bluetoothd[1042]: Bluetooth daemon 5.50
Apr 23 17:14:37 Gregg-HP-Laptop bluetoothd[1042]: Starting SDP server
Apr 23 17:14:37 Gregg-HP-Laptop systemd[1]: Started Bluetooth service.
Apr 23 17:14:37 Gregg-HP-Laptop bluetoothd[1042]: Bluetooth management interface 1.14 initialized
Apr 23 17:15:04 Gregg-HP-Laptop bluetoothd[1042]: Endpoint registered: sender=:1.355 path=/MediaEndpoint/A2DPSource
Apr 23 17:15:04 Gregg-HP-Laptop bluetoothd[1042]: Endpoint registered: sender=:1.355 path=/MediaEndpoint/A2DPSink


gregg@Gregg-HP-Laptop:~$ lspci -nnk
00:00.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Root Complex [1022:1576]
	Subsystem: Hewlett-Packard Company Family 15h (Models 60h-6fh) Processor Root Complex [103c:8332]
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Wani [Radeon R5/R6/R7 Graphics] [1002:9874] (rev c8)
	Subsystem: Hewlett-Packard Company Wani [Radeon R5/R6/R7 Graphics] [103c:8332]
	Kernel driver in use: amdgpu
	Kernel modules: amdgpu
00:01.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Kabini HDMI/DP Audio [1002:9840]
	Subsystem: Hewlett-Packard Company Kabini HDMI/DP Audio [103c:8332]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel
00:02.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Host Bridge [1022:157b]
00:02.2 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Root Port [1022:157c]
	Kernel driver in use: pcieport
00:02.4 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Root Port [1022:157c]
	Kernel driver in use: pcieport
00:03.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Host Bridge [1022:157b]
00:03.1 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Root Port [1022:157c]
	Kernel driver in use: pcieport
00:08.0 Encryption controller [1080]: Advanced Micro Devices, Inc. [AMD] Device [1022:1578]
	Subsystem: Hewlett-Packard Company Device [103c:8332]
00:09.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:157d]
00:09.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Audio Controller [1022:157a]
	Subsystem: Hewlett-Packard Company Family 15h (Models 60h-6fh) Audio Controller [103c:8332]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel
00:10.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller [1022:7914] (rev 20)
	Subsystem: Hewlett-Packard Company FCH USB XHCI Controller [103c:8332]
	Kernel driver in use: xhci_hcd
00:11.0 SATA controller [0106]: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] [1022:7904] (rev 49)
	Subsystem: Hewlett-Packard Company FCH SATA Controller [AHCI mode] [103c:8332]
	Kernel driver in use: ahci
	Kernel modules: ahci
00:12.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller [1022:7908] (rev 49)
	Subsystem: Hewlett-Packard Company FCH USB EHCI Controller [103c:8332]
	Kernel driver in use: ehci-pci
00:14.0 SMBus [0c05]: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller [1022:790b] (rev 4a)
	Subsystem: Hewlett-Packard Company FCH SMBus Controller [103c:8332]
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c_piix4, sp5100_tco
00:14.3 ISA bridge [0601]: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge [1022:790e] (rev 11)
	Subsystem: Hewlett-Packard Company FCH LPC Bridge [103c:8332]
00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Function 0 [1022:1570]
00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Function 1 [1022:1571]
00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Function 2 [1022:1572]
00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Function 3 [1022:1573]
	Kernel driver in use: k10temp
	Kernel modules: k10temp
00:18.4 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Function 4 [1022:1574]
	Kernel driver in use: fam15h_power
	Kernel modules: fam15h_power
00:18.5 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Function 5 [1022:1575]
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
	Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:8332]
	Kernel driver in use: r8168
	Kernel modules: r8168
02:00.0 Network controller [0280]: Intel Corporation Dual Band Wireless-AC 3168NGW [Stone Peak] [8086:24fb] (rev 10)
	Subsystem: Intel Corporation Dual Band Wireless-AC 3168NGW [Stone Peak] [8086:2110]
	Kernel driver in use: iwlwifi
	Kernel modules: iwlwifi

gregg@Gregg-HP-Laptop:~$ lsusb
Bus 001 Device 004: ID 8087:0aa7 Intel Corp. 
Bus 001 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 1058:25ee Western Digital Technologies, Inc. 
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 002 Device 002: ID 0bda:58ed Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


gregg@Gregg-HP-Laptop:~$ usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=05.00
S:  Manufacturer=Linux 5.0.0-13-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:12.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#=0x0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0438 ProdID=7900 Rev=00.18
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#=0x0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=02 Prnt=02 Port=00 Cnt=01 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=c52b Rev=12.07
S:  Manufacturer=Logitech
S:  Product=USB Receiver
C:  #Ifs= 3 Cfg#= 1 Atr=a0 MxPwr=98mA
I:  If#=0x0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid
I:  If#=0x1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
I:  If#=0x2 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid

T:  Bus=01 Lev=02 Prnt=02 Port=03 Cnt=02 Dev#=  4 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0aa7 Rev=00.01
C:  #Ifs= 2 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#=0x0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#=0x1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=05.00
S:  Manufacturer=Linux 5.0.0-13-generic xhci-hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:10.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#=0x0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0bda ProdID=58ed Rev=00.13
S:  Manufacturer=DGENE019IAFFBF
S:  Product=HP Webcam
S:  SerialNumber=200901010001
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#=0x0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#=0x1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

T:  Bus=02 Lev=01 Prnt=01 Port=03 Cnt=02 Dev#=  3 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=c408 Rev=14.00
S:  Manufacturer=Logitech
S:  Product=USB Trackball
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=50mA
I:  If#=0x0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 4
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev=05.00
S:  Manufacturer=Linux 5.0.0-13-generic xhci-hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:10.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#=0x0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#=  2 Spd=5000 MxCh= 0
D:  Ver= 3.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 9 #Cfgs=  1
P:  Vendor=1058 ProdID=25ee Rev=40.04
S:  Manufacturer=Western Digital
S:  Product=My Book 25EE
S:  SerialNumber=574343374B3645484A345348
C:  #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=8mA
I:  If#=0x0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage


gregg@Gregg-HP-Laptop:~$ hciconfig --all
hci0:	Type: Primary  Bus: USB
	BD Address: 34:41:5D:06:55:C6  ACL MTU: 1021:4  SCO MTU: 96:6
	UP RUNNING PSCAN 
	RX bytes:2024 acl:0 sco:0 events:263 errors:0
	TX bytes:50764 acl:0 sco:0 commands:263 errors:0
	Features: 0xbf 0xfe 0x0f 0xfe 0xdb 0xff 0x7b 0x87
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: RSWITCH SNIFF 
	Link mode: SLAVE ACCEPT 
	Name: 'Gregg-HP-Laptop'
	Class: 0x0c010c
	Service Classes: Rendering, Capturing
	Device Class: Computer, Laptop
	HCI Version: 4.2 (0x8)  Revision: 0x1100
	LMP Version: 4.2 (0x8)  Subversion: 0x1100
	Manufacturer: Intel Corp. (2)

gregg@Gregg-HP-Laptop:~$ lsmod
Module                  Size  Used by
rfcomm                 77824  4
cmac                   16384  1
bnep                   24576  2
nls_iso8859_1          16384  1
edac_mce_amd           28672  0
ccp                    86016  0
kvm                   626688  0
irqbypass              16384  1 kvm
snd_hda_codec_realtek   114688  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
ledtrig_audio          16384  2 snd_hda_codec_generic,snd_hda_codec_realtek
crct10dif_pclmul       16384  1
snd_hda_codec_hdmi     53248  1
crc32_pclmul           16384  0
snd_hda_intel          40960  4
snd_hda_codec         131072  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
snd_hda_core           86016  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
ghash_clmulni_intel    16384  0
snd_hwdep              20480  1 snd_hda_codec
uvcvideo               98304  0
snd_pcm               102400  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
arc4                   16384  2
amdgpu               3518464  14
snd_seq_midi           20480  0
videobuf2_vmalloc      20480  1 uvcvideo
videobuf2_memops       20480  1 videobuf2_vmalloc
snd_seq_midi_event     16384  1 snd_seq_midi
videobuf2_v4l2         24576  1 uvcvideo
iwlmvm                380928  0
videobuf2_common       49152  2 videobuf2_v4l2,uvcvideo
mac80211              806912  1 iwlmvm
snd_rawmidi            36864  1 snd_seq_midi
chash                  16384  1 amdgpu
videodev              200704  3 videobuf2_v4l2,uvcvideo,videobuf2_common
amd_iommu_v2           20480  1 amdgpu
media                  53248  4 videodev,videobuf2_v4l2,uvcvideo,videobuf2_common
aesni_intel           372736  2
gpu_sched              32768  1 amdgpu
joydev                 24576  0
btusb                  49152  0
snd_seq                69632  2 snd_seq_midi,snd_seq_midi_event
iwlwifi               311296  1 iwlmvm
aes_x86_64             20480  1 aesni_intel
btrtl                  20480  1 btusb
crypto_simd            16384  1 aesni_intel
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
ttm                   102400  1 amdgpu
btbcm                  16384  1 btusb
glue_helper            16384  1 aesni_intel
input_leds             16384  0
btintel                24576  1 btusb
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
drm_kms_helper        180224  1 amdgpu
snd_timer              36864  2 snd_seq,snd_pcm
hp_wmi                 16384  0
serio_raw              20480  0
bluetooth             557056  31 btrtl,btintel,btbcm,bnep,btusb,rfcomm
sparse_keymap          16384  1 hp_wmi
drm                   475136  8 gpu_sched,drm_kms_helper,amdgpu,ttm
wmi_bmof               16384  0
ecdh_generic           28672  2 bluetooth
i2c_algo_bit           16384  1 amdgpu
cfg80211              671744  3 iwlmvm,iwlwifi,mac80211
fb_sys_fops            16384  1 drm_kms_helper
snd                    81920  19 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
fam15h_power           16384  0
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
k10temp                16384  0
sysimgblt              16384  1 drm_kms_helper
soundcore              16384  1 snd
mac_hid                16384  0
hp_wireless            16384  0
sch_fq_codel           20480  2
parport_pc             40960  0
ppdev                  24576  0
lp                     20480  0
parport                53248  3 parport_pc,lp,ppdev
ip_tables              28672  0
x_tables               40960  1 ip_tables
autofs4                45056  2
raid10                 57344  0
raid456               155648  0
async_raid6_recov      24576  1 raid456
async_memcpy           20480  2 raid456,async_raid6_recov
async_pq               24576  2 raid456,async_raid6_recov
async_xor              20480  3 async_pq,raid456,async_raid6_recov
async_tx               20480  5 async_pq,async_memcpy,async_xor,raid456,async_raid6_recov
xor                    24576  1 async_xor
ses                    20480  0
enclosure              16384  1 ses
scsi_transport_sas     40960  1 ses
raid6_pq              114688  3 async_pq,raid456,async_raid6_recov
libcrc32c              16384  1 raid456
raid1                  45056  0
raid0                  24576  0
multipath              20480  0
linear                 20480  0
hid_logitech_hidpp     45056  0
hid_logitech_dj        20480  0
hid_generic            16384  0
usbhid                 53248  0
hid                   126976  4 usbhid,hid_generic,hid_logitech_dj,hid_logitech_hidpp
uas                    24576  0
usb_storage            69632  2 uas
ahci                   40960  2
psmouse               151552  0
r8168                 540672  0
i2c_piix4              28672  0
libahci                32768  1 ahci
wmi                    28672  2 hp_wmi,wmi_bmof
i2c_scmi               20480  0
video                  45056  0

---

