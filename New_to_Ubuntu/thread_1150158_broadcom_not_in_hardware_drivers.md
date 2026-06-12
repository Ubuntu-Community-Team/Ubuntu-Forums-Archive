---
title: "broadcom not in hardware drivers"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by mamamia88 on 2009-05-05
anyone know how to get it?

---

### Post by Didius Falco on 2009-05-05
I have no experience with Broadcom, but these threads may help:

[https://help.ubuntu.com/9.04/internet/C/troubleshooting-wireless.html](https://help.ubuntu.com/9.04/internet/C/troubleshooting-wireless.html)

[http://ubuntuforums.org/showthread.php?t=1140063](http://ubuntuforums.org/showthread.php?t=1140063)

[http://ubuntuforums.org/showthread.php?p=7220008](http://ubuntuforums.org/showthread.php?p=7220008)

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

I hope at least one of those helps...

Regards,

 Didius

---

### Post by mamamia88 on 2009-05-05
i just did a reinstall of jaunty and i can't find the driver in hardware drivers.  wireless was working in windows until i restarted and it wasn't working in windows either is there a test to see if the card is even dected?  it was working fine a couple hours ago until i reinstalled after deciding i didn't need windows anymore so deleted it

---

### Post by pastalavista on 2009-05-05
Are you referring to a wireless card? It is there. Make sure the universe and multiverse repositories are enabled in System > Administration > Software Sources. It should update automatically but if not, open Synaptic Package Manager (same menu) and search for Broadcom. My son has a Broadcom card and it uses a driver called fwcutter.. something.

---

### Post by mamamia88 on 2009-05-05
> **pastalavista said:**
> Are you referring to a wireless card? It is there. Make sure the universe and multiverse repositories are enabled in System > Administration > Software Sources. It should update automatically but if not, open Synaptic Package Manager (same menu) and search for Broadcom. My son has a Broadcom card and it uses a driver called fwcutter.. something.

ok ill search synaptic for fwcfutter

---

### Post by rpwdh on 2009-05-05
> **pastalavista said:**
> Are you referring to a wireless card? It is there. Make sure the universe and multiverse repositories are enabled in System > Administration > Software Sources. It should update automatically but if not, open Synaptic Package Manager (same menu) and search for Broadcom. My son has a Broadcom card and it uses a driver called fwcutter.. something.

Also, go to System> Administration> Hardware Drivers. 

When you click on that, it should search for the driver and give you the option to use the Broadcom card. 

At least that's how it worked on my laptop. 

Good luck!

---

### Post by mamamia88 on 2009-05-05
nope i've enabled all repositories and updated but still no driver.  also installed fwcutter nothing anyone know how to test if card died or something before i go banging my head against a wall?

---

### Post by rpwdh on 2009-05-05
> **mamamia88 said:**
> nope i've enabled all repositories and updated but still no driver.  also installed fwcutter nothing anyone know how to test if card died or something before i go banging my head against a wall?

Did you try a hardwire connection to the router? I'm assuming that you're trying to do this over wireless.

---

### Post by mamamia88 on 2009-05-05
yeah i have my laptop hooked up to ehternet now but still no wireless which is what im trying to setup which i've been able to do in all previous versions of ubuntu

---

### Post by rpwdh on 2009-05-05
> **mamamia88 said:**
> yeah i have my laptop hooked up to ehternet now but still no wireless which is what im trying to setup which i've been able to do in all previous versions of ubuntu

I'm at a loss. I updated from Hardy> Ibex> Jaunty an it works fine.

In software sources, I have everything in the first tab checked. 

In the Third Party tab I've checked everything but "unsupported updates" and CD.

Under the Updates tab, I have "Important" & "Recommended" checked with "Install Security Updates without confirmation" checked.

Try that and then check for updates, maybe it will pick something up. 

Sorry I'm not better with the commands in terminal, I'm kinda new myself.


**_[COLOR="Red"]EDIT:[/COLOR]_** Silly question but did you try pressing the wireless button (laptop?) to turn it on? Mine defaulted to off when I did the upgrade.

---

### Post by lkraemer on 2009-05-05
88,
You sure haven't given us much to go on.

Open a Terminal Window, cut & paste each line - one at a time:
```

lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist
iwconfig
dmesg

```
Post the output of the commands in order, and separated so we can
have a look at what you system shows.

If you just need the Broadcom firmware for b43xx it can be found on
the internet.  Are you using b43, b43xx, or ndiswrapper?

Now search through dmesg for any references to Broadcom firmware,
looking for missing firmware or what is causing the Wifi to
not function. There might be a clue. Is the firmware installed
in /lib/firmware or possibly in /lib/firmware/b43 Once again
dmesg might give you a clue. ie. [www.omattos.com/broadcom](www.omattos.com/broadcom)

If lsmod shows module b43 and others installed you will
need to blacklist them, since you are going to be using b43xx.
You may have to remove the following depending on what lsmod
shows:
```

modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb

```
You can use sudo gedit /etc/modprobe.d/blacklist
and add the necessary modules to blacklist.

Once this is all straightened up..........
I'd reboot or try:
```

sudo /etc/init.d/networking restart

```

If you know the routers essid and the correct <interface>,
shown by using iwconfig ie wlan0, ath0, etc.... replace that
as the <interface> below:

```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo iwconfig <interface> essid "youressidofrouter"
sudo iwconfig <interface> mode Managed
sudo ifconfig <interface> up
sudo dhclient <interface>
iwconfig

```
Post the output of iwconfig above.

REF URL:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)
[https://help.ubuntu.com/community/Wi...ative%20Driver](https://help.ubuntu.com/community/Wi...ative%20Driver)

lkraemer

---

### Post by mamamia88 on 2009-05-05
nope not working either it was running fine in beta but then i reinstalled and it's not working .  it wasn't working in windows earlier so im thinking the card may be dead is there a way to check?

---

### Post by rpwdh on 2009-05-05
I'd try what lkraemer is suggesting.

---

### Post by lsmobrian on 2009-05-05
```
sudo apt-get install b43-fwcutter
```

That should do it, automatically grab the firmware and install it, if it doesnt install the firmware right:

Grab b43-fwcutter and install (dont need to download if youre on ethernet and apt-get worked, but I had to transfer using a usb)
[http://packages.ubuntu.com/jaunty/i386/b43-fwcutter/download](http://packages.ubuntu.com/jaunty/i386/b43-fwcutter/download)


download these 2 files
[http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
[http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)

do this as root, or sudo
```
b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
```
```
tar xfvj broadcom-wl-4.150.10.5.tar.bz2
```
```
b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o
```
```
chmod o+rx /lib/firmware/b43 /lib/firmware/b43/legacy
```

I have a broadcom pcmcia card bcm4318, hopefully this can tell you your card, if that will help
```
lspci | grep -i broadcom
```

---

### Post by mamamia88 on 2009-05-05
> **lkraemer said:**
> 88,
You sure haven't given us much to go on.

Open a Terminal Window, cut & paste each line - one at a time:
```

lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist
iwconfig
dmesg

```
Post the output of the commands in order, and separated so we can
have a look at what you system shows.

If you just need the Broadcom firmware for b43xx it can be found on
the internet.  Are you using b43, b43xx, or ndiswrapper?

Now search through dmesg for any references to Broadcom firmware,
looking for missing firmware or what is causing the Wifi to
not function. There might be a clue. Is the firmware installed
in /lib/firmware or possibly in /lib/firmware/b43 Once again
dmesg might give you a clue. ie. [www.omattos.com/broadcom](www.omattos.com/broadcom)

If lsmod shows module b43 and others installed you will
need to blacklist them, since you are going to be using b43xx.
You may have to remove the following depending on what lsmod
shows:
```

modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb

```
You can use sudo gedit /etc/modprobe.d/blacklist
and add the necessary modules to blacklist.

Once this is all straightened up..........
I'd reboot or try:
```

sudo /etc/init.d/networking restart

```

If you know the routers essid and the correct <interface>,
shown by using iwconfig ie wlan0, ath0, etc.... replace that
as the <interface> below:

```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo iwconfig <interface> essid "youressidofrouter"
sudo iwconfig <interface> mode Managed
sudo ifconfig <interface> up
sudo dhclient <interface>
iwconfig

```
Post the output of iwconfig above.

REF URL:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)
[https://help.ubuntu.com/community/Wi...ative%20Driver](https://help.ubuntu.com/community/Wi...ative%20Driver)

lkraemer

lshw -C network

WARNING: you should run this program as super-user.

  *-network DISABLED      

       description: Ethernet interface

       physical id: 1

       logical name: pan0

       serial: fa:0f:53:71:c1:ce

       capabilities: ethernet physical

       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes



Module                  Size  Used by

binfmt_misc            16776  1 

ppdev                  15620  0 

bridge                 56340  0 

stp                    10500  1 bridge

bnep                   20224  2 

input_polldev          11912  0 

lp                     17156  0 

parport                42220  2 ppdev,lp

joydev                 18368  0 

snd_hda_intel         435636  2 

snd_pcm_oss            46336  0 

snd_mixer_oss          22656  1 snd_pcm_oss

snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss

snd_seq_dummy          10756  0 

snd_seq_oss            37760  0 

snd_seq_midi           14336  0 

snd_rawmidi            29696  1 snd_seq_midi

snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi

snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event

snd_timer              29704  2 snd_pcm,snd_seq

snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq

snd                    62628  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

psmouse                61972  0 

ricoh_mmc              11904  0 

k8temp                 12416  0 

pcspkr                 10496  0 

sdhci_pci              15232  0 

sdhci                  23940  1 sdhci_pci

soundcore              15200  1 snd

snd_page_alloc         16904  2 snd_hda_intel,snd_pcm

serio_raw              13316  0 

i2c_nforce2            14980  0 

nvidia               7233756  39 

uvcvideo               63240  0 

compat_ioctl32          9344  1 uvcvideo

videodev               41600  1 uvcvideo

v4l1_compat            21764  2 uvcvideo,videodev

agpgart                42696  1 nvidia

video                  25360  5 

output                 11008  1 video

ohci1394               38576  0 

ieee1394               94660  1 ohci1394

forcedeth              61712  0 

fbcon                  46112  0 

tileblit               10752  1 fbcon

font                   16384  1 fbcon

bitblit                13824  1 fbcon

softcursor              9984  1 bitblit


cat /etc/modprobe.d/blacklist
lo        no wireless extensions.



eth0      no wireless extensions.



pan0      no wireless extensions.



[    0.496416] pci 0000:00:0e.0: reg 24 32bit mmio: [0xb0006000-0xb0006fff]

[    0.496489] pci 0000:00:10.1: reg 10 32bit mmio: [0xb0000000-0xb0003fff]

[    0.496514] pci 0000:00:10.1: PME# supported from D3hot D3cold

[    0.496518] pci 0000:00:10.1: PME# disabled

[    0.496550] pci 0000:00:14.0: reg 10 32bit mmio: [0xb0008000-0xb0008fff]

[    0.496556] pci 0000:00:14.0: reg 14 io port: [0x30e0-0x30e7]

[    0.496575] pci 0000:00:14.0: supports D1 D2

[    0.496577] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold

[    0.496581] pci 0000:00:14.0: PME# disabled

[    0.496695] pci 0000:00:02.0: bridge io port: [0x4000-0x4fff]

[    0.496698] pci 0000:00:02.0: bridge 32bit mmio: [0xb4000000-0xb5ffffff]

[    0.496703] pci 0000:00:02.0: bridge 64bit mmio pref: [0xd0000000-0xd01fffff]

[    0.496743] pci 0000:00:03.0: bridge io port: [0x5000-0x5fff]

[    0.496747] pci 0000:00:03.0: bridge 32bit mmio: [0xb6000000-0xb7ffffff]

[    0.496751] pci 0000:00:03.0: bridge 64bit mmio pref: [0xd0200000-0xd03fffff]

[    0.496784] pci 0000:07:05.0: reg 10 32bit mmio: [0xb8000000-0xb80007ff]

[    0.496814] pci 0000:07:05.0: supports D1 D2

[    0.496816] pci 0000:07:05.0: PME# supported from D0 D1 D2 D3hot D3cold

[    0.496821] pci 0000:07:05.0: PME# disabled

[    0.496847] pci 0000:07:05.1: reg 10 32bit mmio: [0xb8000800-0xb80008ff]

[    0.496877] pci 0000:07:05.1: supports D1 D2

[    0.496880] pci 0000:07:05.1: PME# supported from D0 D1 D2 D3hot D3cold

[    0.496884] pci 0000:07:05.1: PME# disabled

[    0.496911] pci 0000:07:05.2: reg 10 32bit mmio: [0xb8000c00-0xb8000cff]

[    0.496941] pci 0000:07:05.2: supports D1 D2

[    0.496943] pci 0000:07:05.2: PME# supported from D0 D1 D2 D3hot D3cold

[    0.496947] pci 0000:07:05.2: PME# disabled

[    0.496974] pci 0000:07:05.3: reg 10 32bit mmio: [0xb8001000-0xb80010ff]

[    0.497004] pci 0000:07:05.3: supports D1 D2

[    0.497006] pci 0000:07:05.3: PME# supported from D0 D1 D2 D3hot D3cold

[    0.497011] pci 0000:07:05.3: PME# disabled

[    0.497037] pci 0000:07:05.4: reg 10 32bit mmio: [0xb8001400-0xb80014ff]

[    0.497067] pci 0000:07:05.4: supports D1 D2

[    0.497070] pci 0000:07:05.4: PME# supported from D0 D1 D2 D3hot D3cold

[    0.497074] pci 0000:07:05.4: PME# disabled

[    0.497109] pci 0000:00:10.0: transparent bridge

[    0.497114] pci 0000:00:10.0: bridge 32bit mmio: [0xb8000000-0xb80fffff]

[    0.497124] bus 00 -> node 0

[    0.497133] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]

[    0.497266] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]

[    0.497302] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]

[    0.497347] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]

[    0.535686] ACPI: PCI Interrupt Link [LNK1] (IRQs 5) *0, disabled.

[    0.535935] ACPI: PCI Interrupt Link [LNK2] (IRQs 7) *11

[    0.536191] ACPI: PCI Interrupt Link [LNK3] (IRQs 10) *11

[    0.536446] ACPI: PCI Interrupt Link [LNK4] (IRQs 11) *0, disabled.

[    0.536692] ACPI: PCI Interrupt Link [LK1E] (IRQs 16) *0, disabled.

[    0.536937] ACPI: PCI Interrupt Link [LK2E] (IRQs 17) *0, disabled.

[    0.537181] ACPI: PCI Interrupt Link [LK3E] (IRQs 18) *11

[    0.537426] ACPI: PCI Interrupt Link [LK4E] (IRQs 19) *0, disabled.

[    0.537670] ACPI: PCI Interrupt Link [LSMB] (IRQs *10)

[    0.537914] ACPI: PCI Interrupt Link [LPMU] (IRQs 11) *10

[    0.538158] ACPI: PCI Interrupt Link [LUS0] (IRQs 22) *11

[    0.538410] ACPI: PCI Interrupt Link [LUS2] (IRQs 22) *7

[    0.538654] ACPI: PCI Interrupt Link [LMAC] (IRQs 20) *10

[    0.538898] ACPI: PCI Interrupt Link [LAZA] (IRQs 21) *0, disabled.

[    0.539143] ACPI: PCI Interrupt Link [LACI] (IRQs 21) *0, disabled.

[    0.539388] ACPI: PCI Interrupt Link [LMCI] (IRQs 21) *0, disabled.

[    0.539633] ACPI: PCI Interrupt Link [LPID] (IRQs 21) *0, disabled.

[    0.539886] ACPI: PCI Interrupt Link [LTID] (IRQs 23) *5

[    0.540150] ACPI: PCI Interrupt Link [LSI1] (IRQs 20) *10

[    0.540401] ACPI: WMI: Mapper loaded

[    0.544140] SCSI subsystem initialized

[    0.544148] libata version 3.00 loaded.

[    0.544148] usbcore: registered new interface driver usbfs

[    0.544148] usbcore: registered new interface driver hub

[    0.544148] usbcore: registered new device driver usb

[    0.544148] PCI: Using ACPI for IRQ routing

[    0.548017] Bluetooth: Core ver 2.13

[    0.552018] NET: Registered protocol family 31

[    0.552018] Bluetooth: HCI device and connection manager initialized

[    0.552018] Bluetooth: HCI socket layer initialized

[    0.552021] NET: Registered protocol family 8

[    0.552023] NET: Registered protocol family 20

[    0.552035] NetLabel: Initializing

[    0.552037] NetLabel:  domain hash size = 128

[    0.552039] NetLabel:  protocols = UNLABELED CIPSOv4

[    0.552060] NetLabel:  unlabeled traffic allowed by default

[    0.552079] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31

[    0.552085] hpet0: 3 comparators, 32-bit 25.000000 MHz counter

[    0.556096] AppArmor: AppArmor Filesystem Enabled

[    0.564028] Switched to high resolution mode on CPU 0

[    0.564042] Switched to high resolution mode on CPU 1

[    0.564061] pnp: PnP ACPI init

[    0.564077] ACPI: bus type pnp registered

[    0.567922] pnp: PnP ACPI: found 13 devices

[    0.567925] ACPI: ACPI bus type pnp unregistered

[    0.567929] PnPBIOS: Disabled by ACPI PNP

[    0.567941] system 00:00: iomem range 0xe0000000-0xefffffff has been reserved

[    0.567948] system 00:01: iomem range 0xffc00000-0xffffffff could not be reserved

[    0.567952] system 00:01: iomem range 0xfec00000-0xfec00fff has been reserved

[    0.567955] system 00:01: iomem range 0xfee00000-0xfeefffff could not be reserved

[    0.567959] system 00:01: iomem range 0xfed00000-0xfed00fff has been reserved

[    0.567966] system 00:03: iomem range 0xe0000000-0xefffffff has been reserved

[    0.567973] system 00:04: ioport range 0x1000-0x107f has been reserved

[    0.567976] system 00:04: ioport range 0x1080-0x10ff has been reserved

[    0.567979] system 00:04: ioport range 0x1400-0x147f has been reserved

[    0.567982] system 00:04: ioport range 0x1480-0x14ff has been reserved

[    0.567985] system 00:04: ioport range 0x1800-0x187f has been reserved

[    0.567989] system 00:04: ioport range 0x1880-0x18ff has been reserved

[    0.567992] system 00:04: ioport range 0x2000-0x203f has been reserved

[    0.568005] system 00:05: ioport range 0x360-0x361 has been reserved

[    0.568008] system 00:05: ioport range 0x380-0x383 has been reserved

[    0.568011] system 00:05: ioport range 0x4d0-0x4d1 has been reserved

[    0.602769] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01

[    0.602772] pci 0000:00:02.0:   IO window: 0x4000-0x4fff

[    0.602776] pci 0000:00:02.0:   MEM window: 0xb4000000-0xb5ffffff

[    0.602780] pci 0000:00:02.0:   PREFETCH window: 0x000000d0000000-0x000000d01fffff

[    0.602784] pci 0000:00:03.0: PCI bridge, secondary bus 0000:03

[    0.602787] pci 0000:00:03.0:   IO window: 0x5000-0x5fff

[    0.602791] pci 0000:00:03.0:   MEM window: 0xb6000000-0xb7ffffff

[    0.602794] pci 0000:00:03.0:   PREFETCH window: 0x000000d0200000-0x000000d03fffff

[    0.602799] pci 0000:00:10.0: PCI bridge, secondary bus 0000:07

[    0.602801] pci 0000:00:10.0:   IO window: disabled

[    0.602805] pci 0000:00:10.0:   MEM window: 0xb8000000-0xb80fffff

[    0.602809] pci 0000:00:10.0:   PREFETCH window: disabled

[    0.602820] pci 0000:00:02.0: setting latency timer to 64

[    0.602825] pci 0000:00:03.0: setting latency timer to 64

[    0.602830] pci 0000:00:10.0: setting latency timer to 64

[    0.602834] bus: 00 index 0 io port: [0x00-0xffff]

[    0.602837] bus: 00 index 1 mmio: [0x000000-0xffffffff]

[    0.602840] bus: 01 index 0 io port: [0x4000-0x4fff]

[    0.602842] bus: 01 index 1 mmio: [0xb4000000-0xb5ffffff]

[    0.602845] bus: 01 index 2 mmio: [0xd0000000-0xd01fffff]

[    0.602848] bus: 01 index 3 mmio: [0x0-0x0]

[    0.602850] bus: 03 index 0 io port: [0x5000-0x5fff]

[    0.602852] bus: 03 index 1 mmio: [0xb6000000-0xb7ffffff]

[    0.602855] bus: 03 index 2 mmio: [0xd0200000-0xd03fffff]

[    0.602857] bus: 03 index 3 mmio: [0x0-0x0]

[    0.602859] bus: 07 index 0 mmio: [0x0-0x0]

[    0.602861] bus: 07 index 1 mmio: [0xb8000000-0xb80fffff]

[    0.602864] bus: 07 index 2 mmio: [0x0-0x0]

[    0.602866] bus: 07 index 3 io port: [0x00-0xffff]

[    0.602868] bus: 07 index 4 mmio: [0x000000-0xffffffff]

[    0.602884] NET: Registered protocol family 2

[    0.613109] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)

