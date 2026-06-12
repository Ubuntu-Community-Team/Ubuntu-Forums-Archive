---
title: "Wireless / it worked in Ubuntu &amp; after the first boot"
date: 2010-12-07
forum: New to Ubuntu
---

### Post by Blutkoete on 2010-12-07
Hello!

I'm having some trouble with my wireless connection.

It worked out of the box in Ubuntu 10.10 - I was really happy, no more unsupported packagas - and it worked when I installed Kubuntu 10.10. Well, it kind of worked, as it showed me all the available networks but wasn't able to connect to one of them. I rebooted.

Since then, it doesn't even show any networks around me.

*ifconfig* says
```
eth0      Link encap:Ethernet  Hardware Adresse 40:61:86:13:49:b5  
          inet Adresse:192.168.2.105  Bcast:192.168.2.255  Maske:255.255.255.0
          inet6-Adresse: fe80::4261:86ff:fe13:49b5/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:1471 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1657 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:637777 (637.7 KB)  TX bytes:271257 (271.2 KB)
          Interrupt:19 Basisadresse:0xdead 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:640 (640.0 B)  TX bytes:640 (640.0 B)

```

and *iwconfig* tells me
```

...

wlan0  IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

As I wanted to learn something about log files, I tried to compare my first boot log with my later ones and actually found a difference.

Both state
```
Dec  5 18:40:09 jtb-kubuntu kernel: [   15.005703] rt2800pci 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec  5 18:40:09 jtb-kubuntu kernel: [   15.005714] rt2800pci 0000:02:00.0: setting latency timer to 64
Dec  5 18:40:09 jtb-kubuntu kernel: [   15.134445] cfg80211: World regulatory domain updated:
Dec  5 18:40:09 jtb-kubuntu kernel: [   15.134449]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Dec  5 18:40:09 jtb-kubuntu kernel: [   15.134452]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec  5 18:40:09 jtb-kubuntu kernel: [   15.134455]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Dec  5 18:40:09 jtb-kubuntu kernel: [   15.134457]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Dec  5 18:40:09 jtb-kubuntu kernel: [   15.134460]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec  5 18:40:09 jtb-kubuntu kernel: [   15.134462]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec  5 18:40:09 jtb-kubuntu kernel: [   15.192805] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x81a0b1, caps: 0xa04711/0x200000/0x0
Dec  5 18:40:10 jtb-kubuntu kernel: [   15.246974] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
Dec  5 18:40:10 jtb-kubuntu kernel: [   15.315884] phy0: Selected rate control algorithm 'minstrel'
Dec  5 18:40:10 jtb-kubuntu kernel: [   15.316542] Registered led device: rt2800pci-phy0::radio
Dec  5 18:40:10 jtb-kubuntu kernel: [   15.316558] Registered led device: rt2800pci-phy0::assoc
Dec  5 18:40:10 jtb-kubuntu kernel: [   15.316575] Registered led device: rt2800pci-phy0::quality
Dec  5 18:40:10 jtb-kubuntu kernel: [   15.602620] rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.

```

but while the first one goes on with something like

```

Dec  5 18:40:28 jtb-kubuntu kernel: [   33.260797] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Dec  5 18:40:38 jtb-kubuntu kernel: [   44.030073] eth0: no IPv6 routers present
Dec  5 18:41:04 jtb-kubuntu kernel: [   70.148496] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Dec  5 18:41:20 jtb-kubuntu kernel: [   85.374406] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
Dec  5 18:41:21 jtb-kubuntu kernel: [   86.782606] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
Dec  5 18:44:33 jtb-kubuntu kernel: [  278.621546] wlan0: direct probe to a-mac-address (try 1)
...

```

The later kern.log throws an error:

```

Dec  7 15:43:59 jtb-kubuntu kernel: [   21.345021] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec  7 15:43:59 jtb-kubuntu kernel: [   21.491334] phy0 -> rt2800pci_load_firmware: Error - PBF system register not ready.
Dec  7 15:43:59 jtb-kubuntu kernel: [   21.491876] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0x3581ec28
Dec  7 15:43:59 jtb-kubuntu kernel: [   21.546972] ppdev: user-space parallel port driver
Dec  7 15:43:59 jtb-kubuntu kernel: [   21.611290] phy0 -> rt2800pci_load_firmware: Error - PBF system register not ready.
Dec  7 15:43:59 jtb-kubuntu kernel: [   21.611820] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0x3581ec28

```

Any ideas/suggestions?

Thank you very much! I hope I haven't posted a huge security breach.

---

### Post by TBABill on 2010-12-07
If this is an internal wireless device, please post the output of ```
lspci
``` and if it is USB, please post output of ```
lsusb
``` It appears you are using the rt2800 Ralink driver, but you may have a 2860 or 2870 or another model so there are some blacklisting you may need to do. Once we know what you have for hardware it'll be easier to diagnose.

---

### Post by Blutkoete on 2010-12-07
*lspci* returns 

```

...
02:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe

```

I just checked their homepage, according to the manufacturer the 28xx driver should also fit the 30xx series.

*EDIT:* Or no, maybe that's just true for the firmware.

Thank you very much,

Blutkoete

---

### Post by TBABill on 2010-12-07
Ok, first look in Synaptic and see if you have the b43 driver installed. If you do, uninstall it there (mark for removal, then apply).
 
To get the 3090 going it looks like you need to use the RT2060STA so ```
sudo gedit /etc/modprobe.d/blacklist.conf
``` and then add all this to the end of the file: ```
blacklist rt2800pci
blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2x00usb
``` Then ```
sudo gedit /etc/modules
``` and add the following to the end of the file ```
rt2860
rt2860sta
``` and then ```
sudo modprobe rt2860sta
```
 
You may need to reboot.

---

### Post by Trandre on 2010-12-07
Hi I am not an Ubuntu specialist, but it sounds like a simular problem that i had. I have this problem on my dell laptop. 

I solved it my disableing the hardware switch to the Wifi, reboot and then enabeling it when back on. Sometimes I have to rightclick and enable wireless.

Another odd thing on my fresh out of the box install is that the settings for administration --> users --> advanced settings--> user privileges. The wifi is not included 

Hope this helps;)

---

### Post by Blutkoete on 2010-12-07
Hello TBABill, hello Trandre!

I tried the turn-off-turn-on trick already (normally that solved my problems, too), but this time it didn't work.

So I followed TBABill's precise instructions and it worked like a charm. I'm back online via my wireless interface! Thank you very much.

I'm just curios:

So the blacklist entries prevent the Kernel from loading those drivers, while the modules entries force him to do so? Is there somewhere a nice documentations for those files and for the way the Kernel handles the drivers (I mean, it appears to load a [wrong] driver when there is no entry in the modules file)?

But anyway, thank you very much!

I'll add some tags to this thread for other Ralink RT3090 users.

---

### Post by TBABill on 2010-12-07
You could remove the entries from modules as well. Glad to have helped!

---

