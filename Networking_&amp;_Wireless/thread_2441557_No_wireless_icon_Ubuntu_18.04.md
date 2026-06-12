---
title: "No wireless icon Ubuntu 18.04"
date: 2020-04-24
forum: Networking &amp; Wireless
---

### Post by SUPERFITTER on 2020-04-24
I was running version 16.04 and decided to update to version 18.04. 
After it was installed I ran update and upgrade, everything worked great.  
I rebooted and could not find the wireless icon, to enter my code. I have tried many solutions, but nothing works.

---

### Post by mörgæs on 2020-04-24
It would be more fair to both Ubuntuforum and Askubuntu if you selected one of them for your troubleshooting in stead of copy-pasting from one site to the other.

---

### Post by SUPERFITTER on 2020-04-26
The problem is there is no driver for my ASUS-N13 USB Dongle.  I will have to find a dongle that will work with Ubuntu 18.04 and the new version 20.04.  If you have any ideas please let us know.

---

### Post by chili555 on 2020-04-26
> The problem is there is no driver for my ASUS-N13 USB Dongle. Let's see if we can find one. Please run and post:```
lsusb
```...with the device inserted, of course.

---

### Post by SUPERFITTER on 2020-04-26
```
dennis@dennis1:~$ lsusb
Bus 002 Device 004: ID 046d:09a1 Logitech, Inc. QuickCam Communicate MP/S5500
Bus 002 Device 003: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 002: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 046d:c31c Logitech, Inc. Keyboard K120
Bus 001 Device 005: ID 0b05:17ab ASUSTek Computer, Inc. USB-N13 802.11n Network Adapter (rev. B1) [Realtek RTL8192CU]
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
dennis@dennis1:~$
```

---

### Post by chili555 on 2020-04-26
> 0b05:17ab ASUSTek Computer, Inc. USB-N13 802.11n Network Adapter (rev. B1) [Realtek RTL8192CU]Your device is covered by the driver rtl8192cu; it's already included in recent Ubuntu kernels. Did it load?

```
lsmod | grep rtl
```

If not, load it and see if there are any informative messages:

```
sudo modprobe rtl8192cu && dmesg | grep -i rtl
rfkill list all
```We probably only need to blacklist something.

---

### Post by SUPERFITTER on 2020-04-26
```
dennis@dennis1:~$ lsmod | grep rtl
dennis@dennis1:~$ sudo modprobe rtl8192cu && dmesg | grep -i rtl
[sudo] password for dennis: 
modprobe: ERROR: ../libkmod/libkmod-module.c:979 command_do() Error running install command for rtlwifi
modprobe: ERROR: could not insert 'rtl8192cu': Operation not permitted
dennis@dennis1:~$
```

---

### Post by chili555 on 2020-04-26
> ERROR: ../libkmod/libkmod-module.c:979 command_do() Error running install command for rtlwifiAh, haaa!

Let's see:

```
ls /etc/modprobe.d
```

If you have a file you added related to rtl, please show us the contents:

```
cat /etc/modprobe.d/some_file_rtl.conf
```

Or whatever you found.

---

### Post by SUPERFITTER on 2020-04-26
```
dennis@dennis1:~$ ls /etc/modprobe.d
alsa-base.conf                  blacklist-ath_pci.conf   blacklist-framebuffer.conf     blacklist-oss.conf           dkms.conf                       rtl8723de.conf
amd64-microcode-blacklist.conf  blacklist.conf           blacklist-modem.conf           blacklist-rare-network.conf  intel-microcode-blacklist.conf  vmwgfx-fbdev.conf
backports.conf                  blacklist-firewire.conf  blacklist-native-rtl8192.conf  blacklist-watchdog.conf      iwlwifi.conf
dennis@dennis1:~$ cat /etc/modprobe.d/some_file_rtl.conf
cat: /etc/modprobe.d/some_file_rtl.conf: No such file or directory
dennis@dennis1:~$
```

---

### Post by chili555 on 2020-04-26
May we see:

```
cat /etc/modprobe.d/blacklist-native-rtl8192.conf 
```

And also:

```
cat /etc/modprobe.d/rtl8723de.conf
```

And finally:

```
modinfo rtl8xxxu | grep 17AB
```

---

### Post by SUPERFITTER on 2020-04-26
dennis@dennis1:~$ cat /etc/modprobe.d/blacklist-native-rtl8192.conf
```
## This file ships with the rtl8192-fixes DKMS module.
## Keep the native (and currently broken) kernel driver from loading so ours
## is used instead:
install rtl8192cu /bin/false
install rtl8192c_common /bin/false
install rtlwifi /bin/false
## There is also a new mainline driver starting with kernel v4.4
install rtl8xxxu /bin/false
dennis@dennis1:~$ cat /etc/modprobe.d/rtl8723de.conf
options rtl8723de ant_sel=2
dennis@dennis1:~$ modinfo rtl8xxxu | grep 17AB
alias:          usb:v0B05p17ABd*dc*dsc*dp*icFFiscFFipFFin*
dennis@dennis1:~$
```

---

### Post by wildmanne39 on 2020-04-26
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by SUPERFITTER on 2020-04-26
Thank you wildmanne39

---

### Post by wildmanne39 on 2020-04-26
You're welcome.

---

### Post by chili555 on 2020-04-26
> This file ships with the rtl8192-fixes DKMS module.  Verrrry interesting. We're getting close. Let's see:

```
modinfo rtl8192cu | grep file
sudo dkms status
uname -r
```It appears, so far, that the "fixes" prevent anything at all from working!

---

### Post by SUPERFITTER on 2020-04-26
[COLOR=#000000] ```