[    0.613441] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)

[    0.614267] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)

[    0.614701] TCP: Hash tables configured (established 131072 bind 65536)

[    0.614704] TCP reno registered

[    0.617143] NET: Registered protocol family 1

[    0.617291] checking if image is initramfs... it is

[    1.295110] Freeing initrd memory: 7352k freed

[    1.295151] Simple Boot Flag at 0x36 set to 0x1

[    1.295361] cpufreq: No nForce2 chipset.

[    1.295511] audit: initializing netlink socket (disabled)

[    1.295529] type=2000 audit(1241573863.292:1): initialized

[    1.304837] highmem bounce pool size: 64 pages

[    1.304844] HugeTLB registered 4 MB page size, pre-allocated 0 pages

[    1.306345] VFS: Disk quotas dquot_6.5.1

[    1.306413] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)

[    1.307099] fuse init (API version 7.10)

[    1.307184] msgmni has been set to 1701

[    1.307427] alg: No test for stdrng (krng)

[    1.307443] io scheduler noop registered

[    1.307445] io scheduler anticipatory registered

[    1.307448] io scheduler deadline registered

[    1.307466] io scheduler cfq registered (default)

[    1.307484] pci 0000:00:00.0: Enabling HT MSI Mapping

[    1.307528] pci 0000:00:02.0: Enabling HT MSI Mapping

