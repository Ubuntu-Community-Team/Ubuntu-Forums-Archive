---
title: "Netgear A6210 USB Wifi Adapter"
date: 2014-11-23
forum: Networking &amp; Wireless
---

### Post by furryaletheia on 2014-11-23
I am using a NETGEAR A6210 Wifi USB adapter. [http://www.netgear.com/home/products/networking/wifi-adapters/a6210.aspx](http://www.netgear.com/home/products/networking/wifi-adapters/a6210.aspx)

Here's what I did:

1. I got the windows driver from the CD that came with the adapter.
2. Installed the driver using the ndiswrapper gui--ndisgtk. 

After installing, ndisgtk says the hardware is present. However, the wifi never went up. I typed in 'ifconfig', and I couldn't find wlan0.

What am I doing wrong?

---

### Post by ajgreeny on 2014-11-23
Which version of Ubuntu are you running?

In 12.04 using the repository version of ndiswrapper gives exactly the symptoms you are seeing here, so you may need to compile ndsiwrapper if this is the case, but don't panic, it is very easy to do.

Download source from sourceforge :-
[http://sourceforge.net/projects/ndiswrapper/files/latest/download?source=files](http://sourceforge.net/projects/ndiswrapper/files/latest/download?source=files)
and extract the archive into a folder, ndiswrapper-#.##
From repositories install:-
ndisgtk, ndiswrapper-common, ndiswrapper-dkms, ndiswrapper-source and ndiswrapper-utils-#.#
plus all dependencies.

Ensure you have installed the linux-header packages for your kernel version.

cd to extracted ndiswrapper-#.## folder

Run these commands in order:-

sudo make
sudo make install
sudo modprobe ndiswrapper

Wireless connection should now be available.

---

### Post by furryaletheia on 2014-11-25
I am using ubuntu 14.04, but I will try compiling ndiswrapper from source.

---

### Post by malegault on 2015-09-08
Hi, I have the exact problem, did the solution suggested here turn out to work with 14.04?

Thanks,

---

### Post by Radall on 2015-09-21
No, tried the given solution as of today, because I stumbled on the exact same problem too, and had the same result.

Which means:
ndiswrapper tells me the drivers are installed and the device is present, but no WiFi will be shown.

I'm on a dualboot Win 8.1/Ubuntu 14.04 with a 3.16.0-49-generic kernel.

---

### Post by praseodym on 2015-09-21
Please show the outputs of
```

lsusb
lsmod
ndiswrapper -l
```

---

### Post by Radall on 2015-09-21
Yeah, sure. Please let me know, if you have an idea.

lsusb
```
Bus 002 Device 002: ID 8087:8001 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8009 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 046d:c32b Logitech, Inc. 
Bus 003 Device 005: ID 046d:c21c Logitech, Inc. G13 Advanced Gameboard
Bus 003 Device 010: ID 0846:9053 NetGear, Inc. 
Bus 003 Device 004: ID 045e:02d1 Microsoft Corp. 
Bus 003 Device 011: ID 07d1:3c16 D-Link System DWA-125 Wireless N 150 Adapter(rev.A2) [Ralink RT3070]
Bus 003 Device 003: ID 046d:c068 Logitech, Inc. G500 Laser Mouse
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

lsmod
```
Module                  Size  Used by
ndiswrapper           283985  0 
ctr                    13049  2 
ccm                    17773  2 
arc4                   12608  2 
rt2800usb              27189  0 
rt2x00usb              20742  1 rt2800usb
rt2800lib              89076  1 rt2800usb
rt2x00lib              55307  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              652777  3 rt2x00lib,rt2x00usb,rt2800lib
cfg80211              498458  2 mac80211,rt2x00lib
crc_ccitt              12707  1 rt2800lib
joydev                 17393  0 
hid_generic            12559  0 
usbhid                 52616  0 
hid                   110426  2 hid_generic,usbhid
rfcomm                 69509  0 
bnep                   19624  2 
bluetooth             446409  10 bnep,rfcomm
6lowpan_iphc           18702  1 bluetooth
nls_iso8859_1          12713  1 
snd_hda_codec_hdmi     47548  1 
nvidia               8591825  58 
snd_hda_codec_realtek    77561  1 
snd_hda_codec_generic    69011  1 snd_hda_codec_realtek
eeepc_wmi              13151  0 
asus_wmi               24094  1 eeepc_wmi
sparse_keymap          13948  1 asus_wmi
mxm_wmi                13021  0 
snd_hda_intel          30469  7 
snd_hda_controller     30228  1 snd_hda_intel
snd_hda_codec         139719  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              17698  1 snd_hda_codec
snd_pcm               104112  5 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30876  1 snd_seq_midi
intel_rapl             18783  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       18823  0 
coretemp               13441  0 
kvm                   452096  0 
crct10dif_pclmul       14307  0 
crc32_pclmul           13133  0 
ghash_clmulni_intel    13230  0 
snd_seq                63074  2 snd_seq_midi_event,snd_seq_midi
aesni_intel           152552  4 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_timer              29562  2 snd_pcm,snd_seq
serio_raw              13483  0 
snd                    79468  24 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
mei_me                 19696  0 
mei                    87875  1 mei_me
soundcore              15047  2 snd,snd_hda_codec
drm                   311018  3 nvidia
shpchp                 37047  0 
tpm_infineon           17131  0 
video                  20128  1 asus_wmi
wmi                    19193  2 mxm_wmi,asus_wmi
acpi_pad               17942  0 
mac_hid                13227  0 
parport_pc             32741  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
e1000e                226396  0 
psmouse               106767  0 
ptp                    19395  1 e1000e
ahci                   34142  5 
libahci                32424  1 ahci
pps_core               19382  1 ptp


```

ndiswrapper -l
```
netr28ux : driver installed
    device (0846:9053) present

```

EDIT: I have an old D-Link adapter, this is what you're seeing here
```
Bus 003 Device 011: ID 07d1:3c16 D-Link System DWA-125 Wireless N 150 Adapter(rev.A2) [Ralink RT3070]
```
But it's actually about
```
Bus 003 Device 010: ID 0846:9053 NetGear, Inc. 
```
like the thread says..

---

### Post by praseodym on 2015-09-21
So far, I haven't found a solution for this one. Errors?!
```

dmesg | grep ndis
```
Checked this thread?

[http://ubuntuforums.org/showthread.php?t=2265150&p=13227958#post13227958](http://ubuntuforums.org/showthread.php?t=2265150&p=13227958#post13227958)

---

### Post by Radall on 2015-09-21
Yes, I checked this thread, but basically the solution there is, to get a compatible device  >.<

But actually there were a lot of errors for ndiswrapper in my log:

dmesg -T | grep ndis
```
[Mon Sep 21 23:24:59 2015] usbcore: deregistering interface driver ndiswrapper
[Mon Sep 21 23:24:59 2015] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[Mon Sep 21 23:25:00 2015] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[Mon Sep 21 23:25:00 2015] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[Mon Sep 21 23:25:00 2015] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateTimerObject'
[Mon Sep 21 23:25:00 2015] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisSetTimerObject'
[Mon Sep 21 23:25:00 2015] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisCancelTimerObject'
[Mon Sep 21 23:25:00 2015] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeTimerObject'
[Mon Sep 21 23:25:00 2015] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferPool'
[Mon Sep 21 23:25:00 2015] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferPool'
[Mon Sep 21 23:25:00 2015] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[Mon Sep 21 23:25:00 2015] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[Mon Sep 21 23:25:00 2015] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[Mon Sep 21 23:25:00 2015] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[Mon Sep 21 23:25:00 2015] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[Mon Sep 21 23:25:00 2015] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[Mon Sep 21 23:25:00 2015] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[Mon Sep 21 23:25:00 2015] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[Mon Sep 21 23:25:00 2015] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[Mon Sep 21 23:25:00 2015] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
[Mon Sep 21 23:25:00 2015] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[Mon Sep 21 23:25:00 2015] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[Mon Sep 21 23:25:00 2015] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[Mon Sep 21 23:25:00 2015] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMFreePort'
[Mon Sep 21 23:25:00 2015] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[Mon Sep 21 23:25:00 2015] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[Mon Sep 21 23:25:00 2015] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[Mon Sep 21 23:25:00 2015] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBuffer'
[Mon Sep 21 23:25:00 2015] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBuffer'
[Mon Sep 21 23:25:00 2015] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferList'
[Mon Sep 21 23:25:00 2015] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[Mon Sep 21 23:25:00 2015] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[Mon Sep 21 23:25:00 2015] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'MmGetSystemRoutineAddress'
[Mon Sep 21 23:25:00 2015] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'KeSetCoalescableTimer'
[Mon Sep 21 23:25:00 2015] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'ExEventObjectType'
[Mon Sep 21 23:25:00 2015] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'RtlUnwindEx'
[Mon Sep 21 23:25:00 2015] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'RtlUnicodeToMultiByteN'
[Mon Sep 21 23:25:00 2015] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionBindClass'
[Mon Sep 21 23:25:00 2015] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[Mon Sep 21 23:25:00 2015] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[Mon Sep 21 23:25:00 2015] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionUnbindClass'
[Mon Sep 21 23:25:00 2015] ndiswrapper (load_sys_files:200): couldn't prepare driver 'netr28ux'
[Mon Sep 21 23:25:00 2015] ndiswrapper (load_wrap_driver:103): couldn't load driver netr28ux; check system log for messages from 'loadndisdriver'
[Mon Sep 21 23:25:00 2015] usbcore: registered new interface driver ndiswrapper


```

So I checked for 'loadndisdriver' in /var/log/syslog:
grep 'loadndisdriver' syslog
```
Sep 21 23:25:06 MonstersInc loadndisdriver: loadndisdriver: load_driver(364): couldn't load driver netr28ux
```

Well, this doesn't tell me much..

---

### Post by joyfiremike on 2015-09-23
Hello everybody.

I have the same problem, with similar 'dmesg' messages, so I started to investigate.
The messages indicates that ndiswrapper don't know [some "NDIS" functions]("https://msdn.microsoft.com/en-us/library/windows/hardware/ff563598(v=vs.85).aspx") that exist since [NDIS 6.0, i.e. Windows Vista]("https://msdn.microsoft.com/en-us/library/windows/hardware/ff567893(v=vs.85).aspx").

So, apparently, **ndiswrapper works only with Windows XP** drivers.

I then ran the Netgear driver install on an XP (virtual) machine I have, got the driver files, installed it under ndiswrapper... Fail.

Checking dmesg again, it appears that **ndiswrapper don't want a 32-bit windows driver with a 64-bit linux kernel**.
Damn. I always used Windows XP in 32-bit version only. No x64 version.
Ok. I had to install it on a new virtual machine... (Thank you Netgear to waste my time)
Then we go again: installed Netgear driver (very slow in x64 version!), got the driver files, installed them under ndiswrapper... Fail. Again.

Now I'm stuck. It seems that the Netgear driver uses Windows kernel calls that are out of ndiswrapper scope.

dmesg -T|grep ndis
```
[mer. sept. 23 16:04:21 2015] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[mer. sept. 23 16:04:21 2015] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'ExEventObjectType'
[mer. sept. 23 16:04:21 2015] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'MmGetSystemRoutineAddress'
[mer. sept. 23 16:04:21 2015] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'IoWMIWriteEvent'
[mer. sept. 23 16:04:21 2015] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'RtlStringFromGUID'
[mer. sept. 23 16:04:21 2015] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'__chkstk'
[mer. sept. 23 16:04:21 2015] ndiswrapper (load_sys_files:200): couldn't prepare driver 'rt2870'
[mer. sept. 23 16:04:21 2015] ndiswrapper (load_wrap_driver:103): couldn't load driver rt2870; check system log for messages from 'loadndisdriver'
[mer. sept. 23 16:04:21 2015] usbcore: registered new interface driver ndiswrapper
```

For example, '[MmGetSystemRoutineAddress]("https://msdn.microsoft.com/en-us/library/windows/hardware/ff554563(v=vs.85).aspx")' is a function used to get the pointer to a system function, so potentially, through this function, the driver can call any Windows function, which is out of ndiswrapper scope.

Any suggestion?

---

