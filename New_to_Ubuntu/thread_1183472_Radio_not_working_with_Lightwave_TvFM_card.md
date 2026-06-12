---
title: "Radio not working with Lightwave Tv/FM card"
date: 2009-06-10
forum: New to Ubuntu
---

### Post by demikid on 2009-06-10
I have this tv/radio card.It used to work  windows perfectly both tv and radio. In Ubuntu however,the radio part of it does not work. Tv works perfectly with tvtime. kradio does not have sound nor does it  pick any radio stations.I am suspecting it's a case of incorrect tuner but i have tried all the tuners with the modprobe tuner=x option, nothing works. i have tried different card numbers even, with no luck sadly:(.I have been using ubuntu for three years now but i have never nailed this one. Somebody help.

The card is a Lightwave Tv/FM Card.Its is detected as a LifeView/Typhoon card.

Here is the dmesg output.

[   10.043772] Linux video capture interface: v2.00
[   10.385843] saa7130/34: v4l2 driver version 0.2.14 loaded
[   10.388274] saa7134 0000:02:07.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[   10.388286] saa7130[0]: found at 0000:02:07.0, rev: 1, irq: 23, latency: 248, mmio: 0xfebffc00
[   10.388295] saa7130[0]: subsystem: 4e42:0138, board: LifeView/Typhoon FlyVIDEO2000 [card=3,autodetected]
[   10.388382] saa7130[0]: board init: gpio is 39100
[   10.388387] saa7130[0]: there are different flyvideo cards with different tuners
[   10.388388] saa7130[0]: out there, you might have to use the tuner=<nr> insmod
[   10.388390] saa7130[0]: option to override the default value.
[   10.388563] input: saa7134 IR (LifeView/Typhoon Fl as /devices/pci0000:00/0000:00:1e.0/0000:02:07.0/input/input6
[   10.448466] ppdev: user-space parallel port driver
[   10.540688] saa7130[0]: i2c eeprom 00: 42 4e 38 01 10 28 ff ff ff ff ff ff ff ff ff ff
[   10.540706] saa7130[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.540719] saa7130[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.540733] saa7130[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.540746] saa7130[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.540760] saa7130[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.540773] saa7130[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.540786] saa7130[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.540799] saa7130[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.540813] saa7130[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.540826] saa7130[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.540839] saa7130[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.540853] saa7130[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.540866] saa7130[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.540879] saa7130[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.540893] saa7130[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.588028] tuner' 0-0061: chip found @ 0xc2 (saa7130[0])
[   10.597221] tuner' 0-0063: chip found @ 0xc6 (saa7130[0])
[   10.660024] tuner-simple 0-0061: creating new instance
[   10.660032] tuner-simple 0-0061: type set to 37 (LG PAL (newer TAPC series))
[   10.684174] saa7130[0]: registered device video0 [v4l2]
[   10.684253] saa7130[0]: registered device vbi0
[   10.684326] saa7130[0]: registered device radio0
[   10.707822] saa7134 ALSA driver for DMA sound loaded
[   10.707866] saa7130[0]/alsa: saa7130[0] at 0xfebffc00 irq 23 registered as card -2
[   10.749674] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.749785] Intel ICH 0000:00:1e.2: setting latency timer to 64

---

