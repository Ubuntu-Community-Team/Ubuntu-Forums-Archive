---
title: "huawei e173 modem"
date: 2015-10-29
forum: Networking &amp; Wireless
---

### Post by ronb19495 on 2015-10-29
my e173 huawei usb modem will not connect on ubuntu 15.10 it is recognized in lsusb usb_modeswitch.d/12d1:1436 I have had it connect 2 timed then nothing sometimes is switches to modem mode but still wont connect
any help please

I cant work this out this morning my usb stick is connecting to the internet but when I look in lsusb usb stick is not in modem mode
```
grumpy@grumpy-desktop:~$ lsusb
Bus 006 Device 002: ID 8087:8001 Intel Corp. 
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 8087:8009 Intel Corp. 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 0451:8041 Texas Instruments, Inc. 
Bus 002 Device 002: ID 2109:0812 VIA Labs, Inc. VL812 Hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 008: ID 046d:0a1f Logitech, Inc. G930
Bus 001 Device 007: ID 046d:0809 Logitech, Inc. Webcam Pro 9000
Bus 001 Device 006: ID 0451:8043 Texas Instruments, Inc. 
Bus 001 Device 005: ID 046d:c526 Logitech, Inc. Nano Receiver
Bus 001 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 2109:2812 VIA Labs, Inc. VL812 Hub
Bus 001 Device 003: ID 12d1:1436 Huawei Technologies Co., Ltd. Broadband stick
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
does any one hava any idea whats going on here

---

### Post by ronb19495 on 2015-11-01
Here is the output of that code you sent me
 ```
 	 	 	 	   grumpy@grumpy-desktop:~$ sudo mmcli -m 0 | grep -Ev "imei|equipment|Numbers"
 [sudo] password for grumpy:  
 
 
 /org/freedesktop/ModemManager1/Modem/0 (device id 'c640d505eba92313212c61778d8a0c69ffd7c3b1')
   -------------------------
   Hardware |   manufacturer: 'huawei'
            |          model: 'E173'
            |       revision: '11.126.16.05.895'
            |      supported: 'gsm-umts'
            |        current: 'gsm-umts'
   -------------------------
   System   |         device: '/sys/devices/pci0000:00/0000:00:14.0/usb1/1-14'
            |        drivers: 'option1, cdc_ether'
            |         plugin: 'Generic'
            |   primary port: 'ttyUSB2'
            |          ports: 'ttyUSB1 (qcdm), ttyUSB2 (at), wwx0250f3000000 (net)'
   -------------------------
   -------------------------
   Status   |           lock: 'none'
            | unlock retries: 'unknown'
            |          state: 'disconnecting'
            |    power state: 'on'
            |    access tech: 'gprs'
            | signal quality: '40' (recent)
   -------------------------
   Modes    |      supported: 'allowed: 2g, 3g; preferred: none'
            |        current: 'allowed: 2g, 3g; preferred: none'
   -------------------------
   Bands    |      supported: 'unknown'
            |        current: 'unknown'
   -------------------------
   IP       |      supported: 'ipv4, ipv6'
   -------------------------
            |  enabled locks: 'none'
            |    operator id: '52015'
            |  operator name: 'TOT3G'
            |   subscription: 'unknown'
            |   registration: 'home'
   -------------------------
   SIM      |           path: '/org/freedesktop/ModemManager1/SIM/0'
 
 
   -------------------------
   Bearers  |          paths: '/org/freedesktop/ModemManager1/Bearer/0'