[/COLOR]@dennis1:~$ modinfo rtl8192cu | grep file
filename:       /lib/modules/4.15.0-96-generic/updates/dkms/rtl8192cu.ko
dennis@dennis1:~$ sudo dkms status
[sudo] password for dennis: 
8192cu, 1.10, 4.4.0-177-generic, x86_64: installed
backport-iwlwifi, 8324, 4.15.0-96-generic, x86_64: installed (WARNING! Diff between built and installed module!) (WARNING! Diff between built and installed module!) (WARNING! Diff between built and installed module!) (WARNING! Diff between built and installed module!) (WARNING! Diff between built and installed module!) (WARNING! Diff between built and installed module!)
rtl8723de, 5.1.1.8_21285.20171026_COEX20170111-1414, 4.15.0-96-generic, x86_64: installed
rtlwifi-new, 0.6, 4.15.0-96-generic, x86_64: installed (WARNING! Diff between built and installed module!)
dennis@dennis1:~$ uname -r
4.15.0-96-generic
dennis@dennis1:~$ 
[COLOR=#000000] 
```[/COLOR]

---

### Post by chili555 on 2020-04-26
> 8192cu, 1.10, 4.4.0-177-generic, x86_64: installed
backport-iwlwifi, 8324, 4.15.0-96-generic, x86_64: installed (WARNING! Diff between built and installed module!) (WARNING! Diff between built and installed module!) (WARNING! Diff between built and installed module!) (WARNING! Diff between built and installed module!) (WARNING! Diff between built and installed module!) (WARNING! Diff between built and installed module!)
rtl8723de, 5.1.1.8_21285.20171026_COEX20170111-1414, 4.15.0-96-generic, x86_64: installed
rtlwifi-new, 0.6, 4.15.0-96-generic, x86_64: installed (WARNING! Diff between built and installed module!)YIKES!

While I sharpen up a few scalpels and put a fresh blade on my reciprcating saw, please tell us what the symptoms were that motivated you to do all this "fixing."

My inclination is to remove *all* and start fresh.

---

### Post by SUPERFITTER on 2020-04-26
I tried different methods that I found on youtube and the internet.  I guess I really messed up the computer.

Sorry I should have come here earlier.

---

### Post by chili555 on 2020-04-26
Again, what were your symptoms? Did your wireless not work at all? Did it work but was slow? Did it work but it wouldn't connect? Or...what?

---

### Post by jeremy31 on 2020-04-26
Lets see if some of this can be fixed
```
sudo dkms remove backport-iwlwifi/8324 --all
sudo dkms remove rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414 --all
sudo dkms remove rtlwifi-new/0.6 --all
```

Reboot

You might want to also post result for
```
mokutil --sb-state
```

---

### Post by SUPERFITTER on 2020-04-26
I had Ubuntu 16.04 and I did an update to 18.04. Everything worked except I had no wireless icon and no way to get on the internet, except run a cat 6 line from the basement router.

---

### Post by chili555 on 2020-04-26
I might just add a few things to Jeremy's post:

Please open a terminal and do:

```
sudo dkms remove 8192cu/1.10 --all
sudo dkms remove rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414 --all
sudo dkms remove rtlwifi-new/0.6 --all
sudo apt purge backport-iwlwifi-dkms
sudo rm /etc/modprobe.d/blacklist-native-rtl8192.conf
sudo rm /etc/modprobe.d/rtl8723de.conf
sudo -i
echo "blacklist rtl8192cu"  >>  /etc/modprobe.d/blacklist.conf
exit

```
Reboot.

---

### Post by SUPERFITTER on 2020-04-26
Do you want me to run jeremy31 codes?

---

### Post by SUPERFITTER on 2020-04-26
```
dennis@dennis1:~$ sudo dkms remove backport-iwlwifi/8324 --all[sudo] password for dennis: 


-------- Uninstall Beginning --------
Module:  backport-iwlwifi
Version: 8324
Kernel:  4.15.0-96-generic (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


compat.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.15.0-96-generic/
rmdir: failed to remove '': No such file or directory
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




iwlwifi.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.15.0-96-generic/
rmdir: failed to remove '': No such file or directory
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




iwlxvt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.15.0-96-generic/
rmdir: failed to remove '': No such file or directory
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




iwlmvm.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.15.0-96-generic/
rmdir: failed to remove '': No such file or directory
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




mac80211.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.15.0-96-generic/
rmdir: failed to remove '': No such file or directory
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




cfg80211.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.15.0-96-generic/
rmdir: failed to remove '': No such file or directory
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


depmod.......


DKMS: uninstall completed.


------------------------------
Deleting module version: 8324
completely from the DKMS tree.
------------------------------
Done.
dennis@dennis1:~$ sudo dkms remove rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414 --all


-------- Uninstall Beginning --------
Module:  rtl8723de
Version: 5.1.1.8_21285.20171026_COEX20170111-1414
Kernel:  4.15.0-96-generic (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


rtl8723de.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.15.0-96-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


depmod...


DKMS: uninstall completed.


------------------------------
Deleting module version: 5.1.1.8_21285.20171026_COEX20170111-1414
completely from the DKMS tree.
------------------------------
Done.
dennis@dennis1:~$ sudo dkms remove rtlwifi-new/0.6 --all


-------- Uninstall Beginning --------
Module:  rtlwifi-new
Version: 0.6
Kernel:  4.15.0-96-generic (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


rtl_pci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.15.0-96-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




rtl_usb.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.15.0-96-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




rtlwifi.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.15.0-96-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




btcoexist.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.15.0-96-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




halmac.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.15.0-96-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




phydm_mod.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.15.0-96-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




rtl8188ee.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.15.0-96-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




rtl8192c-common.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.15.0-96-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




rtl8192ce.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.15.0-96-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




rtl8192cu.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.15.0-96-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




rtl8192de.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.15.0-96-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




rtl8192ee.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.15.0-96-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




rtl8192se.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.15.0-96-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




rtl8723ae.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.15.0-96-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




rtl8723be.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.15.0-96-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




rtl8723de.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.15.0-96-generic/
rmdir: failed to remove '': No such file or directory
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




rtl8723-common.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.15.0-96-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




rtl8821ae.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.15.0-96-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




rtl8822be.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.15.0-96-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


depmod...


DKMS: uninstall completed.


------------------------------
Deleting module version: 0.6
completely from the DKMS tree.
------------------------------
Done.
dennis@dennis1:~$ 

```

---

### Post by SUPERFITTER on 2020-04-26
```
dennis@dennis1:~$ mokutil --sb-state

Command 'mokutil' not found, but can be installed with:


sudo apt install mokutil


dennis@dennis1:~$ sudo dkms remove 8192cu/1.10 --all
[sudo] password for dennis: 


-------- Uninstall Beginning --------
Module:  8192cu
Version: 1.10
Kernel:  4.4.0-177-generic (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


8192cu.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-177-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


depmod............


Backing up initrd.img-4.4.0-177-generic to /boot/initrd.img-4.4.0-177-generic.old-dkms
Making new initrd.img-4.4.0-177-generic
(If next boot fails, revert to initrd.img-4.4.0-177-generic.old-dkms image)
update-initramfs.......


DKMS: uninstall completed.


------------------------------
Deleting module version: 1.10
completely from the DKMS tree.
------------------------------
Done.
dennis@dennis1:~$ sudo dkms remove rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414 --all
Error! There are no instances of module: rtl8723de
5.1.1.8_21285.20171026_COEX20170111-1414 located in the DKMS tree.
dennis@dennis1:~$ sudo dkms remove rtlwifi-new/0.6 --all
Error! There are no instances of module: rtlwifi-new
0.6 located in the DKMS tree.
dennis@dennis1:~$ sudo apt purge backport-iwlwifi-dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  backport-iwlwifi-dkms*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 10.0 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 152350 files and directories currently installed.)
Removing backport-iwlwifi-dkms (8324-0ubuntu1~latest~ubuntu18.04.1) ...
dennis@dennis1:~$ sudo rm /etc/modprobe.d/blacklist-native-rtl8192.conf
dennis@dennis1:~$ sudo rm /etc/modprobe.d/rtl8723de.conf
dennis@dennis1:~$ sudo -i
root@dennis1:~# echo "blacklist rtl8192cu"  >>  /etc/modprobe.d/blacklist.conf
root@dennis1:~# exit 
```

---

### Post by chili555 on 2020-04-26
Now does the wireless work after a reboot?

---

### Post by SUPERFITTER on 2020-04-26
No

---

### Post by chili555 on 2020-04-26
> **SUPERFITTER said:**
> NoPlease show us:

```
sudo modprobe rtl8xxxu && dmesg | grep -i rtl
rfkill list all
```

---

### Post by SUPERFITTER on 2020-04-26
```
dennis@dennis1:~$ sudo modprobe rtl8xxxu && dmesg | grep -i rtl[sudo] password for dennis: 
[    1.026204] r8169 0000:07:00.0 eth0: RTL8168evl/8111evl at 0x        (ptrval), 50:e5:49:c4:df:a1, XID 0c900800 IRQ 26
[   24.978459] usb 1-1.4: rtl8192cu_parse_efuse: dumping efuse (0x80 bytes):
[   24.978472] usb 1-1.4: RTL8192CU rev A (TSMC) 2T2R, TX queues 2, WiFi=1, BT=0, GPS=0, HI PA=0
[   24.978473] usb 1-1.4: RTL8192CU MAC: 08:60:6e:cd:f6:1a
[   24.978474] usb 1-1.4: rtl8xxxu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[   25.598992] Modules linked in: snd_usb_audio(+) snd_usbmidi_lib snd_hda_codec_realtek snd_hda_codec_hdmi snd_hda_codec_generic snd_hda_intel s5h1409 snd_hda_codec snd_hda_core snd_hwdep tuner_simple tuner_types snd_pcm uvcvideo intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp videobuf2_vmalloc kvm_intel videobuf2_memops videobuf2_v4l2 kvm irqbypass crct10dif_pclmul crc32_pclmul ghash_clmulni_intel snd_seq_midi snd_seq_midi_event cs5345 joydev rtl8xxxu(+) mac80211(OE) cfg80211(OE) compat(OE) videobuf2_core pcbc snd_rawmidi tda9887 tda8290 input_leds aesni_intel tuner aes_x86_64 i915 nouveau snd_seq snd_seq_device mxm_wmi crypto_simd video glue_helper cryptd cx18(+) ttm videobuf_vmalloc drm_kms_helper snd_timer tveeprom cx2341x drm intel_cstate fb_sys_fops snd videobuf_core intel_rapl_perf
[   25.599067]  rtl8xxxu_probe+0xeac/0x1070 [rtl8xxxu]
[   25.599082]  rtl8xxxu_module_init+0x24/0x1000 [rtl8xxxu]
[   25.599118] usb 1-1.4: rtl8xxxu_probe: Failed to register: -22
[   25.599131] rtl8xxxu: probe of 1-1.4:1.0 failed with error -22
[   25.599149] usbcore: registered new interface driver rtl8xxxu
[  173.387454] usb 1-1.4: rtl8192cu_parse_efuse: dumping efuse (0x80 bytes):
[  173.387481] usb 1-1.4: RTL8192CU rev A (TSMC) 2T2R, TX queues 2, WiFi=1, BT=0, GPS=0, HI PA=0
[  173.387483] usb 1-1.4: RTL8192CU MAC: 08:60:6e:cd:f6:1a
[  173.387485] usb 1-1.4: rtl8xxxu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[  173.978750] Modules linked in: gpio_ich cx18_alsa mxl5005s snd_usb_audio snd_usbmidi_lib snd_hda_codec_realtek snd_hda_codec_hdmi snd_hda_codec_generic snd_hda_intel s5h1409 snd_hda_codec snd_hda_core snd_hwdep tuner_simple tuner_types snd_pcm uvcvideo intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp videobuf2_vmalloc kvm_intel videobuf2_memops videobuf2_v4l2 kvm irqbypass crct10dif_pclmul crc32_pclmul ghash_clmulni_intel snd_seq_midi snd_seq_midi_event cs5345 joydev rtl8xxxu mac80211(OE) cfg80211(OE) compat(OE) videobuf2_core pcbc snd_rawmidi tda9887 tda8290 input_leds aesni_intel tuner aes_x86_64 i915 nouveau snd_seq snd_seq_device mxm_wmi crypto_simd video glue_helper cryptd cx18 ttm videobuf_vmalloc drm_kms_helper snd_timer tveeprom cx2341x drm intel_cstate fb_sys_fops snd videobuf_core
[  173.978892]  rtl8xxxu_probe+0xeac/0x1070 [rtl8xxxu]
[  173.979011] usb 1-1.4: rtl8xxxu_probe: Failed to register: -22
[  173.979032] rtl8xxxu: probe of 1-1.4:1.0 failed with error -22
dennis@dennis1:~$ rfkill list all
dennis@dennis1:~$ 
```

---

### Post by chili555 on 2020-04-26
I will be off for the evening. I'll check in tomorrow.

---

### Post by SUPERFITTER on 2020-04-26
Thank you

---

### Post by chili555 on 2020-04-27
> [  173.979011] usb 1-1.4: rtl8xxxu_probe: Failed to register: -22
[  173.979032] rtl8xxxu: probe of 1-1.4:1.0 failed with error -22

Please try:

```
sudo modprobe -r rtl8xxxu

```
Now unplug the device and plug it in to a different USB port. Perhaps the device wants a USB3 port while it is now in a USB2 port or vice-versa. Now check:

```
dmesg | grep -i rtl
```

We are looking for the newest message entries; that is later than the timestamp 173.979032 above.

If the 'probe failed' still appears, let's try the alternate driver:

```
sudo nano /etc/modprobe.d/blacklist.conf
```

The last line should read:

```
blacklist rtl8192cu
```

Change it to read:

```
blacklist rtl8xxxu
```

Save (Ctrl+o followed by Enter) and exit (Ctrl+x) the text editor nano.

Reboot and show us:

```
dmesg | grep -i rtl
```

---

### Post by jeremy31 on 2020-04-27
Post results for ```
dkms status; modinfo compat
```
There must be backports installed yet as I see ```
mac80211(OE) cfg80211(OE) compat(OE)
```
The O means out of tree(not part of original kernel) and E means unsigned, modules that are part of the kernel are signed

---

### Post by SUPERFITTER on 2020-04-27
```
dennis@dennis1:~$ sudo modprobe -r rtl8xxxu[sudo] password for dennis: 
dennis@dennis1:~$ dmesg | grep -i rtl
[    1.031539] r8169 0000:07:00.0 eth0: RTL8168evl/8111evl at 0x        (ptrval), 50:e5:49:c4:df:a1, XID 0c900800 IRQ 26
[   17.867659] usb 1-1.4: rtl8192cu_parse_efuse: dumping efuse (0x80 bytes):
[   17.867671] usb 1-1.4: RTL8192CU rev A (TSMC) 2T2R, TX queues 2, WiFi=1, BT=0, GPS=0, HI PA=0
[   17.867672] usb 1-1.4: RTL8192CU MAC: 08:60:6e:cd:f6:1a
[   17.867673] usb 1-1.4: rtl8xxxu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[   18.555061] Modules linked in: crct10dif_pclmul crc32_pclmul ghash_clmulni_intel snd_hda_codec_hdmi pcbc cx18(+) uvcvideo videobuf_vmalloc videobuf2_vmalloc videobuf2_memops tveeprom videobuf2_v4l2 cx2341x videobuf2_core snd_hda_codec_realtek snd_hda_codec_generic snd_usb_audio snd_usbmidi_lib aesni_intel rtl8xxxu(+) videobuf_core aes_x86_64 dvb_core mac80211(OE) snd_hda_intel snd_hda_codec joydev input_leds cfg80211(OE) compat(OE) v4l2_common crypto_simd nouveau snd_hda_core videodev glue_helper media snd_hwdep mxm_wmi i915 ttm video cryptd drm_kms_helper snd_pcm snd_seq_midi snd_seq_midi_event drm snd_rawmidi snd_seq intel_cstate snd_seq_device intel_rapl_perf snd_timer serio_raw snd mei_me i2c_algo_bit fb_sys_fops syscopyarea soundcore mei shpchp lpc_ich sysfillrect sysimgblt wmi mac_hid sch_fq_codel
[   18.555133]  rtl8xxxu_probe+0xeac/0x1070 [rtl8xxxu]
[   18.555147]  rtl8xxxu_module_init+0x24/0x1000 [rtl8xxxu]
[   18.555185] usb 1-1.4: rtl8xxxu_probe: Failed to register: -22
[   18.555198] rtl8xxxu: probe of 1-1.4:1.0 failed with error -22
[   18.555221] usbcore: registered new interface driver rtl8xxxu
[ 2375.106745] usb 5-1: rtl8192cu_parse_efuse: dumping efuse (0x80 bytes):
[ 2375.106774] usb 5-1: RTL8192CU rev A (TSMC) 2T2R, TX queues 2, WiFi=1, BT=0, GPS=0, HI PA=0
[ 2375.106776] usb 5-1: RTL8192CU MAC: 08:60:6e:cd:f6:1a
[ 2375.106778] usb 5-1: rtl8xxxu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[ 2376.124754] Modules linked in: intel_rapl x86_pkg_temp_thermal intel_powerclamp gpio_ich cx18_alsa mxl5005s coretemp kvm_intel kvm s5h1409 tuner_simple tuner_types cs5345 tda9887 irqbypass tda8290 tuner crct10dif_pclmul crc32_pclmul ghash_clmulni_intel snd_hda_codec_hdmi pcbc cx18 uvcvideo videobuf_vmalloc videobuf2_vmalloc videobuf2_memops tveeprom videobuf2_v4l2 cx2341x videobuf2_core snd_hda_codec_realtek snd_hda_codec_generic snd_usb_audio snd_usbmidi_lib aesni_intel rtl8xxxu videobuf_core aes_x86_64 dvb_core mac80211(OE) snd_hda_intel snd_hda_codec joydev input_leds cfg80211(OE) compat(OE) v4l2_common crypto_simd nouveau snd_hda_core videodev glue_helper media snd_hwdep mxm_wmi i915 ttm video cryptd drm_kms_helper snd_pcm snd_seq_midi snd_seq_midi_event drm snd_rawmidi snd_seq intel_cstate snd_seq_device
[ 2376.124897]  rtl8xxxu_probe+0xeac/0x1070 [rtl8xxxu]
[ 2376.125018] usb 5-1: rtl8xxxu_probe: Failed to register: -22
[ 2376.125038] rtl8xxxu: probe of 5-1:1.0 failed with error -22
[ 2382.210654] usb 5-1: rtl8192cu_parse_efuse: dumping efuse (0x80 bytes):
[ 2382.210684] usb 5-1: RTL8192CU rev A (TSMC) 2T2R, TX queues 2, WiFi=1, BT=0, GPS=0, HI PA=0
[ 2382.210686] usb 5-1: RTL8192CU MAC: 08:60:6e:cd:f6:1a
[ 2382.210688] usb 5-1: rtl8xxxu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[ 2383.228665] Modules linked in: intel_rapl x86_pkg_temp_thermal intel_powerclamp gpio_ich cx18_alsa mxl5005s coretemp kvm_intel kvm s5h1409 tuner_simple tuner_types cs5345 tda9887 irqbypass tda8290 tuner crct10dif_pclmul crc32_pclmul ghash_clmulni_intel snd_hda_codec_hdmi pcbc cx18 uvcvideo videobuf_vmalloc videobuf2_vmalloc videobuf2_memops tveeprom videobuf2_v4l2 cx2341x videobuf2_core snd_hda_codec_realtek snd_hda_codec_generic snd_usb_audio snd_usbmidi_lib aesni_intel rtl8xxxu videobuf_core aes_x86_64 dvb_core mac80211(OE) snd_hda_intel snd_hda_codec joydev input_leds cfg80211(OE) compat(OE) v4l2_common crypto_simd nouveau snd_hda_core videodev glue_helper media snd_hwdep mxm_wmi i915 ttm video cryptd drm_kms_helper snd_pcm snd_seq_midi snd_seq_midi_event drm snd_rawmidi snd_seq intel_cstate snd_seq_device
[ 2383.228811]  rtl8xxxu_probe+0xeac/0x1070 [rtl8xxxu]
[ 2383.228931] usb 5-1: rtl8xxxu_probe: Failed to register: -22
[ 2383.228952] rtl8xxxu: probe of 5-1:1.0 failed with error -22
[ 2420.534576] usbcore: deregistering interface driver rtl8xxxu
[ 2438.935519] usb 5-1: rtl8192cu_parse_efuse: dumping efuse (0x80 bytes):
[ 2438.935549] usb 5-1: RTL8192CU rev A (TSMC) 2T2R, TX queues 2, WiFi=1, BT=0, GPS=0, HI PA=0
[ 2438.935551] usb 5-1: RTL8192CU MAC: 08:60:6e:cd:f6:1a
[ 2438.935553] usb 5-1: rtl8xxxu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[ 2439.952510] Modules linked in: rtl8xxxu(+) mac80211(OE) cfg80211(OE) compat(OE) intel_rapl x86_pkg_temp_thermal intel_powerclamp gpio_ich cx18_alsa mxl5005s coretemp kvm_intel kvm s5h1409 tuner_simple tuner_types cs5345 tda9887 irqbypass tda8290 tuner crct10dif_pclmul crc32_pclmul ghash_clmulni_intel snd_hda_codec_hdmi pcbc cx18 uvcvideo videobuf_vmalloc videobuf2_vmalloc videobuf2_memops tveeprom videobuf2_v4l2 cx2341x videobuf2_core snd_hda_codec_realtek snd_hda_codec_generic snd_usb_audio snd_usbmidi_lib aesni_intel videobuf_core aes_x86_64 dvb_core snd_hda_intel snd_hda_codec joydev input_leds v4l2_common crypto_simd nouveau snd_hda_core videodev glue_helper media snd_hwdep mxm_wmi i915 ttm video cryptd drm_kms_helper snd_pcm snd_seq_midi snd_seq_midi_event drm snd_rawmidi snd_seq intel_cstate
[ 2439.952659]  rtl8xxxu_probe+0xeac/0x1070 [rtl8xxxu]
[ 2439.952695]  rtl8xxxu_module_init+0x24/0x1000 [rtl8xxxu]
[ 2439.952777] usb 5-1: rtl8xxxu_probe: Failed to register: -22
[ 2439.952799] rtl8xxxu: probe of 5-1:1.0 failed with error -22
[ 2439.952841] usbcore: registered new interface driver rtl8xxxu
dennis@dennis1:~$ sudo nano /etc/modprobe.d/blacklist.conf
dennis@dennis1:~$ 
```

---

### Post by SUPERFITTER on 2020-04-27
```
dennis@dennis1:~$ sudo modprobe -r rtl8xxxu<div>[sudo] password for dennis:&nbsp;</div><div>dennis@dennis1:~$ dmesg | grep -i rtl</div><div>[&nbsp; &nbsp; 1.031539] r8169 0000:07:00.0 eth0: RTL8168evl/8111evl at 0x&nbsp; &nbsp; &nbsp; &nbsp; (ptrval), 50:e5:49:c4:df:a1, XID 0c900800 IRQ 26</div><div>[&nbsp; &nbsp;17.867659] usb 1-1.4: rtl8192cu_parse_efuse: dumping efuse (0x80 bytes):</div><div>[&nbsp; &nbsp;17.867671] usb 1-1.4: RTL8192CU rev A (TSMC) 2T2R, TX queues 2, WiFi=1, BT=0, GPS=0, HI PA=0</div><div>[&nbsp; &nbsp;17.867672] usb 1-1.4: RTL8192CU MAC: 08:60:6e:cd:f6:1a</div><div>[&nbsp; &nbsp;17.867673] usb 1-1.4: rtl8xxxu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin</div><div>[&nbsp; &nbsp;18.555061] Modules linked in: crct10dif_pclmul crc32_pclmul ghash_clmulni_intel snd_hda_codec_hdmi pcbc cx18(+) uvcvideo videobuf_vmalloc videobuf2_vmalloc videobuf2_memops tveeprom videobuf2_v4l2 cx2341x videobuf2_core snd_hda_codec_realtek snd_hda_codec_generic snd_usb_audio snd_usbmidi_lib aesni_intel rtl8xxxu(+) videobuf_core aes_x86_64 dvb_core mac80211(OE) snd_hda_intel snd_hda_codec joydev input_leds cfg80211(OE) compat(OE) v4l2_common crypto_simd nouveau snd_hda_core videodev glue_helper media snd_hwdep mxm_wmi i915 ttm video cryptd drm_kms_helper snd_pcm snd_seq_midi snd_seq_midi_event drm snd_rawmidi snd_seq intel_cstate snd_seq_device intel_rapl_perf snd_timer serio_raw snd mei_me i2c_algo_bit fb_sys_fops syscopyarea soundcore mei shpchp lpc_ich sysfillrect sysimgblt wmi mac_hid sch_fq_codel</div><div>[&nbsp; &nbsp;18.555133]&nbsp; rtl8xxxu_probe+0xeac/0x1070 [rtl8xxxu]</div><div>[&nbsp; &nbsp;18.555147]&nbsp; rtl8xxxu_module_init+0x24/0x1000 [rtl8xxxu]</div><div>[&nbsp; &nbsp;18.555185] usb 1-1.4: rtl8xxxu_probe: Failed to register: -22</div><div>[&nbsp; &nbsp;18.555198] rtl8xxxu: probe of 1-1.4:1.0 failed with error -22</div><div>[&nbsp; &nbsp;18.555221] usbcore: registered new interface driver rtl8xxxu</div><div>[ 2375.106745] usb 5-1: rtl8192cu_parse_efuse: dumping efuse (0x80 bytes):</div><div>[ 2375.106774] usb 5-1: RTL8192CU rev A (TSMC) 2T2R, TX queues 2, WiFi=1, BT=0, GPS=0, HI PA=0</div><div>[ 2375.106776] usb 5-1: RTL8192CU MAC: 08:60:6e:cd:f6:1a</div><div>[ 2375.106778] usb 5-1: rtl8xxxu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin</div><div>[ 2376.124754] Modules linked in: intel_rapl x86_pkg_temp_thermal intel_powerclamp gpio_ich cx18_alsa mxl5005s coretemp kvm_intel kvm s5h1409 tuner_simple tuner_types cs5345 tda9887 irqbypass tda8290 tuner crct10dif_pclmul crc32_pclmul ghash_clmulni_intel snd_hda_codec_hdmi pcbc cx18 uvcvideo videobuf_vmalloc videobuf2_vmalloc videobuf2_memops tveeprom videobuf2_v4l2 cx2341x videobuf2_core snd_hda_codec_realtek snd_hda_codec_generic snd_usb_audio snd_usbmidi_lib aesni_intel rtl8xxxu videobuf_core aes_x86_64 dvb_core mac80211(OE) snd_hda_intel snd_hda_codec joydev input_leds cfg80211(OE) compat(OE) v4l2_common crypto_simd nouveau snd_hda_core videodev glue_helper media snd_hwdep mxm_wmi i915 ttm video cryptd drm_kms_helper snd_pcm snd_seq_midi snd_seq_midi_event drm snd_rawmidi snd_seq intel_cstate snd_seq_device</div><div>[ 2376.124897]&nbsp; rtl8xxxu_probe+0xeac/0x1070 [rtl8xxxu]</div><div>[ 2376.125018] usb 5-1: rtl8xxxu_probe: Failed to register: -22</div><div>[ 2376.125038] rtl8xxxu: probe of 5-1:1.0 failed with error -22</div><div>[ 2382.210654] usb 5-1: rtl8192cu_parse_efuse: dumping efuse (0x80 bytes):</div><div>[ 2382.210684] usb 5-1: RTL8192CU rev A (TSMC) 2T2R, TX queues 2, WiFi=1, BT=0, GPS=0, HI PA=0</div><div>[ 2382.210686] usb 5-1: RTL8192CU MAC: 08:60:6e:cd:f6:1a</div><div>[ 2382.210688] usb 5-1: rtl8xxxu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin</div><div>[ 2383.228665] Modules linked in: intel_rapl x86_pkg_temp_thermal intel_powerclamp gpio_ich cx18_alsa mxl5005s coretemp kvm_intel kvm s5h1409 tuner_simple tuner_types cs5345 tda9887 irqbypass tda8290 tuner crct10dif_pclmul crc32_pclmul ghash_clmulni_intel snd_hda_codec_hdmi pcbc cx18 uvcvideo videobuf_vmalloc videobuf2_vmalloc videobuf2_memops tveeprom videobuf2_v4l2 cx2341x videobuf2_core snd_hda_codec_realtek snd_hda_codec_generic snd_usb_audio snd_usbmidi_lib aesni_intel rtl8xxxu videobuf_core aes_x86_64 dvb_core mac80211(OE) snd_hda_intel snd_hda_codec joydev input_leds cfg80211(OE) compat(OE) v4l2_common crypto_simd nouveau snd_hda_core videodev glue_helper media snd_hwdep mxm_wmi i915 ttm video cryptd drm_kms_helper snd_pcm snd_seq_midi snd_seq_midi_event drm snd_rawmidi snd_seq intel_cstate snd_seq_device</div><div>[ 2383.228811]&nbsp; rtl8xxxu_probe+0xeac/0x1070 [rtl8xxxu]</div><div>[ 2383.228931] usb 5-1: rtl8xxxu_probe: Failed to register: -22</div><div>[ 2383.228952] rtl8xxxu: probe of 5-1:1.0 failed with error -22</div><div>[ 2420.534576] usbcore: deregistering interface driver rtl8xxxu</div><div>[ 2438.935519] usb 5-1: rtl8192cu_parse_efuse: dumping efuse (0x80 bytes):</div><div>[ 2438.935549] usb 5-1: RTL8192CU rev A (TSMC) 2T2R, TX queues 2, WiFi=1, BT=0, GPS=0, HI PA=0</div><div>[ 2438.935551] usb 5-1: RTL8192CU MAC: 08:60:6e:cd:f6:1a</div><div>[ 2438.935553] usb 5-1: rtl8xxxu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin</div><div>[ 2439.952510] Modules linked in: rtl8xxxu(+) mac80211(OE) cfg80211(OE) compat(OE) intel_rapl x86_pkg_temp_thermal intel_powerclamp gpio_ich cx18_alsa mxl5005s coretemp kvm_intel kvm s5h1409 tuner_simple tuner_types cs5345 tda9887 irqbypass tda8290 tuner crct10dif_pclmul crc32_pclmul ghash_clmulni_intel snd_hda_codec_hdmi pcbc cx18 uvcvideo videobuf_vmalloc videobuf2_vmalloc videobuf2_memops tveeprom videobuf2_v4l2 cx2341x videobuf2_core snd_hda_codec_realtek snd_hda_codec_generic snd_usb_audio snd_usbmidi_lib aesni_intel videobuf_core aes_x86_64 dvb_core snd_hda_intel snd_hda_codec joydev input_leds v4l2_common crypto_simd nouveau snd_hda_core videodev glue_helper media snd_hwdep mxm_wmi i915 ttm video cryptd drm_kms_helper snd_pcm snd_seq_midi snd_seq_midi_event drm snd_rawmidi snd_seq intel_cstate</div><div>[ 2439.952659]&nbsp; rtl8xxxu_probe+0xeac/0x1070 [rtl8xxxu]</div><div>[ 2439.952695]&nbsp; rtl8xxxu_module_init+0x24/0x1000 [rtl8xxxu]</div><div>[ 2439.952777] usb 5-1: rtl8xxxu_probe: Failed to register: -22</div><div>[ 2439.952799] rtl8xxxu: probe of 5-1:1.0 failed with error -22</div><div>[ 2439.952841] usbcore: registered new interface driver rtl8xxxu</div><div>dennis@dennis1:~$ sudo nano /etc/modprobe.d/blacklist.conf</div><div>dennis@dennis1:~$ 
```</div><div><br></div>

---

### Post by SUPERFITTER on 2020-04-27
```
dennis@dennis1:~$ dmesg | grep -i rtl[    1.027856] r8169 0000:07:00.0 eth0: RTL8168evl/8111evl at 0x        (ptrval), 50:e5:49:c4:df:a1, XID 0c900800 IRQ 27
dennis@dennis1:~$ clear


dennis@dennis1:~$ dkms status; modinfo compat
filename:       /lib/modules/4.15.0-96-generic/updates/compat/compat.ko
version:        iwlwifi-stack-public:master:8324:9176b151
license:        GPL
description:    Kernel backport module
author:         Luis R. Rodriguez
license:        GPL
srcversion:     3C36367992F235399730CBD
depends:        
retpoline:      Y
name:           compat
vermagic:       4.15.0-96-generic SMP mod_unload 
parm:           backported_kernel_name:The kernel tree name that was used for this backport (iwlwifi) (charp)
parm:           backports_tracker_id:The version of the tree containing this backport (iwlwifi-stack-public:master:8324:9176b151) (charp)
dennis@dennis1:~$ mac80211(OE) cfg80211(OE) compat(OE)
bash: syntax error near unexpected token `OE'
dennis@dennis1:~$ 
```

---

### Post by jeremy31 on 2020-04-27
What about ```
ls | grep iwlwifi
```

---

### Post by SUPERFITTER on 2020-04-27
```
dennis@dennis1:~$ ls | grep iwlwifibackport-iwlwifi
dennis@dennis1:~$ 
```

---

### Post by jeremy31 on 2020-04-27
Try this
```
cd backport-iwlwifi
sudo make uninstall
```
Reboot, then see the wireless script link in my signature and post results

---

### Post by SUPERFITTER on 2020-04-27
```
dennis@dennis1:~$ cd backport-iwlwifidennis@dennis1:~/backport-iwlwifi$ sudo make uninstall
[sudo] password for dennis: 
  uninstall /lib/modules/4.15.0-96-generic/updates/drivers/net/wireless/intel/iwlwifi/xvt/iwlxvt.ko
  uninstall /lib/modules/4.15.0-96-generic/updates/drivers/net/wireless/intel/iwlwifi/mvm/iwlmvm.ko
  uninstall /lib/modules/4.15.0-96-generic/updates/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
  uninstall /lib/modules/4.15.0-96-generic/updates/compat/compat.ko
  uninstall /lib/modules/4.15.0-96-generic/updates/net/wireless/cfg80211.ko
  uninstall /lib/modules/4.15.0-96-generic/updates/net/mac80211/mac80211.ko
Note:
You may or may not need to update your initramfs, you should if
any of the modules installed are part of your initramfs. To add
support for your distribution to do this automatically send a
patch against "update-initramfs.sh". If your distribution does not
require this send a patch with the '/usr/bin/lsb_release -i -s'
("Ubuntu") tag for your distribution to avoid this warning.


Your backported driver modules should be uninstalled now.
Reboot.


dennis@dennis1:~/backport-iwlwifi$ 
```

---

### Post by SUPERFITTER on 2020-04-27
should I reboot?

---

### Post by jeremy31 on 2020-04-27
Yes, after reboot see the wireless script link in my signature if things are not working correctly

---

### Post by SUPERFITTER on 2020-04-27
Still not working

---

### Post by jeremy31 on 2020-04-27
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info
cat wireless-info.txt | nc termbin.com 9999
```
Post termbin URL

---

### Post by SUPERFITTER on 2020-04-27
```
dennis@dennis1:~$ wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info--2020-04-27 13:53:42--  https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info
Resolving github.com (github.com)... 140.82.112.3
Connecting to github.com (github.com)|140.82.112.3|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info [following]
--2020-04-27 13:53:42--  https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 199.232.76.133
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|199.232.76.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 17452 (17K) [text/plain]
Saving to: ‘wireless-info’


wireless-info                                        100%[=====================================================================================================================>]  17.04K  --.-KB/s    in 0.01s   


Last-modified header missing -- time-stamps turned off.
2020-04-27 13:53:43 (1.12 MB/s) - ‘wireless-info’ saved [17452/17452]


[sudo] password for dennis: 


Results saved in "/home/dennis/wireless-info.txt". 
```

---

### Post by SUPERFITTER on 2020-04-27
```
dennis@dennis1:~$ /home/dennis/wireless-info.txtbash: /home/dennis/wireless-info.txt: Permission denied 
```

---

### Post by jeremy31 on 2020-04-27
Now do ```
cat wireless-info.txt | nc termbin.com 9999
```
Post URL

---

### Post by SUPERFITTER on 2020-04-27
```
$ cat wireless-info.txt | nc termbin.com 9999https://termbin.com/mwon 
```

---

### Post by jeremy31 on 2020-04-27
Lets remove one driver from the blacklist
```
sudo sed -i 's/blacklist rtl8xxxu/#blacklist rtl8xxxu/' /etc/modprobe.d/blacklist.conf
```
Reboot
If no improvement run ```
./wireless-info && cat wireless-info.txt | nc termbin.com 9999
```

---

### Post by SUPERFITTER on 2020-04-27
jeremy 31

I ran the first command and rebooted, and now I have WIFI connection.  I rebooted 3 times and i am still connected.  

Thank you and Chilli555 very much for the help.  

One thing that I noticed is the flashing blue light from my ASUS N13 dongle is not flashing, no blue light at all.  The cone shaped WIFI signal is 2 bars and not 3 like it was before, but it is working.

I ran update and upgrade and rebooted, now I only have 1 bar on my WIFI cone.

---

### Post by jeremy31 on 2020-04-27
If you want to try the rtl8192cu 
```
sudo sed -i 's/#blacklist rtl8xxxu/blacklist rtl8xxxu/' /etc/modprobe.d/blacklist.conf
sudo sed -i 's/blacklist rtl8192cu/#blacklist rtl8192cu/' /etc/modprobe.d/blacklist.conf
```

Reboot and if the rtl8192cu doesn't work any better do
```
sudo sed -i 's/blacklist rtl8xxxu/#blacklist rtl8xxxu/' /etc/modprobe.d/blacklist.conf
sudo sed -i 's/#blacklist rtl8192cu/blacklist rtl8192cu/' /etc/modprobe.d/blacklist.conf
```

I think the biggest issue was the backport-iwlwifi as only some newer Intel wifi devices can work with it installed

---

### Post by SUPERFITTER on 2020-04-28
When I booted up I had 2 bars out of 3 then I ran both sets of code and rebooted between each.  
I got 2 bars with either set of codes. 
 I will try these for a couple of days to see if there are any changes.  

Thank you

---

