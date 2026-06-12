---
title: "wired network not working in lts12.04"
date: 2013-11-18
forum: Networking &amp; Wireless
---

### Post by boz86 on 2013-11-18
Hi,

I had the wired network working after my upgrade, but only while using the command

code:
```
modprobe b43
```

had to do this on every restart.

Today, after having to deconflict video drivers to get the GUI desktop back, I no longer can get the wired network even using the above code.

Somewhere in the video troubleshooting I remember doing a general update of nonfree drivers but I don't remember exactly what I did.

I've tried some of the solutions I see on the forum but I'm definitely not doing this in a systemic way and I'm getting nowhere after hours of trying, so any help would be greatly appreciated.

Thanks!

---

### Post by chili555 on 2013-11-18
First, please tell us about your wired and wireless devices:```
lspci -nn | grep -e 0200 -e 0280
```Does the ethernet spring to life with:```
sudo modprobe b4[COLOR="#FF0000"]4[/COLOR]
```We'll get this fixed up!

---

### Post by boz86 on 2013-11-18
> **chili555 said:**
> First, please tell us about your wired and wireless devices: 

```
lspci -nn | grep -e 0200 -e 0280
```

03:00.0 Ethernet controller [0200]: Broadcom Corporation bcm4401-B0 100Base-TX [14e4:170c] (rev 02)
0c:00.0: Broadcom corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

Does the ethernet spring to life with:```
sudo modprobe b4[COLOR=#FF0000]4[/COLOR]
```

Yes, I get a wired connection (could swear I tried this and got an error earlier -- maybe I forgot the sudo.)

Thanks for the help,

---

### Post by chili555 on 2013-11-18
Let's see a few more things and then we'll tweak a thing or two and be fixed:```
ls /etc/modprobe.d
lsmod | grep -e wl -e b4
```

---

### Post by boz86 on 2013-11-19
Thanks again, here's the info:

> **chili555 said:**
> Let's see a few more things and then we'll tweak a thing or two and be fixed:

```
ls /etc/modprobe.d
```
alsa-base.conf           blacklist-framebuffer.conf   libpisock9.conf
blacklist                blacklist-modem.conf         nvidia-319_hybrid.conf
blacklist-ath_pci.conf   blacklist-oss.conf           nvidia-graphics-drivers.conf
blacklist.conf           blacklist-rare-network.conf  vmwgfx-fbdev.conf
blacklist.conf~          blacklist-watchdog.conf
blacklist-firewire.conf  dkms.conf

```
lsmod | grep -e wl -e b4
```
b44                    31412  0 
ssb                    50691  1 b44

For what it's worth, here's the blacklist.conf file:
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

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
#blacklist bcm43xx

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
blacklist b43
blacklist b43legacy
blacklist wl
```

---

### Post by chili555 on 2013-11-19
Please open a terminal and do:```
sudo apt-get remove --purge bcmwl-kernel-source
```If it isn't installed, that's fine, just proceed:```
gksudo gedit /etc/modprobe.d/blacklist.conf
```Remove the b43 lines so that the last several lines look like:```
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist wl
```In fact, b43 is correct for your wireless device. Proofread carefully, save and close gedit. Now do:```
sudo -i
echo b44 >> /etc/modules
echo b43 >> /etc/modules
exit
```Reboot. Is it all working as expected now?

---

### Post by boz86 on 2013-11-19
The wired still requires the command:

```
sudo mobprobe b44
```

However, it works just fine otherwise. And the wireless works now, which is a bonus.

Should these give me some indication they worked? A couple of times it looked like it finished but when I tried to close the terminal it warned me process were still running.
```

sudo -i 
echo b44 >> /etc/modules 
echo b43 >> /etc/modules 
exit
```

It's about 98% there and I could certainly live with it as is.
thanks,
Boz

---

### Post by boz86 on 2013-11-19
The wired still requires the command:

```
sudo mobprobe b44
```

However, it works just fine otherwise. And the wireless works now, which is a bonus.

Should these give me some indication they worked? A couple of times it looked like it finished but when I tried to close the terminal it warned me process were still running.
```

