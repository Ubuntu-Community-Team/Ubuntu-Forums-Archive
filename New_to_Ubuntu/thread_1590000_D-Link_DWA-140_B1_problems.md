---
title: "D-Link DWA-140 B1 problems"
date: 2010-10-07
forum: New to Ubuntu
---

### Post by ThePlank on 2010-10-07
Hi all,

I am a noob, so please be gentle.

I cannot get the above wireless USB dongle to work. I have followed the instructions on what seems to be thousands of  links, each after a fresh build, and after running the package updater.

The problem, it seems to me, is that the USB subsystem is somehow faulty since at no point does lsusb ever show anything even remotely related to this USB stick - showing only the keyboard and mouse. Of course, this means that all the techniques for blacklisting other drivers in order to get the manufacturer driver (ralink, 2870) to load instead is mute.

I suspect it might well be some source-code issue as when I compile the driver it reports, what looks to me, to be some programmer errors (ie some lazy, ahem, person, is allowing int pointers to passed as void*)

This is my first real go at a long-term linux installation (for my kids) and, unfortunately, I am now stuck.

Anyone got any ideas of how to proceed?

Thanks,

The Plank.

---

### Post by ThePlank on 2010-10-07
Sorry, I lost myself in frustration and depair: I am using Ubuntu 10.04.1, 2.6.32-25-generic, on a reasonably old Fujitsu-Siemens Esprimo, and I also have problems with the video/driver and monitor (but that can wait)

Also after the reboot on installation there was a perpetual IO error that required a hard-reset, but seems to go away after Ubuntu comes back up again.

---

### Post by Hippytaff on 2010-10-07
Does ubuntu recognise a normal usb flash drive in the same port?
Does the usb wireless adapter work in other (not so good) operating systems (ie windows)

---

### Post by ThePlank on 2010-10-07
Hi,

Windows 7 (yes, I have to use it for work :( ) recognises that somethings plugged in, but requires manufacturers driver; USB stick (integral, 2Gb) comes up fine. Also, using an external DVD drive, and USB mouse and keyboard.

Here is the output of the lsusb (with everthing plugged in) 

> 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0603:00f2 Novatek Microelectronics Corp. 
Bus 002 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 152d:2339 JMicron Technology Corp. / JMicron USA Technology Corp. 
Bus 001 Device 005: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
For completeness, here is the output of the lsmod, too:

> 
Module                  Size  Used by
nls_utf8                1069  1 
isofs                  29250  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
binfmt_misc             6587  1 
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_hda_codec_realtek   203374  1 
vga16fb                11385  0 
vgastate                8961  1 vga16fb
ppdev                   5259  0 
snd_hda_intel          22037  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
i915                  286079  3 
drm_kms_helper         29297  1 i915
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
drm                   162409  4 i915,drm_kms_helper
snd_rawmidi            19056  1 snd_seq_midi
i2c_algo_bit            5028  1 i915
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
video                  17375  1 i915
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
output                  1871  1 video
intel_agp              24119  2 i915
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
agpgart                31724  2 drm,intel_agp
serio_raw               3978  0 
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
usb_storage            39553  1 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
lp                      7060  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67032  1 usbhid
ohci1394               26950  0 
ieee1394               81181  1 ohci1394
ahci                   32200  2 
e1000e                119856  0 
I am no expert (at all ) but it seems to me that Ubuntu=>Linux, simply doesn't see it. I have built the 2870 driver and insmod'd it and it appears under lsmod, but still not in lsusb.

Thanks,

The Plank

(Edit: any commands for a more pretty-print of the lsmod output?)

---

### Post by ThePlank on 2010-10-07
If I remove the external USB DVD drive lsusb gives:

> 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0603:00f2 Novatek Microelectronics Corp. 
Bus 002 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


which, is the keyboard and mouse (the alcor device, I think, reflects that the DVD drive has two USB ports on the back of it, so is some sort of USB hub extension)

Thanks,

The Plank.

---

### Post by Hippytaff on 2010-10-07
Looks like it can't see it your right...I'm no where near an expert on this either.
 
The only thing I can really suggest for the time being (until someone who knows more than me comes along, which they probably will shortly) is do lsub without the adapter plugged in. Plug it in, leasve it for a minute and lsusb again and compare the output. might be reading it as something else!?
 
was going to suggest modprobe, but no good if it's not picking up the usb device in the first place.

---

### Post by ThePlank on 2010-10-07
Hi,

Device unplugged (everything else plugged in)

> 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0603:00f2 Novatek Microelectronics Corp. 
Bus 002 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 010: ID 152d:2339 JMicron Technology Corp. / JMicron USA Technology Corp. 
Bus 001 Device 009: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Device plugged in (with everything else):

> 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0603:00f2 Novatek Microelectronics Corp. 
Bus 002 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 010: ID 152d:2339 JMicron Technology Corp. / JMicron USA Technology Corp. 
Bus 001 Device 009: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


So no difference, as you suspected.

Perhaps it's trying to register with the USB subsystem using a non-dynamic device id? Something like, it wants to be device 2, say, but the mouse already has that, so it doesn't register. Is there anyway I can force the kernel to remap, say, the keyboard and mouse to different device Id's and see if that works?

If so, how would I go about doing that? Another thought, and I must say, I am well out of my comfort zone, even suggesting it - how do I look at the IRQ's, and are they remappable under Linux? Does USB use DMA?

Thanks,

The Plank.

---

### Post by Hippytaff on 2010-10-07
>  
Something like, it wants to be device 2, say, but the mouse already has that, so it doesn't register

 
could remove the mouse and see if lsusb picks up the usb adapter instead? but other than that I'm afraid I've reached the extent of my knowledge (currently). I'll do some research after work, but by then hopefully someone will have come to your aid (someone who knows more than me)

---

### Post by ThePlank on 2010-10-07
> **Hippytaff said:**
> could remove the mouse and see if lsusb picks up the usb adapter instead? but other than that I'm afraid I've reached the extent of my knowledge (currently). I'll do some research after work, but by then hopefully someone will have come to your aid (someone who knows more than me)

Just tried pulling all of the devices in and out, and, where possible, I've looked up lsusb, and they all seem to be able to be dynamic. Looks like a red-herring, unfortunately ... thanks for your help :)

---

### Post by ThePlank on 2010-10-07
Here's the output from dmesg | less that seems relevant to this problem:

> 
[    1.195787] usb 2-1: configuration #1 chosen from 1 choice
[    1.215691] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[fdaff000-fdaff7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    1.223257] usbcore: registered new interface driver hiddev
[    1.238242] input: NOVATEK USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input3
[    1.238364] generic-usb 0003:0603:00F2.0001: input,hidraw0: USB HID v1.10 Keyboard [NOVATEK USB Keyboard] on usb-0000:00:1d.0-1/input0
[    1.273783] input: NOVATEK USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/input/input4
[    1.274012] generic-usb 0003:0603:00F2.0002: input,hiddev96,hidraw1: USB HID v1.10 Device [NOVATEK USB Keyboard] on usb-0000:00:1d.0-1/input1
[    1.274042] usbcore: registered new interface driver usbhid
[    1.274105] usbhid: v2.6:USB HID core driver
[    1.436094] usb 2-2: new full speed USB device using uhci_hcd and address 3
[    1.497951] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    1.560100] usb 2-2: device descriptor read/64, error -71
[    1.784048] usb 2-2: device descriptor read/64, error -71
[    2.000045] usb 2-2: new full speed USB device using uhci_hcd and address 4
[    2.120082] usb 2-2: device descriptor read/64, error -71
[    2.344068] usb 2-2: device descriptor read/64, error -71
[    2.492344] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000180139466a53e]
[    2.560057] usb 2-2: new full speed USB device using uhci_hcd and address 5
[    2.968066] usb 2-2: device not accepting address 5, error -71
[    3.080160] usb 2-2: new full speed USB device using uhci_hcd and address 6
[    3.488098] usb 2-2: device not accepting address 6, error -71
[    3.488127] hub 2-0:1.0: unable to enumerate USB device on port 2


