---
title: "Internet Connection - not getting established."
date: 2015-10-18
forum: Networking &amp; Wireless
---

### Post by eruptionjoojo on 2015-10-18
Hello All,

         I'm having Ubuntu 14.04 - 64 bit on my laptop. I'm tring to access internet via Huawei E3531 Data card/Dongle, while I plug-in the device Ubuntu recognises it and shows the option - 'Enable Mobile Broadband' under network as well the name of my ISP(i.e. BSNL - Cellone; India) is also listed in the list automatically. I check mark the 'Enable Mobile Broadband' connection and then on click the 'Connect - Cellone - BSNL' network option available under networks, but it doesn't get connected. It tries to connect again - and - again but all in vein. 

                                  So, please help me in sorting out this issue for which I shall be highly thankful to you. I have already read a number of threads on this forum but those turned out to be irrelevant as such because in my case Ubuntu does recognise it as well lists the options but unforutnately doesn't get connected.

My Laptop is :-

ASUS X53U SX181D

Thanks & Regards,
Joojo.

---

### Post by praseodym on 2015-10-18
Please check here

[http://ubuntuforums.org/showthread.php?t=1831649&highlight=umts+checklist](http://ubuntuforums.org/showthread.php?t=1831649&highlight=umts+checklist)

Also check if the stick provides a web interface for setting up the connection

---

### Post by eruptionjoojo on 2015-10-19
Thanks a lot for your quick & responsive reply ........... by the way while trying to ascertain the output of the below listed commands, I had connected the Data card but somehow now it doesn't show the Enable Mobile broadband which was available previously. I seem to have messed up with the USB device mounting option as such because this was suggested in one of the thread & I may have had done it wrongly. Anyhow here's the ouput of the commands : -

```

K53U:~$ lsusb

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 001 Device 002: ID 04f2:b23b Chicony Electronics Co., Ltd 

Bus 001 Device 007: ID 12d1:1446 Huawei Technologies Co., Ltd. E1552/E1800/E173 (HSPA modem)

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 004 Device 002: ID 04ca:3002 Lite-On Technology Corp. 

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

K53U:~$ lsmod

Module                              Size                  Used 
by
nls_iso8859_1                     12713                   0 

nls_utf8                            12557                   1 

isofs                               39837                   1 

pci_stub                            12622                   1

vboxpci                             23194                   0 

vboxnetadp                          25670                   0 

vboxnetflt                          27613                   0 

vboxdrv                             339502                  3 vboxnetadp,vboxnetflt,vboxpci

asus_nb_wmi                         16990                   0 

asus_wmi                            24191                   1 
asus_nb_wmi
sparse_keymap            13948                   1 
asus_wmi
snd_hda_codec_realtek       65626                   1 

snd_hda_codec_hdmi                  46368                   1 

rfcomm                              69160                   0 

bnep                                19624                   2  

uvcvideo                            80885                   0 

videobuf2_vmalloc                   13216                   1 
uvcvideo
videobuf2_memops            13362                   1 
videobuf2_vmalloc
kvm_amd            60026                   0 

videobuf2_core                      40664                   1 
uvcvideo
videodev                    134688                  2 
uvcvideo,videobuf2_core
kvm          455794                  1 
kvm_amd
snd_hda_intel                56531                   5 

binfmt_misc                         17468                   1 

snd_hda_codec                       192980                  3 
snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
arc4                   12608  2 
snd_hwdep              13602  1 snd_hda_codec
ath9k                 164164  0 
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
btusb                  32412  0 
bluetooth             391136  12 bnep,btusb,rfcomm
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
joydev                 17381  0 
mac80211              630728  1 ath9k
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
serio_raw              13462  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
k10temp                13126  0 
radeon               1522664  3 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
cfg80211              484040  3 ath,ath9k,mac80211
snd_timer              29482  2 snd_pcm,snd_seq
ttm                    93424  1 radeon
drm_kms_helper         55071  1 radeon
snd                    69322  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
i2c_piix4              22155  0 
drm                   303102  5 ttm,drm_kms_helper,radeon
shpchp                 37032  0 
soundcore              12680  1 snd
i2c_algo_bit           13413  1 radeon
wmi                    19177  1 asus_wmi
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
video                  19476  1 asus_wmi
mac_hid                13205  0 
ums_realtek            18029  0 
usb_storage            62209  2 ums_realtek
pata_acpi              13038  0 
psmouse               106590  0 
r8169                  67581  0 
mii                    13934  1 r8169
ahci                   29915  2 
pata_atiixp            13271  0 
libahci                32716  1 ahci
K53U:~$ usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 5
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.13
S:  Manufacturer=Linux 3.13.0-55-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:12.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  7 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=ff MxPS=64 #Cfgs=  2
P:  Vendor=12d1 ProdID=1446 Rev=01.02
S:  Manufacturer=HUAWEI
S:  Product=HUAWEI Mobile
S:  SerialNumber=FFFFFFFFFFFFFFFF
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=01 Lev=01 Prnt=01 Port=02 Cnt=02 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=04f2 ProdID=b23b Rev=26.62
S:  Manufacturer=Chicony
S:  Product=Chicony CNFA078
S:  SerialNumber=0x0001
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 5
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.13
S:  Manufacturer=Linux 3.13.0-55-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:13.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.13
S:  Manufacturer=Linux 3.13.0-55-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:16.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 5
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.13
S:  Manufacturer=Linux 3.13.0-55-generic ohci_hcd
S:  Product=OHCI PCI host controller
S:  SerialNumber=0000:00:12.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=01 Prnt=01 Port=03 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=04ca ProdID=3002 Rev=00.01
C:  #Ifs= 2 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb

T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 5
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.13
S:  Manufacturer=Linux 3.13.0-55-generic ohci_hcd
S:  Product=OHCI PCI host controller
S:  SerialNumber=0000:00:13.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=06 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.13
S:  Manufacturer=Linux 3.13.0-55-generic ohci_hcd
S:  Product=OHCI PCI host controller
S:  SerialNumber=0000:00:14.5
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=07 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 4
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.13
S:  Manufacturer=Linux 3.13.0-55-generic ohci_hcd
S:  Product=OHCI PCI host controller
S:  SerialNumber=0000:00:16.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

K53U:~$ lsusb -v -d 12d1:1446

Bus 001 Device 011: ID 12d1:1446 Huawei Technologies Co., Ltd. E1552/E1800/E173 (HSPA modem)
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol       255 
  bMaxPacketSize0        64
  idVendor           0x12d1 Huawei Technologies Co., Ltd.
  idProduct          0x1446 E1552/E1800/E173 (HSPA modem)
  bcdDevice            1.02
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      2
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk-Only
      iInterface              4 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          110
    bNumInterfaces          3
    bConfigurationValue     2
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              500mA
    Interface Association:
      bLength                 8
      bDescriptorType        11
      bFirstInterface         0
      bInterfaceCount         2
      bFunctionClass          2 Communications
      bFunctionSubClass      14 
      bFunctionProtocol       0 
      iFunction               8 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         2 Communications
      bInterfaceSubClass     14 
      bInterfaceProtocol      0 
      iInterface              5 
      CDC Header:
        bcdCDC               1.10
      CDC MBIM:
        bcdMBIMVersion       1.00
        wMaxControlMessage   1024
        bNumberFilters       16
        bMaxFilterSize       20
        wMaxSegmentSize      1500
        bmNetworkCapabilities 0x20
          8-byte ntb input size
      CDC Union:
        bMasterInterface        0
        bSlaveInterface         1 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               9
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      2 
      iInterface              6 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      2 
      iInterface              6 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk-Only
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1

```

---

### Post by praseodym on 2015-10-19
> ```
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=[COLOR="#FF0000"]usb-storage[/COLOR]
```
Is it shown as a storage device? If yes, ricght-click->unmount

Did you install "usb-modeswitch"?

---

### Post by eruptionjoojo on 2015-10-19
Thanks a lot for your reply .......... I'm just gonna try this unmount one and about the 'usb-modeswitch' - I haven't installed it as such because it was previously directly showing the Enable Mobile Broadband option as well listing my ISP in the Connections list. Anyhow if I have to install it what is the detailed procedure(if you could guide me via offline mode) because I can't directly install it on my Laptop as such because the only way to access internet is my Huawei Data Card which unfortunately is not connecting under Ubuntu.

---

### Post by praseodym on 2015-10-19
You need these files, save them in "Downloads":

[http://de.archive.ubuntu.com/ubuntu/pool/main/u/usb-modeswitch/usb-modeswitch_2.1.1+repack0-1ubuntu1_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/u/usb-modeswitch/usb-modeswitch_2.1.1+repack0-1ubuntu1_amd64.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/main/u/usb-modeswitch-data/usb-modeswitch-data_20140327-1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/u/usb-modeswitch-data/usb-modeswitch-data_20140327-1_all.deb)

Installation:
```

sudo dpkg -i ~/Downloads/*.deb
sudo service udev reload
sudo service udev restart
```
You may need to reboot. Check the outputs again.

---

### Post by eruptionjoojo on 2015-10-20
Thanks a lot for the help ............ really appreciate it. I'm gonno install this usb-modeswitch and report back.

Sorry for replying this late ........ here's the output : 
```

K53U:~$ lsusb
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 12d1:1506 Huawei Technologies Co., Ltd. E398 LTE/UMTS/GSM Modem/Networkcard
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b23b Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 04ca:3002 Lite-On Technology Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

K53U:~$ lsmod
Module                  Size  Used by
nls_utf8               12557  1 
huawei_cdc_ncm         12966  0 
cdc_wdm                19053  1 huawei_cdc_ncm
cdc_ncm                24511  1 huawei_cdc_ncm
option                 46837  0 
usb_wwan               20429  1 option
usbnet                 43913  2 huawei_cdc_ncm,cdc_ncm
usbserial              45014  2 option,usb_wwan
isofs                  39837  1 
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             27613  0 
vboxdrv               339502  3 vboxnetadp,vboxnetflt,vboxpci
snd_hda_codec_realtek    65626  1 
snd_hda_codec_hdmi     46368  1 
asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
rfcomm                 69160  0 
bnep                   19624  2 
kvm_amd                60026  0 
arc4                   12608  2 
ath9k                 164164  0 
ath9k_common           13551  1 ath9k
kvm                   455794  1 kvm_amd
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630728  1 ath9k
snd_seq_midi           13324  0 
btusb                  32412  0 
snd_seq_midi_event     14899  1 snd_seq_midi
bluetooth             391136  12 bnep,btusb,rfcomm
snd_hda_intel          56531  5 
snd_rawmidi            30144  1 snd_seq_midi
snd_hda_codec         192980  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
joydev                 17381  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
serio_raw              13462  0 
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
radeon               1522664  3 
cfg80211              484040  3 ath,ath9k,mac80211
k10temp                13126  0 
binfmt_misc            17468  1 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
ttm                    93424  1 radeon
snd_timer              29482  2 snd_pcm,snd_seq
drm_kms_helper         55071  1 radeon
i2c_piix4              22155  0 
drm                   303102  5 ttm,drm_kms_helper,radeon
snd                    69322  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
i2c_algo_bit           13413  1 radeon
shpchp                 37032  0 
soundcore              12680  1 snd
wmi                    19177  1 asus_wmi
video                  19476  1 asus_wmi
mac_hid                13205  0 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
ums_realtek            18029  0 
usb_storage            62209  2 ums_realtek
pata_acpi              13038  0 
psmouse               106590  0 
r8169                  67581  0 
mii                    13934  2 r8169,usbnet
pata_atiixp            13271  0 
ahci                   29915  2 
libahci                32716  1 ahci

K53U:~$ usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 5
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.13
S:  Manufacturer=Linux 3.13.0-55-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:12.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=04f2 ProdID=b23b Rev=26.62
S:  Manufacturer=Chicony
S:  Product=Chicony CNFA078
S:  SerialNumber=0x0001
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 5
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.13
S:  Manufacturer=Linux 3.13.0-55-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:13.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=02(commc) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1506 Rev=01.02
S:  Manufacturer=HUAWEI
S:  Product=HUAWEI Mobile
C:  #Ifs= 6 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=03 Prot=01 Driver=option
I:  If#= 1 Alt= 1 #EPs= 3 Cls=ff(vend.) Sub=03 Prot=16 Driver=huawei_cdc_ncm
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=03 Prot=03 Driver=option
I:  If#= 3 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=03 Prot=02 Driver=option
I:  If#= 4 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 5 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.13
S:  Manufacturer=Linux 3.13.0-55-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:16.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 5
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.13
S:  Manufacturer=Linux 3.13.0-55-generic ohci_hcd
S:  Product=OHCI PCI host controller
S:  SerialNumber=0000:00:12.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=01 Prnt=01 Port=03 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=04ca ProdID=3002 Rev=00.01
C:  #Ifs= 2 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb

T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 5
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.13
S:  Manufacturer=Linux 3.13.0-55-generic ohci_hcd
S:  Product=OHCI PCI host controller
S:  SerialNumber=0000:00:13.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=06 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.13
S:  Manufacturer=Linux 3.13.0-55-generic ohci_hcd
S:  Product=OHCI PCI host controller
S:  SerialNumber=0000:00:14.5
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=07 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 4
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.13
S:  Manufacturer=Linux 3.13.0-55-generic ohci_hcd
S:  Product=OHCI PCI host controller
S:  SerialNumber=0000:00:16.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

K53U:~$ lsusb -vd 12d1:1506

Bus 002 Device 003: ID 12d1:1506 Huawei Technologies Co., Ltd. E398 LTE/UMTS/GSM Modem/Networkcard
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            2 Communications
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x12d1 Huawei Technologies Co., Ltd.
  idProduct          0x1506 E398 LTE/UMTS/GSM Modem/Networkcard
  bcdDevice            1.02
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          225
    bNumInterfaces          6
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      3 
      bInterfaceProtocol      1 
      iInterface              0 
      ** UNRECOGNIZED:  05 24 00 10 01
      ** UNRECOGNIZED:  04 24 02 02
      ** UNRECOGNIZED:  05 24 01 00 00
      ** UNRECOGNIZED:  05 24 06 00 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               5
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      3 
      bInterfaceProtocol     22 
      iInterface              5 
      ** UNRECOGNIZED:  05 24 00 10 01
      ** UNRECOGNIZED:  06 24 1a 00 01 1f
      ** UNRECOGNIZED:  0d 24 0f 07 0f 00 00 00 ea 05 03 00 01
      ** UNRECOGNIZED:  05 24 06 01 01
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               9
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      3 
      bInterfaceProtocol     22 
      iInterface              6 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               9
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      3 
      bInterfaceProtocol      3 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x86  EP 6 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        3
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      3 
      bInterfaceProtocol      2 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x87  EP 7 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x05  EP 5 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        4
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk-Only
      iInterface              4 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x88  EP 8 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x06  EP 6 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        5
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk-Only
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x89  EP 9 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x07  EP 7 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1


```
Please do guide me as to what needs to be done NEXT.

---

### Post by praseodym on 2015-10-21
Lets do an udev-rule:
```

gksudo gedit /etc/udev/rules.d/70-usb-modeswitch.rules
```
Add these lines:
```

ACTION=="add", SUBSYSTEM=="usb", ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1446", RUN+="/usr/sbin/usb_modeswitch -v 12d1 -p 1446 -M '55534243123456780000000000000011062000000100000000000000000000'"
ACTION=="add", SUBSYSTEM=="usb", ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1506", RUN+="/bin/bash -c 'modprobe option && echo 12d1 1506 > /sys/bus/usb-serial/drivers/option1/new_id'"
```
Save, close the editor and reboot.

---

### Post by eruptionjoojo on 2015-10-22
Thanks again for your reply .......... anyhow I was just wondering, looking at the code - 'Do I need to add ATTRS{idProduct}== ----- for each usb port individually i.e. it seems that for each USB port it showcases a different 'idProduct' i.e. ATTRS{idProduct}=="1446" & ATTRS{idProduct}=="1506" and if so ..... how would I do that ... is it just by changing the 'idproduct' for each USB port and adding the line -
```

ACTION=="add", SUBSYSTEM=="usb", ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="abcd", RUN+="/bin/bash -c 'modprobe option && echo 12d1 abcd > /sys/bus/usb-serial/drivers/option1/new_id'"

```
*abcd is the idProduct
or something else needs to be done.

I added the specified lines and then rebooted the system, but then now again that - Enable Mobile Broadband Network options is available as well my ISP(BSNL- Cellone;India) is also listed. As soon as I enable the mobile broadband network, it tries to connect but connection doesn't get established, finally again shows Disconnected from the network.

---

### Post by praseodym on 2015-10-22
1446 is the storage mode, 1506 modem mode. Tried USB 3 or 2 slots?

---

### Post by eruptionjoojo on 2015-10-22
ok! thanks for updating my knowledge .......... anyhow USB 2.0 with 3 slots are there on my laptop and I have tried using the USB Data Card on all the 3 USB slots but haven't been successful.

---

### Post by praseodym on 2015-10-24
Lets try;
```

sudo modprobe -rfv option cdc_wdm cdc_ncm
sudo modprobe -v option
sudo service network-manager restart
```
Is there a web-login for this stick with your browser?

---

### Post by eruptionjoojo on 2015-10-25
Thanks again for trying to help ......... anyhow before plugging-in the USB Data Card I executed the following commands and the output are as listed below :- 
```

K53U:~$ sudo modprobe -rfv option cdc_wdm cdc_ncm
[sudo] password for K53U: 
K53U:~$ sudo modprobe -v option
insmod /lib/modules/3.13.0-55-generic/kernel/drivers/usb/serial/usbserial.ko 
insmod /lib/modules/3.13.0-55-generic/kernel/drivers/usb/serial/usb_wwan.ko 
insmod /lib/modules/3.13.0-55-generic/kernel/drivers/usb/serial/option.ko 
K53U:~$ sudo service network-manager restart
network-manager stop/waiting
network-manager start/running, process 2291

```
Then I plugged in the USB Data card but, still it didn't get connected although there was one minor change visible and that was while it showed disconnected - the symbol used for disconnection was the one with Network Towers i.e. which showcases signal strangth. 
If there is any other information that you need just ask for it please and yeah there is no web-login for this stick.

---

### Post by praseodym on 2015-10-25
Please show:

```
mmcli -m [COLOR="#FF0000"]0[/COLOR] | grep -Ev "imei|equipment|Numbers"
```
If the stick was plugged multiple times, then repeat the command replacing the "0" with 1,2,3, etc.

---

### Post by eruptionjoojo on 2015-10-26
Thanks again for your reply ........... this is the output while I plugged in the USB Data Card for the 1st time(*without enabling the Mobile Broadband under Network Manager).
```

K53U:~$ mmcli -m 0 | grep -Ev "imei|equipment|Numbers"

/org/freedesktop/ModemManager1/Modem/0 (device id '963c4d74ec913eba8024cda89744dc0e6854d8f8')
  -------------------------
  Hardware |   manufacturer: 'huawei'
           |          model: 'E173'
           |       revision: '21.318.15.00.910'
           |      supported: 'gsm-umts'
           |        current: 'gsm-umts'
  -------------------------
  System   |         device: '/sys/devices/pci0000:00/0000:00:13.2/usb2/2-1'
           |        drivers: 'option1'
           |         plugin: 'Huawei'
           |   primary port: 'ttyUSB2'
           |          ports: 'ttyUSB0 (at), ttyUSB2 (at)'
  -------------------------
  -------------------------
  Status   |           lock: 'none'
           | unlock retries: 'sim-pin (3), sim-pin2 (3), sim-puk (10), sim-puk2 (10)'
           |          state: 'disabled'
           |    power state: 'on'
           |    access tech: 'unknown'
           | signal quality: '0' (cached)
  -------------------------
  Modes    |      supported: 'allowed: any; preferred: none'
           |        current: 'allowed: any; preferred: none'
  -------------------------
  Bands    |      supported: 'unknown'
           |        current: 'unknown'
  -------------------------
  IP       |      supported: 'ipv4, ipv6, ipv4v6'
  -------------------------
           |  enabled locks: 'none'
           |    operator id: 'unknown'
           |  operator name: 'unknown'
           |   registration: 'unknown'
  -------------------------
  SIM      |           path: '/org/freedesktop/ModemManager1/SIM/0'

```

Plugged in the USB Data Card in the same USB port with Mobile Broadband Enabled - 2nd time
```

K53U:~$ mmcli -m 1 | grep -Ev "imei|equipment|Numbers"

/org/freedesktop/ModemManager1/Modem/1 (device id '963c4d74ec913eba8024cda89744dc0e6854d8f8')
  -------------------------
  Hardware |   manufacturer: 'huawei'
           |          model: 'E173'
           |       revision: '21.318.15.00.910'
           |      supported: 'gsm-umts'
           |        current: 'gsm-umts'
  -------------------------
  System   |         device: '/sys/devices/pci0000:00/0000:00:13.2/usb2/2-1'
           |        drivers: 'option1'
           |         plugin: 'Huawei'
           |   primary port: 'ttyUSB3'
           |          ports: 'ttyUSB0 (at), ttyUSB3 (at)'
  -------------------------
  -------------------------
  Status   |           lock: 'none'
           | unlock retries: 'sim-pin (3), sim-pin2 (3), sim-puk (10), sim-puk2 (10)'
           |          state: 'registered'
           |    power state: 'on'
           |    access tech: 'umts'
           | signal quality: '51' (recent)
  -------------------------
  Modes    |      supported: 'allowed: any; preferred: none'
           |        current: 'allowed: any; preferred: none'
  -------------------------
  Bands    |      supported: 'unknown'
           |        current: 'unknown'
  -------------------------
  IP       |      supported: 'ipv4, ipv6, ipv4v6'
  -------------------------
           |  enabled locks: 'none'
           |    operator id: '40458'
           |  operator name: 'BSNL MOBILE'
           |   registration: 'home'
  -------------------------
  SIM      |           path: '/org/freedesktop/ModemManager1/SIM/1'

```

---

### Post by praseodym on 2015-10-26
> ```
           | unlock retries: 'sim-pin (3), sim-pin2 (3), sim-puk (10), sim-puk2 (10)'
           |          state: 'disabled'
```
The SIM card is disabled, the maximum tries 3 for the PIN and 10 for the PUK are still available. Lets try to send the PIN directly:
```

mmcli -i 0 --pin=xxxx
```
Replace xxxx with the PIN and check the output again.

---

### Post by eruptionjoojo on 2015-10-26
Thanks again ......... anyhow it seems, by mistake you took note of just the 1st ouput i.e. while I had not check marked the Mobile Broadband Network connection option but in the second output when I have enabled the Mobile Broadband Internet option under network, the following output is visible :-
```

Status   |           lock: 'none'
           | unlock retries: 'sim-pin (3), sim-pin2 (3), sim-puk (10), sim-puk2 (10)'
           |          state: 'registered'
           |    power state: 'on'
           |    access tech: 'umts'
           | signal quality: '51' (recent)

```
I suppose this states that it is not locked I guess ........ please would you check again and correct me If I'm wrong?
Regards.

---

### Post by praseodym on 2015-10-26
Yes, it is not locked. Please check:

```
sudo adduser $(whoami) dialout 
```
Login again and check

```
sudo service modemmanager stop 
echo -e "AT+CPIN?\r" > /dev/ttyUSB0 && cat /dev/ttyUSB0 
sudo service modemmanager start 
```
You can also try "USB1" or "USB2" in the 2nd command

---

### Post by eruptionjoojo on 2015-10-26
No success, btw here's the output while I tried to connect : -
```

K53U:~$ mmcli -m 0 | grep -Ev "imei|equipment|Numbers"

/org/freedesktop/ModemManager1/Modem/0 (device id '963c4d74ec913eba8024cda89744dc0e6854d8f8')
  -------------------------
  Hardware |   manufacturer: 'huawei'
           |          model: 'E173'
           |       revision: '21.318.15.00.910'
           |      supported: 'gsm-umts'
           |        current: 'gsm-umts'
  -------------------------
  System   |         device: '/sys/devices/pci0000:00/0000:00:13.2/usb2/2-1'
           |        drivers: 'option1'
           |         plugin: 'Huawei'
           |   primary port: 'ttyUSB2'
           |          ports: 'ttyUSB0 (at), ttyUSB2 (at)'
  -------------------------
  -------------------------
  Status   |           lock: 'none'
           | unlock retries: 'sim-pin (3), sim-pin2 (0), sim-puk (10), sim-puk2 (10)'
           |          state: 'connecting'
           |    power state: 'on'
           |    access tech: 'umts'
           | signal quality: '51' (recent)
  -------------------------
  Modes    |      supported: 'allowed: any; preferred: none'
           |        current: 'allowed: any; preferred: none'
  -------------------------
  Bands    |      supported: 'unknown'
           |        current: 'unknown'
  -------------------------
  IP       |      supported: 'ipv4, ipv6, ipv4v6'
  -------------------------
           |  enabled locks: 'none'
           |    operator id: '40458'
           |  operator name: 'BSNL'
           |   registration: 'roaming'
  -------------------------
  SIM      |           path: '/org/freedesktop/ModemManager1/SIM/0'

K53U:~$ mmcli -m 0 | grep -Ev "imei|equipment|Numbers"

/org/freedesktop/ModemManager1/Modem/0 (device id '963c4d74ec913eba8024cda89744dc0e6854d8f8')
  -------------------------
  Hardware |   manufacturer: 'huawei'
           |          model: 'E173'
           |       revision: '21.318.15.00.910'
           |      supported: 'gsm-umts'
           |        current: 'gsm-umts'
  -------------------------
  System   |         device: '/sys/devices/pci0000:00/0000:00:13.2/usb2/2-1'
           |        drivers: 'option1'
           |         plugin: 'Huawei'
           |   primary port: 'ttyUSB2'
           |          ports: 'ttyUSB0 (at), ttyUSB2 (at)'
  -------------------------
  -------------------------
  Status   |           lock: 'none'
           | unlock retries: 'sim-pin (3), sim-pin2 (0), sim-puk (10), sim-puk2 (10)'
           |          state: 'registered'
           |    power state: 'on'
           |    access tech: 'umts'
           | signal quality: '51' (recent)
  -------------------------
  Modes    |      supported: 'allowed: any; preferred: none'
           |        current: 'allowed: any; preferred: none'
  -------------------------
  Bands    |      supported: 'unknown'
           |        current: 'unknown'
  -------------------------
  IP       |      supported: 'ipv4, ipv6, ipv4v6'
  -------------------------
           |  enabled locks: 'none'
           |    operator id: '40458'
           |  operator name: 'BSNL'
           |   registration: 'roaming'
  -------------------------
  SIM      |           path: '/org/freedesktop/ModemManager1/SIM/0'


```

Then it showed it had got disconnected, here is the output of the other commands :

```

K53U:~$ sudo adduser $(whoami) dialout
[sudo] password for K53U: 
The user `K53U' is already a member of `dialout'

K53U:~$ sudo service modemmanager stop
modemmanager stop/waiting
K53U:~$ echo -e "AT+CPIN?\r" > /dev/ttyUSB0 && cat /dev/ttyUSB0

+CPIN: READY

OK
^C
K53U:~$ sudo service modemmanager start
[sudo] password for K53U: 
modemmanager start/running, process 2731


K53U:~$ sudo service modemmanager stop
modemmanager stop/waiting
K53U:~$ echo -e "AT+CPIN?\r" > /dev/ttyUSB1 && cat /dev/ttyUSB1
bash: /dev/ttyUSB1: Permission denied

K53U:~$ sudo service modemmanager stop
modemmanager stop/waiting
K53U:~$ echo -e "AT+CPIN?\r" > /dev/ttyUSB2 && cat /dev/ttyUSB2
^C
K53U:~$ sudo service modemmanager start
modemmanager start/running, process 2806

```
had to press ctrl+C in order to get out as it had got stuck there for more than 15 minutes and there is one instance where it showed Permission Denied too.
Now what to do next ??


Anyhow just now I plugged in the Data Card on Kali Linux 64 bit(have it on my Pendrive) and it works absolutely fine.

---

### Post by praseodym on 2015-10-27
```
cat /etc/udev/rules.d/70-usb-modeswitch.rules
```
please. Do you have a Windows system to check the stick?

---

### Post by eruptionjoojo on 2015-10-28
thanks again ....... yeah I do have windows 7 .. infact i'm using it to post these replies. It's working perfectly fine in both the OS's i.e. Windows 7 64 bit as well as in Kali Linux. I will be posting the output of the command in a short while.

Here's the output : 
```

K53U:~$ cat /etc/udev/rules.d/70-usb-modeswitch.rules
ACTION=="add", SUBSYSTEM=="usb", ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1446", RUN+="/usr/sbin/usb_modeswitch -v 12d1 -p 1446 -M '55534243123456780000000000000011062000000100000000000000000000'"
ACTION=="add", SUBSYSTEM=="usb", ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1506", RUN+="/bin/bash -c 'modprobe option && echo 12d1 1506 > /sys/bus/usb-serial/drivers/option1/new_id'"

```

---

### Post by eruptionjoojo on 2015-10-29
Could somebody please help me with this disconnection issue ........... ?

---

### Post by praseodym on 2015-10-29
Do you know the mtu-value of your ISP? If yes, add it as a number instead of "Automatic" to your network-manager profile

---

### Post by eruptionjoojo on 2015-10-29
Sorry!to be but I really don't have any idea about the MTU value ........... neither as of how to set it ............

---

### Post by eruptionjoojo on 2015-11-03
Could somebody please help me out with this issue of mine ......... I'm unable to access internet on my Ubuntu 14.04 (64 bit), it's just that while I try to connect it shows - You are registered on the 
Home network and then just disconnects. The USB data card is working perfectly fine on Kali Linux (64 bit) as well as on Windows 7(64 bit). If you need any other info, just ask for it.

---

### Post by praseodym on 2015-11-03
Please show all of the outputs from above under Kali:
```

uname -a
lsusb
usb-devices
lsmod
ifconfig -a
route -n
```

---

### Post by eruptionjoojo on 2015-11-04
Thanks a lot again ......... here's the output :
```

root@kali:~# uname -a
Linux kali 3.14-kali1-amd64 #1 SMP Debian 3.14.5-1kali1 (2014-06-07) x86_64 GNU/Linux
root@kali:~# lsusb
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 12d1:1506 Huawei Technologies Co., Ltd. E398 LTE/UMTS/GSM Modem/Networkcard
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04f2:b23b Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 0781:5567 SanDisk Corp. Cruzer Blade
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 04ca:3002 Lite-On Technology Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
root@kali:~# usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 5
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.14
S:  Manufacturer=Linux 3.14-kali1-amd64 ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:12.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0781 ProdID=5567 Rev=01.27
S:  Manufacturer=SanDisk
S:  Product=Cruzer Blade
S:  SerialNumber=4C530099940527105391
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=200mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=01 Lev=01 Prnt=01 Port=02 Cnt=02 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=04f2 ProdID=b23b Rev=26.62
S:  Manufacturer=Chicony
S:  Product=Chicony CNFA078
S:  SerialNumber=0x0001
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 5
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.14
S:  Manufacturer=Linux 3.14-kali1-amd64 ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:13.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=02(commc) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1506 Rev=01.02
S:  Manufacturer=HUAWEI
S:  Product=HUAWEI Mobile
C:  #Ifs= 6 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=03 Prot=01 Driver=option
I:  If#= 1 Alt= 0 #EPs= 1 Cls=ff(vend.) Sub=03 Prot=16 Driver=(none)
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=03 Prot=03 Driver=option
I:  If#= 3 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=03 Prot=02 Driver=option
I:  If#= 4 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 5 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.14
S:  Manufacturer=Linux 3.14-kali1-amd64 ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:16.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 5
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.14
S:  Manufacturer=Linux 3.14-kali1-amd64 ohci_hcd
S:  Product=OHCI PCI host controller
S:  SerialNumber=0000:00:12.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=01 Prnt=01 Port=03 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=04ca ProdID=3002 Rev=00.01
C:  #Ifs= 2 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb

T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 5
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.14
S:  Manufacturer=Linux 3.14-kali1-amd64 ohci_hcd
S:  Product=OHCI PCI host controller
S:  SerialNumber=0000:00:13.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=06 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.14
S:  Manufacturer=Linux 3.14-kali1-amd64 ohci_hcd
S:  Product=OHCI PCI host controller
S:  SerialNumber=0000:00:14.5
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=07 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 4
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=03.14
S:  Manufacturer=Linux 3.14-kali1-amd64 ohci_hcd
S:  Product=OHCI PCI host controller
S:  SerialNumber=0000:00:16.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
root@kali:~# lsmod
Module                  Size  Used by
ppp_deflate            12834  0 
bsd_comp               12842  0 
ppp_async              17146  1 
crc_ccitt              12347  1 ppp_async
ppp_generic            30396  7 bsd_comp,ppp_async,ppp_deflate
slhc                   12562  1 ppp_generic
option                 45416  1 
usb_wwan               12998  1 option
usbserial              28105  5 option,usb_wwan
nls_utf8               12456  1 
isofs                  38963  1 
nfnetlink_log          17241  0 
nfnetlink              12989  1 nfnetlink_log
binfmt_misc            16949  1 
loop                   26605  0 
dm_crypt               22731  0 
snd_hda_codec_realtek    54360  1 
snd_hda_codec_generic    59079  1 snd_hda_codec_realtek
snd_hda_codec_hdmi     45004  1 
arc4                   12543  2 
ath9k                  98430  0 
uvcvideo               78910  0 
videobuf2_vmalloc      12816  1 uvcvideo
videobuf2_memops       12519  1 videobuf2_vmalloc
videobuf2_core         35348  1 uvcvideo
videodev              122088  2 uvcvideo,videobuf2_core
media                  18303  2 uvcvideo,videodev
ath9k_common           12634  1 ath9k
ath9k_hw              391009  2 ath9k_common,ath9k
snd_hda_intel          39656  5 
snd_hda_codec          99921  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
snd_hwdep              13148  1 snd_hda_codec
btusb                  25619  0 
bluetooth             243618  2 btusb
asus_nb_wmi            16568  0 
ath                    26026  3 ath9k_common,ath9k,ath9k_hw
snd_pcm                88538  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
asus_wmi               22933  1 asus_nb_wmi
sparse_keymap          12760  1 asus_wmi
radeon               1302204  2 
ttm                    69667  1 radeon
mac80211              488308  1 ath9k
drm_kms_helper         39998  1 radeon
snd_timer              26606  1 snd_pcm
cfg80211              436618  3 ath,ath9k,mac80211
6lowpan_iphc           16588  1 bluetooth
rfkill                 18902  4 cfg80211,bluetooth,asus_wmi
kvm_amd                54863  0 
evdev                  17489  9 
snd                    61039  18 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
sp5100_tco             12864  0 
soundcore              13026  1 snd
drm                   240557  4 ttm,drm_kms_helper,radeon
kvm                   404503  1 kvm_amd
psmouse                86464  0 
k10temp                12618  0 
serio_raw              12849  0 
i2c_piix4              12672  0 
i2c_algo_bit           12751  1 radeon
i2c_core               24265  6 drm,i2c_piix4,drm_kms_helper,i2c_algo_bit,radeon,videodev
battery                13101  0 
ac                     12678  0 
wmi                    17339  1 asus_wmi
video                  17804  1 asus_wmi
acpi_cpufreq           17218  0 
processor              28221  3 acpi_cpufreq
button                 12944  0 
ext4                  489943  1 
crc16                  12343  2 ext4,bluetooth
mbcache                13082  1 ext4
jbd2                   86788  1 ext4
ums_realtek            17223  0 
dm_mod                 89276  1 dm_crypt
sd_mod                 44346  3 
crct10dif_generic      12581  1 
sg                     30043  0 
sr_mod                 21898  1 
crc_t10dif             12431  1 sd_mod
cdrom                  39232  1 sr_mod
crct10dif_common       12356  2 crct10dif_generic,crc_t10dif
ata_generic            12490  0 
usb_storage            52037  4 ums_realtek
pata_atiixp            12747  0 
ahci                   29195  0 
libahci                27103  1 ahci
ohci_pci               12808  0 
ohci_hcd               34767  1 ohci_pci
ehci_pci               12472  0 
ehci_hcd               48517  1 ehci_pci
libata                169163  4 ahci,libahci,ata_generic,pata_atiixp
r8169                  64490  0 
mii                    12675  1 r8169
scsi_mod              186841  5 sg,usb_storage,libata,sd_mod,sr_mod
usbcore               166472  11 btusb,uvcvideo,ums_realtek,usb_storage,usbserial,ohci_hcd,ohci_pci,ehci_hcd,ehci_pci,option,usb_wwan
thermal                17468  0 
thermal_sys            27685  3 video,thermal,processor
usb_common             12440  1 usbcore
root@kali:~# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 11:fb:48:08:1d:7e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:59 errors:0 dropped:0 overruns:0 frame:0
          TX packets:59 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4156 (4.0 KiB)  TX bytes:4156 (4.0 KiB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.37.89.104  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:36898 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30286 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:38669374 (36.8 MiB)  TX bytes:4001293 (3.8 MiB)

wlan0     Link encap:Ethernet  HWaddr 43:2d:77:14:95:32  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

root@kali:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.64.64.64     0.0.0.0         UG    0      0        0 ppp0
10.64.64.64     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
root@kali:~# 

```

---

### Post by praseodym on 2015-11-04
Its not using the module cdc_ether. Lets try under Ubuntu:

```
sudo rmmod cdc_ether
```

---

### Post by eruptionjoojo on 2015-11-05
Here's the output:


```


K53U:~$ sudo rmmod cdc_ether
[sudo] password for K53U: 
rmmod: ERROR: Module cdc_ether is not currently loaded


```

What else can I try ??

---

### Post by eruptionjoojo on 2015-11-07
Could somebody please help me out in sorting this issue of - Internet Connection - not getting established under Ubuntu 14.04(64 bit) using a USB Data Card while it runs smoothly under Windows 7(64 bit) as well on Kali Linux(64 bit).

"praseodym" has been trying to help, but I guess he has been busy lately so has not replied. Anyhow, could somebody suggest me something that I could try to fix this.

---

### Post by praseodym on 2015-11-08
Kali runs kernel 3.14, Ubuntu 3.13. Lets try to install the LTS enablement stack with a newer kernel:

```
sudo apt-get -s install --install-recommends linux-generic-lts-vivid xserver-xorg-core-lts-vivid xserver-xorg-lts-vivid xserver-xorg-video-all-lts-vivid xserver-xorg-input-all-lts-vivid libwayland-egl1-mesa-lts-vivid 
```
This simulates the installation. If it runs without errors then repeat the line without "- s". If you installed on an UEFI system then also run afterwards:

```
sudo apt-get install linux-signed-generic-lts-vivid 
```

In any case run:

```
sudo dpkg-reconfigure xserver-xorg-lts-vivid 
```
and reboot. Check then
```

uname -a
```

---

### Post by howefield on 2015-11-08
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by praseodym on 2015-11-08
Please return it back to the networking section, the thread starter uses Ubuntu, the card works with Kali, but not with Ubuntu, the Kali output was for comparison!

---

### Post by howefield on 2015-11-08
With a more careful read, that seems fair enough!

---

### Post by eruptionjoojo on 2015-11-08
Thanks again ........... anyhow, do I need to download these packages and then install them, please clarify. Here's the output by the way :
```

K53U:~$ sudo apt-get -s install --install-recommends linux-generic-lts-vivid xserver-xorg-core-lts-vivid xserver-xorg-lts-vivid xserver-xorg-video-all-lts-vivid xserver-xorg-input-all-lts-vivid libwayland-egl1-mesa-lts-vivid
[sudo] password for K53U: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fonts-horai-umefont gnome-exe-thumbnailer libasn1-8-heimdal:i386
  libaudio2:i386 libavahi-client3:i386 libavahi-common-data:i386
  libavahi-common3:i386 libcapi20-3 libcapi20-3:i386 libcups2:i386
  libdbusmenu-qt2:i386 libdrm-intel1:i386 libdrm-nouveau2:i386
  libdrm-radeon1:i386 libelf1:i386 libexif12:i386 libexpat1:i386 libffi6:i386
  libfontconfig1:i386 libgcrypt11:i386 libgd3:i386 libgif4:i386
  libglib2.0-0:i386 libgnutls26:i386 libgpg-error0:i386 libgphoto2-6:i386
  libgphoto2-port10:i386 libgssapi-krb5-2:i386 libgssapi3-heimdal:i386
  libgstreamer-plugins-base0.10-0:i386 libgstreamer-plugins-base1.0-0:i386
  libgstreamer0.10-0:i386 libgstreamer1.0-0:i386 libhcrypto4-heimdal:i386
  libheimbase1-heimdal:i386 libheimntlm0-heimdal:i386 libhx509-5-heimdal:i386
  libieee1284-3:i386 libjbig0:i386 libjpeg-turbo8:i386 libjpeg8:i386
  libk5crypto3:i386 libkeyutils1:i386 libkrb5-26-heimdal:i386 libkrb5-3:i386
  libkrb5support0:i386 liblcms2-2:i386 libldap-2.4-2:i386 libllvm3.4:i386
  libltdl7:i386 libmpg123-0:i386 libmysqlclient18:i386 libodbc1
  libopenal1:i386 liborc-0.4-0:i386 libp11-kit-gnome-keyring:i386
  libp11-kit0:i386 libpciaccess0:i386 libqt4-dbus:i386 libqt4-declarative:i386
  libqt4-network:i386 libqt4-script:i386 libqt4-sql:i386 libqt4-sql-mysql:i386
  libqt4-xml:i386 libqt4-xmlpatterns:i386 libqtcore4:i386 libqtdbus4:i386
  libqtgui4:i386 libroken18-heimdal:i386 libsane:i386 libsasl2-2:i386
  libsasl2-modules:i386 libsasl2-modules-db:i386 libsqlite3-0:i386
  libssl1.0.0:i386 libtasn1-6:i386 libtiff5:i386 libtxc-dxtn-s2tc0:i386
  libusb-1.0-0:i386 libv4l-0:i386 libv4lconvert0:i386 libvpx1:i386
  libwind0-heimdal:i386 libx11-xcb1:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386
  libxcb-glx0:i386 libxcb-present0:i386 libxcb-sync1:i386 libxcomposite1:i386
  libxcursor1:i386 libxi6:i386 libxinerama1:i386 libxml2:i386 libxpm4:i386
  libxshmfence1:i386 libxslt1.1:i386 libxss1:i386 libxv1:i386 libxxf86vm1:i386
  mysql-common ocl-icd-libopencl1:i386 odbcinst odbcinst1debian2
  p11-kit-modules:i386 p7zip sni-qt:i386 unixodbc wine-gecko2.21
  wine-gecko2.21:i386 wine-mono0.0.8 winetricks
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libegl1-mesa-lts-vivid libepoxy0 libevdev2 libgbm1-lts-vivid
  libgl1-mesa-dri-lts-vivid libgl1-mesa-glx-lts-vivid libglapi-mesa-lts-vivid
  libgles1-mesa-lts-vivid libgles2-mesa-lts-vivid libllvm3.6
  libxatracker2-lts-vivid linux-headers-3.19.0-25
  linux-headers-3.19.0-25-generic linux-headers-generic-lts-vivid
  linux-image-3.19.0-25-generic linux-image-extra-3.19.0-25-generic
  linux-image-generic-lts-vivid thermald xserver-xorg-input-evdev-lts-vivid
  xserver-xorg-input-mouse-lts-vivid xserver-xorg-input-synaptics-lts-vivid
  xserver-xorg-input-vmmouse-lts-vivid xserver-xorg-input-wacom-lts-vivid
  xserver-xorg-video-ati-lts-vivid xserver-xorg-video-cirrus-lts-vivid
  xserver-xorg-video-fbdev-lts-vivid xserver-xorg-video-intel-lts-vivid
  xserver-xorg-video-mach64-lts-vivid xserver-xorg-video-mga-lts-vivid
  xserver-xorg-video-neomagic-lts-vivid xserver-xorg-video-nouveau-lts-vivid
  xserver-xorg-video-openchrome-lts-vivid xserver-xorg-video-r128-lts-vivid
  xserver-xorg-video-radeon-lts-vivid xserver-xorg-video-savage-lts-vivid
  xserver-xorg-video-siliconmotion-lts-vivid
  xserver-xorg-video-sisusb-lts-vivid xserver-xorg-video-tdfx-lts-vivid
  xserver-xorg-video-trident-lts-vivid xserver-xorg-video-vesa-lts-vivid
  xserver-xorg-video-vmware-lts-vivid
Suggested packages:
  fdutils linux-lts-vivid-tools xfonts-100dpi xfonts-75dpi
  gpointing-device-settings touchfreeze firmware-linux
Recommended packages:
  libegl1-mesa-drivers-lts-vivid
The following packages will be REMOVED
  libegl1-mesa libegl1-mesa-drivers libgl1-mesa-dri libgl1-mesa-dri:i386
  libgl1-mesa-glx libgl1-mesa-glx:i386 libglapi-mesa libglapi-mesa:i386
  libgles1-mesa libgles2-mesa libglu1-mesa:i386 libopenvg1-mesa libosmesa6
  libosmesa6:i386 libqt4-opengl:i386 libqtwebkit4:i386 libwayland-egl1-mesa
  libxatracker2 skype skype-bin:i386 wine1.6 wine1.6-amd64 wine1.6-i386:i386
  xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-ati
  xserver-xorg-video-cirrus xserver-xorg-video-fbdev
  xserver-xorg-video-glamoregl xserver-xorg-video-intel
  xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-modesetting xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-openchrome
  xserver-xorg-video-qxl xserver-xorg-video-r128 xserver-xorg-video-radeon
  xserver-xorg-video-s3 xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-vesa xserver-xorg-video-vmware
The following NEW packages will be installed
  libegl1-mesa-lts-vivid libepoxy0 libevdev2 libgbm1-lts-vivid
  libgl1-mesa-dri-lts-vivid libgl1-mesa-glx-lts-vivid libglapi-mesa-lts-vivid
  libgles1-mesa-lts-vivid libgles2-mesa-lts-vivid libllvm3.6
  libwayland-egl1-mesa-lts-vivid libxatracker2-lts-vivid
  linux-generic-lts-vivid linux-headers-3.19.0-25
  linux-headers-3.19.0-25-generic linux-headers-generic-lts-vivid
  linux-image-3.19.0-25-generic linux-image-extra-3.19.0-25-generic
  linux-image-generic-lts-vivid thermald xserver-xorg-core-lts-vivid
  xserver-xorg-input-all-lts-vivid xserver-xorg-input-evdev-lts-vivid
  xserver-xorg-input-mouse-lts-vivid xserver-xorg-input-synaptics-lts-vivid
  xserver-xorg-input-vmmouse-lts-vivid xserver-xorg-input-wacom-lts-vivid
  xserver-xorg-lts-vivid xserver-xorg-video-all-lts-vivid
  xserver-xorg-video-ati-lts-vivid xserver-xorg-video-cirrus-lts-vivid
  xserver-xorg-video-fbdev-lts-vivid xserver-xorg-video-intel-lts-vivid
  xserver-xorg-video-mach64-lts-vivid xserver-xorg-video-mga-lts-vivid
  xserver-xorg-video-neomagic-lts-vivid xserver-xorg-video-nouveau-lts-vivid
  xserver-xorg-video-openchrome-lts-vivid xserver-xorg-video-r128-lts-vivid
  xserver-xorg-video-radeon-lts-vivid xserver-xorg-video-savage-lts-vivid
  xserver-xorg-video-siliconmotion-lts-vivid
  xserver-xorg-video-sisusb-lts-vivid xserver-xorg-video-tdfx-lts-vivid
  xserver-xorg-video-trident-lts-vivid xserver-xorg-video-vesa-lts-vivid
  xserver-xorg-video-vmware-lts-vivid
0 to upgrade, 47 to newly install, 55 to remove and 29 not to upgrade.
Remv libwayland-egl1-mesa [10.1.3-0ubuntu0.4] [libegl1-mesa-drivers:amd64 ]
Remv libgl1-mesa-dri:i386 [10.1.3-0ubuntu0.4] [libegl1-mesa-drivers:amd64 ]
Remv xserver-xorg-video-radeon [1:7.3.0-1ubuntu3.1] [libegl1-mesa-drivers:amd64 xserver-xorg-video-ati:amd64 ]
Remv xserver-xorg-video-intel [2:2.99.910-0ubuntu1.6] [libegl1-mesa-drivers:amd64 xserver-xorg-video-all:amd64 xserver-xorg-video-ati:amd64 ]
Remv xserver-xorg-input-all [1:7.7+1ubuntu8.1] [libegl1-mesa-drivers:amd64 xserver-xorg-video-all:amd64 xserver-xorg-video-ati:amd64 ]
Remv xserver-xorg-input-wacom [1:0.23.0-0ubuntu2] [libegl1-mesa-drivers:amd64 xserver-xorg-video-all:amd64 xserver-xorg-video-ati:amd64 ]
Remv xserver-xorg-core [2:1.15.1-0ubuntu2.7] [xserver-xorg-video-vmware:amd64 xserver-xorg-video-siliconmotion:amd64 libegl1-mesa-drivers:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-glamoregl:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-all:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-ati:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv libgl1-mesa-dri [10.1.3-0ubuntu0.4] [xserver-xorg-video-vmware:amd64 xserver-xorg-video-siliconmotion:amd64 xorg:amd64 libegl1-mesa-drivers:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-glamoregl:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-all:amd64 xserver-xorg-video-qxl:amd64 libxatracker2:amd64 qtdeclarative5-qtquick2-plugin:amd64 xserver-xorg-video-ati:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-trident:amd64 libgbm1:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv xserver-xorg [1:7.7+1ubuntu8.1] [xserver-xorg-video-vmware:amd64 xserver-xorg-video-siliconmotion:amd64 xorg:amd64 libegl1-mesa-drivers:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-glamoregl:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-all:amd64 xserver-xorg-video-qxl:amd64 libxatracker2:amd64 qtdeclarative5-qtquick2-plugin:amd64 xserver-xorg-video-ati:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-trident:amd64 libgbm1:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Inst libgl1-mesa-dri-lts-vivid (10.5.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64]) [xserver-xorg-video-vmware:amd64 xserver-xorg-video-siliconmotion:amd64 xorg:amd64 libegl1-mesa-drivers:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-glamoregl:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-all:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-ati:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv xserver-xorg-video-vmware [1:13.0.2-2ubuntu1] [xserver-xorg-video-siliconmotion:amd64 xorg:amd64 libegl1-mesa-drivers:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-glamoregl:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-all:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-ati:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv libxatracker2 [10.1.3-0ubuntu0.4] [xserver-xorg-video-siliconmotion:amd64 xorg:amd64 libegl1-mesa-drivers:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-glamoregl:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-all:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-ati:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv skype [4.3.0.37-0ubuntu0.12.04.1] [xserver-xorg-video-siliconmotion:amd64 xorg:amd64 libegl1-mesa-drivers:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-glamoregl:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-all:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-ati:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv skype-bin:i386 [4.3.0.37-0ubuntu0.12.04.1] [xserver-xorg-video-siliconmotion:amd64 xorg:amd64 libegl1-mesa-drivers:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-glamoregl:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-all:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-ati:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv libqtwebkit4:i386 [2.3.2-0ubuntu7] [xserver-xorg-video-siliconmotion:amd64 xorg:amd64 libegl1-mesa-drivers:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-glamoregl:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-all:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-ati:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv libqt4-opengl:i386 [4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1] [xserver-xorg-video-siliconmotion:amd64 xorg:amd64 libegl1-mesa-drivers:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-glamoregl:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-all:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-ati:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv libgl1-mesa-glx:i386 [10.1.3-0ubuntu0.4] [xserver-xorg-video-siliconmotion:amd64 xorg:amd64 libegl1-mesa-drivers:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-glamoregl:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-all:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-ati:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 libglu1-mesa:i386 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv libgl1-mesa-glx [10.1.3-0ubuntu0.4] [libopencv-core2.4:amd64 xserver-xorg-video-siliconmotion:amd64 libcogl15:amd64 libglew1.10:amd64 gnome-session-bin:amd64 mesa-utils:amd64 libnux-4.0-0:amd64 xorg:amd64 x11-utils:amd64 libegl1-mesa-drivers:amd64 libqt5opengl5:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 libqt4-opengl:amd64 xserver-xorg-video-glamoregl:amd64 xserver-xorg-video-neomagic:amd64 unity:amd64 libgnome-desktop-3-7:amd64 vdpau-va-driver:amd64 xserver-xorg-input-synaptics:amd64 libqtwebkit4:amd64 libreoffice-core:amd64 libvisual-0.4-plugins:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-all:amd64 xserver-xorg-video-qxl:amd64 libqt5quick5:amd64 virtualbox-qt:amd64 libreoffice-ogltrans:amd64 libwebkitgtk-3.0-0:amd64 xserver-xorg-video-ati:amd64 freshplayerplugin:amd64 libglamor0:amd64 libxine2-x:amd64 libglewmx1.10:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 libqt5webkit5:amd64 openjdk-7-jre:amd64 xserver-xorg-video-trident:amd64 libopencv-highgui2.4:amd64 libgtkglext1:amd64 compiz-plugins-default:amd64 unity-control-center:amd64 xserver-xorg-video-openchrome:amd64 qtdeclarative5-ubuntu-ui-toolkit-plugin:amd64 xserver-xorg-input-vmmouse:amd64 nux-tools:amd64 vlc:amd64 libxine1-x:amd64 xserver-xorg-video-sis:amd64 libqt5gui5:amd64 mplayer:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 libva-glx1:amd64 libglu1-mesa:amd64 libglu1-mesa:i386 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 libwxgtk2.8-0:amd64 ]
Inst libgl1-mesa-glx-lts-vivid (10.5.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64]) [xserver-xorg-video-siliconmotion:amd64 xorg:amd64 libegl1-mesa-drivers:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-glamoregl:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-all:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-ati:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 libglu1-mesa:i386 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv libosmesa6 [10.1.3-0ubuntu0.4] [xserver-xorg-video-siliconmotion:amd64 xorg:amd64 libegl1-mesa-drivers:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-glamoregl:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-all:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-ati:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 libglu1-mesa:i386 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv libglapi-mesa [10.1.3-0ubuntu0.4] [xserver-xorg-video-siliconmotion:amd64 xorg:amd64 libegl1-mesa-drivers:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-glamoregl:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-all:amd64 xserver-xorg-video-qxl:amd64 libgles2-mesa:amd64 xserver-xorg-video-ati:amd64 libgles1-mesa:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 libglu1-mesa:i386 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv libosmesa6:i386 [10.1.3-0ubuntu0.4] [xserver-xorg-video-siliconmotion:amd64 xorg:amd64 libegl1-mesa-drivers:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-glamoregl:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-all:amd64 xserver-xorg-video-qxl:amd64 libgles2-mesa:amd64 xserver-xorg-video-ati:amd64 libgles1-mesa:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 libglu1-mesa:i386 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv libglapi-mesa:i386 [10.1.3-0ubuntu0.4] [xserver-xorg-video-siliconmotion:amd64 xorg:amd64 libegl1-mesa-drivers:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-glamoregl:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-all:amd64 xserver-xorg-video-qxl:amd64 libgles2-mesa:amd64 xserver-xorg-video-ati:amd64 libgles1-mesa:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 libglu1-mesa:i386 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv libgles1-mesa [10.1.3-0ubuntu0.4] [xserver-xorg-video-siliconmotion:amd64 xorg:amd64 libegl1-mesa-drivers:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-glamoregl:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-all:amd64 xserver-xorg-video-qxl:amd64 libgles2-mesa:amd64 xserver-xorg-video-ati:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 vlc:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 libglu1-mesa:i386 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Inst libgles1-mesa-lts-vivid (10.5.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64]) [xserver-xorg-video-siliconmotion:amd64 xorg:amd64 libegl1-mesa-drivers:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-glamoregl:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-all:amd64 xserver-xorg-video-qxl:amd64 libgles2-mesa:amd64 xserver-xorg-video-ati:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 libglu1-mesa:i386 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv libgles2-mesa [10.1.3-0ubuntu0.4] [xserver-xorg-video-siliconmotion:amd64 xorg:amd64 libegl1-mesa-drivers:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-glamoregl:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-all:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-ati:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 gstreamer1.0-plugins-bad:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 vlc:amd64 xserver-xorg-video-sis:amd64 libqt5gui5:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 libglu1-mesa:i386 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Inst libgles2-mesa-lts-vivid (10.5.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64]) [xserver-xorg-video-siliconmotion:amd64 xorg:amd64 libegl1-mesa-drivers:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-glamoregl:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-all:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-ati:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 libglu1-mesa:i386 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv libopenvg1-mesa [10.1.3-0ubuntu0.4] [xserver-xorg-video-siliconmotion:amd64 xorg:amd64 libegl1-mesa-drivers:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-glamoregl:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-all:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-ati:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 libglu1-mesa:i386 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv libegl1-mesa [10.1.3-0ubuntu0.4] [xserver-xorg-video-siliconmotion:amd64 libcogl15:amd64 xorg:amd64 libegl1-mesa-drivers:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-glamoregl:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-all:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-ati:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 gstreamer1.0-plugins-bad:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 vlc:amd64 xserver-xorg-video-sis:amd64 libqt5gui5:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 libglu1-mesa:i386 libgstreamer-plugins-bad1.0-0:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv libegl1-mesa-drivers [10.1.3-0ubuntu0.4] [xserver-xorg-video-siliconmotion:amd64 libcogl15:amd64 xorg:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-glamoregl:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-all:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-ati:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 gstreamer1.0-plugins-bad:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 vlc:amd64 xserver-xorg-video-sis:amd64 libqt5gui5:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 libglu1-mesa:i386 libgstreamer-plugins-bad1.0-0:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv xserver-xorg-video-all [1:7.7+1ubuntu8.1] [xserver-xorg-video-siliconmotion:amd64 libcogl15:amd64 xorg:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-glamoregl:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-ati:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 gstreamer1.0-plugins-bad:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 vlc:amd64 xserver-xorg-video-sis:amd64 libqt5gui5:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 libglu1-mesa:i386 libgstreamer-plugins-bad1.0-0:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Inst xserver-xorg-lts-vivid (1:7.7+7ubuntu3~trusty1 Ubuntu:14.04/trusty-updates [amd64]) [xserver-xorg-video-siliconmotion:amd64 libcogl15:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-glamoregl:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-ati:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 gstreamer1.0-plugins-bad:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 vlc:amd64 xserver-xorg-video-sis:amd64 libqt5gui5:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 libglu1-mesa:i386 libgstreamer-plugins-bad1.0-0:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv xserver-xorg-video-ati [1:7.3.0-1ubuntu3.1] [xserver-xorg-video-siliconmotion:amd64 libcogl15:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-glamoregl:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 gstreamer1.0-plugins-bad:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 vlc:amd64 xserver-xorg-video-sis:amd64 libqt5gui5:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 libglu1-mesa:i386 libgstreamer-plugins-bad1.0-0:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv xserver-xorg-video-glamoregl [0.6.0-0ubuntu4] [xserver-xorg-video-siliconmotion:amd64 libcogl15:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 gstreamer1.0-plugins-bad:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 vlc:amd64 xserver-xorg-video-sis:amd64 libqt5gui5:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 libglu1-mesa:i386 libgstreamer-plugins-bad1.0-0:amd64 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Inst libegl1-mesa-lts-vivid (10.5.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64]) [xserver-xorg-video-siliconmotion:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 libglu1-mesa:i386 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Inst libllvm3.6 (1:3.6-2ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64]) [xserver-xorg-video-siliconmotion:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 libglu1-mesa:i386 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Inst libglapi-mesa-lts-vivid (10.5.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64]) [xserver-xorg-video-siliconmotion:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-modesetting:amd64 xserver-xorg-video-r128:amd64 libglu1-mesa:i386 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv xserver-xorg-video-modesetting [0.8.1-1build1] [xserver-xorg-video-siliconmotion:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-vesa:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-r128:amd64 libglu1-mesa:i386 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv xserver-xorg-video-vesa [1:2.3.3-1build1] [xserver-xorg-video-siliconmotion:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-trident:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-r128:amd64 libglu1-mesa:i386 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv xserver-xorg-video-trident [1:1.3.6-0ubuntu5] [xserver-xorg-video-siliconmotion:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-tdfx:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-r128:amd64 libglu1-mesa:i386 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv xserver-xorg-video-tdfx [1:1.4.5-1build1] [xserver-xorg-video-siliconmotion:amd64 xserver-xorg-video-sisusb:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-r128:amd64 libglu1-mesa:i386 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv xserver-xorg-video-sisusb [1:0.9.6-2build1] [xserver-xorg-video-siliconmotion:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-sis:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-r128:amd64 libglu1-mesa:i386 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv xserver-xorg-video-sis [1:0.10.7-0ubuntu6] [xserver-xorg-video-siliconmotion:amd64 xserver-xorg-video-savage:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-r128:amd64 libglu1-mesa:i386 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv xserver-xorg-video-siliconmotion [1:1.7.7-2build1] [xserver-xorg-video-savage:amd64 xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-r128:amd64 libglu1-mesa:i386 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv xserver-xorg-video-savage [1:2.3.7-2ubuntu2] [xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-s3:amd64 xserver-xorg-video-r128:amd64 libglu1-mesa:i386 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv xserver-xorg-video-s3 [1:0.6.5-0ubuntu4] [xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 xserver-xorg-video-r128:amd64 libglu1-mesa:i386 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv xserver-xorg-video-r128 [6.9.2-1build1] [xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-qxl:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 libglu1-mesa:i386 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv xserver-xorg-video-qxl [0.1.1-0ubuntu3] [xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-video-openchrome:amd64 xserver-xorg-input-vmmouse:amd64 libglu1-mesa:i386 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv xserver-xorg-video-openchrome [1:0.3.3-1build1] [xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-input-vmmouse:amd64 libglu1-mesa:i386 xserver-xorg-video-mga:amd64 xserver-xorg-video-nouveau:amd64 ]
Remv xserver-xorg-video-nouveau [1:1.0.10-1ubuntu2] [xserver-xorg-video-neomagic:amd64 xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-input-vmmouse:amd64 libglu1-mesa:i386 xserver-xorg-video-mga:amd64 ]
Remv xserver-xorg-video-neomagic [1:1.2.8-1build1] [xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-input-vmmouse:amd64 libglu1-mesa:i386 xserver-xorg-video-mga:amd64 ]
Remv xserver-xorg-video-mga [1:1.6.3-1build1] [xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-mach64:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-input-vmmouse:amd64 libglu1-mesa:i386 ]
Remv xserver-xorg-video-mach64 [6.9.4-1build1] [xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-video-fbdev:amd64 xserver-xorg-input-vmmouse:amd64 libglu1-mesa:i386 ]
Remv xserver-xorg-video-fbdev [1:0.4.4-1build1] [xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-video-cirrus:amd64 xserver-xorg-input-vmmouse:amd64 libglu1-mesa:i386 ]
Remv xserver-xorg-video-cirrus [1:1.5.2-1build1] [xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 xserver-xorg-input-vmmouse:amd64 libglu1-mesa:i386 ]
Remv xserver-xorg-input-vmmouse [1:13.0.0-1build1] [xserver-xorg-input-synaptics:amd64 xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 libglu1-mesa:i386 ]
Remv xserver-xorg-input-synaptics [1.7.4-0ubuntu1] [xserver-xorg-input-evdev:amd64 xserver-xorg-input-mouse:amd64 libglu1-mesa:i386 ]
Remv xserver-xorg-input-mouse [1:1.9.0-1build1] [xserver-xorg-input-evdev:amd64 libglu1-mesa:i386 ]
Remv xserver-xorg-input-evdev [1:2.8.2-1ubuntu2] [libglu1-mesa:i386 ]
Inst libepoxy0 (1.1-1build1 Ubuntu:14.04/trusty-updates [amd64]) [libglu1-mesa:i386 ]
Inst libgbm1-lts-vivid (10.5.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64]) [libglu1-mesa:i386 ]
Inst xserver-xorg-core-lts-vivid (2:1.17.1-0ubuntu3~trusty1 Ubuntu:14.04/trusty-updates [amd64]) [libglu1-mesa:i386 ]
Inst xserver-xorg-video-r128-lts-vivid (6.9.2-1ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64]) [libglu1-mesa:i386 ]
Inst xserver-xorg-video-mach64-lts-vivid (6.9.4-2ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64]) [libglu1-mesa:i386 ]
Inst xserver-xorg-video-radeon-lts-vivid (1:7.5.0-1ubuntu2~trusty1 Ubuntu:14.04/trusty-updates [amd64]) [libglu1-mesa:i386 ]
Inst xserver-xorg-video-ati-lts-vivid (1:7.5.0-1ubuntu2~trusty1 Ubuntu:14.04/trusty-updates [amd64]) [libglu1-mesa:i386 ]
Inst xserver-xorg-video-cirrus-lts-vivid (1:1.5.2-2ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64]) [libglu1-mesa:i386 ]
Inst xserver-xorg-video-fbdev-lts-vivid (1:0.4.4-1build3~trusty1 Ubuntu:14.04/trusty-updates [amd64]) [libglu1-mesa:i386 ]
Inst xserver-xorg-video-intel-lts-vivid (2:2.99.917-1~exp1ubuntu2.2~trusty1 Ubuntu:14.04/trusty-updates [amd64]) [libglu1-mesa:i386 ]
Inst xserver-xorg-video-mga-lts-vivid (1:1.6.3-2ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64]) [libglu1-mesa:i386 ]
Inst xserver-xorg-video-neomagic-lts-vivid (1:1.2.8-1ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64]) [libglu1-mesa:i386 ]
Inst xserver-xorg-video-nouveau-lts-vivid (1:1.0.11-1ubuntu2build1~trusty1 Ubuntu:14.04/trusty-updates [amd64]) [libglu1-mesa:i386 ]
Inst xserver-xorg-video-openchrome-lts-vivid (1:0.3.3-1ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64]) [libglu1-mesa:i386 ]
Inst xserver-xorg-video-savage-lts-vivid (1:2.3.7-2ubuntu4~trusty1 Ubuntu:14.04/trusty-updates [amd64]) [libglu1-mesa:i386 ]
Inst xserver-xorg-video-siliconmotion-lts-vivid (1:1.7.7-2ubuntu2~trusty1 Ubuntu:14.04/trusty-updates [amd64]) [libglu1-mesa:i386 ]
Inst xserver-xorg-video-sisusb-lts-vivid (1:0.9.6-2build3~trusty1 Ubuntu:14.04/trusty-updates [amd64]) [libglu1-mesa:i386 ]
Inst xserver-xorg-video-tdfx-lts-vivid (1:1.4.6-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64]) [libglu1-mesa:i386 ]
Inst xserver-xorg-video-trident-lts-vivid (1:1.3.6-0ubuntu6build1~trusty1 Ubuntu:14.04/trusty-updates [amd64]) [libglu1-mesa:i386 ]
Inst xserver-xorg-video-vesa-lts-vivid (1:2.3.3-1build3~trusty1 Ubuntu:14.04/trusty-updates [amd64]) [libglu1-mesa:i386 ]
Inst libxatracker2-lts-vivid (10.5.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64]) [libglu1-mesa:i386 ]
Inst xserver-xorg-video-vmware-lts-vivid (1:13.1.0-0ubuntu1build1~trusty1 Ubuntu:14.04/trusty-updates [amd64]) [libglu1-mesa:i386 ]
Inst xserver-xorg-video-all-lts-vivid (1:7.7+7ubuntu3~trusty1 Ubuntu:14.04/trusty-updates [amd64]) [libglu1-mesa:i386 ]
Inst libevdev2 (1.0.99.2+dfsg-2ubuntu2 Ubuntu:14.04/trusty [amd64]) [libglu1-mesa:i386 ]
Inst xserver-xorg-input-evdev-lts-vivid (1:2.9.0-1ubuntu2~trusty1 Ubuntu:14.04/trusty-updates [amd64]) [libglu1-mesa:i386 ]
Inst xserver-xorg-input-mouse-lts-vivid (1:1.9.1-1~trusty1 Ubuntu:14.04/trusty-updates [amd64]) [libglu1-mesa:i386 ]
Inst xserver-xorg-input-vmmouse-lts-vivid (1:13.0.0-1ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64]) [libglu1-mesa:i386 ]
Inst xserver-xorg-input-synaptics-lts-vivid (1.8.1-1ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64]) [libglu1-mesa:i386 ]
Inst xserver-xorg-input-wacom-lts-vivid (1:0.25.0-0ubuntu1.1~trusty1 Ubuntu:14.04/trusty-updates [amd64]) [libglu1-mesa:i386 ]
Inst xserver-xorg-input-all-lts-vivid (1:7.7+7ubuntu3~trusty1 Ubuntu:14.04/trusty-updates [amd64]) [libglu1-mesa:i386 ]
Remv wine1.6-i386:i386 [1:1.6.2-0ubuntu4] [wine1.6:amd64 libglu1-mesa:i386 ]
Remv wine1.6 [1:1.6.2-0ubuntu4] [wine1.6-amd64:amd64 libglu1-mesa:i386 ]
Remv wine1.6-amd64 [1:1.6.2-0ubuntu4] [libglu1-mesa:i386 ]
Remv libglu1-mesa:i386 [9.0.0-2]
Inst libwayland-egl1-mesa-lts-vivid (10.5.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Inst linux-image-3.19.0-25-generic (3.19.0-25.26~14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Inst linux-image-extra-3.19.0-25-generic (3.19.0-25.26~14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Inst linux-image-generic-lts-vivid (3.19.0.25.12 Ubuntu:14.04/trusty-updates [amd64])
Inst linux-headers-3.19.0-25 (3.19.0-25.26~14.04.1 Ubuntu:14.04/trusty-updates [all])
Inst linux-headers-3.19.0-25-generic (3.19.0-25.26~14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Inst linux-headers-generic-lts-vivid (3.19.0.25.12 Ubuntu:14.04/trusty-updates [amd64])
Inst linux-generic-lts-vivid (3.19.0.25.12 Ubuntu:14.04/trusty-updates [amd64])
Inst thermald (1.4.3-2~14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libllvm3.6 (1:3.6-2ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf libgl1-mesa-dri-lts-vivid (10.5.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf libglapi-mesa-lts-vivid (10.5.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf libgl1-mesa-glx-lts-vivid (10.5.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf libgles1-mesa-lts-vivid (10.5.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf libgles2-mesa-lts-vivid (10.5.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf libgbm1-lts-vivid (10.5.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf libegl1-mesa-lts-vivid (10.5.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf libepoxy0 (1.1-1build1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-core-lts-vivid (2:1.17.1-0ubuntu3~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-r128-lts-vivid (6.9.2-1ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-mach64-lts-vivid (6.9.4-2ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-radeon-lts-vivid (1:7.5.0-1ubuntu2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-ati-lts-vivid (1:7.5.0-1ubuntu2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-cirrus-lts-vivid (1:1.5.2-2ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-fbdev-lts-vivid (1:0.4.4-1build3~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-intel-lts-vivid (2:2.99.917-1~exp1ubuntu2.2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-mga-lts-vivid (1:1.6.3-2ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-neomagic-lts-vivid (1:1.2.8-1ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-nouveau-lts-vivid (1:1.0.11-1ubuntu2build1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-openchrome-lts-vivid (1:0.3.3-1ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-savage-lts-vivid (1:2.3.7-2ubuntu4~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-siliconmotion-lts-vivid (1:1.7.7-2ubuntu2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-sisusb-lts-vivid (1:0.9.6-2build3~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-tdfx-lts-vivid (1:1.4.6-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-trident-lts-vivid (1:1.3.6-0ubuntu6build1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-vesa-lts-vivid (1:2.3.3-1build3~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf libxatracker2-lts-vivid (10.5.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-vmware-lts-vivid (1:13.1.0-0ubuntu1build1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-video-all-lts-vivid (1:7.7+7ubuntu3~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf libevdev2 (1.0.99.2+dfsg-2ubuntu2 Ubuntu:14.04/trusty [amd64])
Conf xserver-xorg-input-evdev-lts-vivid (1:2.9.0-1ubuntu2~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-input-mouse-lts-vivid (1:1.9.1-1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-input-vmmouse-lts-vivid (1:13.0.0-1ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-input-synaptics-lts-vivid (1.8.1-1ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-input-wacom-lts-vivid (1:0.25.0-0ubuntu1.1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-input-all-lts-vivid (1:7.7+7ubuntu3~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf xserver-xorg-lts-vivid (1:7.7+7ubuntu3~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf libwayland-egl1-mesa-lts-vivid (10.5.2-0ubuntu1~trusty1 Ubuntu:14.04/trusty-updates [amd64])
Conf linux-image-3.19.0-25-generic (3.19.0-25.26~14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf linux-image-extra-3.19.0-25-generic (3.19.0-25.26~14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf linux-image-generic-lts-vivid (3.19.0.25.12 Ubuntu:14.04/trusty-updates [amd64])
Conf linux-headers-3.19.0-25 (3.19.0-25.26~14.04.1 Ubuntu:14.04/trusty-updates [all])
Conf linux-headers-3.19.0-25-generic (3.19.0-25.26~14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf linux-headers-generic-lts-vivid (3.19.0.25.12 Ubuntu:14.04/trusty-updates [amd64])
Conf linux-generic-lts-vivid (3.19.0.25.12 Ubuntu:14.04/trusty-updates [amd64])
Conf thermald (1.4.3-2~14.04.1 Ubuntu:14.04/trusty-updates [amd64])
K53U:~$ sudo apt-get install --install-recommends linux-generic-lts-vivid xserver-xorg-core-lts-vivid xserver-xorg-lts-vivid xserver-xorg-video-all-lts-vivid xserver-xorg-input-all-lts-vivid libwayland-egl1-mesa-lts-vivid
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fonts-horai-umefont gnome-exe-thumbnailer libasn1-8-heimdal:i386
  libaudio2:i386 libavahi-client3:i386 libavahi-common-data:i386
  libavahi-common3:i386 libcapi20-3 libcapi20-3:i386 libcups2:i386
  libdbusmenu-qt2:i386 libdrm-intel1:i386 libdrm-nouveau2:i386
  libdrm-radeon1:i386 libelf1:i386 libexif12:i386 libexpat1:i386 libffi6:i386
  libfontconfig1:i386 libgcrypt11:i386 libgd3:i386 libgif4:i386
  libglib2.0-0:i386 libgnutls26:i386 libgpg-error0:i386 libgphoto2-6:i386
  libgphoto2-port10:i386 libgssapi-krb5-2:i386 libgssapi3-heimdal:i386
  libgstreamer-plugins-base0.10-0:i386 libgstreamer-plugins-base1.0-0:i386
  libgstreamer0.10-0:i386 libgstreamer1.0-0:i386 libhcrypto4-heimdal:i386
  libheimbase1-heimdal:i386 libheimntlm0-heimdal:i386 libhx509-5-heimdal:i386
  libieee1284-3:i386 libjbig0:i386 libjpeg-turbo8:i386 libjpeg8:i386
  libk5crypto3:i386 libkeyutils1:i386 libkrb5-26-heimdal:i386 libkrb5-3:i386
  libkrb5support0:i386 liblcms2-2:i386 libldap-2.4-2:i386 libllvm3.4:i386
  libltdl7:i386 libmpg123-0:i386 libmysqlclient18:i386 libodbc1
  libopenal1:i386 liborc-0.4-0:i386 libp11-kit-gnome-keyring:i386
  libp11-kit0:i386 libpciaccess0:i386 libqt4-dbus:i386 libqt4-declarative:i386
  libqt4-network:i386 libqt4-script:i386 libqt4-sql:i386 libqt4-sql-mysql:i386
  libqt4-xml:i386 libqt4-xmlpatterns:i386 libqtcore4:i386 libqtdbus4:i386
  libqtgui4:i386 libroken18-heimdal:i386 libsane:i386 libsasl2-2:i386
  libsasl2-modules:i386 libsasl2-modules-db:i386 libsqlite3-0:i386
  libssl1.0.0:i386 libtasn1-6:i386 libtiff5:i386 libtxc-dxtn-s2tc0:i386
  libusb-1.0-0:i386 libv4l-0:i386 libv4lconvert0:i386 libvpx1:i386
  libwind0-heimdal:i386 libx11-xcb1:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386
  libxcb-glx0:i386 libxcb-present0:i386 libxcb-sync1:i386 libxcomposite1:i386
  libxcursor1:i386 libxi6:i386 libxinerama1:i386 libxml2:i386 libxpm4:i386
  libxshmfence1:i386 libxslt1.1:i386 libxss1:i386 libxv1:i386 libxxf86vm1:i386
  mysql-common ocl-icd-libopencl1:i386 odbcinst odbcinst1debian2
  p11-kit-modules:i386 p7zip sni-qt:i386 unixodbc wine-gecko2.21
  wine-gecko2.21:i386 wine-mono0.0.8 winetricks
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libegl1-mesa-lts-vivid libepoxy0 libevdev2 libgbm1-lts-vivid
  libgl1-mesa-dri-lts-vivid libgl1-mesa-glx-lts-vivid libglapi-mesa-lts-vivid
  libgles1-mesa-lts-vivid libgles2-mesa-lts-vivid libllvm3.6
  libxatracker2-lts-vivid linux-headers-3.19.0-25
  linux-headers-3.19.0-25-generic linux-headers-generic-lts-vivid
  linux-image-3.19.0-25-generic linux-image-extra-3.19.0-25-generic
  linux-image-generic-lts-vivid thermald xserver-xorg-input-evdev-lts-vivid
  xserver-xorg-input-mouse-lts-vivid xserver-xorg-input-synaptics-lts-vivid
  xserver-xorg-input-vmmouse-lts-vivid xserver-xorg-input-wacom-lts-vivid
  xserver-xorg-video-ati-lts-vivid xserver-xorg-video-cirrus-lts-vivid
  xserver-xorg-video-fbdev-lts-vivid xserver-xorg-video-intel-lts-vivid
  xserver-xorg-video-mach64-lts-vivid xserver-xorg-video-mga-lts-vivid
  xserver-xorg-video-neomagic-lts-vivid xserver-xorg-video-nouveau-lts-vivid
  xserver-xorg-video-openchrome-lts-vivid xserver-xorg-video-r128-lts-vivid
  xserver-xorg-video-radeon-lts-vivid xserver-xorg-video-savage-lts-vivid
  xserver-xorg-video-siliconmotion-lts-vivid
  xserver-xorg-video-sisusb-lts-vivid xserver-xorg-video-tdfx-lts-vivid
  xserver-xorg-video-trident-lts-vivid xserver-xorg-video-vesa-lts-vivid
  xserver-xorg-video-vmware-lts-vivid
Suggested packages:
  fdutils linux-lts-vivid-tools xfonts-100dpi xfonts-75dpi
  gpointing-device-settings touchfreeze firmware-linux
Recommended packages:
  libegl1-mesa-drivers-lts-vivid
The following packages will be REMOVED
  libegl1-mesa libegl1-mesa-drivers libgl1-mesa-dri libgl1-mesa-dri:i386
  libgl1-mesa-glx libgl1-mesa-glx:i386 libglapi-mesa libglapi-mesa:i386
  libgles1-mesa libgles2-mesa libglu1-mesa:i386 libopenvg1-mesa libosmesa6
  libosmesa6:i386 libqt4-opengl:i386 libqtwebkit4:i386 libwayland-egl1-mesa
  libxatracker2 skype skype-bin:i386 wine1.6 wine1.6-amd64 wine1.6-i386:i386
  xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-ati
  xserver-xorg-video-cirrus xserver-xorg-video-fbdev
  xserver-xorg-video-glamoregl xserver-xorg-video-intel
  xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-modesetting xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-openchrome
  xserver-xorg-video-qxl xserver-xorg-video-r128 xserver-xorg-video-radeon
  xserver-xorg-video-s3 xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-vesa xserver-xorg-video-vmware
The following NEW packages will be installed
  libegl1-mesa-lts-vivid libepoxy0 libevdev2 libgbm1-lts-vivid
  libgl1-mesa-dri-lts-vivid libgl1-mesa-glx-lts-vivid libglapi-mesa-lts-vivid
  libgles1-mesa-lts-vivid libgles2-mesa-lts-vivid libllvm3.6
  libwayland-egl1-mesa-lts-vivid libxatracker2-lts-vivid
  linux-generic-lts-vivid linux-headers-3.19.0-25
  linux-headers-3.19.0-25-generic linux-headers-generic-lts-vivid
  linux-image-3.19.0-25-generic linux-image-extra-3.19.0-25-generic
  linux-image-generic-lts-vivid thermald xserver-xorg-core-lts-vivid
  xserver-xorg-input-all-lts-vivid xserver-xorg-input-evdev-lts-vivid
  xserver-xorg-input-mouse-lts-vivid xserver-xorg-input-synaptics-lts-vivid
  xserver-xorg-input-vmmouse-lts-vivid xserver-xorg-input-wacom-lts-vivid
  xserver-xorg-lts-vivid xserver-xorg-video-all-lts-vivid
  xserver-xorg-video-ati-lts-vivid xserver-xorg-video-cirrus-lts-vivid
  xserver-xorg-video-fbdev-lts-vivid xserver-xorg-video-intel-lts-vivid
  xserver-xorg-video-mach64-lts-vivid xserver-xorg-video-mga-lts-vivid
  xserver-xorg-video-neomagic-lts-vivid xserver-xorg-video-nouveau-lts-vivid
  xserver-xorg-video-openchrome-lts-vivid xserver-xorg-video-r128-lts-vivid
  xserver-xorg-video-radeon-lts-vivid xserver-xorg-video-savage-lts-vivid
  xserver-xorg-video-siliconmotion-lts-vivid
  xserver-xorg-video-sisusb-lts-vivid xserver-xorg-video-tdfx-lts-vivid
  xserver-xorg-video-trident-lts-vivid xserver-xorg-video-vesa-lts-vivid
  xserver-xorg-video-vmware-lts-vivid
0 to upgrade, 47 to newly install, 55 to remove and 29 not to upgrade.
Need to get 80.9 MB of archives.
After this operation, 69.6 MB disk space will be freed.
Do you want to continue? [Y/n] y
Err http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main libgl1-mesa-dri-lts-vivid amd64 10.5.2-0ubuntu1~trusty1
  Could not resolve 'in.archive.ubuntu.com'
Err http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main libgl1-mesa-glx-lts-vivid amd64 10.5.2-0ubuntu1~trusty1
  Could not resolve 'in.archive.ubuntu.com'
Err http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main libgles1-mesa-lts-vivid amd64 10.5.2-0ubuntu1~trusty1
  Could not resolve 'in.archive.ubuntu.com'
Err http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main libgles2-mesa-lts-vivid amd64 10.5.2-0ubuntu1~trusty1
  Could not resolve 'in.archive.ubuntu.com'
Err http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main xserver-xorg-lts-vivid amd64 1:7.7+7ubuntu3~trusty1
  Could not resolve 'in.archive.ubuntu.com'
Err http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main libegl1-mesa-lts-vivid amd64 10.5.2-0ubuntu1~trusty1
  Could not resolve 'in.archive.ubuntu.com'
Err http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main libllvm3.6 amd64 1:3.6-2ubuntu1~trusty1
  Could not resolve 'in.archive.ubuntu.com'
Err http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main libglapi-mesa-lts-vivid amd64 10.5.2-0ubuntu1~trusty1
  Could not resolve 'in.archive.ubuntu.com'
Err http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main libepoxy0 amd64 1.1-1build1
  Could not resolve 'in.archive.ubuntu.com'
Err http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main libgbm1-lts-vivid amd64 10.5.2-0ubuntu1~trusty1
  Could not resolve 'in.archive.ubuntu.com'
Err http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main xserver-xorg-core-lts-vivid amd64 2:1.17.1-0ubuntu3~trusty1
  Could not resolve 'in.archive.ubuntu.com'
Err http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main xserver-xorg-video-r128-lts-vivid amd64 6.9.2-1ubuntu1~trusty1
  Could not resolve 'in.archive.ubuntu.com'
Err http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main xserver-xorg-video-mach64-lts-vivid amd64 6.9.4-2ubuntu1~trusty1
  Could not resolve 'in.archive.ubuntu.com'
Err http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main xserver-xorg-video-radeon-lts-vivid amd64 1:7.5.0-1ubuntu2~trusty1
  Could not resolve 'in.archive.ubuntu.com'
Err http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main xserver-xorg-video-ati-lts-vivid amd64 1:7.5.0-1ubuntu2~trusty1
  Could not resolve 'in.archive.ubuntu.com'
Err http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main xserver-xorg-video-cirrus-lts-vivid amd64 1:1.5.2-2ubuntu1~trusty1
  Could not resolve 'in.archive.ubuntu.com'
Err http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main xserver-xorg-video-fbdev-lts-vivid amd64 1:0.4.4-1build3~trusty1
  Could not resolve 'in.archive.ubuntu.com'
Err http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main xserver-xorg-video-intel-lts-vivid amd64 2:2.99.917-1~exp1ubuntu2.2~trusty1
  Could not resolve 'in.archive.ubuntu.com'
Err http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main xserver-xorg-video-mga-lts-vivid amd64 1:1.6.3-2ubuntu1~trusty1
  Could not resolve 'in.archive.ubuntu.com'
Err http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main xserver-xorg-video-neomagic-lts-vivid amd64 1:1.2.8-1ubuntu1~trusty1
  Could not resolve 'in.archive.ubuntu.com'
Err http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main xserver-xorg-video-nouveau-lts-vivid amd64 1:1.0.11-1ubuntu2build1~trusty1
  Could not resolve 'in.archive.ubuntu.com'
Err http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main xserver-xorg-video-openchrome-lts-vivid amd64 1:0.3.3-1ubuntu1~trusty1
  Could not resolve 'in.archive.ubuntu.com'
Err http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main xserver-xorg-video-savage-lts-vivid amd64 1:2.3.7-2ubuntu4~trusty1
  Could not resolve 'in.archive.ubuntu.com'
Err http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main xserver-xorg-video-siliconmotion-lts-vivid amd64 1:1.7.7-2ubuntu2~trusty1
  Could not resolve 'in.archive.ubuntu.com'
Err http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main xserver-xorg-video-sisusb-lts-vivid amd64 1:0.9.6-2build3~trusty1
  Could not resolve 'in.archive.ubuntu.com'
Err http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main xserver-xorg-video-tdfx-lts-vivid amd64 1:1.4.6-0ubuntu1~trusty1
  Could not resolve 'in.archive.ubuntu.com'
Err http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main xserver-xorg-video-trident-lts-vivid amd64 1:1.3.6-0ubuntu6build1~trusty1
  Could not resolve 'in.archive.ubuntu.com'
Err http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main xserver-xorg-video-vesa-lts-vivid amd64 1:2.3.3-1build3~trusty1
  Could not resolve 'in.archive.ubuntu.com'
Err http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main libxatracker2-lts-vivid amd64 10.5.2-0ubuntu1~trusty1
  Could not resolve 'in.archive.ubuntu.com'
Err http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main xserver-xorg-video-vmware-lts-vivid amd64 1:13.1.0-0ubuntu1build1~trusty1
  Could not resolve 'in.archive.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ trusty-security/main libepoxy0 amd64 1.1-1build1
  Could not resolve 'security.ubuntu.com'
Err http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main xserver-xorg-video-all-lts-vivid amd64 1:7.7+7ubuntu3~trusty1
  Could not resolve 'in.archive.ubuntu.com'
Err http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main xserver-xorg-input-evdev-lts-vivid amd64 1:2.9.0-1ubuntu2~trusty1
  Could not resolve 'in.archive.ubuntu.com'
Err http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main xserver-xorg-input-mouse-lts-vivid amd64 1:1.9.1-1~trusty1
  Could not resolve 'in.archive.ubuntu.com'
Err http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main xserver-xorg-input-vmmouse-lts-vivid amd64 1:13.0.0-1ubuntu1~trusty1
  Could not resolve 'in.archive.ubuntu.com'
Err http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main xserver-xorg-input-synaptics-lts-vivid amd64 1.8.1-1ubuntu1~trusty1
  Could not resolve 'in.archive.ubuntu.com'
Err http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main xserver-xorg-input-wacom-lts-vivid amd64 1:0.25.0-0ubuntu1.1~trusty1
  Could not resolve 'in.archive.ubuntu.com'
Err http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main xserver-xorg-input-all-lts-vivid amd64 1:7.7+7ubuntu3~trusty1
  Could not resolve 'in.archive.ubuntu.com'
Err http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main libwayland-egl1-mesa-lts-vivid amd64 10.5.2-0ubuntu1~trusty1
  Could not resolve 'in.archive.ubuntu.com'
Err http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-image-3.19.0-25-generic amd64 3.19.0-25.26~14.04.1
  Could not resolve 'in.archive.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ trusty-security/main linux-image-3.19.0-25-generic amd64 3.19.0-25.26~14.04.1
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ trusty-security/main linux-image-extra-3.19.0-25-generic amd64 3.19.0-25.26~14.04.1
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ trusty-security/main linux-image-generic-lts-vivid amd64 3.19.0.25.12
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ trusty-security/main linux-headers-3.19.0-25 all 3.19.0-25.26~14.04.1
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ trusty-security/main linux-headers-3.19.0-25-generic amd64 3.19.0-25.26~14.04.1
  Could not resolve 'security.ubuntu.com'
Err http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-headers-generic-lts-vivid amd64 3.19.0.25.12
  Could not resolve 'in.archive.ubuntu.com'
Err http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main thermald amd64 1.4.3-2~14.04.1
  Could not resolve 'in.archive.ubuntu.com'
Err http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main libevdev2 amd64 1.0.99.2+dfsg-2ubuntu2
  Could not resolve 'in.archive.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ trusty-security/main linux-headers-generic-lts-vivid amd64 3.19.0.25.12
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ trusty-security/main linux-generic-lts-vivid amd64 3.19.0.25.12
  Could not resolve 'security.ubuntu.com'
E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/m/mesa-lts-vivid/libgl1-mesa-dri-lts-vivid_10.5.2-0ubuntu1~trusty1_amd64.deb  Could not resolve 'in.archive.ubuntu.com'

E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/m/mesa-lts-vivid/libgl1-mesa-glx-lts-vivid_10.5.2-0ubuntu1~trusty1_amd64.deb  Could not resolve 'in.archive.ubuntu.com'

E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/m/mesa-lts-vivid/libgles1-mesa-lts-vivid_10.5.2-0ubuntu1~trusty1_amd64.deb  Could not resolve 'in.archive.ubuntu.com'

E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/m/mesa-lts-vivid/libgles2-mesa-lts-vivid_10.5.2-0ubuntu1~trusty1_amd64.deb  Could not resolve 'in.archive.ubuntu.com'

E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/x/xorg-lts-vivid/xserver-xorg-lts-vivid_7.7+7ubuntu3~trusty1_amd64.deb  Could not resolve 'in.archive.ubuntu.com'

E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/m/mesa-lts-vivid/libegl1-mesa-lts-vivid_10.5.2-0ubuntu1~trusty1_amd64.deb  Could not resolve 'in.archive.ubuntu.com'

E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/l/llvm-toolchain-3.6/libllvm3.6_3.6-2ubuntu1~trusty1_amd64.deb  Could not resolve 'in.archive.ubuntu.com'

E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/m/mesa-lts-vivid/libglapi-mesa-lts-vivid_10.5.2-0ubuntu1~trusty1_amd64.deb  Could not resolve 'in.archive.ubuntu.com'

E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/libe/libepoxy/libepoxy0_1.1-1build1_amd64.deb  Could not resolve 'security.ubuntu.com'

E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/m/mesa-lts-vivid/libgbm1-lts-vivid_10.5.2-0ubuntu1~trusty1_amd64.deb  Could not resolve 'in.archive.ubuntu.com'

E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/x/xorg-server-lts-vivid/xserver-xorg-core-lts-vivid_1.17.1-0ubuntu3~trusty1_amd64.deb  Could not resolve 'in.archive.ubuntu.com'

E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-r128-lts-vivid/xserver-xorg-video-r128-lts-vivid_6.9.2-1ubuntu1~trusty1_amd64.deb  Could not resolve 'in.archive.ubuntu.com'

E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-mach64-lts-vivid/xserver-xorg-video-mach64-lts-vivid_6.9.4-2ubuntu1~trusty1_amd64.deb  Could not resolve 'in.archive.ubuntu.com'

E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-ati-lts-vivid/xserver-xorg-video-radeon-lts-vivid_7.5.0-1ubuntu2~trusty1_amd64.deb  Could not resolve 'in.archive.ubuntu.com'

E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-ati-lts-vivid/xserver-xorg-video-ati-lts-vivid_7.5.0-1ubuntu2~trusty1_amd64.deb  Could not resolve 'in.archive.ubuntu.com'

E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-cirrus-lts-vivid/xserver-xorg-video-cirrus-lts-vivid_1.5.2-2ubuntu1~trusty1_amd64.deb  Could not resolve 'in.archive.ubuntu.com'

E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-fbdev-lts-vivid/xserver-xorg-video-fbdev-lts-vivid_0.4.4-1build3~trusty1_amd64.deb  Could not resolve 'in.archive.ubuntu.com'

E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-intel-lts-vivid/xserver-xorg-video-intel-lts-vivid_2.99.917-1~exp1ubuntu2.2~trusty1_amd64.deb  Could not resolve 'in.archive.ubuntu.com'

E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-mga-lts-vivid/xserver-xorg-video-mga-lts-vivid_1.6.3-2ubuntu1~trusty1_amd64.deb  Could not resolve 'in.archive.ubuntu.com'

E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-neomagic-lts-vivid/xserver-xorg-video-neomagic-lts-vivid_1.2.8-1ubuntu1~trusty1_amd64.deb  Could not resolve 'in.archive.ubuntu.com'

E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-nouveau-lts-vivid/xserver-xorg-video-nouveau-lts-vivid_1.0.11-1ubuntu2build1~trusty1_amd64.deb  Could not resolve 'in.archive.ubuntu.com'

E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-openchrome-lts-vivid/xserver-xorg-video-openchrome-lts-vivid_0.3.3-1ubuntu1~trusty1_amd64.deb  Could not resolve 'in.archive.ubuntu.com'

E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-savage-lts-vivid/xserver-xorg-video-savage-lts-vivid_2.3.7-2ubuntu4~trusty1_amd64.deb  Could not resolve 'in.archive.ubuntu.com'

E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-siliconmotion-lts-vivid/xserver-xorg-video-siliconmotion-lts-vivid_1.7.7-2ubuntu2~trusty1_amd64.deb  Could not resolve 'in.archive.ubuntu.com'

E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-sisusb-lts-vivid/xserver-xorg-video-sisusb-lts-vivid_0.9.6-2build3~trusty1_amd64.deb  Could not resolve 'in.archive.ubuntu.com'

E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-tdfx-lts-vivid/xserver-xorg-video-tdfx-lts-vivid_1.4.6-0ubuntu1~trusty1_amd64.deb  Could not resolve 'in.archive.ubuntu.com'

E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-trident-lts-vivid/xserver-xorg-video-trident-lts-vivid_1.3.6-0ubuntu6build1~trusty1_amd64.deb  Could not resolve 'in.archive.ubuntu.com'

E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-vesa-lts-vivid/xserver-xorg-video-vesa-lts-vivid_2.3.3-1build3~trusty1_amd64.deb  Could not resolve 'in.archive.ubuntu.com'

E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/m/mesa-lts-vivid/libxatracker2-lts-vivid_10.5.2-0ubuntu1~trusty1_amd64.deb  Could not resolve 'in.archive.ubuntu.com'

E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-vmware-lts-vivid/xserver-xorg-video-vmware-lts-vivid_13.1.0-0ubuntu1build1~trusty1_amd64.deb  Could not resolve 'in.archive.ubuntu.com'

E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/x/xorg-lts-vivid/xserver-xorg-video-all-lts-vivid_7.7+7ubuntu3~trusty1_amd64.deb  Could not resolve 'in.archive.ubuntu.com'

E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/libe/libevdev/libevdev2_1.0.99.2+dfsg-2ubuntu2_amd64.deb  Could not resolve 'in.archive.ubuntu.com'

E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-input-evdev-lts-vivid/xserver-xorg-input-evdev-lts-vivid_2.9.0-1ubuntu2~trusty1_amd64.deb  Could not resolve 'in.archive.ubuntu.com'

E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-input-mouse-lts-vivid/xserver-xorg-input-mouse-lts-vivid_1.9.1-1~trusty1_amd64.deb  Could not resolve 'in.archive.ubuntu.com'

E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-input-vmmouse-lts-vivid/xserver-xorg-input-vmmouse-lts-vivid_13.0.0-1ubuntu1~trusty1_amd64.deb  Could not resolve 'in.archive.ubuntu.com'

E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-input-synaptics-lts-vivid/xserver-xorg-input-synaptics-lts-vivid_1.8.1-1ubuntu1~trusty1_amd64.deb  Could not resolve 'in.archive.ubuntu.com'

E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/x/xf86-input-wacom-lts-vivid/xserver-xorg-input-wacom-lts-vivid_0.25.0-0ubuntu1.1~trusty1_amd64.deb  Could not resolve 'in.archive.ubuntu.com'

E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/x/xorg-lts-vivid/xserver-xorg-input-all-lts-vivid_7.7+7ubuntu3~trusty1_amd64.deb  Could not resolve 'in.archive.ubuntu.com'

E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/m/mesa-lts-vivid/libwayland-egl1-mesa-lts-vivid_10.5.2-0ubuntu1~trusty1_amd64.deb  Could not resolve 'in.archive.ubuntu.com'

E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux-lts-vivid/linux-image-3.19.0-25-generic_3.19.0-25.26~14.04.1_amd64.deb  Could not resolve 'security.ubuntu.com'

E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux-lts-vivid/linux-image-extra-3.19.0-25-generic_3.19.0-25.26~14.04.1_amd64.deb  Could not resolve 'security.ubuntu.com'

E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta-lts-vivid/linux-image-generic-lts-vivid_3.19.0.25.12_amd64.deb  Could not resolve 'security.ubuntu.com'

E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux-lts-vivid/linux-headers-3.19.0-25_3.19.0-25.26~14.04.1_all.deb  Could not resolve 'security.ubuntu.com'

E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux-lts-vivid/linux-headers-3.19.0-25-generic_3.19.0-25.26~14.04.1_amd64.deb  Could not resolve 'security.ubuntu.com'

E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta-lts-vivid/linux-headers-generic-lts-vivid_3.19.0.25.12_amd64.deb  Could not resolve 'security.ubuntu.com'

E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta-lts-vivid/linux-generic-lts-vivid_3.19.0.25.12_amd64.deb  Could not resolve 'security.ubuntu.com'

E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/t/thermald/thermald_1.4.3-2~14.04.1_amd64.deb  Could not resolve 'in.archive.ubuntu.com'

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
K53U:~$ sudo apt-get install linux-signed-generic-lts-vividReading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-headers-3.19.0-25 linux-headers-3.19.0-25-generic
  linux-headers-generic-lts-vivid linux-image-3.19.0-25-generic
  linux-image-extra-3.19.0-25-generic linux-signed-image-3.19.0-25-generic
  linux-signed-image-generic-lts-vivid sbsigntool thermald
Suggested packages:
  fdutils linux-lts-vivid-tools
The following NEW packages will be installed
  linux-headers-3.19.0-25 linux-headers-3.19.0-25-generic
  linux-headers-generic-lts-vivid linux-image-3.19.0-25-generic
  linux-image-extra-3.19.0-25-generic linux-signed-generic-lts-vivid
  linux-signed-image-3.19.0-25-generic linux-signed-image-generic-lts-vivid
  sbsigntool thermald
0 to upgrade, 10 to newly install, 0 to remove and 29 not to upgrade.
Need to get 65.3 MB of archives.
After this operation, 289 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Err http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-image-3.19.0-25-generic amd64 3.19.0-25.26~14.04.1
  Could not resolve 'in.archive.ubuntu.com'
Err http://in.archive.ubuntu.com/ubuntu/ trusty/main sbsigntool amd64 0.6-0ubuntu7
  Could not resolve 'in.archive.ubuntu.com'
Err http://in.archive.ubuntu.com/ubuntu/ trusty-updates/main thermald amd64 1.4.3-2~14.04.1
  Could not resolve 'in.archive.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ trusty-security/main linux-image-3.19.0-25-generic amd64 3.19.0-25.26~14.04.1
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ trusty-security/main linux-headers-3.19.0-25 all 3.19.0-25.26~14.04.1
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ trusty-security/main linux-headers-3.19.0-25-generic amd64 3.19.0-25.26~14.04.1
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ trusty-security/main linux-headers-generic-lts-vivid amd64 3.19.0.25.12
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ trusty-security/main linux-image-extra-3.19.0-25-generic amd64 3.19.0-25.26~14.04.1
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ trusty-security/main linux-signed-image-3.19.0-25-generic amd64 3.19.0-25.26~14.04.1
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ trusty-security/main linux-signed-image-generic-lts-vivid amd64 3.19.0.25.12
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ trusty-security/main linux-signed-generic-lts-vivid amd64 3.19.0.25.12
  Could not resolve 'security.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux-lts-vivid/linux-image-3.19.0-25-generic_3.19.0-25.26~14.04.1_amd64.deb  Could not resolve 'security.ubuntu.com'

E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux-lts-vivid/linux-headers-3.19.0-25_3.19.0-25.26~14.04.1_all.deb  Could not resolve 'security.ubuntu.com'

E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux-lts-vivid/linux-headers-3.19.0-25-generic_3.19.0-25.26~14.04.1_amd64.deb  Could not resolve 'security.ubuntu.com'

E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta-lts-vivid/linux-headers-generic-lts-vivid_3.19.0.25.12_amd64.deb  Could not resolve 'security.ubuntu.com'

E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux-lts-vivid/linux-image-extra-3.19.0-25-generic_3.19.0-25.26~14.04.1_amd64.deb  Could not resolve 'security.ubuntu.com'

E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/s/sbsigntool/sbsigntool_0.6-0ubuntu7_amd64.deb  Could not resolve 'in.archive.ubuntu.com'

E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux-signed-lts-vivid/linux-signed-image-3.19.0-25-generic_3.19.0-25.26~14.04.1_amd64.deb  Could not resolve 'security.ubuntu.com'

E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta-lts-vivid/linux-signed-image-generic-lts-vivid_3.19.0.25.12_amd64.deb  Could not resolve 'security.ubuntu.com'

E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta-lts-vivid/linux-signed-generic-lts-vivid_3.19.0.25.12_amd64.deb  Could not resolve 'security.ubuntu.com'

E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/t/thermald/thermald_1.4.3-2~14.04.1_amd64.deb  Could not resolve 'in.archive.ubuntu.com'

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
K53U:~$ sudo dpkg-reconfigure xserver-xorg-lts-vividdpkg-query: package 'xserver-xorg-lts-vivid' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xserver-xorg-lts-vivid is not installed.


```

---

### Post by praseodym on 2015-11-08
Obviously, you have no internet connection at all?! Please try Ubuntu 14.04.3:

64bit:
[http://ftp.halifax.rwth-aachen.de/ubuntu-releases/14.04.3/ubuntu-14.04.3-desktop-amd64.iso](http://ftp.halifax.rwth-aachen.de/ubuntu-releases/14.04.3/ubuntu-14.04.3-desktop-amd64.iso)

---

### Post by eruptionjoojo on 2015-11-09
thanks again ......... thats gonno take some time because this USB data card internet access thing is really expensive, so would have to look out for fixed line connection to download the setup .............. anyhow, really appreciate your gesture for trying to help.

---

### Post by eruptionjoojo on 2015-11-16
Can I try installing the Network Manager again - ? would that help ?

---

