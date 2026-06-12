---
title: "Ubuntu 14.04 Lenovo Edge 15 (2015) Wifi not working"
date: 2015-09-25
forum: Networking &amp; Wireless
---

### Post by aru2 on 2015-09-25
Hello,

Im new to Ubuntu and im trying to get my wifi up and running, i have tried:

**System Settings > Software & Updates > Additional drivers (This freezes my system and renders it unusable, ive had to reinstall ubuntu after trying this)
**sudo apt-get install bcmwl-kernel-source (this did not work)
**sudo apt-get install –reinstall bcmwl-kernel-source (This did not work either)
**sudo apt-get remove --purge bcmwl-kernel-source (after removing i tried reinstalling bcmwl-kernel-source and did not work)

I´m lacking more troubleshooting knowledge as i am new to this OS so i would appreciate any kind of help.

Thank you!

---

### Post by jeremy31 on 2015-09-25
Please post ```
uname -a; dpkg -l | grep -i broadcom
```

---

### Post by aru2 on 2015-09-25
Thanks for the quick response, here is the result:

> 
aru@Mari:~$ uname -a; dpkg -l | grep -i broadcom
Linux Mari 3.19.0-28-generic #30~14.04.1-Ubuntu SMP Tue Sep 1 09:32:55 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
aru@Mari:~$


---

### Post by jeremy31 on 2015-09-25
Ok, ```
lspci -nnk | grep -iA2 net
```

---

### Post by aru2 on 2015-09-25
Result:
> 
aru@Mari:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:43ae] (rev 02)
    Subsystem: Lenovo Device [17aa:0622]
    Kernel driver in use: wl
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:3818]
    Kernel driver in use: r8169
aru@Mari:~$ 



---

### Post by jeremy31 on 2015-09-25
The module wl is there so ```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-dkms
sudo apt-get install linux-firmware
echo "blacklist b43" | sudo tee /etc/modprobe.d/broadcom.conf
echo "blacklist ssb" | sudo tee -a /etc/modprobe.d/broadcom.conf
```

Reboot

---

### Post by aru2 on 2015-09-25
Ok, I ran the commands and rebooted and it still looks the same.

Results:
> aru@Mari:~$ sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-dkms
[sudo] password for aru: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'broadcom-sta-common' is not installed, so not removed
Package 'broadcom-sta-dkms' is not installed, so not removed
Package 'bcmwl-kernel-source' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
aru@Mari:~$ sudo apt-get install linux-firmware
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-firmware is already the newest version.
linux-firmware set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
aru@Mari:~$ echo "blacklist b43" | sudo tee /etc/modprobe.d/broadcom.conf
blacklist b43
aru@Mari:~$ echo "blacklist ssb" | sudo tee -a /etc/modprobe.d/broadcom.conf
blacklist ssb
aru@Mari:~$



---

### Post by jeremy31 on 2015-09-25
Lets see ```
lspci -nnk | grep -iA2 net; iwlist scan
```

---

### Post by aru2 on 2015-09-25
Result:

> 
02:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:43ae] (rev 02)
    Subsystem: Lenovo Device [17aa:0622]
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:3818]
    Kernel driver in use: r8169
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

aru@Mari:~$ 



---

### Post by praseodym on 2015-09-26
Hi,

so far, this device is not supported yet. 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1432869](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1432869)

The actual Broadcom-STA driver is not supporting it.

---

### Post by aru2 on 2015-09-26
is there a way to workaround that? I read online that there is a way to force Ubuntu to use the drivers meant for windows...

---

### Post by praseodym on 2015-09-27
It is possible with the respective Win driver and Ndiswrapper:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Extract the EXE with the file roller (right-klick-> extract)

---

### Post by aru2 on 2015-09-28
Ok... it took me a while but I´m finally getting somewhere...

I installed the windows driver and ndisgtk accepted it ... but the network manager is still not recognizing my wifi...

