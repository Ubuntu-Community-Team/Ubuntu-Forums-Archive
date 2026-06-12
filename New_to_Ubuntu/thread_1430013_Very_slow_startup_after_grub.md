---
title: "Very slow startup after grub"
date: 2010-03-14
forum: New to Ubuntu
---

### Post by golgiapparatus on 2010-03-14
I know very little about how to do things in ubuntu, and this is my first time using linux, so I apologize in advance if I have trouble understanding any help you guys offer.

When I start ubuntu from grub, a black screen with a blinking line appears for about two minutes before the ubuntu startup screen appears.  I want the two minutes of nothing to go away!  I read some other threads, ran dmesg, and tried to take some suggestions based on what I could find, such as blacklisting firewire, but I don't know if I did that right or if I screwed more things up.  Here is the latest output for my dmesg:

```
[   92.645370] ohci1394: fw-host25: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   92.745454] ohci1394: fw-host25: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   92.845536] ohci1394: fw-host25: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   92.945620] ohci1394: fw-host25: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   93.045697] ohci1394: fw-host25: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   93.145776] ohci1394: fw-host25: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   93.245094] ohci1394: fw-host25: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   93.345173] ohci1394: fw-host25: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   93.445262] ohci1394: fw-host25: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   93.545341] ohci1394: fw-host25: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   93.645418] ohci1394: fw-host25: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   93.745502] ohci1394: fw-host25: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   93.845580] ohci1394: fw-host25: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   93.945664] ohci1394: fw-host25: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   94.045742] ohci1394: fw-host25: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   94.135827] ohci1394: fw-host25: Serial EEPROM has suspicious values, attempting to set max_packet_size to 512 bytes
[   94.145821] ohci1394: fw-host24: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   94.236014] pci 0000:00:1e.0: can't derive routing for PCI INT A
[   94.236016] ohci1394 0000:04:1a.0: PCI INT A: no GSI - using IRQ 10
[   94.400007] ohci1394: fw-host26: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   94.543827] ohci1394: fw-host26: Runaway loop while stopping context: ...
[   94.597542] ohci1394: fw-host26: Runaway loop while stopping context: ...
[   94.651259] ohci1394: fw-host26: Runaway loop while stopping context: ...
[   94.704976] ohci1394: fw-host26: Runaway loop while stopping context: ...
[   94.704981] ohci1394: fw-host26: OHCI-1394 165.165 (PCI): IRQ=[10]  MMIO=[fda99000-fda997ff]  Max Packet=[65536]  IR/IT contexts=[32/32]
[   94.710001] ohci1394: fw-host26: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   94.814598] ohci1394: fw-host26: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   94.914683] ohci1394: fw-host26: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   95.014760] ohci1394: fw-host26: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   95.114839] ohci1394: fw-host26: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   95.214923] ohci1394: fw-host26: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   95.315002] ohci1394: fw-host26: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   95.415085] ohci1394: fw-host26: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   95.515164] ohci1394: fw-host26: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   95.615241] ohci1394: fw-host26: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   95.715331] ohci1394: fw-host26: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   95.815409] ohci1394: fw-host26: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   95.915493] ohci1394: fw-host26: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   96.015573] ohci1394: fw-host26: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   96.115652] ohci1394: fw-host26: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   96.215735] ohci1394: fw-host26: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   96.315051] ohci1394: fw-host26: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   96.415133] ohci1394: fw-host26: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   96.515212] ohci1394: fw-host26: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   96.615301] ohci1394: fw-host26: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   96.715386] ohci1394: fw-host26: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   96.815463] ohci1394: fw-host26: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   96.915551] ohci1394: fw-host26: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   97.015629] ohci1394: fw-host26: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   97.115708] ohci1394: fw-host26: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   97.215789] ohci1394: fw-host26: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   97.315869] ohci1394: fw-host26: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   97.415951] ohci1394: fw-host26: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   97.516030] ohci1394: fw-host26: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   97.616108] ohci1394: fw-host26: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   97.706193] ohci1394: fw-host26: Serial EEPROM has suspicious values, attempting to set max_packet_size to 512 bytes
[   97.716191] ohci1394: fw-host25: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   97.805608] pci 0000:00:1e.0: can't derive routing for PCI INT A
[   97.805610] ohci1394 0000:04:1b.0: PCI INT A: no GSI - using IRQ 10
[   97.970007] ohci1394: fw-host27: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   98.113828] ohci1394: fw-host27: Runaway loop while stopping context: ...
[   98.167542] ohci1394: fw-host27: Runaway loop while stopping context: ...
[   98.221261] ohci1394: fw-host27: Runaway loop while stopping context: ...
[   98.274976] ohci1394: fw-host27: Runaway loop while stopping context: ...
[   98.274980] ohci1394: fw-host27: OHCI-1394 165.165 (PCI): IRQ=[10]  MMIO=[fda9a000-fda9a7ff]  Max Packet=[65536]  IR/IT contexts=[32/32]
[   98.280001] ohci1394: fw-host27: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   98.385061] ohci1394: fw-host27: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   98.485146] ohci1394: fw-host27: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   98.585223] ohci1394: fw-host27: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   98.685323] ohci1394: fw-host27: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   98.785402] ohci1394: fw-host27: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   98.885480] ohci1394: fw-host27: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   98.985565] ohci1394: fw-host27: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   99.085645] ohci1394: fw-host27: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   99.185728] ohci1394: fw-host27: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   99.285806] ohci1394: fw-host27: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   99.385007] ohci1394: fw-host27: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   99.485091] ohci1394: fw-host27: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   99.585169] ohci1394: fw-host27: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   99.685253] ohci1394: fw-host27: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   99.785331] ohci1394: fw-host27: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   99.885409] ohci1394: fw-host27: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   99.985492] ohci1394: fw-host27: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  100.085580] ohci1394: fw-host27: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  100.185662] ohci1394: fw-host27: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  100.285742] ohci1394: fw-host27: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  100.385819] ohci1394: fw-host27: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  100.485903] ohci1394: fw-host27: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  100.585981] ohci1394: fw-host27: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  100.686075] ohci1394: fw-host27: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  100.786152] ohci1394: fw-host27: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  100.885460] ohci1394: fw-host27: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  100.985550] ohci1394: fw-host27: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  101.085629] ohci1394: fw-host27: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  101.185712] ohci1394: fw-host27: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  101.275792] ohci1394: fw-host27: Serial EEPROM has suspicious values, attempting to set max_packet_size to 512 bytes
[  101.285791] ohci1394: fw-host26: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  101.375984] ohci1394 0000:04:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  101.540007] ohci1394: fw-host28: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  101.683827] ohci1394: fw-host28: Runaway loop while stopping context: ...
[  101.737542] ohci1394: fw-host28: Runaway loop while stopping context: ...
[  101.791268] ohci1394: fw-host28: Runaway loop while stopping context: ...
[  101.844986] ohci1394: fw-host28: Runaway loop while stopping context: ...
[  101.844991] ohci1394: fw-host28: OHCI-1394 165.165 (PCI): IRQ=[17]  MMIO=[fda9b000-fda9b7ff]  Max Packet=[65536]  IR/IT contexts=[32/32]
[  101.850001] ohci1394: fw-host28: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  101.955073] ohci1394: fw-host28: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  102.055153] ohci1394: fw-host28: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  102.155235] ohci1394: fw-host28: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  102.255316] ohci1394: fw-host28: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  102.354891] ohci1394: fw-host28: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  102.454975] ohci1394: fw-host28: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  102.555053] ohci1394: fw-host28: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  102.655149] ohci1394: fw-host28: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  102.755226] ohci1394: fw-host28: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  102.855308] ohci1394: fw-host28: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  102.955391] ohci1394: fw-host28: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  103.055470] ohci1394: fw-host28: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  103.155558] ohci1394: fw-host28: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  103.255638] ohci1394: fw-host28: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  103.355715] ohci1394: fw-host28: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  103.455799] ohci1394: fw-host28: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  103.555877] ohci1394: fw-host28: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  103.655961] ohci1394: fw-host28: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  103.756038] ohci1394: fw-host28: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  103.855344] ohci1394: fw-host28: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  103.955426] ohci1394: fw-host28: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  104.055505] ohci1394: fw-host28: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  104.155589] ohci1394: fw-host28: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  104.255667] ohci1394: fw-host28: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  104.355744] ohci1394: fw-host28: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  104.455829] ohci1394: fw-host28: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  104.555906] ohci1394: fw-host28: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  104.656001] ohci1394: fw-host28: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  104.756079] ohci1394: fw-host28: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  104.846164] ohci1394: fw-host28: Serial EEPROM has suspicious values, attempting to set max_packet_size to 512 bytes
[  104.856158] ohci1394: fw-host27: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  104.946350] ohci1394 0000:04:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[  105.110007] ohci1394: fw-host29: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  105.253827] ohci1394: fw-host29: Runaway loop while stopping context: ...
[  105.307553] ohci1394: fw-host29: Runaway loop while stopping context: ...
[  105.361280] ohci1394: fw-host29: Runaway loop while stopping context: ...
[  105.414997] ohci1394: fw-host29: Runaway loop while stopping context: ...
[  105.415002] ohci1394: fw-host29: OHCI-1394 165.165 (PCI): IRQ=[20]  MMIO=[fda9c000-fda9c7ff]  Max Packet=[65536]  IR/IT contexts=[32/32]
[  105.420001] ohci1394: fw-host29: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  105.525083] ohci1394: fw-host29: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  105.625163] ohci1394: fw-host29: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  105.725244] ohci1394: fw-host29: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  105.825331] ohci1394: fw-host29: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  105.925413] ohci1394: fw-host29: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  106.025492] ohci1394: fw-host29: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  106.125572] ohci1394: fw-host29: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  106.225657] ohci1394: fw-host29: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  106.325734] ohci1394: fw-host29: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  106.425817] ohci1394: fw-host29: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  106.525895] ohci1394: fw-host29: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  106.625981] ohci1394: fw-host29: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  106.726063] ohci1394: fw-host29: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  106.826143] ohci1394: fw-host29: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  106.925301] ohci1394: fw-host29: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  107.025380] ohci1394: fw-host29: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  107.125458] ohci1394: fw-host29: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  107.225543] ohci1394: fw-host29: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  107.325620] ohci1394: fw-host29: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  107.425705] ohci1394: fw-host29: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  107.525782] ohci1394: fw-host29: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  107.625861] ohci1394: fw-host29: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  107.725943] ohci1394: fw-host29: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  107.826022] ohci1394: fw-host29: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  107.926104] ohci1394: fw-host29: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  108.026184] ohci1394: fw-host29: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  108.126262] ohci1394: fw-host29: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  108.226346] ohci1394: fw-host29: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  108.326424] ohci1394: fw-host29: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  108.415755] ohci1394: fw-host29: Serial EEPROM has suspicious values, attempting to set max_packet_size to 512 bytes
[  108.425753] ohci1394: fw-host28: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  108.515955] pci 0000:00:1e.0: can't derive routing for PCI INT A
[  108.515957] ohci1394 0000:04:1e.0: PCI INT A: no GSI - using IRQ 10
[  108.680007] ohci1394: fw-host30: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  108.823817] ohci1394: fw-host30: Runaway loop while stopping context: ...
[  108.877531] ohci1394: fw-host30: Runaway loop while stopping context: ...
[  108.931259] ohci1394: fw-host30: Runaway loop while stopping context: ...
[  108.984998] ohci1394: fw-host30: Runaway loop while stopping context: ...
[  108.985003] ohci1394: fw-host30: OHCI-1394 165.165 (PCI): IRQ=[10]  MMIO=[fda9d000-fda9d7ff]  Max Packet=[65536]  IR/IT contexts=[32/32]
[  108.990001] ohci1394: fw-host30: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  109.095083] ohci1394: fw-host30: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  109.195168] ohci1394: fw-host30: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  109.295246] ohci1394: fw-host30: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  109.395324] ohci1394: fw-host30: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  109.495408] ohci1394: fw-host30: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  109.595486] ohci1394: fw-host30: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  109.695573] ohci1394: fw-host30: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  109.795653] ohci1394: fw-host30: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  109.895183] ohci1394: fw-host30: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  109.995272] ohci1394: fw-host30: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  110.095350] ohci1394: fw-host30: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  110.195434] ohci1394: fw-host30: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  110.295512] ohci1394: fw-host30: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  110.395592] ohci1394: fw-host30: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  110.495674] ohci1394: fw-host30: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  110.595753] ohci1394: fw-host30: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  110.695847] ohci1394: fw-host30: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  110.795926] ohci1394: fw-host30: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  110.896003] ohci1394: fw-host30: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  110.996088] ohci1394: fw-host30: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  111.096165] ohci1394: fw-host30: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  111.196249] ohci1394: fw-host30: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  111.296331] ohci1394: fw-host30: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  111.396410] ohci1394: fw-host30: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  111.495710] ohci1394: fw-host30: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  111.595790] ohci1394: fw-host30: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  111.695872] ohci1394: fw-host30: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  111.795951] ohci1394: fw-host30: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  111.896029] ohci1394: fw-host30: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  111.986114] ohci1394: fw-host30: Serial EEPROM has suspicious values, attempting to set max_packet_size to 512 bytes
[  111.996112] ohci1394: fw-host29: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  112.086308] pci 0000:00:1e.0: can't derive routing for PCI INT A
[  112.086310] ohci1394 0000:04:1f.0: PCI INT A: no GSI - using IRQ 10
[  112.140029] ohci1394: fw-host31: OHCI-1394 1.1 (PCI): IRQ=[10]  MMIO=[fda9e000-fda9e7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[  113.090008] ohci1394: fw-host30: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[  113.293907] PM: Starting manual resume from disk
[  113.293917] PM: Resume from partition 8:21
[  113.293918] PM: Checking hibernation image.
[  113.294208] PM: Resume from disk failed.
[  113.337855] EXT4-fs (sdb1): barriers enabled
[  113.364801] kjournald2 starting: pid 534, dev sdb1:8, commit interval 5 seconds
[  113.364948] EXT4-fs (sdb1): delayed allocation enabled
[  113.364951] EXT4-fs: file extents enabled
[  113.378217] EXT4-fs: mballoc enabled
[  113.378236] EXT4-fs (sdb1): mounted filesystem with ordered data mode
[  113.952006] type=1505 audit(1268590469.506:2): operation="profile_load" pid=561 name=/usr/share/gdm/guest-session/Xsession
[  113.954779] type=1505 audit(1268590469.506:3): operation="profile_load" pid=562 name=/sbin/dhclient3
[  113.955378] type=1505 audit(1268590469.506:4): operation="profile_load" pid=562 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[  113.955709] type=1505 audit(1268590469.506:5): operation="profile_load" pid=562 name=/usr/lib/connman/scripts/dhclient-script
[  114.000493] type=1505 audit(1268590469.556:6): operation="profile_load" pid=563 name=/usr/bin/evince
[  114.009919] type=1505 audit(1268590469.556:7): operation="profile_load" pid=563 name=/usr/bin/evince-previewer
[  114.015440] type=1505 audit(1268590469.566:8): operation="profile_load" pid=563 name=/usr/bin/evince-thumbnailer
[  114.026461] type=1505 audit(1268590469.576:9): operation="profile_load" pid=565 name=/usr/bin/freshclam
[  114.034757] type=1505 audit(1268590469.586:10): operation="profile_load" pid=566 name=/usr/lib/cups/backend/cups-pdf
[  114.035476] type=1505 audit(1268590469.586:11): operation="profile_load" pid=566 name=/usr/sbin/cupsd
[  114.168977] irq 18: nobody cared (try booting with the "irqpoll" option)
[  114.168982] Pid: 0, comm: swapper Not tainted 2.6.31-20-generic #57-Ubuntu
[  114.168984] Call Trace:
[  114.168985]  <IRQ>  [<ffffffff810b5336>] __report_bad_irq+0x26/0xa0
[  114.168994]  [<ffffffff810b553c>] note_interrupt+0x18c/0x1d0
[  114.168997]  [<ffffffff8107e873>] ? sched_clock_tick+0x83/0xd0
[  114.169000]  [<ffffffff810b5bb5>] handle_fasteoi_irq+0xd5/0x100
[  114.169003]  [<ffffffff81014c5d>] handle_irq+0x1d/0x30
[  114.169005]  [<ffffffff81014137>] do_IRQ+0x67/0xe0
[  114.169008]  [<ffffffff81012a53>] ret_from_intr+0x0/0x11
[  114.169010]  <EOI>  [<ffffffff8101a0bc>] ? mwait_idle+0x7c/0x120
[  114.169016]  [<ffffffff8152fdb5>] ? atomic_notifier_call_chain+0x15/0x20
[  114.169019]  [<ffffffff81010e12>] ? cpu_idle+0xb2/0x100
[  114.169022]  [<ffffffff815275a6>] ? start_secondary+0xa9/0xab
[  114.169023] handlers:
[  114.169025] [<ffffffff813a0d50>] (usb_hcd_irq+0x0/0x80)
[  114.169029] [<ffffffffa0058b60>] (ohci_irq_handler+0x0/0x800 [ohci1394])
[  114.169035] Disabling IRQ #18
[  124.966050] udev: starting version 147
[  124.996966] Adding 11880028k swap on /dev/sdb5.  Priority:-1 extents:1 across:11880028k 
[  125.001817] nvidia: module license 'NVIDIA' taints kernel.
[  125.001821] Disabling lock debugging due to kernel taint
[  125.020926] lp: driver loaded but no devices found
[  125.060328] parport_pc 00:08: reported by Plug and Play ACPI
[  125.060386] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[  125.096335] ppdev: user-space parallel port driver
[  125.104493] ip_tables: (C) 2000-2006 Netfilter Core Team
[  125.134046] lp0: using parport0 (interrupt-driven).
[  125.181334] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  125.181372] HDA Intel 0000:00:1b.0: setting latency timer to 64
[  125.254869] intel_rng: FWH not detected
[  125.256327] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  125.256332] nvidia 0000:01:00.0: setting latency timer to 64
[  125.256478] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  185.18.36  Fri Aug 14 17:35:21 PDT 2009
[  125.366922] hda_codec: Unknown model for ALC888, trying auto-probe from BIOS...
[  125.367095] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input6
[  125.421504] EXT4-fs (sdb1): internal journal on sdb1:8
[  125.833080] __ratelimit: 3 callbacks suppressed
[  125.833082] type=1505 audit(1268615681.380:13): operation="profile_replace" pid=1105 name=/usr/share/gdm/guest-session/Xsession
[  125.834253] type=1505 audit(1268615681.390:14): operation="profile_replace" pid=1106 name=/sbin/dhclient3
[  125.834791] type=1505 audit(1268615681.390:15): operation="profile_replace" pid=1106 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[  125.835083] type=1505 audit(1268615681.390:16): operation="profile_replace" pid=1106 name=/usr/lib/connman/scripts/dhclient-script
[  125.837367] type=1505 audit(1268615681.390:17): operation="profile_replace" pid=1107 name=/usr/bin/evince
[  125.845988] type=1505 audit(1268615681.400:18): operation="profile_replace" pid=1107 name=/usr/bin/evince-previewer
[  125.850995] type=1505 audit(1268615681.400:19): operation="profile_replace" pid=1107 name=/usr/bin/evince-thumbnailer
[  125.857666] type=1505 audit(1268615681.410:20): operation="profile_replace" pid=1109 name=/usr/bin/freshclam
[  125.858977] type=1505 audit(1268615681.410:21): operation="profile_replace" pid=1110 name=/usr/lib/cups/backend/cups-pdf
[  125.859598] type=1505 audit(1268615681.410:22): operation="profile_replace" pid=1110 name=/usr/sbin/cupsd
[  126.163976] sky2 eth0: enabling interface
[  126.164376] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  126.479105] usplash:497 freeing invalid memtype fffffffff9000000-fffffffff9e00000
[  129.168701] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[  129.174135] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  140.140085] eth0: no IPv6 routers present
```Thanks in advance for any help.

