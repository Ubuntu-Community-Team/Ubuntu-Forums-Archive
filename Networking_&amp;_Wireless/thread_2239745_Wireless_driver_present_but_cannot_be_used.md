---
title: "Wireless driver present but cannot be used"
date: 2014-08-15
forum: Networking &amp; Wireless
---

### Post by ahmade-usa-170 on 2014-08-15
i have used both ndiswrapper and backport to get this driver working

here is what lspci gets me
```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation 7 Series Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8723
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)


```
and here is what ndiswrapper -m gets me
```
 adding "alias wlan0 ndiswrapper" to  ...
sh: 1: Syntax error: end of file unexpected
couldn't add module alias:  at /usr/sbin/ndiswrapper line 825.


```
and here is ndiswrapper -l
```
netrtwlane : driver installed
    device (10EC:8723) present (alternate driver: rtl8723ae)


```
if it helps i also tried to compile the driver from the dropbox thing and it wont work it gives me that the file isnt there any help is apperciated

---

### Post by chili555 on 2014-08-15
First, the driver rtl8723ae is present in newer Ubuntu versions. What version are you running?```
lsb_release -d
```What do these diagnostics tell us?```
rfkill list all
dmesg | grep rtl
dmesg | grep ndis
```Thanks.

---

### Post by ahmade-usa-170 on 2014-08-15
forgot to mention that im running debain but my ISP is blocked from their site so i cant access their fourms

```
Description:    Debian GNU/Linux 7.6 (wheezy)
```
rfkill list all
```
command not found :/
```
dmesg / grep rtl
```
root@steamos:/home/desktop/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012# dmesg | grep rtl
[    9.257717] rtl8723ae: Unknown symbol rtl_pci_disconnect (err 0)
[    9.257747] rtl8723ae: Unknown symbol rtl_pci_suspend (err 0)
[    9.257815] rtl8723ae: Unknown symbol rtl_pci_resume (err 0)
[    9.257886] rtl8723ae: Unknown symbol rtl_pci_probe (err 0)
[   24.042997] r8169 0000:03:00.0: firmware: agent loaded rtl_nic/rtl8105e-1.fw into memory
[   27.842197] Modules linked in: rfcomm bnep ipheth rtl8723_common(O) rtlwifi(O) mac80211(O) joydev cfg80211(O) snd_hda_codec_hdmi snd_hda_codec_realtek uvcvideo coretemp videobuf2_vmalloc videobuf2_memops snd_hda_intel videobuf2_core snd_hda_codec videodev crc32c_intel ghash_clmulni_intel cryptd snd_hwdep btusb psmouse acpi_cpufreq mperf iTCO_wdt i2c_i801 iTCO_vendor_support lpc_ich bluetooth media snd_pcm snd_page_alloc snd_timer mei_me compat(O) ac processor battery sparse_keymap mfd_core rfkill snd microcode toshiba_bluetooth soundcore pcspkr serio_raw mei evdev ext4 crc16 jbd2 mbcache sg sr_mod sd_mod cdrom crc_t10dif ums_realtek usb_storage thermal wmi ahci libahci i915 video button i2c_algo_bit xhci_hcd ehci_pci ehci_hcd drm_kms_helper drm i2c_core thermal_sys r8169 mii libata scsi_mod usbcore usb_common
[   48.697406] rtl8723ae: Unknown symbol rtl_pci_disconnect (err 0)
[   48.697425] rtl8723ae: Unknown symbol rtl_pci_suspend (err 0)
[   48.697468] rtl8723ae: Unknown symbol rtl_pci_resume (err 0)
[   48.697514] rtl8723ae: Unknown symbol rtl_pci_probe (err 0)
[ 3464.249552] rtl8723ae: Unknown symbol rtl_pci_disconnect (err 0)
[ 3464.249570] rtl8723ae: Unknown symbol rtl_pci_suspend (err 0)
[ 3464.249612] rtl8723ae: Unknown symbol rtl_pci_resume (err 0)
[ 3464.249657] rtl8723ae: Unknown symbol rtl_pci_probe (err 0)


```
dmesg / grep ndis
this one just skips for some reason

---

### Post by chili555 on 2014-08-15
I know nothing or maybe less than nothing about Debian. If you install Ubuntu 14.04, your device will be working perfectly.

It appears you compiled the driver from source code and encountered many errors.

