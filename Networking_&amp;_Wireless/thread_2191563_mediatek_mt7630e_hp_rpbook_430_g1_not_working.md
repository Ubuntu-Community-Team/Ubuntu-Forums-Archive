---
title: "mediatek mt7630e hp rpbook 430 g1 not working"
date: 2013-12-03
forum: Networking &amp; Wireless
---

### Post by tafazzi87 on 2013-12-03
hi, i've a hp probook 430 g1 with a mediatek mt7630e and it doesn't work out of the box so i try to install drivers with ndiswrapper and now i've this situation:
with 
```
ndiswrapper -l
```
i've this output:
```
netr28x : driver installed
   device (14C3:7630) present
```
and with this:
```
dmesg | grep ndiswrapper
```
i've this output
```
[   11.853001] ndiswrapper version 1.58 loaded (smp=yes, preempt=yes)
[   12.564472] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'isxdigit'
[   12.565549] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'ExEventObjectType'
[   12.566524] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'KeSetCoalescableTimer'
[   12.567477] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   12.568373] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   12.569322] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   12.570430] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'
[   12.571355] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMAllocateNetBufferSGList'
[   12.572339] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisCopySendNetBufferListInfo'
[   12.573287] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[   12.574142] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
[   12.574977] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   12.575907] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[   12.576869] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[   12.577840] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   12.578783] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   12.579589] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   12.580426] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   12.581492] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   12.582419] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   12.583362] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   12.584374] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBuffer'
[   12.585237] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBuffer'
[   12.586186] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMFreePort'
[   12.587011] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[   12.587993] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[   12.588936] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[   12.589897] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   12.590892] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   12.591846] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   12.592790] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   12.593779] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   12.594721] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[   12.595650] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   12.596525] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[   12.597425] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisRegisterDeviceEx'
[   12.598352] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisDeregisterDeviceEx'
[   12.599334] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   12.600291] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   12.601351] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferPool'
[   12.602288] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferPool'
[   12.603245] ndiswrapper (load_sys_files:199): couldn't prepare driver 'netr28x'
[   12.604217] ndiswrapper (load_wrap_driver:121): couldn't load driver 'netr28x'
[   12.609097] usbcore: registered new interface driver ndiswrapper
```
how can i fix this???

---

### Post by praseodym on 2013-12-03
Try the driver **MT7610U USB** from Ralink

[http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501](http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501)

---

### Post by tafazzi87 on 2013-12-03
download not exists...

---

### Post by praseodym on 2013-12-03
I've downloaded the driver but its too large for an attachment.

Try this one

