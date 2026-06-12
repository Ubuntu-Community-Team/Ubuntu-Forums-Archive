---
title: "T60 wireless not showing up"
date: 2015-10-05
forum: Networking &amp; Wireless
---

### Post by leon_trotsky on 2015-10-05
I just got a IBM/Lenovo T60, but I cannot get the wireless working.  I assume that there is a wireless card in the machine because when I go to the BIOS it does say that the wireless is enabled.  But I can't see anything once I boot Linux.  Is there some way that I can see what wireless card I actually have, preferably from a terminal?  My understanding is that this machine shipped with a few different wireless cards.

Thanks

---

### Post by tgalati4 on 2015-10-05
Welcome to the forums.

Open a terminal and post the output of:

```
lspci | grep Network
```

Sometimes the card needs reseating.  I have a T43p (the model right before the T60).  Wireless works fine, so it's a matter of tweaking.

Some reading:  [http://www.thinkwiki.org/wiki/Category:T60](http://www.thinkwiki.org/wiki/Category:T60)

---

### Post by leon_trotsky on 2015-10-05
I put in that command both without and with sudo and got nothing back!  Just the cursor again!  :(

---

### Post by Bucky Ball on 2015-10-05
Hmm. Perhaps no wireless card or a dead one. 

Have a look and see if there is one and, if so, reseat as advised above.

---

### Post by leon_trotsky on 2015-10-05
I think to get at the card I need to take out a bunch of screws and pull of some plastic.  Does that sound right?  

[https://www.ifixit.com/Guide/IBM+Thinkpad+T60+Wireless+Card+Replacement/13018](https://www.ifixit.com/Guide/IBM+Thinkpad+T60+Wireless+Card+Replacement/13018)

---

### Post by praseodym on 2015-10-05
Please show the outputs of:
```

lspci -nnk
pccardctl info
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by tgalati4 on 2015-10-05
Mine is easy to get to.  Yours is not.  Try the commands above to see if your network card is detected.  If it is not, then perhaps it was removed or is burned up.

---

### Post by leon_trotsky on 2015-10-06
```
zorro@zorro-ThinkPad-T60:~$ lspci -nnk
00:00.0 Host bridge [0600]:  Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express  Memory Controller Hub [8086:27a0] (rev 03)
    Subsystem: Lenovo ThinkPad T60/R60 series [17aa:2017]
    Kernel driver in use: agpgart-intel
00:02.0  VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS,  943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
    Subsystem: Lenovo ThinkPad T60/R60 series [17aa:201a]
    Kernel driver in use: i915
00:02.1  Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME,  943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
    Subsystem: Lenovo ThinkPad T60/R60 series [17aa:201a]
00:1b.0 Audio device [0403]: Intel Corporation NM10/ICH7 Family High Definition Audio Controller [8086:27d8] (rev 02)
    Subsystem: Lenovo ThinkPad T60/R60 series [17aa:2010]
    Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 1 [8086:27d0] (rev 02)
    Kernel driver in use: pcieport
00:1c.1 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 2 [8086:27d2] (rev 02)
    Kernel driver in use: pcieport
00:1c.2 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 3 [8086:27d4] (rev 02)
    Kernel driver in use: pcieport
00:1c.3 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 4 [8086:27d6] (rev 02)
    Kernel driver in use: pcieport
00:1d.0 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
    Subsystem: Lenovo ThinkPad T60/R60 series [17aa:200a]
    Kernel driver in use: uhci_hcd
00:1d.1 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
    Subsystem: Lenovo ThinkPad T60/R60 series [17aa:200a]
    Kernel driver in use: uhci_hcd
00:1d.2 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
    Subsystem: Lenovo ThinkPad T60/R60 series [17aa:200a]
    Kernel driver in use: uhci_hcd
00:1d.3 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
    Subsystem: Lenovo ThinkPad T60/R60 series [17aa:200a]
    Kernel driver in use: uhci_hcd
00:1d.7 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
    Subsystem: Lenovo ThinkPad T60/R60 series [17aa:200b]
    Kernel driver in use: ehci-pci
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
    Subsystem: Lenovo ThinkPad T60/R60 series [17aa:2009]
    Kernel driver in use: lpc_ich
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
    Subsystem: Lenovo ThinkPad T60/R60 series [17aa:200c]
    Kernel driver in use: ata_piix
00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [AHCI mode] [8086:27c5] (rev 02)
    Subsystem: Lenovo ThinkPad T60/R60 series [17aa:200d]
    Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation NM10/ICH7 Family SMBus Controller [8086:27da] (rev 02)
    Subsystem: Lenovo ThinkPad T60/R60 series [17aa:200f]
02:00.0 Ethernet controller [0200]: Intel Corporation 82573L Gigabit Ethernet Controller [8086:109a]
    Subsystem: Lenovo ThinkPad T60 [17aa:2001]
    Kernel driver in use: e1000e
15:00.0 CardBus bridge [0607]: Texas Instruments PCI1510 PC card Cardbus Controller [104c:ac56]
    Subsystem: Lenovo ThinkPad T60/R60 series [17aa:2012]
    Kernel driver in use: yenta_cardbus
zorro@zorro-ThinkPad-T60:~$ pccardctl info
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
zorro@zorro-ThinkPad-T60:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
zorro@zorro-ThinkPad-T60:~$ lsmod
Module                  Size  Used by
bnep                   20480  2 
rfcomm                 61440  0 
bluetooth             430080  10 bnep,rfcomm
pcmcia                 53248  0 
coretemp               16384  0 
kvm                   413696  0 
snd_hda_codec_analog    16384  1 
snd_hda_codec_generic    65536  1 snd_hda_codec_analog
joydev                 20480  0 
snd_hda_intel          32768  3 
thinkpad_acpi          73728  0 
serio_raw              16384  0 
nvram                  16384  1 thinkpad_acpi
snd_seq_midi           16384  0 
snd_hda_controller     32768  1 snd_hda_intel
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            28672  1 snd_seq_midi
yenta_socket           40960  0 
pcmcia_rsrc            20480  1 yenta_socket
lpc_ich                20480  0 
snd_hda_codec         122880  4 snd_hda_codec_generic,snd_hda_intel,snd_hda_controller,snd_hda_codec_analog
pcmcia_core            24576  3 pcmcia,pcmcia_rsrc,yenta_socket
snd_seq                57344  2 snd_seq_midi_event,snd_seq_midi
snd_hwdep              16384  1 snd_hda_codec
snd_pcm                94208  3 snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
shpchp                 32768  0 
snd_timer              28672  2 snd_pcm,snd_seq
snd                     69632  17  snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device,snd_hda_codec_analog
nsc_ircc               24576  0 
irda                  172032  1 nsc_ircc
soundcore              16384  2 snd,snd_hda_codec
8250_fintek            16384  0 
crc_ccitt              16384  1 irda
mac_hid                16384  0 
parport_pc             32768  0 
ppdev                  20480  0 
lp                     16384  0 
parport                40960  3 lp,ppdev,parport_pc
i915                  925696  3 
psmouse               102400  0 
ahci                   32768  2 
i2c_algo_bit           16384  1 i915
libahci                32768  1 ahci
pata_acpi              16384  0 
e1000e                212992  0 
drm_kms_helper        114688  1 i915
drm                   282624  5 i915,drm_kms_helper
ptp                    20480  1 e1000e
pps_core               20480  1 ptp
video                  20480  1 i915
zorro@zorro-ThinkPad-T60:~$ iwconfig
irda0     no wireless extensions.

lo        no wireless extensions.

eth0      no wireless extensions.
```

---

### Post by Bucky Ball on 2015-10-06
Please use code tags for terminal stuff. See the last link in my signature. I've added them to your last post.

---

### Post by tgalati4 on 2015-10-06
Your wireless card is not showing up.  But you already knew that.  Talk to the previous owner and ask them:  "What happened to the wireless card?"

Time to break out the screw driver.  Take a piece of paper and tape each screw to it's location on the paper.  Do not put a long screw in a short screw hole; you can short out the motherboard.  Because of whitelisting in IBM/Lenovo's BIOS, you can only use the wireless cards in the T60 Link I put in Post #2.  You can find them online.  They are not cheap.

Or get a USB wireless dongle or a PCMCIA wifi card--lots to choose from, but search the forums for Linux compatibility before purchasing.  Some are easier to setup than others.  There are probably a few that will not work at all under Linux.

My theory is that this was a corporate machine that saw a lot of use.  Check the condition and tightness of the hinges.  If the hinges are loose and floppy, then chances are the wireless antennae have worn out, and the helpful IT guy pulled out the wireless card to put in another machine.

---

