---
title: "Can't figure out installation of USB dongle"
date: 2020-09-14
forum: Networking &amp; Wireless
---

### Post by dshah on 2020-09-14
I recently purchased a USB dongle which has WiFi and Bluetooth capabilities. I followed instructions here to install drivers

```
git clone https://github.com/lwfinger/rtl8723bu.git
cd rtl8723bu
source dkms.conf
sudo mkdir /usr/src/$PACKAGE_NAME-$PACKAGE_VERSION
sudo cp -r core hal include os_dep platform dkms.conf Makefile rtl8723b_fw.bin /usr/src/$PACKAGE_NAME-$PACKAGE_VERSION
sudo dkms add $PACKAGE_NAME/$PACKAGE_VERSION
sudo dkms autoinstall $PACKAGE_NAME/$PACKAGE_VERSION

```

when I attach dongle on USB, here is the output of dmesg
```

$ dmesg
[11162.342536] usb 1-12: new high-speed USB device number 7 using xhci_hcd
[11162.511281] usb 1-12: New USB device found, idVendor=0bda, idProduct=b720
[11162.511285] usb 1-12: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[11162.511288] usb 1-12: Product: 802.11n WLAN Adapter
[11162.511291] usb 1-12: Manufacturer: Realtek
[11162.511293] usb 1-12: SerialNumber: 00e04c000001
[11162.513540] usb 1-12: This Realtek USB WiFi dongle (0x0bda:0xb720) is untested!
[11162.513542] usb 1-12: Please report results to Jes.Sorensen@gmail.com
[11162.589834] usb 1-12: Vendor: Realtek
[11162.589838] usb 1-12: Product: 802.11n WLAN Adapter
[11162.589841] usb 1-12: rtl8723bu_parse_efuse: dumping efuse (0x200 bytes):
[11162.589843] usb 1-12: 00: 29 81 03 7c 01 08 21 00
[11162.589845] usb 1-12: 08: 50 07 05 35 10 00 00 00
[11162.589848] usb 1-12: 10: 31 31 31 31 31 31 31 31
[11162.589849] usb 1-12: 18: 31 31 30 02 ff ff ff ff
[11162.589851] usb 1-12: 20: ff ff ff ff ff ff ff ff
[11162.589853] usb 1-12: 28: ff ff ff ff ff ff ff ff
[11162.589855] usb 1-12: 30: ff ff ff ff ff ff ff ff
[11162.589857] usb 1-12: 38: ff ff 31 31 31 31 31 31
[11162.589858] usb 1-12: 40: 30 30 30 30 30 f3 ff ff
[11162.589860] usb 1-12: 48: ff ff ff ff ff ff ff ff
[11162.589862] usb 1-12: 50: ff ff ff ff ff ff ff ff
[11162.589864] usb 1-12: 58: ff ff ff ff ff ff ff ff
[11162.589866] usb 1-12: 60: ff ff ff ff ff ff ff ff
[11162.589868] usb 1-12: 68: ff ff ff ff ff ff ff ff
[11162.589869] usb 1-12: 70: ff ff ff ff ff ff ff ff
[11162.589871] usb 1-12: 78: ff ff ff ff ff ff ff ff
[11162.589873] usb 1-12: 80: ff ff ff ff ff ff ff ff
[11162.589875] usb 1-12: 88: ff ff ff ff ff ff ff ff
[11162.589877] usb 1-12: 90: ff ff ff ff ff ff ff ff
[11162.589878] usb 1-12: 98: ff ff ff ff ff ff ff ff
[11162.589880] usb 1-12: a0: ff ff ff ff ff ff ff ff
[11162.589882] usb 1-12: a8: ff ff ff ff ff ff ff ff
[11162.589884] usb 1-12: b0: ff ff ff ff ff ff ff ff
[11162.589886] usb 1-12: b8: 20 20 24 00 00 00 ff ff
[11162.589887] usb 1-12: c0: ff 28 20 11 00 00 00 ff
[11162.589889] usb 1-12: c8: 00 ff ff ff ff ff ff ff
[11162.589891] usb 1-12: d0: ff ff ff ff ff ff ff ff
[11162.589893] usb 1-12: d8: ff ff ff ff ff ff ff ff
[11162.589895] usb 1-12: e0: ff ff ff ff ff ff ff ff
[11162.589896] usb 1-12: e8: ff ff ff ff ff ff ff ff
[11162.589898] usb 1-12: f0: ff ff ff ff ff ff ff ff
[11162.589900] usb 1-12: f8: ff ff ff ff ff ff ff ff
[11162.589902] usb 1-12: 100: da 0b 20 b7 e7 47 03 00
[11162.589904] usb 1-12: 108: 13 ef 4f a2 b4 09 03 52
[11162.589906] usb 1-12: 110: 65 61 6c 74 65 6b 16 03
[11162.589908] usb 1-12: 118: 38 30 32 2e 31 31 6e 20
[11162.589910] usb 1-12: 120: 57 4c 41 4e 20 41 64 61
[11162.589911] usb 1-12: 128: 70 74 65 72 00 ff ff ff
[11162.589913] usb 1-12: 130: ff ff ff ff ff ff ff ff
[11162.589915] usb 1-12: 138: ff ff ff ff ff ff ff ff
[11162.589917] usb 1-12: 140: ff ff ff ff ff ff ff 0f
[11162.589919] usb 1-12: 148: ff ff ff ff ff ff ff ff
[11162.589921] usb 1-12: 150: ff ff ff ff ff ff ff ff
[11162.589922] usb 1-12: 158: ff ff ff ff ff ff ff ff
[11162.589924] usb 1-12: 160: ff ff ff ff ff ff ff ff
[11162.589926] usb 1-12: 168: ff ff ff ff ff ff ff ff
[11162.589928] usb 1-12: 170: ff ff ff ff ff ff ff ff
[11162.589930] usb 1-12: 178: ff ff ff ff ff ff ff ff
[11162.589931] usb 1-12: 180: ff ff ff ff ff ff ff ff
[11162.589933] usb 1-12: 188: ff ff ff ff ff ff ff ff
[11162.589935] usb 1-12: 190: ff ff ff ff ff ff ff ff
[11162.589937] usb 1-12: 198: ff ff ff ff ff ff ff ff
[11162.589939] usb 1-12: 1a0: ff ff ff ff ff ff ff ff
[11162.589941] usb 1-12: 1a8: ff ff ff ff ff ff ff ff
[11162.589942] usb 1-12: 1b0: ff ff ff ff ff ff ff ff
[11162.589944] usb 1-12: 1b8: ff ff ff ff ff ff ff ff
[11162.589946] usb 1-12: 1c0: ff ff ff ff ff ff ff ff
[11162.589948] usb 1-12: 1c8: ff ff ff ff ff ff ff ff
[11162.589950] usb 1-12: 1d0: ff ff ff ff ff ff ff ff
[11162.589952] usb 1-12: 1d8: ff ff ff ff ff ff ff ff
[11162.589953] usb 1-12: 1e0: ff ff ff ff ff ff ff ff
[11162.589955] usb 1-12: 1e8: ff ff ff ff ff ff ff ff
[11162.589957] usb 1-12: 1f0: ff ff ff ff ff ff ff ff
[11162.589959] usb 1-12: 1f8: ff ff ff ff ff ff ff ff
[11162.589963] usb 1-12: RTL8723BU rev E (SMIC) 1T1R, TX queues 3, WiFi=1, BT=1, GPS=0, HI PA=0
[11162.589966] usb 1-12: RTL8723BU MAC: 00:13:ef:4f:a2:b4
[11162.589968] usb 1-12: rtl8xxxu: Loading firmware rtlwifi/rtl8723bu_nic.bin
[11162.590024] usb 1-12: Firmware revision 35.0 (signature 0x5301)
[11163.360800] rtl8xxxu 1-12:1.2 wlx0013ef4fa2b4: renamed from wlan0
```

