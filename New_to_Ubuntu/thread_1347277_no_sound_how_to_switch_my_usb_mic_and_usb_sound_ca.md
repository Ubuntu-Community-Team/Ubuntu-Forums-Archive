---
title: "no sound: how to switch my usb mic and usb sound card?"
date: 2009-12-06
forum: New to Ubuntu
---

### Post by frenchn00b on 2009-12-06
# aplay /usr/share/sounds/pop.wav 
```
ALSA lib pcm_dmix.c:996:(snd_pcm_dmix_open) unable to open slave
aplay: main:564: audio open error: No such file or directory
```

>  cat /proc/asound/cards
 0 [default        ]: USB-Audio - AK5370          
                      AKM              AK5370           at usb-0000:00:02.1-1, full speed
 1 [default_1      ]: USB-Audio - PnP Audio Device        
                      PnP Audio Device         at usb-0000:00:02.1-4, full speed




$ arecord -L
```
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=default_1
    PnP Audio Device        , USB Audio
    Default Audio Device
front:CARD=default_1,DEV=0
    PnP Audio Device        , USB Audio
    Front speakers
surround40:CARD=default_1,DEV=0
    PnP Audio Device        , USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=default_1,DEV=0
    PnP Audio Device        , USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=default_1,DEV=0
    PnP Audio Device        , USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=default_1,DEV=0
    PnP Audio Device        , USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=default_1,DEV=0
    PnP Audio Device        , USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=default_1,DEV=0
    PnP Audio Device        , USB Audio
    IEC958 (S/PDIF) Digital Audio Output
```

[/CODE]

my dmesg indicates:
```
 4.289035] usb 3-2: New USB device found, idVendor=0556, idProduct=0001
[    4.289038] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    4.289041] usb 3-2: Product: AK5370          
[    4.289042] usb 3-2: Manufacturer: AKM             
[    4.289109] usb 3-2: configuration #1 chosen from 1 choice
[    4.596032] usb 3-4: new full speed USB device using ohci_hcd and address 3
[    4.596072] hdc: host max PIO5 wanted PIO255(auto-tune) selected PIO4
[    4.596171] hdc: UDMA/66 mode selected
[    4.596304] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    4.611027] ide1 at 0x170-0x177,0x376 on irq 15
[    4.611331] sata_nv 0000:00:0a.0: version 3.5
[    4.611601] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 21
[    4.611605] sata_nv 0000:00:0a.0: PCI INT A -> Link[LTID] -> GSI 21 (level, low) -> IRQ 21
[    4.611634] sata_nv 0000:00:0a.0: setting latency timer to 64
[    4.611677] scsi0 : sata_nv
[    4.611751] scsi1 : sata_nv
[    4.612194] ata1: SATA max UDMA/133 cmd 0xf80 ctl 0xf00 bmdma 0xe000 irq 21
[    4.612197] ata2: SATA max UDMA/133 cmd 0xe80 ctl 0xe00 bmdma 0xe008 irq 21
[    4.806034] usb 3-4: New USB device found, idVendor=0d8c, idProduct=0201
[    4.806038] usb 3-4: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[    4.806040] usb 3-4: Product: PnP Audio Device        
[    4.806107] usb 3-4: configuration #1 chosen from 1 choice
[    5.254944] ide-gd driver 1.18
[    5.254972] hda: max request size: 512KiB
[    5.258359] ide-cd driver 5.00
[    5.258369] hda: 234441648 sectors (120034 MB) w/8192KiB Cache, CHS=16383/255/63
[    5.258762] hda: cache flushes supported
[    5.258801]  hda: hda1 hda2 < hda5 hda6 hda7 > hda3
[    5.334957] ide-cd: hdc: ATAPI 48X DVD-ROM DVD-R/RAM CD-R/RW drive, 2048kB Cache
[    5.334964] Uniform CD-ROM driver Revision: 3.20
[    5.981592] PM: Starting manual resume from disk
[    6.038889] kjournald starting.  Commit interval 5 seconds
[    6.038902] EXT3-fs: mounted filesystem with ordered data mode.
[    7.500906] udevd version 125 started
[    7.815041] Linux agpgart interface v0.103
[    7.817365] agpgart-amd64 0000:00:00.0: AGP bridge [10de/00e1]
[    7.817390] agpgart-amd64 0000:00:00.0: aperture size 4096 MB is not right, using settings from NB
[    7.817394] agpgart-amd64 0000:00:00.0: setting up Nforce3 AGP
[    7.833006] agpgart-amd64 0000:00:00.0: AGP aperture is 512M @ 0xc0000000
[    7.945067] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x5000
[    7.945081] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x5040
[    8.052716] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    8.052723] ACPI: Power Button [PWRF]
[    8.052793] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[    8.052796] ACPI: Power Button [PWRB]
[    8.097668] processor ACPI_CPU:00: registered as cooling_device0
[    8.097699] processor ACPI_CPU:01: registered as cooling_device1
[    8.382280] input: USB Optical Mouse USB Optical Mouse as /devices/pci0000:00/0000:00:02.0/usb1/1-1/1-1:1.0/input/input4
[    8.382328] a4tech 0003:09DA:0006.0001: input,hidraw2: USB HID v1.10 Mouse [USB Optical Mouse USB Optical Mouse] on usb-0000:00:02.0-1/input0
[    8.575155] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    8.588074] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    8.736034] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[    8.793015] input: PC Speaker as /devices/platform/pcspkr/input/input5
[    9.474067] Linux video capture interface: v2.00
[    9.565013] bttv: driver version 0.9.18 loaded
[    9.565017] bttv: using 8 buffers with 2080k (520 pages) each for capture
[    9.565052] bttv: Bt8xx card found (0).
[    9.565299] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 19
[    9.565309] bttv 0000:02:09.0: PCI INT A -> Link[LNKB] -> GSI 19 (level, low) -> IRQ 19
[    9.565318] bttv0: Bt878 (rev 2) at 0000:02:09.0, irq: 19, latency: 32, mmio: 0xfbffe000
[    9.565342] bttv0: detected: FlyVideo 98 (LR50)/ Chronos Video Shuttle II [card=35], PCI subsystem ID is 1851:1850
[    9.565345] bttv0: using: Lifeview FlyVideo 98 LR50 / Chronos Video Shuttle II [card=35,autodetected]
[    9.565348] IRQ 19/bttv0: IRQF_DISABLED is not guaranteed on shared IRQs
[    9.565381] bttv0: gpio: en=00000000, out=00000000 in=008dff00 [init]
[    9.565427] bttv0: FlyVideo_gpio: unknown tuner type.
[    9.565430] bttv0: FlyVideo Radio=no  RemoteControl=yes Tuner=-1 gpio=0x8dff00
[    9.565432] bttv0: FlyVideo  LR90=no  tda9821/tda9820=no  capture_only=no 
[    9.565435] bttv0: tuner type unset
[    9.565468] bttv0: registered device video0
[    9.565487] bttv0: registered device vbi0

```