---

### Post by golgiapparatus on 2010-03-15
I also got this, if it helps at all:  
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=2f393510-5e0f-4b3c-bbef-d1d26f34ecfa)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xab21c16c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   625,139,711   625,137,664   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x92707cb7

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   601,377,209   601,377,147  83 Linux
/dev/sdb2         601,377,210   625,137,344    23,760,135   5 Extended
/dev/sdb5         601,377,273   625,137,344    23,760,072  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        6C9CF9F29CF9B724                       ntfs                                     
/dev/sdb1        2f393510-5e0f-4b3c-bbef-d1d26f34ecfa   ext4                                     
/dev/sdb5        a298d87a-ea60-4c13-8d81-5e8ec3d08ffe   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)


=========================== sdb1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,1)
search --no-floppy --fs-uuid --set 2f393510-5e0f-4b3c-bbef-d1d26f34ecfa
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 2f393510-5e0f-4b3c-bbef-d1d26f34ecfa
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=2f393510-5e0f-4b3c-bbef-d1d26f34ecfa ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 2f393510-5e0f-4b3c-bbef-d1d26f34ecfa
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=2f393510-5e0f-4b3c-bbef-d1d26f34ecfa ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 2f393510-5e0f-4b3c-bbef-d1d26f34ecfa
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=2f393510-5e0f-4b3c-bbef-d1d26f34ecfa ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 2f393510-5e0f-4b3c-bbef-d1d26f34ecfa
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=2f393510-5e0f-4b3c-bbef-d1d26f34ecfa ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6c9cf9f29cf9b724
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=2f393510-5e0f-4b3c-bbef-d1d26f34ecfa /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=a298d87a-ea60-4c13-8d81-5e8ec3d08ffe none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  35.5GB: boot/grub/core.img
  35.2GB: boot/grub/grub.cfg
    .3GB: boot/initrd.img-2.6.31-14-generic
    .5GB: boot/initrd.img-2.6.31-20-generic
    .3GB: boot/vmlinuz-2.6.31-14-generic
    .4GB: boot/vmlinuz-2.6.31-20-generic
    .5GB: initrd.img
    .3GB: initrd.img.old
    .4GB: vmlinuz
    .3GB: vmlinuz.old
