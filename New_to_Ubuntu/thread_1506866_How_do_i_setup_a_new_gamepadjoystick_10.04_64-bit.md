---
title: "How do i setup a new gamepad/joystick 10.04 64-bit?"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by hopelessone on 2010-06-10
Hi,

The package joystick is installed how do i set it up?
```
blade@desktop:~$  jscal

Usage: jscal <device>

  -c             --calibrate         Calibrate the joystick
  -h             --help              Display this help
  -s <x,y,z...>  --set-correction    Sets correction to specified values
  -t             --test-center       Tests if joystick is corectly calibrated
                                       returns 0 on success, see the jscal
                                       manpage for error values
  -V             --version           Prints the version numbers
  -p             --print-correction  Prints the current settings as a jscal
                                       command line
  -q             --print-mappings    Print the current axis and button
                                       mappings as a jscal command line
  -u <n_of_axes,axmap1,axmap2,...,
      n_of_buttons,btnmap1,btnmap2,
      ...>       --set-mappings      Sets axis and button mappings to the
                                        specified values

blade@desktop:~$  jscal -c
jscal: missing devicename
blade@desktop:~$ 

```

Thanks...

---

### Post by hopelessone on 2010-06-11
Oh it's a saulabi arcade stick like these pic's:
[http://www.youloveit.com/pics/4b46d732f2057bf0536205629.jpg](http://www.youloveit.com/pics/4b46d732f2057bf0536205629.jpg)
[http://www.youloveit.com/pics/4a9e0735409ffb9a7f7fb9952.jpg](http://www.youloveit.com/pics/4a9e0735409ffb9a7f7fb9952.jpg)

What modules do i need to load? or how can i find out which module works...?

---

### Post by hopelessone on 2010-06-11
```
blade@desktop:~$ cat /dev/input/js0
cat: /dev/input/js0: No such file or directory
blade@desktop:~$ cd /dev/input
blade@desktop:/dev/input$ sudo MAKEDEV js
[sudo] password for blade: 
blade@desktop:/dev/input$ sudo modprobe joydev
blade@desktop:/dev/input$ sudo modprobe ns558
blade@desktop:/dev/input$ sudo modprobe sidewinder
blade@desktop:/dev/input$ lsmod
Module                  Size  Used by
nls_utf8                1421  1 
isofs                  33399  1 
warrior                 2926  0 
xpad                   10711  0 
led_class               3732  1 xpad
ff_memless              5109  1 xpad
zhenhua                 2391  0 
twidjoy                 2798  0 
tmdc                    5987  0 
stinger                 2534  0 
spaceorb                3561  0 
spaceball               3980  0 
sidewinder             10831  0 
magellan                2850  0 
joydump                 2706  0 
interact                4036  0 
guillemot               4039  0 
grip_mp                 6552  0 
grip                    6039  0 
gf2k                    5436  0 
cobra                   3648  0 
analog                  9909  0 
adi                     8558  0 
a3d                     5294  0 
gameport               10966  12 tmdc,sidewinder,joydump,interact,guillemot,grip_mp,grip,gf2k,cobra,analog,adi,a3d

joydev                 11072  0 
binfmt_misc             7960  1 
vboxnetadp              5171  0 
vboxnetflt             15064  0 
vboxdrv              1792343  2 vboxnetadp,vboxnetflt
snd_hda_codec_intelhdmi    13090  1 
snd_hda_codec_realtek   278890  1 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0 
vgastate                9857  1 vga16fb
snd_hda_intel          25645  0 
snd_hda_codec          85727  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_usb_audio          92747  1 
snd_usb_lib            18978  1 snd_usb_audio
snd_hwdep               6924  2 snd_hda_codec,snd_usb_audio
snd_pcm                87850  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_usb_audio
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23388  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23553  2 snd_pcm,snd_seq
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  317872  3 
drm_kms_helper         30742  1 i915
bttv                  128673  0 
v4l2_common            18357  1 bttv
snd                    70978  16 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_usb_audio,snd_hwdep,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   198770  4 i915,drm_kms_helper
video                  20623  1 i915
lp                      9336  0 
ir_common              43415  1 bttv
i2c_algo_bit            6024  2 i915,bttv
videobuf_dma_sg        12370  1 bttv
uvcvideo               62403  0 
videobuf_core          19269  2 bttv,videobuf_dma_sg
videodev               40486  3 bttv,v4l2_common,uvcvideo
btcx_risc               4224  1 bttv
v4l1_compat            15495  2 uvcvideo,videodev
ppdev                   6375  0 
v4l2_compat_ioctl32    12020  1 videodev
asus_atk0110           10033  0 
soundcore               8052  1 snd
parport_pc             29958  1 
tveeprom               13882  1 bttv
usbhid                 40988  0 
hid                    83376  1 usbhid
psmouse                64608  0 
serio_raw               4918  0 
intel_agp              29225  2 i915
parport                37160  3 lp,ppdev,parport_pc
output                  2503  1 video
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
sata_sil                8895  1 
atl1e                  33233  0 
blade@desktop:/dev/input$ lsmod | grep gameport
gameport               10966  2 sidewinder,ns558
blade@desktop:/dev/input$ cat /dev/input/js0
cat: /dev/input/js0: No such device
blade@desktop:/dev/input$
```

I can't figure out what to do?...please help

---

### Post by hopelessone on 2010-06-11
```
blade@desktop:/$ sudo lsinput
/dev/input/event0
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x1
   version : 0
   name    : "Power Button"
   phys    : "PNP0C0C/button/input0"
   bits ev : EV_SYN EV_KEY

/dev/input/event1
   bustype : BUS_HOST
   vendor  : 0x0
   product : 0x1
   version : 0
   name    : "Power Button"
   phys    : "LNXPWRBN/button/input0"
   bits ev : EV_SYN EV_KEY

/dev/input/event2
   bustype : BUS_ADB
   vendor  : 0x1
   product : 0x1
   version : 256
   name    : "Macintosh mouse button emulation"
   bits ev : EV_SYN EV_KEY EV_REL

/dev/input/event3
   bustype : BUS_USB
   vendor  : 0x99a
   product : 0x2515
   version : 272
   name    : "        USB Receiver"
   phys    : "usb-0000:00:1d.1-2/input0"
   uniq    : ""
   bits ev : EV_SYN EV_KEY EV_MSC EV_LED EV_REP

/dev/input/event4
   bustype : BUS_USB
   vendor  : 0x99a
   product : 0x2515
   version : 272
   name    : "        USB Receiver"
   phys    : "usb-0000:00:1d.1-2/input1"
   uniq    : ""
   bits ev : EV_SYN EV_KEY EV_REL EV_MSC

/dev/input/event5
   bustype : BUS_USB
   vendor  : 0xef5
   product : 0x3000
   version : 256
   name    : "ISAULABI   USBKeyStick"
   phys    : "usb-0000:00:1d.3-2/input0"
   uniq    : ""
   bits ev : EV_SYN EV_KEY EV_MSC EV_LED EV_REP

/dev/input/event6
   bustype : BUS_USB
   vendor  : 0xac8
   product : 0x332
   version : 256
   name    : "SAMSUNG PC-CAM USB 2.0"
   phys    : "usb-0000:00:1d.7-2/button"
   bits ev : EV_SYN EV_KEY

/dev/input/event7
   bustype : BUS_PCI
   vendor  : 0x10ec
   product : 0x887
   version : 1
   name    : "HDA Digital PCBeep"
   phys    : "card0/codec#0/beep0"
   bits ev : EV_SYN EV_SND

/dev/input/event8
   bustype : BUS_USB
   vendor  : 0xef5
   product : 0x3000
   version : 256
   name    : "ISAULABI   USBKeyStick"
   phys    : "usb-0000:00:1d.3-2/input1"
   uniq    : ""
   bits ev : EV_SYN EV_KEY EV_REL EV_MSC

blade@desktop:/$ 

```

some more info...

```
blade@desktop:/$ lsusb
Bus 005 Device 002: ID 0ef5:3000 PointChips 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 099a:2515 Zippy Technology Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0ac8:0332 Z-Star Microelectronics Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
blade@desktop:/$ 

```

---

### Post by hopelessone on 2010-06-11
The direction works i.e. up,down,left,right....just no buttons...

Any suggestions?

---

### Post by hopelessone on 2010-06-11
some more info i found:
```
II) config/udev: removing device ISAULABI   USBKeyStick
(II) ISAULABI   USBKeyStick: Close
(II) UnloadModule: "evdev"
(II) config/udev: removing device ISAULABI   USBKeyStick
(II) ISAULABI   USBKeyStick: Close
(II) UnloadModule: "evdev"
(II) config/udev: Adding input device ISAULABI   USBKeyStick (/dev/input/event3)
(**) ISAULABI   USBKeyStick: Applying InputClass "evdev keyboard catchall"
(**) ISAULABI   USBKeyStick: always reports core events
(**) ISAULABI   USBKeyStick: Device: "/dev/input/event3"
(II) ISAULABI   USBKeyStick: Found keys
(II) ISAULABI   USBKeyStick: Configuring as keyboard
(II) XINPUT: Adding extended input device "ISAULABI   USBKeyStick" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "kr"
```

Why   is it registering it as a keyboard?

Or more to the point how can i change it so i can access/change the buttons on this "Keyboard"?


Shouldn't it be showing up as "/dev/input/js0"

Thanks

---

