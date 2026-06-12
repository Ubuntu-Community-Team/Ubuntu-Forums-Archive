---
title: "Belkin Wg 11mbs wlan usb/Lubuntu/ HP Slimline s7520n"
date: 2014-01-03
forum: Networking &amp; Wireless
---

### Post by johnnytwotimes on 2014-01-03
I recently upgraded to lubuntu 13.10 from Ubuntu 12.04 (Needed a faster distro) 
Previously in 12.04 I managed to configure my own INF file out of a bunch of different drivers (dumb I know you don't even know the amount of errors I went through, which is why I upgraded) 
For some reason I cannot get any of the drivers (and I have many that are compatible) to associate with my device ID. 
I'm having a weird problem where my system just automatically freezes when it comes to any command with the modules
I think it's possible to do with dependancies in the driver? I have a onboard wireless card **(gemtek rt73usb)** and im trying to install the  [b]Belkin wireless usb adapter 11mbs V.1.01[b]  so I have an adapter I can move around for increased signal ect.
I have two of the three drivers for the adapter as well. (smc 2662w v2) and the (belkin F5d6050) I cannot find the AR version of the SMC driver


```
Bus 001 Device 004: ID 15a9:0004 Gemtek WUBR-177G [Ralink RT2571W]
Bus 001 Device 003: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 046d:c513 Logitech, Inc. MX3000 Cordless Desktop Receiver
Bus 003 Device 003: ID 0d5c:a002 SMC Networks, Inc. SMC2662W v2 / SMC2662W-AR / Belkin F5D6050 [Atmel at76c503a]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

```
yanni@yanni-EX259AA-ABA-s7520n:~$ ifconfig
eth2      Link encap:Ethernet  HWaddr 00:17:31:a6:94:f4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1780 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1780 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:139156 (139.1 KB)  TX bytes:139156 (139.1 KB)

wlan1     Link encap:Ethernet  HWaddr 00:14:a5:a9:f8:66  
          inet addr:192.168.1.18  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a5ff:fea9:f866/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16367 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9105 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4363568 (4.3 MB)  TX bytes:1731208 (1.7 MB)
```

```
yanni@yanni-EX259AA-ABA-s7520n:~$ iwconfig
lo        no wireless extensions.

eth2      no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:"11FX08156484"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 0C:D5:02:CA:49:AB   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=26/70  Signal level=-84 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:6  Invalid misc:535   Missed beacon:0

```

I would send the **LSMOD** code but im afraid it will crash on me again. I will after I post this. 
Anything im missing just ask! I will be happy to post any information needed.

---

### Post by chili555 on 2014-01-03
You seem pretty skilled here, so I will go fast and loose and expect that you'll know what to do without step-by-steps.> I have a onboard wireless card (gemtek rt73usb)First, if you don't intend to use it, I'd blacklist its driver, rt73usb, I assume. Please verify before you blacklist the wrong thing.> [COLOR="#FF0000"]0d5c:a002[/COLOR] SMC Networks, Inc. SMC2662W v2 / SMC2662W-AR / Belkin F5D6050 [Atmel at76c503a]This device is driven by the driver *at76c50x-usb*.> license:        GPL
description:    Atmel at76x USB Wireless LAN Driver
author:         Sebastian Smolorz <sesmo@gmx.net>
author:         Kalle Valo <kalle.valo@iki.fi>
author:         Guido Guenther <agx@sigxcpu.org>
author:         Pavel Roskin <proski@gnu.org>
author:         Balint Seeber <n0_5p4m_p13453@hotmail.com>
author:         Nick Jones
author:         Alex <alex@foogod.com>
author:         Joerg Albert <joerg.albert@gmx.de>
author:         Oliver Kurth <oku@masqmail.cx>
[COLOR="#FF0000"]firmware:       atmel_at76c505amx-rfmd.bin
firmware:       atmel_at76c505a-rfmd2958.bin
firmware:       atmel_at76c505-rfmd2958.bin
firmware:       atmel_at76c505-rfmd.bin
firmware:       atmel_at76c503-rfmd-acc.bin
firmware:       atmel_at76c503-rfmd.bin
firmware:       atmel_at76c503-i3863.bin
firmware:       atmel_at76c503-i3861.bin[/COLOR]
srcversion:     C5DBFBFD5AF433C951F7CC7
<snip>
alias:          usb:v[COLOR="#FF0000"]0D5C[/COLOR]p[COLOR="#FF0000"]A002[/COLOR]d*dc*dsc*dp*ic*isc*ip*in*
<snip>
depends:        mac80211
intree:         Y
vermagic:       3.12.4-031204-generic SMP mod_unload modversions 
parm:           debug:Debugging level (uint)
However, it requires firmware that you may or may not have installed. You can get it with a temporary wired ethernet connection and:```
sudo apt-get install atmel-firmware
```You may also get some clues as to what firmware is missing from:```
dmesg | grep at76
```Post back and we'll help if needed.

---

### Post by johnnytwotimes on 2014-01-03
Chipset installed from synaptic package. I did [b] dmesg | grep at76{/b} 
and got this. theres a lot more but i figured this would be would you would go off of.
```
[   24.292247] zram: Created 1 device(s) ...
[   24.379612] Adding 480172k swap on /dev/zram0.  Priority:5 extents:1 across:480172k SSFS
[   24.660049] ndiswrapper (wrap_reset_port:1100): locking failed: -16
[   24.665461] ndiswrapper (mp_init:211): couldn't initialize device: C0000001
[   24.665471] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001)
[   24.665479] ndiswrapper (mp_halt:254): device ef7f1500 is not initialized - not halting
[   24.665481] ndiswrapper: device eth%d removed
[   24.665518] ndiswrapper: probe of 3-1:1.0 failed with error -22
[   24.665564] usbcore: registered new interface driver ndiswrapper
[   24.666391] BUG: unable to handle kernel paging request at f86a5a9d
[   24.666501] IP: [<f86a5a9d>] 0xf86a5a9c
[   24.666566] *pdpt = 0000000001a55001 *pde = 0000000036d1d067 *pte = 0000000000000000 
[   24.666689] Oops: 0010 [#1] SMP 
[   24.666746] Modules linked in: zram(C) parport_pc ppdev rfcomm bnep bluetooth arc4 snd_atiixp snd_ac97_codec ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq snd_seq_device psmouse snd_timer serio_raw snd k8temp rt73usb rt2x00usb rt2x00lib mac80211 soundcore cfg80211 joydev radeon ttm drm_kms_helper drm i2c_piix4 i2c_algo_bit ndiswrapper(OF) shpchp ati_agp mac_hid lp parport hid_logitech ff_memless usbhid hid usb_storage pata_acpi firewire_ohci 8139too firewire_core 8139cp crc_itu_t pata_atiixp mii sata_sil
[   24.667660] CPU: 0 PID: 631 Comm: ntdriver Tainted: PF        C O 3.11.0-15-generic #23-Ubuntu


```

Im actually blacklisting the rt73usb driver and installing the manufacturer driver through nsidwrapper to see if it would help the adapter any. 
In other news I beleive my adapter will not start, is there a way of force starting or anything?
Thank you by the way

---

### Post by praseodym on 2014-01-04
Hi,

uninstall ndiswrapper:

```
sudo apt-get remove --purge ndisgtk ndiswrapper*
```
and reboot.

If it doesnt work directly install this firmware file:```

wget http://media.cdn.ubuntu-de.org/forum/attachments/25/40/2964522-at76_usb-firmware-0.1.zip
unzip 2964522-at76_usb-firmware-0.1.zip
sudo cp at76_usb-firmware-0.1/*.bin /lib/firmware
```

---

