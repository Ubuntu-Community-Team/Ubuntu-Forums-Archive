---
title: "prism54 card crashes"
date: 2005-07-24
forum: Networking &amp; Wireless
---

### Post by dninja on 2005-07-24
This maybe should be in the laptop section but...

I've a Prism54 wireless card which will crash when I try to connect to some networks, my normal network is fine, an alternate one I occasionally use causes the crash.

Basically, I've done the iwconfig's to setup which WAP I'm connecting to then i try ifconfig eth0 up and something crashes. Below is what comes out in the messages file afterwards. Once this has happened once, running ifconfig again locks up, also the machine won't shutdown cleanly as it fails while trying to disable networking.

Can anyone help or suggest where else I could go for help? Feel free to ask for more info, I'll give all I can.

> Jul 24 18:37:55 tasslehoff kernel: ccb3e0db
Jul 24 18:37:55 tasslehoff kernel: PREEMPT 
Jul 24 18:37:55 tasslehoff kernel: Modules linked in: binfmt_misc speedstep_lib proc_intf cpufreq_powersave cpufreq_userspace freq_table axnet_cs ds apm ipv6 af_packet snd_ymfpci snd_ac97_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_opl3_lib snd_timer snd_hwdep snd_page_alloc gameport snd_mpu401_uart snd_rawmidi prism54 firmware_class snd_seq_device snd soundcore yenta_socket pcmcia_core donauboe irda crc_ccitt uhci_hcd usbcore pci_hotplug intel_agp agpgart floppy rtc pcspkr dm_mod capability commoncap parport_pc lp parport tsdev ide_cd cdrom evdev mousedev psmouse reiserfs ext3 jbd ide_generic ide_disk piix ide_core unix font vesafb cfbcopyarea cfbimgblt cfbfillrect
Jul 24 18:37:55 tasslehoff kernel: CPU:    0
Jul 24 18:37:55 tasslehoff kernel: EIP:    0060:[__crc_fb_unregister_client+8187309/9822850]    Not tainted
Jul 24 18:37:55 tasslehoff kernel: EFLAGS: 00010246   (2.6.8.1-3-386) 
Jul 24 18:37:55 tasslehoff kernel: EIP is at firmware_loading_store+0x43/0xb7 [firmware_class]
Jul 24 18:37:55 tasslehoff kernel: eax: 00000000   ebx: ccb40304   ecx: ccb40304   edx: 00000028
Jul 24 18:37:55 tasslehoff kernel: esi: ca54c5e0   edi: c6953fac   ebp: 00000002   esp: c6953f28
Jul 24 18:37:55 tasslehoff kernel: ds: 007b   es: 007b   ss: 0068
Jul 24 18:37:55 tasslehoff kernel: Process firmware.agent (pid: 3962, threadinfo=c6952000 task=c7d0b240)
Jul 24 18:37:55 tasslehoff kernel: Stack: c02cb6b4 c70ad420 c01d4a8e ca5c7de0 c6954000 00000002 c0175430 ca5c7de8 
Jul 24 18:37:55 tasslehoff kernel:        ccb403bc c6954000 00000002 c71f45a0 c0175462 c70ad420 c71f45a0 00000002 
Jul 24 18:37:55 tasslehoff kernel:        00000000 c70ad420 c6953fac c0144779 c70ad420 080ee408 00000002 c6953fac 
Jul 24 18:37:55 tasslehoff kernel: Call Trace:
Jul 24 18:37:55 tasslehoff kernel:  [class_device_attr_store+31/39] class_device_attr_store+0x1f/0x27
Jul 24 18:37:55 tasslehoff kernel:  [flush_write_buffer+34/39] flush_write_buffer+0x22/0x27
Jul 24 18:37:55 tasslehoff kernel:  [sysfs_write_file+45/67] sysfs_write_file+0x2d/0x43
Jul 24 18:37:55 tasslehoff kernel:  [vfs_write+175/217] vfs_write+0xaf/0xd9
Jul 24 18:37:55 tasslehoff kernel:  [sys_write+59/99] sys_write+0x3b/0x63
Jul 24 18:37:55 tasslehoff kernel:  [sysenter_past_esp+82/113] sysenter_past_esp+0x52/0x71
Jul 24 18:37:55 tasslehoff kernel: Code: ff 70 04 e8 ef 21 60 f3 8b 46 44 c7 40 04 00 00 00 00 8b 46 
Jul 24 18:37:55 tasslehoff kernel:  <3>prism54: request_firmware() failed for 'isl3890'

---

