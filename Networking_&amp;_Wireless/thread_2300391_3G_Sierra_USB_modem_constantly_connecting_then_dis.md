---
title: "3G Sierra USB modem constantly connecting then disconnecting"
date: 2015-10-25
forum: Networking &amp; Wireless
---

### Post by hendo2515 on 2015-10-25
Hello,


I have a USB modem supplied by Telstra in Australia. It seems to be connecting and then disconnecting. I can see if flicker on and off in the network manager applet. I am running unbutu 15.04. Is there anyway to fix this?

**uname -mr**

```
3.19.0-31-generic x86_64
```

**lsusb**

```
Bus 001 Device 015: ID 1199:6855 Sierra Wireless, Inc. 
```


**usb-devices**

```
T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#= 60 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1199 ProdID=6855 Rev=00.02
S:  Manufacturer=Sierra Wireless, Incorporated
S:  Product=AirCard
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 7 Cls=ff(vend.) Sub=ff Prot=ff Driver=sierra
```

**lsmod**

```
Module                  Size  Used by
sierra                 20480  104 
usbserial              49152  209 sierra
pci_stub               16384  1 
vboxpci                24576  0 
vboxnetadp             28672  0 
vboxnetflt             28672  0 
vboxdrv               421888  3 vboxnetadp,vboxnetflt,vboxpci
ctr                    16384  2 
ccm                    20480  2 
binfmt_misc            20480  1 
rfcomm                 69632  8 
bnep                   20480  2 
hid_generic            16384  0 
usbhid                 53248  0 
hid                   110592  2 hid_generic,usbhid
uvcvideo               90112  0 
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_core         49152  1 uvcvideo
v4l2_common            16384  1 videobuf2_core
videodev              159744  3 uvcvideo,v4l2_common,videobuf2_core
media                  24576  2 uvcvideo,videodev
btusb                  40960  0 
bluetooth             491520  22 bnep,btusb,rfcomm
snd_hda_codec_hdmi     53248  1 
snd_hda_codec_realtek    86016  1 
snd_hda_codec_generic    69632  1 snd_hda_codec_realtek
arc4                   16384  2 
joydev                 20480  0 
intel_rapl             20480  0 
iosf_mbi               16384  1 intel_rapl
x86_pkg_temp_thermal    16384  0 
intel_powerclamp       20480  0 
coretemp               16384  0 
kvm_intel             151552  0 
kvm                   483328  1 kvm_intel
crct10dif_pclmul       16384  0 
iwlmvm                278528  0 
crc32_pclmul           16384  0 
snd_hda_intel          36864  6 snd_hda_codec_hdmi
ghash_clmulni_intel    16384  0 
snd_hda_controller     32768  1 snd_hda_intel
mac80211              724992  1 iwlmvm
snd_hda_codec         143360  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              20480  1 snd_hda_codec
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
aesni_intel           172032  5 
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
nouveau              1400832  1 
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
serio_raw              16384  0 
iwlwifi               196608  1 iwlmvm
snd_seq_midi           16384  0 
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
thinkpad_acpi          86016  1 
mxm_wmi                16384  1 nouveau
nvram                  16384  1 thinkpad_acpi
ttm                    98304  1 nouveau
i915                 1060864  4 
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
rtsx_pci_ms            20480  0 
cfg80211              540672  3 iwlwifi,mac80211,iwlmvm
lpc_ich                24576  0 
memstick               20480  1 rtsx_pci_ms
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
drm_kms_helper        131072  2 i915,nouveau
mei_me                 20480  0 
snd_timer              32768  2 snd_pcm,snd_seq
mei                    90112  1 mei_me
drm                   348160  8 ttm,i915,drm_kms_helper,nouveau
snd                    90112  22 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device
ie31200_edac           16384  0 
i2c_algo_bit           16384  2 i915,nouveau
edac_core              53248  1 ie31200_edac
shpchp                 40960  0 
wmi                    20480  2 mxm_wmi,nouveau
soundcore              16384  2 snd,snd_hda_codec
video                  20480  2 i915,nouveau
mac_hid                16384  0 
parport_pc             32768  0 
ppdev                  20480  0 
lp                     20480  0 
parport                45056  3 lp,ppdev,parport_pc
autofs4                40960  2 
rtsx_pci_sdmmc         24576  0 
psmouse               118784  0 
ahci                   36864  2 
libahci                32768  1 ahci
rtsx_pci               49152  2 rtsx_pci_ms,rtsx_pci_sdmmc
e1000e                237568  0 
ptp                    20480  1 e1000e
pps_core               20480  1 ptp

```