**lsusb**```
$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 2a7a:0c18  
Bus 001 Device 005: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 007: ID 0bda:b720 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

**lsmod**
```

$ lsmod
Module                  Size  Used by
nls_utf8               16384  0
udf                    90112  0
crc_itu_t              16384  1 udf
nls_iso8859_1          16384  0
bnep                   20480  2
vmw_vsock_vmci_transport    28672  0
vsock                  36864  1 vmw_vsock_vmci_transport
vmw_vmci               69632  1 vmw_vsock_vmci_transport
pci_stub               16384  1
vboxpci                24576  0
vboxnetadp             28672  0
vboxnetflt             28672  0
vboxdrv               454656  3 vboxnetadp,vboxnetflt,vboxpci
nbd                    20480  0
8723bu                888832  0
arc4                   16384  2
rtl8xxxu              126976  0
mac80211              765952  1 rtl8xxxu
cfg80211              589824  2 8723bu,mac80211
intel_rapl             20480  0
input_leds             16384  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             192512  0
kvm                   598016  1 kvm_intel
irqbypass              16384  1 kvm
intel_cstate           16384  0
intel_rapl_perf        16384  0
ie31200_edac           16384  0
edac_core              53248  1 ie31200_edac
hci_uart               94208  0
intel_th_gth           16384  0
intel_th_pci           16384  0
mei_me                 36864  0
btbcm                  16384  1 hci_uart
intel_th               16384  2 intel_th_pci,intel_th_gth
mei                   102400  1 mei_me
btqca                  16384  1 hci_uart
btintel                16384  1 hci_uart
bluetooth             557056  11 hci_uart,btintel,btqca,bnep,btbcm
acpi_als               16384  0
kfifo_buf              16384  1 acpi_als
intel_lpss_acpi        16384  0
intel_lpss             16384  1 intel_lpss_acpi
industrialio           65536  2 acpi_als,kfifo_buf
mac_hid                16384  0
acpi_pad               20480  0
binfmt_misc            20480  1
ib_iser                49152  0
rdma_cm                57344  1 ib_iser
iw_cm                  49152  1 rdma_cm
ib_cm                  45056  1 rdma_cm
ib_core               212992  4 ib_iser,ib_cm,rdma_cm,iw_cm
configfs               40960  2 rdma_cm
iscsi_tcp              20480  0
libiscsi_tcp           24576  1 iscsi_tcp
libiscsi               53248  3 ib_iser,libiscsi_tcp,iscsi_tcp
scsi_transport_iscsi   102400  4 ib_iser,libiscsi,iscsi_tcp
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
autofs4                40960  2
btrfs                1048576  0
raid10                 49152  0
raid456               106496  0
async_raid6_recov      20480  1 raid456
async_memcpy           16384  2 raid456,async_raid6_recov
async_pq               16384  2 raid456,async_raid6_recov
async_xor              16384  3 async_pq,raid456,async_raid6_recov
async_tx               16384  5 async_xor,async_pq,raid456,async_memcpy,async_raid6_recov
xor                    24576  2 async_xor,btrfs
raid6_pq              102400  4 async_pq,btrfs,raid456,async_raid6_recov
libcrc32c              16384  1 raid456
raid0                  20480  0
multipath              16384  0
linear                 16384  0
raid1                  36864  1
i915                 1314816  5
uas                    24576  0
crct10dif_pclmul       16384  0
hid_generic            16384  0
i2c_algo_bit           16384  1 i915
crc32_pclmul           16384  0
drm_kms_helper        167936  1 i915
ghash_clmulni_intel    16384  0
ahci                   36864  4
aesni_intel           167936  0
e1000e                249856  0
syscopyarea            16384  1 drm_kms_helper
aes_x86_64             20480  1 aesni_intel
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
lrw                    16384  1 aesni_intel
ptp                    20480  1 e1000e
glue_helper            16384  1 aesni_intel
pps_core               20480  1 ptp
usbhid                 53248  0
ablk_helper            16384  1 aesni_intel
usb_storage            73728  1 uas
libahci                32768  1 ahci
cryptd                 24576  3 ablk_helper,ghash_clmulni_intel,aesni_intel
i2c_hid                20480  0
wmi                    16384  0
drm                   364544  7 i915,drm_kms_helper
pinctrl_sunrisepoint    28672  0
hid                   118784  3 i2c_hid,hid_generic,usbhid
video                  40960  1 i915
pinctrl_intel          20480  1 pinctrl_sunrisepoint
fjes                   28672  0
```

I dont see any network icon, no Bluetooth either?

Could someone please help?

---

### Post by CelticWarrior on 2020-09-14
Disable Secure Boot in UEFI. Reboot. Any change?

---

### Post by dshah on 2020-09-14
@CelticWarrior  Thanks for replying, before I do Secure boot in UEFI, I was able to make WiFi work, here are the steps I taken


USB dongle was not reading the right driver, which I found with command $ usb-devices

T:  Bus=01 Lev=01 Prnt=01 Port=11 Cnt=02 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.10 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0bda ProdID=b720 Rev=02.00
S:  Manufacturer=Realtek
S:  Product=802.11n WLAN Adapter
S:  SerialNumber=00e04c000001
C:  #Ifs= 3 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=(none)
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=(none)
I:  If#= 2 Alt= 0 #EPs= 6 Cls=ff(vend.) Sub=ff Prot=ff Driver=[B][COLOR=#000000][FONT=&amp]rtl8xxxu
[/FONT][/COLOR][/B]
then to solve it I uninstalled and re-install after running this command ran this:
```

