---
title: "Moving a driver from one laptop to another?"
date: 2014-03-28
forum: Networking &amp; Wireless
---

### Post by riverguy99 on 2014-03-28
I have two Dell D620 laptops. On one the wireless works and on the other it never has.  Is there a way to extract the driver (or driver specs/info) so that I can find and use the same one on the other laptop?

---

### Post by praseodym on 2014-03-28
Is it the same device? Check with both:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
rfkill list
```

---

### Post by riverguy99 on 2014-03-28
Thanks.  I'll have access to both laptops this afternoon and will post what I find.  :)

---

### Post by riverguy99 on 2014-03-28
**OK, here is the output from the D620 on which the wireless works:**

[COLOR=#222222][FONT=arial]dell@dell-Latitude-D630:~$ uname -a[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Linux dell-Latitude-D630 3.11.0-18-generic #32-Ubuntu SMP Tue Feb 18 21:13:28 UTC 2014 i686 i686 i686 GNU/Linux[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]dell@dell-Latitude-D630:~$ lipci - nnk | grep -iA2net[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]grep: 2net: invalid context length argument[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]No command 'lipci' found, did you mean:[/FONT][/COLOR]
[COLOR=#222222][FONT=arial] Command 'lspci' from package 'pciutils' (main)[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]lipci: command not found[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]dell@dell-Latitude-D630:~$ lsusb[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Bus 007 Device 003: ID 0b97:7772 O2 Micro, Inc. OZ776 CCID Smartcard Reader[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Bus 007 Device 002: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]dell@dell-Latitude-D630:~$ lsmod[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Module                  Size  Used by[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]parport_pc             31981  0 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]ppdev                  17391  0 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]bnep                   18959  2 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]rfcomm                 53664  0 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]bluetooth             323656  10 bnep,rfcomm[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]coretemp               13195  0 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]gpio_ich               13229  0 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]kvm                   368975  0 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]joydev                 17097  0 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]snd_hda_codec_idt      44605  1 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]dell_wmi               12665  0 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]sparse_keymap          13708  1 dell_wmi[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]dell_laptop            17161  0 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]dcdbas                 14383  1 dell_laptop[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]snd_hda_intel          42658  3 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]pcmcia                 51368  0 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]snd_hda_codec         164003  2 snd_hda_codec_idt,snd_hda_[/FONT][/COLOR][COLOR=#222222][FONT=arial]intel[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]arc4                   12536  2 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]snd_hwdep              13272  1 snd_hda_codec[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]snd_pcm                89488  2 snd_hda_codec,snd_hda_intel[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]iwl3945                63619  0 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]snd_page_alloc         14230  2 snd_pcm,snd_hda_intel[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]snd_seq_midi           13132  0 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]iwlegacy               88016  1 iwl3945[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]yenta_socket           40193  0 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]microcode              18894  0 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]snd_seq_midi_event     14475  1 snd_seq_midi[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]mac80211              517444  2 iwl3945,iwlegacy[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]pcmcia_rsrc            18319  1 yenta_socket[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]psmouse                90642  0 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]serio_raw              13189  0 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]pcmcia_core            22328  3 pcmcia,pcmcia_rsrc,yenta_[/FONT][/COLOR][COLOR=#222222][FONT=arial]socket[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]snd_rawmidi            25094  1 snd_seq_midi[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]lpc_ich                16864  0 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]snd_seq                55383  2 snd_seq_midi_event,snd_seq_[/FONT][/COLOR][COLOR=#222222][FONT=arial]midi[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_[/FONT][/COLOR][COLOR=#222222][FONT=arial]midi[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]cfg80211              401762  3 iwl3945,iwlegacy,mac80211[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]snd_timer              24447  2 snd_pcm,snd_seq[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]snd                    60790  16 snd_hwdep,snd_timer,snd_hda_[/FONT][/COLOR][COLOR=#222222][FONT=arial]codec_idt,snd_pcm,snd_seq,snd_[/FONT][/COLOR][COLOR=#222222][FONT=arial]rawmidi,snd_hda_codec,snd_hda_[/FONT][/COLOR][COLOR=#222222][FONT=arial]intel,snd_seq_device,snd_seq_[/FONT][/COLOR][COLOR=#222222][FONT=arial]midi[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]i915                  594442  3 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]soundcore              12600  1 snd[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]drm_kms_helper         46867  1 i915[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]mac_hid                13037  0 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]drm                   242400  4 i915,drm_kms_helper[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]video                  18777  1 i915[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]wmi                    18590  1 dell_wmi[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]i2c_algo_bit           13197  1 i915[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]lp                     13299  0 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]parport                40795  3 lp,ppdev,parport_pc[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]firewire_ohci          35463  0 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]tg3                   152066  0 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]firewire_core          57656  1 firewire_ohci[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]ptp                    18156  1 tg3[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]pps_core               18546  1 ptp[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]crc_itu_t              12627  1 firewire_core[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]dell@dell-Latitude-D630:~$ rfkill list[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]0: phy0: Wireless LAN[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]    Soft blocked: no[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]    Hard blocked: no[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]dell@dell-Latitude-D630:~$

[B]
And this is the output from the one that will not connect:[/B]

[COLOR=#222222][FONT=arial]papa@papa-Latitude-D620:~$ uname -a[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Linux papa-Latitude-D620 3.8.0-29-generic #42~precise1-Ubuntu SMP Wed Aug 14 16:19:23 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]papa@papa-Latitude-D620:~$ lspci - nnk | grep -iA2net[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]grep: 2net: invalid context length argument[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Usage: lspci [<switches>][/FONT][/COLOR]

[COLOR=#222222][FONT=arial]Basic display modes:[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]-mm        Produce machine-readable output (single -m for an obsolete format)[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]-t        Show bus tree[/FONT][/COLOR]

[COLOR=#222222][FONT=arial]Display options:[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]-v        Be verbose (-vv for very verbose)[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]-k        Show kernel drivers handling each device[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]-x        Show hex-dump of the standard part of the config space[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]-xxx        Show hex-dump of the whole config space (dangerous; root only)[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]-xxxx        Show hex-dump of the 4096-byte extended config space (root only)[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]-b        Bus-centric view (addresses and IRQ's as seen by the bus)[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]-D        Always show domain numbers[/FONT][/COLOR]

[COLOR=#222222][FONT=arial]Resolving of device ID's to names:[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]-n        Show numeric ID's[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]-nn        Show both textual and numeric ID's (names & numbers)[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]-q        Query the PCI ID database for unknown ID's via DNS[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]-qq        As above, but re-query locally cached entries[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]-Q        Query the PCI ID database for all ID's via DNS[/FONT][/COLOR]

[COLOR=#222222][FONT=arial]Selection of devices:[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]-s [[[[<domain>]:]<bus>]:][<slot>[/FONT][/COLOR][COLOR=#222222][FONT=arial]][.[<func>]]    Show only devices in selected slots[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]-d [<vendor>]:[<device>]            Show only devices with specified ID's[/FONT][/COLOR]

[COLOR=#222222][FONT=arial]Other options:[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]-i <file>    Use specified ID database instead of /usr/share/misc/pci.ids.gz[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]-p <file>    Look up kernel modules in a given file instead of default modules.pcimap[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]-M        Enable `bus mapping' mode (dangerous; root only)[/FONT][/COLOR]

