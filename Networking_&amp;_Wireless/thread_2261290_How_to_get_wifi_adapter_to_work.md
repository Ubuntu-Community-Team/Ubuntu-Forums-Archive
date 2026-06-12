---
title: "How to get wifi adapter to work"
date: 2015-01-17
forum: Networking &amp; Wireless
---

### Post by devdlp on 2015-01-17
I have a HP Pavilion a4000 and the wireless adapter doesnt seem to work but a ethernet cable does is there a script i can write in the terminal to get this work?

---

### Post by jeremy31 on 2015-01-17
> **devdlp said:**
> I have a HP Pavilion a4000 and the wireless adapter doesnt seem to work but a ethernet cable does is there a script i can write in the terminal to get this work?

I would start by running the script that is in the sticky post "before posting in networking & wireless" and post the results

---

### Post by devdlp on 2015-01-17
whats sticky post

---

### Post by QIII on 2015-01-17
The sticky post is [here]("http://ubuntuforums.org/showthread.php?t=370108").

A sticky post is one we caused to not be pushed down as new threads are added to a section.  It is "stuck" at the top like a sticky note.

---

### Post by devdlp on 2015-01-17
thank you

the sticky notes didnt help i still would like to get this work could someone help me with this please?

---

### Post by QIII on 2015-01-18
One of the things in the sticky was to run a script and post the results here.

If you do that, there are folks who have a great deal of expertise in these things.  They will be happy to help, but they need information to be able to do that.  Please have a look at the sticky again.  Run the script recommended and post the information back here.

There are a lot of folks that can help.

---

### Post by devdlp on 2015-01-18
i am so confused the thread is closed and i checked out some of the links on the page and they didnt help any

---

### Post by praseodym on 2015-01-18
Please open a terminal with CTRL+ALT+T and show the outputs of the commands:
```

uname -a
lspci -nnk
lsusb
iwconfig
rfkill list
lsmod
sudo iwlist scan
```

---

### Post by devdlp on 2015-01-18
deven@deven-BM384AA-ABA-a4511f:~$ uname -a
Linux deven-BM384AA-ABA-a4511f 3.13.0-44-generic #73-Ubuntu SMP Tue Dec 16 00:23:46 UTC 2014 i686 athlon i686 GNU/Linux
deven@deven-BM384AA-ABA-a4511f:~$ lspci -nnk
00:00.0 RAM memory [0500]: NVIDIA Corporation MCP61 Memory Controller [10de:03ea] (rev a1)
    Subsystem: Hewlett-Packard Company Device [103c:2a99]
00:01.0 ISA bridge [0601]: NVIDIA Corporation MCP61 LPC Bridge [10de:03e0] (rev a2)
    Subsystem: Hewlett-Packard Company Device [103c:2a99]
00:01.1 SMBus [0c05]: NVIDIA Corporation MCP61 SMBus [10de:03eb] (rev a2)
    Subsystem: Hewlett-Packard Company Device [103c:2a99]
    Kernel driver in use: nForce2_smbus
00:01.2 RAM memory [0500]: NVIDIA Corporation MCP61 Memory Controller [10de:03f5] (rev a2)
    Subsystem: Hewlett-Packard Company Device [103c:2a99]
00:02.0 USB controller [0c03]: NVIDIA Corporation MCP61 USB 1.1 Controller [10de:03f1] (rev a3)
    Subsystem: Hewlett-Packard Company Device [103c:2a99]
    Kernel driver in use: ohci-pci
00:02.1 USB controller [0c03]: NVIDIA Corporation MCP61 USB 2.0 Controller [10de:03f2] (rev a3)
    Subsystem: Hewlett-Packard Company Device [103c:2a99]
    Kernel driver in use: ehci-pci
00:04.0 PCI bridge [0604]: NVIDIA Corporation MCP61 PCI bridge [10de:03f3] (rev a1)
00:05.0 Audio device [0403]: NVIDIA Corporation MCP61 High Definition Audio [10de:03f0] (rev a2)
    Subsystem: Hewlett-Packard Company Device [103c:2a99]
    Kernel driver in use: snd_hda_intel
00:07.0 Bridge [0680]: NVIDIA Corporation MCP61 Ethernet [10de:03ef] (rev a2)
    Subsystem: Hewlett-Packard Company Device [103c:2a99]
    Kernel driver in use: forcedeth
00:08.0 IDE interface [0101]: NVIDIA Corporation MCP61 SATA Controller [10de:03f6] (rev a2)
    Subsystem: Hewlett-Packard Company Device [103c:2a99]
    Kernel driver in use: sata_nv
