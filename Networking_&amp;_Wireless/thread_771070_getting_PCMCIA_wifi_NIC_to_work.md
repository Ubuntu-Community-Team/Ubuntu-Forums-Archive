---
title: "getting PCMCIA wifi NIC to work"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by anystupidname on 2008-04-27
Hello, I have a D-Link Air DWL-650 802.11b PCMCIA wifi NIC that I'm having difficulty getting it to work.

Question#1: What will I need to do to get it to work without security?
Question#2: Is it possible to connect this NIC using WPA2?

The first thing bothering me is that LSPCMCIA is not showing this device even though one of the LEDs lights up and I have every indication it is functional (works in Winblows) Do I need to use ndiswrapper? IWCONFIG shows nothing too. I'm trying to get this working on an older Thinkpad running Xubuntu 8.04 and I have a newer Thinkpad available (running Kubuntu 8.04) which I'm using to test on too.

DMESG output shows:
> [209191.925328] pccard: PCMCIA card inserted into slot 0
[209191.925740] pcmcia: registering new device pcmcia0.0
[209191.926080] hostap_cs: setting Vcc=33 (constant)
[209191.926149] Checking CFTABLE_ENTRY 0x01 (default 0x01)
[209191.926155] IO window settings: cfg->io.nwin=1 dflt.io.nwin=1
[209191.926160] io->flags = 0x0047, io.base=0x0000, len=128
[209191.927622] hostap_cs: Registered netdevice wifi0
[209191.967425] hostap_cs: index 0x01: , irq 3, io 0x4100-0x417f
[209191.987546] wifi0: __hfa384x_cmd_no_wait(6) - timeout - reg=0x9e44
[209191.987551] hostap_cs: first command failed - assuming card does not have primary firmware
[125417.559657] hostap_cs: assuming no Primary image in flash - card initialization not completed
[125417.559668] wifi0: test Genesis mode with HCR 0x1f
[125417.559690] prism2_pccard_cor_sreset: original COR 41
[125417.563709] prism2_pccard_genesis_sreset: original COR 41
[125417.593558] Readback test failed, HCR 0x1f write 00 e1 a1 ff read 00 ce a1 ce
[125417.593561] wifi0: test Genesis mode with HCR 0x0f
[125417.593576] prism2_pccard_cor_sreset: original COR 41
[125417.597594] prism2_pccard_genesis_sreset: original COR 41
[125417.627439] Readback test succeeded, HCR 0x0f
[125417.627454] prism2_pccard_genesis_sreset: original COR 41
[125417.713118] wifi0: registered netdevice wlan0
[125417.878434] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[209193.810970] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[209193.819682] wlan0: cannot set RID fc02 (len=34) - no PRI f/w
[209193.821646] wifi0: cannot get RID fc28 (len=2) - no PRI f/w
[209193.821656] Could not read current WEP flags.
[209193.821661] wifi0: encryption setup failed
[209193.821665] wlan0: set_encryption failed
[209193.852259] wlan0: cannot get RID fc84 (len=2) - no PRI f/w

Any assistance would be much appreciated!

---