[COLOR=#222222][FONT=arial]PCI access options:[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]-A <method>    Use the specified PCI access method (see `-A help' for a list)[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]-O <par>=<val>    Set PCI access parameter (see `-O help' for a list)[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]-G        Enable PCI access debugging[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]-H <mode>    Use direct hardware access (<mode> = 1 or 2)[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]-F <file>    Read PCI configuration dump from a given file[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]papa@papa-Latitude-D620:~$ lsusb[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Bus 001 Device 003: ID 413c:0058 Dell Computer Corp. Port Replicator[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Bus 002 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Bus 001 Device 005: ID 046d:c52b Logitech, Inc. Unifying Receiver[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Bus 001 Device 006: ID 046d:c526 Logitech, Inc. Nano Receiver[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Bus 002 Device 003: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Bus 001 Device 007: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Bus 002 Device 004: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]papa@papa-Latitude-D620:~$ lsmod[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]Module                  Size  Used by[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]bnep                   18258  2 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]rfcomm                 47864  0 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]bluetooth             247024  10 bnep,rfcomm[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]usblp                  18284  0 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]snd_hda_codec_idt      71153  1 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]snd_hda_intel          44339  3 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]snd_hda_codec         141716  2 snd_hda_codec_idt,snd_hda_[/FONT][/COLOR][COLOR=#222222][FONT=arial]intel[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]coretemp               13596  0 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]joydev                 17613  0 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]hid_logitech_dj        18767  0 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]hid_generic            12540  0 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]i915                  620421  2 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]usbhid                 47346  1 hid_logitech_dj[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]snd_hwdep              13668  1 snd_hda_codec[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]snd_pcm               102477  2 snd_hda_intel,snd_hda_codec[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]hid                   105549  3 hid_logitech_dj,hid_generic,[/FONT][/COLOR][COLOR=#222222][FONT=arial]usbhid[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]kvm                   455932  0 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]snd_seq_midi           13324  0 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]snd_rawmidi            30417  1 snd_seq_midi[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]gpio_ich               13526  0 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]snd_seq_midi_event     14899  1 snd_seq_midi[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]drm_kms_helper         49597  1 i915[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]snd_seq                61930  2 snd_seq_midi,snd_seq_midi_[/FONT][/COLOR][COLOR=#222222][FONT=arial]event[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]drm                   287564  3 i915,drm_kms_helper[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]snd_timer              29989  2 snd_pcm,snd_seq[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_[/FONT][/COLOR][COLOR=#222222][FONT=arial]seq[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]pcmcia                 49389  0 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]psmouse                97873  0 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]yenta_socket           32135  0 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]microcode              23017  0 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]mac_hid                13253  0 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]snd                    69533  15 snd_hda_codec_idt,snd_hda_[/FONT][/COLOR][COLOR=#222222][FONT=arial]intel,snd_hda_codec,snd_hwdep,[/FONT][/COLOR][COLOR=#222222][FONT=arial]snd_pcm,snd_rawmidi,snd_seq,[/FONT][/COLOR][COLOR=#222222][FONT=arial]snd_timer,snd_seq_device[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]soundcore              12680  1 snd[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]pcmcia_rsrc            18430  1 yenta_socket[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]lpc_ich                17144  0 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]snd_page_alloc         18798  2 snd_hda_intel,snd_pcm[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]dell_wmi               12681  0 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]dell_laptop            17425  0 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]pcmcia_core            22614  3 pcmcia,yenta_socket,pcmcia_[/FONT][/COLOR][COLOR=#222222][FONT=arial]rsrc[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]serio_raw              13215  0 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]sparse_keymap          13890  1 dell_wmi[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]i2c_algo_bit           13564  1 i915[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]dcdbas                 14449  1 dell_laptop[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]ppdev                  17113  0 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]wmi                    19256  1 dell_wmi[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]parport_pc             28284  1 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]video                  19652  1 i915[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]lp                     17799  0 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]parport                46562  3 ppdev,parport_pc,lp[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]tg3                   165622  0 [/FONT][/COLOR]
[COLOR=#222222][FONT=arial]ptp                    18668  1 tg3[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]pps_core               14080  1 ptp[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]papa@papa-Latitude-D620:~$ rfkill list[/FONT][/COLOR]
[COLOR=#222222][FONT=arial]papa@papa-Latitude-D620:~$ [/FONT][/COLOR]



[/FONT][/COLOR]

---

### Post by GigabyteProduction on 2014-03-28
could you run ```
lspci -nnk
``` on both devices and return the output to me?

---

### Post by riverguy99 on 2014-03-28
**From the D-620 that gets online:**

dell@dell-Latitude-D630:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
     Subsystem: Dell Device [1028:01f9]
    Kernel driver in use: agpgart-intel
00:02.0  VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960  Integrated Graphics Controller (primary) [8086:2a02] (rev 0c)
     Subsystem: Dell Latitude D630 [1028:01f9]
    Kernel driver in use: i915
00:02.1  Display controller [0380]: Intel Corporation Mobile GM965/GL960  Integrated Graphics Controller (secondary) [8086:2a03] (rev 0c)
     Subsystem: Dell Device [1028:01f9]
00:1a.0 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
    Subsystem: Dell Device [1028:01f9]
    Kernel driver in use: uhci_hcd
 00:1a.1 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
    Subsystem: Dell Device [1028:01f9]
    Kernel driver in use: uhci_hcd
00:1a.7 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
     Subsystem: Dell Device [1028:01f9]
    Kernel driver in use: ehci-pci
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
    Subsystem: Dell Dell Latitude D630 [1028:01f9]
     Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
    Kernel driver in use: pcieport
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02)
     Kernel driver in use: pcieport
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 02)
    Kernel driver in use: pcieport
00:1d.0 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
     Subsystem: Dell Device [1028:01f9]
    Kernel driver in use: uhci_hcd
00:1d.1 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
    Subsystem: Dell Device [1028:01f9]
     Kernel driver in use: uhci_hcd
00:1d.2 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
    Subsystem: Dell Device [1028:01f9]
    Kernel driver in use: uhci_hcd
 00:1d.7 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
    Subsystem: Dell Device [1028:01f9]
    Kernel driver in use: ehci-pci
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2)
 00:1f.0 ISA bridge [0601]: Intel Corporation 82801HM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)
    Subsystem: Dell Device [1028:01f9]
    Kernel driver in use: lpc_ich