sudo -i 
echo b44 >> /etc/modules 
echo b43 >> /etc/modules 
exit
```

It's about 98% there and I could certainly live with it as is.
thanks,
Boz

---

### Post by chili555 on 2013-11-19
Let's check:```
gksudo gedit /etc/modules
```At the very end, it should look about like this:```
loop
lp
rtc
b44
b43
```If the latter two are not there, simply add them, proofread carefully, save and close gedit. Reboot and let me have your report.

---

### Post by boz86 on 2013-11-19
All it had was 
```
lp 
b44
b43
b44
b43
b44
b43
```

I changed it to read like yours and had the same issue. Wireless came up automatically, when I disconnected I had to do the manual
```
modprobe b44
```
to get the wired network functioning.

> **chili555 said:**
> Let's check:```
gksudo gedit /etc/modules
```At the very end, it should look about like this:
```

loop
lp
rtc
b44
b43

```If the latter two are not there, simply add them, proofread carefully, save and close gedit. Reboot and let me have your report.

---

### Post by sioxs on 2013-11-19
Hi,
just wanted to add my 2 cents here.
I've been trying to install 12.04.3 LTS into a older Lenovo N200 which as the Broadcom chipset [14e4:4311]
According to the installation details on ../WifiDocs/Drivers/bcm43xx#b43 at help.ubuntu one of the initial steps is to install the bcmwl-kernel-source package
in every case (on 3 clean installs) the kernel panics and obviously can't complete the processes.
here's  the output:
```