```

```
grumpy@grumpy-desktop:~$ sudo mmcli -m 0 | grep -Ev "imei|equipment|Numbers"
 [sudo] password for grumpy:  
 
 
 /org/freedesktop/ModemManager1/Modem/0 (device id 'c640d505eba92313212c61778d8a0c69ffd7c3b1')
   -------------------------
   Hardware |   manufacturer: 'huawei'
            |          model: 'E173'
            |       revision: '11.126.16.05.895'
            |      supported: 'gsm-umts'
            |        current: 'gsm-umts'
   -------------------------
   System   |         device: '/sys/devices/pci0000:00/0000:00:14.0/usb1/1-14'
            |        drivers: 'option1, cdc_ether'
            |         plugin: 'Generic'
            |   primary port: 'ttyUSB2'
            |          ports: 'ttyUSB1 (qcdm), ttyUSB2 (at), wwx0250f3000000 (net)'
   -------------------------
   -------------------------
   Status   |           lock: 'none'
            | unlock retries: 'unknown'
            |          state: 'disconnecting'
            |    power state: 'on'
            |    access tech: 'gprs'
            | signal quality: '40' (recent)
   -------------------------
   Modes    |      supported: 'allowed: 2g, 3g; preferred: none'
            |        current: 'allowed: 2g, 3g; preferred: none'
   -------------------------
   Bands    |      supported: 'unknown'
            |        current: 'unknown'
   -------------------------
   IP       |      supported: 'ipv4, ipv6'
   -------------------------
            |  enabled locks: 'none'
            |    operator id: '52015'
            |  operator name: 'TOT3G'
            |   subscription: 'unknown'
            |   registration: 'home'
   -------------------------
   SIM      |           path: '/org/freedesktop/ModemManager1/SIM/0'
 
 
   -------------------------
   Bearers  |          paths: '/org/freedesktop/ModemManager1/Bearer/0'
```
here is the output of that code

---

### Post by praseodym on 2015-11-01
Please have a look on the "checklist" here:

[http://ubuntuforums.org/showthread.php?t=1831649&highlight=umts+checklist](http://ubuntuforums.org/showthread.php?t=1831649&highlight=umts+checklist)

and show the outputs of:
```