It seems like there are lot of errors with USB devices!

A bit of research led me to [http://ubuntuforums.org/showthread.php?t=797789](http://ubuntuforums.org/showthread.php?t=797789), which suggests:

> 
sudo echo -1 >/sys/module/usbcore/parameters/autosuspend


When I try to run the command, however, I always get permission denied.

Any ideas?

Thanks,

The Plank

---

### Post by ThePlank on 2010-10-07
I managed to run autosuspend, 
> 
cd /sys/module/usbcore/parameters/
sudo .\autosuspend
but no change. Does the echo pass -1 into the autosuspend command? If so, how do I 'sudo' to both parts of the command as in previous post?

I've also added,

> 
blacklist vga16fb
blacklist fbcon
to /etc/modprobe.d/blacklist-framebuffer.conf, as the link suggested. vga16fb no longer appears, but, it seems, that the fbcon blacklist is ignored.

Here's the current (known) problem identified by,

> 
dmesg | less | greg usb
> 
[    0.211129] usbcore: registered new interface driver usbfs
[    0.211147] usbcore: registered new interface driver hub
[    0.211184] usbcore: registered new device driver usb
[    0.339320] usb usb1: configuration #1 chosen from 1 choice
[    0.339768] usb usb2: configuration #1 chosen from 1 choice
[    0.340085] usb usb3: configuration #1 chosen from 1 choice
[    0.340387] usb usb4: configuration #1 chosen from 1 choice
[    0.340691] usb usb5: configuration #1 chosen from 1 choice
[    0.771362] usb 1-3: new high speed USB device using ehci_hcd and address 3
[    0.904336] usb 1-3: configuration #1 chosen from 1 choice
[    1.256106] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    1.437805] usb 2-1: configuration #1 chosen from 1 choice
[    1.455985] usbcore: registered new interface driver hiddev
[    1.471188] input: NOVATEK USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input3
[    1.471301] generic-usb 0003:0603:00F2.0001: input,hidraw0: USB HID v1.10 Keyboard [NOVATEK USB Keyboard] on usb-0000:00:1d.0-1/input0
[    1.507724] input: NOVATEK USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/input/input4
[    1.507860] generic-usb 0003:0603:00F2.0002: input,hiddev96,hidraw1: USB HID v1.10 Device [NOVATEK USB Keyboard] on usb-0000:00:1d.0-1/input1
[    1.507887] usbcore: registered new interface driver usbhid
[    1.507892] usbhid: v2.6:USB HID core driver
[    1.683353] usb 4-1: new full speed USB device using uhci_hcd and address 2
[    1.804085] usb 4-1: device descriptor read/64, error -71
[    2.028046] usb 4-1: device descriptor read/64, error -71
[    2.248046] usb 4-1: new full speed USB device using uhci_hcd and address 3
[    2.368065] usb 4-1: device descriptor read/64, error -71
[    2.592057] usb 4-1: device descriptor read/64, error -71
[    2.809113] usb 4-1: new full speed USB device using uhci_hcd and address 4
[    3.216050] usb 4-1: device not accepting address 4, error -71
[    3.328300] usb 4-1: new full speed USB device using uhci_hcd and address 5
[    3.740025] usb 4-1: device not accepting address 5, error -71
[    3.828204] usb 1-3.1: new high speed USB device using ehci_hcd and address 5
[    3.937107] usb 1-3.1: configuration #1 chosen from 1 choice
[    4.024184] usb 1-3.3: new low speed USB device using ehci_hcd and address 6
[    4.136807] usb 1-3.3: configuration #1 chosen from 1 choice
[    4.139262] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.3/1-3.3:1.0/input/input5
[    4.139367] generic-usb 0003:046D:C016.0003: input,hidraw2: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.7-3.3/input0
[   13.009008] usbcore: registered new interface driver usb-storage
[   13.009425] usb-storage: device found at 5
[   13.009427] usb-storage: waiting for device to settle before scanning
[   18.008781] usb-storage: device scan complete
[   20.528625] usb 4-1: new full speed USB device using uhci_hcd and address 6
[   20.652034] usb 4-1: device descriptor read/64, error -71
[   20.876057] usb 4-1: device descriptor read/64, error -71
[   21.092047] usb 4-1: new full speed USB device using uhci_hcd and address 7
[   21.216037] usb 4-1: device descriptor read/64, error -71
[   21.444046] usb 4-1: device descriptor read/64, error -71
[   21.660032] usb 4-1: new full speed USB device using uhci_hcd and address 8
[   22.068017] usb 4-1: device not accepting address 8, error -71
[   22.180035] usb 4-1: new full speed USB device using uhci_hcd and address 9
[   22.588015] usb 4-1: device not accepting address 9, error -71
[  117.152037] usb 4-1: new full speed USB device using uhci_hcd and address 10
[  117.272031] usb 4-1: device descriptor read/64, error -71
[  117.496035] usb 4-1: device descriptor read/64, error -71
[  117.712022] usb 4-1: new full speed USB device using uhci_hcd and address 11
[  117.832031] usb 4-1: device descriptor read/64, error -71
[  118.056041] usb 4-1: device descriptor read/64, error -71
[  118.272031] usb 4-1: new full speed USB device using uhci_hcd and address 12
[  118.680031] usb 4-1: device not accepting address 12, error -71
[  118.792033] usb 4-1: new full speed USB device using uhci_hcd and address 13
[  119.204046] usb 4-1: device not accepting address 13, error -71


