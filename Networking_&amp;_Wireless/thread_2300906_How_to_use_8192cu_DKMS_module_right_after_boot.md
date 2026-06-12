---
title: "How to use 8192cu DKMS module right after boot"
date: 2015-10-29
forum: Networking &amp; Wireless
---

### Post by tdzbdao on 2015-10-29
Hello folks,

I had quite some problems with random connection drop-outs, so after reading a bit on how to use my TP-Link USB Wifi adapter on Ubuntu 15.10 I learned theres something wrong with the rtl8192cu driver that ships with the kernel.
I built my own DKMS module using this source repository:

[https://github.com/vincent-t/rt8192cu_dkms](https://github.com/vincent-t/rt8192cu_dkms)

Everything seems to be fine now, the installation routine shipped with the dkms module also blacklists rtl8192cu and adds itself to the DKMS registry (or whatever its called). Drop-outs are gone and the connection even seems to be much faster.

One last thing remains that is bugging me a lot, though. My wifi adapter isn't ready for use right after boot. I need to unplug and plug to get it going. I ran out of ideas how this could have happened because all the relevant stuff like lsmod, usb-devices, lsusb are showing
the kernel module is loaded and the device is present.

However, usb-devices indicates that the rtl8192cu kernel module is used for the device, even though it is currently blacklisted. After plugging it in it still displays rtl8192cu and NOT 8191cu (name of the DKMS module).
In summary, all diagnostic information seem to be the same before and after plugging out/in. Here are the relevant parts of dmesg:

```

[    3.417462] r8169 0000:05:00.0 enp5s0: link down
[    3.417501] IPv6: ADDRCONF(NETDEV_UP): enp5s0: link is not ready
[    3.449047] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input21
[    3.449159] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input22
[    3.449218] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input23
[    3.449267] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input24
[    3.911147] usbcore: registered new interface driver rtl8192cu
[    3.912327] rtl8192cu 1-4:1.0 wlxe894f614093e: renamed from wlan0
[    4.055643] cfg80211: World regulatory domain updated:
[    4.055644] cfg80211:  DFS Master region: unset
[    4.055645] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[    4.055646] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[    4.055647] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[    4.055648] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[    4.055649] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[    4.055649] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[    4.055650] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[    4.055651] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[    4.055651] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[    4.326464] snd_hda_codec_hdmi hdaudioC2D0: HDMI: invalid ELD data byte 5
[   57.442976] usb 1-4: USB disconnect, device number 2
[   62.398118] usb 1-4: new high-speed USB device number 3 using xhci_hcd
[   62.527357] usb 1-4: New USB device found, idVendor=0bda, idProduct=8178
[   62.527362] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   62.527365] usb 1-4: Product: USB WLAN
[   62.527367] usb 1-4: Manufacturer: Realtek
[   62.527369] usb 1-4: SerialNumber: 00e04c000001
[   63.583523] rtl8192cu 1-4:1.0 wlxe894f614093e: renamed from wlan0
[   63.623764] IPv6: ADDRCONF(NETDEV_UP): wlxe894f614093e: link is not ready
[   64.046407] IPv6: ADDRCONF(NETDEV_UP): wlxe894f614093e: link is not ready
[   64.060530] IPv6: ADDRCONF(NETDEV_UP): wlxe894f614093e: link is not ready
[   64.098980] IPv6: ADDRCONF(NETDEV_UP): wlxe894f614093e: link is not ready
[   65.460829] IPv6: ADDRCONF(NETDEV_CHANGE): wlxe894f614093e: link becomes ready

```

No wifi related stuff is happening before or after those messages and I don't see anything suspicious here (but after all that's why I'm asking :)

Anyone got some ideas helping me out here? Crawling back and forth under my desk all the time seems to be a tedious thing I'd like to get rid of in the future...

Thanks !

**EDIT:** Just as a side note, i noticed 15.10 giving weird names to my network interfaces (see dmesg output). Is this supposed to be like that or maybe related to the topic?

---

### Post by praseodym on 2015-10-29
Hi,

please check
```

sudo modprobe -rfv rtl8192cu 8192cu
sudo modprobe -v 8192cu
sudo depmod -a
sudo update-initramfs -u
```
Reboot. The interface names changed in 15.10!

[https://lists.ubuntu.com/archives/ubuntu-devel/2015-June/038786.html](https://lists.ubuntu.com/archives/ubuntu-devel/2015-June/038786.html)

---

### Post by tdzbdao on 2015-10-29
paseodym,

thanks for your suggestion! I tried what you recommended, but sadly didn't see any changes. Wifi is still unavailable after boot.

I gathered some additional information that may help:

**lsmod | grep 8192**
```

8192cu                634880  0
snd                    81920  30 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_usb_us122l,snd_hda_codec_generic,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device
r8169                  81920  0
```

[B]dmesg | grep 8192
[/B]```

[    0.000000] PERCPU: Embedded 33 pages/cpu @ffff88062f200000 s96728 r8192 d30248 u524288
[    0.000000] pcpu-alloc: s96728 r8192 d30248 u524288 alloc=1*2097152
[    3.910930] usbcore: registered new interface driver rtl8192cu
[    3.912046] rtl8192cu 1-4:1.0 wlxe894f614093e: renamed from wlan0
```

[B]usb-devices (relevant part)
[/B]```

T:  Bus=01 Lev=01 Prnt=01 Port=03 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0bda ProdID=8178 Rev=02.00
S:  Manufacturer=Realtek
S:  Product=USB WLAN
S:  SerialNumber=00e04c000001
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 4 Cls=ff(vend.) Sub=ff Prot=ff Driver=rtl8192cu
```

**cat /etc/modprobe.d/blacklist-rtl-wlan-driver.conf **
```
blacklist rtl8192cu
```

Now as you can see usb-devices reports rtl8192cu used as device driver even though it is not visible in lsmod. Another thing that confuses me is that 8192cu (the DKMS module I built) is shown in lsmod but not used. If none of these drivers are used or even loaded, how am I able to use the wifi adapter at all? Since I'm not that familiar with dynamic kernel modules it may be just a wild guess but I think the original kernel module is still in use somehow. By the way: I also noticed my connection getting much slower after a while, so another evidence for using a bad driver maybe...

Any ideas? :-/

---

### Post by praseodym on 2015-10-29
Uninstall that driver and try this one:

[https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes)

---

### Post by tdzbdao on 2015-10-29
I was trying this in the first place, but after uninstalling the other driver I followed your hint and reinstalled again - still no luck.

By the way, dmesg is also reporting "rtl8192cu". This driver seems rather tenacious in terms of blacklisting...
Is usb-devices supposed to show the kernel driver regardless of which one should be used on the system anyway?

---

### Post by praseodym on 2015-10-30
Lets check:
```

modinfo 8192cu | egrep 'versi|filen'
locate 8192cu.ko | grep lib
```

---

### Post by tdzbdao on 2015-10-30
Sure:

**modinfo 8192cu | egrep 'versi|filen'**
```

filename:       /lib/modules/4.2.0-16-generic/updates/dkms/8192cu.ko
version:        v4.0.2_9000.20130911
srcversion:     0EE2695501799ED72A177DA
vermagic:       4.2.0-16-generic SMP mod_unload modversions 
parm:           rtw_chip_version:int

```

**locate 8192cu.ko | grep lib**
```

/lib/modules/4.2.0-16-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
/lib/modules/4.2.0-16-generic/updates/dkms/8192cu.ko
/var/lib/dkms/8192cu/1.10/4.2.0-16-generic/x86_64/module/8192cu.ko

```

Thanks, I really appreciate your help!

---

### Post by praseodym on 2015-10-30
Strange, its using the right one. Try renaming the other one:
```

sudo mv /var/lib/dkms/8192cu/1.10/4.2.0-16-generic/x86_64/module/8192cu.ko /var/lib/dkms/8192cu/1.10/4.2.0-16-generic/x86_64/module/8192cu.bak
sudo depmod -a
sudo update-initramfs -u
```
Reboot.

---

### Post by tdzbdao on 2015-10-30
Okay, removed the dkms driver. Still no change though. usb-devices still shows "rtl8192cu" as driver used for the device.
Is my kernel haunted or something?

EDIT: Oh wait, I see a change in **dkms status**:
```

8192cu, 1.10: **added**
bbswitch, 0.7, 4.2.0-16-generic, x86_64: installed
ndiswrapper, 1.59, 4.2.0-16-generic, x86_64: installed
nvidia-352, 352.41, 4.2.0-16-generic, x86_64: installed
virtualbox, 5.0.4, 4.2.0-16-generic, x86_64: installed

```

So 8192cu is missing now I guess. Should I try to reinstall it?

---

### Post by praseodym on 2015-10-30
Why is ndiswrapper installed? If you don't need it, remove it:
```

sudo modprobe -rfv ndiswrapper
sudo apt-get remove --purge ndisgtk ndiswrapper*
```
Reboot.

---

### Post by tdzbdao on 2015-10-30
My fault. Yesterday I started to install it because i wanted to try if the win32 drivers would work on the device. Never installed them though. It's gone now, but the problem still persists.

Why am I getting "rtl8192cu" displayed as selected driver under "usb-devices"? Isn't this supposed to be blacklisted and never used for anything?

**EDIT:** I should also mention that this is a completely fresh installation of ubuntu. I did not install anything else that may be related to the topic. On my previous installation (which was periodically upgraded from 12.04 i believe) I just used the DKMS module you suggested and everything went fine from this point. Never tried clean installations of 13.xx/14.xx though.

---

### Post by praseodym on 2015-10-30
rtl8192cu is the alias of the module 8192cu. Please check after booting:
```
lsusb
ifconfig -a
iwconfig
cat /etc/resolv.conf
route -n
dmesg | egrep '81|wl|reason'
```

---

### Post by tdzbdao on 2015-10-30
Here we go:

**lsusb**
```

Bus 004 Device 005: ID 045e:028e Microsoft Corp. Xbox360 Controller
Bus 004 Device 007: ID 1532:001e Razer USA, Ltd 
Bus 004 Device 006: ID 04f2:0971 Chicony Electronics Co., Ltd 
Bus 004 Device 004: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 004 Device 003: ID 0644:8021 TEAC Corp. TASCAM US-122mkII
Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 0bda:8178 Realtek Semiconductor Corp. RTL8192CU 802.11n WLAN Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

**ifconfig -a**
```

enp5s0    Link encap:Ethernet  HWaddr d0:50:99:7c:bc:4e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0                                                                                                                                                                                     
          collisions:0 txqueuelen:1000                                                                                                                                                                                                             
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)                                                                                                                                                                                                   
                                                                                                                                                                                                                                                   
lo        Link encap:Local Loopback                                                                                                                                                                                                                
          inet addr:127.0.0.1  Mask:255.0.0.0                                                                                                                                                                                                      
          inet6 addr: ::1/128 Scope:Host                                                                                                                                                                                                           
          UP LOOPBACK RUNNING  MTU:65536  Metric:1                                                                                                                                                                                                 
          RX packets:431 errors:0 dropped:0 overruns:0 frame:0                                                                                                                                                                                     
          TX packets:431 errors:0 dropped:0 overruns:0 carrier:0                                                                                                                                                                                   
          collisions:0 txqueuelen:0                                                                                                                                                                                                                
          RX bytes:35419 (35.4 KB)  TX bytes:35419 (35.4 KB)                                                                                                                                                                                       
                                                                                                                                                                                                                                                   
wlxe894f614093e Link encap:Ethernet  HWaddr e8:94:f6:14:09:3e                                                                                                                                                                                      
          BROADCAST MULTICAST  MTU:1500  Metric:1                                                                                                                                                                                                  
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0                                                                                                                                                                                       
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0                                                                                                                                                                                     
          collisions:0 txqueuelen:1000                                                                                                                                                                                                             
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

```

[B]iwconfig
[/B]```

wlxe894f614093e  unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

enp5s0    no wireless extensions.

lo        no wireless extensions.

```

[B]cat /etc/resolv.conf
[/B]```

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)                                                                                                                                                                     
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN 