lsmod
usb-devices
```

---

### Post by ronb19495 on 2015-11-01
Here are the outputs you requeted
 ```
 	 	 	 	   grumpy@grumpy-desktop:~$ lsmod
 Module                  Size  Used by
 ppp_async              20480  1
 crc_ccitt              16384  1 ppp_async
 uvcvideo               90112  0
 videobuf2_vmalloc      16384  1 uvcvideo
 videobuf2_memops       16384  1 videobuf2_vmalloc
 videobuf2_core         49152  1 uvcvideo
 v4l2_common            16384  1 videobuf2_core
 snd_usb_audio         176128  2
 videodev              172032  3 uvcvideo,v4l2_common,videobuf2_core
 snd_usbmidi_lib        32768  1 snd_usb_audio
 media                  24576  2 uvcvideo,videodev
 input_leds             16384  0
 hid_logitech_hidpp     20480  0
 joydev                 20480  0
 hid_logitech_dj        20480  0
 hid_generic            16384  0
 option                 49152  2
 usb_wwan               20480  1 option
 uas                    24576  0
 usbserial              53248  7 option,usb_wwan
 usb_storage            69632  1 uas
 usbhid                 49152  0
 cdc_ether              16384  0
 usbnet                 40960  1 cdc_ether
 mii                    16384  1 usbnet
 nls_iso8859_1          16384  1
 btrfs                 970752  0
 xor                    24576  1 btrfs
 raid6_pq              102400  1 btrfs
 intel_rapl             20480  0
 iosf_mbi               16384  1 intel_rapl
 x86_pkg_temp_thermal    16384  0
 intel_powerclamp       16384  0
 coretemp               16384  0
 kvm_intel             167936  0
 kvm                   512000  1 kvm_intel
 crct10dif_pclmul       16384  0
 crc32_pclmul           16384  0
 ghash_clmulni_intel    16384  0
 aesni_intel           167936  0
 aes_x86_64             20480  1 aesni_intel
 lrw                    16384  1 aesni_intel
 gf128mul               16384  1 lrw
 glue_helper            16384  1 aesni_intel
 ablk_helper            16384  1 aesni_intel
 cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
 serio_raw              16384  0
 snd_soc_rt5640        114688  0
 snd_soc_rl6231         16384  1 snd_soc_rt5640
 snd_hda_codec_hdmi     49152  1
 snd_soc_core          196608  1 snd_soc_rt5640
 lpc_ich                24576  0
 snd_compress           20480  1 snd_soc_core
 snd_hda_intel          36864  2
 ac97_bus               16384  1 snd_soc_core
 snd_pcm_dmaengine      16384  1 snd_soc_core
 snd_hda_codec         135168  2 snd_hda_codec_hdmi,snd_hda_intel
 snd_virtuoso           49152  1
 snd_hda_core           65536  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
 snd_oxygen_lib         45056  1 snd_virtuoso
 snd_seq_midi           16384  0
 snd_mpu401_uart        16384  1 snd_oxygen_lib
 snd_seq_midi_event     16384  1 snd_seq_midi
 snd_hwdep              16384  2 snd_usb_audio,snd_hda_codec
 snd_pcm               102400  9 snd_soc_rt5640,snd_usb_audio,snd_soc_core,snd_hda_codec_hdmi,snd_oxygen_lib,snd_hda_codec,snd_hda_intel,snd_pcm_dmaengine,snd_hda_core
 snd_rawmidi            32768  3 snd_usbmidi_lib,snd_mpu401_uart,snd_seq_midi
 mei_me                 32768  0
 snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
 mei                    98304  1 mei_me
 shpchp                 36864  0
 snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
 snd_timer              32768  2 snd_pcm,snd_seq
 snd                    81920  26 snd_usb_audio,snd_soc_core,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_virtuoso,snd_oxygen_lib,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_mpu401_uart,snd_seq_device,snd_compress
 dw_dmac                16384  0
 8250_fintek            16384  0
 dw_dmac_core           24576  1 dw_dmac
 snd_soc_sst_acpi       16384  0
 soundcore              16384  1 snd
 8250_dw                16384  0
 i2c_designware_platform    16384  0
 i2c_designware_core    16384  1 i2c_designware_platform
 spi_pxa2xx_platform    24576  0
 acpi_pad               20480  0
 mac_hid                16384  0
 intel_smartconnect     16384  0
 parport_pc             32768  0
 ppdev                  20480  0
 lp                     20480  0
 parport                49152  3 lp,ppdev,parport_pc
 autofs4                40960  2
 amdkfd                122880  1
 mxm_wmi                16384  0
 amd_iommu_v2           20480  1 amdkfd
 radeon               1519616  3
 i2c_algo_bit           16384  1 radeon
 ttm                    94208  1 radeon
 e1000e                237568  0
 drm_kms_helper        126976  1 radeon
 psmouse               126976  0
 drm                   356352  45 ttm,drm_kms_helper,radeon
 ahci                   36864  6
 ptp                    20480  1 e1000e
 libahci                32768  1 ahci
 pps_core               20480  1 ptp
 video                  36864  0
 wmi                    20480  1 mxm_wmi
 sdhci_acpi             16384  0
 i2c_hid                20480  0
 sdhci                  45056  1 sdhci_acpi
 hid                   118784  5 i2c_hid,hid_generic,usbhid,hid_logitech_dj,hid_logitech_hidpp

  	 	 	 	   