anyone got any ideas?... I feel like I´m very close to making this thing work... but google can only get me so far... and right now im stumped... 

[IMG]http://i92.photobucket.com/albums/l7/arutsuro-kun/Selection_002_1.png[/IMG]

---

### Post by praseodym on 2015-09-28
Lets check:
```

sudo ndiswrapper -ma
grep loadndisdriver /var/log/syslog
dmesg | grep ndis
lsmod
```

---

### Post by aru2 on 2015-09-28
Result:

> root@Mari:~# sudo ndiswrapper -ma
module configuration information is stored in /etc/modprobe.d/ndiswrapper.conf
root@Mari:~# grep loadndisdriver /var/log/syslog
Sep 28 00:56:47 Mari loadndisdriver: loadndisdriver: load_driver(364): couldn't load driver bcmwl63
Sep 28 00:56:47 Mari kernel: [15720.641273] ndiswrapper (load_wrap_driver:103): couldn't load driver bcmwl63; check system log for messages from 'loadndisdriver'
Sep 28 01:08:07 Mari kernel: [    2.220156] ndiswrapper (load_wrap_driver:103): couldn't load driver bcmwl63; check system log for messages from 'loadndisdriver'
Sep 28 01:29:41 Mari kernel: [    2.138383] ndiswrapper (load_wrap_driver:103): couldn't load driver bcmwl63; check system log for messages from 'loadndisdriver'
Sep 28 01:51:23 Mari loadndisdriver: loadndisdriver: load_driver(364): couldn't load driver bcmwl63
Sep 28 01:51:23 Mari kernel: [    1.957687] ndiswrapper (load_wrap_driver:103): couldn't load driver bcmwl63; check system log for messages from 'loadndisdriver'
Sep 28 09:26:44 Mari kernel: [    2.072547] ndiswrapper (load_wrap_driver:103): couldn't load driver bcmwl63; check system log for messages from 'loadndisdriver'
Sep 28 09:28:53 Mari loadndisdriver: loadndisdriver: load_driver(364): couldn't load driver bcmwl63
Sep 28 09:28:53 Mari kernel: [  131.257938] ndiswrapper (load_wrap_driver:103): couldn't load driver bcmwl63; check system log for messages from 'loadndisdriver'
Sep 28 09:29:51 Mari loadndisdriver: loadndisdriver: load_driver(364): couldn't load driver bcmwl63
Sep 28 09:29:51 Mari kernel: [  188.969212] ndiswrapper (load_wrap_driver:103): couldn't load driver bcmwl63; check system log for messages from 'loadndisdriver'
Sep 28 09:30:19 Mari loadndisdriver: loadndisdriver: load_driver(364): couldn't load driver bcmwl63
Sep 28 09:30:19 Mari kernel: [  216.929602] ndiswrapper (load_wrap_driver:103): couldn't load driver bcmwl63; check system log for messages from 'loadndisdriver'
Sep 28 09:30:39 Mari loadndisdriver: loadndisdriver: load_driver(364): couldn't load driver bcmwl63
Sep 28 09:30:39 Mari kernel: [  237.231772] ndiswrapper (load_wrap_driver:103): couldn't load driver bcmwl63; check system log for messages from 'loadndisdriver'
Sep 28 09:32:06 Mari loadndisdriver: loadndisdriver: load_driver(364): couldn't load driver bcmwl63
Sep 28 09:32:06 Mari kernel: [  324.733866] ndiswrapper (load_wrap_driver:103): couldn't load driver bcmwl63; check system log for messages from 'loadndisdriver'
Sep 28 09:32:27 Mari loadndisdriver: loadndisdriver: load_driver(364): couldn't load driver bcmwl63
Sep 28 09:32:27 Mari kernel: [  345.757594] ndiswrapper (load_wrap_driver:103): couldn't load driver bcmwl63; check system log for messages from 'loadndisdriver'
Sep 28 09:32:54 Mari loadndisdriver: loadndisdriver: load_driver(364): couldn't load driver bcmwl63
Sep 28 09:32:54 Mari kernel: [  372.488458] ndiswrapper (load_wrap_driver:103): couldn't load driver bcmwl63; check system log for messages from 'loadndisdriver'
Sep 28 09:33:37 Mari loadndisdriver: loadndisdriver: load_driver(364): couldn't load driver bcmwl63
Sep 28 09:33:37 Mari kernel: [  415.424719] ndiswrapper (load_wrap_driver:103): couldn't load driver bcmwl63; check system log for messages from 'loadndisdriver'
Sep 28 11:10:53 Mari kernel: [    2.266781] ndiswrapper (load_wrap_driver:103): couldn't load driver bcmwl63; check system log for messages from 'loadndisdriver'
Sep 28 11:15:27 Mari loadndisdriver: loadndisdriver: load_driver(364): couldn't load driver bcmwl63
Sep 28 11:15:27 Mari kernel: [    2.306729] ndiswrapper (load_wrap_driver:103): couldn't load driver bcmwl63; check system log for messages from 'loadndisdriver'
root@Mari:~# dmesg | grep ndis
[    1.999558] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[    2.000551] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[    2.305674] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'strcat_s'
[    2.305681] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'RtlTimeToTimeFields'
[    2.305686] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'strcpy_s'
[    2.305690] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'_vsnprintf_s'
[    2.305694] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'_snprintf_s'
[    2.305700] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'ExGetFirmwareEnvironmentVariable'
[    2.305710] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'MmGetSystemRoutineAddress'
[    2.305751] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[    2.305755] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[    2.305760] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[    2.305764] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[    2.305772] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[    2.305779] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[    2.305784] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[    2.305788] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[    2.305792] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[    2.305796] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[    2.305801] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[    2.305805] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[    2.305812] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
[    2.305818] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[    2.305822] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[    2.305827] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMFreePort'
[    2.305831] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[    2.305837] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[    2.305841] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[    2.305845] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[    2.305850] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisCancelTimerObject'
[    2.305854] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisSetTimerObject'
[    2.305861] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[    2.305865] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeTimerObject'
[    2.305871] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateTimerObject'
[    2.305876] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[    2.305882] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[    2.305890] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[    2.305898] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[    2.305902] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[    2.305907] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[    2.305912] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[    2.305917] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[    2.305923] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[    2.305927] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMPauseComplete'
[    2.305929] ndiswrapper (load_sys_files:200): couldn't prepare driver 'bcmwl63'
[    2.306729] ndiswrapper (load_wrap_driver:103): couldn't load driver bcmwl63; check system log for messages from 'loadndisdriver'
[    2.341106] usbcore: registered new interface driver ndiswrapper
root@Mari:~# lsmod
Module                  Size  Used by
bbswitch               16384  0 
btusb                  40960  0 
uvcvideo               90112  0 
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_core         53248  1 uvcvideo
nvidia               8380416  35 
v4l2_common            16384  1 videobuf2_core
videodev              159744  3 uvcvideo,v4l2_common,videobuf2_core
media                  24576  2 uvcvideo,videodev
hid_multitouch         20480  0 
bnep                   20480  2 
rfcomm                 69632  8 
bluetooth             491520  22 bnep,btusb,rfcomm
snd_hda_codec_hdmi     53248  1 
snd_hda_codec_realtek    81920  1 
snd_hda_codec_generic    69632  1 snd_hda_codec_realtek
intel_rapl             20480  0 
iosf_mbi               16384  1 intel_rapl
x86_pkg_temp_thermal    16384  0 
intel_powerclamp       20480  0 
coretemp               16384  0 
kvm                   479232  0 
crct10dif_pclmul       16384  0 
crc32_pclmul           16384  0 
snd_hda_intel          32768  5 
ghash_clmulni_intel    16384  0 
snd_hda_controller     32768  1 snd_hda_intel
aesni_intel           172032  1 
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
i915                 1048576  4 
joydev                 20480  0 
snd_soc_rt5640         94208  0 
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          196608  1 snd_soc_rt5640
drm_kms_helper        126976  1 i915
snd_compress           20480  1 snd_soc_core
serio_raw              16384  0 
snd_pcm_dmaengine      16384  1 snd_soc_core
snd_hda_codec         143360  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              20480  1 snd_hda_codec
snd_seq_midi           16384  0 
lpc_ich                24576  0 
binfmt_misc            20480  1 
ndiswrapper           286720  0 
mei_me                 20480  0 
shpchp                 40960  0 
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
mei                    90112  1 mei_me
snd_seq_midi_event     16384  1 snd_seq_midi
drm                   344064  7 i915,drm_kms_helper,nvidia
i2c_algo_bit           16384  1 i915
snd_rawmidi            32768  1 snd_seq_midi
wmi                    20480  0 
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
nls_iso8859_1          16384  1 
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
ideapad_laptop         20480  0 
sparse_keymap          16384  1 ideapad_laptop
snd_timer              32768  2 snd_pcm,snd_seq
snd                    86016  23 snd_hda_codec_realtek,snd_soc_core,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_compress
video                  20480  1 i915
dw_dmac                16384  0 
soundcore              16384  2 snd,snd_hda_codec
i2c_hid                20480  0 
dw_dmac_core           24576  1 dw_dmac
spi_pxa2xx_platform    24576  0 
i2c_designware_platform    16384  0 
8250_dw                16384  0 
snd_soc_sst_acpi       16384  0 
i2c_designware_core    16384  1 i2c_designware_platform
mac_hid                16384  0 
acpi_pad               20480  0 
parport_pc             32768  0 
ppdev                  20480  0 
lp                     20480  0 
parport                45056  3 lp,ppdev,parport_pc
hid_generic            16384  0 
usbhid                 53248  0 
hid                   110592  4 i2c_hid,hid_multitouch,hid_generic,usbhid
psmouse               114688  0 
ahci                   36864  3 
r8169                  81920  0 
libahci                32768  1 ahci
mii                    16384  1 r8169
sdhci_acpi             16384  0 
sdhci                  45056  1 sdhci_acpi
root@Mari:~# 