```

---

### Post by oldfred on 2010-03-15
You are past the booting of grub and into kernel loading so the boot info script does not help. I do notice no boot flag on sdb. Linux does not use the boot flag but some BIOS need it to boot. Are you booting from sda or sdb? Grub does load slower (about 20sec) if not on the same drive as Ubuntu. I would boot from sdb.

Did you see this thread?

[http://ubuntuforums.org/showthread.php?t=810125](http://ubuntuforums.org/showthread.php?t=810125)

In grub2 you add irqpoll to /etc/default/grub
[https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202](https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202)

---

### Post by golgiapparatus on 2010-03-16
I had seen that thread before, I re-read it, tried changing the blacklist around, still takes ~3 minutes for kubuntu to load after grub.  It says at the end that it's almost definitely a hardware problem with Shuttle, which is also the kind of computer that I use.  So there is no way to fix this, I guess?

Do you think this would happen with other linux distros?

---

### Post by hongpan1986 on 2010-12-21
I also have the same problem after I remove one of the entries from synpatic manager. I removed one of them because after the auto update, grub created 3 same entries for the system with only number different between them.

it gets so slow after that. i was impressed by how fast the ubuntu starts up, but now, it took about 40 secs to boot up, it was only like 10 secs before.

---

### Post by oldfred on 2010-12-21
I think all you did was house clean out older kernels. We normally suggest you keep the current one and one older one incase there is an issue, so you have something to fall back to.

Do you have an SSD? I have only seen 10 sec boots with SSDs. My system takes about 50-60 sec from power on till working. Windows XP takes over 4 Min. But I am mounting several NTFS partitions as well as multiple ext3 or ext4 partitions. All that adds to boot time.

Did you check the log files like the user above to see if messages or other log file has errors or repeated tries at loading a driver.

---

### Post by gbestrada on 2010-12-21
I had the same problem until I flashed the bios on my computer 

following this thread : [http://ubuntuforums.org/showthread.php?t=1643535&highlight=update+bios+ubuntu;](http://ubuntuforums.org/showthread.php?t=1643535&highlight=update+bios+ubuntu;))

---