grumpy@grumpy-desktop:~$ usb-devices
 
 
 T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh=14
 D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
 P:  Vendor=1d6b ProdID=0002 Rev=04.02
 S:  Manufacturer=Linux 4.2.0-16-generic xhci-hcd
 S:  Product=xHCI Host Controller
 S:  SerialNumber=0000:00:14.0
 C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
 
 
 T:  Bus=01 Lev=01 Prnt=01 Port=13 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
 D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
 P:  Vendor=12d1 ProdID=1436 Rev=00.00
 S:  Manufacturer=HUAWEI Technology
 S:  Product=HUAWEI Mobile
 C:  #Ifs= 7 Cfg#= 1 Atr=e0 MxPwr=500mA
 I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
 I:  If#= 1 Alt= 0 #EPs= 1 Cls=02(commc) Sub=06 Prot=ff Driver=cdc_ether
 I:  If#= 2 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_ether
 I:  If#= 3 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
 I:  If#= 4 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
 I:  If#= 5 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
 I:  If#= 6 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
 
 
 T:  Bus=01 Lev=01 Prnt=01 Port=06 Cnt=02 Dev#=  2 Spd=480 MxCh= 4
 D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
 P:  Vendor=2109 ProdID=2812 Rev=85.70
 S:  Product=USB 2.0 HUB
        
 C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=100mA
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
 
 
 T:  Bus=01 Lev=02 Prnt=02 Port=00 Cnt=01 Dev#=  4 Spd=12  MxCh= 0
 D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
 P:  Vendor=046d ProdID=c52b Rev=12.01
 S:  Manufacturer=Logitech
 S:  Product=USB Receiver
 C:  #Ifs= 3 Cfg#= 1 Atr=a0 MxPwr=98mA
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid
 I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
 I:  If#= 2 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid
 
 
 T:  Bus=01 Lev=02 Prnt=02 Port=01 Cnt=02 Dev#=  5 Spd=12  MxCh= 0
 D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=32 #Cfgs=  1
 P:  Vendor=046d ProdID=c526 Rev=05.00
 S:  Manufacturer=Logitech
 S:  Product=USB Receiver
 C:  #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr=98mA
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
 I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid
 
 
 T:  Bus=01 Lev=02 Prnt=02 Port=02 Cnt=03 Dev#=  6 Spd=480 MxCh= 4
 D:  Ver= 2.10 Cls=09(hub  ) Sub=00 Prot=02 MxPS=64 #Cfgs=  1
 P:  Vendor=0451 ProdID=8043 Rev=01.00
 S:  SerialNumber=0F0008516890
 C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
 I:  If#= 0 Alt= 1 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=02 Driver=hub
 
 
 T:  Bus=01 Lev=03 Prnt=06 Port=02 Cnt=01 Dev#=  7 Spd=480 MxCh= 0
 D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
 P:  Vendor=046d ProdID=0809 Rev=00.10
 S:  SerialNumber=8B53779A
 C:  #Ifs= 4 Cfg#= 1 Atr=80 MxPwr=500mA
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
 I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo
 I:  If#= 2 Alt= 0 #EPs= 0 Cls=01(audio) Sub=01 Prot=00 Driver=snd-usb-audio
 I:  If#= 3 Alt= 0 #EPs= 0 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
 
 
 T:  Bus=01 Lev=03 Prnt=06 Port=03 Cnt=02 Dev#=  8 Spd=12  MxCh= 0
 D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
 P:  Vendor=046d ProdID=0a1f Rev=01.00
 S:  Manufacturer=Logitech
 S:  Product=Logitech G930 Headset
 C:  #Ifs= 4 Cfg#= 1 Atr=80 MxPwr=100mA
 I:  If#= 0 Alt= 0 #EPs= 0 Cls=01(audio) Sub=01 Prot=00 Driver=snd-usb-audio
 I:  If#= 1 Alt= 0 #EPs= 0 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
 I:  If#= 2 Alt= 0 #EPs= 0 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
 I:  If#= 3 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid
 
 
 T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 6
 D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
 P:  Vendor=1d6b ProdID=0003 Rev=04.02
 S:  Manufacturer=Linux 4.2.0-16-generic xhci-hcd
 S:  Product=xHCI Host Controller
 S:  SerialNumber=0000:00:14.0
 C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
 
 
 T:  Bus=02 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#=  2 Spd=5000 MxCh= 4
 D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
 P:  Vendor=2109 ProdID=0812 Rev=85.71
 S:  Manufacturer=VLI Labs, Inc.  
 S:  Product=USB 3.0 HUB
        
 C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
 
 
 T:  Bus=02 Lev=02 Prnt=02 Port=02 Cnt=01 Dev#=  3 Spd=5000 MxCh= 4
 D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
 P:  Vendor=0451 ProdID=8041 Rev=01.00
 C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
 
 
 T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
 D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
 P:  Vendor=1d6b ProdID=0002 Rev=04.02
 S:  Manufacturer=Linux 4.2.0-16-generic xhci-hcd
 S:  Product=xHCI Host Controller
 S:  SerialNumber=0000:06:00.0
 C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
 
 
 T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 2
 D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
 P:  Vendor=1d6b ProdID=0003 Rev=04.02
 S:  Manufacturer=Linux 4.2.0-16-generic xhci-hcd
 S:  Product=xHCI Host Controller
 S:  SerialNumber=0000:06:00.0
 C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
 
 
 T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
 D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
 P:  Vendor=1d6b ProdID=0002 Rev=04.02
 S:  Manufacturer=Linux 4.2.0-16-generic ehci_hcd
 S:  Product=EHCI Host Controller
 S:  SerialNumber=0000:00:1a.0
 C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
 
 
 T:  Bus=05 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6
 D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
 P:  Vendor=8087 ProdID=8009 Rev=00.00
 C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
 
 
 T:  Bus=06 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
 D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
 P:  Vendor=1d6b ProdID=0002 Rev=04.02
 S:  Manufacturer=Linux 4.2.0-16-generic ehci_hcd
 S:  Product=EHCI Host Controller
 S:  SerialNumber=0000:00:1d.0
 C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
 
 
 T:  Bus=06 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 8
 D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
 P:  Vendor=8087 ProdID=8001 Rev=00.00
 C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
 I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