[    1.307540] pci 0000:00:03.0: Enabling HT MSI Mapping

[    1.307550] pci 0000:00:05.0: Boot video device

[    1.307573] pci 0000:00:09.0: Enabling HT MSI Mapping

[    1.524101] pci 0000:00:0e.0: Enabling HT MSI Mapping

[    1.524113] pci 0000:00:10.0: Enabling HT MSI Mapping

[    1.524126] pci 0000:00:10.1: Enabling HT MSI Mapping

[    1.529362] pcieport-driver 0000:00:02.0: setting latency timer to 64

[    1.529390] pcieport-driver 0000:00:02.0: found MSI capability

[    1.529409] pcieport-driver 0000:00:02.0: irq 2303 for MSI/MSI-X

[    1.529416] pci_express 0000:00:02.0:pcie00: allocate port service

[    1.529435] pci_express 0000:00:02.0:pcie03: allocate port service

[    1.529475] pcieport-driver 0000:00:03.0: setting latency timer to 64

[    1.529499] pcieport-driver 0000:00:03.0: found MSI capability

[    1.529513] pcieport-driver 0000:00:03.0: irq 2302 for MSI/MSI-X

[    1.529520] pci_express 0000:00:03.0:pcie00: allocate port service

[    1.529537] pci_express 0000:00:03.0:pcie03: allocate port service