11/18/13 02:48:30 PM    kubuntu    kernel    [  645.450000] kernel BUG at include/net/cfg80211.h:2209!
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.450043] invalid opcode: 0000 [#1] SMP 
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.450087] CPU 1 
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.450108] Modules linked in: wl(P+) lib80211 nls_iso8859_1 nls_cp437 vfat fat usb_storage dm_crypt snd_hda_codec_realtek arc4 snd_hda_intel snd_hda_codec snd_hwdep snd_pcm mac80211 snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd joydev r852 sm_common nand psmouse rfcomm cfg80211 bnep nand_ids bluetooth mtd nand_bch bch nand_ecc r592 soundcore memstick parport_pc ppdev snd_page_alloc mac_hid serio_raw lp dm_multipath parport squashfs overlayfs nls_utf8 isofs dm_raid45 xor dm_mirror dm_region_hash dm_log btrfs zlib_deflate libcrc32c firewire_ohci firewire_core crc_itu_t sdhci_pci sdhci wmi i915 drm_kms_helper tg3 drm i2c_algo_bit video [last unloaded: bcma]
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.450780] 
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.450795] Pid: 9904, comm: modprobe Tainted: P           O 3.2.0-52-generic #78-Ubuntu LENOVO 0769AK8/IEL10
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.450869] RIP: 0010:[<ffffffffa06666ba>]  [<ffffffffa06666ba>] wdev_priv.part.7+0x4/0x6 [wl]
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.450961] RSP: 0018:ffff8800b4e69ae8  EFLAGS: 00010246
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.450998] RAX: 0000000000000000 RBX: ffff8800b70ac418 RCX: 000000000003ffff
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.451034] RDX: ffff8800b34b6780 RSI: ffff8800b70ac510 RDI: ffff8800b34b6000
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.451071] RBP: ffff8800b4e69ae8 R08: 000000000003ffff R09: 0000000000000000
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.451107] R10: 0000000000000000 R11: 0000000000000000 R12: ffff8800b34b6780
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.451143] R13: ffff8800b70ac510 R14: 0000000000000000 R15: ffff8800aedd7400
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.451180] FS:  00007fe6d84f3700(0000) GS:ffff8800bf500000(0000) knlGS:0000000000000000
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.451233] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.451263] CR2: 00007fe6d7f25000 CR3: 00000000aeda9000 CR4: 00000000000006e0
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.451299] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.451336] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.451373] Process modprobe (pid: 9904, threadinfo ffff8800b4e68000, task ffff8800b9562e00)
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.451427] Stack:
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.451444]  ffff8800b4e69b18 ffffffffa0665a8a ffff8800b4e69b3e ffff8800b70ac418
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.451507]  ffff8800b34b6780 ffff8800b70ac510 ffff8800b4e69b48 ffffffffa065db2f
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.451567]  0000000f00000001 ffff8800b70ac400 ffff8800b7510000 ffff8800b34b6000
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.451627] Call Trace:
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.451672]  [<ffffffffa0665a8a>] wl_cfg80211_detach+0xfa/0x100 [wl]
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.451743]  [<ffffffffa065db2f>] wl_free_if.isra.9+0x2f/0xd0 [wl]
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.451812]  [<ffffffffa065e6da>] wl_free+0x6a/0x290 [wl]
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.451845]  [<ffffffff81647cdc>] ? printk+0x51/0x53
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.451906]  [<ffffffffa0666610>] wl_pci_probe+0x56a/0x594 [wl]
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.451940]  [<ffffffff8103ec59>] ? default_spin_lock_flags+0x9/0x10
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.451986]  [<ffffffff81337bec>] local_pci_probe+0x5c/0xd0
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.452017]  [<ffffffff813394e9>] __pci_device_probe+0xf9/0x100
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.452052]  [<ffffffff8131040a>] ? kobject_get+0x1a/0x30
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.452053]  [<ffffffff8133952a>] pci_device_probe+0x3a/0x60
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.452053]  [<ffffffff813f9668>] really_probe+0x68/0x190
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.452053]  [<ffffffff813f98f5>] driver_probe_device+0x45/0x70
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.452053]  [<ffffffff813f99cb>] __driver_attach+0xab/0xb0
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.452053]  [<ffffffff813f9920>] ? driver_probe_device+0x70/0x70
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.452053]  [<ffffffff813f9920>] ? driver_probe_device+0x70/0x70
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.452053]  [<ffffffff813f8754>] bus_for_each_dev+0x64/0xa0
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.452053]  [<ffffffff813f942e>] driver_attach+0x1e/0x20
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.452053]  [<ffffffff813f9080>] bus_add_driver+0x1a0/0x270
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.452053]  [<ffffffffa0498000>] ? 0xffffffffa0497fff
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.452053]  [<ffffffff813f9f36>] driver_register+0x76/0x140
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.452053]  [<ffffffffa0498000>] ? 0xffffffffa0497fff
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.452053]  [<ffffffff813391c6>] __pci_register_driver+0x56/0xd0
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.452053]  [<ffffffff81043873>] ? set_memory_nx+0x43/0x50
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.452053]  [<ffffffffa049801e>] wl_module_init+0x1e/0x1000 [wl]
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.452053]  [<ffffffff81002040>] do_one_initcall+0x40/0x180
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.452053]  [<ffffffff810a9eae>] sys_init_module+0xbe/0x230
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.452053]  [<ffffffff81668d02>] system_call_fastpath+0x16/0x1b
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.452053] Code: e7 e8 db 7f ff ff 48 89 df e8 d3 02 cd e0 31 f6 4c 89 ef e8 a9 2b d9 e0 5b 41 5c 41 5d 41 5e 5d c3 55 48 89 e5 0f 0b 55 48 89 e5 <0f> 0b 55 48 89 e5 66 66 66 66 90 0f 0b 55 48 89 e5 66 66 66 66 
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.452053] RIP  [<ffffffffa06666ba>] wdev_priv.part.7+0x4/0x6 [wl]
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.452053]  RSP <ffff8800b4e69ae8>
11/18/13 02:48:30 PM    kubuntu    kernel    [  645.490451] ---[ end trace 6504ff5928dceb58 ]---

