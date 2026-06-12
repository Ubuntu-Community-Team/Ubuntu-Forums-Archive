---
title: "No sound driver"
date: 2011-06-05
forum: New to Ubuntu
---

### Post by hoxzyk on 2011-06-05
Hello,

My Sounds drivers are not installed...

they are not coming up within sound preferences but the hardware is detected.

can anyone help me install snd-hda-intel....

Happy Regards,
Hoxy

---

### Post by jtarin on 2011-06-05
Enter into a terminal the command "lspci" and post the results. Then the command "lsmod" and post the results.Copy your results in the reply using "#" code tags.

---

### Post by LowSky on 2011-06-05
you should need to install any drivers, especially for intel sound. go into sound preferences, change the hardware profile, and test sound till it works.

---

### Post by hoxzyk on 2011-06-05
Ok i have added them below... but i can fix them by running 

```
sudo modprobe snd-hda-intel
```

but after a reboot they disappear... i will try again....

lspci

```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series]
01:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
7f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
7f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
7f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
7f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
7f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
7f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```lsmod
```

Module                  Size  Used by
cryptd                 20510  0 
aes_x86_64             17208  3 
aes_generic            38279  1 aes_x86_64
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   21708  1 
fat                    61374  1 vfat
ses                    17321  0 
binfmt_misc            17565  1 
enclosure              15217  1 ses
nfsd                  316512  11 
lockd                  85732  1 nfsd
nfs_acl                12883  1 nfsd
auth_rpcgss            52881  1 nfsd
sunrpc                234297  12 nfsd,lockd,nfs_acl,auth_rpcgss
exportfs               12998  1 nfsd
parport_pc             36959  0 
ppdev                  17113  0 
usb_storage            53538  2 
uas                    17996  0 
arc4                   12529  2 
ath9k                 120457  0 
joydev                 17606  0 
hp_wmi                 13706  0 
mac80211              302021  1 ath9k
sparse_keymap          13898  1 hp_wmi
ath9k_common           13839  1 ath9k
ath9k_hw              313028  2 ath9k,ath9k_common
i915                  514985  7 
ath                    23782  2 ath9k,ath9k_hw
uvcvideo               72195  0 
cfg80211              192234  3 ath9k,mac80211,ath
videodev               82052  1 uvcvideo
usbhid                 46956  0 
v4l2_compat_ioctl32    17078  1 videodev
fglrx                2786290  87 
hid                    91020  1 usbhid
psmouse                73535  0 
drm_kms_helper         42136  1 i915
hp_accel               21880  0 
serio_raw              13166  0 
drm                   227495  3 i915,drm_kms_helper
lis3lv02d              19893  1 hp_accel
intel_ips              18097  0 
i2c_algo_bit           13400  1 i915
input_polldev          14007  1 lis3lv02d
video                  19438  1 i915
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
ahci                   25951  2 
libahci                26642  1 ahci
r8169                  48022  0 

```

---

### Post by hoxzyk on 2011-06-05
The hardware doesn't show up in the sound preferences unless i run the previously posted code.....

---

### Post by jtarin on 2011-06-05
Try running the modprobe command without sudo.

---

### Post by hoxzyk on 2011-06-05
Nope......

```
WARNING: Error inserting soundcore (/lib/modules/2.6.38-8-generic/kernel/sound/soundcore.ko): Operation not permitted
WARNING: Error inserting snd (/lib/modules/2.6.38-8-generic/kernel/sound/core/snd.ko): Operation not permitted
WARNING: Error inserting snd_timer (/lib/modules/2.6.38-8-generic/kernel/sound/core/snd-timer.ko): Operation not permitted
WARNING: Error inserting snd_pcm (/lib/modules/2.6.38-8-generic/kernel/sound/core/snd-pcm.ko): Operation not permitted
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.38-8-generic/kernel/sound/core/snd-hwdep.ko): Operation not permitted
WARNING: Error inserting snd_hda_codec (/lib/modules/2.6.38-8-generic/kernel/sound/pci/hda/snd-hda-codec.ko): Operation not permitted
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.38-8-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Operation not permitted

```

---

### Post by jtarin on 2011-06-05
In a terminal ```
gksudo gedit /etc/rc.local
``` add the command there. That file is used for applications to start at user run-levels. You might have to try it several ways to launch. For modules I usually use "/sbln/insmod/nameofmodule"

---

### Post by hoxzyk on 2011-06-05
dunno how to add it.... ill have to look around coz should be able to install the freakin drivers.... not just run a command on login...

---

### Post by jtarin on 2011-06-05
Look at it this way....a command is run to load that module whether you write it or someone else does by script. Check this.
[http://ubuntuforums.org/showthread.php?t=1468048](http://ubuntuforums.org/showthread.php?t=1468048)

---

