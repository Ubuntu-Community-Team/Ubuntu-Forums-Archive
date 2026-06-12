---
title: "Connecting to wifi on Dell Optiplex 760"
date: 2016-11-16
forum: Networking &amp; Wireless
---

### Post by nktrain on 2016-11-16
I have put Ubuntu 16.04 on my dell optiplex 760. I can't find a way to connect it to the internet. No wifi connections show up, and I can't figure out how to use an ethernet connection either. I'm very new to linux, and i have no idea what the heck to do.

---

### Post by wildmanne39 on 2016-11-16
*Thread moved to **Networking & Wireless**.*

Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by nktrain on 2016-11-17
I have everything from terminal, but I don't know how to copy it and put it on my mac

---

### Post by wildmanne39 on 2016-11-17
Copy the information to your flash drive then put the flash drive into your mac and paste the information here using code tags.

---

### Post by nktrain on 2016-11-17
Heres what it said: (i had to export the text as a PDF to transport it)

[FONT=Helvetica]```

kearn@kearn-OptiPlex-760:~$ cat /lsb-release; uname -a[/FONT]
[FONT=Helvetica]cat: /lsb-release: No such file or directory[/FONT]
[FONT=Helvetica]Linux kearn-OptiPlex-760 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64[/FONT]
[FONT=Helvetica]x86_64 x86_64 GNU/Linux[/FONT]
[FONT=Helvetica]kearn@kearn-OptiPlex-760:~$ lspci -nnk | grep -iA2 net[/FONT]
[FONT=Helvetica]00:19.0 Ethernet controller [0200]: Intel Corporation 82567LM-3 Gigabit Network Connection[/FONT]
[FONT=Helvetica][8086:10de] (rev 02)[/FONT]
[FONT=Helvetica]Subsystem: Dell 82567LM-3 Gigabit Network Connection [1028:027f][/FONT]
[FONT=Helvetica]Kernel driver in use: e1000e[/FONT]
[FONT=Helvetica]Kernel modules: e1000e[/FONT]
[FONT=Helvetica]kearn@kearn-OptiPlex-760:~$ lsusb[/FONT]
[FONT=Helvetica]Bus 002 Device 002: ID 154b:005b PNY Flash Drive[/FONT]
[FONT=Helvetica]Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT]
[FONT=Helvetica]Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]
[FONT=Helvetica]Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]
[FONT=Helvetica]Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]
[FONT=Helvetica]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT]
[FONT=Helvetica]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]
[FONT=Helvetica]Bus 004 Device 003: ID 046d:c077 Logitech, Inc. M105 Optical Mouse[/FONT]
[FONT=Helvetica]Bus 004 Device 002: ID 413c:2105 Dell Computer Corp. Model L100 Keyboard[/FONT]
[FONT=Helvetica]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]
[FONT=Helvetica]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]
[FONT=Helvetica]kearn@kearn-OptiPlex-760:~$ iwconfig[/FONT]
[FONT=Helvetica]lo no wireless extensions.[/FONT]
[FONT=Helvetica]enp0s25 no wireless extensions.[/FONT]
[FONT=Helvetica]kearn@kearn-OptiPlex-760:~$ rfkill list all[/FONT]
[FONT=Helvetica]kearn@kearn-OptiPlex-760:~$ lsmod[/FONT]
[FONT=Helvetica]Module Size Used by[/FONT]
[FONT=Helvetica]nls_iso8859_1 16384 1[/FONT]
[FONT=Helvetica]uas 24576 0[/FONT]
[FONT=Helvetica]usb_storage 69632 2 uas[/FONT]
[FONT=Helvetica]snd_hda_codec_analog 16384 1[/FONT]
[FONT=Helvetica]snd_hda_codec_generic 77824 1 snd_hda_codec_analog[/FONT]
[FONT=Helvetica]snd_hda_intel 36864 3[/FONT]
[FONT=Helvetica]snd_hda_codec 135168 3 snd_hda_codec_generic,snd_hda_intel,snd_hda_codec_analog[/FONT]
[FONT=Helvetica]snd_hda_core 73728 4[/FONT]
[FONT=Helvetica]snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_hda_codec_analog[/FONT]
[FONT=Helvetica]snd_hwdep 16384 1 snd_hda_codec[/FONT]
[FONT=Helvetica]snd_pcm 106496 3 snd_hda_codec,snd_hda_intel,snd_hda_core[/FONT]
[FONT=Helvetica]snd_seq_midi 16384 0[/FONT]
[FONT=Helvetica]snd_seq_midi_event 16384 1 snd_seq_midi[/FONT]
[FONT=Helvetica]dell_wmi 16384 0[/FONT]
[FONT=Helvetica]sparse_keymap 16384 1 dell_wmi[/FONT]
[FONT=Helvetica]snd_rawmidi 32768 1 snd_seq_midi[/FONT]
[FONT=Helvetica]gpio_ich 16384 0[/FONT]
[FONT=Helvetica]dcdbas 16384 0[/FONT]
[FONT=Helvetica]snd_seq 69632 2 snd_seq_midi_event,snd_seq_midi
[/FONT]
[FONT=Helvetica]snd_seq_device 16384 3 snd_seq,snd_rawmidi,snd_seq_midi[/FONT]
[FONT=Helvetica]input_leds 16384 0[/FONT]
[FONT=Helvetica]coretemp 16384 0[/FONT]
[FONT=Helvetica]snd_timer 32768 2 snd_pcm,snd_seq[/FONT]
[FONT=Helvetica]serio_raw 16384 0[/FONT]
[FONT=Helvetica]shpchp 36864 0[/FONT]
[FONT=Helvetica]snd 81920 16[/FONT]
[FONT=Helvetica]snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda[/FONT]
[FONT=Helvetica]_intel,snd_seq_device,snd_hda_codec_analog[/FONT]
[FONT=Helvetica]soundcore 16384 1 snd[/FONT]
[FONT=Helvetica]mei_me 36864 0[/FONT]
[FONT=Helvetica]lpc_ich 24576 0[/FONT]
[FONT=Helvetica]8250_fintek 16384 0[/FONT]
[FONT=Helvetica]mei 98304 1 mei_me[/FONT]
[FONT=Helvetica]mac_hid 16384 0[/FONT]
[FONT=Helvetica]parport_pc 32768 1[/FONT]
[FONT=Helvetica]ppdev 20480 0[/FONT]
[FONT=Helvetica]lp 20480 0[/FONT]
[FONT=Helvetica]parport 49152 3 lp,ppdev,parport_pc[/FONT]
[FONT=Helvetica]autofs4 40960 2[/FONT]
[FONT=Helvetica]hid_generic 16384 0[/FONT]
[FONT=Helvetica]usbhid 49152 0[/FONT]
[FONT=Helvetica]hid 118784 2 hid_generic,usbhid[/FONT]
[FONT=Helvetica]psmouse 126976 0[/FONT]
[FONT=Helvetica]ahci 36864 2[/FONT]
[FONT=Helvetica]libahci 32768 1 ahci[/FONT]
[FONT=Helvetica]i915 1208320 3[/FONT]
[FONT=Helvetica]video 40960 2 i915,dell_wmi[/FONT]
[FONT=Helvetica]i2c_algo_bit 16384 1 i915[/FONT]
[FONT=Helvetica]drm_kms_helper 147456 1 i915[/FONT]
[FONT=Helvetica]wmi 20480 1 dell_wmi[/FONT]
[FONT=Helvetica]syscopyarea 16384 1 drm_kms_helper[/FONT]
[FONT=Helvetica]sysfillrect 16384 1 drm_kms_helper[/FONT]
[FONT=Helvetica]sysimgblt 16384 1 drm_kms_helper[/FONT]
[FONT=Helvetica]fb_sys_fops 16384 1 drm_kms_helper[/FONT]
[FONT=Helvetica]e1000e 237568 0[/FONT]
[FONT=Helvetica]drm 360448 5 i915,drm_kms_helper[/FONT]
[FONT=Helvetica]ptp 20480 1 e1000e[/FONT]
[FONT=Helvetica]pps_core 20480 1 ptp[/FONT]
[FONT=Helvetica]pata_acpi 16384 0

```[/FONT]

---

### Post by wildmanne39 on 2016-11-17
I do not see a wireless card listed, how old is this computer? Make sure it is enabled in the bios.

Your ethernet should be working, just plug it in and let network manager find the connection. Anyway we are just dealing with the wifi issue in this thread.

---

### Post by nktrain on 2016-11-17
apparently it doesn't have a wifi card. After opening it up, i discovered that there was no PCI card. That makes sense, as it was a school computer for a computer lab. Who knows what else it doesn't have. It didn't even have a disk drive. I also have no idea how to set up ethernet on linux.

---

### Post by wildmanne39 on 2016-11-17
I suggest you mark this thread solved by using thread tools at the top of the page and then start a new thread for your ethernet connection.
Thanks

---