```

With a CD install there initially is no compatable modules loaded to make a connection wired or wifi - although through several attemts (rebooting Live CD) sometimes a wired or wifi connection is present  - most of the time not. Even if it's present durring installation it's not after the first reboot into the new install
To enable a connection download the firmware from another machine and put it on a USB
Enable the CDROM sources in apt and install the b43-fwcutter package 
Change directories to the path of the firmware you downloaded, extract it and then issue the command:
```
sudo b43-fwcutter -w /lib/firmware broadcom-wl-5.10.56.27.3/driver/wl_apsta/wl_prebuilt.o
```
Refer to the table for the correct firmware drivers and command to use for your card at: [http://wireless.kernel.org/en/users/Drivers/b43#Supported_devices](http://wireless.kernel.org/en/users/Drivers/b43#Supported_devices)

Remove all the modules including the one your going to use
```
sudo modprobe -r b43 ssb wl brcmfmac bcma
``` 
Enable the module you wish to use
```
sudo modprobe wl
```
Wait a few seconds and wifi should now work
if it does update the kernel to preserve the configuration on the next boot
```
sudo update-initramfs -u
```
if not check the entries in /etc/modprobe.d/blacklist-whatever for conflicting drivers and add or disable them
To find which modules are loaded do:
```
cat /proc/modules
```

In this case the **bcmwl-kernel-source** package was the problem after removal internet access was restored.
thanks for the tips! [                                                      [IMG]http://ubuntuforums.org/customavatars/avatar35909_18.gif[/IMG]                                              ]("http://ubuntuforums.org/member.php?u=35909")                                                                                     [**[COLOR=#000000]chili555[/COLOR]**]("http://ubuntuforums.org/member.php?u=35909")
 
peace!
sioxs

---

### Post by chili555 on 2013-11-19
> **boz86 said:**
>  Wireless came up automatically, when I disconnected I had to do the manual
```
modprobe b44
```
to get the wired network functioning.Weird. Let's see if the logs tell us what's going wrong here:```
dmesg | grep -e ssb -e b44
```Thanks.

---

### Post by boz86 on 2013-11-19
> **chili555 said:**
> Weird. Let's see if the logs tell us what's going wrong here:```
dmesg | grep -e ssb -e b44
```Thanks.

I got this:

[    1.308162] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
[    1.308174] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
[    1.308184] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
[    1.308193] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
[    1.372580] ssb: Sonics Silicon Backplane found on PCI device 0000:0c:00.0
[    1.426776] b44 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.444047] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[    1.444056] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[    1.444064] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[    1.484147] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[    1.484188] b44: Broadcom 44xx/47xx 10/100 PCI ethernet driver version 2.0
[    1.507042] b44 ssb1:0: eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver 00:1c:23:a6:e6:1f
[   52.816215] b44 ssb1:0: eth0: Link is up at 100 Mbps, full duplex
[   52.816219] b44 ssb1:0: eth0: Flow control is off for TX and off for RX
[   63.288335] b44 ssb1:0: eth0: powering down PHY
[   63.336265] b44 0000:03:00.0: PCI INT A disabled
[  189.616269] b44 0000:03:00.0: BAR 0: set to [mem 0xf9bfe000-0xf9bfffff] (PCI address [0xf9bfe000-0xf9bfffff])
[  189.616285] b44 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  189.636233] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[  189.636263] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[  189.636277] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[  189.676140] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[  189.676176] b44: Broadcom 44xx/47xx 10/100 PCI ethernet driver version 2.0
[  189.697285] b44 ssb2:0: eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver 00:1c:23:a6:e6:1f
[  192.804387] b44 ssb2:0: eth0: Link is up at 100 Mbps, full duplex
[  192.804391] b44 ssb2:0: eth0: Flow control is off for TX and off for RX

Thanks again for the help!

---

### Post by chili555 on 2013-11-19
> b44 ssb1:0: eth0: powering down PHYIt may be an official bug! [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1018456](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1018456)  Notice the bug report says it was fixed in a later kernel version.> This bug was fixed in the package linux - 3.5.0-4.4Which kernel version do you have?```
uname -a
```

---

### Post by boz86 on 2013-11-19
Looks like I have an older kernel:
3.2.0-56-generic #86-Ubuntu SMP Wed Oct 23 17:31:43 UTC 2013 i686 i686 i386 GNU/Linux

---

### Post by Hadaka on 2013-11-19
Hi, 3.2.0-56-generic is the current 32bit kernel.
last i knew, [14e4:4311] ran best on linux-firmware-nonfree...b43
has there been a change in 13.10? If not,please try..
```
sudo apt-get remove --purge bcmwl-kernel-source
```
BOOT
```
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
good results?

---

### Post by chili555 on 2013-11-19
I think we have the wireless in order; we're struggling temporarily with wired.

---

### Post by houshdaran on 2013-11-20
> **chili555 said:**
> First, please tell us about your wired and wireless devices:```
lspci -nn | grep -e 0200 -e 0280
```Does the ethernet spring to life with:```
sudo modprobe b4[COLOR=#FF0000]4[/COLOR]
```We'll get this fixed up!

Mine didn't connect to the internet with those commands

---

### Post by houshdaran on 2013-11-20
How can I disable all DSL connections I have created  inubuntu and then re-create them?