**dmesg**

```
[ 1565.910954] usb 1-1: new full-speed USB device number 11 using xhci_hcd
[ 1566.040601] usb 1-1: New USB device found, idVendor=1199, idProduct=6855
[ 1566.040610] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 1566.040614] usb 1-1: Product: AirCard
[ 1566.040617] usb 1-1: Manufacturer: Sierra Wireless, Incorporated
[ 1567.263271] usbcore: registered new interface driver usbserial
[ 1567.263293] usbcore: registered new interface driver usbserial_generic
[ 1567.263307] usbserial: USB Serial support registered for generic
[ 1567.270134] usbcore: registered new interface driver sierra
[ 1567.270192] usbserial: USB Serial support registered for Sierra USB modem
[ 1567.270268] sierra 1-1:1.0: Sierra USB modem converter detected
[ 1567.270829] usb 1-1: Sierra USB modem converter now attached to ttyUSB0
[ 1567.271347] usb 1-1: Sierra USB modem converter now attached to ttyUSB1
[ 1567.271889] usb 1-1: Sierra USB modem converter now attached to ttyUSB2
[ 1607.781245] usb 1-1: USB disconnect, device number 11
[ 1607.781821] sierra ttyUSB0: Sierra USB modem converter now disconnected from ttyUSB0
[ 1607.782002] sierra ttyUSB1: Sierra USB modem converter now disconnected from ttyUSB1
[ 1607.782209] sierra ttyUSB2: Sierra USB modem converter now disconnected from ttyUSB2
[ 1607.782243] sierra 1-1:1.0: device disconnected
[ 1613.156001] usb 1-1: new full-speed USB device number 12 using xhci_hcd
[ 1613.285851] usb 1-1: New USB device found, idVendor=1199, idProduct=6855
[ 1613.285859] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 1613.285864] usb 1-1: Product: AirCard
[ 1613.285867] usb 1-1: Manufacturer: Sierra Wireless, Incorporated
[ 1613.287730] sierra 1-1:1.0: Sierra USB modem converter detected
[ 1613.288150] usb 1-1: Sierra USB modem converter now attached to ttyUSB3
[ 1613.288326] usb 1-1: Sierra USB modem converter now attached to ttyUSB4
[ 1613.288474] usb 1-1: Sierra USB modem converter now attached to ttyUSB5
[ 1654.131392] usb 1-1: USB disconnect, device number 12
[ 1654.131891] sierra ttyUSB3: Sierra USB modem converter now disconnected from ttyUSB3
[ 1654.132012] sierra ttyUSB4: Sierra USB modem converter now disconnected from ttyUSB4
[ 1654.132129] sierra ttyUSB5: Sierra USB modem converter now disconnected from ttyUSB5
[ 1654.132144] sierra 1-1:1.0: device disconnected
[ 1659.240327] usb 1-1: new full-speed USB device number 13 using xhci_hcd
[ 1659.369835] usb 1-1: New USB device found, idVendor=1199, idProduct=6855
[ 1659.369838] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 1659.369840] usb 1-1: Product: AirCard
[ 1659.369842] usb 1-1: Manufacturer: Sierra Wireless, Incorporated
[ 1659.370871] sierra 1-1:1.0: Sierra USB modem converter detected
[ 1659.371088] usb 1-1: Sierra USB modem converter now attached to ttyUSB6
[ 1659.371147] usb 1-1: Sierra USB modem converter now attached to ttyUSB7
[ 1659.371198] usb 1-1: Sierra USB modem converter now attached to ttyUSB8
[ 1700.097983] usb 1-1: USB disconnect, device number 13
[ 1700.098705] sierra ttyUSB6: Sierra USB modem converter now disconnected from ttyUSB6
[ 1700.098938] sierra ttyUSB7: Sierra USB modem converter now disconnected from ttyUSB7
[ 1700.099157] sierra ttyUSB8: Sierra USB modem converter now disconnected from ttyUSB8
[ 1700.099184] sierra 1-1:1.0: device disconnected
[ 1705.208639] usb 1-1: new full-speed USB device number 14 using xhci_hcd
[ 1705.338310] usb 1-1: New USB device found, idVendor=1199, idProduct=6855
[ 1705.338318] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 1705.338322] usb 1-1: Product: AirCard
[ 1705.338326] usb 1-1: Manufacturer: Sierra Wireless, Incorporated
[ 1705.339769] sierra 1-1:1.0: Sierra USB modem converter detected
[ 1705.340204] usb 1-1: Sierra USB modem converter now attached to ttyUSB9
[ 1705.340491] usb 1-1: Sierra USB modem converter now attached to ttyUSB10
[ 1705.341709] usb 1-1: Sierra USB modem converter now attached to ttyUSB11

```

