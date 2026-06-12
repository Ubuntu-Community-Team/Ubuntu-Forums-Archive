---
title: "0bda:0811 Realtek Semiconductor Corp not working"
date: 2020-04-13
forum: Networking &amp; Wireless
---

### Post by Joe_Linux on 2020-04-13
I am using Ubuntu 18.04.4 LTS and the kernel is 5.3.0-46-generic. From the title I ran the lsusb command to find out the chipset on the usb 802.11ac wifi adapter. It does not function as a wifi adapter. I tried the solution listed in this link [https://askubuntu.com/questions/1076771/realtek-0bdaa811-wifi-driver-rtl8812au-on-ubuntu-18-04](https://askubuntu.com/questions/1076771/realtek-0bdaa811-wifi-driver-rtl8812au-on-ubuntu-18-04). Here are my results 
```
joe@joe-GA-78LMT-USB3:~$ git clone [https://github.com/abperiasamy/rtl8812AU_8821AU_linux.git](https://github.com/abperiasamy/rtl8812AU_8821AU_linux.git)
Cloning into 'rtl8812AU_8821AU_linux'...
remote: Enumerating objects: 1680, done.
remote: Total 1680 (delta 0), reused 0 (delta 0), pack-reused 1680
Receiving objects: 100% (1680/1680), 3.77 MiB | 2.09 MiB/s, done.
Resolving deltas: 100% (1042/1042), done.
joe@joe-GA-78LMT-USB3:~$ cd rtl8812AU_8821AU_linux
joe@joe-GA-78LMT-USB3:~/rtl8812AU_8821AU_linux$ sudo make -f Makefile.dkms install
[sudo] password for joe: 
make clean
make[1]: Entering directory '/home/joe/rtl8812AU_8821AU_linux'
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/5.3.0-46-generic/build M=/home/joe/rtl8812AU_8821AU_linux clean
make[2]: Entering directory '/usr/src/linux-headers-5.3.0-46-generic'
make[2]: Leaving directory '/usr/src/linux-headers-5.3.0-46-generic'
make[1]: Leaving directory '/home/joe/rtl8812AU_8821AU_linux'
mkdir -p '/usr/src/rtl8812au-4.3.14'
cp -r dkms.conf Kconfig Makefile.dkms Makefile platform core hal include os_dep '/usr/src/rtl8812au-4.3.14'
cp Makefile '/usr/src/rtl8812au-4.3.14/Makefile'
sed 's/#MODULE_VERSION#/4.3.14/' dkms.conf > '/usr/src/rtl8812au-4.3.14/dkms.conf'
dkms add -m rtl8812au -v 4.3.14 2>/dev/null || true
dkms build -m rtl8812au -v 4.3.14
Module rtl8812au/4.3.14 already built for kernel 5.3.0-46-generic/4
dkms install -m rtl8812au -v 4.3.14
Module rtl8812au/4.3.14 already installed on kernel 5.3.0-46-generic/x86_64
joe@joe-GA-78LMT-USB3:~/rtl8812AU_8821AU_linux$ sudo dkms status
rtl8812au, 4.3.14, 4.15.0-96-generic, x86_64: installed
rtl8812au, 4.3.14, 5.3.0-45-generic, x86_64: installed
rtl8812au, 4.3.14, 5.3.0-46-generic, x86_64: installed
joe@joe-GA-78LMT-USB3:~/rtl8812AU_8821AU_linux$
```


It still does not show up as a wifi adapter even though Module rtl8812au/4.3.14 already installed on kernel 5.3.0-46-generic/x86_64 any help would be appreciated. Just out curiosity will it be any better in Ubuntu 20.04 with a newer kernel ? Thanks again.

---

### Post by CelticWarrior on 2020-04-13
Please try again after disabling Secure Boot in UEFI ("BIOS").

Ubuntu 20.04 is newer but should make no difference in this case.

---

### Post by slickymaster on 2020-04-13
*Thread moved to **Networking & Wireless**.*

---

### Post by Joe_Linux on 2020-04-14
> **CelticWarrior said:**
> Please try again after disabling Secure Boot in UEFI ("BIOS").

Ubuntu 20.04 is newer but should make no difference in this case.

I have a GA-78LMT-USB3 motherboard with an award bios no secure boot feature because my bios is not uefi

---

### Post by morrownr on 2020-04-14
I also have a usb wifi adapter based on the rtl8812au chipset.

The driver I use is located here: [https://github.com/aircrack-ng/rtl8812au](https://github.com/aircrack-ng/rtl8812au)

This driver is well maintained.

---

### Post by CelticWarrior on 2020-04-14
> **Joe_Linux said:**
> I have a GA-78LMT-USB3 motherboard with an award bios no secure boot feature because my bios is not uefi

No BIOS is UEFI, no UEFI is BIOS... Let's get this out of the way. UEFI is what replaced BIOS, if you have one automatically you don't have the other. Now, some manufacturers still use the now wrong old terminology and Gigabyte (and Award, the actual firmware publisher) is one of them.

In your motherboard's [product page]("https://www.gigabyte.com/Motherboard/GA-78LMT-USB3-rev-60#ov") it's clearly stated: 
> Hybrid EFI technology with GIGABYTE DualBIOS&#8482;

So, it's UEFI, and unless you have the OS installed in Legacy/CSM - BTW, any UEFI system should be installed in UEFI mode -, Secure Boot IS relevant and likely to be enabled because that is the typical default.

Also of note, Gigabyte usually doesn't have an explicit "Secure Boot" setting. It's done via an obscure "OS selection" (or similar, I'm not sure) where Windows something = Secure Boot ON and Other = Secure Boot OFF.

---

### Post by chili555 on 2020-04-14
What does this tell us? 

```
sudo modprobe 8812au
dmesg | grep -i rtl
```

---

### Post by Joe_Linux on 2020-04-15
```
joe@joe-GA-78LMT-USB3:~$ sudo modprobe 8812au
[sudo] password for joe: 
joe@joe-GA-78LMT-USB3:~$ sudo modprobe 8812au
joe@joe-GA-78LMT-USB3:~$ dmesg | grep -i rtl
[    1.829249] r8169 0000:03:00.0 eth0: RTL8168evl/8111evl, 74:d4:35:99:c7:48, XID 2c9, IRQ 28
[    4.535301] RTL871X: module init start
[    4.535302] RTL871X: rtl8812au v4.3.8_12175.20140902
[    4.535303] RTL871X: build time: Apr 14 2020 12:40:03
[    4.535445] Modules linked in: 8812au(OE+) mac80211 mxm_wmi snd_hwdep crc32_pclmul video snd_pcm ghash_clmulni_intel ttm btusb snd_seq_midi drm_kms_helper btrtl snd_seq_midi_event btbcm libarc4 btintel cfg80211 input_leds drm aesni_intel snd_rawmidi bluetooth joydev i2c_algo_bit aes_x86_64 fb_sys_fops crypto_simd ecdh_generic syscopyarea snd_seq cryptd ecc sysfillrect glue_helper snd_seq_device sysimgblt snd_timer serio_raw wmi_bmof snd soundcore fam15h_power k10temp mac_hid sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 hid_generic usbhid hid pata_acpi pata_atiixp i2c_piix4 r8169 ahci realtek libahci wmi
[    4.642010] usbcore: registered new interface driver rtl8812au
[    4.642012] RTL871X: module init ret=0
[    4.721510] RTL871X: module init start
[    4.721512] RTL871X: rtl8812au v4.3.14_13455.20150212_BTCOEX20150128-51
[    4.721513] RTL871X: rtl8812au BT-Coex version = BTCOEX20150128-51
[    4.721525] Error: Driver 'rtl8812au' is already registered, aborting...
[    4.721530] RTL871X: module init ret=-16
[    6.017614] RTL8211E Gigabit Ethernet r8169-300:00: attached PHY driver [RTL8211E Gigabit Ethernet] (mii_bus:phy_addr=r8169-300:00, irq=IGNORE)
joe@joe-GA-78LMT-USB3:~$
```

---

### Post by Joe_Linux on 2020-04-15
I looked through the bios and bios manual and saw nothing about it sorrry :(

---

### Post by slickymaster on 2020-04-15
@Joe_Linux:

Please [use code tags]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") when posting output. Output posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand.

---

### Post by chili555 on 2020-04-15
Please also post:

```
rfkill list all
```

Which of the two modules loaded; 8812au or else rtl8812au? Or both??

```
lsmod | grep 8812
```

Also:

```
sudo dkms status
```

---

### Post by Joe_Linux on 2020-04-15
> **chili555 said:**
> What does this tell us? 

```
sudo modprobe 8812au
dmesg | grep -i rtl
```

```
 
[sudo] password for joe: 
joe@joe-GA-78LMT-USB3:~$ dmesg | grep -i rtl
[    1.791760] r8169 0000:03:00.0 eth0: RTL8168evl/8111evl, 74:d4:35:99:c7:48, XID 2c9, IRQ 28
[    4.319846] RTL871X: module init start
[    4.319848] RTL871X: rtl8812au v4.3.8_12175.20140902
[    4.319848] RTL871X: build time: Apr 14 2020 12:40:03
[    4.319985] Modules linked in: mxm_wmi btusb btrtl 8812au(OE+) video btbcm snd_rawmidi btintel ttm aes_x86_64 crypto_simd snd_seq bluetooth drm_kms_helper joydev drm cryptd ecdh_generic snd_seq_device i2c_algo_bit glue_helper ecc input_leds cfg80211 fb_sys_fops snd_timer syscopyarea sysfillrect sysimgblt serio_raw wmi_bmof snd soundcore fam15h_power mac_hid k10temp sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 hid_generic usbhid hid pata_acpi pata_atiixp r8169 ahci i2c_piix4 libahci realtek wmi
[    4.433030] usbcore: registered new interface driver rtl8812au
[    4.433031] RTL871X: module init ret=0
[    4.452919] RTL871X: module init start
[    4.452921] RTL871X: rtl8812au v4.3.14_13455.20150212_BTCOEX20150128-51
[    4.452922] RTL871X: rtl8812au BT-Coex version = BTCOEX20150128-51
[    4.452932] Error: Driver 'rtl8812au' is already registered, aborting...
[    4.452936] RTL871X: module init ret=-16
[    5.950949] RTL8211E Gigabit Ethernet r8169-300:00: attached PHY driver [RTL8211E Gigabit Ethernet] (mii_bus:phy_addr=r8169-300:00, irq=IGNORE)
joe@joe-GA-78LMT-USB3:~$ 

```

---

### Post by Joe_Linux on 2020-04-15
> **chili555 said:**
> Please also post:

```
rfkill list all
```

Which of the two modules loaded; 8812au or else rtl8812au? Or both??

```
lsmod | grep 8812
```

Also:

```
sudo dkms status
```

```

joe@joe-GA-78LMT-USB3:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
joe@joe-GA-78LMT-USB3:~$ 

``` 
```
 
joe@joe-GA-78LMT-USB3:~$ lsmod | grep 8812
8812au               1290240  0
cfg80211              704512  1 8812au
joe@joe-GA-78LMT-USB3:~$ 

```
```

joe@joe-GA-78LMT-USB3:~$ sudo dkms status
rtl8812au, 4.3.14, 4.15.0-96-generic, x86_64: installed
rtl8812au, 4.3.14, 5.3.0-45-generic, x86_64: installed
rtl8812au, 4.3.14, 5.3.0-46-generic, x86_64: built
rtl8812au, 4.3.8.12175.20140902+dfsg, 5.3.0-46-generic, x86_64: installed
joe@joe-GA-78LMT-USB3:~$ 

```

thank you

---

### Post by Joe_Linux on 2020-04-15
> **slickymaster said:**
> @Joe_Linux:

Please [use code tags]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") when posting output. Output posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand.

Thanks

---

### Post by chili555 on 2020-04-15
What is the result of:

```
sudo modprobe -r 8812au
sudo modprobe rtl8812au
dmesg | grep 8812
```

---

### Post by Joe_Linux on 2020-04-16
> **chili555 said:**
> What is the result of:

```
sudo modprobe -r 8812au
sudo modprobe rtl8812au
dmesg | grep 8812
```

```
 
sudo modprobe -r 8812au

```

```

joe@joe-GA-78LMT-USB3:~$ sudo modprobe -r 8812au
[sudo] password for joe: 
joe@joe-GA-78LMT-USB3:~$ 

```

```

sudo modprobe rtl8812au

```

```

joe@joe-GA-78LMT-USB3:~$ sudo modprobe rtl8812au
[sudo] password for joe: 
joe@joe-GA-78LMT-USB3:~$ 

```

```

dmesg | grep 8812

```

```

joe@joe-GA-78LMT-USB3:~$ dmesg | grep 8812
[    6.271249] 8812au: loading out-of-tree module taints kernel.
[    6.275059] 8812au: module verification failed: signature and/or required key missing - tainting kernel
[    6.282984] RTL871X: rtl8812au v4.3.8_12175.20140902
[    6.283190] Modules linked in: snd_seq_midi aes_x86_64 8812au(OE+) btusb snd_seq_midi_event crypto_simd mac80211 ttm btrtl snd_rawmidi cryptd btbcm glue_helper drm_kms_helper snd_seq btintel libarc4 cfg80211 drm bluetooth snd_seq_device snd_timer input_leds joydev ecdh_generic snd ecc i2c_algo_bit wmi_bmof fb_sys_fops syscopyarea sysfillrect serio_raw k10temp fam15h_power sysimgblt soundcore mac_hid sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 uas usb_storage hid_generic usbhid hid pata_acpi pata_atiixp r8169 i2c_piix4 ahci realtek libahci wmi
[    6.283301]  ? _rtw_malloc+0x2d/0x2f [8812au]
[    6.283332]  ? _rtw_memcpy+0x10/0x12 [8812au]
[    6.283363]  ? rtw_5g_rates_init+0x1a/0x1c [8812au]
[    6.283396]  rtw_wdev_alloc+0xf9/0x29f [8812au]
[    6.283428]  ? rtw_wdev_alloc+0xf9/0x29f [8812au]
[    6.283460]  rtw_usb_if1_init+0xf0/0x209 [8812au]
[    6.283492]  rtw_drv_init+0x244/0x2f7 [8812au]
[    6.283551]  rtw_drv_entry+0x65/0x1000 [8812au]
[    6.396641] usbcore: registered new interface driver rtl8812au
[    6.412393] RTL871X: rtl8812au v4.3.14_13455.20150212_BTCOEX20150128-51
[    6.412394] RTL871X: rtl8812au BT-Coex version = BTCOEX20150128-51
[    6.412403] Error: Driver 'rtl8812au' is already registered, aborting...
[ 3449.225538] usbcore: deregistering interface driver rtl8812au
[ 3686.694415] RTL871X: rtl8812au v4.3.14_13455.20150212_BTCOEX20150128-51
[ 3686.694416] RTL871X: rtl8812au BT-Coex version = BTCOEX20150128-51
[ 3686.842788] Modules linked in: rtl8812au(OE+) nls_iso8859_1 rfcomm ccm bnep snd_hda_codec_hdmi edac_mce_amd ccp kvm irqbypass snd_hda_codec_via snd_hda_codec_generic ledtrig_audio crct10dif_pclmul snd_hda_intel crc32_pclmul snd_intel_nhlt nouveau snd_hda_codec ghash_clmulni_intel snd_hda_core rt2800usb rt2x00usb snd_hwdep mxm_wmi rt2800lib snd_pcm aesni_intel rt2x00lib video snd_seq_midi aes_x86_64 btusb snd_seq_midi_event crypto_simd mac80211 ttm btrtl snd_rawmidi cryptd btbcm glue_helper drm_kms_helper snd_seq btintel libarc4 cfg80211 drm bluetooth snd_seq_device snd_timer input_leds joydev ecdh_generic snd ecc i2c_algo_bit wmi_bmof fb_sys_fops syscopyarea sysfillrect serio_raw k10temp fam15h_power sysimgblt soundcore mac_hid sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 uas usb_storage hid_generic usbhid hid pata_acpi pata_atiixp r8169 i2c_piix4 ahci realtek libahci wmi [last unloaded: 8812au]
[ 3686.842994]  ? _rtw_malloc+0x2d/0x2f [rtl8812au]
[ 3686.843057]  ? _rtw_memcpy+0x10/0x12 [rtl8812au]
[ 3686.843123]  ? rtw_5g_rates_init+0x1a/0x1c [rtl8812au]
[ 3686.843189]  rtw_wdev_alloc+0x10a/0x2b0 [rtl8812au]
[ 3686.843255]  ? rtw_wdev_alloc+0x10a/0x2b0 [rtl8812au]
[ 3686.843319]  rtw_usb_if1_init+0x138/0x202 [rtl8812au]
[ 3686.843388]  rtw_drv_init+0x23d/0x2d6 [rtl8812au]
[ 3686.843480]  rtw_drv_entry+0x86/0x1000 [rtl8812au]
[ 3686.958069] usbcore: registered new interface driver rtl8812au
joe@joe-GA-78LMT-USB3:~$ 

```

---

### Post by chili555 on 2020-04-16
It seems that your system doesn't like *either* version of the driver! Let's remove them both and install what I suspect is a better version. From the terminal:

```
sudo dkms remove rtl8812au/4.3.14 --all
sudo dkms remove rtl8812au/4.3.8.12175.20140902+dfsg --all
```

With a working internet connection by ethernet, tethering or whatever means possible, do:

```
git clone https://github.com/gordboy/rtl8812au.git
cd rtl8812au
sudo rsync -rvhP ./ /usr/src/rtl8812au-5.2.20
sudo dkms add -m rtl8812au -v 5.2.20
sudo dkms build -m rtl8812au -v 5.2.20
sudo dkms install -m rtl8812au -v 5.2.20
sudo modprobe 8812au
```

Any improvement?

---

### Post by Joe_Linux on 2020-04-16
No change sorry 
```

joe@joe-GA-78LMT-USB3:~$ sudo dkms remove rtl8812au/4.3.14 --all
[sudo] password for joe: 

-------- Uninstall Beginning --------
Module:  rtl8812au
Version: 4.3.14
Kernel:  4.15.0-96-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

rtl8812au.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.15.0-96-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod...

DKMS: uninstall completed.

-------- Uninstall Beginning --------
Module:  rtl8812au
Version: 4.3.14
Kernel:  5.3.0-45-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

rtl8812au.ko:
 - Uninstallation
   - Deleting from: /lib/modules/5.3.0-45-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.

-------- Uninstall Beginning --------
Module:  rtl8812au
Version: 4.3.14
Kernel:  5.3.0-46-generic (x86_64)
-------------------------------------

Status: This module version was INACTIVE for this kernel.
depmod...

DKMS: uninstall completed.

------------------------------
Deleting module version: 4.3.14
completely from the DKMS tree.
------------------------------
Done.
joe@joe-GA-78LMT-USB3:~$ sudo dkms remove rtl8812au/4.3.8.12175.20140902+dfsg --all

-------- Uninstall Beginning --------
Module:  rtl8812au
Version: 4.3.8.12175.20140902+dfsg
Kernel:  5.3.0-46-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

8812au.ko:
 - Uninstallation
   - Deleting from: /lib/modules/5.3.0-46-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod...

DKMS: uninstall completed.

------------------------------
Deleting module version: 4.3.8.12175.20140902+dfsg
completely from the DKMS tree.
------------------------------
Done.
joe@joe-GA-78LMT-USB3:~$ git clone https://github.com/gordboy/rtl8812au.git
Cloning into 'rtl8812au'...
remote: Enumerating objects: 18, done.
remote: Counting objects: 100% (18/18), done.
remote: Compressing objects: 100% (15/15), done.
remote: Total 874 (delta 3), reused 7 (delta 3), pack-reused 856
Receiving objects: 100% (874/874), 2.82 MiB | 2.12 MiB/s, done.
Resolving deltas: 100% (432/432), done.
joe@joe-GA-78LMT-USB3:~$ cd rtl8812au
joe@joe-GA-78LMT-USB3:~/rtl8812au$ sudo rsync -rvhP ./ /usr/src/rtl8812au-5.2.20
sending incremental file list
created directory /usr/src/rtl8812au-5.2.20
./
Kconfig
            110 100%    0.00kB/s    0:00:00 (xfr#1, to-chk=586/588)
Makefile
         58.49K 100%   55.78MB/s    0:00:00 (xfr#2, to-chk=585/588)
README.md
          2.23K 100%    2.13MB/s    0:00:00 (xfr#3, to-chk=584/588)
Realtek_Changelog.txt
          2.32K 100%    2.21MB/s    0:00:00 (xfr#4, to-chk=583/588)
clean
             64 100%   62.50kB/s    0:00:00 (xfr#5, to-chk=582/588)
dkms.conf
            316 100%  308.59kB/s    0:00:00 (xfr#6, to-chk=581/588)
ifcfg-wlan0
             51 100%   49.80kB/s    0:00:00 (xfr#7, to-chk=580/588)
runwpa
            415 100%  405.27kB/s    0:00:00 (xfr#8, to-chk=579/588)
wlan0dhcp
            294 100%  287.11kB/s    0:00:00 (xfr#9, to-chk=578/588)
.git/
.git/HEAD
             23 100%    0.75kB/s    0:00:00 (xfr#10, to-chk=570/588)
.git/config
            265 100%    8.63kB/s    0:00:00 (xfr#11, to-chk=569/588)
.git/description
             73 100%    2.38kB/s    0:00:00 (xfr#12, to-chk=568/588)
.git/index
         47.85K 100%    1.52MB/s    0:00:00 (xfr#13, to-chk=567/588)
.git/packed-refs
            114 100%    3.71kB/s    0:00:00 (xfr#14, to-chk=566/588)
.git/branches/
.git/hooks/
.git/hooks/applypatch-msg.sample
            478 100%   15.56kB/s    0:00:00 (xfr#15, to-chk=559/588)
.git/hooks/commit-msg.sample
            896 100%   29.17kB/s    0:00:00 (xfr#16, to-chk=558/588)
.git/hooks/fsmonitor-watchman.sample
          3.33K 100%  104.81kB/s    0:00:00 (xfr#17, to-chk=557/588)
.git/hooks/post-update.sample
            189 100%    5.95kB/s    0:00:00 (xfr#18, to-chk=556/588)
.git/hooks/pre-applypatch.sample
            424 100%   13.36kB/s    0:00:00 (xfr#19, to-chk=555/588)
.git/hooks/pre-commit.sample
          1.64K 100%   51.73kB/s    0:00:00 (xfr#20, to-chk=554/588)
.git/hooks/pre-push.sample
          1.35K 100%   42.46kB/s    0:00:00 (xfr#21, to-chk=553/588)
.git/hooks/pre-rebase.sample
          4.90K 100%  154.30kB/s    0:00:00 (xfr#22, to-chk=552/588)
.git/hooks/pre-receive.sample
            544 100%   17.14kB/s    0:00:00 (xfr#23, to-chk=551/588)
.git/hooks/prepare-commit-msg.sample
          1.49K 100%   47.00kB/s    0:00:00 (xfr#24, to-chk=550/588)
.git/hooks/update.sample
          3.61K 100%  113.72kB/s    0:00:00 (xfr#25, to-chk=549/588)
.git/info/
.git/info/exclude
            240 100%    7.56kB/s    0:00:00 (xfr#26, to-chk=548/588)
.git/logs/
.git/logs/HEAD
            193 100%    6.08kB/s    0:00:00 (xfr#27, to-chk=547/588)
.git/logs/refs/
.git/logs/refs/heads/
.git/logs/refs/heads/master
            193 100%    6.08kB/s    0:00:00 (xfr#28, to-chk=543/588)
.git/logs/refs/remotes/
.git/logs/refs/remotes/origin/
.git/logs/refs/remotes/origin/HEAD
            193 100%    6.08kB/s    0:00:00 (xfr#29, to-chk=541/588)
.git/objects/
.git/objects/info/
.git/objects/pack/
.git/objects/pack/pack-d0518b93d638d1dbe2dc8cabed9bb9fd81308c82.idx
         25.54K 100%  804.69kB/s    0:00:00 (xfr#30, to-chk=538/588)
.git/objects/pack/pack-d0518b93d638d1dbe2dc8cabed9bb9fd81308c82.pack
          2.96M 100%   58.84MB/s    0:00:00 (xfr#31, to-chk=537/588)
.git/refs/
.git/refs/heads/
.git/refs/heads/master
             41 100%    0.83kB/s    0:00:00 (xfr#32, to-chk=533/588)
.git/refs/remotes/
.git/refs/remotes/origin/
.git/refs/remotes/origin/HEAD
             32 100%    0.65kB/s    0:00:00 (xfr#33, to-chk=531/588)
.git/refs/tags/
core/
core/rtw_ap.c
        136.88K 100%    2.66MB/s    0:00:00 (xfr#34, to-chk=530/588)
core/rtw_beamforming.c
         90.06K 100%    1.75MB/s    0:00:00 (xfr#35, to-chk=529/588)
core/rtw_br_ext.c
         46.20K 100%  902.36kB/s    0:00:00 (xfr#36, to-chk=528/588)
core/rtw_bt_mp.c
         50.95K 100%  995.02kB/s    0:00:00 (xfr#37, to-chk=527/588)
core/rtw_btcoex.c
         49.02K 100%  957.44kB/s    0:00:00 (xfr#38, to-chk=526/588)
core/rtw_btcoex_wifionly.c
          1.17K 100%   22.79kB/s    0:00:00 (xfr#39, to-chk=525/588)
core/rtw_cmd.c
        130.73K 100%    2.44MB/s    0:00:00 (xfr#40, to-chk=524/588)
core/rtw_debug.c
        178.63K 100%    3.34MB/s    0:00:00 (xfr#41, to-chk=523/588)
core/rtw_eeprom.c
          8.26K 100%  158.16kB/s    0:00:00 (xfr#42, to-chk=522/588)
core/rtw_ieee80211.c
         69.65K 100%    1.28MB/s    0:00:00 (xfr#43, to-chk=521/588)
core/rtw_io.c
         19.31K 100%  362.61kB/s    0:00:00 (xfr#44, to-chk=520/588)
core/rtw_ioctl_query.c
          5.75K 100%  108.00kB/s    0:00:00 (xfr#45, to-chk=519/588)
core/rtw_ioctl_rtl.c
         30.13K 100%  565.84kB/s    0:00:00 (xfr#46, to-chk=518/588)
core/rtw_ioctl_set.c
         31.51K 100%  591.68kB/s    0:00:00 (xfr#47, to-chk=517/588)
core/rtw_iol.c
         10.88K 100%  204.38kB/s    0:00:00 (xfr#48, to-chk=516/588)
core/rtw_mem.c
          3.42K 100%   64.27kB/s    0:00:00 (xfr#49, to-chk=515/588)
core/rtw_mi.c
         41.70K 100%  768.43kB/s    0:00:00 (xfr#50, to-chk=514/588)
core/rtw_mlme.c
        147.79K 100%    2.61MB/s    0:00:00 (xfr#51, to-chk=513/588)
core/rtw_mlme_ext.c
        485.04K 100%    8.26MB/s    0:00:00 (xfr#52, to-chk=512/588)
core/rtw_mp.c
         94.76K 100%    1.61MB/s    0:00:00 (xfr#53, to-chk=511/588)
core/rtw_mp_ioctl.c
         66.22K 100%    1.11MB/s    0:00:00 (xfr#54, to-chk=510/588)
core/rtw_odm.c
         13.42K 100%  229.89kB/s    0:00:00 (xfr#55, to-chk=509/588)
core/rtw_p2p.c
        168.12K 100%    2.81MB/s    0:00:00 (xfr#56, to-chk=508/588)
core/rtw_pwrctrl.c
         70.72K 100%    1.16MB/s    0:00:00 (xfr#57, to-chk=507/588)
core/rtw_recv.c
        134.40K 100%    2.21MB/s    0:00:00 (xfr#58, to-chk=506/588)
core/rtw_rf.c
         57.41K 100%  950.29kB/s    0:00:00 (xfr#59, to-chk=505/588)
core/rtw_rson.c
         18.45K 100%  305.40kB/s    0:00:00 (xfr#60, to-chk=504/588)
core/rtw_sdio.c
          3.68K 100%   60.88kB/s    0:00:00 (xfr#61, to-chk=503/588)
core/rtw_security.c
         90.88K 100%    1.47MB/s    0:00:00 (xfr#62, to-chk=502/588)
core/rtw_sreset.c
         10.34K 100%  171.08kB/s    0:00:00 (xfr#63, to-chk=501/588)
core/rtw_sta_mgt.c
         32.25K 100%  533.82kB/s    0:00:00 (xfr#64, to-chk=500/588)
core/rtw_tdls.c
        109.17K 100%    1.74MB/s    0:00:00 (xfr#65, to-chk=499/588)
core/rtw_vht.c
         30.43K 100%  495.25kB/s    0:00:00 (xfr#66, to-chk=498/588)
core/rtw_wapi.c
         39.88K 100%  649.01kB/s    0:00:00 (xfr#67, to-chk=497/588)
core/rtw_wapi_sms4.c
         27.65K 100%  450.08kB/s    0:00:00 (xfr#68, to-chk=496/588)
core/rtw_wlan_util.c
        124.66K 100%    1.95MB/s    0:00:00 (xfr#69, to-chk=495/588)
core/rtw_xmit.c
        148.11K 100%    2.32MB/s    0:00:00 (xfr#70, to-chk=494/588)
core/efuse/
core/efuse/rtw_efuse.c
         86.74K 100%    1.33MB/s    0:00:00 (xfr#71, to-chk=492/588)
hal/
hal/HalPwrSeqCmd.c
          5.52K 100%   86.93kB/s    0:00:00 (xfr#72, to-chk=491/588)
hal/hal_btcoex.c
        147.65K 100%    2.27MB/s    0:00:00 (xfr#73, to-chk=490/588)
hal/hal_btcoex_wifionly.c
          5.51K 100%   86.84kB/s    0:00:00 (xfr#74, to-chk=489/588)
hal/hal_com.c
        357.79K 100%    5.33MB/s    0:00:00 (xfr#75, to-chk=488/588)
hal/hal_com_c2h.h
          4.02K 100%   61.36kB/s    0:00:00 (xfr#76, to-chk=487/588)
hal/hal_com_phycfg.c
        160.43K 100%    2.39MB/s    0:00:00 (xfr#77, to-chk=486/588)
hal/hal_dm.c
         38.12K 100%  572.69kB/s    0:00:00 (xfr#78, to-chk=485/588)
hal/hal_dm.h
          2.34K 100%   35.11kB/s    0:00:00 (xfr#79, to-chk=484/588)
hal/hal_dm_acs.c
         14.16K 100%  212.73kB/s    0:00:00 (xfr#80, to-chk=483/588)
hal/hal_dm_acs.h
          3.47K 100%   52.13kB/s    0:00:00 (xfr#81, to-chk=482/588)
hal/hal_halmac.c
         99.35K 100%    1.46MB/s    0:00:00 (xfr#82, to-chk=481/588)
hal/hal_halmac.h
          9.18K 100%  137.91kB/s    0:00:00 (xfr#83, to-chk=480/588)
hal/hal_intf.c
         37.70K 100%  566.38kB/s    0:00:00 (xfr#84, to-chk=479/588)
hal/hal_mcc.c
         61.32K 100%  907.29kB/s    0:00:00 (xfr#85, to-chk=478/588)
hal/hal_mp.c
         83.62K 100%    1.21MB/s    0:00:00 (xfr#86, to-chk=477/588)
hal/hal_phy.c
          6.37K 100%   94.21kB/s    0:00:00 (xfr#87, to-chk=476/588)
hal/btc/
hal/btc/halbtc8192e1ant.c
        105.91K 100%    1.53MB/s    0:00:00 (xfr#88, to-chk=469/588)
hal/btc/halbtc8192e1ant.h
          8.20K 100%  121.37kB/s    0:00:00 (xfr#89, to-chk=468/588)
hal/btc/halbtc8192e2ant.c
        135.87K 100%    1.93MB/s    0:00:00 (xfr#90, to-chk=467/588)
hal/btc/halbtc8192e2ant.h
          7.29K 100%  106.18kB/s    0:00:00 (xfr#91, to-chk=466/588)
hal/btc/halbtc8703b1ant.c
        138.12K 100%    1.94MB/s    0:00:00 (xfr#92, to-chk=465/588)
hal/btc/halbtc8703b1ant.h
         14.42K 100%  207.07kB/s    0:00:00 (xfr#93, to-chk=464/588)
hal/btc/halbtc8723b1ant.c
        159.62K 100%    2.24MB/s    0:00:00 (xfr#94, to-chk=463/588)
hal/btc/halbtc8723b1ant.h
         10.62K 100%  150.32kB/s    0:00:00 (xfr#95, to-chk=462/588)
hal/btc/halbtc8723b2ant.c
        158.88K 100%    2.20MB/s    0:00:00 (xfr#96, to-chk=461/588)
hal/btc/halbtc8723b2ant.h
          7.54K 100%  106.69kB/s    0:00:00 (xfr#97, to-chk=460/588)
hal/btc/halbtc8723bwifionly.c
          3.27K 100%   46.27kB/s    0:00:00 (xfr#98, to-chk=459/588)
hal/btc/halbtc8723bwifionly.h
            821 100%   11.62kB/s    0:00:00 (xfr#99, to-chk=458/588)
hal/btc/halbtc8723d1ant.c
        193.09K 100%    2.63MB/s    0:00:00 (xfr#100, to-chk=457/588)
hal/btc/halbtc8723d1ant.h
         14.98K 100%  208.94kB/s    0:00:00 (xfr#101, to-chk=456/588)
hal/btc/halbtc8723d2ant.c
        220.08K 100%    2.96MB/s    0:00:00 (xfr#102, to-chk=455/588)
hal/btc/halbtc8723d2ant.h
         15.29K 100%  210.35kB/s    0:00:00 (xfr#103, to-chk=454/588)
hal/btc/halbtc8812a1ant.c
        106.56K 100%    1.43MB/s    0:00:00 (xfr#104, to-chk=453/588)
hal/btc/halbtc8812a1ant.h
          8.26K 100%  113.61kB/s    0:00:00 (xfr#105, to-chk=452/588)
hal/btc/halbtc8812a2ant.c
        175.71K 100%    2.33MB/s    0:00:00 (xfr#106, to-chk=451/588)
hal/btc/halbtc8812a2ant.h
          7.93K 100%  107.63kB/s    0:00:00 (xfr#107, to-chk=450/588)
hal/btc/halbtc8821a1ant.c
        104.18K 100%    1.38MB/s    0:00:00 (xfr#108, to-chk=449/588)
hal/btc/halbtc8821a1ant.h
          7.64K 100%  103.57kB/s    0:00:00 (xfr#109, to-chk=448/588)
hal/btc/halbtc8821a2ant.c
        143.98K 100%    1.88MB/s    0:00:00 (xfr#110, to-chk=447/588)
hal/btc/halbtc8821a2ant.h
          7.47K 100%   99.92kB/s    0:00:00 (xfr#111, to-chk=446/588)
hal/btc/halbtc8821c1ant.c
        168.87K 100%    2.18MB/s    0:00:00 (xfr#112, to-chk=445/588)
hal/btc/halbtc8821c1ant.h
         17.34K 100%  228.83kB/s    0:00:00 (xfr#113, to-chk=444/588)
hal/btc/halbtc8821c2ant.c
        192.53K 100%    2.45MB/s    0:00:00 (xfr#114, to-chk=443/588)
hal/btc/halbtc8821c2ant.h
         17.64K 100%  229.73kB/s    0:00:00 (xfr#115, to-chk=442/588)
hal/btc/halbtc8821cwifionly.c
          6.18K 100%   80.43kB/s    0:00:00 (xfr#116, to-chk=441/588)
hal/btc/halbtc8821cwifionly.h
          2.56K 100%   33.29kB/s    0:00:00 (xfr#117, to-chk=440/588)
hal/btc/halbtc8822b1ant.c
        200.64K 100%    2.52MB/s    0:00:00 (xfr#118, to-chk=439/588)
hal/btc/halbtc8822b1ant.h
         17.32K 100%  222.57kB/s    0:00:00 (xfr#119, to-chk=438/588)
hal/btc/halbtc8822b2ant.c
        177.51K 100%    2.23MB/s    0:00:00 (xfr#120, to-chk=437/588)
hal/btc/halbtc8822b2ant.h
         17.76K 100%  228.23kB/s    0:00:00 (xfr#121, to-chk=436/588)
hal/btc/halbtc8822bwifionly.c
          2.02K 100%   26.02kB/s    0:00:00 (xfr#122, to-chk=435/588)
hal/btc/halbtc8822bwifionly.h
          1.13K 100%   14.32kB/s    0:00:00 (xfr#123, to-chk=434/588)
hal/btc/halbtcoutsrc.h
         28.71K 100%  364.17kB/s    0:00:00 (xfr#124, to-chk=433/588)
hal/btc/mp_precomp.h
          2.11K 100%   26.71kB/s    0:00:00 (xfr#125, to-chk=432/588)
hal/efuse/
hal/efuse/efuse_mask.h
          3.35K 100%   42.46kB/s    0:00:00 (xfr#126, to-chk=431/588)
hal/efuse/rtl8812a/
hal/efuse/rtl8812a/HalEfuseMask8812A_PCIE.c
          1.87K 100%   23.67kB/s    0:00:00 (xfr#127, to-chk=429/588)
hal/efuse/rtl8812a/HalEfuseMask8812A_PCIE.h
          1.07K 100%   13.62kB/s    0:00:00 (xfr#128, to-chk=428/588)
hal/efuse/rtl8812a/HalEfuseMask8812A_USB.c
          1.85K 100%   23.53kB/s    0:00:00 (xfr#129, to-chk=427/588)
hal/efuse/rtl8812a/HalEfuseMask8812A_USB.h
          1.07K 100%   13.58kB/s    0:00:00 (xfr#130, to-chk=426/588)
hal/efuse/rtl8812a/HalEfuseMask8821A_PCIE.c
          1.86K 100%   23.65kB/s    0:00:00 (xfr#131, to-chk=425/588)
hal/efuse/rtl8812a/HalEfuseMask8821A_PCIE.h
          1.07K 100%   13.62kB/s    0:00:00 (xfr#132, to-chk=424/588)
hal/efuse/rtl8812a/HalEfuseMask8821A_SDIO.c
          1.90K 100%   24.10kB/s    0:00:00 (xfr#133, to-chk=423/588)
hal/efuse/rtl8812a/HalEfuseMask8821A_SDIO.h
          1.07K 100%   13.60kB/s    0:00:00 (xfr#134, to-chk=422/588)
hal/efuse/rtl8812a/HalEfuseMask8821A_USB.c
          1.86K 100%   23.54kB/s    0:00:00 (xfr#135, to-chk=421/588)
hal/efuse/rtl8812a/HalEfuseMask8821A_USB.h
          1.07K 100%   13.55kB/s    0:00:00 (xfr#136, to-chk=420/588)
hal/hal_hci/
hal/hal_hci/hal_usb.c
         12.45K 100%  157.87kB/s    0:00:00 (xfr#137, to-chk=419/588)
hal/led/
hal/led/hal_usb_led.c
        112.47K 100%    1.38MB/s    0:00:00 (xfr#138, to-chk=418/588)
hal/phydm/
hal/phydm/ap_makefile.mk
          3.36K 100%   41.51kB/s    0:00:00 (xfr#139, to-chk=417/588)
hal/phydm/halhwimg.h
          4.10K 100%   50.67kB/s    0:00:00 (xfr#140, to-chk=416/588)
hal/phydm/mp_precomp.h
            656 100%    8.11kB/s    0:00:00 (xfr#141, to-chk=415/588)
hal/phydm/phydm.c
         77.86K 100%  962.46kB/s    0:00:00 (xfr#142, to-chk=414/588)
hal/phydm/phydm.h
         32.62K 100%  403.27kB/s    0:00:00 (xfr#143, to-chk=413/588)
hal/phydm/phydm.mk
          6.28K 100%   77.68kB/s    0:00:00 (xfr#144, to-chk=412/588)
hal/phydm/phydm_acs.c
         37.49K 100%  452.03kB/s    0:00:00 (xfr#145, to-chk=411/588)
hal/phydm/phydm_acs.h
          2.61K 100%   31.47kB/s    0:00:00 (xfr#146, to-chk=410/588)
hal/phydm/phydm_adaptivity.c
         35.97K 100%  433.71kB/s    0:00:00 (xfr#147, to-chk=409/588)
hal/phydm/phydm_adaptivity.h
          3.93K 100%   47.38kB/s    0:00:00 (xfr#148, to-chk=408/588)
hal/phydm/phydm_adc_sampling.c
         23.49K 100%  283.22kB/s    0:00:00 (xfr#149, to-chk=407/588)
hal/phydm/phydm_adc_sampling.h
          2.98K 100%   35.92kB/s    0:00:00 (xfr#150, to-chk=406/588)
hal/phydm/phydm_antdect.c
         34.57K 100%  416.81kB/s    0:00:00 (xfr#151, to-chk=405/588)
hal/phydm/phydm_antdect.h
          1.94K 100%   23.40kB/s    0:00:00 (xfr#152, to-chk=404/588)
hal/phydm/phydm_antdiv.c
        174.60K 100%    2.03MB/s    0:00:00 (xfr#153, to-chk=403/588)
hal/phydm/phydm_antdiv.h
         13.95K 100%  166.15kB/s    0:00:00 (xfr#154, to-chk=402/588)
hal/phydm/phydm_api.c
         32.51K 100%  387.12kB/s    0:00:00 (xfr#155, to-chk=401/588)
hal/phydm/phydm_api.h
          3.64K 100%   43.34kB/s    0:00:00 (xfr#156, to-chk=400/588)
hal/phydm/phydm_auto_dbg.c
         19.81K 100%  235.89kB/s    0:00:00 (xfr#157, to-chk=399/588)
hal/phydm/phydm_auto_dbg.h
          2.57K 100%   30.59kB/s    0:00:00 (xfr#158, to-chk=398/588)
hal/phydm/phydm_beamforming.c
         66.92K 100%  787.38kB/s    0:00:00 (xfr#159, to-chk=397/588)
hal/phydm/phydm_beamforming.h
          9.83K 100%  115.66kB/s    0:00:00 (xfr#160, to-chk=396/588)
hal/phydm/phydm_cck_pd.c
         12.22K 100%  143.83kB/s    0:00:00 (xfr#161, to-chk=395/588)
hal/phydm/phydm_cck_pd.h
          2.22K 100%   26.11kB/s    0:00:00 (xfr#162, to-chk=394/588)
hal/phydm/phydm_ccx.c
         37.54K 100%  441.70kB/s    0:00:00 (xfr#163, to-chk=393/588)
hal/phydm/phydm_ccx.h
          4.05K 100%   47.71kB/s    0:00:00 (xfr#164, to-chk=392/588)
hal/phydm/phydm_cfotracking.c
         12.79K 100%  150.52kB/s    0:00:00 (xfr#165, to-chk=391/588)
hal/phydm/phydm_cfotracking.h
          1.57K 100%   18.46kB/s    0:00:00 (xfr#166, to-chk=390/588)
hal/phydm/phydm_debug.c
        114.16K 100%    1.30MB/s    0:00:00 (xfr#167, to-chk=389/588)
hal/phydm/phydm_debug.h
          9.35K 100%  108.69kB/s    0:00:00 (xfr#168, to-chk=388/588)
hal/phydm/phydm_dfs.c
         23.15K 100%  269.17kB/s    0:00:00 (xfr#169, to-chk=387/588)
hal/phydm/phydm_dfs.h
          2.79K 100%   32.49kB/s    0:00:00 (xfr#170, to-chk=386/588)
hal/phydm/phydm_dig.c
         58.53K 100%  680.44kB/s    0:00:00 (xfr#171, to-chk=385/588)
hal/phydm/phydm_dig.h
          7.62K 100%   87.49kB/s    0:00:00 (xfr#172, to-chk=384/588)
hal/phydm/phydm_dynamic_rx_path.c
         11.19K 100%  128.56kB/s    0:00:00 (xfr#173, to-chk=383/588)
hal/phydm/phydm_dynamic_rx_path.h
          2.71K 100%   31.15kB/s    0:00:00 (xfr#174, to-chk=382/588)
hal/phydm/phydm_dynamictxpower.c
         14.47K 100%  166.29kB/s    0:00:00 (xfr#175, to-chk=381/588)
hal/phydm/phydm_dynamictxpower.h
          2.46K 100%   28.27kB/s    0:00:00 (xfr#176, to-chk=380/588)
hal/phydm/phydm_features.h
          1.46K 100%   16.82kB/s    0:00:00 (xfr#177, to-chk=379/588)
hal/phydm/phydm_features_ap.h
          3.93K 100%   45.17kB/s    0:00:00 (xfr#178, to-chk=378/588)
hal/phydm/phydm_features_ce.h
          2.80K 100%   32.20kB/s    0:00:00 (xfr#179, to-chk=377/588)
hal/phydm/phydm_features_win.h
          2.95K 100%   33.92kB/s    0:00:00 (xfr#180, to-chk=376/588)
hal/phydm/phydm_hwconfig.c
         31.72K 100%  364.46kB/s    0:00:00 (xfr#181, to-chk=375/588)
hal/phydm/phydm_hwconfig.h
          2.37K 100%   27.18kB/s    0:00:00 (xfr#182, to-chk=374/588)
hal/phydm/phydm_interface.c
         34.68K 100%  398.46kB/s    0:00:00 (xfr#183, to-chk=373/588)
hal/phydm/phydm_interface.h
          9.82K 100%  112.82kB/s    0:00:00 (xfr#184, to-chk=372/588)
hal/phydm/phydm_math_lib.c
          3.73K 100%   42.30kB/s    0:00:00 (xfr#185, to-chk=371/588)
hal/phydm/phydm_math_lib.h
          1.80K 100%   20.44kB/s    0:00:00 (xfr#186, to-chk=370/588)
hal/phydm/phydm_noisemonitor.c
         13.53K 100%  153.65kB/s    0:00:00 (xfr#187, to-chk=369/588)
hal/phydm/phydm_noisemonitor.h
          1.19K 100%   13.56kB/s    0:00:00 (xfr#188, to-chk=368/588)
hal/phydm/phydm_pathdiv.c
         21.69K 100%  246.34kB/s    0:00:00 (xfr#189, to-chk=367/588)
hal/phydm/phydm_pathdiv.h
          5.31K 100%   60.29kB/s    0:00:00 (xfr#190, to-chk=366/588)
hal/phydm/phydm_phystatus.c
         82.76K 100%  939.73kB/s    0:00:00 (xfr#191, to-chk=365/588)
hal/phydm/phydm_phystatus.h
         21.35K 100%  239.70kB/s    0:00:00 (xfr#192, to-chk=364/588)
hal/phydm/phydm_pow_train.c
          6.63K 100%   74.48kB/s    0:00:00 (xfr#193, to-chk=363/588)
hal/phydm/phydm_pow_train.h
          1.96K 100%   22.03kB/s    0:00:00 (xfr#194, to-chk=362/588)
hal/phydm/phydm_pre_define.h
         19.37K 100%  217.43kB/s    0:00:00 (xfr#195, to-chk=361/588)
hal/phydm/phydm_precomp.h
         11.56K 100%  129.76kB/s    0:00:00 (xfr#196, to-chk=360/588)
hal/phydm/phydm_primary_cca.c
         24.27K 100%  272.45kB/s    0:00:00 (xfr#197, to-chk=359/588)
hal/phydm/phydm_primary_cca.h
          2.96K 100%   33.23kB/s    0:00:00 (xfr#198, to-chk=358/588)
hal/phydm/phydm_psd.c
         11.37K 100%  127.59kB/s    0:00:00 (xfr#199, to-chk=357/588)
hal/phydm/phydm_psd.h
          1.77K 100%   19.86kB/s    0:00:00 (xfr#200, to-chk=356/588)
hal/phydm/phydm_rainfo.c
         68.55K 100%  752.21kB/s    0:00:00 (xfr#201, to-chk=355/588)
hal/phydm/phydm_rainfo.h
          9.27K 100%  101.75kB/s    0:00:00 (xfr#202, to-chk=354/588)
hal/phydm/phydm_reg.h
          8.28K 100%   90.86kB/s    0:00:00 (xfr#203, to-chk=353/588)
hal/phydm/phydm_regdefine11ac.h
          2.81K 100%   30.82kB/s    0:00:00 (xfr#204, to-chk=352/588)
hal/phydm/phydm_regdefine11n.h
          7.43K 100%   81.56kB/s    0:00:00 (xfr#205, to-chk=351/588)
hal/phydm/phydm_rssi_monitor.c
         14.39K 100%  157.87kB/s    0:00:00 (xfr#206, to-chk=350/588)
hal/phydm/phydm_rssi_monitor.h
          1.95K 100%   21.40kB/s    0:00:00 (xfr#207, to-chk=349/588)
hal/phydm/phydm_smt_ant.c
         74.95K 100%  813.22kB/s    0:00:00 (xfr#208, to-chk=348/588)
hal/phydm/phydm_smt_ant.h
          6.71K 100%   72.75kB/s    0:00:00 (xfr#209, to-chk=347/588)
hal/phydm/phydm_soml.c
         20.67K 100%  224.33kB/s    0:00:00 (xfr#210, to-chk=346/588)
hal/phydm/phydm_soml.h
          3.17K 100%   34.35kB/s    0:00:00 (xfr#211, to-chk=345/588)
hal/phydm/phydm_types.h
          7.12K 100%   77.25kB/s    0:00:00 (xfr#212, to-chk=344/588)
hal/phydm/halrf/
hal/phydm/halrf/halphyrf_ap.c
         62.11K 100%  673.91kB/s    0:00:00 (xfr#213, to-chk=340/588)
hal/phydm/halrf/halphyrf_ap.h
          2.95K 100%   31.99kB/s    0:00:00 (xfr#214, to-chk=339/588)
hal/phydm/halrf/halphyrf_ce.c
         42.00K 100%  450.76kB/s    0:00:00 (xfr#215, to-chk=338/588)
hal/phydm/halrf/halphyrf_ce.h
          2.69K 100%   28.92kB/s    0:00:00 (xfr#216, to-chk=337/588)
hal/phydm/halrf/halphyrf_win.c
         37.84K 100%  406.05kB/s    0:00:00 (xfr#217, to-chk=336/588)
hal/phydm/halrf/halphyrf_win.h
          2.89K 100%   31.05kB/s    0:00:00 (xfr#218, to-chk=335/588)
hal/phydm/halrf/halrf.c
         41.39K 100%  444.16kB/s    0:00:00 (xfr#219, to-chk=334/588)
hal/phydm/halrf/halrf.h
          7.52K 100%   80.67kB/s    0:00:00 (xfr#220, to-chk=333/588)
hal/phydm/halrf/halrf_features.h
            960 100%   10.30kB/s    0:00:00 (xfr#221, to-chk=332/588)
hal/phydm/halrf/halrf_iqk.h
          2.48K 100%   26.60kB/s    0:00:00 (xfr#222, to-chk=331/588)
hal/phydm/halrf/halrf_kfree.c
         30.85K 100%  331.04kB/s    0:00:00 (xfr#223, to-chk=330/588)
hal/phydm/halrf/halrf_kfree.h
          3.15K 100%   33.79kB/s    0:00:00 (xfr#224, to-chk=329/588)
hal/phydm/halrf/halrf_powertracking.c
          4.49K 100%   48.13kB/s    0:00:00 (xfr#225, to-chk=328/588)
hal/phydm/halrf/halrf_powertracking.h
          1.06K 100%   11.41kB/s    0:00:00 (xfr#226, to-chk=327/588)
hal/phydm/halrf/halrf_powertracking_ap.c
         52.92K 100%  561.69kB/s    0:00:00 (xfr#227, to-chk=326/588)
hal/phydm/halrf/halrf_powertracking_ap.h
         10.81K 100%  114.76kB/s    0:00:00 (xfr#228, to-chk=325/588)
hal/phydm/halrf/halrf_powertracking_ce.c
         30.91K 100%  328.16kB/s    0:00:00 (xfr#229, to-chk=324/588)
hal/phydm/halrf/halrf_powertracking_ce.h
         10.59K 100%  112.43kB/s    0:00:00 (xfr#230, to-chk=323/588)
hal/phydm/halrf/halrf_powertracking_win.c
         32.03K 100%  339.98kB/s    0:00:00 (xfr#231, to-chk=322/588)
hal/phydm/halrf/halrf_powertracking_win.h
          9.92K 100%  105.26kB/s    0:00:00 (xfr#232, to-chk=321/588)
hal/phydm/halrf/halrf_psd.c
          6.90K 100%   73.28kB/s    0:00:00 (xfr#233, to-chk=320/588)
hal/phydm/halrf/halrf_psd.h
          1.27K 100%   13.53kB/s    0:00:00 (xfr#234, to-chk=319/588)
hal/phydm/halrf/halrf_txgapcal.c
          9.36K 100%   98.29kB/s    0:00:00 (xfr#235, to-chk=318/588)
hal/phydm/halrf/halrf_txgapcal.h
             55 100%    0.58kB/s    0:00:00 (xfr#236, to-chk=317/588)
hal/phydm/halrf/rtl8812a/
hal/phydm/halrf/rtl8812a/halrf_8812a_ap.c
         75.44K 100%  792.15kB/s    0:00:00 (xfr#237, to-chk=315/588)
hal/phydm/halrf/rtl8812a/halrf_8812a_ap.h
          1.66K 100%   17.47kB/s    0:00:00 (xfr#238, to-chk=314/588)
hal/phydm/halrf/rtl8812a/halrf_8812a_ce.c
         76.91K 100%  807.64kB/s    0:00:00 (xfr#239, to-chk=313/588)
hal/phydm/halrf/rtl8812a/halrf_8812a_ce.h
          2.10K 100%   22.05kB/s    0:00:00 (xfr#240, to-chk=312/588)
hal/phydm/halrf/rtl8812a/halrf_8812a_win.c
        104.02K 100%    1.06MB/s    0:00:00 (xfr#241, to-chk=311/588)
hal/phydm/halrf/rtl8812a/halrf_8812a_win.h
          2.06K 100%   21.45kB/s    0:00:00 (xfr#242, to-chk=310/588)
hal/phydm/rtl8812a/
hal/phydm/rtl8812a/halhwimg8812a_bb.c
         41.78K 100%  434.10kB/s    0:00:00 (xfr#243, to-chk=309/588)
hal/phydm/rtl8812a/halhwimg8812a_bb.h
          4.21K 100%   43.74kB/s    0:00:00 (xfr#244, to-chk=308/588)
hal/phydm/rtl8812a/halhwimg8812a_mac.c
          7.97K 100%   82.84kB/s    0:00:00 (xfr#245, to-chk=307/588)
hal/phydm/rtl8812a/halhwimg8812a_mac.h
          1.18K 100%   12.28kB/s    0:00:00 (xfr#246, to-chk=306/588)
hal/phydm/rtl8812a/halhwimg8812a_rf.c
        166.02K 100%    1.67MB/s    0:00:00 (xfr#247, to-chk=305/588)
hal/phydm/rtl8812a/halhwimg8812a_rf.h
          4.93K 100%   50.65kB/s    0:00:00 (xfr#248, to-chk=304/588)
hal/phydm/rtl8812a/phydm_regconfig8812a.c
          4.55K 100%   46.76kB/s    0:00:00 (xfr#249, to-chk=303/588)
hal/phydm/rtl8812a/phydm_regconfig8812a.h
          1.75K 100%   18.00kB/s    0:00:00 (xfr#250, to-chk=302/588)
hal/phydm/rtl8812a/phydm_rtl8812a.c
          4.68K 100%   48.16kB/s    0:00:00 (xfr#251, to-chk=301/588)
hal/phydm/rtl8812a/phydm_rtl8812a.h
          1.10K 100%   11.29kB/s    0:00:00 (xfr#252, to-chk=300/588)
hal/phydm/rtl8812a/version_rtl8812a.h
            982 100%   10.09kB/s    0:00:00 (xfr#253, to-chk=299/588)
hal/phydm/txbf/
hal/phydm/txbf/halcomtxbf.c
         14.93K 100%  153.48kB/s    0:00:00 (xfr#254, to-chk=298/588)
hal/phydm/txbf/halcomtxbf.h
          3.97K 100%   40.82kB/s    0:00:00 (xfr#255, to-chk=297/588)
hal/phydm/txbf/haltxbf8192e.c
         13.65K 100%  138.87kB/s    0:00:00 (xfr#256, to-chk=296/588)
hal/phydm/txbf/haltxbf8192e.h
          1.63K 100%   16.56kB/s    0:00:00 (xfr#257, to-chk=295/588)
hal/phydm/txbf/haltxbf8814a.c
         22.87K 100%  232.67kB/s    0:00:00 (xfr#258, to-chk=294/588)
hal/phydm/txbf/haltxbf8814a.h
          2.26K 100%   23.02kB/s    0:00:00 (xfr#259, to-chk=293/588)
hal/phydm/txbf/haltxbf8822b.c
         39.22K 100%  399.01kB/s    0:00:00 (xfr#260, to-chk=292/588)
hal/phydm/txbf/haltxbf8822b.h
          2.02K 100%   20.57kB/s    0:00:00 (xfr#261, to-chk=291/588)
hal/phydm/txbf/haltxbfinterface.c
         43.05K 100%  437.90kB/s    0:00:00 (xfr#262, to-chk=290/588)
hal/phydm/txbf/haltxbfinterface.h
          3.81K 100%   38.74kB/s    0:00:00 (xfr#263, to-chk=289/588)
hal/phydm/txbf/haltxbfjaguar.c
         17.61K 100%  179.19kB/s    0:00:00 (xfr#264, to-chk=288/588)
hal/phydm/txbf/haltxbfjaguar.h
          2.02K 100%   20.57kB/s    0:00:00 (xfr#265, to-chk=287/588)
hal/phydm/txbf/phydm_hal_txbf_api.c
          4.69K 100%   47.26kB/s    0:00:00 (xfr#266, to-chk=286/588)
hal/phydm/txbf/phydm_hal_txbf_api.h
          1.51K 100%   15.21kB/s    0:00:00 (xfr#267, to-chk=285/588)
hal/rtl8812a/
hal/rtl8812a/Hal8812PwrSeq.c
          2.75K 100%   27.64kB/s    0:00:00 (xfr#268, to-chk=284/588)
hal/rtl8812a/Hal8821APwrSeq.c
          2.82K 100%   28.36kB/s    0:00:00 (xfr#269, to-chk=283/588)
hal/rtl8812a/hal8812a_fw.c
        859.67K 100%    8.20MB/s    0:00:00 (xfr#270, to-chk=282/588)
hal/rtl8812a/hal8812a_fw.h
          1.63K 100%   15.94kB/s    0:00:00 (xfr#271, to-chk=281/588)
hal/rtl8812a/hal8821a_fw.c
        659.39K 100%    6.17MB/s    0:00:00 (xfr#272, to-chk=280/588)
hal/rtl8812a/hal8821a_fw.h
          1.32K 100%   12.69kB/s    0:00:00 (xfr#273, to-chk=279/588)
hal/rtl8812a/rtl8812a_cmd.c
         48.05K 100%  459.99kB/s    0:00:00 (xfr#274, to-chk=278/588)
hal/rtl8812a/rtl8812a_dm.c
          9.86K 100%   94.37kB/s    0:00:00 (xfr#275, to-chk=277/588)
hal/rtl8812a/rtl8812a_hal_init.c
        179.69K 100%    1.66MB/s    0:00:00 (xfr#276, to-chk=276/588)
hal/rtl8812a/rtl8812a_phycfg.c
         66.69K 100%  632.34kB/s    0:00:00 (xfr#277, to-chk=275/588)
hal/rtl8812a/rtl8812a_rf6052.c
          4.54K 100%   43.03kB/s    0:00:00 (xfr#278, to-chk=274/588)
hal/rtl8812a/rtl8812a_rxdesc.c
          3.25K 100%   30.83kB/s    0:00:00 (xfr#279, to-chk=273/588)
hal/rtl8812a/rtl8812a_sreset.c
          3.59K 100%   34.00kB/s    0:00:00 (xfr#280, to-chk=272/588)
hal/rtl8812a/rtl8812a_xmit.c
         15.30K 100%  145.08kB/s    0:00:00 (xfr#281, to-chk=271/588)
hal/rtl8812a/usb/
hal/rtl8812a/usb/rtl8812au_led.c
         10.24K 100%   97.06kB/s    0:00:00 (xfr#282, to-chk=269/588)
hal/rtl8812a/usb/rtl8812au_recv.c
            969 100%    9.19kB/s    0:00:00 (xfr#283, to-chk=268/588)
hal/rtl8812a/usb/rtl8812au_xmit.c
         32.96K 100%  312.54kB/s    0:00:00 (xfr#284, to-chk=267/588)
hal/rtl8812a/usb/usb_halinit.c
         76.78K 100%  721.01kB/s    0:00:00 (xfr#285, to-chk=266/588)
hal/rtl8812a/usb/usb_ops_linux.c
          7.62K 100%   71.51kB/s    0:00:00 (xfr#286, to-chk=265/588)
include/
include/Hal8188EPhyCfg.h
          6.80K 100%   63.90kB/s    0:00:00 (xfr#287, to-chk=264/588)
include/Hal8188EPhyReg.h
         35.29K 100%  331.39kB/s    0:00:00 (xfr#288, to-chk=263/588)
include/Hal8188EPwrSeq.h
         13.29K 100%  124.82kB/s    0:00:00 (xfr#289, to-chk=262/588)
include/Hal8188FPhyCfg.h
          3.00K 100%   28.13kB/s    0:00:00 (xfr#290, to-chk=261/588)
include/Hal8188FPhyReg.h
         36.76K 100%  345.15kB/s    0:00:00 (xfr#291, to-chk=260/588)
include/Hal8188FPwrSeq.h
         18.29K 100%  171.78kB/s    0:00:00 (xfr#292, to-chk=259/588)
include/Hal8192EPhyCfg.h
          3.81K 100%   35.79kB/s    0:00:00 (xfr#293, to-chk=258/588)
include/Hal8192EPhyReg.h
         36.63K 100%  340.71kB/s    0:00:00 (xfr#294, to-chk=257/588)
include/Hal8192EPwrSeq.h
         13.24K 100%  123.13kB/s    0:00:00 (xfr#295, to-chk=256/588)
include/Hal8703BPhyCfg.h
          2.95K 100%   27.43kB/s    0:00:00 (xfr#296, to-chk=255/588)
include/Hal8703BPhyReg.h
         35.98K 100%  334.59kB/s    0:00:00 (xfr#297, to-chk=254/588)
include/Hal8703BPwrSeq.h
         17.66K 100%  164.23kB/s    0:00:00 (xfr#298, to-chk=253/588)
include/Hal8723BPhyCfg.h
          2.95K 100%   27.46kB/s    0:00:00 (xfr#299, to-chk=252/588)
include/Hal8723BPhyReg.h
         35.87K 100%  333.58kB/s    0:00:00 (xfr#300, to-chk=251/588)
include/Hal8723BPwrSeq.h
         23.15K 100%  215.35kB/s    0:00:00 (xfr#301, to-chk=250/588)
include/Hal8723DPhyCfg.h
          2.95K 100%   27.41kB/s    0:00:00 (xfr#302, to-chk=249/588)
include/Hal8723DPhyReg.h
         35.87K 100%  333.59kB/s    0:00:00 (xfr#303, to-chk=248/588)
include/Hal8723DPwrSeq.h
         18.66K 100%  173.57kB/s    0:00:00 (xfr#304, to-chk=247/588)
include/Hal8723PwrSeq.h
         15.80K 100%  145.56kB/s    0:00:00 (xfr#305, to-chk=246/588)
include/Hal8812PhyCfg.h
          3.72K 100%   34.31kB/s    0:00:00 (xfr#306, to-chk=245/588)
include/Hal8812PhyReg.h
         24.70K 100%  227.58kB/s    0:00:00 (xfr#307, to-chk=244/588)
include/Hal8812PwrSeq.h
         18.59K 100%  171.29kB/s    0:00:00 (xfr#308, to-chk=243/588)
include/Hal8814PhyCfg.h
          5.17K 100%   47.59kB/s    0:00:00 (xfr#309, to-chk=242/588)
include/Hal8814PhyReg.h
         30.39K 100%  280.00kB/s    0:00:00 (xfr#310, to-chk=241/588)
include/Hal8814PwrSeq.h
         22.26K 100%  205.06kB/s    0:00:00 (xfr#311, to-chk=240/588)
include/Hal8821APwrSeq.h
         18.07K 100%  166.47kB/s    0:00:00 (xfr#312, to-chk=239/588)
include/HalPwrSeqCmd.h
          4.12K 100%   37.98kB/s    0:00:00 (xfr#313, to-chk=238/588)
include/HalVerDef.h
         10.28K 100%   94.68kB/s    0:00:00 (xfr#314, to-chk=237/588)
include/autoconf.h
          9.46K 100%   87.14kB/s    0:00:00 (xfr#315, to-chk=236/588)
include/basic_types.h
         11.61K 100%  106.95kB/s    0:00:00 (xfr#316, to-chk=235/588)
include/circ_buf.h
            864 100%    7.96kB/s    0:00:00 (xfr#317, to-chk=234/588)
include/cmd_osdep.h
          1.08K 100%    9.89kB/s    0:00:00 (xfr#318, to-chk=233/588)
include/custom_gpio.h
          1.22K 100%   11.13kB/s    0:00:00 (xfr#319, to-chk=232/588)
include/drv_conf.h
         10.77K 100%   98.25kB/s    0:00:00 (xfr#320, to-chk=231/588)
include/drv_types.h
         43.63K 100%  398.18kB/s    0:00:00 (xfr#321, to-chk=230/588)
include/drv_types_ce.h
          2.49K 100%   22.72kB/s    0:00:00 (xfr#322, to-chk=229/588)
include/drv_types_gspi.h
          1.37K 100%   12.48kB/s    0:00:00 (xfr#323, to-chk=228/588)
include/drv_types_linux.h
            725 100%    6.62kB/s    0:00:00 (xfr#324, to-chk=227/588)
include/drv_types_pci.h
          7.54K 100%   68.79kB/s    0:00:00 (xfr#325, to-chk=226/588)
include/drv_types_sdio.h
          2.52K 100%   22.96kB/s    0:00:00 (xfr#326, to-chk=225/588)
include/drv_types_xp.h
          2.54K 100%   23.20kB/s    0:00:00 (xfr#327, to-chk=224/588)
include/ethernet.h
          1.59K 100%   14.49kB/s    0:00:00 (xfr#328, to-chk=223/588)
include/gspi_hal.h
            983 100%    8.97kB/s    0:00:00 (xfr#329, to-chk=222/588)
include/gspi_ops.h
          7.79K 100%   71.05kB/s    0:00:00 (xfr#330, to-chk=221/588)
include/gspi_ops_linux.h
            722 100%    6.59kB/s    0:00:00 (xfr#331, to-chk=220/588)
include/gspi_osintf.h
            931 100%    8.50kB/s    0:00:00 (xfr#332, to-chk=219/588)
include/h2clbk.h
            850 100%    7.76kB/s    0:00:00 (xfr#333, to-chk=218/588)
include/hal_btcoex.h
          4.25K 100%   38.83kB/s    0:00:00 (xfr#334, to-chk=217/588)
include/hal_btcoex_wifionly.h
          2.33K 100%   21.31kB/s    0:00:00 (xfr#335, to-chk=216/588)
include/hal_com.h
         22.96K 100%  209.60kB/s    0:00:00 (xfr#336, to-chk=215/588)
include/hal_com_h2c.h
         30.13K 100%  272.42kB/s    0:00:00 (xfr#337, to-chk=214/588)
include/hal_com_led.h
         13.94K 100%  126.02kB/s    0:00:00 (xfr#338, to-chk=213/588)
include/hal_com_phycfg.h
          7.69K 100%   69.50kB/s    0:00:00 (xfr#339, to-chk=212/588)
include/hal_com_reg.h
         66.02K 100%  591.51kB/s    0:00:00 (xfr#340, to-chk=211/588)
include/hal_data.h
         34.66K 100%  310.54kB/s    0:00:00 (xfr#341, to-chk=210/588)
include/hal_gspi.h
          1.18K 100%   10.45kB/s    0:00:00 (xfr#342, to-chk=209/588)
include/hal_ic_cfg.h
          5.47K 100%   48.54kB/s    0:00:00 (xfr#343, to-chk=208/588)
include/hal_intf.h
         28.09K 100%  249.42kB/s    0:00:00 (xfr#344, to-chk=207/588)
include/hal_pg.h
         26.76K 100%  237.61kB/s    0:00:00 (xfr#345, to-chk=206/588)
include/hal_phy.h
          5.48K 100%   48.69kB/s    0:00:00 (xfr#346, to-chk=205/588)
include/hal_phy_reg.h
            918 100%    8.15kB/s    0:00:00 (xfr#347, to-chk=204/588)
include/hal_sdio.h
          1.32K 100%   11.68kB/s    0:00:00 (xfr#348, to-chk=203/588)
include/ieee80211.h
         55.83K 100%  495.66kB/s    0:00:00 (xfr#349, to-chk=202/588)
include/ieee80211_ext.h
         10.39K 100%   92.22kB/s    0:00:00 (xfr#350, to-chk=201/588)
include/if_ether.h
          4.58K 100%   40.64kB/s    0:00:00 (xfr#351, to-chk=200/588)
include/ip.h
          4.04K 100%   35.87kB/s    0:00:00 (xfr#352, to-chk=199/588)
include/mlme_osdep.h
          1.19K 100%   10.56kB/s    0:00:00 (xfr#353, to-chk=198/588)
include/mp_custom_oid.h
         14.42K 100%  128.03kB/s    0:00:00 (xfr#354, to-chk=197/588)
include/nic_spec.h
          1.24K 100%   10.99kB/s    0:00:00 (xfr#355, to-chk=196/588)
include/osdep_intf.h
          4.61K 100%   40.89kB/s    0:00:00 (xfr#356, to-chk=195/588)
include/osdep_service.h
         25.38K 100%  223.32kB/s    0:00:00 (xfr#357, to-chk=194/588)
include/osdep_service_bsd.h
         21.45K 100%  188.69kB/s    0:00:00 (xfr#358, to-chk=193/588)
include/osdep_service_ce.h
          4.52K 100%   39.77kB/s    0:00:00 (xfr#359, to-chk=192/588)
include/osdep_service_linux.h
         12.84K 100%  112.93kB/s    0:00:00 (xfr#360, to-chk=191/588)
include/osdep_service_xp.h
          4.83K 100%   42.48kB/s    0:00:00 (xfr#361, to-chk=190/588)
include/pci_hal.h
          1.37K 100%   12.04kB/s    0:00:00 (xfr#362, to-chk=189/588)
include/pci_ops.h
          3.33K 100%   29.29kB/s    0:00:00 (xfr#363, to-chk=188/588)
include/pci_osintf.h
          1.74K 100%   15.29kB/s    0:00:00 (xfr#364, to-chk=187/588)
include/recv_osdep.h
          2.51K 100%   22.07kB/s    0:00:00 (xfr#365, to-chk=186/588)
include/rtl8188e_cmd.h
          5.20K 100%   45.71kB/s    0:00:00 (xfr#366, to-chk=185/588)
include/rtl8188e_dm.h
          1.06K 100%    9.32kB/s    0:00:00 (xfr#367, to-chk=184/588)
include/rtl8188e_hal.h
         12.27K 100%  107.92kB/s    0:00:00 (xfr#368, to-chk=183/588)
include/rtl8188e_led.h
          1.40K 100%   12.27kB/s    0:00:00 (xfr#369, to-chk=182/588)
include/rtl8188e_recv.h
          3.55K 100%   31.21kB/s    0:00:00 (xfr#370, to-chk=181/588)
include/rtl8188e_rf.h
            965 100%    8.49kB/s    0:00:00 (xfr#371, to-chk=180/588)
include/rtl8188e_spec.h
          5.78K 100%   50.89kB/s    0:00:00 (xfr#372, to-chk=179/588)
include/rtl8188e_sreset.h
            921 100%    8.10kB/s    0:00:00 (xfr#373, to-chk=178/588)
include/rtl8188e_xmit.h
          7.61K 100%   66.99kB/s    0:00:00 (xfr#374, to-chk=177/588)
include/rtl8188f_cmd.h
         12.02K 100%  105.79kB/s    0:00:00 (xfr#375, to-chk=176/588)
include/rtl8188f_dm.h
          1.42K 100%   12.39kB/s    0:00:00 (xfr#376, to-chk=175/588)
include/rtl8188f_hal.h
          9.51K 100%   82.89kB/s    0:00:00 (xfr#377, to-chk=174/588)
include/rtl8188f_led.h
          1.55K 100%   13.52kB/s    0:00:00 (xfr#378, to-chk=173/588)
include/rtl8188f_recv.h
          2.36K 100%   20.54kB/s    0:00:00 (xfr#379, to-chk=172/588)
include/rtl8188f_rf.h
            863 100%    7.52kB/s    0:00:00 (xfr#380, to-chk=171/588)
include/rtl8188f_spec.h
         12.33K 100%  107.53kB/s    0:00:00 (xfr#381, to-chk=170/588)
include/rtl8188f_sreset.h
            919 100%    8.01kB/s    0:00:00 (xfr#382, to-chk=169/588)
include/rtl8188f_xmit.h
         19.71K 100%  171.88kB/s    0:00:00 (xfr#383, to-chk=168/588)
include/rtl8192e_cmd.h
          6.23K 100%   54.30kB/s    0:00:00 (xfr#384, to-chk=167/588)
include/rtl8192e_dm.h
          1.06K 100%    9.24kB/s    0:00:00 (xfr#385, to-chk=166/588)
include/rtl8192e_hal.h
         13.26K 100%  115.65kB/s    0:00:00 (xfr#386, to-chk=165/588)
include/rtl8192e_led.h
          1.36K 100%   11.85kB/s    0:00:00 (xfr#387, to-chk=164/588)
include/rtl8192e_recv.h
          8.85K 100%   77.18kB/s    0:00:00 (xfr#388, to-chk=163/588)
include/rtl8192e_rf.h
            889 100%    7.75kB/s    0:00:00 (xfr#389, to-chk=162/588)
include/rtl8192e_spec.h
         13.20K 100%  115.05kB/s    0:00:00 (xfr#390, to-chk=161/588)
include/rtl8192e_sreset.h
            922 100%    8.04kB/s    0:00:00 (xfr#391, to-chk=160/588)
include/rtl8192e_xmit.h
         19.89K 100%  173.45kB/s    0:00:00 (xfr#392, to-chk=159/588)
include/rtl8703b_cmd.h
         12.03K 100%  103.96kB/s    0:00:00 (xfr#393, to-chk=158/588)
include/rtl8703b_dm.h
          1.42K 100%   12.28kB/s    0:00:00 (xfr#394, to-chk=157/588)
include/rtl8703b_hal.h
          9.66K 100%   83.47kB/s    0:00:00 (xfr#395, to-chk=156/588)
include/rtl8703b_led.h
          1.58K 100%   13.66kB/s    0:00:00 (xfr#396, to-chk=155/588)
include/rtl8703b_recv.h
          2.65K 100%   22.88kB/s    0:00:00 (xfr#397, to-chk=154/588)
include/rtl8703b_rf.h
            863 100%    7.46kB/s    0:00:00 (xfr#398, to-chk=153/588)
include/rtl8703b_spec.h
         18.91K 100%  163.41kB/s    0:00:00 (xfr#399, to-chk=152/588)
include/rtl8703b_sreset.h
            921 100%    7.96kB/s    0:00:00 (xfr#400, to-chk=151/588)
include/rtl8703b_xmit.h
         19.98K 100%  172.66kB/s    0:00:00 (xfr#401, to-chk=150/588)
include/rtl8723b_cmd.h
         12.03K 100%  103.96kB/s    0:00:00 (xfr#402, to-chk=149/588)
include/rtl8723b_dm.h
          1.42K 100%   12.16kB/s    0:00:00 (xfr#403, to-chk=148/588)
include/rtl8723b_hal.h
          9.99K 100%   85.56kB/s    0:00:00 (xfr#404, to-chk=147/588)
include/rtl8723b_led.h
          1.56K 100%   13.35kB/s    0:00:00 (xfr#405, to-chk=146/588)
include/rtl8723b_recv.h
          2.65K 100%   22.68kB/s    0:00:00 (xfr#406, to-chk=145/588)
include/rtl8723b_rf.h
            863 100%    7.39kB/s    0:00:00 (xfr#407, to-chk=144/588)
include/rtl8723b_spec.h
         11.65K 100%   99.79kB/s    0:00:00 (xfr#408, to-chk=143/588)
include/rtl8723b_sreset.h
            921 100%    7.89kB/s    0:00:00 (xfr#409, to-chk=142/588)
include/rtl8723b_xmit.h
         19.98K 100%  171.15kB/s    0:00:00 (xfr#410, to-chk=141/588)
include/rtl8723d_cmd.h
         10.71K 100%   91.75kB/s    0:00:00 (xfr#411, to-chk=140/588)
include/rtl8723d_dm.h
          1.42K 100%   12.17kB/s    0:00:00 (xfr#412, to-chk=139/588)
include/rtl8723d_hal.h
         10.49K 100%   89.85kB/s    0:00:00 (xfr#413, to-chk=138/588)
include/rtl8723d_led.h
          1.57K 100%   13.41kB/s    0:00:00 (xfr#414, to-chk=137/588)
include/rtl8723d_lps_poff.h
          2.79K 100%   23.91kB/s    0:00:00 (xfr#415, to-chk=136/588)
include/rtl8723d_recv.h
          4.29K 100%   36.74kB/s    0:00:00 (xfr#416, to-chk=135/588)
include/rtl8723d_rf.h
            854 100%    7.32kB/s    0:00:00 (xfr#417, to-chk=134/588)
include/rtl8723d_spec.h
         16.37K 100%  140.23kB/s    0:00:00 (xfr#418, to-chk=133/588)
include/rtl8723d_sreset.h
            921 100%    7.89kB/s    0:00:00 (xfr#419, to-chk=132/588)
include/rtl8723d_xmit.h
         24.27K 100%  206.09kB/s    0:00:00 (xfr#420, to-chk=131/588)
include/rtl8812a_cmd.h
          7.21K 100%   61.25kB/s    0:00:00 (xfr#421, to-chk=130/588)
include/rtl8812a_dm.h
          1.05K 100%    8.96kB/s    0:00:00 (xfr#422, to-chk=129/588)
include/rtl8812a_hal.h
         14.68K 100%  124.65kB/s    0:00:00 (xfr#423, to-chk=128/588)
include/rtl8812a_led.h
          1.51K 100%   12.83kB/s    0:00:00 (xfr#424, to-chk=127/588)
include/rtl8812a_recv.h
          7.89K 100%   66.97kB/s    0:00:00 (xfr#425, to-chk=126/588)
include/rtl8812a_rf.h
            887 100%    7.53kB/s    0:00:00 (xfr#426, to-chk=125/588)
include/rtl8812a_spec.h
         10.66K 100%   90.52kB/s    0:00:00 (xfr#427, to-chk=124/588)
include/rtl8812a_sreset.h
            918 100%    7.80kB/s    0:00:00 (xfr#428, to-chk=123/588)
include/rtl8812a_xmit.h
         15.52K 100%  131.83kB/s    0:00:00 (xfr#429, to-chk=122/588)
include/rtl8814a_cmd.h
         10.91K 100%   92.67kB/s    0:00:00 (xfr#430, to-chk=121/588)
include/rtl8814a_dm.h
            909 100%    7.72kB/s    0:00:00 (xfr#431, to-chk=120/588)
include/rtl8814a_hal.h
         13.75K 100%  116.75kB/s    0:00:00 (xfr#432, to-chk=119/588)
include/rtl8814a_led.h
          1.45K 100%   12.29kB/s    0:00:00 (xfr#433, to-chk=118/588)
include/rtl8814a_recv.h
         10.18K 100%   85.68kB/s    0:00:00 (xfr#434, to-chk=117/588)
include/rtl8814a_rf.h
            889 100%    7.48kB/s    0:00:00 (xfr#435, to-chk=116/588)
include/rtl8814a_spec.h
         26.03K 100%  219.13kB/s    0:00:00 (xfr#436, to-chk=115/588)
include/rtl8814a_sreset.h
            920 100%    7.75kB/s    0:00:00 (xfr#437, to-chk=114/588)
include/rtl8814a_xmit.h
         19.88K 100%  167.36kB/s    0:00:00 (xfr#438, to-chk=113/588)
include/rtl8821a_spec.h
          3.45K 100%   29.03kB/s    0:00:00 (xfr#439, to-chk=112/588)
include/rtl8821a_xmit.h
          4.25K 100%   35.80kB/s    0:00:00 (xfr#440, to-chk=111/588)
include/rtl8821c_dm.h
            887 100%    7.47kB/s    0:00:00 (xfr#441, to-chk=110/588)
include/rtl8821c_hal.h
          2.63K 100%   22.12kB/s    0:00:00 (xfr#442, to-chk=109/588)
include/rtl8821c_spec.h
          7.05K 100%   58.88kB/s    0:00:00 (xfr#443, to-chk=108/588)
include/rtl8821ce_hal.h
            841 100%    7.02kB/s    0:00:00 (xfr#444, to-chk=107/588)
include/rtl8821cs_hal.h
            839 100%    7.00kB/s    0:00:00 (xfr#445, to-chk=106/588)
include/rtl8821cu_hal.h
            894 100%    7.46kB/s    0:00:00 (xfr#446, to-chk=105/588)
include/rtl8822b_hal.h
          7.99K 100%   66.71kB/s    0:00:00 (xfr#447, to-chk=104/588)
include/rtl8822be_hal.h
            992 100%    8.28kB/s    0:00:00 (xfr#448, to-chk=103/588)
include/rtl8822bs_hal.h
          1.09K 100%    9.14kB/s    0:00:00 (xfr#449, to-chk=102/588)
include/rtl8822bu_hal.h
          1.96K 100%   16.38kB/s    0:00:00 (xfr#450, to-chk=101/588)
include/rtw_android.h
          3.45K 100%   28.82kB/s    0:00:00 (xfr#451, to-chk=100/588)
include/rtw_ap.h
          4.78K 100%   39.86kB/s    0:00:00 (xfr#452, to-chk=99/588)
include/rtw_beamforming.h
         11.82K 100%   98.66kB/s    0:00:00 (xfr#453, to-chk=98/588)
include/rtw_br_ext.h
          2.00K 100%   16.67kB/s    0:00:00 (xfr#454, to-chk=97/588)
include/rtw_bt_mp.h
          8.01K 100%   66.85kB/s    0:00:00 (xfr#455, to-chk=96/588)
include/rtw_btcoex.h
         19.18K 100%  160.06kB/s    0:00:00 (xfr#456, to-chk=95/588)
include/rtw_btcoex_wifionly.h
            963 100%    8.04kB/s    0:00:00 (xfr#457, to-chk=94/588)
include/rtw_byteorder.h
          1.15K 100%    9.56kB/s    0:00:00 (xfr#458, to-chk=93/588)
include/rtw_cmd.h
         29.47K 100%  245.99kB/s    0:00:00 (xfr#459, to-chk=92/588)
include/rtw_debug.h
         26.99K 100%  223.36kB/s    0:00:00 (xfr#460, to-chk=91/588)
include/rtw_eeprom.h
          4.04K 100%   33.40kB/s    0:00:00 (xfr#461, to-chk=90/588)
include/rtw_efuse.h
          9.40K 100%   77.79kB/s    0:00:00 (xfr#462, to-chk=89/588)
include/rtw_event.h
          2.42K 100%   20.03kB/s    0:00:00 (xfr#463, to-chk=88/588)
include/rtw_ht.h
         12.11K 100%  100.21kB/s    0:00:00 (xfr#464, to-chk=87/588)
include/rtw_io.h
         19.60K 100%  160.82kB/s    0:00:00 (xfr#465, to-chk=86/588)
include/rtw_ioctl.h
         14.55K 100%  119.42kB/s    0:00:00 (xfr#466, to-chk=85/588)
include/rtw_ioctl_query.h
            940 100%    7.71kB/s    0:00:00 (xfr#467, to-chk=84/588)
include/rtw_ioctl_rtl.h
          4.39K 100%   36.03kB/s    0:00:00 (xfr#468, to-chk=83/588)
include/rtw_ioctl_set.h
          2.75K 100%   22.60kB/s    0:00:00 (xfr#469, to-chk=82/588)
include/rtw_iol.h
          5.48K 100%   44.95kB/s    0:00:00 (xfr#470, to-chk=81/588)
include/rtw_mcc.h
          6.72K 100%   55.14kB/s    0:00:00 (xfr#471, to-chk=80/588)
include/rtw_mem.h
          1.23K 100%   10.10kB/s    0:00:00 (xfr#472, to-chk=79/588)
include/rtw_mi.h
         10.87K 100%   89.20kB/s    0:00:00 (xfr#473, to-chk=78/588)
include/rtw_mlme.h
         41.52K 100%  340.74kB/s    0:00:00 (xfr#474, to-chk=77/588)
include/rtw_mlme_ext.h
         49.02K 100%  398.90kB/s    0:00:00 (xfr#475, to-chk=76/588)
include/rtw_mp.h
         25.37K 100%  206.43kB/s    0:00:00 (xfr#476, to-chk=75/588)
include/rtw_mp_ioctl.h
         23.80K 100%  193.68kB/s    0:00:00 (xfr#477, to-chk=74/588)
include/rtw_mp_phy_regdef.h
         38.09K 100%  307.46kB/s    0:00:00 (xfr#478, to-chk=73/588)
include/rtw_odm.h
          3.45K 100%   27.86kB/s    0:00:00 (xfr#479, to-chk=72/588)
include/rtw_p2p.h
          8.01K 100%   64.64kB/s    0:00:00 (xfr#480, to-chk=71/588)
include/rtw_pwrctrl.h
         16.92K 100%  136.58kB/s    0:00:00 (xfr#481, to-chk=70/588)
include/rtw_qos.h
          2.12K 100%   17.07kB/s    0:00:00 (xfr#482, to-chk=69/588)
include/rtw_recv.h
         20.10K 100%  162.25kB/s    0:00:00 (xfr#483, to-chk=68/588)
include/rtw_rf.h
          8.75K 100%   70.59kB/s    0:00:00 (xfr#484, to-chk=67/588)
include/rtw_rson.h
          2.51K 100%   20.24kB/s    0:00:00 (xfr#485, to-chk=66/588)
include/rtw_sdio.h
          1.17K 100%    9.47kB/s    0:00:00 (xfr#486, to-chk=65/588)
include/rtw_security.h
         14.71K 100%  118.74kB/s    0:00:00 (xfr#487, to-chk=64/588)
include/rtw_sreset.h
          1.86K 100%   15.00kB/s    0:00:00 (xfr#488, to-chk=63/588)
include/rtw_tdls.h
          9.52K 100%   76.82kB/s    0:00:00 (xfr#489, to-chk=62/588)
include/rtw_version.h
             49 100%    0.40kB/s    0:00:00 (xfr#490, to-chk=61/588)
include/rtw_vht.h
          8.46K 100%   68.29kB/s    0:00:00 (xfr#491, to-chk=60/588)
include/rtw_wapi.h
          6.53K 100%   52.66kB/s    0:00:00 (xfr#492, to-chk=59/588)
include/rtw_wifi_regd.h
          1.04K 100%    8.37kB/s    0:00:00 (xfr#493, to-chk=58/588)
include/rtw_xmit.h
         27.70K 100%  221.74kB/s    0:00:00 (xfr#494, to-chk=57/588)
include/sdio_hal.h
          1.35K 100%   10.84kB/s    0:00:00 (xfr#495, to-chk=56/588)
include/sdio_ops.h
          6.51K 100%   52.15kB/s    0:00:00 (xfr#496, to-chk=55/588)
include/sdio_ops_ce.h
          1.82K 100%   14.60kB/s    0:00:00 (xfr#497, to-chk=54/588)
include/sdio_ops_linux.h
          2.60K 100%   20.82kB/s    0:00:00 (xfr#498, to-chk=53/588)
include/sdio_ops_xp.h
          1.82K 100%   14.55kB/s    0:00:00 (xfr#499, to-chk=52/588)
include/sdio_osintf.h
            928 100%    7.43kB/s    0:00:00 (xfr#500, to-chk=51/588)
include/sta_info.h
         17.18K 100%  137.50kB/s    0:00:00 (xfr#501, to-chk=50/588)
include/usb_hal.h
          1.78K 100%   14.22kB/s    0:00:00 (xfr#502, to-chk=49/588)
include/usb_ops.h
          4.11K 100%   32.91kB/s    0:00:00 (xfr#503, to-chk=48/588)
include/usb_ops_linux.h
          4.68K 100%   37.43kB/s    0:00:00 (xfr#504, to-chk=47/588)
include/usb_osintf.h
            953 100%    7.63kB/s    0:00:00 (xfr#505, to-chk=46/588)
include/usb_vendor_req.h
          2.01K 100%   16.07kB/s    0:00:00 (xfr#506, to-chk=45/588)
include/wifi.h
         46.34K 100%  367.88kB/s    0:00:00 (xfr#507, to-chk=44/588)
include/wlan_bssdef.h
         21.98K 100%  174.51kB/s    0:00:00 (xfr#508, to-chk=43/588)
include/xmit_osdep.h
          2.63K 100%   20.87kB/s    0:00:00 (xfr#509, to-chk=42/588)
include/byteorder/
include/byteorder/big_endian.h
          3.21K 100%   25.52kB/s    0:00:00 (xfr#510, to-chk=38/588)
include/byteorder/generic.h
          7.18K 100%   56.98kB/s    0:00:00 (xfr#511, to-chk=37/588)
include/byteorder/little_endian.h
          3.39K 100%   26.88kB/s    0:00:00 (xfr#512, to-chk=36/588)
include/byteorder/swab.h
          3.27K 100%   25.98kB/s    0:00:00 (xfr#513, to-chk=35/588)
include/byteorder/swabb.h
          4.02K 100%   31.92kB/s    0:00:00 (xfr#514, to-chk=34/588)
include/cmn_info/
include/cmn_info/rtw_sta_info.h
          7.72K 100%   61.27kB/s    0:00:00 (xfr#515, to-chk=33/588)
include/linux/
include/linux/wireless.h
          2.74K 100%   21.56kB/s    0:00:00 (xfr#516, to-chk=32/588)
os_dep/
os_dep/osdep_service.c
         57.84K 100%  455.48kB/s    0:00:00 (xfr#517, to-chk=31/588)
os_dep/linux/
os_dep/linux/custom_gpio_linux.c
          8.42K 100%   66.30kB/s    0:00:00 (xfr#518, to-chk=29/588)
os_dep/linux/ioctl_cfg80211.c
        233.49K 100%    1.77MB/s    0:00:00 (xfr#519, to-chk=28/588)
os_dep/linux/ioctl_cfg80211.h
         13.47K 100%  104.40kB/s    0:00:00 (xfr#520, to-chk=27/588)
os_dep/linux/ioctl_linux.c
        371.50K 100%    2.79MB/s    0:00:00 (xfr#521, to-chk=26/588)
os_dep/linux/ioctl_mp.c
         71.94K 100%  548.85kB/s    0:00:00 (xfr#522, to-chk=25/588)
os_dep/linux/mlme_linux.c
         11.34K 100%   86.48kB/s    0:00:00 (xfr#523, to-chk=24/588)
os_dep/linux/os_intfs.c
        138.21K 100%    1.03MB/s    0:00:00 (xfr#524, to-chk=23/588)
os_dep/linux/recv_linux.c
         19.15K 100%  146.09kB/s    0:00:00 (xfr#525, to-chk=22/588)
os_dep/linux/rtw_android.c
         34.27K 100%  261.49kB/s    0:00:00 (xfr#526, to-chk=21/588)
os_dep/linux/rtw_cfgvendor.c
         45.66K 100%  345.70kB/s    0:00:00 (xfr#527, to-chk=20/588)
os_dep/linux/rtw_cfgvendor.h
         24.11K 100%  182.50kB/s    0:00:00 (xfr#528, to-chk=19/588)
os_dep/linux/rtw_proc.c
         91.19K 100%  690.32kB/s    0:00:00 (xfr#529, to-chk=18/588)
os_dep/linux/rtw_proc.h
          2.00K 100%   15.18kB/s    0:00:00 (xfr#530, to-chk=17/588)
os_dep/linux/usb_intf.c
         52.23K 100%  392.32kB/s    0:00:00 (xfr#531, to-chk=16/588)
os_dep/linux/usb_ops_linux.c
         28.78K 100%  216.21kB/s    0:00:00 (xfr#532, to-chk=15/588)
os_dep/linux/wifi_regd.c
         13.96K 100%  104.83kB/s    0:00:00 (xfr#533, to-chk=14/588)
os_dep/linux/xmit_linux.c
         14.04K 100%  105.47kB/s    0:00:00 (xfr#534, to-chk=13/588)
platform/
platform/custom_country_chplan.h
          1.04K 100%    7.85kB/s    0:00:00 (xfr#535, to-chk=12/588)
platform/platform_ARM_SUN50IW1P1_sdio.c
          2.21K 100%   16.62kB/s    0:00:00 (xfr#536, to-chk=11/588)
platform/platform_ARM_SUNnI_sdio.c
          3.51K 100%   26.40kB/s    0:00:00 (xfr#537, to-chk=10/588)
platform/platform_ARM_SUNxI_sdio.c
          2.67K 100%   20.03kB/s    0:00:00 (xfr#538, to-chk=9/588)
platform/platform_ARM_SUNxI_usb.c
          3.90K 100%   29.26kB/s    0:00:00 (xfr#539, to-chk=8/588)
platform/platform_ARM_WMT_sdio.c
          1.53K 100%   11.51kB/s    0:00:00 (xfr#540, to-chk=7/588)
platform/platform_RTK_DMP_usb.c
            966 100%    7.26kB/s    0:00:00 (xfr#541, to-chk=6/588)
platform/platform_arm_act_sdio.c
          1.35K 100%   10.16kB/s    0:00:00 (xfr#542, to-chk=5/588)
platform/platform_ops.c
            897 100%    6.74kB/s    0:00:00 (xfr#543, to-chk=4/588)
platform/platform_ops.h
            887 100%    6.66kB/s    0:00:00 (xfr#544, to-chk=3/588)
platform/platform_sprd_sdio.c
          2.05K 100%   15.38kB/s    0:00:00 (xfr#545, to-chk=2/588)
regdb/
regdb/regulatory.db
          3.58K 100%   26.89kB/s    0:00:00 (xfr#546, to-chk=1/588)
regdb/regulatory.db.p7s
          1.18K 100%    8.88kB/s    0:00:00 (xfr#547, to-chk=0/588)

sent 17.83M bytes  received 10.71K bytes  35.68M bytes/sec
total size is 17.79M  speedup is 1.00
joe@joe-GA-78LMT-USB3:~/rtl8812au$ sudo dkms add -m rtl8812au -v 5.2.20

Creating symlink /var/lib/dkms/rtl8812au/5.2.20/source ->
                 /usr/src/rtl8812au-5.2.20

DKMS: add completed.
joe@joe-GA-78LMT-USB3:~/rtl8812au$ sudo dkms build -m rtl8812au -v 5.2.20

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area...
'make' -j8 KVER=5.3.0-46-generic KSRC=/lib/modules/5.3.0-46-generic/build.........
cleaning build area...

DKMS: build completed.
joe@joe-GA-78LMT-USB3:~/rtl8812au$ sudo dkms install -m rtl8812au -v 5.2.20

8812au:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.3.0-46-generic/updates/dkms/

depmod...

DKMS: install completed.
joe@joe-GA-78LMT-USB3:~/rtl8812au$ sudo modprobe 8812au
joe@joe-GA-78LMT-USB3:~/rtl8812au$ 

```

---

### Post by chili555 on 2020-04-16
Let's see:

```
dmesg | grep -e wlx -e 8812 -e RTL
```

---

### Post by Joe_Linux on 2020-04-16
> **chili555 said:**
> Let's see:

```
dmesg | grep -e wlx -e 8812 -e RTL
```

```
 
joe@joe-GA-78LMT-USB3:~$ dmesg | grep -e wlx -e 8812 -e RTL
[    1.825750] r8169 0000:03:00.0 eth0: RTL8168evl/8111evl, 74:d4:35:99:c7:48, XID 2c9, IRQ 28
[    5.809344] RTL8211E Gigabit Ethernet r8169-300:00: attached PHY driver [RTL8211E Gigabit Ethernet] (mii_bus:phy_addr=r8169-300:00, irq=IGNORE)
[   56.649826] rtl8812au: loading out-of-tree module taints kernel.
[   56.651046] rtl8812au: module verification failed: signature and/or required key missing - tainting kernel
[   56.655062] RTL871X: module init start
[   56.655064] RTL871X: rtl8812au v4.3.14_13455.20150212_BTCOEX20150128-51
[   56.655065] RTL871X: rtl8812au BT-Coex version = BTCOEX20150128-51
[   56.803416] Modules linked in: rtl8812au(OE+) cfg80211 snd_hda_codec_hdmi edac_mce_amd ccp kvm irqbypass snd_hda_codec_via snd_hda_codec_generic ledtrig_audio nouveau snd_hda_intel snd_intel_nhlt snd_hda_codec snd_hda_core crct10dif_pclmul snd_hwdep crc32_pclmul mxm_wmi snd_pcm ghash_clmulni_intel video ttm snd_seq_midi aesni_intel snd_seq_midi_event drm_kms_helper aes_x86_64 crypto_simd snd_rawmidi drm cryptd snd_seq i2c_algo_bit glue_helper fb_sys_fops snd_seq_device joydev input_leds syscopyarea snd_timer sysfillrect serio_raw sysimgblt wmi_bmof snd soundcore fam15h_power k10temp mac_hid sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 hid_generic usbhid hid pata_acpi ahci r8169 libahci i2c_piix4 pata_atiixp realtek wmi
[   56.803573]  ? _rtw_malloc+0x2d/0x2f [rtl8812au]
[   56.803622]  ? _rtw_memcpy+0x10/0x12 [rtl8812au]
[   56.803673]  ? rtw_5g_rates_init+0x1a/0x1c [rtl8812au]
[   56.803724]  rtw_wdev_alloc+0x10a/0x2b0 [rtl8812au]
[   56.803775]  ? rtw_wdev_alloc+0x10a/0x2b0 [rtl8812au]
[   56.803825]  rtw_usb_if1_init+0x138/0x202 [rtl8812au]
[   56.803875]  rtw_drv_init+0x23d/0x2d6 [rtl8812au]
[   56.803947]  rtw_drv_entry+0x86/0x1000 [rtl8812au]
[   56.917866] usbcore: registered new interface driver rtl8812au
[   56.917868] RTL871X: module init ret=0
[   65.624068] rt2800usb 1-2.2:1.0 wlx00120eb1f7aa: renamed from wlan0
[   67.356896] wlx00120eb1f7aa: authenticate with 38:3b:c8:62:92:86
[   67.379495] wlx00120eb1f7aa: send auth to 38:3b:c8:62:92:86 (try 1/3)
[   67.387462] wlx00120eb1f7aa: authenticated
[   67.388679] wlx00120eb1f7aa: associate with 38:3b:c8:62:92:86 (try 1/3)
[   67.392023] wlx00120eb1f7aa: RX AssocResp from 38:3b:c8:62:92:86 (capab=0x411 status=0 aid=3)
[   67.398936] wlx00120eb1f7aa: associated
[   67.947138] IPv6: ADDRCONF(NETDEV_CHANGE): wlx00120eb1f7aa: link becomes ready
[  190.576551] wlx00120eb1f7aa: deauthenticating from 38:3b:c8:62:92:86 by local choice (Reason: 3=DEAUTH_LEAVING)
[  348.907904] rt2800usb 1-2.1.1:1.0 wlx38607727ae57: renamed from wlan0
[  382.499670] wlx38607727ae57: authenticate with 38:3b:c8:62:92:86
[  382.532281] wlx38607727ae57: send auth to 38:3b:c8:62:92:86 (try 1/3)
[  382.540135] wlx38607727ae57: authenticated
[  382.543897] wlx38607727ae57: associate with 38:3b:c8:62:92:86 (try 1/3)
[  382.549372] wlx38607727ae57: RX AssocResp from 38:3b:c8:62:92:86 (capab=0x411 status=0 aid=3)
[  382.560108] wlx38607727ae57: associated
[  382.586296] IPv6: ADDRCONF(NETDEV_CHANGE): wlx38607727ae57: link becomes ready
[  470.583227] wlx38607727ae57: deauthenticating from 38:3b:c8:62:92:86 by local choice (Reason: 3=DEAUTH_LEAVING)
joe@joe-GA-78LMT-USB3:~$ 

```

---

### Post by chili555 on 2020-04-16
> 
[   65.624068] [COLOR="#FF0000"]rt2800usb[/COLOR] 1-2.2:1.0 wlx00120eb1f7aa: renamed from wlan0
[   67.356896] wlx00120eb1f7aa: authenticate with 38:3b:c8:62:92:86
[   67.379495] wlx00120eb1f7aa: send auth to 38:3b:c8:62:92:86 (try 1/3)
[   67.387462] wlx00120eb1f7aa: authenticated
And next:> 
[  348.907904] rt2800usb 1-2.1.1:1.0 wlx38607727ae57: renamed from wlan0
[  382.499670] wlx38607727ae57: authenticate with 38:3b:c8:62:92:86
[  382.532281] wlx38607727ae57: send auth to 38:3b:c8:62:92:86 (try 1/3)
[  382.540135] wlx38607727ae57: authenticated
Is yours a Realtak 8812au device or a Ralink/Mediatek rt2800usb device??????????????????????????????

I don't understand why you get two different interface designations,  wlx00120eb1f7aa and then wlx38607727ae57.

In both cases, you seem to connect just fine.

I have trouble trying to troubleshoot two devices and drivers at once.

Please explain.

---

### Post by Joe_Linux on 2020-04-17
I have another usb wireless adapter Mvix. I have removed it (removed it from a usb port) Sorry. It is only 802.11n, I wanted 802.11ac
Sorry I took so long to respond.

[http://en.techinfodepot.shoutwiki.com/wiki/Mvix_Nubbin_(MS-811N)]("http://en.techinfodepot.shoutwiki.com/wiki/Mvix_Nubbin_(MS-811N)")

This it what I tried on my own 
```

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

joe@joe-GA-78LMT-USB3:~$ sudo lsmod
[sudo] password for joe: 
Module                  Size  Used by
rfcomm                 81920  4
bnep                   24576  2
btusb                  57344  0
btrtl                  20480  1 btusb
btbcm                  16384  1 btusb
btintel                24576  1 btusb
bluetooth             573440  31 btrtl,btintel,btbcm,bnep,btusb,rfcomm
ecdh_generic           16384  1 bluetooth
ecc                    32768  1 ecdh_generic
rtl8812au            1351680  0
cfg80211              704512  1 rtl8812au
snd_hda_codec_hdmi     57344  1
edac_mce_amd           32768  0
ccp                    90112  0
kvm                   655360  0
snd_hda_codec_via      20480  1
snd_hda_codec_generic    81920  1 snd_hda_codec_via
irqbypass              16384  1 kvm
ledtrig_audio          16384  1 snd_hda_codec_generic
snd_hda_intel          53248  8
snd_intel_nhlt         20480  1 snd_hda_intel
snd_hda_codec         131072  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_via
snd_hda_core           90112  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_via
snd_hwdep              20480  1 snd_hda_codec
nouveau              1892352  24
snd_pcm               102400  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
snd_seq_midi           20480  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            36864  1 snd_seq_midi
crct10dif_pclmul       16384  1
mxm_wmi                16384  1 nouveau
snd_seq                69632  2 snd_seq_midi,snd_seq_midi_event
crc32_pclmul           16384  0
video                  49152  1 nouveau
ghash_clmulni_intel    16384  0
ttm                   102400  1 nouveau
drm_kms_helper        180224  1 nouveau
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
aesni_intel           372736  0
drm                   491520  17 drm_kms_helper,ttm,nouveau
snd_timer              36864  2 snd_seq,snd_pcm
aes_x86_64             20480  1 aesni_intel
i2c_algo_bit           16384  1 nouveau
fb_sys_fops            16384  1 drm_kms_helper
crypto_simd            16384  1 aesni_intel
syscopyarea            16384  1 drm_kms_helper
input_leds             16384  0
sysfillrect            16384  1 drm_kms_helper
joydev                 28672  0
sysimgblt              16384  1 drm_kms_helper
cryptd                 24576  2 crypto_simd,ghash_clmulni_intel
glue_helper            16384  1 aesni_intel
serio_raw              20480  0
snd                    86016  27 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_timer,snd_hda_codec_via,snd_pcm,snd_rawmidi
wmi_bmof               16384  0
soundcore              16384  1 snd
fam15h_power           16384  0
k10temp                16384  0
mac_hid                16384  0
sch_fq_codel           20480  2
parport_pc             40960  1
ppdev                  24576  0
lp                     20480  0
parport                53248  3 parport_pc,lp,ppdev
ip_tables              32768  0
x_tables               40960  1 ip_tables
autofs4                45056  2
hid_generic            16384  0
usbhid                 53248  0
hid                   126976  2 usbhid,hid_generic
pata_acpi              16384  0
i2c_piix4              28672  0
r8169                  81920  0
ahci                   40960  1
pata_atiixp            16384  0
libahci                32768  1 ahci
realtek                20480  1
wmi                    32768  3 wmi_bmof,mxm_wmi,nouveau
joe@joe-GA-78LMT-USB3:~$ rmmod cfg80211              704512
rmmod: ERROR: Module cfg80211 is in use by: rtl8812au
rmmod: ERROR: Module 704512 is not currently loaded
joe@joe-GA-78LMT-USB3:~$ rmmod cfg80211
rmmod: ERROR: Module cfg80211 is in use by: rtl8812au
joe@joe-GA-78LMT-USB3:~$ rmmod rtl8812au
rmmod: ERROR: ../libkmod/libkmod-module.c:793 kmod_module_remove_module() could not remove 'rtl8812au': Operation not permitted
rmmod: ERROR: could not remove module rtl8812au: Operation not permitted
joe@joe-GA-78LMT-USB3:~$ sudo rmmod rtl8812au
joe@joe-GA-78LMT-USB3:~$ sudo cfg80211
sudo: cfg80211: command not found
joe@joe-GA-78LMT-USB3:~$ sudo rmmod cfg80211
joe@joe-GA-78LMT-USB3:~$ sudo modprobe rtl8812au
joe@joe-GA-78LMT-USB3:~$ sudo lsmod 
Module                  Size  Used by
rtl8812au            1351680  0
cfg80211              704512  1 rtl8812au
rfcomm                 81920  4
bnep                   24576  2
btusb                  57344  0
btrtl                  20480  1 btusb
btbcm                  16384  1 btusb
btintel                24576  1 btusb
bluetooth             573440  31 btrtl,btintel,btbcm,bnep,btusb,rfcomm
ecdh_generic           16384  1 bluetooth
ecc                    32768  1 ecdh_generic
snd_hda_codec_hdmi     57344  1
edac_mce_amd           32768  0
ccp                    90112  0
kvm                   655360  0
snd_hda_codec_via      20480  1
snd_hda_codec_generic    81920  1 snd_hda_codec_via
irqbypass              16384  1 kvm
ledtrig_audio          16384  1 snd_hda_codec_generic
snd_hda_intel          53248  8
snd_intel_nhlt         20480  1 snd_hda_intel
snd_hda_codec         131072  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_via
snd_hda_core           90112  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_via
snd_hwdep              20480  1 snd_hda_codec
nouveau              1892352  24
snd_pcm               102400  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
snd_seq_midi           20480  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            36864  1 snd_seq_midi
crct10dif_pclmul       16384  1
mxm_wmi                16384  1 nouveau
snd_seq                69632  2 snd_seq_midi,snd_seq_midi_event
crc32_pclmul           16384  0
video                  49152  1 nouveau
ghash_clmulni_intel    16384  0
ttm                   102400  1 nouveau
drm_kms_helper        180224  1 nouveau
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
aesni_intel           372736  0
drm                   491520  17 drm_kms_helper,ttm,nouveau
snd_timer              36864  2 snd_seq,snd_pcm
aes_x86_64             20480  1 aesni_intel
i2c_algo_bit           16384  1 nouveau
fb_sys_fops            16384  1 drm_kms_helper
crypto_simd            16384  1 aesni_intel
syscopyarea            16384  1 drm_kms_helper
input_leds             16384  0
sysfillrect            16384  1 drm_kms_helper
joydev                 28672  0
sysimgblt              16384  1 drm_kms_helper
cryptd                 24576  2 crypto_simd,ghash_clmulni_intel
glue_helper            16384  1 aesni_intel
serio_raw              20480  0
snd                    86016  27 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_timer,snd_hda_codec_via,snd_pcm,snd_rawmidi
wmi_bmof               16384  0
soundcore              16384  1 snd
fam15h_power           16384  0
k10temp                16384  0
mac_hid                16384  0
sch_fq_codel           20480  2
parport_pc             40960  1
ppdev                  24576  0
lp                     20480  0
parport                53248  3 parport_pc,lp,ppdev
ip_tables              32768  0
x_tables               40960  1 ip_tables
autofs4                45056  2
hid_generic            16384  0
usbhid                 53248  0
hid                   126976  2 usbhid,hid_generic
pata_acpi              16384  0
i2c_piix4              28672  0
r8169                  81920  0
ahci                   40960  1
pata_atiixp            16384  0
libahci                32768  1 ahci
realtek                20480  1
wmi                    32768  3 wmi_bmof,mxm_wmi,nouveau
joe@joe-GA-78LMT-USB3:~$ 

```

---

### Post by Joe_Linux on 2020-04-18
morrownr 
May I ask what version of Ubuntu and what kernel you are using ?
I am using Ubuntu Ubuntu 18.04.4 with 5.3.0-46-generic kernel.
Do you think the driver will work with this ?

---

### Post by Joe_Linux on 2020-04-19
bump

---

### Post by charles-scoville on 2020-04-19
Hi,

I'm n00bish enough that you should take what I say with a grain of salt, but have you tried a live boot or another system to real quick rule out a config vs. blown adapter issue?

I only butt in because I too have the same rtl8812au chipset in a USB device and I too have had some hit/miss issues with mine. Kali on one system works with it, on another doesn't. At the same time, with Kubuntu and Manjaro, the place where the adapter works switch on me.

Anyway, doing that for me was a useful diagnostic step to gain some insight. If you get similar results, it's a pattern. My 2c

---

### Post by charles-scoville on 2020-04-19
> **morrownr said:**
> I also have a usb wifi adapter based on the rtl8812au chipset.

The driver I use is located here: [https://github.com/aircrack-ng/rtl8812au](https://github.com/aircrack-ng/rtl8812au)

This driver is well maintained.

I'm curious, is that driver compatible with other (read: older) Kernels? It  looks like it's dkms, so... yes? I too have the same adapter, and I'm on 18.04 LTS, however [FONT=fixedsys]uname -r[/FONT] is reporting back my kernel as 4.15.0-96-generic. But, if that driver is better, I'd like to use it.

Hummm ... Actually

Come to think of it, my Manjaro system has a 5.6.x kernel, and I believe it is one of the systems that has trouble even getting this adapter running!

... Let me check real quick. ...

Yes! My Manjaro install, with kernel 5.6.3-2-MANJARO does NOT automatically load the kernel module for this same adapter (0bda:0811 Realtek Semiconductor Corp.) where as my Kubuntu 18.04 LTS install, on kernel 4.15.096-generic does, and the adapter works fine on this system.

Here is the dmesg output for when I install the adaptor on Kubuntu. *
```
[105163.438329] usb 1-1.3: new high-speed USB device number 7 using ehci-pci
[105163.547378] usb 1-1.3: New USB device found, idVendor=0bda, idProduct=0811               
[105163.547384] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3          
[105163.547387] usb 1-1.3: Product: 802.11ac WLAN Adapter                                    
[105163.547389] usb 1-1.3: Manufacturer: Realtek                                             
[105163.547391] usb 1-1.3: SerialNumber: 000000000001                                        
[105164.294141] 8812au: version magic '4.15.0-91-generic SMP mod_unload ' should be '4.15.0-96-generic SMP mod_unload '                                                                   
[105164.351564] 88XXau: loading out-of-tree module taints kernel.                            
[105164.353369] 88XXau: module verification failed: signature and/or required key missing - tainting kernel                                                                               
[105164.509132] usb 1-1.3: 88XXau 12:34:5a:bc:de hw_info[107]
[105164.514740] usbcore: registered new interface driver 88XXau 
```

And here is my Manjaro output of the same.*
```
[  598.190089] usb 2-1.2: new high-speed USB device number 4 using ehci-pci
[  598.218297] usb 2-1.2: New USB device found, idVendor=0bda, idProduct=0811, bcdDevice= 2.00
[  598.218301] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  598.218304] usb 2-1.2: Product: 802.11ac WLAN Adapter 
[  598.218306] usb 2-1.2: Manufacturer: Realtek 
[  598.218308] usb 2-1.2: SerialNumber: 000000000001
```

notice that, on the latter case, it just stops after the SerialNumber, and provides no further rtl8812au related output. 

When I get a bit more time I may try using that git repo to build for my Manjaro machine, and report back.

[SIZE=1]*Note that both my adapter serial number and MAC have been obscured for privacy reasons.[/SIZE]

---

### Post by charles-scoville on 2020-04-19
OK, put the dog up and gave this a go.

So, building and installing the aircrack-ng repo, as well as gordboy's repo, either with DKMS, or manually did not work on my Manjaro/5.6.x system. That is including manually using insmod && modprobe to get lsmod to show it as loaded.

Another interesting thing I noted is that plugging in the adapter to the USB ports has some anomalies in dmesg feedback. Particularly, with the Kubuntu 4.15.x system, I will get USB discovery every time I insert and remove the adapter. With the Manjaro 5.6.x system, however, I only get USB discovery feedback when I first insert the device into a port. If I remove it, then reinsert into the same port, I get -ZERO- feedback from dmesg that indicates that this has happened. If I, however, move to a different port, I get USB discovery again. But, again, only for the first time.

Basically, either my caffeine balance is all wrong, or something really screwy is going on with 5.6.x and these adapters. (:/)

---

### Post by chili555 on 2020-04-19
> 
When I get a bit more time I may try using that git repo to build for my Manjaro machine, and report back.We know nothing at all about Manjaro. I suggest that you start your own new thread either here: [https://ubuntuforums.org/forumdisplay.php?f=446](https://ubuntuforums.org/forumdisplay.php?f=446) or, even better, on a Manjaro-specific forum.

---

### Post by charles-scoville on 2020-04-19
> **chili555 said:**
> We know nothing at all about Manjaro. I suggest that you start your own new thread either here: [https://ubuntuforums.org/forumdisplay.php?f=446](https://ubuntuforums.org/forumdisplay.php?f=446) or, even better, on a Manjaro-specific forum.

You're kinda missing the point friend. What I'm saying is this is also  apparently a problem on other distros, not just Ubuntu. That shows that  this is a lower level issue. It clearly has something to do with the  kernel/drivers that are common to more than just Ubuntu. That is useful  information in it's own rite no matter how you want to spell it.

---

### Post by Joe_Linux on 2020-04-19
Well I started this thread in the beginning. I have more than one usb 802.11n adapters that work. Does anyone have personal experience with a 802.11ac usb adapter that currently works with Ubuntu 18.04.4 5.3.0-46-generic kernel ? BTW thank you everyone who tried to help me.

---

### Post by Joe_Linux on 2020-04-20
> **charles-scoville said:**
> I'm curious, is that driver compatible with other (read: older) Kernels? It  looks like it's dkms, so... yes? I too have the same adapter, and I'm on 18.04 LTS, however [FONT=fixedsys]uname -r[/FONT] is reporting back my kernel as 4.15.0-96-generic. But, if that driver is better, I'd like to use it.

Hummm ... Actually

Come to think of it, my Manjaro system has a 5.6.x kernel, and I believe it is one of the systems that has trouble even getting this adapter running!

... Let me check real quick. ...

Yes! My Manjaro install, with kernel 5.6.3-2-MANJARO does NOT automatically load the kernel module for this same adapter (0bda:0811 Realtek Semiconductor Corp.) where as my Kubuntu 18.04 LTS install, on kernel 4.15.096-generic does, and the adapter works fine on this system.

Here is the dmesg output for when I install the adaptor on Kubuntu. *
```
[105163.438329] usb 1-1.3: new high-speed USB device number 7 using ehci-pci
[105163.547378] usb 1-1.3: New USB device found, idVendor=0bda, idProduct=0811               
[105163.547384] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3          
[105163.547387] usb 1-1.3: Product: 802.11ac WLAN Adapter                                    
[105163.547389] usb 1-1.3: Manufacturer: Realtek                                             
[105163.547391] usb 1-1.3: SerialNumber: 000000000001                                        
[105164.294141] 8812au: version magic '4.15.0-91-generic SMP mod_unload ' should be '4.15.0-96-generic SMP mod_unload '                                                                   
[105164.351564] 88XXau: loading out-of-tree module taints kernel.                            
[105164.353369] 88XXau: module verification failed: signature and/or required key missing - tainting kernel                                                                               
[105164.509132] usb 1-1.3: 88XXau 12:34:5a:bc:de hw_info[107]
[105164.514740] usbcore: registered new interface driver 88XXau 
```

And here is my Manjaro output of the same.*
```
[  598.190089] usb 2-1.2: new high-speed USB device number 4 using ehci-pci
[  598.218297] usb 2-1.2: New USB device found, idVendor=0bda, idProduct=0811, bcdDevice= 2.00
[  598.218301] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  598.218304] usb 2-1.2: Product: 802.11ac WLAN Adapter 
[  598.218306] usb 2-1.2: Manufacturer: Realtek 
[  598.218308] usb 2-1.2: SerialNumber: 000000000001
```

notice that, on the latter case, it just stops after the SerialNumber, and provides no further rtl8812au related output. 

When I get a bit more time I may try using that git repo to build for my Manjaro machine, and report back.

[SIZE=1]*Note that both my adapter serial number and MAC have been obscured for privacy reasons.[/SIZE]

charles-scoville

I will ask the question why are you using an older kernel ?
Thank you

---

### Post by charles-scoville on 2020-04-20
> **Joe_Linux said:**
> charles-scoville

I will ask the question why are you using an older kernel ?
Thank you

I was kinda asking myself the same question, until I noticed this problem, and now I'm wondering if I shouldn't be glad I am.

If I had to guess as to why, I'd say it's because I'm on an LTS release, which I don't think loads in a newer kernel by default? Other than that, I don't know. 

TBH, I don't notice any problems with my Kubuntu system NOT being on the newer kernel, if that means anything. In particular, the adapter in question works fine on it.

---

### Post by Joe_Linux on 2020-04-20
Thanks for responding 
charles-scoville

---

### Post by Joe_Linux on 2020-04-20
I did get my adapter to work in Ubuntu 18.04.4 LTS using 5.3.0-46-generic kernel. Identified as Bus 001 Device 010: ID 0bda:0811 Realtek Semiconductor Corp. by lsusb.
I found from this page [https://askubuntu.com/questions/1185952/need-rtl8814au-driver-for-kernel-5-3-on-ubuntu-19-10]("https://askubuntu.com/questions/1185952/need-rtl8814au-driver-for-kernel-5-3-on-ubuntu-19-10")
I did this 
```

oe@joe-GA-78LMT-USB3:~$ sudo apt install git dkms
[sudo] password for joe:
Reading package lists... Done
Building dependency tree
Reading state information... Done
dkms is already the newest version (2.3-3ubuntu9.7).
dkms set to manually installed.
git is already the newest version (1:2.17.1-1ubuntu0.6).
The following packages were automatically installed and are no longer required:
libllvm7 libllvm8
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
joe@joe-GA-78LMT-USB3:~$ git clone https://github.com/aircrack-ng/rtl8812au.git
Cloning into 'rtl8812au'...
remote: Enumerating objects: 10205, done.
remote: Total 10205 (delta 0), reused 0 (delta 0), pack-reused 10205
Receiving objects: 100% (10205/10205), 69.58 MiB | 2.02 MiB/s, done.
Resolving deltas: 100% (7122/7122), done.
joe@joe-GA-78LMT-USB3:~$ cd rtl8812au
joe@joe-GA-78LMT-USB3:~/rtl8812au$ sudo ./dkms-install.sh
About to run dkms install steps...
Creating symlink /var/lib/dkms/rtl8812au/5.6.4.2/source ->
/usr/src/rtl8812au-5.6.4.2
DKMS: add completed.
Kernel preparation unnecessary for this kernel. Skipping...
Building module:
cleaning build area...
'make' -j8 KVER=5.3.0-46-generic KSRC=/lib/modules/5.3.0-46-generic/build.............
cleaning build area...
DKMS: build completed.
88XXau:
Running module version sanity check.
- Original module
- This kernel never originally had a module by this name
- Installation
- Installing to /lib/modules/5.3.0-46-generic/updates/dkms/
depmod....
DKMS: install completed.
Finished running dkms install steps.
joe@joe-GA-78LMT-USB3:~/rtl8812au$

```
And after at least one reboot the adapter is working. Again thank you everyone

---

### Post by chili555 on 2020-04-21
> You're kinda missing the point friend. What I'm saying is this is also apparently a problem on other distros, not just Ubuntu. That shows that this is a lower level issue. It clearly has something to do with the kernel/drivers that are common to more than just Ubuntu. That is useful information in it's own rite no matter how you want to spell it.

I'm not missing the point at all. You clearly said:

> my Kubuntu 18.04 LTS install, on kernel 4.15.096-generic does, and the adapter works fine on this system.

So that's not a question or problem we need to solve here on ubuntuforums.org. You also said:

> My Manjaro install, with kernel 5.6.3-2-MANJARO does NOT automatically load the kernel module for this same adapter (0bda:0811

That's also not a problem that we can address and solve here.

I can think of no possible way that the fact that the driver doesn't work in Manjaro and that it doesn't work in a 5.6.xx kernel is useful here. The latest mainstream kernel in a standard Ubuntu system is 5.3.xx. In a few days, Ubuntu 20.04 will be released. It will use kernel version 5.4.xx. 

Included in the official Ubuntu repositories in the package *rtl8812au-dkms*. I have no reason to assume that it won't be tested and shown to work in 20.04.

We are not kernel developers here, nor are we driver developers. Almost all of us are volunteers with other non-Linux lives.

The drivers for newer devices come first from the manufacturer of the chipset, in this case Realtek. They never, in any official way that I am aware of, update the drivers as newer kernel versions come along and different, often vastly different, Linux distributuions come along. That task is left to intrepid souls who update the driver independently, sometimes notably on github.

You referenced the git repository for gordboy. I don't know which of the repos you cloned, but you might try: [https://github.com/gordboy/rtl8812au-5.6.4.2](https://github.com/gordboy/rtl8812au-5.6.4.2). If it doesn't work as expected, raise an issue with gordboy. [https://github.com/gordboy/rtl8812au-5.6.4.2/issues](https://github.com/gordboy/rtl8812au-5.6.4.2/issues) He rewrites code; we do not.

---

### Post by Joe_Linux on 2020-04-28
> **Joe_Linux said:**
> I did get my adapter to work in Ubuntu 18.04.4 LTS using 5.3.0-46-generic kernel. Identified as Bus 001 Device 010: ID 0bda:0811 Realtek Semiconductor Corp. by lsusb.
I found from this page [https://askubuntu.com/questions/1185952/need-rtl8814au-driver-for-kernel-5-3-on-ubuntu-19-10]("https://askubuntu.com/questions/1185952/need-rtl8814au-driver-for-kernel-5-3-on-ubuntu-19-10")
I did this 
```

oe@joe-GA-78LMT-USB3:~$ sudo apt install git dkms
[sudo] password for joe:
Reading package lists... Done
Building dependency tree
Reading state information... Done
dkms is already the newest version (2.3-3ubuntu9.7).
dkms set to manually installed.
git is already the newest version (1:2.17.1-1ubuntu0.6).
The following packages were automatically installed and are no longer required:
libllvm7 libllvm8
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
joe@joe-GA-78LMT-USB3:~$ git clone https://github.com/aircrack-ng/rtl8812au.git
Cloning into 'rtl8812au'...
remote: Enumerating objects: 10205, done.
remote: Total 10205 (delta 0), reused 0 (delta 0), pack-reused 10205
Receiving objects: 100% (10205/10205), 69.58 MiB | 2.02 MiB/s, done.
Resolving deltas: 100% (7122/7122), done.
joe@joe-GA-78LMT-USB3:~$ cd rtl8812au
joe@joe-GA-78LMT-USB3:~/rtl8812au$ sudo ./dkms-install.sh
About to run dkms install steps...
Creating symlink /var/lib/dkms/rtl8812au/5.6.4.2/source ->
/usr/src/rtl8812au-5.6.4.2
DKMS: add completed.
Kernel preparation unnecessary for this kernel. Skipping...
Building module:
cleaning build area...
'make' -j8 KVER=5.3.0-46-generic KSRC=/lib/modules/5.3.0-46-generic/build.............
cleaning build area...
DKMS: build completed.
88XXau:
Running module version sanity check.
- Original module
- This kernel never originally had a module by this name
- Installation
- Installing to /lib/modules/5.3.0-46-generic/updates/dkms/
depmod....
DKMS: install completed.
Finished running dkms install steps.
joe@joe-GA-78LMT-USB3:~/rtl8812au$

```
And after at least one reboot the adapter is working. Again thank you everyone

Just to lt anyone know (FYI) the above works on a live USB adapter with persistence  of Ubuntu 20.04

---

