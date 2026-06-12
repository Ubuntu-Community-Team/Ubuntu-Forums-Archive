---
title: "my TP-Link TL-WN821N don't work Properly after reboot"
date: 2018-04-09
forum: Networking &amp; Wireless
---

### Post by justin077 on 2018-04-09
Hi,
After my first installation of Ubuntu 16.04 ,my USB-Wireless works well, but immediately after the first reboot, it losses connection constantly. To make it work, i have to unplug and plug it again.

My problem is : it losses connection if i reboot the system, i have to unplug and plug it again.
I tried different drivers installation, it does'nt help. 
What to do ?

```
lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler / Genius NetScroll 120
Bus 003 Device 003: ID 1a2c:2124 China Resource Semico Co., Ltd 
Bus 003 Device 006: ID 2357:0107  
Bus 003 Device 005: ID 8564:1000 Transcend Information, Inc. JetFlash
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```
dmesg | grep rtl
[   11.716053] usb 3-3: rtl8192eu_parse_efuse: dumping efuse (0x200 bytes):
[   11.716132] usb 3-3: rtl8xxxu: Loading firmware rtlwifi/rtl8192eu_nic.bin
[   12.643528] usbcore: registered new interface driver rtl8xxxu
[   12.681326] RTL871X: rtl8192eu v4.4.1_17696.20160509_BTCOEX20160412-0042
[   12.681327] RTL871X: rtl8192eu BT-Coex version = BTCOEX20160412-0042
[   12.681642] usbcore: registered new interface driver rtl8192eu
[   12.683539] rtl8xxxu 3-3:1.0 wlx503eaa457233: renamed from wlan0
[  135.671272] usb 3-3: rtl8192eu_active_to_emu: Disabling MAC timed out
[  146.247864] usb 3-3: rtl8192eu_parse_efuse: dumping efuse (0x200 bytes):
[  146.248016] usb 3-3: rtl8xxxu: Loading firmware rtlwifi/rtl8192eu_nic.bin
[  148.154242] rtl8xxxu 3-3:1.0 wlx503eaa457233: renamed from wlan0
[  242.650556] usb 3-3: rtl8xxxu_bss_info_changed: HT supported

```

```
cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.4 LTS"
Linux manu-desktop 4.13.0-38-generic #43~16.04.1-Ubuntu SMP Wed Mar 14 17:48:43 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

```

```
 rfkill list all
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```
```
lsmod
Module                  Size  Used by
ccm                    20480  6
nls_iso8859_1          16384  1
8192eu               1097728  0
arc4                   16384  2
rtl8xxxu              126976  0
mac80211              782336  1 rtl8xxxu
cfg80211              614400  2 mac80211,8192eu
snd_hda_codec_hdmi     49152  1
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             204800  0
kvm                   589824  1 kvm_intel
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
cryptd                 24576  1 ghash_clmulni_intel
snd_hda_codec_realtek    98304  1
intel_cstate           20480  0
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek


```

---

### Post by wyliecoyoteuk on 2018-04-09
Are you dual booting with Windows, or just Ubuntu?

---

### Post by jeremy31 on 2018-04-09
See if blacklisting the one module helps
```
echo "blacklist 8192eu" | sudo tee /etc/modprobe.d/8192eu.conf
```
Reboot

---

### Post by justin077 on 2018-04-10
Yes, i was dual booting with windows 10.  Now for testing reasons I'm triple booting with Mint18.3. The USB-wifi was not recognized the first time, i installed the driver from Mange, and everything work fine there even after rebooting the system .

I blacklist  8192eu but nothing changed.

---

### Post by wyliecoyoteuk on 2018-04-10
Sometimes when dual booting between Windows and Linux, a wifi card's firmware will be left in an incorrect condition by one OS and the other cannot load it unless you do a "cold boot", i.e. fully power down the pc and reboot.
It seems to be trying to load the firmware and failing, so this may be the cause, as it works if you unplug and replug the Card, which would force a clean reload of the firmware.

---

### Post by justin077 on 2018-04-10
yes but the thing is i'm not changing the OS, i'm rebooting from Ubuntu and back to Ubuntu,

Anyway, this is a deep engineering work,  i brought it back to the shop, and bought another one. The D-Link dwa-140, it's working fine.

Thanks

---

### Post by jeremy31 on 2018-04-10
Try a different blacklist
```
echo "blacklist rtl8xxxu" | sudo tee /etc/modprobe.d/8192eu.conf
```
Reboot

---