**cat /var/log/syslog | tail -20**
```
Oct 26 07:26:24 mel-prgl002 kernel: [ 4157.615319] usb 1-1: new full-speed USB device number 67 using xhci_hcd
Oct 26 07:26:24 mel-prgl002 kernel: [ 4157.744375] usb 1-1: New USB device found, idVendor=1199, idProduct=6855
Oct 26 07:26:24 mel-prgl002 kernel: [ 4157.744378] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Oct 26 07:26:24 mel-prgl002 kernel: [ 4157.744380] usb 1-1: Product: AirCard
Oct 26 07:26:24 mel-prgl002 kernel: [ 4157.744381] usb 1-1: Manufacturer: Sierra Wireless, Incorporated
Oct 26 07:26:24 mel-prgl002 kernel: [ 4157.745369] sierra 1-1:1.0: Sierra USB modem converter detected
Oct 26 07:26:24 mel-prgl002 kernel: [ 4157.745534] usb 1-1: Sierra USB modem converter now attached to ttyUSB168
Oct 26 07:26:24 mel-prgl002 kernel: [ 4157.745586] usb 1-1: Sierra USB modem converter now attached to ttyUSB169
Oct 26 07:26:24 mel-prgl002 kernel: [ 4157.745635] usb 1-1: Sierra USB modem converter now attached to ttyUSB170
Oct 26 07:26:24 mel-prgl002 mtp-probe: checking bus 1, device 67: "/sys/devices/pci0000:00/0000:00:14.0/usb1/1-1"
Oct 26 07:26:24 mel-prgl002 mtp-probe: bus: 1, device: 67 was not an MTP device
Oct 26 07:26:25 mel-prgl002 ModemManager[871]: <warn>  (ttyUSB168): port attributes not fully set
Oct 26 07:26:25 mel-prgl002 ModemManager[871]: <warn>  (ttyUSB170): port attributes not fully set
Oct 26 07:26:25 mel-prgl002 ModemManager[871]: <warn>  (ttyUSB169): port attributes not fully set

```

**rfkill list**
```
0: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

---

### Post by Hadaka on 2015-10-25
hi from a working wired connection with the usb device removed please do..
```
sudo apt-get updates && sudo apt-get upgrade
sudo apt-get autoremove && sudo apt-get autoclean
```
let this run to completion-then leave wired connection attached 
insert the usb and reboot
then do..
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```
once again reboot and do..
```
cat /etc/udev/rules.d/70-persistent-net.rules
```
is your device listed??? 
Device ID ->USB Device ????? --- [ID 1199:6855 Sierra Wireless,] xxxx 6855

---

### Post by hendo2515 on 2015-10-26
Hello Hadaka,

The /etc/udev/rules.d/70-persistent-net.rules did not regenerate on the reboot.

---