After each change, a full reboot was performed

Thanks,

The Plank

---

### Post by ThePlank on 2010-10-07
Added irqpoll, (here:[http://ubuntuforums.org/showthread.php?t=1477330](http://ubuntuforums.org/showthread.php?t=1477330)) to kernel options:

> 
gksudo gedit /etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash irqpoll"
sudo update-grub
Still no change, DWA-140 does not show on lsusb.

:(

---

### Post by ThePlank on 2010-10-07
On this site [http://www.mail-archive.com/barry-devel@lists.sourceforge.net/msg00398.html](http://www.mail-archive.com/barry-devel@lists.sourceforge.net/msg00398.html), it suggests two options:

(1) recompile kernel with relevant options set
(2) configure a file with the options in it

The first option seems a little scary to me. How do I go about the second option? I can't find a file in /etc/modprobe.d that has the corresponding settings.

Thanks,

The Plank

---

### Post by Hippytaff on 2010-10-07
I wouldn't recommend rebuilding the kernel.
>  
 
I can't find a file in /etc/modprobe.d that has the corresponding settings.

 
what s in the folder modprobe.d :-)
 
I'll have a look at what mine looks like when I eventually get home...might shed some light :-)

---

### Post by ThePlank on 2010-10-07
> **Hippytaff said:**
> I wouldn't recommend rebuilding the kernel.

 
what s in the folder modprobe.d :-)

Lots of blacklisting stuff.

Have tried,

> [FONT=monospace]
[/FONT]echo Y > sudo /sys/module/usbcore/parameters/old_scheme_first[FONT=Verdana]
[/FONT][FONT=Verdana]

which also resolves the problem of 'sudo'ing both bits (you don't have too). I tried the autosuspend, accordingly (as above) as well, but still no luck.

Recompiling the kernel seems to be the end of the road. I can't find any more branches for further research ....

Surely I don't have to give up on Ubuntu only two days in?

:(
[/FONT]

---

### Post by ThePlank on 2010-10-07
OK - new tack:

Here's the output from 
> 
[    0.215108] usbcore: registered new interface driver usbfs
[    0.215124] usbcore: registered new interface driver hub
[    0.215161] usbcore: registered new device driver usb
[    0.343338] usb usb1: configuration #1 chosen from 1 choice
[    0.343788] usb usb2: configuration #1 chosen from 1 choice
[    0.344103] usb usb3: configuration #1 chosen from 1 choice
[    0.344408] usb usb4: configuration #1 chosen from 1 choice
[    0.344712] usb usb5: configuration #1 chosen from 1 choice
[    0.781708] usb 1-3: new high speed USB device using ehci_hcd and address 3
[    0.912223] usb 1-3: configuration #1 chosen from 1 choice
[    1.264063] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    1.445745] usb 2-1: configuration #1 chosen from 1 choice
[    1.464633] usbcore: registered new interface driver hiddev
[    1.480139] input: NOVATEK USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input3
[    1.480254] generic-usb 0003:0603:00F2.0001: input,hidraw0: USB HID v1.10 Keyboard [NOVATEK USB Keyboard] on usb-0000:00:1d.0-1/input0
[    1.516684] input: NOVATEK USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/input/input4
[    1.516840] generic-usb 0003:0603:00F2.0002: input,hiddev96,hidraw1: USB HID v1.10 Device [NOVATEK USB Keyboard] on usb-0000:00:1d.0-1/input1
[    1.516888] usbcore: registered new interface driver usbhid
[    1.516892] usbhid: v2.6:USB HID core driver
[    1.688053] usb 4-1: new full speed USB device using uhci_hcd and address 2
[    1.808060] usb 4-1: device descriptor read/64, error -71
[    2.036052] usb 4-1: device descriptor read/64, error -71
[    2.308069] usb 4-1: new full speed USB device using uhci_hcd and address 3
[    2.428043] usb 4-1: device descriptor read/64, error -71
[    2.656073] usb 4-1: device descriptor read/64, error -71
[    2.872075] usb 4-1: new full speed USB device using uhci_hcd and address 4
[    3.284044] usb 4-1: device not accepting address 4, error -71
[    3.396053] usb 4-1: new full speed USB device using uhci_hcd and address 5
[    3.804045] usb 4-1: device not accepting address 5, error -71
[    3.892209] usb 1-3.1: new high speed USB device using ehci_hcd and address 5
[    4.005089] usb 1-3.1: configuration #1 chosen from 1 choice
[    4.092188] usb 1-3.3: new low speed USB device using ehci_hcd and address 6
[    4.204696] usb 1-3.3: configuration #1 chosen from 1 choice
[    4.207255] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.3/1-3.3:1.0/input/input5
[    4.207363] generic-usb 0003:046D:C016.0003: input,hidraw2: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.7-3.3/input0
[   13.029097] usbcore: registered new interface driver usb-storage
[   13.029671] usb-storage: device found at 5
[   13.029674] usb-storage: waiting for device to settle before scanning
[   18.028255] usb-storage: device scan complete
[   20.827340] usb 4-1: new full speed USB device using uhci_hcd and address 6
[   20.949068] usb 4-1: device descriptor read/64, error -71
[   21.172077] usb 4-1: device descriptor read/64, error -71
[   21.388056] usb 4-1: new full speed USB device using uhci_hcd and address 7
[   21.508050] usb 4-1: device descriptor read/64, error -71
[   21.732042] usb 4-1: device descriptor read/64, error -71
[   21.948065] usb 4-1: new full speed USB device using uhci_hcd and address 8
[   22.356087] usb 4-1: device not accepting address 8, error -71
[   22.468041] usb 4-1: new full speed USB device using uhci_hcd and address 9
[   22.876056] usb 4-1: device not accepting address 9, error -71
[   45.476171] usb 4-1: new full speed USB device using uhci_hcd and address 10
[   45.596061] usb 4-1: device descriptor read/64, error -71
[   45.820052] usb 4-1: device descriptor read/64, error -71
[   46.036041] usb 4-1: new full speed USB device using uhci_hcd and address 11
[   46.156046] usb 4-1: device descriptor read/64, error -71
[   46.380044] usb 4-1: device descriptor read/64, error -71
[   46.596062] usb 4-1: new full speed USB device using uhci_hcd and address 12
[   47.004049] usb 4-1: device not accepting address 12, error -71
[   47.116045] usb 4-1: new full speed USB device using uhci_hcd and address 13
[   47.524037] usb 4-1: device not accepting address 13, error -71
[   62.423326] usb 1-3: USB disconnect, address 3
[   62.423334] usb 1-3.1: USB disconnect, address 5
[   62.433515] usb 1-3.3: USB disconnect, address 6
[   67.176233] usb 1-5: new high speed USB device using ehci_hcd and address 7
[   67.308578] usb 1-5: configuration #1 chosen from 1 choice
[   67.596155] usb 1-5.1: new high speed USB device using ehci_hcd and address 8
[   67.705126] usb 1-5.1: configuration #1 chosen from 1 choice
[   67.706304] usb-storage: device found at 8
[   67.706307] usb-storage: waiting for device to settle before scanning
[   67.792107] usb 1-5.3: new low speed USB device using ehci_hcd and address 9
[   67.904826] usb 1-5.3: configuration #1 chosen from 1 choice
[   67.907243] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5.3/1-5.3:1.0/input/input7
[   67.907378] generic-usb 0003:046D:C016.0004: input,hidraw2: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.7-5.3/input0
[   72.704441] usb-storage: device scan complete
[   73.408054] usb 3-1: new full speed USB device using uhci_hcd and address 2
[   73.528060] usb 3-1: device descriptor read/64, error -71
[   73.752060] usb 3-1: device descriptor read/64, error -71
[   73.968061] usb 3-1: new full speed USB device using uhci_hcd and address 3
[   74.088052] usb 3-1: device descriptor read/64, error -71
[   74.312041] usb 3-1: device descriptor read/64, error -71
[   74.528054] usb 3-1: new full speed USB device using uhci_hcd and address 4
[   74.936034] usb 3-1: device not accepting address 4, error -71
[   75.048071] usb 3-1: new full speed USB device using uhci_hcd and address 5
[   75.456063] usb 3-1: device not accepting address 5, error -71
[  618.000132] usb 3-1: new full speed USB device using uhci_hcd and address 6
[  618.124023] usb 3-1: device descriptor read/64, error -71
[  618.348026] usb 3-1: device descriptor read/64, error -71
[  618.564026] usb 3-1: new full speed USB device using uhci_hcd and address 7
[  618.684020] usb 3-1: device descriptor read/64, error -71
[  618.908023] usb 3-1: device descriptor read/64, error -71
[  619.124024] usb 3-1: new full speed USB device using uhci_hcd and address 8
[  619.532018] usb 3-1: device not accepting address 8, error -71
[  619.644022] usb 3-1: new full speed USB device using uhci_hcd and address 9
[  620.052024] usb 3-1: device not accepting address 9, error -71
[  896.696021] usb 3-1: new full speed USB device using uhci_hcd and address 10
[  896.816023] usb 3-1: device descriptor read/64, error -71
[  897.044023] usb 3-1: device descriptor read/64, error -71
[  897.260024] usb 3-1: new full speed USB device using uhci_hcd and address 11
[  897.380019] usb 3-1: device descriptor read/64, error -71
[  897.604030] usb 3-1: device descriptor read/64, error -71
[  897.820024] usb 3-1: new full speed USB device using uhci_hcd and address 12
[  898.228024] usb 3-1: device not accepting address 12, error -71
[  898.340023] usb 3-1: new full speed USB device using uhci_hcd 
It seems to me that I should not be using uhci_hcd. However, when I try,

> 
sudo modprobe -r uhci_hcd


I get the fatal error that this is built in, and there is no option, in the, it must be said rather naff, BIOS there is no option to select USB version. Perhaps, a BIOS flash might do the trick ....

---

### Post by Hippytaff on 2010-10-07
Have you checked the log files /var/log/ to see if it is reporting anything odd going on.
 
```

sudo tail -f /var/log/messages

```
 
Tail shows only the last 10 (I think 10) entrys.

---

### Post by ThePlank on 2010-10-07
That yields:

> 
Oct  7 17:06:01 ****-desktop kernel: [  454.492036] usb 4-1: new full speed USB device using uhci_hcd and address 10
Oct  7 17:06:01  ****-desktop kernel: [  455.056034] usb 4-1: new full speed USB device using uhci_hcd and address 11
Oct  7 17:06:02  ****-desktop kernel: [  455.616036] usb 4-1: new full speed USB device using uhci_hcd and address 12
Oct  7 17:06:03  ****-desktop kernel: [  456.136027] usb 4-1: new full speed USB device using uhci_hcd and address 13


So it is seeing it, I guess ... this output is produced by unplugging the damn thing, and plugging it back in again.

(I didn't know about that command - handy!)

Thanks,

The Plank

---

### Post by ThePlank on 2010-10-07
... as oppose to unplugging, and then plugging the mouse back in ....

> 
Oct  7 17:11:00 wilson-desktop kernel: [  754.084025] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.3/1-3.3:1.0/input/input9
Oct  7 17:11:00 wilson-desktop kernel: [  754.084449] generic-usb 0003:046D:C016.0006: input,hidraw2: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.7-3.3/input0
Oct  7 17:11:01 wilson-desktop kernel: [  754.276031] usb 4-1: new full speed USB device using uhci_hcd and address 22
Oct  7 17:11:01 wilson-desktop kernel: [  754.896027] usb 4-1: new full speed USB device using uhci_hcd and address 23
Oct  7 17:11:02 wilson-desktop kernel: [  755.456051] usb 4-1: new full speed USB device using uhci_hcd and address 24
Oct  7 17:11:02 wilson-desktop kernel: [  755.976035] usb 4-1: new full speed USB device using uhci_hcd and address 25


The difference, is the identification of the device, it seems. I reckon the kernel can't identify it so doesn't bother with it; so the next question is - how do I get the kernel to add this device to it's autodetect routine? Or can I force it's identity (how do I find that out?) to load a specific driver?

---

### Post by Hippytaff on 2010-10-07
As far as I know usb isn't driver dependent (ie you don't need a driver to see the device, only to use it). I'm sure there's a way to force it on, fire it up kind of thing. I read it in a post somewhere...will keep looking.

Edit - I think I might be thinking of what you have already tried - the suspend thing

---

### Post by Locke_99GS on 2010-10-07
I've had all sorts of issues with certain USB devices in the past (and still today, to some extent) and after going through most of the same crap you did came to the same result. NO-GO.

The best I've been able to get is from newer kernel versions. The changes to USB stuffs in the kernel is amazing. 

Try a new kernel and see if it resolves the issue.

```

sudo apt-add-repository ppa:kernel-ppa/ppa && sudo apt-get update
sudo apt-get install linux-generic-lts-backport-maverick linux-headers-generic-lts-backport-maverick

```

Thats all I got :) Hope it helps!

---

### Post by ThePlank on 2010-10-08
Hi,

Tried updating the kernel such that uname -r gives:

> 
2.6.35-22-generic
Still get recognition that something is being plugged in, sudo tail -f /var/log/messages gives

> 
Oct  8 11:02:12 ****-desktop kernel: [  271.096052] usb 4-1: new full speed USB device using uhci_hcd and address 22
Oct  8 11:02:12 ****-desktop kernel: [  271.657026] usb 4-1: new full speed USB device using uhci_hcd and address 23
Oct  8 11:02:13 ****-desktop kernel: [  272.220027] usb 4-1: new full speed USB device using uhci_hcd and address 24
Oct  8 11:02:13 ****-desktop kernel: [  272.740039] usb 4-1: new full speed USB device using uhci_hcd and address 25
But, alas, no recognition of the device itself (just that it has a USB interface) lsusb gives:

> 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0603:00f2 Novatek Microelectronics Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 001 Device 005: ID 152d:2339 JMicron Technology Corp. / JMicron USA Technology Corp. 
Bus 001 Device 003: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
and lsmod gives:

> 
Module                  Size  Used by
snd_hda_codec_realtek   217948  1 
binfmt_misc             6599  1 
ppdev                   5556  0 
snd_hda_intel          22107  2 
snd_hda_codec          87424  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71507  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  290972  3 
drm_kms_helper         30136  1 i915
drm                   168071  4 i915,drm_kms_helper
snd                    49006  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              26392  2 i915
i2c_algo_bit            5168  1 i915
soundcore                880  1 snd
video                  18712  1 i915
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
lp                      7342  0 
output                  1883  1 video
parport                31492  2 ppdev,lp
led_class               2633  0 
agpgart                32011  2 drm,intel_agp
usb_storage            40172  0 
serio_raw               4022  0 
usbhid                 37106  0 
hid                    67710  1 usbhid
ohci1394               27056  0 
ieee1394               81069  1 ohci1394
ahci                   19013  0 
e1000e                132924  0 
libahci                21667  3 ahci
So, now I am really stuck.

Anyone got any ideas of how to proceed?

Thanks,

The Plank

---

### Post by ThePlank on 2010-10-08
.. sorry, keep forgetting to put it all in one post!

```

dmesg | less | grep usb

```

gives,

```

[    0.217488] usbcore: registered new interface driver usbfs
[    0.217560] usbcore: registered new interface driver hub
[    0.217648] usbcore: registered new device driver usb
[    0.703937] usb 1-3: new high speed USB device using ehci_hcd and address 3
[    1.188045] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    1.388240] usbcore: registered new interface driver hiddev
[    1.404373] input: NOVATEK USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input2
[    1.404578] generic-usb 0003:0603:00F2.0001: input,hidraw0: USB HID v1.10 Keyboard [NOVATEK USB Keyboard] on usb-0000:00:1d.0-1/input0
[    1.442424] input: NOVATEK USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/input/input3
[    1.442703] generic-usb 0003:0603:00F2.0002: input,hiddev96,hidraw1: USB HID v1.10 Device [NOVATEK USB Keyboard] on usb-0000:00:1d.0-1/input1
[    1.442816] usbcore: registered new interface driver usbhid
[    1.442872] usbhid: USB HID core driver
[    1.612069] usb 4-1: new full speed USB device using uhci_hcd and address 2
[    1.732047] usb 4-1: device descriptor read/64, error -71
[    1.956063] usb 4-1: device descriptor read/64, error -71
[    2.172080] usb 4-1: new full speed USB device using uhci_hcd and address 3
[    2.292061] usb 4-1: device descriptor read/64, error -71
[    2.516037] usb 4-1: device descriptor read/64, error -71
[    2.732068] usb 4-1: new full speed USB device using uhci_hcd and address 4
[    3.140051] usb 4-1: device not accepting address 4, error -71
[    3.252150] usb 4-1: new full speed USB device using uhci_hcd and address 5
[    3.660163] usb 4-1: device not accepting address 5, error -71
[    3.748183] usb 1-3.1: new high speed USB device using ehci_hcd and address 5
[    3.944187] usb 1-3.3: new low speed USB device using ehci_hcd and address 6
[    4.059983] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.3/1-3.3:1.0/input/input4
[    4.060194] generic-usb 0003:046D:C016.0003: input,hidraw2: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.7-3.3/input0
[   12.428041] scsi6 : usb-storage 1-3.1:1.0
[   12.428276] usbcore: registered new interface driver usb-storage
[   20.989027] usb 4-1: new full speed USB device using uhci_hcd and address 6
[   21.113076] usb 4-1: device descriptor read/64, error -71
[   21.336050] usb 4-1: device descriptor read/64, error -71
[   21.552084] usb 4-1: new full speed USB device using uhci_hcd and address 7
[   21.672047] usb 4-1: device descriptor read/64, error -71
[   21.896064] usb 4-1: device descriptor read/64, error -71
[   22.112069] usb 4-1: new full speed USB device using uhci_hcd and address 8
[   22.520152] usb 4-1: device not accepting address 8, error -71
[   22.632069] usb 4-1: new full speed USB device using uhci_hcd and address 9
[   23.044219] usb 4-1: device not accepting address 9, error -71
[   55.236057] usb 4-1: new full speed USB device using uhci_hcd and address 10
[   55.356067] usb 4-1: device descriptor read/64, error -71
[   55.580086] usb 4-1: device descriptor read/64, error -71
[   55.796069] usb 4-1: new full speed USB device using uhci_hcd and address 11
[   55.916065] usb 4-1: device descriptor read/64, error -71
[   56.145066] usb 4-1: device descriptor read/64, error -71
[   56.360040] usb 4-1: new full speed USB device using uhci_hcd and address 12
[   56.772050] usb 4-1: device not accepting address 12, error -71
[   56.884071] usb 4-1: new full speed USB device using uhci_hcd and address 13
[   57.296089] usb 4-1: device not accepting address 13, error -71
[   92.340024] usb 4-1: new full speed USB device using uhci_hcd and address 14
[   92.460069] usb 4-1: device descriptor read/64, error -71
[   92.684030] usb 4-1: device descriptor read/64, error -71
[   92.900050] usb 4-1: new full speed USB device using uhci_hcd and address 15
[   93.020046] usb 4-1: device descriptor read/64, error -71
[   93.244049] usb 4-1: device descriptor read/64, error -71
[   93.460041] usb 4-1: new full speed USB device using uhci_hcd and address 16
[   93.868095] usb 4-1: device not accepting address 16, error -71
[   93.980049] usb 4-1: new full speed USB device using uhci_hcd and address 17
[   94.388034] usb 4-1: device not accepting address 17, error -71
[  115.652053] usb 4-1: new full speed USB device using uhci_hcd and address 18
[  115.772045] usb 4-1: device descriptor read/64, error -71
[  115.996040] usb 4-1: device descriptor read/64, error -71
[  116.212043] usb 4-1: new full speed USB device using uhci_hcd and address 19
[  116.332047] usb 4-1: device descriptor read/64, error -71
[  116.556058] usb 4-1: device descriptor read/64, error -71
[  116.772046] usb 4-1: new full speed USB device using uhci_hcd and address 20
[  117.181022] usb 4-1: device not accepting address 20, error -71
[  117.292048] usb 4-1: new full speed USB device using uhci_hcd and address 21
[  117.704042] usb 4-1: device not accepting address 21, error -71
[  271.096052] usb 4-1: new full speed USB device using uhci_hcd and address 22
[  271.217036] usb 4-1: device descriptor read/64, error -71
[  271.440048] usb 4-1: device descriptor read/64, error -71
[  271.657026] usb 4-1: new full speed USB device using uhci_hcd and address 23
[  271.781019] usb 4-1: device descriptor read/64, error -71
[  272.004042] usb 4-1: device descriptor read/64, error -71
[  272.220027] usb 4-1: new full speed USB device using uhci_hcd and address 24
[  272.629022] usb 4-1: device not accepting address 24, error -71
[  272.740039] usb 4-1: new full speed USB device using uhci_hcd and address 25
[  273.148036] usb 4-1: device not accepting address 25, error -71
[  335.072035] usb 4-1: new full speed USB device using uhci_hcd and address 26
[  335.192028] usb 4-1: device descriptor read/64, error -71
[  335.417044] usb 4-1: device descriptor read/64, error -71
[  335.633023] usb 4-1: new full speed USB device using uhci_hcd and address 27
[  335.756038] usb 4-1: device descriptor read/64, error -71
[  335.980042] usb 4-1: device descriptor read/64, error -71
[  336.196027] usb 4-1: new full speed USB device using uhci_hcd and address 28
[  336.604051] usb 4-1: device not accepting address 28, error -71
[  336.716044] usb 4-1: new full speed USB device using uhci_hcd and address 29
[  337.128046] usb 4-1: device not accepting address 29, error -71

```

---

### Post by ThePlank on 2010-10-08
Next interesting thing is this line,

```

usdbcode: registered new interface driver usb-storage

```

Now, I don't really now what this is. Is this going to the be the USB DVD drive? Or is it miss reading the USB wireless stick?

Any ideas?

Thanks,

The Plank

---

### Post by ThePlank on 2010-10-08
Should I report this as a bug?

---

### Post by Hippytaff on 2010-10-08
Might be worth checking the bug reports and filing one if one doesn't allready exist. Might work with an older kernel...
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink)
 
found this about the driver you need to use
> 
802.11 b/g/n card. Works out of the box on Jaunty Jackalope kernel 2.6.28-11. Module from staging at this time, with zero issue found yet. 

 
but I'm not convinced it's a driver issue. Might be worth considering buying a different usb wireless effot. Check the list of ones known to work :-)