---

### Post by chili555 on 2013-11-20
> **houshdaran said:**
> Mine didn't connect to the internet with those commandsDo you have the exact same devices as the original poster? If not, please start your own new thread.

---

### Post by boz86 on 2013-11-20
Chili,

Should I install kernel 3.5.0-4.4? If so, how? I don't see it in the software center.

Thanks,
Boz

---

### Post by chili555 on 2013-11-20
> **boz86 said:**
> Chili,

Should I install kernel 3.5.0-4.4? If so, how? I don't see it in the software center.

Thanks,
BozI am trying to work out installing b44 and b43 only from kernel 3.5.0-xx. I need to get to my 12.04 LTS ("Tweak it till you break it!") machine first. Back in a while.

---

### Post by chili555 on 2013-11-20
I see no way to install a backported b44. I think the only reasonable option is to install the latest 3.5.0-xx kernel you can find. On my 12.04 system, it's 3.5.0-43. Do you have that one?

---

### Post by boz86 on 2013-11-20
Looks like I have that one, getting multiple programs in the software center with that kernel referenced.

---

### Post by chili555 on 2013-11-20
I'd install linux-image-3.5.0-43-generic and reboot. We will have a bit of housekeeping to do afterwards.

---

### Post by boz86 on 2013-11-20
Chili,
I've got 3.5.0-43 installed now. Wireless working, wired not anymore with

```
 modprobe b44 
```

---

### Post by chili555 on 2013-11-20
> **boz86 said:**
> Chili,
I've got 3.5.0-43 installed now. Wireless working, wired not anymore with

```
 modprobe b44 
```Oh, my!! Let's look for clues in the logs:```
sudo modprobe b44
dmesg | grep b44
```

---

### Post by boz86 on 2013-11-20
Ok, I'm an idiot. I left the sudo. At least I reported what I did accurately :-)

```
 dmesg | grep b44 
```
dmesg | grep b44
[    1.252925] b44: Broadcom 44xx/47xx 10/100 PCI ethernet driver version 2.0
[    1.276621] b44 ssb1:0: eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver 00:1c:23:a6:e6:1f
[   49.804223] b44 ssb1:0: eth0: Link is up at 100 Mbps, full duplex
[   49.804231] b44 ssb1:0: eth0: Flow control is off for TX and off for RX
[   60.283183] b44 ssb1:0: eth0: powering down PHY
[ 2213.520280] b44: Broadcom 44xx/47xx 10/100 PCI ethernet driver version 2.0
[ 2213.540730] b44 ssb2:0: eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver 00:1c:23:a6:e6:1f
[ 2217.000201] b44 ssb2:0: eth0: Link is up at 100 Mbps, full duplex
[ 2217.000206] b44 ssb2:0: eth0: Flow control is off for TX and off for RX

---

### Post by chili555 on 2013-11-21
> b44 ssb1:0: eth0: powering down PHYThe same problem as before....

I have but one further suggestion. I saw this: [http://h30434.www3.hp.com/t5/Notebook-Hardware/Disappearing-Ethernet-Adaptor/td-p/271987](http://h30434.www3.hp.com/t5/Notebook-Hardware/Disappearing-Ethernet-Adaptor/td-p/271987) Of course, I have no idea if you have an HP laptop, however, these power-saving schemes are becomming more common in all computers; not just to save battery power on a laptop, but also to conserve power drawn from the power mains that we all have to pay for every month!> The dissapearing wired ethernet adaptor is due to a bios setting LAN Power saving [Enabled] 

Hit F10 on boot up I think... if not it'll be either [esc] or [F2] or [delete] or [F10]?  Can't remember, even though I only just fixed this 15mins ago lol... 

Disable the powersaving for the LAN and the wired ethernet adaptor will show up in device manager and network adaptors regardless of a working LAN cable fitted.I suggest you look around in the BIOS to see if you find and can disable power saving for the LAN. Aside from that, I really have no further suggestions.

---

### Post by boz86 on 2013-11-21
Ok, thanks much for all the help. We're at 99% on it, good enough for me. Not like I reboot it that often and the wireless is good now.

---

### Post by boz86 on 2013-11-21
It was already disabled, changing it didn't fix the issue.

---