# lsmod | grep snd
```
snd_usb_audio          72008  1 
snd_pcm_oss            32232  0 
snd_mixer_oss          12368  1 snd_pcm_oss
snd_pcm                62364  2 snd_usb_audio,snd_pcm_oss
snd_page_alloc          8180  1 snd_pcm
snd_usb_lib            13508  1 snd_usb_audio
snd_hwdep               6104  1 snd_usb_audio
snd_seq_midi            5688  0 
snd_rawmidi            18580  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      6212  1 snd_seq_midi
snd_seq                42436  2 snd_seq_midi,snd_seq_midi_event
snd_timer              17436  2 snd_pcm,snd_seq
snd_seq_device          6136  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    49040  11 snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6184  1 snd
usbcore               125872  6 snd_usb_audio,snd_usb_lib,usbhid,ehci_hcd,ohci_hcd


```

I would like to exchange the usb microphone to the sound card.
USB microphone would be second place, since it is a mic only.
first main sound would come from usb sound card system. 

then would get sounds


>   ALSA  has  a  special built&#8208;in module autoloading system.  You do
not have to make use of it, and it is useless if your /dev direc&#8208;
tory  is managed by udev, but in case you do want to use it, here
is a brief explanation of how it is supposed to work.

When the "snd" module is loaded and the  user  tries  to  open  a
sound  device  file  with a minor number that indicates that card
number N is wanted, snd modprobes "snd&#8208;card&#8208;N".  Thus, if you set
up module loader configuration file /etc/modprobe.d/sound to look
like this:

    alias snd&#8208;card&#8208;0 snd&#8208;cs46xx
    options snd&#8208;cs46xx index=0

then snd&#8208;cs46xx will be automagically loaded when it is needed to
handle  the  attempted open() of the sound device.  The "index=0"
option ensures that when snd&#8208;cs46xx is loaded the first card that
it registers is given index 0.

If  you  have an additional sound card of the same type then make
the file look like this:

    alias snd&#8208;card&#8208;0    snd&#8208;cs46xx
    alias snd&#8208;card&#8208;1    snd&#8208;cs46xx
    options snd&#8208;cs46xx  index=0,1

If you have, instead, an additional sound  card  of  a  different
type then make the file look like this:

    alias snd&#8208;card&#8208;0    snd&#8208;cs46xx
    options snd&#8208;cs46xx  index=0
    alias snd&#8208;card&#8208;1    snd&#8208;emu10k1
    options snd&#8208;emu10k1 index=1

ALSA supports up to eight sound cards.

The alsaconf program, available in the alsa&#8208;utils package (in De&#8208;
bian but not in Ubuntu),  performs  hardware  detection  and  can
write  out a module loader configuration file that looks like the
above.

Unfortunately, alsaconf can only detect one  sound  card  and  is
generally a poorly written program.