[http://www.mediatek.com/_en/07_downloads/01-1_windowsDetail.php?sn=5041](http://www.mediatek.com/_en/07_downloads/01-1_windowsDetail.php?sn=5041)

you need to add a random name and an email address

---

### Post by tafazzi87 on 2013-12-04
sorry but after compilation i've to do what?
```
modprobe mt7650u_sta
```
?

---

### Post by praseodym on 2013-12-04
Reboot and check
```

iwconfig
lsmod
rfkill list
cat /etc/resolv.conf
route -n
iwlist chan
sudo iwlist scan
```

---

### Post by tafazzi87 on 2013-12-05
this is my output:
```
tafazzi87@tafazzi87-HP-ProBook-430-G1:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

tafazzi87@tafazzi87-HP-ProBook-430-G1:~$ lsmod
Module                  Size  Used by
snd_hda_codec_idt      64649  1 
snd_hda_codec_hdmi     36612  1 
rfcomm                 38400  0 
bnep                   17852  2 
bluetooth             211552  10 rfcomm,bnep
parport_pc             27612  0 
ppdev                  12849  0 
joydev                 17329  0 
snd_hda_intel          38819  5 
snd_hda_codec         118650  3 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                85934  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
uvcvideo               72250  0 
coretemp               13324  0 
snd_seq_midi           13132  0 
snd_rawmidi            25157  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
videobuf2_core         39385  1 uvcvideo
kvm_intel             127786  0 
i915                  550464  3 
kvm                   384557  1 kvm_intel
snd_seq                51593  2 snd_seq_midi,snd_seq_midi_event
videodev               96131  2 uvcvideo,videobuf2_core
aesni_intel            18196  0 
ablk_helper            13357  1 aesni_intel
cryptd                 19821  1 ablk_helper
lrw                    13127  1 aesni_intel
aes_i586               16995  1 aesni_intel
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
xts                    12778  1 aesni_intel
videobuf2_vmalloc      12920  1 uvcvideo
videobuf2_memops       13042  1 videobuf2_vmalloc
drm_kms_helper         47749  1 i915
drm                   233935  4 i915,drm_kms_helper
snd                    57014  20 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                82769  0 
gf128mul               14503  2 lrw,xts
microcode              18433  0 
hp_wmi                 17748  0 
sparse_keymap          13658  1 hp_wmi
i2c_algo_bit           13316  1 i915
serio_raw              13031  0 
soundcore              12600  1 snd
snd_page_alloc         18398  2 snd_hda_intel,snd_pcm
video                  19116  1 i915
mei                    36756  0 
lpc_ich                17048  0 
rtsx_pci_ms            13012  0 
memstick               15885  1 rtsx_pci_ms
wmi                    18744  1 hp_wmi
mac_hid                13077  0 
ndiswrapper           197073  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
rtsx_pci_sdmmc         17544  0 
ahci                   25631  2 
libahci                26336  1 ahci
rtsx_pci               32978  2 rtsx_pci_ms,rtsx_pci_sdmmc
r8169                  62532  0 
tafazzi87@tafazzi87-HP-ProBook-430-G1:~$ rfkill list
tafazzi87@tafazzi87-HP-ProBook-430-G1:~$ cat /etc/resolv.conf 
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
tafazzi87@tafazzi87-HP-ProBook-430-G1:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
tafazzi87@tafazzi87-HP-ProBook-430-G1:~$ iwlist chan
lo        no frequency information.

eth0      no frequency information.

tafazzi87@tafazzi87-HP-ProBook-430-G1:~$ sudo iwlist scan
[sudo] password for tafazzi87: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


```

---

### Post by praseodym on 2013-12-05
Try
```

sudo modprobe -v mt7650u_sta
iwconfig
dmesg | grep mt7
sudo iwlist scan
iwlist chan
```

---

### Post by tafazzi87 on 2013-12-06
first input give me
```
FATAL: Module mt7650u_sta note found.
```

---

### Post by praseodym on 2013-12-06
```
modinfo mt7650u_sta 
filename:       /lib/modules/3.8.0-34-generic/kernel/drivers/net/wireless/mt7650u_sta.ko
version:        3.0.0.2
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
license:        GPL
srcversion:     D1E588C2E22F986426962F9
alias:          usb:v[COLOR="#FF0000"]0E8D[/COLOR]p[COLOR="#FF0000"]7650[/COLOR]d*dc*dsc*dp*icFFisc02ipFFin*
alias:          usb:v0E8Dp7630d*dc*dsc*dp*icFFisc02ipFFin*
alias:          usb:v0E8Dp7610d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp7610d*dc*dsc*dp*ic*isc*ip*in*
depends:        
vermagic:       3.8.0-34-generic SMP mod_unload modversions 686 
parm:           mac:rt28xx: wireless mac addr (charp)

```
You device ID is not part of this driver. Here, it compiled with kernel 3.8 on 12.04. Try the other driver there: mt7601Usta

```
modinfo mt7601Usta 
filename:       /lib/modules/3.8.0-34-generic/kernel/drivers/net/wireless/mt7601Usta.ko
version:        3.0.0.3
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
license:        GPL
srcversion:     E3EE381863883B309D682BB
alias:          usb:v148Fp7601d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp6370d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp7650d*dc*dsc*dp*ic*isc*ip*in*
depends:        
vermagic:       3.8.0-34-generic SMP mod_unload modversions 686 
parm:           mac:rt28xx: wireless mac addr (charp)

```

Please check first:
```

lsusb
```

---

### Post by tafazzi87 on 2013-12-07
i try with mt7601Usta 
and this is output of previous command:
```

tafazzi87@tafazzi87-HP-ProBook-430-G1:~$ sudo modprobe -v mt7601Usta 
[sudo] password for tafazzi87: 
insmod /lib/modules/3.8.0-34-generic/kernel/drivers/net/wireless/mt7601Usta.ko 
tafazzi87@tafazzi87-HP-ProBook-430-G1:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

tafazzi87@tafazzi87-HP-ProBook-430-G1:~$ dmesg | grep mt7
tafazzi87@tafazzi87-HP-ProBook-430-G1:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

tafazzi87@tafazzi87-HP-ProBook-430-G1:~$ iwlist chan
lo        no frequency information.

eth0      no frequency information.

```
for lsusb i've this output:
```

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 002: ID 0e8d:763e MediaTek Inc. 
Bus 002 Device 003: ID 138a:003f Validity Sensors, Inc. 
Bus 002 Device 004: ID 04ca:7022 Lite-On Technology Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

```
thanks for your patient!!!

---

### Post by praseodym on 2013-12-07
Obviously, both drivers are not suitable. Lets try to add the device ID to the driver, but first copy its firmware to the right place:
```

sudo cp /common/rt2870_wow.bin /lib/firmware/
```
Add the ID:
```

echo 'install mt7601Usta modprobe --ignore-install mt7601Usta; /bin/echo "0e8d 763e" > /sys/bus/usb/drivers/mt7601Usta/new_id' | sudo tee /etc/modprobe.d/mt7601Usta.conf
```

This is one line, you better copy/paste it. Reboot after that.

---

### Post by tafazzi87 on 2013-12-07
ok i'll do it but now after reboot if i give 
```
sudo modprobe -v mt7601Usta
```
it give me this:
```
tafazzi87@tafazzi87-HP-ProBook-430-G1:~$ sudo modprobe -v mt7601Usta 
[sudo] password for tafazzi87: 
install modprobe --ignore-install mt7601Usta; /bin/echo "0e8d 763e" > /sys/bus/usb/drivers/mt7601Usta/new_id
insmod /lib/modules/3.8.0-34-generic/kernel/drivers/net/wireless/mt7601Usta.ko 
sh: 1: cannot create /sys/bus/usb/drivers/mt7601Usta/new_id: Directory nonexistent
FATAL: Error running install command for mt7601Usta

```

---

### Post by praseodym on 2013-12-07
Ok, then first:
[B]
sudo mkdir -p /sys/bus/usb/drivers/mt7601Usta/[/B]

---

### Post by tafazzi87 on 2013-12-07
> **praseodym said:**
> Ok, then first:
[B]
sudo mkdir -p /sys/bus/usb/drivers/mt7601Usta/[/B]

give me this error:
```
mkdir: cannot create directory `/sys/bus/usb/drivers/mt7601Usta/': No such file or directory
```

---

### Post by praseodym on 2013-12-07
sudo mkdir -p /sys/bus/usb/drivers/mt7601Usta

without slash, sorry

---

### Post by tafazzi87 on 2013-12-07
i've same error also without last slash

---

### Post by praseodym on 2013-12-07
Lets try it with driver rt2800usb:
```

echo 'install rt2800usb modprobe --ignore-install rt2800usb; /bin/echo "0e8d 763e" > /sys/bus/usb/drivers/rt2800usb/new_id' | sudo tee /etc/modprobe.d/rt2800usb.conf
sudo modprobe -v rt2800usb
iwconfig
dmesg | grep rt2
```

---

### Post by tafazzi87 on 2013-12-07
i'll try it but second input stopped in this way:
```

root@tafazzi87-HP-ProBook-430-G1:~# sudo modprobe -v rt2800usb
insmod /lib/modules/3.8.0-34-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.8.0-34-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.8.0-34-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko 
insmod /lib/modules/3.8.0-34-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko 
insmod /lib/modules/3.8.0-34-generic/kernel/lib/crc-ccitt.ko 
insmod /lib/modules/3.8.0-34-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko 
install modprobe --ignore-install rt2800usb; /bin/echo "0e8d 763e" > /sys/bus/usb/drivers/rt2800usb/new_id
insmod /lib/modules/3.8.0-34-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko 
```
and it doesn't finish

---

### Post by tafazzi87 on 2013-12-07
i've closed and i've make another time input and now it works, now i've this output:
```

tafazzi87@tafazzi87-HP-ProBook-430-G1:~$ echo 'install rt2800usb modprobe --ignore-install rt2800usb; /bin/echo "0e8d 763e" > /sys/bus/usb/drivers/rt2800usb/new_id' | sudo tee /etc/modprobe.d/rt2800usb.conf
[sudo] password for tafazzi87: 
install rt2800usb modprobe --ignore-install rt2800usb; /bin/echo "0e8d 763e" > /sys/bus/usb/drivers/rt2800usb/new_id
tafazzi87@tafazzi87-HP-ProBook-430-G1:~$ sudo modprobe -v rt2800
rt2800lib  rt2800pci  rt2800usb  
tafazzi87@tafazzi87-HP-ProBook-430-G1:~$ sudo modprobe -v rt2800usb 
tafazzi87@tafazzi87-HP-ProBook-430-G1:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

tafazzi87@tafazzi87-HP-ProBook-430-G1:~$ dmesg | grep rt2
[  175.479069] usbcore: registered new interface driver rt2800usb

```

---

### Post by praseodym on 2013-12-07
Re-plug the stick and check again:

```
lsusb
lsmod
iwconfig

```
Does Ubuntu show an additional hard drive if the stick is plugged? If yes, right-click and remove it. Show then "lsusb" again.

---

### Post by tafazzi87 on 2013-12-07
i don't have a stick, wifi card is integrated on my laptop!!;)

---

### Post by praseodym on 2013-12-07
> ```
Bus 002 Device 002: ID 0e8d:763e MediaTek Inc. 
```
Obviously, its an internal USB? Lets be sure
```

lspci -nnk
lsusb
```

---

### Post by tafazzi87 on 2013-12-07
```
tafazzi87@tafazzi87-HP-ProBook-430-G1:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Haswell-ULT DRAM Controller [8086:0a04] (rev 09)
	Subsystem: Hewlett-Packard Company Device [103c:1946]
00:02.0 VGA compatible controller [0300]: Intel Corporation Haswell-ULT Integrated Graphics Controller [8086:0a16] (rev 09)
	Subsystem: Hewlett-Packard Company Device [103c:1946]
	Kernel driver in use: i915
	Kernel modules: i915
00:03.0 Audio device [0403]: Intel Corporation Device [8086:0a0c] (rev 09)
	Subsystem: Hewlett-Packard Company Device [103c:1946]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel
00:14.0 USB controller [0c03]: Intel Corporation Lynx Point-LP USB xHCI HC [8086:9c31] (rev 04)
	Subsystem: Hewlett-Packard Company Device [103c:1946]
	Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation Lynx Point-LP HECI #0 [8086:9c3a] (rev 04)
	Subsystem: Hewlett-Packard Company Device [103c:1946]
	Kernel modules: mei
00:1b.0 Audio device [0403]: Intel Corporation Lynx Point-LP HD Audio Controller [8086:9c20] (rev 04)
	Subsystem: Hewlett-Packard Company Device [103c:1946]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation Lynx Point-LP PCI Express Root Port 1 [8086:9c10] (rev e4)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation Lynx Point-LP PCI Express Root Port 2 [8086:9c12] (rev e4)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation Lynx Point-LP PCI Express Root Port 3 [8086:9c14] (rev e4)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation Lynx Point-LP PCI Express Root Port 4 [8086:9c16] (rev e4)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation Lynx Point-LP USB EHCI #1 [8086:9c26] (rev 04)
	Subsystem: Hewlett-Packard Company Device [103c:1946]
	Kernel driver in use: ehci-pci
00:1f.0 ISA bridge [0601]: Intel Corporation Lynx Point-LP LPC Controller [8086:9c43] (rev 04)
	Subsystem: Hewlett-Packard Company Device [103c:1946]
	Kernel driver in use: lpc_ich
	Kernel modules: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] [8086:9c03] (rev 04)
	Subsystem: Hewlett-Packard Company Device [103c:1946]
	Kernel driver in use: ahci
	Kernel modules: ahci
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5227] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:1946]
	Kernel driver in use: rtsx_pci
	Kernel modules: rtsx_pci
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
	Subsystem: Hewlett-Packard Company Device [103c:1946]
	Kernel driver in use: r8169
	Kernel modules: r8169