00:08.1 IDE interface [0101]: NVIDIA Corporation MCP61 SATA Controller [10de:03f6] (rev a2)
    Subsystem: Hewlett-Packard Company Device [103c:2a99]
    Kernel driver in use: sata_nv
00:09.0 PCI bridge [0604]: NVIDIA Corporation MCP61 PCI Express bridge [10de:03e8] (rev a2)
    Kernel driver in use: pcieport
00:0b.0 PCI bridge [0604]: NVIDIA Corporation MCP61 PCI Express bridge [10de:03e9] (rev a2)
    Kernel driver in use: pcieport
00:0c.0 PCI bridge [0604]: NVIDIA Corporation MCP61 PCI Express bridge [10de:03e9] (rev a2)
    Kernel driver in use: pcieport
00:0d.0 VGA compatible controller [0300]: NVIDIA Corporation C61 [GeForce 6150SE nForce 430] [10de:03d0] (rev a2)
    Subsystem: Hewlett-Packard Company Device [103c:2a99]
    Kernel driver in use: nvidia
00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 10h Processor HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 10h Processor DRAM Controller [1022:1202]
00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Miscellaneous Control [1022:1203]
    Kernel driver in use: k10temp
00:18.4 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Link Control [1022:1204]
deven@deven-BM384AA-ABA-a4511f:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 004: ID 1241:1166 Belkin MI-2150 Trust Mouse
Bus 002 Device 003: ID 046d:0a03 Logitech, Inc. Logitech USB Microphone
Bus 002 Device 002: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
deven@deven-BM384AA-ABA-a4511f:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

deven@deven-BM384AA-ABA-a4511f:~$ rfkill list
deven@deven-BM384AA-ABA-a4511f:~$ lsmod
Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39205  1 
snd_hda_codec_realtek    59259  1 
rfcomm                 53664  0 
bnep                   18895  2 
bluetooth             342208  10 bnep,rfcomm
snd_hda_intel          42730  5 
snd_usb_audio         128066  1 
snd_usbmidi_lib        24367  1 snd_usb_audio
snd_hda_codec         164067  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  2 snd_usb_audio,snd_hda_codec
snd_seq_midi           13132  0 
binfmt_misc            13140  1 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25135  2 snd_usbmidi_lib,snd_seq_midi
snd_pcm                85501  4 snd_usb_audio,snd_hda_codec,snd_hda_intel
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
joydev                 17101  0 
nvidia              10333941  50 
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
kvm                   388310  0 
snd_timer              28584  2 snd_pcm,snd_seq
serio_raw              13230  0 
drm                   244037  1 nvidia
k10temp                12958  0 
snd                    60939  23 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
i2c_nforce2            13037  0 
mac_hid                13037  0 
soundcore              12600  1 snd
parport_pc             31981  0 
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
hid_generic            12492  0 
pata_acpi              12886  0 
usbhid                 47070  0 
hid                    87604  2 hid_generic,usbhid
psmouse                91357  0 
sata_nv                23004  3 
forcedeth              62140  0 
deven@deven-BM384AA-ABA-a4511f:~$ sudo iwlist scan
[sudo] password for deven: 
Sorry, try again.
[sudo] password for deven: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

deven@deven-BM384AA-ABA-a4511f:~$

---

### Post by praseodym on 2015-01-19
No wireless adapter shown. Lets try
```

pccardctl info
```
Can you check the BIOS settings if there is any wireless option to activate?

---

### Post by devdlp on 2015-01-20
could someone give me advice on this or am i just doomed??

deven@deven-BM384AA-ABA-a4511f:~$ pccardctl info
deven@deven-BM384AA-ABA-a4511f:~$

I have still have a problem with this

---

### Post by praseodym on 2015-05-30
Have you checked the BIOS? BIOS-reset?

---

### Post by Asser on 2015-05-30
i have an HP pavilion dv6 - i had the same issue as yours and so far it has been solved after i read the steps in the link - **[https://sites.google.com/site/easylinuxtipsproject/internet](https://sites.google.com/site/easylinuxtipsproject/internet)** you just have to activate the right driver after re-installing it on your device.

---

### Post by jeremy31 on 2015-05-30
> **Asser said:**
> i have an HP pavilion dv6 - i had the same issue as yours and so far it has been solved after i read the steps in the link - **[https://sites.google.com/site/easylinuxtipsproject/internet](https://sites.google.com/site/easylinuxtipsproject/internet)** you just have to activate the right driver after re-installing it on your device.

But you have a laptop, the OP has a desktop and is unlikely to have a wifi device or the wifi is no longer functioning as it isn't detected

---