```
  
every thing in the ckeck list looks ok

---

### Post by praseodym on 2015-11-01
```
T: Bus=01 Lev=01 Prnt=01 Port=13 Cnt=01 Dev#= 3 Spd=480 MxCh= 0
D: Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs= 1
P: Vendor=12d1 ProdID=1436 Rev=00.00
S: Manufacturer=HUAWEI Technology
S: Product=HUAWEI Mobile
C: #Ifs= 7 Cfg#= 1 Atr=e0 MxPwr=500mA
I: If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I: If#= 1 Alt= 0 #EPs= 1 Cls=02(commc) Sub=06 Prot=ff Driver=[COLOR="#FF0000"]cdc_ether[/COLOR]
I: If#= 2 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_ether
I: If#= 3 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I: If#= 4 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I: If#= 5 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I: If#= 6 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
```
Is it shown as "cable network" in the network-manager? Can you access a webinterface to configure? Please show:

```
mmcli -m 0 | grep -Ev "imei|equipment|Numbers"
```

---

### Post by praseodym on 2015-11-01
It doesn't seem to be SIM-locked. Lets check:

```
echo -e "AT+CPIN?\r" > /dev/ttyUSB0 && cat /dev/ttyUSB0 
echo -e "AT+CPIN?\r" > /dev/ttyUSB1 && cat /dev/ttyUSB1
echo -e "AT+CPIN?\r" > /dev/ttyUSB2 && cat /dev/ttyUSB2
```

---

### Post by ronb19495 on 2015-11-01
no its not locked because it does work on fedora and sabayon and it does work on 15.10 sometimes very rarely

---

### Post by praseodym on 2015-11-01
Outputs?!

---

### Post by ronb19495 on 2015-11-01
```
grumpy@grumpy-desktop:~$ echo -e "AT+CPIN?\r" > /dev/ttyUSB0 && cat /dev/ttyUSB0  
 bash: /dev/ttyUSB0: Permission denied
 grumpy@grumpy-desktop:~$ echo -e "AT+CPIN?\r" > /dev/ttyUSB1 && cat /dev/ttyUSB1bash: /dev/ttyUSB1: Permission denied
 grumpy@grumpy-desktop:~$ 
 grumpy@grumpy-desktop:~$ echo -e "AT+CPIN?\r" > /dev/ttyUSB2 && cat /dev/ttyUSB2bash: /dev/ttyUSB2: Permission denied
 grumpy@grumpy-desktop:~$