$ modprobe -r rtl8xxxu

```

and this driver can not work with the standard driver rtl8xxxu, thus I need to blacklist it. Run the following command ... sudo nano /etc/modprobe.d/50-rtl8xxxu.conf ... Add a single line: blacklist rtl8xxxu .
than in my setup I had this
```

...
$sudo modprobe -v 8723bu
...

```

rebooted and checked usb-devices is showing correct Driver.
Now I am able to connect with WiFi, But, in Bluetooth manager I am not seeing any adapter. 
```
$ dmesg | egrep -i 'blue|firm'
[    0.308483] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    1.167666] GHES: APEI firmware first mode is enabled by APEI bit.
[    7.298102] [drm] GuC firmware load skipped
[   13.802353] Bluetooth: Core ver 2.21
[   13.802359] Bluetooth: HCI device and connection manager initialized
[   13.802361] Bluetooth: HCI socket layer initialized
[   13.802364] Bluetooth: L2CAP socket layer initialized
[   13.802367] Bluetooth: SCO socket layer initialized
[   14.019436] Bluetooth: HCI UART driver ver 2.3
[   14.019437] Bluetooth: HCI UART protocol H4 registered
[   14.019438] Bluetooth: HCI UART protocol BCSP registered
[   14.019438] Bluetooth: HCI UART protocol LL registered
[   14.019438] Bluetooth: HCI UART protocol ATH3K registered
[   14.019439] Bluetooth: HCI UART protocol Three-wire (H5) registered
[   14.019469] Bluetooth: HCI UART protocol Intel registered
[   14.019475] Bluetooth: HCI UART protocol BCM registered
[   14.019476] Bluetooth: HCI UART protocol QCA registered
[   14.019476] Bluetooth: HCI UART protocol AG6XX registered
[  105.193832] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  105.193834] Bluetooth: BNEP filters: protocol multicast
[  105.193840] Bluetooth: BNEP socket layer initialized



