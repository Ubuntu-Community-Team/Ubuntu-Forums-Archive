---
title: "Kernel &quot;crash&quot; on removing USB wireless adapter under Edgy"
date: 2006-11-12
forum: Networking &amp; Wireless
---

### Post by Jose Catre-Vandis on 2006-11-12
The adapter in question is a Corega WLUSB Stick II v2, running on a fairly clean Edgy installation.

Following bootup, I insert the adapter, and dmesg reports as follows:

> Nov 12 13:30:42 edgy kernel: [17184968.652000] ohci_hcd 0000:00:02.1: wakeup
Nov 12 13:30:42 edgy kernel: [17184969.036000] usb 2-2: new full speed USB device using ohci_hcd and address 2
Nov 12 13:30:42 edgy kernel: [17184969.240000] usb 2-2: configuration #1 chosen from 1 choice
Nov 12 13:30:42 edgy kernel: [17184969.380000] drivers/usb/net/atmel/at76_usbdfu.c: USB Device Firmware Upgrade (DFU) handler v0.12beta23-fw_dwl loading
Nov 12 13:30:42 edgy kernel: [17184969.384000] drivers/usb/net/atmel/at76c503.c: Generic Atmel at76c503/at76c505 routines v0.12beta23-fw_dwl
Nov 12 13:30:42 edgy kernel: [17184969.388000] drivers/usb/net/atmel/at76c503-fw_skel.c: Atmel at76c505 (RFMD 2958) Wireless LAN Driver v0.12beta23-fw_dwl loading
Nov 12 13:30:42 edgy kernel: [17184969.388000] drivers/usb/net/atmel/at76c503-fw_skel.c: downloading firmware atmel_at76c505-rfmd2958.bin
Nov 12 13:30:42 edgy kernel: [17184969.432000] drivers/usb/net/atmel/at76c503-fw_skel.c: got it.
Nov 12 13:30:42 edgy kernel: [17184969.432000] usbcore: registered new driver at76c505-rfmd2958
Nov 12 13:30:45 edgy kernel: [17184971.900000] usb 2-2: reset full speed USB device using ohci_hcd and address 2
Nov 12 13:30:45 edgy kernel: [17184972.104000] usb 2-2: device firmware changed
Nov 12 13:30:45 edgy kernel: [17184972.104000] usb 2-2: USB disconnect, address 2
Nov 12 13:30:45 edgy kernel: [17184972.108000] drivers/usb/net/atmel/at76c503-fw_skel.c: wlan%%d disconnecting
Nov 12 13:30:45 edgy kernel: [17184972.108000] drivers/usb/net/atmel/at76c503-fw_skel.c: at76c505-rfmd2958 disconnected
Nov 12 13:30:45 edgy kernel: [17184972.284000] usb 2-2: new full speed USB device using ohci_hcd and address 3
Nov 12 13:30:45 edgy kernel: [17184972.492000] usb 2-2: configuration #1 chosen from 1 choice
Nov 12 13:30:45 edgy kernel: [17184972.496000] drivers/usb/net/atmel/at76c503-fw_skel.c: downloading firmware atmel_at76c505-rfmd2958.bin
Nov 12 13:30:46 edgy kernel: [17184972.528000] drivers/usb/net/atmel/at76c503-fw_skel.c: got it.
Nov 12 13:30:46 edgy kernel: [17184972.668000] drivers/usb/net/atmel/at76c503.c: $Id: at76c503.c,v 1.74 2005/03/08 01:33:14 jal2 Exp $ compiled Oct 13 2006 16:50:21
Nov 12 13:30:46 edgy kernel: [17184972.668000] drivers/usb/net/atmel/at76c503.c: firmware version 1.101.0 #86 (fcs_len 4)
Nov 12 13:30:46 edgy kernel: [17184972.672000] drivers/usb/net/atmel/at76c503.c: device's MAC 00:40:f4:81:df:0b, regulatory domain ETSI (Europe - (Spain+France) (id 48)
Nov 12 13:30:46 edgy kernel: [17184972.672000] drivers/usb/net/atmel/at76c503.c: registered wlan0
Nov 12 13:30:46 edgy kernel: [17184972.736000] wlan0 (WE) : Driver using old /proc/net/wireless support, please fix driver !

I then setup the wlan0 connection with my router and am happily connected.