[    1.529592] pci_hotplug: PCI Hot Plug PCI Core version: 0.5

[    1.529605] pciehp: PCI Express Hot Plug Controller Driver version: 0.4

[    1.530955] ACPI: AC Adapter [ACAD] (off-line)

[    1.801338] ACPI: Battery Slot [BAT0] (battery present)

[    1.801447] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0

[    1.801451] ACPI: Power Button (FF) [PWRF]

[    1.801503] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1

[    1.801506] ACPI: Power Button (CM) [PWRB]

[    1.801557] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2

[    1.801560] ACPI: Sleep Button (CM) [SLPB]

[    1.801608] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3

[    1.802349] ACPI: Lid Switch [LID]

[    1.802671] ACPI: processor limited to max C-state 1

[    1.802697] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])

[    1.802726] processor ACPI_CPU:00: registered as cooling_device0

[    1.802762] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])

[    1.802782] processor ACPI_CPU:01: registered as cooling_device1

[    2.062523] thermal LNXTHERM:01: registered as thermal_zone0

[    2.064698] ACPI: Thermal Zone [THRM] (50 C)

[    2.064764] isapnp: Scanning for PnP cards...

[    2.417573] isapnp: No Plug & Play device found

[    2.429380] Serial: 8250/16550 driver4 ports, IRQ sharing enabled