---

### Post by praseodym on 2015-09-28
Try reinstalling the wrapper:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms ndisgtk ndiswrapper-dkms
```
Reboot.

---

### Post by aru2 on 2015-09-28
Ok, I did that and this was the result:

> root@Mari:~# sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms ndisgtk ndiswrapper-dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  apturl-common guile-2.0-libs libaudio2:i386 libcaca0:i386 libcurl3:i386
  libdevmapper1.02.1:i386 libevent-2.0-5 libgc1c2 libidn11:i386
  libmysqlclient18:i386 libnatpmp1 libpython2.7:i386 libpython2.7-minimal:i386
  libpython2.7-stdlib:i386 libqt4-declarative:i386 libqt4-network:i386
  libqt4-opengl:i386 libqt4-script:i386 libqt4-sql:i386 libqt4-sql-mysql:i386
  libqt4-xml:i386 libqt4-xmlpatterns:i386 libqtcore4:i386 libqtdbus4:i386
  libqtgui4:i386 libreadline6:i386 libreoffice-gtk librtmp0:i386
  libsdl1.2debian:i386 libxmu6:i386 mysql-common transmission-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 5 reinstalled, 0 to remove and 1 not upgraded.
Need to get 0 B/983 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 244641 files and directories currently installed.)
Preparing to unpack .../build-essential_11.6ubuntu6_amd64.deb ...
Unpacking build-essential (11.6ubuntu6) over (11.6ubuntu6) ...
Preparing to unpack .../dkms_2.2.0.3-1.1ubuntu5.14.04.2_all.deb ...
Unpacking dkms (2.2.0.3-1.1ubuntu5.14.04.2) over (2.2.0.3-1.1ubuntu5.14.04.2) ...
Preparing to unpack .../linux-headers-3.19.0-28-generic_3.19.0-28.30~14.04.1_amd64.deb ...
Unpacking linux-headers-3.19.0-28-generic (3.19.0-28.30~14.04.1) over (3.19.0-28.30~14.04.1) ...
Preparing to unpack .../ndisgtk_0.8.5-1ubuntu1_amd64.deb ...
Unpacking ndisgtk (0.8.5-1ubuntu1) over (0.8.5-1ubuntu1) ...
Preparing to unpack .../ndiswrapper-dkms_1.59-2_all.deb ...

-------- Uninstall Beginning --------
Module:  ndiswrapper
Version: 1.59
Kernel:  3.19.0-28-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

ndiswrapper.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-28-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.

------------------------------
Deleting module version: 1.59
completely from the DKMS tree.
------------------------------
Done.
Unpacking ndiswrapper-dkms (1.59-2) over (1.59-2) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Setting up build-essential (11.6ubuntu6) ...
Setting up dkms (2.2.0.3-1.1ubuntu5.14.04.2) ...
Setting up linux-headers-3.19.0-28-generic (3.19.0-28.30~14.04.1) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.19.0-28-generic /boot/vmlinuz-3.19.0-28-generic
Setting up ndisgtk (0.8.5-1ubuntu1) ...
Setting up ndiswrapper-dkms (1.59-2) ...
Loading new ndiswrapper-1.59 DKMS files...
Building only for 3.19.0-28-generic
Building initial module for 3.19.0-28-generic
Done.

ndiswrapper:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.19.0-28-generic/updates/dkms/

depmod....

DKMS: install completed.
root@Mari:~#

and then I rebooted and tried re-loading the drivers to memory with 
> [I]sudo depmod -a
sudo modprobe ndiswrapper[/I]

and then tried doing 
> [I]ip addr
iwconfig[/I]

and this was the result
> root@Mari:~# ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 54:ee:75:70:c9:15 brd ff:ff:ff:ff:ff:ff
    inet 10.0.0.6/24 brd 10.0.0.255 scope global eth0
       valid_lft forever preferred_lft forever
    inet6 2601:602:8d01:7780::c/128 scope global 
       valid_lft forever preferred_lft forever
    inet6 2601:602:8d01:7780:9d12:5279:603d:aaf9/64 scope global temporary dynamic 
       valid_lft 345593sec preferred_lft 84783sec
    inet6 2601:602:8d01:7780:56ee:75ff:fe70:c915/64 scope global dynamic 
       valid_lft 345593sec preferred_lft 345593sec
    inet6 fe80::56ee:75ff:fe70:c915/64 scope link 
       valid_lft forever preferred_lft forever
root@Mari:~# iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

root@Mari:~# 



so... still no go...

---

### Post by aru2 on 2015-09-28
I decided im not gonna take any more of broadcom's bulls#*t and im going to replace the wifi card with an intel ... 

I appreciate the help though... this whole experience was really good for starting with a deep dive on this new OS for me as i am new to linux. 
If anything at least i got that out of this.

Thank you!

---

### Post by jeremy31 on 2015-09-28
Get a card from Lenovo, or your computer may not boot with it installed.  Lenovo uses a BIOS whitelist in most of their laptops, I have a G710 and it wouldn't boot with a Intel 7260 I got on ebay but it wasn't advertised as being a Lenovo card

---

### Post by aru2 on 2015-09-28
Will do, thanks for the tip!

---

### Post by aru2 on 2015-09-30
Hi,

Just wanted to report my success... I bought myself this WIFI card and I couldn&#8217;t be happier... it worked right out of the box, no tinkering needed. 

If somebody with this same laptop is having this same issue just buy this wifi card and save yourself the trouble.

[URL="http://www.amazon.com/gp/product/B011XB19VS"]http://www.amazon.com/gp/product/B011XB19VS
[/URL]
Thanks!

---