if I then remove the adapter from the PC (with a terminal open) I get a load of output in the terminal screen:
> 
Nov 12 14:13:59 edgy kernel: [17179654.572000] usb 2-2: USB disconnect, address 3
Nov 12 14:13:59 edgy kernel: [17179654.572000] drivers/usb/net/atmel/at76c503-fw_skel.c: wlan0 disconnecting
Nov 12 14:13:59 edgy kernel: [17179654.572000] drivers/usb/net/atmel/at76c503.c: at76c503_delete_device: rtnl_lock already taken
Nov 12 14:13:59 edgy kernel: [17179654.596000] ------------[ cut here ]------------
Nov 12 14:13:59 edgy kernel: [17179654.596000] kernel BUG at net/core/dev.c:3134!
Nov 12 14:13:59 edgy kernel: [17179654.596000] invalid opcode: 0000 [#1]
Nov 12 14:13:59 edgy kernel: [17179654.596000] SMP 
Nov 12 14:13:59 edgy kernel: [17179654.596000] Modules linked in: ipv6 vmnet vmmon binfmt_misc rfcomm l2cap bluetooth cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative video tc1100_wmi sbs sony_acpi pcc_acpi i2c_ec hotkey dev_acpi button battery container ac asus_acpi nls_iso8859_1 nls_cp437 vfat fat nls_utf8 ntfs saa7134_dvb mt352 video_buf_dvb dvb_core nxt200x dvb_pll tda1004x sbp2 lp saa7134_alsa tuner snd_intel8x0 snd_ac97_codec snd_ac97_bus saa7134 snd_pcm_oss snd_pcm snd_mixer_oss video_buf compat_ioctl32 v4l2_common v4l1_compat ir_kbd_i2c ir_common videodev snd_seq_dummy snd_seq_oss tsdev at76c505_rfmd2958 at76c503 at76_usbdfu snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device i2c_nforce2 parport_pc parport floppy i2c_core shpchp pci_hotplug snd soundcore snd_page_alloc evdev psmouse serio_raw nvidia_agp agpgart pcspkr forcedeth ext3 jbd ehci_hcd ohci1394 ieee1394 ohci_hcd usbcore ide_generic ide_cd cdrom ide_disk generic amd74x
Nov 12 14:13:59 edgy kernel:  sata_nv libata scsi_mod thermal processor fan fbcon tileblit font bitblit softcursor vesafb capability commoncap
Nov 12 14:13:59 edgy kernel: [17179654.596000] CPU:    0
Nov 12 14:13:59 edgy kernel: [17179654.596000] EIP:    0060:[free_netdev+58/80]    Tainted: P      VLI
Nov 12 14:13:59 edgy kernel: [17179654.596000] EFLAGS: 00010297   (2.6.17-10-generic #2) 
Nov 12 14:13:59 edgy kernel: [17179654.596000] EIP is at free_netdev+0x3a/0x50
Nov 12 14:13:59 edgy kernel: [17179654.596000] eax: 00000002   ebx: f6a02400   ecx: 00000000   edx: f6a02000
Nov 12 14:13:59 edgy kernel: [17179654.596000] esi: f6a025e4   edi: 000000a0   ebp: f6a025e0   esp: c192fe78
Nov 12 14:13:59 edgy kernel: [17179654.596000] ds: 007b   es: 007b   ss: 0068
Nov 12 14:13:59 edgy kernel: [17179654.596000] Process khubd (pid: 1742, threadinfo=c192e000 task=c19ff560)
Nov 12 14:13:59 edgy kernel: [17179654.596000] Stack: f8b0a517 f8b127a8 f8b0f168 f8b0ec63 00000246 f6a02400 f8a3e080 f8a3e0a8 
Nov 12 14:13:59 edgy kernel: [17179654.596000]        dfa6fe14 f6a02400 f8a3e080 f8a3e0a8 dfa6fe14 f8a3d036 f8a3d4c8 f8a3d1b4 
Nov 12 14:13:59 edgy kernel: [17179654.596000]        f6a02000 dfa6fe00 f88e9994 dfa6fe8c dfa6fe14 c0245e2b dfa6fe14 dfa6fe14 
Nov 12 14:13:59 edgy kernel: [17179654.596000] Call Trace:
Nov 12 14:13:59 edgy kernel: [17179654.596000]  <f8b0a517> at76c503_delete_device+0x187/0x2c0 [at76c503]  <f8a3d036> at76c50x_disconnect+0x36/0x50 [at76c505_rfmd2958]
Nov 12 14:13:59 edgy kernel: [17179654.596000]  <f88e9994> usb_unbind_interface+0x34/0x70 [usbcore]  <c0245e2b> __device_release_driver+0x5b/0xa0
Nov 12 14:13:59 edgy kernel: [17179654.596000]  <c02460ec> device_release_driver+0x1c/0x30  <c0245657> bus_remove_device+0x77/0x90
Nov 12 14:13:59 edgy kernel: [17179654.596000]  <c02446c5> device_del+0x35/0x70  <f88e7bc6> usb_disable_device+0x86/0xe0 [usbcore]
Nov 12 14:13:59 edgy kernel: [17179654.596000]  <f88e3927> usb_disconnect+0x97/0xf0 [usbcore]  <f88e498a> hub_thread+0x27a/0xc80 [usbcore]
Nov 12 14:13:59 edgy kernel: [17179654.596000]  <c0136180> autoremove_wake_function+0x0/0x50  <f88e4710> hub_thread+0x0/0xc80 [usbcore]
Nov 12 14:13:59 edgy kernel: [17179654.596000]  <c0135f8b> kthread+0xab/0xe0  <c0135ee0> kthread+0x0/0xe0
Nov 12 14:13:59 edgy kernel: [17179654.596000]  <c0101005> kernel_thread_helper+0x5/0x10 
Nov 12 14:13:59 edgy kernel: [17179654.596000] Code: 64 29 c2 89 d0 e9 17 62 ef ff 8d b4 26 00 00 00 00 83 f8 03 75 15 c7 82 94 02 00 00 04 00 00 00 8d 82 f0 02 00 00 e9 56 63 fd ff <0f> 0b 3e 0c 84 d1 30 c0 eb e1 8d b6 00 00 00 00 8d bf 00 00 00 
Nov 12 14:13:59 edgy kernel: [17179654.596000] EIP: [free_netdev+58/80] free_netdev+0x3a/0x50 SS:ESP 0068:c192fe78

This does not resolve to a command prompt and just hangs there

Functionality is reduced to 0 and requires a hard reset to get going again.

OK, I hear you say, don't remove the USB adapter. Yes, this may be my only recourse, but its a bit of a dirty solution. Can anyone advise at to how to avoid this, so that I can safely remove the adapter without a crash?

---

### Post by FrodoB on 2006-11-12
Have you tried taking the network down for this device prior to removing?

$ sudo ifdown wlan0

A long shot, but who knows.

---

### Post by Jose Catre-Vandis on 2006-11-13
> **FrodoB said:**
> Have you tried taking the network down for this device prior to removing?

$ sudo ifdown wlan0

A long shot, but who knows.


Worth a go, but still crashes on removal :confused:

---

### Post by FrodoB on 2006-11-13
Maybe if you blacklisted the usb modules one at a time and tried to see if your device would use a different one if its normal one was not available.  

This is a long shot, but stranger things have happened. Here the ones in Edgy:

-rw-r--r-- 1 root root 40018 2006-10-13 15:09 ehci-hcd.ko
-rw-r--r-- 1 root root 26888 2006-10-13 15:09 ohci-hcd.ko
-rw-r--r-- 1 root root  9328 2006-10-13 15:09 sl811_cs.ko
-rw-r--r-- 1 root root 17833 2006-10-13 15:09 sl811-hcd.ko
-rw-r--r-- 1 root root 30284 2006-10-13 15:09 uhci-hcd.ko

I would blacklist ohci-hcd and see if your device would use uhci-hcd instead.

Don't forget to remove it from the blacklist if it does not help. 

Reference article:

[http://linuxusbguide.sourceforge.net/USB-guide-1.0.9/c122.html](http://linuxusbguide.sourceforge.net/USB-guide-1.0.9/c122.html)

Good luck.

---

### Post by Jose Catre-Vandis on 2006-11-15
> **FrodoB said:**
> 

I would blacklist ohci-hcd and see if your device would use uhci-hcd instead.



Hmmm...how do I blacklist ohci-hcd?

I tried putting it in /etc/modprobe.d/blacklist but it still loaded up after I inserted the adapter?

---

### Post by FrodoB on 2006-11-15
I don't know. I have read some articles on the net in the distant past that mentioned doing this for one reason or another.

It may just be a feature at the moment.  Some of the Ralink rt2500's do this using native drivers. The rt73's do not seem to have the problem.

---

### Post by Jose Catre-Vandis on 2006-11-15
I guess for now, no matter how tempting, I'll just have to resist the urge, 

anyway, sticking it in is always much more productive than taking it out ! :-)

Thanks for your help :-)

---