00:1f.1 IDE interface [0101]: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02)
     Subsystem: Dell Device [1028:01f9]
    Kernel driver in use: ata_piix
00:1f.2 IDE interface [0101]: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [IDE mode] [8086:2828] (rev 02)
    Subsystem: Dell Device [1028:01f9]
     Kernel driver in use: ata_piix
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
    Subsystem: Dell Device [1028:01f9]
03:01.0 CardBus bridge [0607]: O2 Micro, Inc. Cardbus bridge [1217:7135] (rev 21)
     Subsystem: Dell Device [1028:01f9]
    Kernel driver in use: yenta_cardbus
03:01.4 FireWire (IEEE 1394) [0c00]: O2 Micro, Inc. Firewire (IEEE 1394) [1217:00f7] (rev 02)
    Subsystem: Dell Device [1028:01f9]
     Kernel driver in use: firewire_ohci
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express [14e4:1673] (rev 02)
    Subsystem: Dell Device [1028:01f9]
    Kernel driver in use: tg3
 0c:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Subsystem: Intel Corporation Device [8086:1020]
    Kernel driver in use: iwl3945
dell@dell-Latitude-D630:~$ 
[B]
And from the one that does not:[/B]

papa@papa-Latitude-D620:~$ lspci -nnk
00:00.0 Host bridge [0600]:  Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express  Memory Controller Hub [8086:27a0] (rev 03)
    Subsystem: Dell Device [1028:01c2]
    Kernel driver in use: agpgart-intel