```
here you go

---

### Post by praseodym on 2015-11-02
Please repeat the commands with "sudo". Are you member of this group:
```

sudo adduser $USER dialout
```
Login again for the changes

---

### Post by ronb19495 on 2015-11-02
After that it took nine reboots before it connected

---

### Post by praseodym on 2015-11-02
Does it work now permanently? Please show the "sudo" outputs from above

---

### Post by ronb19495 on 2015-11-02
no it stopped connecting again I am typing this from sabayon,I will go back to ubuntu and get info for you

grumpy@grumpy-desktop:~$ sudo mmcli -m 0 | grep -Ev "imei|equipment|Numbers"
[sudo] password for grumpy: 

/org/freedesktop/ModemManager1/Modem/0 (device id 'c640d505eba92313212c61778d8a0c69ffd7c3b1')
  -------------------------
  Hardware |   manufacturer: 'huawei'
           |          model: 'E173'
           |       revision: '11.126.16.05.895'
           |      supported: 'gsm-umts'
           |        current: 'gsm-umts'
  -------------------------
  System   |         device: '/sys/devices/pci0000:00/0000:00:14.0/usb1/1-14'
           |        drivers: 'option1, cdc_ether'
           |         plugin: 'Generic'
           |   primary port: 'ttyUSB0'
           |          ports: 'ttyUSB0 (at), ttyUSB1 (qcdm), ttyUSB2 (at), wwx0250f3000000 (net)'
  -------------------------
  -------------------------
  Status   |           lock: 'none'
           | unlock retries: 'unknown'
           |          state: 'connected'
           |    power state: 'on'
           |    access tech: 'umts'
           | signal quality: '51' (recent)
  -------------------------
  Modes    |      supported: 'allowed: 2g, 3g; preferred: none'
           |        current: 'allowed: 2g, 3g; preferred: none'
  -------------------------
  Bands    |      supported: 'unknown'
           |        current: 'unknown'
  -------------------------
  IP       |      supported: 'ipv4, ipv6'
  -------------------------
           |  enabled locks: 'none'
           |    operator id: '52015'
           |  operator name: 'TOT3G'
           |   subscription: 'unknown'
           |   registration: 'home'
  -------------------------
  SIM      |           path: '/org/freedesktop/ModemManager1/SIM/0'

  -------------------------
  Bearers  |          paths: '/org/freedesktop/ModemManager1/Bearer/0'

grumpy@grumpy-desktop:~$ echo -e "AT+CPIN?\r" > /dev/ttyUSB0 && cat /dev/ttyUSB0bash: /dev/ttyUSB0: Device or resource busy
grumpy@grumpy-desktop:~$ echo -e "AT+CPIN?\r" > /dev/ttyUSB1 && cat /dev/ttyUSB1bash: /dev/ttyUSB1: Device or resource busy
grumpy@grumpy-desktop:~$ echo -e "AT+CPIN?\r" > /dev/ttyUSB2 && cat /dev/ttyUSB2bash: /dev/ttyUSB2: Device or resource busy
it is connected agaun

Maybe I have found the problem,in network settings I see 2 connections one wired the other mobile connection it looks like they are both trying to connect together,I have disabled wired to see what happens

no still not booting properly

---

### Post by praseodym on 2015-11-02
Tried disabling mobile instead?

---

### Post by ronb19495 on 2015-11-05
Thanks for your help [**[COLOR=#000000]praseodym[/COLOR]**]("http://ubuntuforums.org/member.php?u=1411497"),Ihave decided to do away with unbuntu due the the fact my huawei modem failed on ubuntu it works well on my other systems do thanks and good luck

---