[    2.430470] brd: module loaded

[    2.430817] loop: module loaded

[    2.430907] Fixed MDIO Bus: probed

[    2.430914] PPP generic driver version 2.4.2

[    2.430989] input: Macintosh mouse button emulation as /devices/virtual/input/input4

[    2.431033] Driver 'sd' needs updating - please use bus_type methods

[    2.431042] Driver 'sr' needs updating - please use bus_type methods

[    2.431285] sata_nv 0000:00:0e.0: version 3.5

[    2.431299] sata_nv 0000:00:0e.0: enabling device (0005 -> 0007)

[    2.431724] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 23

[    2.431739] sata_nv 0000:00:0e.0: PCI INT A -> Link[LTID] -> GSI 23 (level, high) -> IRQ 23

[    2.431743] sata_nv 0000:00:0e.0: Using SWNCQ mode

[    2.431827] sata_nv 0000:00:0e.0: setting latency timer to 64

[    2.432031] scsi0 : sata_nv

[    2.432174] scsi1 : sata_nv

[    2.432360] ata1: SATA max UDMA/133 cmd 0x30c0 ctl 0x30b4 bmdma 0x3090 irq 23

[    2.432364] ata2: SATA max UDMA/133 cmd 0x30b8 ctl 0x30b0 bmdma 0x3098 irq 23

[    3.308087] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)

[    3.316239] ata1.00: ATA-7: ST9120822AS, 3.BHD, max UDMA/100

[    3.316242] ata1.00: 234441648 sectors, multi 16: LBA48 

[    3.332260] ata1.00: configured for UDMA/100

[    4.066610] ata2: SATA link down (SStatus 0 SControl 300)

[    4.066749] scsi 0:0:0:0: Direct-Access     ATA      ST9120822AS      3.BH PQ: 0 ANSI: 5

[    4.066874] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors: (120 GB/111 GiB)