Here is my suggested fix: [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

---

### Post by ahmade-usa-170 on 2014-08-15
i have ubuntu on a CD but i want to try SteamOS because it runs games better
also when i compile the normal driver you linked before this is what happens
```
root@steamos:/home/desktop/Downloads/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012# make
make -C /lib/modules/3.10-3-amd64/build M=/home/desktop/.local/share/Trash/files/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012 modules
make[1]: Entering directory `/usr/src/linux-headers-3.10-3-amd64'
  CC [M]  /home/desktop/.local/share/Trash/files/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.o
In file included from /home/desktop/.local/share/Trash/files/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:39:0:
/home/desktop/.local/share/Trash/files/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/pci.h:245:15: error: expected &#65533;&#65533;&#65533;=&#65533;&#65533;&#65533;, &#65533;&#65533;&#65533;,&#65533;&#65533;&#65533;, &#65533;&#65533;&#65533;;&#65533;&#65533;&#65533;, &#65533;&#65533;&#65533;asm&#65533;&#65533;&#65533; or &#65533;&#65533;&#65533;__attribute__&#65533;&#65533;&#65533; before &#65533;&#65533;&#65533;rtl_pci_probe&#65533;&#65533;&#65533;
/home/desktop/.local/share/Trash/files/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:162:2: error: expected &#65533;&#65533;&#65533;}&#65533;&#65533;&#65533; before numeric constant
/home/desktop/.local/share/Trash/files/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c: In function &#65533;&#65533;&#65533;_rtl_init_mac80211&#65533;&#65533;&#65533;:
/home/desktop/.local/share/Trash/files/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:320:6: error: &#65533;&#65533;&#65533;IEEE80211_HW_BEACON_FILTER&#65533;&#65533;&#65533; undeclared (first use in this function)
/home/desktop/.local/share/Trash/files/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:320:6: note: each undeclared identifier is reported only once for each function it appears in
/home/desktop/.local/share/Trash/files/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:319:35: error: invalid operands to binary | (have &#65533;&#65533;&#65533;int&#65533;&#65533;&#65533; and &#65533;&#65533;&#65533;const u8 *&#65533;&#65533;&#65533;)
/home/desktop/.local/share/Trash/files/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:320:33: error: invalid operands to binary | (have &#65533;&#65533;&#65533;const u8 *&#65533;&#65533;&#65533; and &#65533;&#65533;&#65533;int&#65533;&#65533;&#65533;)
/home/desktop/.local/share/Trash/files/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:321:37: error: invalid operands to binary | (have &#65533;&#65533;&#65533;const u8 *&#65533;&#65533;&#65533; and &#65533;&#65533;&#65533;int&#65533;&#65533;&#65533;)
/home/desktop/.local/share/Trash/files/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:322:41: error: invalid operands to binary | (have &#65533;&#65533;&#65533;const u8 *&#65533;&#65533;&#65533; and &#65533;&#65533;&#65533;int&#65533;&#65533;&#65533;)
/home/desktop/.local/share/Trash/files/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:323:38: error: invalid operands to binary | (have &#65533;&#65533;&#65533;const u8 *&#65533;&#65533;&#65533; and &#65533;&#65533;&#65533;int&#65533;&#65533;&#65533;)
/home/desktop/.local/share/Trash/files/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:325:31: error: invalid operands to binary | (have &#65533;&#65533;&#65533;const u8 *&#65533;&#65533;&#65533; and &#65533;&#65533;&#65533;int&#65533;&#65533;&#65533;)
/home/desktop/.local/share/Trash/files/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:318:12: warning: assignment makes integer from pointer without a cast [enabled by default]
/home/desktop/.local/share/Trash/files/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c: In function &#65533;&#65533;&#65533;rtl_action_proc&#65533;&#65533;&#65533;:
/home/desktop/.local/share/Trash/files/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:867:32: error: &#65533;&#65533;&#65533;struct ieee80211_conf&#65533;&#65533;&#65533; has no member named &#65533;&#65533;&#65533;channel&#65533;&#65533;&#65533;
/home/desktop/.local/share/Trash/files/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:867:40: error: request for member &#65533;&#65533;&#65533;center_freq&#65533;&#65533;&#65533; in something not a structure or union
/home/desktop/.local/share/Trash/files/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:867:22: warning: assignment makes integer from pointer without a cast [enabled by default]
/home/desktop/.local/share/Trash/files/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:868:32: error: &#65533;&#65533;&#65533;struct ieee80211_conf&#65533;&#65533;&#65533; has no member named &#65533;&#65533;&#65533;channel&#65533;&#65533;&#65533;
/home/desktop/.local/share/Trash/files/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:868:40: error: request for member &#65533;&#65533;&#65533;band&#65533;&#65533;&#65533; in something not a structure or union
/home/desktop/.local/share/Trash/files/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:868:22: warning: assignment makes integer from pointer without a cast [enabled by default]
/home/desktop/.local/share/Trash/files/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:870:25: error: &#65533;&#65533;&#65533;RX_FLAG_MACTIME_MPDU&#65533;&#65533;&#65533; undeclared (first use in this function)
/home/desktop/.local/share/Trash/files/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:870:22: error: invalid operands to binary | (have &#65533;&#65533;&#65533;u32&#65533;&#65533;&#65533; and &#65533;&#65533;&#65533;const u8 *&#65533;&#65533;&#65533;)
/home/desktop/.local/share/Trash/files/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:870:7: warning: statement with no effect [-Wunused-value]
/home/desktop/.local/share/Trash/files/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c: In function &#65533;&#65533;&#65533;rtl_send_smps_action&#65533;&#65533;&#65533;:
/home/desktop/.local/share/Trash/files/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:1432:16: error: &#65533;&#65533;&#65533;struct <anonymous>&#65533;&#65533;&#65533; has no member named &#65533;&#65533;&#65533;sta&#65533;&#65533;&#65533;
/home/desktop/.local/share/Trash/files/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:1432:3: warning: statement with no effect [-Wunused-value]
/home/desktop/.local/share/Trash/files/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:1433:24: error: &#65533;&#65533;&#65533;struct ieee80211_conf&#65533;&#65533;&#65533; has no member named &#65533;&#65533;&#65533;channel&#65533;&#65533;&#65533;
/home/desktop/.local/share/Trash/files/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:1433:32: error: request for member &#65533;&#65533;&#65533;band&#65533;&#65533;&#65533; in something not a structure or union
/home/desktop/.local/share/Trash/files/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:1433:14: warning: assignment makes integer from pointer without a cast [enabled by default]
make[4]: *** [/home/desktop/.local/share/Trash/files/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.o] Error 1
make[3]: *** [_module_/home/desktop/.local/share/Trash/files/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012] Error 2
make[2]: *** [sub-make] Error 2
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.10-3-amd64'
make: *** [all] Error 2


```

---

### Post by chili555 on 2014-08-15
That's the thing about forum posts. The post is there forever; however, newer kernels, gcc versions, etc. come along that are now incompatible with that creaky, musty old rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.[COLOR="#FF0000"]2012[/COLOR] driver.

I suggest you try this. Download this file to your desktop: [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.13.2/backports-3.13.2-1.tar.gz](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.13.2/backports-3.13.2-1.tar.gz) Right-click it and select 'Extract Here.' Now, in a terminal:```
cd Desktop/backports-3.13.2-1/
make clean
make defconfig-rtlwifi
make
sudo make install
sudo modprobe rtl8723ae
```Then, we'll probably need to remove all the ndiswrapper stuff.

---

### Post by ahmade-usa-170 on 2014-08-15
im downloading Gnome+Ubuntu just incase it doesnt workout also i did what you said and now its saying
```
ERROR: could not insert 'rtl8723ae': Invalid argument


```

---

### Post by chili555 on 2014-08-15
Did 'make' end in errors or some other abnormal ending? It works for me:```
<snip>
  CC      /home/chili/Desktop/Forum/backports-3.13.2-1/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.mod.o
  LD [M]  /home/chili/Desktop/Forum/backports-3.13.2-1/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko
  CC      /home/chili/Desktop/Forum/backports-3.13.2-1/drivers/net/wireless/rtlwifi/rtl8723ae/rtl8723ae.mod.o
  LD [M]  /home/chili/Desktop/Forum/backports-3.13.2-1/drivers/net/wireless/rtlwifi/rtl8723ae/[COLOR="#FF0000"]rtl8723ae[/COLOR].ko
  CC      /home/chili/Desktop/Forum/backports-3.13.2-1/drivers/net/wireless/rtlwifi/rtl_pci.mod.o
  LD [M]  /home/chili/Desktop/Forum/backports-3.13.2-1/drivers/net/wireless/rtlwifi/rtl_pci.ko
  CC      /home/chili/Desktop/Forum/backports-3.13.2-1/drivers/net/wireless/rtlwifi/rtl_usb.mod.o
<snip>
```

---

### Post by ahmade-usa-170 on 2014-08-15
i uninstalled SteamOS and installed Gnome+Ubuntu  becaue i like Gnome :D if your a mod or something remove this post please :3

---