The  module  loader  configuration files just described are addi&#8208;
tional to /etc/modprobe.d/alsa&#8208;base which is shipped as  conffile
with  the  alsa&#8208;base package.  The files contain basic configura&#8208;
tion entries which don&#8217;t normally need to be customized.  The en&#8208;
tries may include:

*  ALSA  autoloader aliases * an entry for each normal sound card
driver that will cause a command
  to be executed after the driver has initialized * an entry  for
each abnormal driver (i.e., a driver that drives
  hardware  such  as  a TV card or modem that is not suited to be
the
  primary sound card) preventing it from grabbing index 0

Suppose you decide that you need to load a certain  driver,  snd&#8208;
foo,  with  options: "dma1=0 ctlport=0x530".  The recommended way
to set this up is to create additional files in  /etc/modprobe.d/
each containing an "options" line:

    # /etc/modprobe.d/alsa_local
    options snd&#8208;foo dma1=0 ctlport=0x530

creating  device  files  &#8208;&#8208;&#8208;&#8208;&#8208;&#8208;&#8208;&#8208;&#8208;&#8208;&#8208;&#8208;&#8208;&#8208;&#8208;&#8208;&#8208;&#8208;&#8208;&#8208;&#8208; ALSA native device
files are located in /dev/snd/.   (ALSA&#8217;s  kernel&#8208;  OSS&#8208;emulation
device files are of course the same as the OSS device files.)

Udev  takes care of creating devices files when modules are load&#8208;
ed.

reloading     modules     across      APM      suspend&#8208;a 

what shall I enter into, /etc/modprobe.d/sound.conf 

Create /etc/modprobe.d/sound.conf with the following contents:

> ## ALSA portion
alias char-major-116 snd
alias snd-card-0 snd-hda-intel
alias snd-card-1 snd-usb-audio

## module options should go here
options snd-hda-intel index=0 model=ref
options snd-usb-audio index=1

and run 'alsa force-reload' or reboot.


modproble alsabase:
>   LINE_OPTS && /lib/alsa/modprobe-post-install snd-verbose-printk
install snd-virtuoso /sbin/modprobe --ignore-install snd-virtuoso $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-virtuoso
install snd-vx222 /sbin/modprobe --ignore-install snd-vx222 $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-vx222
install snd-vxpocket /sbin/modprobe --ignore-install snd-vxpocket $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-vxpocket
install snd-wavefront /sbin/modprobe --ignore-install snd-wavefront $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-wavefront
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
 

---

### Post by daimaru on 2009-12-06
try installing pulse audio device chooser
```
sudo apt-get install padevchooser
```
then while playing a audio file (video mp3...) left click on the tray icon choose -> volume control go to the playback tab and under "Playback Stream on:" change it to the desired device.

works for switching between my usb headset and internal audio card.

---

### Post by frenchn00b on 2009-12-06
> **daimaru said:**
> try installing pulse audio device chooser
```
sudo apt-get install padevchooser
```
then while playing a audio file (video mp3...) left click on the tray icon choose -> volume control go to the playback tab and under "Playback Stream on:" change it to the desired device.

works for switching between my usb headset and internal audio card.

I use the console and crontab. no X. shall be more expect solution.
 
[B]the issue is in /etc/modprobe.d/sound.conf , but no one understand the guy that made the man page.
[/B]

---

### Post by frenchn00b on 2009-12-08
[B]Ok guys, solved with assistance of ALSA programer, apparently on boards and forums, everywhere even by debian, nobody knows really how ALSA works and noboby reads the man page of alsa. 

check your card name into  /etc/modprobe.d/alsa-base

the very best solution made by linux professional lies into a single file which is called sound.conf :
 cat /etc/modprobe.d/sound.conf[/B]
[COLOR="Red"]```
## ALSA portion
alias char-major-116 snd
alias snd-card-0 snd-pcsp
alias snd-card-1 snd-usb-audio

## module options should go here
#options snd-hda-intel index=0 model=ref
options snd-usb-audio index=1
options snd-pcsp index=0
```[/COLOR]

reload it, alsa:
```
alsa force-reload
```

snd-pcsp is the sound card
and snd-usb-audio  is the microphoen mic ak type logitech
 
then you get the right order and you can play and hear music:
 arecord -l
```
**** List of CAPTURE Hardware Devices ****
card 0: default_1 [PnP Audio Device        ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [AK5370          ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

the problem lies also here:
 cat /proc/asound/modules
>  0 snd_usb_audio
 1 snd_usb_audio


 dmesg | grep pcsp
> [    8.982118] input: PC Speaker as /devices/platform/pcspkr/input/input4

---

### Post by afrodeity on 2012-01-25
apt-get install padevchooser

No candidate version found for padevchooser

I am using Oneiric

---

### Post by oldos2er on 2012-01-25
Closed, necromancy. Please start a new thread for your question.

---