04:00.0 Network controller [0280]: MEDIATEK Corp. Device [14c3:7630]
	Subsystem: Hewlett-Packard Company Device [103c:197c]

```
and this is lsusb
```

tafazzi87@tafazzi87-HP-ProBook-430-G1:~$ lsusb
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 005: ID 0781:5567 SanDisk Corp. Cruzer Blade
Bus 002 Device 002: ID 0e8d:763e MediaTek Inc. 
Bus 002 Device 003: ID 138a:003f Validity Sensors, Inc. 
Bus 002 Device 004: ID 04ca:7022 Lite-On Technology Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

```

---

### Post by praseodym on 2013-12-07
Ok, it was a misunderstanding. Remove this file:

```
sudo rm /etc/modprobe.d/mt7601Usta.conf
```
Its a PCI device:
```

04:00.0 Network controller [0280]: MEDIATEK Corp. Device [14c3:7630]
	Subsystem: Hewlett-Packard Company Device [103c:197c]
```
Ndiswrapper obviously doesnt work:

```
sudo modprobe -rfv ndiswrapper
```
Try to add the ID to rt2800pci:
```

echo 'install rt2800pci modprobe --ignore-install rt2800pci; /bin/echo "14c3 7630" > /sys/bus/pci/drivers/rt2800pci/new_id' | sudo tee /etc/modprobe.d/rt2800pci.conf
```
Load the driver
```