```

**route -n**
```

Kernel IP routing table                                                                                                                                                                                                                            
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 

```

[B]dmesg | egrep '81|wl|reason'
[/B]```

[    0.000000] ACPI: DSDT 0x00000000C9958178 009BAD (v02 ALASKA A M I    00000022 INTL 20051117)                                                                                                                                                   
[    0.000000] PERCPU: Embedded 33 pages/cpu @ffff88062f200000 s96728 r8192 d30248 u524288                                                                                                                                                         
[    0.000000] pcpu-alloc: s96728 r8192 d30248 u524288 alloc=1*2097152                                                                                                                                                                             
[    0.000000] Memory: 24540776K/25049744K available (8146K kernel code, 1237K rwdata, 3800K rodata, 1460K init, 1292K bss, 508968K reserved, 0K cma-reserved)
[    0.015781] Mountpoint-cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.016484] Freeing SMP alternatives memory: 28K (ffffffff81ea4000 - ffffffff81eab000)
[    0.109814] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.109816] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.136813] pci 0000:00:02.0: [8086:0152] type 00 class 0x038000
[    0.137088] pci 0000:00:16.0: reg 0x10: [mem 0xf781a000-0xf781a00f 64bit]
[    0.137236] pci 0000:00:1a.0: reg 0x10: [mem 0xf7818000-0xf78183ff]
[    0.137396] pci 0000:00:1b.0: reg 0x10: [mem 0xf7810000-0xf7813fff 64bit]
[    0.137992] pci 0000:00:1d.0: reg 0x10: [mem 0xf7817000-0xf78173ff]
[    0.138127] pci 0000:00:1f.0: [8086:1e46] type 00 class 0x060100
[    0.138329] pci 0000:00:1f.2: reg 0x24: [mem 0xf7816000-0xf78167ff]
[    0.138424] pci 0000:00:1f.3: reg 0x10: [mem 0xf7815000-0xf78150ff 64bit]
[    0.150200] pci 0000:05:00.0: [10ec:8168] type 00 class 0x020000
[    0.158100] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.158136] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.158170] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.158481] vgaarb: bridge control possible 0000:01:00.0
[    0.160442] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.166981] pnp: PnP ACPI init
[    0.167811] system 00:08: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.173812] pci 0000:00:1c.5:   bridge window [io  0xd000-0xdfff]
[    0.173818] pci 0000:00:1c.5:   bridge window [mem 0xf2100000-0xf21fffff 64bit pref]
[    0.174381] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.599281] zbud: loaded
[    0.600681] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.625726] xhci_hcd 0000:00:14.0: hcc params 0x20007181 hci version 0x100 quirks 0x0000b930
[    0.626481] ehci-pci: EHCI PCI platform driver
[    0.630463] ehci-pci 0000:00:1a.0: irq 16, io mem 0xf7818000
[    0.646193] ehci-pci 0000:00:1d.0: irq 23, io mem 0xf7817000
[    0.658184] hub 4-0:1.0: USB hub found
[    0.658191] hub 4-0:1.0: 2 ports detected
[    0.671957] Freeing unused kernel memory: 1460K (ffffffff81d37000 - ffffffff81ea4000)
[    0.711732] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.711740] r8169 0000:05:00.0: can't disable ASPM; OS doesn't have ASPM control
[    0.712244] r8169 0000:05:00.0 eth0: RTL8168evl/8111evl at 0xffffc9000000e000, d0:50:99:7c:bc:4e, XID 0c900800 IRQ 26
[    0.712246] r8169 0000:05:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    0.731195] r8169 0000:05:00.0 enp5s0: renamed from eth0
[    0.767319] ata1: SATA max UDMA/133 abar m2048@0xf7816000 port 0xf7816100 irq 27
[    0.767321] ata2: SATA max UDMA/133 abar m2048@0xf7816000 port 0xf7816180 irq 27
[    0.767323] ata3: SATA max UDMA/133 abar m2048@0xf7816000 port 0xf7816200 irq 27
[    0.767326] ata4: SATA max UDMA/133 abar m2048@0xf7816000 port 0xf7816280 irq 27
[    0.767328] ata5: SATA max UDMA/133 abar m2048@0xf7816000 port 0xf7816300 irq 27
[    0.767330] ata6: SATA max UDMA/133 abar m2048@0xf7816000 port 0xf7816380 irq 27
[    1.067543] usb 1-4: New USB device found, idVendor=0bda, idProduct=8178
[    1.127781] scsi 0:0:0:0: Direct-Access     ATA      MKNSSDCR180GB    BBF0 PQ: 0 ANSI: 5
[    1.128112] sd 0:0:0:0: [sda] Write Protect is off
[    1.128114] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.128123] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.145812] ata2.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.145815] ata2.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    2.117810] usb 4-1.6.1: Manufacturer: Thermaltake
[    2.252814] hid-generic 0003:04F2:0971.0002: input,hiddev0,hidraw1: USB HID v1.11 Device [Thermaltake Tt eSPORTS Challenger Pro gaming keyboard] on usb-0000:00:1d.0-1.6.1/input1
[    2.776140] [drm] Initialized drm 1.1.0 20060810
[    3.493349] r8169 0000:05:00.0 enp5s0: link down
[    3.922734] usbcore: registered new interface driver rtl8192cu
[    3.923801] rtl8192cu 1-4:1.0 wlxe894f614093e: renamed from wlan0