```


any advice for this?

---

### Post by dshah on 2020-09-14
ps here is the output
```

$ mokutil --sb-state
EFI variables are not supported on this system

```

---

### Post by morrownr on 2020-09-14
dshah, I am not familiar with this specific device but I have seen reports on some combo devices where the BT won't run on Linux. I have usb wifi adapters and usb BT adapters that run well on Linux but I do have any combo devices.

I wish we had a sticky threat at the top where we maintain a select list of usb wifi and BT adapters that work well on Linux/Ubuntu. I'd even volunteer to help manage it.

---

### Post by dshah on 2020-09-15
@morrownr thanks for replying, seems there is no solution for this. so I am looking for another bluetooth adapter

you think this will work?  [https://www.skroutz.gr/s/19355624/TP-LINK-UB400-v1.html](https://www.skroutz.gr/s/19355624/TP-LINK-UB400-v1.html)
or any from this list? [https://www.skroutz.gr/c/228/bluetooth-adapters.html?o=bluetooth+adapter](https://www.skroutz.gr/c/228/bluetooth-adapters.html?o=bluetooth+adapter)

---

### Post by morrownr on 2020-09-15
Here are some links:

[Option 1]("https://smile.amazon.com/Panda-Bluetooth-4-0-Nano-Adapter/dp/B00BCU4TZE/ref=sr_1_9?dchild=1&keywords=usb+bluetooth+adapter+for+linux&qid=1600197606&sr=8-9")
[Option 2]("https://smile.amazon.com/Plugable-Bluetooth-Adapter-Compatible-Raspberry/dp/B009ZIILLI/ref=sr_1_3?dchild=1&keywords=usb+bluetooth+adapter+for+linux&qid=1600197606&sr=8-3")

There are other options. Amazon can be a good resource even if you don't buy from Amazon.

---

### Post by dshah on 2020-09-19
Thanks morrownr, I just updated ubuntu from 16 to 20 , and my dongle started to work without installing any extra packages

---

### Post by morrownr on 2020-09-19
I am happy to hear that. You can mark the thread solved.

---