00:02.0 VGA compatible  controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML  Express Integrated Graphics Controller [8086:27a2] (rev 03)
    Subsystem: Dell Device [1028:01c2]
    Kernel driver in use: i915
    Kernel modules: intelfb, i915
00:02.1  Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME,  943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
    Subsystem: Dell Device [1028:01c2]
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 01)
    Subsystem: Dell Device [1028:01c2]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 01)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 01)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 01)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 01)
    Subsystem: Dell Device [1028:01c2]
    Kernel driver in use: uhci_hcd
00:1d.1 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 01)
    Subsystem: Dell Device [1028:01c2]
    Kernel driver in use: uhci_hcd
00:1d.2 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 01)
    Subsystem: Dell Device [1028:01c2]
    Kernel driver in use: uhci_hcd
00:1d.3 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 01)
    Subsystem: Dell Device [1028:01c2]
    Kernel driver in use: uhci_hcd
00:1d.7 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 01)
    Subsystem: Dell Device [1028:01c2]
    Kernel driver in use: ehci-pci
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 01)
    Subsystem: Dell Device [1028:01c2]
    Kernel driver in use: lpc_ich
    Kernel modules: leds-ss4200, lpc_ich, intel-rng
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] [8086:27c4] (rev 01)
    Subsystem: Dell Device [1028:01c2]
    Kernel driver in use: ata_piix
    Kernel modules: pata_acpi
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 01)
    Subsystem: Dell Device [1028:01c2]
    Kernel modules: i2c-i801
