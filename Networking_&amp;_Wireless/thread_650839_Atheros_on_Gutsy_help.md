---
title: "Atheros on Gutsy help"
date: 2007-12-26
forum: Networking &amp; Wireless
---

### Post by jludeman on 2007-12-26
Bit of background first.

I installled Gutsy on my desktop from the command line. I use Openbox as a window manager. After a lot of head banging I got everything working.

I also installed the full Ubuntu 7.10 on my laptop. Everything but the sound worked.

After a few weeks of ignoring my laptop and really really enjoying openbox on the desktop computer, I decided to do a command line install on the laptop.

Much to my suprise I ended up with no network on the laptop.
Both the full install and the command line install were done from the same cd.

Repeat again same cd - different results.

I did ndiswrapper with the windows drivers. Bingo I got the network up. Reboot once - still have network. Reboot twice - network is dead.

Tried the mad-wifi driver. Make runs with no errors. None of the modules are created anywhere on my computer. Huh?

Using wifi-radar shows my wlan router fine but no connection is ever made. Wifi-radar is showing 96% signal strength.

So my options are?

---

### Post by jludeman on 2007-12-26
I wrote the original post on the desktop. No network on the laptop.

After a complete power down of the laptop the network was again working.

So could someone give me instructions on this mystery?

Do I have to stand on my head at the full moon with one finger in my ear and my thumb in the other ear?
Is wearing chicken feathers and blue paint mandatory?

What is going on with this system?

Actual serious question now.

What if any linux distro should I try?

I've gotten a lot of good info from the folks at Arch.

---

### Post by jludeman on 2007-12-27
Could someone please help?

If you are more familiar with these forums than I am please:

a. Tell me that no help will be forthcoming and why.
b. Point me elsewhere on the web where answers might be available.

Lest you think I'm slacking in my own efforts here is a screen shot of my firefox history and current session.

Here is wifi radar clearly showing my router.

Here is the output from ndiswrapper and ifconfig.
 ndiswrapper -l
net5211 : driver installed
        device (168C:001C) present

 ifconfig
ath0      Link encap:Ethernet  HWaddr 00:19:7D:CA:34:8B  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Memory:d8000000-d8010000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

Output of lsapci -v
04:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
        Subsystem: AMBIT Microsystem Corp. Unknown device 0425
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at d8000000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, fast devsel, latency 0, IRQ 18
        I/O ports at 4000 [size=256]
        Memory at da000000 (64-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at d4000000 [disabled] [size=64K]
        Capabilities: <access denied>

The other controller is not in use but cannot be turned off in this laptops lame bios.

I just noticed that the wireless card is using IRQ 16. Let me check dmesg.
I'll have to boot both machines to windows 2000 so I can attach the output of dmesg. Back in a flash.

---

### Post by jludeman on 2007-12-27
Here are the relevant parts of dmesg. Clearly there is something strange going on with IRQ 16 that I don't know how to fix.

```
[    3.856000] irq 16: nobody cared (try booting with the "irqpoll" option)
[    3.856000]  [<c015b594>] __report_bad_irq+0x24/0x80
[    3.856000]  [<c015b852>] note_interrupt+0x262/0x2a0
[    3.856000]  [<c015aab0>] handle_IRQ_event+0x30/0x60
[    3.856000]  [<c015c23b>] handle_fasteoi_irq+0xbb/0xf0
[    3.856000]  [<c0106b1b>] do_IRQ+0x3b/0x70
[    3.856000]  [<c0105223>] common_interrupt+0x23/0x30
[    3.856000]  [<c0144a4b>] tick_nohz_stop_sched_tick+0x1ab/0x2a0
[    3.856000]  [<c0144c3a>] tick_nohz_restart_sched_tick+0xfa/0x140
[    3.856000]  [<f885c74b>] acpi_processor_idle+0x0/0x425 [processor]
[    3.856000]  [<c01023f0>] cpu_idle+0x30/0xe0
[    3.856000]  [<c03e3a85>] start_kernel+0x325/0x3b0
[    3.856000]  [<c03e31f0>] unknown_bootoption+0x0/0x260
[    3.856000]  =======================
[    3.856000] handlers:
[    3.856000] [<f88ca3b0>] (ohci_irq_handler+0x0/0x9a0 [ohci1394])
[    3.856000] Disabling IRQ #16

[   10.240000] ndiswrapper version 1.45 loaded (smp=yes)
[   10.332000] ndiswrapper: driver net5211 (,06/21/2007,5.3.0.56) loaded
[   10.332000] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 17 (level, low) -> IRQ 16
[   10.332000] ndiswrapper (ZwClose:2247): closing handle 0xdfd1a628 not implemented
[   10.336000] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   10.748000] ndiswrapper: using IRQ 16
[   10.948000] wlan0: ethernet device 00:19:7d:ca:34:8b using serialized NDIS driver: net5211, version: 0x50003, NDIS version: 0x501, vendor: '', 168C:001C.5.conf
[   10.952000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   10.952000] usbcore: registered new interface driver ndiswrapper
[   11.052000] ndiswrapper: changing interface name from 'wlan0' to 'ath0'
```

Anybody have any suggestions?

---

### Post by jludeman on 2007-12-27
Okay I tried the irqpoll option at boot and the network worked. I still don't understand any of this but it's working.

---