sudo modprobe -v rt2800pci
lsmod
iwconfig
rfkill list
sudo iwlist scan
dmesg | grep rt2
```

---

### Post by tafazzi87 on 2013-12-07
this is output for all inputs:
```

tafazzi87@tafazzi87-HP-ProBook-430-G1:~$ sudo modprobe -v rt2800pci 
insmod /lib/modules/3.8.0-34-generic/kernel/drivers/misc/eeprom/eeprom_93cx6.ko 
insmod /lib/modules/3.8.0-34-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.8.0-34-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.8.0-34-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko 
insmod /lib/modules/3.8.0-34-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko 
insmod /lib/modules/3.8.0-34-generic/kernel/lib/crc-ccitt.ko 
insmod /lib/modules/3.8.0-34-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko 
install modprobe --ignore-install rt2800pci; /bin/echo "14c3 7630" > /sys/bus/pci/drivers/rt2800pci/new_id
insmod /lib/modules/3.8.0-34-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko 
tafazzi87@tafazzi87-HP-ProBook-430-G1:~$ lsmod
Module                  Size  Used by
rt2800pci              18371  0 
rt2800lib              61785  1 rt2800pci
crc_ccitt              12627  1 rt2800lib
rt2x00pci              14237  1 rt2800pci
rt2x00lib              49144  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              541819  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              453919  2 rt2x00lib,mac80211
eeprom_93cx6           13168  1 rt2800pci
nls_iso8859_1          12617  1 
usb_storage            48053  1 
snd_hda_codec_idt      64649  1 
snd_hda_codec_hdmi     36612  1 
rfcomm                 38400  0 
bnep                   17852  2 
bluetooth             211552  10 rfcomm,bnep
parport_pc             27612  0 
ppdev                  12849  0 
joydev                 17329  0 
snd_hda_intel          38819  5 
snd_hda_codec         118650  3 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel
uvcvideo               72250  0 
videobuf2_core         39385  1 uvcvideo
videodev               96131  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12920  1 uvcvideo
videobuf2_memops       13042  1 videobuf2_vmalloc
coretemp               13324  0 
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                85934  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
i915                  550464  3 
kvm_intel             127786  0 
kvm                   384557  1 kvm_intel
snd_rawmidi            25157  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51593  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
aesni_intel            18196  0 
ablk_helper            13357  1 aesni_intel
drm_kms_helper         47749  1 i915
cryptd                 19821  1 ablk_helper
drm                   233935  4 i915,drm_kms_helper
snd                    57014  20 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                82769  0 
hp_wmi                 17748  0 
lrw                    13127  1 aesni_intel
aes_i586               16995  1 aesni_intel
xts                    12778  1 aesni_intel
gf128mul               14503  2 lrw,xts
sparse_keymap          13658  1 hp_wmi
soundcore              12600  1 snd
i2c_algo_bit           13316  1 i915
snd_page_alloc         18398  2 snd_hda_intel,snd_pcm
video                  19116  1 i915
microcode              18433  0 
serio_raw              13031  0 
lpc_ich                17048  0 
rtsx_pci_ms            13012  0 
mei                    36756  0 
memstick               15885  1 rtsx_pci_ms
wmi                    18744  1 hp_wmi
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
rtsx_pci_sdmmc         17544  0 
ahci                   25631  2 
libahci                26336  1 ahci
r8169                  62532  0 
rtsx_pci               32978  2 rtsx_pci_ms,rtsx_pci_sdmmc
tafazzi87@tafazzi87-HP-ProBook-430-G1:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

tafazzi87@tafazzi87-HP-ProBook-430-G1:~$ rfkill list
tafazzi87@tafazzi87-HP-ProBook-430-G1:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

tafazzi87@tafazzi87-HP-ProBook-430-G1:~$ dmesg | grep rt2
[  123.964397] phy0 -> rt2800_init_eeprom: Error - Invalid RT chipset 0x7650 detected.
[  123.964401] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
tafazzi87@tafazzi87-HP-ProBook-430-G1:~$ 

```

---

### Post by praseodym on 2013-12-07
Nope, sorry:
```

sudo rm /etc/modprobe.d/rt2800pci.conf
```
I recommend contacting Ralink about it.

---

### Post by tafazzi87 on 2013-12-07
ok thanks for your time!!!

---

### Post by praseodym on 2013-12-08
You're welcome. If there's a solution, please post it here.

Thanks.

---

### Post by praseodym on 2013-12-08
You're welcome. If there's a solution, please post it here.

Thanks.

---