---

### Post by Hippytaff on 2010-10-08
> 
usdbcode: registered new interface driver usb-storage

 
If this is what is being registered for your usb wireless I think you can switch it...hang on

---

### Post by ThePlank on 2010-10-08
> **Hippytaff said:**
> Might be worth checking the bug reports and filing one if one doesn't allready exist. Might work with an older kernel...
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink)
 
found this about the driver you need to use

 
but I'm not convinced it's a driver issue. Might be worth considering buying a different usb wireless effot. Check the list of ones known to work :-)


OK - here's the rub ...

> 
802.11 b/g/n card. Works out of the box on Jaunty Jackalope kernel  2.6.28-11. Module from staging at this time, with zero issue found yet.   


How do I say - please install kernel 2.6.28-11 ?

Thanks,

The Plank

---

### Post by Hippytaff on 2010-10-08
try this - [http://ubuntuforums.org/showpost.php?p=8591348&postcount=6](http://ubuntuforums.org/showpost.php?p=8591348&postcount=6)
 
before potching with kernels

---

### Post by Hippytaff on 2010-10-08
this will guide you through compiling new kernel headers
 
[http://ubuntuforums.org/showthread.php?t=1342593](http://ubuntuforums.org/showthread.php?t=1342593)
 
If we don't get to the bottom of this I'm buying you a new usb wireless adapter

---

### Post by ThePlank on 2010-10-08
> **Hippytaff said:**
> try this - [http://ubuntuforums.org/showpost.php?p=8591348&postcount=6](http://ubuntuforums.org/showpost.php?p=8591348&postcount=6)
 
before potching with kernels

Given it a go, but, dmesg | egrep 'rt28|usb|Phy', gives:

> 
[    0.009007] CPU: Physical Processor ID: 0
[    0.217555] usbcore: registered new interface driver usbfs
[    0.217628] usbcore: registered new interface driver hub
[    0.217715] usbcore: registered new device driver usb
[    0.699938] usb 1-3: new high speed USB device using ehci_hcd and address 3
[    1.184048] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    1.385324] usbcore: registered new interface driver hiddev
[    1.401063] input: NOVATEK USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input2
[    1.401262] generic-usb 0003:0603:00F2.0001: input,hidraw0: USB HID v1.10 Keyboard [NOVATEK USB Keyboard] on usb-0000:00:1d.0-1/input0
[    1.439115] input: NOVATEK USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/input/input3
[    1.439431] generic-usb 0003:0603:00F2.0002: input,hiddev96,hidraw1: USB HID v1.10 Device [NOVATEK USB Keyboard] on usb-0000:00:1d.0-1/input1
[    1.439675] usbcore: registered new interface driver usbhid
[    1.439733] usbhid: USB HID core driver
[    1.604074] usb 4-1: new full speed USB device using uhci_hcd and address 2
[    1.724050] usb 4-1: device descriptor read/64, error -71
[    1.948047] usb 4-1: device descriptor read/64, error -71
[    2.164064] usb 4-1: new full speed USB device using uhci_hcd and address 3
[    2.284043] usb 4-1: device descriptor read/64, error -71
[    2.508047] usb 4-1: device descriptor read/64, error -71
[    2.724101] usb 4-1: new full speed USB device using uhci_hcd and address 4
[    3.132038] usb 4-1: device not accepting address 4, error -71
[    3.244272] usb 4-1: new full speed USB device using uhci_hcd and address 5
[    3.656066] usb 4-1: device not accepting address 5, error -71
[    3.744190] usb 1-3.1: new high speed USB device using ehci_hcd and address 5
[    3.940175] usb 1-3.3: new low speed USB device using ehci_hcd and address 6
[    4.055744] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3.3/1-3.3:1.0/input/input4
[    4.055942] generic-usb 0003:046D:C016.0003: input,hidraw2: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.7-3.3/input0
[   15.805184] scsi6 : usb-storage 1-3.1:1.0
[   15.805380] usbcore: registered new interface driver usb-storage
[   53.036066] usb 4-1: new full speed USB device using uhci_hcd and address 6
[   53.156066] usb 4-1: device descriptor read/64, error -71
[   53.380080] usb 4-1: device descriptor read/64, error -71
[   53.596033] usb 4-1: new full speed USB device using uhci_hcd and address 7
[   53.716057] usb 4-1: device descriptor read/64, error -71
[   53.940070] usb 4-1: device descriptor read/64, error -71
[   54.156079] usb 4-1: new full speed USB device using uhci_hcd and address 8
[   54.564030] usb 4-1: device not accepting address 8, error -71
[   54.676034] usb 4-1: new full speed USB device using uhci_hcd and address 9
[   55.084035] usb 4-1: device not accepting address 9, error -71


ie - no change :(

---

### Post by Hippytaff on 2010-10-08
Try the kernel thing - the instructions start halfway down the page. Ubuntu 10.10 is out in 2 day's. You might have better luck with that, but it's worth checling these options out first

---

### Post by ThePlank on 2010-10-08
> **Hippytaff said:**
> Try the kernel thing - the instructions start halfway down the page. Ubuntu 10.10 is out in 2 day's. You might have better luck with that, but it's worth checling these options out first

Alas, just wiped the lot, and installed the 10.10 rc.  Still not working ....

---

### Post by Hippytaff on 2010-10-08
> 
Alas, just wiped the lot, and installed the 10.10 rc. Still not working

 
How annoying - lsusb?

---

### Post by ThePlank on 2010-10-08
The same :(

Just running through update manager, will give it a shove, and see what's what. Interestingly, wrong monitor detected, and wrong video driver selected, too (worse than 10.04)

It's like looking at the computer through a prescription monitor :lol:

---

### Post by Hippytaff on 2010-10-08
Just a punt
```

sudo rmmod rt2800usb

```
 
There is a solved thread with the same driver, but might be differect issue!? conflicting driver
 
[http://ubuntuforums.org/showthread.php?t=1589504](http://ubuntuforums.org/showthread.php?t=1589504)

---

### Post by ThePlank on 2010-10-08
> **Hippytaff said:**
> Just a punt
```

sudo rmmod rt2800usb

```There is a solved thread with the same driver, but might be differect issue!? conflicting driver
 
[http://ubuntuforums.org/showthread.php?t=1589504](http://ubuntuforums.org/showthread.php?t=1589504)

Nah - unfortunately, I get *no* wireless driver since the kernel doesn't recognise the device.

sudo tail -f /var/log/messages shows that it knows something's plugged in, but lsmod, and lsusb return nothing changed.

Sigh. I suspect it's part of the kernel development and not Ubuntu, but not looking promising, now -especially if the solution is to *downgrade* to any older kernel version (which, I think, is a step too far)

Nevermind. All is forgiven M$ ......

---

### Post by Hippytaff on 2010-10-08
I think there is a problem with ralink driver based stuff...since I've been on these forums I've seen so many posts about them...some get resolved, but unfortunately the damn thing needs to be recognised before you can mess about with blacklisting etc. Sorry I couldn't help resolve the issues - don't stop using the buntu though...for all it's failings in this respect it is fun :-D

---

### Post by ThePlank on 2010-10-08
> **Hippytaff said:**
> I think there is a problem with ralink driver based stuff...since I've been on these forums I've seen so many posts about them...some get resolved, but unfortunately the damn thing needs to be recognised before you can mess about with blacklisting etc. Sorry I couldn't help resolve the issues - don't stop using the buntu though...for all it's failings in this respect it is fun :-D

Thanks for trying, tho :)

Unfortunately, I think this has the same problems as Microsoft. Trying to do all things for all computers. Alas, it is doomed to failure (and doomed for second-best, even when it does work, since the sheer volume of work required for all success is monumental, and, possibly, not even possible)

Time to take a look at the Mac - yes, I know it's some odd variant of BSD ...but at least the hardware's fixed ... sort of.

Linux's goal, is, unfortunately, flawed: and it shows.

---

### Post by ThePlank on 2010-10-08
Sorry about the rant .... borne out of three solid days trying to resolve this problem ... :(

Will buy an 'approved' wireless dongle and see where we go from there.

Thanks for your help,

The Plank

(should blame Ralink, really - even Windows can't use generic drivers for it which implies that their kit is, ahem, not very good. I suspect that if I plugged my toaster into the usb bus, I'd have the same problems - but at least I'd get toast!!)

---

### Post by Hippytaff on 2010-10-08
Blame ralink :-D the annoying ting is Ubuntu worked out of the box for me!

---

### Post by ThePlank on 2010-10-09
Yup - lesson learnt

---