[    4.066894] sd 0:0:0:0: [sda] Write Protect is off

[    4.066896] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00

[    4.066925] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

[    4.067006] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors: (120 GB/111 GiB)

[    4.067022] sd 0:0:0:0: [sda] Write Protect is off

[    4.067025] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00

[    4.067051] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

[    4.067056]  sda: sda1 sda2 sda3 sda4

[    4.105116] sd 0:0:0:0: [sda] Attached SCSI disk

[    4.105183] sd 0:0:0:0: Attached scsi generic sg0 type 0

[    4.105306] pata_amd 0000:00:0d.0: version 0.3.10

[    4.105360] pata_amd 0000:00:0d.0: setting latency timer to 64

[    4.105463] scsi2 : pata_amd

[    4.105566] scsi3 : pata_amd

[    4.106325] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x3080 irq 14

[    4.106328] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x3088 irq 15

[    4.284353] ata3.00: ATAPI: TSSTcorpCD/DVDW TS-L632D, HH17, max MWDMA2

[    4.284381] ata3: nv_mode_filter: 0x39f&0x39f->0x39f, BIOS=0x0 (0xc600) ACPI=0x39f (120:600:0x12)

[    4.316301] ata3.00: configured for MWDMA2

[    4.316833] ata4: port disabled. ignoring.

[    4.332433] scsi 2:0:0:0: CD-ROM            TSSTcorp CD/DVDW TS-L632D HH17 PQ: 0 ANSI: 5

[    4.388268] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray

[    4.388272] Uniform CD-ROM driver Revision: 3.20

[    4.388404] sr 2:0:0:0: Attached scsi CD-ROM sr0

[    4.388461] sr 2:0:0:0: Attached scsi generic sg1 type 5

[    4.389081] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver

[    4.389520] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22

[    4.389533] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[LUS2] -> GSI 22 (level, high) -> IRQ 22

[    4.389558] ehci_hcd 0000:00:0b.1: setting latency timer to 64

[    4.389562] ehci_hcd 0000:00:0b.1: EHCI Host Controller

[    4.389629] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1

[    4.389665] ehci_hcd 0000:00:0b.1: debug port 1

[    4.389670] ehci_hcd 0000:00:0b.1: cache line size of 64 is not supported

[    4.389695] ehci_hcd 0000:00:0b.1: irq 22, io mem 0xb0005000

[    4.400057] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00

[    4.400142] usb usb1: configuration #1 chosen from 1 choice

[    4.400178] hub 1-0:1.0: USB hub found

[    4.400188] hub 1-0:1.0: 8 ports detected

[    4.400325] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver

[    4.400737] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 22

[    4.400742] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[LUS0] -> GSI 22 (level, high) -> IRQ 22

[    4.400762] ohci_hcd 0000:00:0b.0: setting latency timer to 64

[    4.400766] ohci_hcd 0000:00:0b.0: OHCI Host Controller

[    4.400827] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2

[    4.400846] ohci_hcd 0000:00:0b.0: irq 22, io mem 0xb0004000

[    4.458121] usb usb2: configuration #1 chosen from 1 choice

[    4.458150] hub 2-0:1.0: USB hub found

[    4.458165] hub 2-0:1.0: 8 ports detected

[    4.458284] uhci_hcd: USB Universal Host Controller Interface driver

[    4.458364] usbcore: registered new interface driver libusual

[    4.458401] usbcore: registered new interface driver usbserial

[    4.458414] USB Serial support registered for generic

[    4.458432] usbcore: registered new interface driver usbserial_generic

[    4.458435] usbserial: USB Serial Driver core

[    4.458487] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12

[    4.476190] serio: i8042 KBD port at 0x60,0x64 irq 1

[    4.476199] serio: i8042 AUX port at 0x60,0x64 irq 12

[    4.477078] mice: PS/2 mouse device common for all mice

[    4.497119] rtc_cmos 00:09: RTC can wake from S4

[    4.497161] rtc_cmos 00:09: rtc core: registered rtc_cmos as rtc0

[    4.497200] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs

[    4.497273] device-mapper: uevent: version 1.0.3

[    4.497393] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]

[    4.497563] device-mapper: multipath: version 1.0.5 loaded

[    4.497566] device-mapper: multipath round-robin: version 1.0.0 loaded

[    4.497696] EISA: Probing bus 0 at eisa.0

[    4.497703] Cannot allocate resource for EISA slot 1

[    4.497706] Cannot allocate resource for EISA slot 2

[    4.497709] Cannot allocate resource for EISA slot 3

[    4.497712] Cannot allocate resource for EISA slot 4

[    4.497714] Cannot allocate resource for EISA slot 5

[    4.497725] EISA: Detected 0 cards.

[    4.497874] cpuidle: using governor ladder

[    4.497944] cpuidle: using governor menu

[    4.498507] TCP cubic registered

[    4.498620] NET: Registered protocol family 10

[    4.499084] lo: Disabled Privacy Extensions

[    4.499458] NET: Registered protocol family 17

[    4.499480] Bluetooth: L2CAP ver 2.11

[    4.499482] Bluetooth: L2CAP socket layer initialized

[    4.499485] Bluetooth: SCO (Voice Link) ver 0.6

[    4.499487] Bluetooth: SCO socket layer initialized

[    4.499552] Bluetooth: RFCOMM socket layer initialized

[    4.499560] Bluetooth: RFCOMM TTY layer initialized

[    4.499562] Bluetooth: RFCOMM ver 1.10

[    4.499632] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual-Core Processor TK-53 processors (2 cpu cores) (version 2.20.00)

