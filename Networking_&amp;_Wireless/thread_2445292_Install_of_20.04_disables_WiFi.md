---
title: "Install of 20.04 disables WiFi"
date: 2020-06-11
forum: Networking &amp; Wireless
---

### Post by jet-bundle on 2020-06-11
I have an HP Paviliion TS11 running Lubuntu 18.04, with a dongle for WiFi access (I couldn't get the built-in RT3290 to work). A couple of years ago, a kernel upgrade disabled WiFi, but I was given assistance in [https://ubuntuforums.org/showthread.php?t=2398249](https://ubuntuforums.org/showthread.php?t=2398249) by Jeremy31.

I have now arranged for this machine to boot Lubuntu 20.04 alongside 18.04, with kernels 4.5.0-106 and 5.4.0-26 respectively. The 18.04 system works fine, but not the 20.04 system (I tried downloading the software from the same address as before, [https://github.com/abperiasamy/rtl8812AU_8821AU_linux.git](https://github.com/abperiasamy/rtl8812AU_8821AU_linux.git), but presumably this isn't suitable for a 5.4 kernel).

I wonder if software for the series 5 kernels is available?

Thanks.

---

### Post by chili555 on 2020-06-11
This compiles cleanly on my 5.4.0-xx system: [https://github.com/gordboy/rtl8812au](https://github.com/gordboy/rtl8812au) 

Please post back if you need a step-by-step.

---

### Post by jet-bundle on 2020-06-12
Thank you. I downloaded the software and followed the instructions in the file README.md:
```

To use dkms install:

```sh
  (as root, or sudo) copy source folder contents to /usr/src/rtl8812au-5.2.20
```

```sh
$ sudo dkms add -m rtl8812au -v 5.2.20
$ sudo dkms build -m rtl8812au -v 5.2.20
$ sudo dkms install -m rtl8812au -v 5.2.20
```

```
There were no errors. I also noted that the README file contained a comment
```

### NetworkManager

As others have noted, people using NetworkManager need to add this stanza to /etc/NetworkManager/NetworkManager.conf

```sh
  [device]
  wifi.scan-rand-mac-address=no
```

```
but it was already there.

Unfortunately there's a problem. I found the following:
```

rfkill
ID TYPE DEVICE      SOFT    HARD
 0 wlan phy1   unblocked blocked

```
This was the problem I had with the built-in RT3290 adapter, and is the reason I'm using a dongle.

I'd be grateful for further advice; wireless-info is at [https://pastebin.com/RnVmGJC1](https://pastebin.com/RnVmGJC1).

PS I wonder whether the comment at the top of the README file is relevant:
```

# rtl8812au

## Realtek 8812AU driver version 5.2.20.2 ** NOW OBSOLETE **

**************************************************************************
Please use 5.6.4.2 version at https://github.com/gordboy/rtl8812au-5.6.4.2
**************************************************************************

```

---

### Post by chili555 on 2020-06-12
> 0 wlan phy1   unblocked blockedSince there is only one entry, we don't know if it is referring to the built-in, the USB or both. 

As the wireless drivers may conflict, I suggest that we blacklist the drivers for the built-in to see if it helps.

```
sudo -i
echo "blacklist rt2800pci"  >>  /etc/modprobe.d/blacklist.conf
echo "blacklist rt2x00pci"  >>  /etc/modprobe.d/blacklist.conf
exit

```Reboot and show us:

```
rfkill
dmesg | grep -e rtl -e rtw
```

> PS I wonder whether the comment at the top of the README file is relevant:
Code:
# rtl8812au

## Realtek 8812AU driver version 5.2.20.2 ** NOW OBSOLETE **However, the 5.2.20.2 version compiles for our 5.4.0-xx kernel versions. The 5.6.4.2 version does not:

> /home/chili/Desktop/Forum/gordboy/rtl8812au-5.6.4.2/include/../hal/phydm/phydm_precomp.h:270:11: fatal error: rtl8821a/halhwimg8821a_mac.h: No such file or directory
  270 |  #include "rtl8821a/halhwimg8821a_mac.h"
      |           ^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
compilation terminated.


---

### Post by jet-bundle on 2020-06-12
The response from rfkill came from the built-in adapter: I confirmed this by removing the dongle (sorry, I should have tried that earlier).

After blacklisting the built-in adapter, here is the response (I put the dongle back, of course):
```

~$ rfkill
~$ dmesg | grep -e rtl -e rtw
[   20.785103] rtl8812au: loading out-of-tree module taints kernel.
[   20.787518] rtl8812au: module verification failed: signature and/or required key missing - tainting kernel
[   20.794288] RTL871X: rtl8812au v4.3.14_13455.20150212_BTCOEX20150128-51
[   20.794291] RTL871X: rtl8812au BT-Coex version = BTCOEX20150128-51
[   21.441476] Modules linked in: uvcvideo rtl8812au(OE+) videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_common cfg80211 videodev amd_freq_sensitivity mc edac_mce_amd ccp snd_hda_codec_realtek kvm snd_hda_codec_generic ledtrig_audio snd_hda_codec_hdmi snd_hda_intel hid_multitouch snd_intel_dspcfg snd_hda_codec joydev input_leds hp_wmi wmi_bmof sparse_keymap snd_hda_core serio_raw rtsx_pci_ms snd_hwdep memstick k10temp fam15h_power snd_pcm snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq snd_seq_device snd_timer snd soundcore hp_accel lis3lv02d mac_hid input_polldev hp_wireless sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 btrfs xor zstd_compress raid6_pq libcrc32c dm_mirror dm_region_hash dm_log amdgpu amd_iommu_v2 gpu_sched crct10dif_pclmul crc32_pclmul ghash_clmulni_intel radeon i2c_algo_bit ttm rtsx_pci_sdmmc aesni_intel crypto_simd drm_kms_helper sdhci_pci syscopyarea cqhci cryptd glue_helper sysfillrect ahci sdhci sysimgblt i2c_piix4 libahci psmouse
[   21.441780]  ? _rtw_malloc+0x2d/0x2f [rtl8812au]
[   21.441856]  ? _rtw_memcpy+0x10/0x12 [rtl8812au]
[   21.441931]  ? rtw_5g_rates_init+0x1a/0x1c [rtl8812au]
[   21.442007]  ? rtw_spt_band_alloc+0xb0/0xb2 [rtl8812au]
[   21.442082]  rtw_wdev_alloc+0x107/0x2ad [rtl8812au]
[   21.442158]  rtw_usb_if1_init+0x138/0x205 [rtl8812au]
[   21.442233]  rtw_drv_init+0x23a/0x2c5 [rtl8812au]
[   21.442363]  rtw_drv_entry+0x86/0x1000 [rtl8812au]
[   21.593635] usbcore: registered new interface driver rtl8812au
~$
```
Should I follow this instruction from the README file?
```

### Regdb files

If needed, copy the regulatory database files in regdb/ to /lib/firmware/

```sh
$ sudo cp ./regdb/* /lib/firmware/
```

```

---

### Post by chili555 on 2020-06-12
> RTL871X: rtl8812au v[COLOR="#FF0000"]4.3.14[/COLOR]_13455.20150212_BTCOEX20150128-51I thought that you had successfully compiled version 5.2.20.2. Let's see what went wrong:

```
sudo dkms status
```

> Should I follow this instruction from the README file?
Code:
### Regdb files

If needed, copy the regulatory database files in regdb/ to /lib/firmware/

```sh
$ sudo cp ./regdb/* /lib/firmware/I don't believe it is needed here.

---

### Post by jet-bundle on 2020-06-12
```

rtl8812au, 4.3.14, 5.4.0-26-generic, x86_64: built
rtl8812au, 4.3.14, 5.4.0-37-generic, x86_64: installed
rtl8812au, 5.2.20, 5.4.0-26-generic, x86_64: installed

```
(The default boot is into 5.4.0-26, but that's an accidental consequence of the route I took to getting the machine to be set up as triple-boot with 18.04, 20.04 and Windows; I'll fix that in due course.)

So I guess the problem is that I installed the old version of rtl8812au, not realising that it wouldn't work with a 5.4 kernel, and that this is now conflicting with the new version? If so, how should I remove the old version?

---

### Post by chili555 on 2020-06-12
Please do:

```
sudo dkms remove rtl8812au/4.3.14 --all
```Reboot into 5.4.0-26 and let us see:

```
rfkill
dmesg | grep -e rtl -e rtw
```

---

### Post by jet-bundle on 2020-06-13
I've done that, and rebooted into 5.4.0-26; here's the result.
```

~$ sudo dkms status
rtl8812au, 5.2.20, 5.4.0-26-generic, x86_64: installed
~$ rfkill
~$ dmesg | grep -e rtl -e rtw
[   19.542194] rtl8812au: loading out-of-tree module taints kernel.
[   19.544771] rtl8812au: module verification failed: signature and/or required key missing - tainting kernel
[   19.551427] RTL871X: rtl8812au v4.3.14_13455.20150212_BTCOEX20150128-51
[   19.551430] RTL871X: rtl8812au BT-Coex version = BTCOEX20150128-51
[   20.188688] Modules linked in: snd_hda_intel videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 snd_intel_dspcfg videobuf2_common snd_hda_codec rtl8812au(OE+) videodev snd_hda_core snd_hwdep snd_pcm mc amd_freq_sensitivity cfg80211 edac_mce_amd snd_seq_midi snd_seq_midi_event ccp snd_rawmidi kvm snd_seq k10temp fam15h_power joydev hid_multitouch input_leds serio_raw hp_wmi snd_seq_device wmi_bmof rtsx_pci_ms snd_timer sparse_keymap memstick snd soundcore hp_accel lis3lv02d hp_wireless input_polldev mac_hid sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 btrfs xor zstd_compress raid6_pq libcrc32c dm_mirror dm_region_hash dm_log amdgpu amd_iommu_v2 gpu_sched crct10dif_pclmul crc32_pclmul ghash_clmulni_intel radeon aesni_intel i2c_algo_bit rtsx_pci_sdmmc crypto_simd ttm drm_kms_helper cryptd sdhci_pci syscopyarea sysfillrect psmouse cqhci glue_helper sysimgblt fb_sys_fops rtsx_pci sdhci drm i2c_piix4 ahci r8169 libahci realtek wmi video hid_logitech_hidpp hid_logitech_dj
[   20.188986]  ? _rtw_malloc+0x2d/0x2f [rtl8812au]
[   20.189062]  ? _rtw_memcpy+0x10/0x12 [rtl8812au]
[   20.189137]  ? rtw_5g_rates_init+0x1a/0x1c [rtl8812au]
[   20.189213]  ? rtw_spt_band_alloc+0xb0/0xb2 [rtl8812au]
[   20.189288]  rtw_wdev_alloc+0x107/0x2ad [rtl8812au]
[   20.189364]  rtw_usb_if1_init+0x138/0x205 [rtl8812au]
[   20.189439]  rtw_drv_init+0x23a/0x2c5 [rtl8812au]
[   20.189570]  rtw_drv_entry+0x86/0x1000 [rtl8812au]
[   20.339676] usbcore: registered new interface driver rtl8812au
~$

```

---

### Post by chili555 on 2020-06-13
> RTL871X: rtl8812au [COLOR="#FF0000"]v4.3.14[/COLOR]_13455.20150212_BTCOEX20150128-51A very interesting but puzzling result. May we see:

```
modinfo rtl8812au | grep version
modinfo 8812au | grep version
lsmod | grep 8812
sudo updatedb
locate 8812au.ko

```

---

### Post by jet-bundle on 2020-06-13
This is fascinating. I found the following:
```

~$ modinfo rtl8812au | grep version
version:        v4.3.14_13455.20150212_BTCOEX20150128-51
srcversion:     62D307B56D9BE4887112742
parm:           rtw_chip_version:int
~$ modinfo 8812au | grep version
version:        v5.2.20.2_28373.20180619
srcversion:     DDEECF1BBEBF84483F7E120
parm:           rtw_chip_version:int
~$ lsmod | grep 8812
rtl8812au            1347584  0
cfg80211              704512  1 rtl8812au
~$ sudo updatedb
sudo: updatedb: command not found
~$ sudo apt install mlocate

```
And then trying again:
```

~$ sudo updatedb
~$ locate 8812au.ko
/usr/lib/modules/5.4.0-26-generic/updates/dkms/8812au.ko
/usr/lib/modules/5.4.0-26-generic/updates/dkms/rtl8812au.ko
/var/lib/dkms/rtl8812au/5.2.20/5.4.0-26-generic/x86_64/module/8812au.ko
~$

```

---

### Post by chili555 on 2020-06-13
Please do:

```
sudo -i
echo "blacklist rtl8812au"  >>  /etc/modprobe.d/blacklist.conf
modprobe -r rtl8812au
modprobe 8812au
exit

```
Please note and post any errors. It might take a reboot.

---

### Post by jet-bundle on 2020-06-13
I did that, and there were no errors. Then I rebooted, and tried some of your earlier data-gathering suggestions again.
```

~$ rfkill
~$ sudo dkms status
rtl8812au, 5.2.20, 5.4.0-26-generic, x86_64: installed
~$ dmesg | grep -e rtl -e rtw
~$ modinfo rtl8812au | grep version
version:        v4.3.14_13455.20150212_BTCOEX20150128-51
srcversion:     62D307B56D9BE4887112742
parm:           rtw_chip_version:int
~$ modinfo 8812au | grep version
version:        v5.2.20.2_28373.20180619
srcversion:     DDEECF1BBEBF84483F7E120
parm:           rtw_chip_version:int
~$ lsmod | grep 8812
~$ sudo updatedb
~$ locate 8812au.ko
/usr/lib/modules/5.4.0-26-generic/updates/dkms/8812au.ko
/usr/lib/modules/5.4.0-26-generic/updates/dkms/rtl8812au.ko
/var/lib/dkms/rtl8812au/5.2.20/5.4.0-26-generic/x86_64/module/8812au.ko
~$

```
I see that [COLOR=#ff0000]dmesg | grep -e rtl -e rtw[/COLOR] now gives no result at all.

---

### Post by chili555 on 2020-06-13
What does this tell us?

```
sudo modprobe 8812au
dmesg | grep 8812
dmesg | grep -i rtl
```

---

### Post by jet-bundle on 2020-06-14
```

~$ sudo modprobe 8812au
~$ dmesg | grep 8812
[  161.517360] 8812au: loading out-of-tree module taints kernel.
[  161.521600] 8812au: module verification failed: signature and/or required key missing - tainting kernel
[  161.529527] usbcore: registered new interface driver rtl8812au
~$ dmesg | grep -i rtl
[    3.078038] r8169 0000:01:00.0 eth0: RTL8106e, a0:1d:48:0e:80:88, XID 449, IRQ 37
[   42.848813] RTL8208 Fast Ethernet r8169-100:00: attached PHY driver [RTL8208 Fast Ethernet] (mii_bus:phy_addr=r8169-100:00, irq=IGNORE)
[  161.529527] usbcore: registered new interface driver rtl8812au
~$

```

---

### Post by jet-bundle on 2020-06-20
I've taken the opportunity to investigate this a little further, by installing a second copy of Lubuntu 20.04 (that is, a genuine fresh copy on a new partition); I've also upgraded it to 5.4.0-37. This time, I didn't install the 4.3.14 version of the driver by mistake, and I also disabled the on-board WiFi adapter.
```

sudo -i
echo "blacklist rt2800pci"  >>  /etc/modprobe.d/blacklist.conf
echo "blacklist rt2x00pci"  >>  /etc/modprobe.d/blacklist.conf
exit

```
I then downloaded and compiled the 5.2.20 version of the driver. Here's the full compilation report.
```

$ sudo dkms build -m rtl8812au -v 5.2.20

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area...
'make' -j4 KVER=5.4.0-37-generic KSRC=/lib/modules/5.4.0-37-generic/build.............................................
Signing module:
Generating a new Secure Boot signing key:
Can't load /var/lib/shim-signed/mok/.rnd into RNG
139938584503616:error:2406F079:random number generator:RAND_load_file:Cannot open file:../crypto/rand/randfile.c:98:Filename=/var/lib/shim-signed/mok/.rnd
Generating a RSA private key
.........+++++
............+++++
writing new private key to '/var/lib/shim-signed/mok/MOK.priv'
-----
 - /var/lib/dkms/rtl8812au/5.2.20/5.4.0-37-generic/x86_64/module/8812au.ko
Secure Boot not enabled on this system.
cleaning build area...

DKMS: build completed.
$ sudo dkms install -m rtl8812au -v 5.2.20

8812au.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.4.0-37-generic/updates/dkms/

depmod..........

DKMS: install completed.
$ 

```
Is it significant that there's an error related to generating a secure boot signing key? (Secure boot is turned off.)

Still no WiFi after rebooting. Here are various reports.
```

$ rfkill
$ sudo dkms status
[sudo] password for david: 
rtl8812au, 5.2.20, 5.4.0-37-generic, x86_64: installed
$ dmesg | grep -e rtl -e rtw
$ modinfo rtl8812au | grep version
modinfo: ERROR: Module rtl8812au not found.
$ modinfo 8812au | grep version
version:        v5.2.20.2_28373.20180619
srcversion:     DDEECF1BBEBF84483F7E120
parm:           rtw_chip_version:int
$ lsmod | grep 8812
$ sudo updatedb
$ locate 8812au.ko
/usr/lib/modules/5.4.0-37-generic/updates/dkms/8812au.ko
/var/lib/dkms/rtl8812au/5.2.20/5.4.0-37-generic/x86_64/module/8812au.ko
$ sudo modprobe 8812au
$ dmesg | grep 8812
[ 9393.866505] 8812au: loading out-of-tree module taints kernel.
[ 9393.870449] 8812au: module verification failed: signature and/or required key missing - tainting kernel
[ 9393.882642] usbcore: registered new interface driver rtl8812au
$ dmesg | grep -i rtl
[    3.043292] r8169 0000:01:00.0 eth0: RTL8106e, a0:1d:48:0e:80:88, XID 449, IRQ 37
[   39.207642] RTL8208 Fast Ethernet r8169-100:00: attached PHY driver [RTL8208 Fast Ethernet] (mii_bus:phy_addr=r8169-100:00, irq=IGNORE)
[ 9393.882642] usbcore: registered new interface driver rtl8812au
$ 

```

---

### Post by chili555 on 2020-06-20
The driver in question doesn't actually cover your 0bda:a811 device. I am very sorry that I didn't catch it before today. Let's fix it:

```
sudo dkms remove rtl8812au/5.2.20 --all
git clone https://github.com/abperiasamy/rtl8812AU_8821AU_linux.git
cd rtl8812AU_8821AU_linux
sudo make -f Makefile.dkms install
```


Reboot.

This version compiles without any warnings or errors on my 5.4.0-xx system and reports:

```
$ modinfo rtl8812au.ko | grep A811
alias:          usb:v[COLOR="#FF0000"]0BDA[/COLOR]p[COLOR="#FF0000"]A811[/COLOR]d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDApA811d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392pA811d*dc*dsc*dp*ic*isc*ip*in*

```

---

### Post by jet-bundle on 2020-06-21
Thank you. That compiled with no signing error. Unfortunately the result wasn't successful:
```

$ rfkill
$ sudo dkms status
rtl8812au, 4.3.14, 5.4.0-37-generic, x86_64: installed
$ modinfo rtl8812au.ko | grep A811
modinfo: ERROR: Module rtl8812au.ko not found.

```
I notice that this appears to be version 4.3.14 (and indeed the compilation report confirms this)! In fact the source of the code, [https://github.com/abperiasamy/rtl8812AU_8821AU_linux.git](https://github.com/abperiasamy/rtl8812AU_8821AU_linux.git), is the same as the source of v4.3.14 which I installed originally by mistake (see post #1). Is this really the correct version?

---

### Post by chili555 on 2020-06-21
Please do:

```
sudo nano /etc/modprobe.d/blacklist.conf

```
Change the line:

```
blacklist rtl8812au
```

by commenting it out:

```
#blacklist rtl8812au
```Proofread carefully. Save (Ctrl+o followed by Enter) and exit (Ctrl+x). Now do:

```
sudo modprobe rtl8812au
dmesg | grep -i -e 8812 -e rtl

```
Please post the result.

---

### Post by jet-bundle on 2020-06-21
The file [COLOR=#ff0000]/etc/modprobe.d/blacklist.conf[/COLOR] doesn't contain a line [COLOR=#ff0000]blacklist rtl8812au[/COLOR]. For confirmation, here's the complete file:
```

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist rt2800pci
blacklist rt2x00pci

```
Here's the result of your request.
```

$ sudo modprobe rtl8812au
$ dmesg | grep -i -e 8812 -e rtl
[    3.076617] r8169 0000:01:00.0 eth0: RTL8106e, a0:1d:48:0e:80:88, XID 449, IRQ 39
[   20.034664] rtl8812au: loading out-of-tree module taints kernel.
[   20.036713] rtl8812au: module verification failed: signature and/or required key missing - tainting kernel
[   20.041852] RTL871X: module init start
[   20.041857] RTL871X: rtl8812au v4.3.14_13455.20150212_BTCOEX20150128-51
[   20.041858] RTL871X: rtl8812au BT-Coex version = BTCOEX20150128-51
[   20.632943] Modules linked in: snd_hda_core mc snd_hwdep rtl8812au(OE+) snd_pcm cfg80211 snd_seq_midi snd_seq_midi_event snd_rawmidi amd_freq_sensitivity snd_seq edac_mce_amd hid_multitouch rtsx_pci_ms ccp kvm snd_seq_device snd_timer memstick hp_wmi snd joydev input_leds k10temp serio_raw fam15h_power sparse_keymap hp_accel wmi_bmof soundcore lis3lv02d mac_hid hp_wireless input_polldev sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 btrfs xor zstd_compress raid6_pq libcrc32c dm_mirror dm_region_hash dm_log amdgpu amd_iommu_v2 gpu_sched crct10dif_pclmul crc32_pclmul ghash_clmulni_intel radeon rtsx_pci_sdmmc aesni_intel i2c_algo_bit ttm crypto_simd drm_kms_helper cryptd syscopyarea sdhci_pci glue_helper sysfillrect cqhci sysimgblt fb_sys_fops psmouse drm sdhci r8169 i2c_piix4 realtek ahci rtsx_pci libahci wmi hid_logitech_hidpp video hid_logitech_dj hid_generic usbhid hid
[   20.633163]  ? _rtw_malloc+0x2d/0x2f [rtl8812au]
[   20.633221]  ? _rtw_memcpy+0x10/0x12 [rtl8812au]
[   20.633279]  ? rtw_5g_rates_init+0x1a/0x1c [rtl8812au]
[   20.633337]  ? rtw_spt_band_alloc+0xb0/0xb2 [rtl8812au]
[   20.633396]  rtw_wdev_alloc+0x107/0x2ad [rtl8812au]
[   20.633455]  rtw_usb_if1_init+0x138/0x205 [rtl8812au]
[   20.633513]  rtw_drv_init+0x23a/0x2c5 [rtl8812au]
[   20.633626]  rtw_drv_entry+0x86/0x1000 [rtl8812au]
[   20.914783] usbcore: registered new interface driver rtl8812au
[   20.914788] RTL871X: module init ret=0
[   40.851914] RTL8208 Fast Ethernet r8169-100:00: attached PHY driver [RTL8208 Fast Ethernet] (mii_bus:phy_addr=r8169-100:00, irq=IGNORE)
$ 

```

---

### Post by chili555 on 2020-06-21
Once again, a very unhappy driver and hardware combination. Let's try a different version:

```
sudo dkms remove rtl8812au/4.3.14_13455.20150212_BTCOEX20150128-51 --all
git clone https://github.com/aircrack-ng/rtl8812au.git
cd rtl8812au
sudo ./dkms-install.sh
sudo modprobe 88XXau
```
Reboot and your wireless should now be working.

This version compiles cleanly on my 5.4.0-xx kernel version and covers your device. Its version is 5.6.4.2_35491.20191025.

Fingers crossed!

---

### Post by jet-bundle on 2020-06-21
Ha! It works! Thank you very much for your assistance. 

All I have to do now is to zap my other 20.04 partition (and to figure out why rEFInd lists the main kernel option for 20.04 as 5.4.0-26 rather than 5.4.0-37 when both are installed); but that can be for another day.

---

### Post by chili555 on 2020-06-21
Awesome! Glad it's working. Thanks for marking this Solved so that others can search for and benefit from our arduous journey!

---