03:01.0 CardBus bridge [0607]: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller [1217:6972] (rev 40)
    Subsystem: Dell Device [1028:01c2]
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express [14e4:1600] (rev 02)
    Subsystem: Dell Latitude D620 [1028:01c2]
    Kernel driver in use: tg3
    Kernel modules: tg3
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)
    Subsystem: Dell Wireless 1490 Dual Band WLAN Mini-Card [1028:0007]
    Kernel modules: ssb
papa@papa-Latitude-D620:~$ 
[FONT=arial]
[/FONT]

---

### Post by GigabyteProduction on 2014-03-28
well that's why right there, they're two different wifi cards. i also had problems with broadcom using different drivers than what it should...
```
0c:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Subsystem: Intel Corporation Device [8086:1020]
    Kernel driver in use: iwl3945
```

```
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)
    Subsystem: Dell Wireless 1490 Dual Band WLAN Mini-Card [1028:0007]
    Kernel modules: ssb
```
now this specific broadcom card needs the b43-fwcutter package, and since you are offline on that machine, you'll have to get on a machine that has the internet and get the firmware-b43-installer deb file from [https://launchpad.net/ubuntu/+source/b43-fwcutter](https://launchpad.net/ubuntu/+source/b43-fwcutter) and install it with ```
sudo dpkg -i filename.deb
``` and if it fails to install, look at what packages it says it requires and obtain the deb files for them, all of the files you need should all be in the packages section of [https://launchpad.net/ubuntu/+source/b43-fwcutter](https://launchpad.net/ubuntu/+source/b43-fwcutter) but i may be wrong so let me know if there's something missing

---

### Post by westie457 on 2014-03-29
@ riverguy99
The [COLOR=#000000][FONT=Ubuntu Mono]BCM4311 802.11a/b/g [14e4:4312] (rev 01) chip works better with a slightly different driver.

Plug in a cable, open a terminal, run ```
sudo apt-get install linux-firmware-nonfree
``` unplug the cable and reboot. Let us know what happens.
If any errors post bak here.[/FONT][/COLOR]

---

### Post by riverguy99 on 2014-03-29
When I downloaded and tried to install the firmware package, I got: Conflicts with installed package: firmware -b43-lpphy-installer.

---

### Post by GigabyteProduction on 2014-03-29
my card wouldn't work with the linux-firmware-nonfree, and  [http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43) says it works, but if  linux-firmware-nonfree works better, then i guess it's worth a shot.

> **riverguy99 said:**
> When I downloaded and tried to install the firmware package, I got: Conflicts with installed package: firmware -b43-lpphy-installer.

If there's a conflicting package, remove it with ```
sudo apt-get remove firmware-b43-lpphy-installer
```

---

### Post by riverguy99 on 2014-03-29
Did the remove, tried the driver again.  It tried to install and gave me this:  Dependency not satisfiable:  D43 Fwcutter (>=1:015-14)

---

### Post by GigabyteProduction on 2014-03-29
for which driver?

---

### Post by westie457 on 2014-03-29
Try ```
sudo apt-get remove b43-fwcutter && sudo apt-get purge firmware-b43-lpphy-installer

sudo apt-get install --reinstall linux-firmware-nonfree
```

And next ```
sudo modprobe -rvf b43

sudo modprobe wl
```

If no errors unplug the cable and check the netwok icon near the top-right for networks.

If error is module not found then run 'sudo modprobe b43'

Let us have your report.

---

### Post by riverguy99 on 2014-03-30
I did the remove, reinstalled [COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install linux-firmware-nonfree

Rebooted, and still no wifi showing.
[/FONT][/COLOR]

---

### Post by GigabyteProduction on 2014-03-30
try using my driver ```
sudo apt-get install firmware-b43-installer
```

but uninstall the other driver, first.

---