[    4.499692] powernow-k8:    0 : fid 0x9 (1700 MHz), vid 0x13

[    4.499696] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x14

[    4.499699] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x1a

[    4.499762] Using IPI No-Shortcut mode

[    4.499866] registered taskstats version 1

[    4.500072]   Magic number: 9:127:609

[    4.500193] rtc_cmos 00:09: setting system clock to 2009-05-06 01:37:47 UTC (1241573867)

[    4.500197] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found

[    4.500199] EDD information not available.

[    4.500649] Freeing unused kernel memory: 532k freed

[    4.500827] Write protecting the kernel text: 4128k

[    4.500888] Write protecting the kernel read-only data: 1532k

[    4.509316] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5

[    4.727476] usb 1-4: new high speed USB device using ehci_hcd and address 2

[    5.058941] usb 1-4: configuration #1 chosen from 1 choice

[    5.137389] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.

[    5.137841] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20

[    5.137856] forcedeth 0000:00:14.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, high) -> IRQ 20

[    5.137862] forcedeth 0000:00:14.0: setting latency timer to 64

[    5.137946] nv_probe: set workaround bit for reversed mac addr

[    5.155989] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 5

[    5.156041] ohci1394 0000:07:05.0: PCI INT A -> Link[LNK1] -> GSI 5 (level, high) -> IRQ 5

[    5.207834] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[5]  MMIO=[b8000000-b80007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]

[    5.425158] usb 2-6: new low speed USB device using ohci_hcd and address 2

[    5.672847] usb 2-6: device descriptor read/64, error -62

[    5.801847] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1b:24:66:25:07

[    5.801852] forcedeth 0000:00:14.0: highdma pwrctl timirq lnktim desc-v3

[    6.041032] usb 2-6: device descriptor read/64, error -62

[    6.159410] PM: Starting manual resume from disk

[    6.159415] PM: Resume from partition 8:2

[    6.159418] PM: Checking hibernation image.

[    6.159625] PM: Resume from disk failed.

[    6.192155] EXT4-fs: barriers enabled

[    6.209446] kjournald2 starting.  Commit interval 5 seconds

[    6.209479] EXT4-fs: delayed allocation enabled

[    6.209481] EXT4-fs: file extents enabled

[    6.221516] EXT4-fs: mballoc enabled

[    6.221523] EXT4-fs: mounted filesystem with ordered data mode.

[    6.330497] usb 2-6: new low speed USB device using ohci_hcd and address 3

[    6.504837] usb 2-6: device descriptor read/64, error -62

[    6.514002] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b004dbc3200]

[    6.799890] usb 2-6: device descriptor read/64, error -62

[    7.081173] usb 2-6: new low speed USB device using ohci_hcd and address 4

[    7.494994] usb 2-6: device not accepting address 4, error -62

[    7.666591] usb 2-6: new low speed USB device using ohci_hcd and address 5

[    8.097478] usb 2-6: device not accepting address 5, error -62

[    8.097493] hub 2-0:1.0: unable to enumerate USB device on port 6

[   11.623304] udev: starting version 141

[   11.976262] acpi device:24: registered as cooling_device2

[   11.976584] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:22/input/input6

[   12.009203] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)

[   12.050469] Linux agpgart interface v0.103

[   12.131302] Linux video capture interface: v2.00

[   12.162904] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:62c0)

[   12.164043] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:0b.1/usb1/1-4/1-4:1.0/input/input7

[   12.176228] usbcore: registered new interface driver uvcvideo

[   12.176259] USB Video Class driver (v0.1.0)

[   12.947763] nvidia: module license 'NVIDIA' taints kernel.

[   12.994742] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x3040

[   12.994788] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x3000

[   13.072846] sdhci: Secure Digital Host Controller Interface driver

[   13.072851] sdhci: Copyright(c) Pierre Ossman

[   13.082893] sdhci-pci 0000:07:05.1: SDHCI controller found [1180:0822] (rev 19)

[   13.083314] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 7

[   13.083329] sdhci-pci 0000:07:05.1: PCI INT B -> Link[LNK2] -> GSI 7 (level, high) -> IRQ 7

[   13.086658] mmc0: SDHCI controller on PCI [0000:07:05.1] using PIO

[   13.092975] input: PC Speaker as /devices/platform/pcspkr/input/input8

[   13.203401] nvidia 0000:00:05.0: power state changed by ACPI to D0

[   13.203802] ACPI: PCI Interrupt Link [LK3E] enabled at IRQ 18

[   13.203816] nvidia 0000:00:05.0: PCI INT A -> Link[LK3E] -> GSI 18 (level, high) -> IRQ 18

[   13.203825] nvidia 0000:00:05.0: setting latency timer to 64

[   13.204592] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009

[   13.378705] ricoh-mmc: Ricoh MMC Controller disabling driver

[   13.378709] ricoh-mmc: Copyright(c) Philip Langdale

[   13.378753] ricoh-mmc: Ricoh MMC controller found at 0000:07:05.2 [1180:0843] (rev 1)

[   13.378770] ricoh-mmc: Controller is now disabled.

[   13.558341] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume

[   13.662806] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21

[   13.662822] HDA Intel 0000:00:10.1: PCI INT B -> Link[LAZA] -> GSI 21 (level, high) -> IRQ 21

[   13.662921] HDA Intel 0000:00:10.1: setting latency timer to 64

[   14.535445] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000

[   14.601236] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9

[   14.720389] lp: driver loaded but no devices found

[   14.822618] Adding 2618584k swap on /dev/sda2.  Priority:-1 extents:1 across:2618584k