```

Everything done in order right after logging in. As you can see there is a wifi interface (the one with the ugly name), but appearantly it is not working properly. Network manager is not showing any wifis without replugging the usb connection.

---

### Post by praseodym on 2015-10-30
/etc/resolv.conf is empty after booting. Lets write it each time, when booting up:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee /etc/resolv.conf
sudo cp /etc/resolv.conf /etc/resolv.default 
sudo touch /etc/network/if-up.d/resolv
gksudo gedit /etc/network/if-up.d/resolv
```
Add these lines:
```
#!/bin/sh

cp /etc/resolv.default /etc/resolv.conf
```, save, close the editor and run:
```

sudo chmod +x /etc/network/if-up.d/resolv
```
Try it again.

---

### Post by tdzbdao on 2015-10-30
Still no success, sorry.

As I said I'm not an expert, but aren't the messages above indicating there is a problem with connecting to the AP in the first place? I mean, I can get gateway and dhcp stuff without any problem once I'm connected to the access point - it just won't do by itself (plus it seems to slow down after a while, but thats another problem I guess).

Another thing that might be interesting: When booting up and before disconnecting the adapter, iwlist scan reports "interface doesn't support scanning".

---

### Post by praseodym on 2015-10-30
Ok, remove the file if you wish to do so:

```
sudo rm /etc/network/if-up.d/resolv
```
Lets try:
```

gksudo gedit /etc/rc.local
```
Add _before_ "exit 0":
```

modprobe -rf rtl8192cu 8192cu
sleep 3
modprobe 8192cu
```
Save and reboot.

---

### Post by tdzbdao on 2015-10-30
Okay, did that. Still no change. iwlist scan reports "no scan results".

I did not experience any 3 second delay while booting though.

---

### Post by praseodym on 2015-10-30
Sorry, I'm running out of ideas, maybe the USB layer is initialized after boot, not during boot.

---

### Post by tdzbdao on 2015-10-30
Nothing to be sorry about. I'm grateful you took time to help me out here, thank you for that. Honestly I feel the same about that, no clue why it wouldn't work. Typically I can find a few suspicious dmesg or syslog entries that indicate the error, but this one is really, really tough..

---

### Post by vincentthiele on 2015-12-09
> **tdzbdao said:**
> Nothing to be sorry about. I'm grateful you took time to help me out here, thank you for that. Honestly I feel the same about that, no clue why it wouldn't work. Typically I can find a few suspicious dmesg or syslog entries that indicate the error, but this one is really, really tough..

I have found a solution for this bug wich was introduced by ubuntu 15.10.
Open a terminal and type: sudo nano /etc/rc.localthen add: sleep 10 && systemctl restart network-manager.service
before "exit 0"
save & reboot.

---