[   14.847722] EXT4 FS on sda1, internal journal on sda1:8

[   15.168450] EXT4-fs: barriers enabled

[   15.180280] kjournald2 starting.  Commit interval 5 seconds

[   15.180460] EXT4 FS on sda3, internal journal on sda3:8

[   15.180463] EXT4-fs: delayed allocation enabled

[   15.180465] EXT4-fs: file extents enabled

[   15.182826] EXT4-fs: mballoc enabled

[   15.182832] EXT4-fs: mounted filesystem with ordered data mode.

[   15.478208] type=1505 audit(1241573878.475:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2032

[   15.543357] type=1505 audit(1241573878.540:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2036

[   15.543540] type=1505 audit(1241573878.540:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2036

[   15.543601] type=1505 audit(1241573878.540:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2036

[   15.543654] type=1505 audit(1241573878.540:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2036

[   15.728389] type=1505 audit(1241573878.724:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2041

[   15.728628] type=1505 audit(1241573878.724:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2041

[   15.766682] type=1505 audit(1241573878.764:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2045

[   19.268445] Bluetooth: BNEP (Ethernet Emulation) ver 1.3

[   19.268449] Bluetooth: BNEP filters: protocol multicast

[   19.316403] Bridge firewalling registered

[   19.629192] usb 2-6: new low speed USB device using ohci_hcd and address 6

[   19.877173] usb 2-6: device descriptor read/64, error -62

[   20.164455] usb 2-6: device descriptor read/64, error -62

[   20.454287] usb 2-6: new low speed USB device using ohci_hcd and address 7

[   20.721575] usb 2-6: device descriptor read/64, error -62

[   21.013905] usb 2-6: device descriptor read/64, error -62

[   21.145220] ppdev: user-space parallel port driver

[   21.308444] usb 2-6: new low speed USB device using ohci_hcd and address 8

[   21.726030] usb 2-6: device not accepting address 8, error -62

[   21.903688] usb 2-6: new low speed USB device using ohci_hcd and address 9

[   22.320030] usb 2-6: device not accepting address 9, error -62

[   22.320051] hub 2-0:1.0: unable to enumerate USB device on port 6

[   35.516017] eth0: no IPv6 routers present

[   72.069039] usb 2-6: new low speed USB device using ohci_hcd and address 10

[   72.253762] usb 2-6: device descriptor read/64, error -62

[   72.541057] usb 2-6: device descriptor read/64, error -62

[   72.820403] usb 2-6: new low speed USB device using ohci_hcd and address 11

[   73.005050] usb 2-6: device descriptor read/64, error -62

[   73.289210] usb 2-6: device descriptor read/64, error -62

[   73.561053] usb 2-6: new low speed USB device using ohci_hcd and address 12

[   73.973033] usb 2-6: device not accepting address 12, error -62

[   74.153039] usb 2-6: new low speed USB device using ohci_hcd and address 13

[   74.561427] usb 2-6: device not accepting address 13, error -62

[   74.561451] hub 2-0:1.0: unable to enumerate USB device on port 6

[   83.500030] Clocksource tsc unstable (delta = -95860084 ns)

[ 1251.281056] usb 2-6: new low speed USB device using ohci_hcd and address 14

[ 1251.464049] usb 2-6: device descriptor read/64, error -62

[ 1251.748059] usb 2-6: device descriptor read/64, error -62

[ 1252.029047] usb 2-6: new low speed USB device using ohci_hcd and address 15

[ 1252.212128] usb 2-6: device descriptor read/64, error -62

[ 1252.501065] usb 2-6: device descriptor read/64, error -62

[ 1252.781069] usb 2-6: new low speed USB device using ohci_hcd and address 16

[ 1253.188056] usb 2-6: device not accepting address 16, error -62

[ 1253.365057] usb 2-6: new low speed USB device using ohci_hcd and address 17

[ 1253.773046] usb 2-6: device not accepting address 17, error -62

[ 1253.773089] hub 2-0:1.0: unable to enumerate USB device on port 6

[ 2070.808039] usb 2-6: new low speed USB device using ohci_hcd and address 18

[ 2070.993085] usb 2-6: device descriptor read/64, error -62

[ 2071.281064] usb 2-6: device descriptor read/64, error -62

[ 2071.561037] usb 2-6: new low speed USB device using ohci_hcd and address 19

[ 2071.744074] usb 2-6: device descriptor read/64, error -62

[ 2072.032058] usb 2-6: device descriptor read/64, error -62

[ 2072.313133] usb 2-6: new low speed USB device using ohci_hcd and address 20

[ 2072.721060] usb 2-6: device not accepting address 20, error -62

[ 2072.896075] usb 2-6: new low speed USB device using ohci_hcd and address 21

[ 2073.304047] usb 2-6: device not accepting address 21, error -62

[ 2073.304095] hub 2-0:1.0: unable to enumerate USB device on port 6

sportscrazed2@sportscrazed2-laptop:~$

---

### Post by lkraemer on 2009-05-05
88,
Unless I missed something, I don't see any references to Wifi
(Broadcom, Atheros, Intel, etc) in ndiswrapper, lsmod, dmesg,
iwconfig, etc..

Is it possible to boot it in Windows and double check that it at
least works in Windows?  What about moving the card to another 
PCI slot, if possible, and see if it works in Windows then.  
Also double check that if it is a Laptop, that the Wifi is
turned on, or Enabled if done by keystrokes or a hardware switch.

We must be missing something, unless your Wifi card has died......

lkraemer

---

