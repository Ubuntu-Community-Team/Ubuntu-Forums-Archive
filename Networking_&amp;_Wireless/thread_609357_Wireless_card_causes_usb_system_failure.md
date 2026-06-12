---
title: "Wireless card causes usb system failure"
date: 2007-11-10
forum: Networking &amp; Wireless
---

### Post by frazras on 2007-11-10
I got a trendnet wireless card, installed the driver through ndiswrapper and it works perfectly on my ubuntu edgy install, but at times after extended use it just dies... the light goes out and it kills my usb ports. if i plug it in and out it doest light back up even in different ports. My usb mouse continues to work until i disconnect and reconnect it.
heres the tail of my /var/log messages when it happened.
I have to restart for it to work again.


```

 
Nov 10 19:17:07 abidah -- MARK --
Nov 10 19:37:10 abidah -- MARK --
Nov 10 19:51:20 abidah kernel: [17183413.968000] usb 3-3: USB disconnect, address 3
Nov 10 19:51:21 abidah kernel: [17183415.236000] f8f056b9
Nov 10 19:51:21 abidah kernel: [17183415.236000] Modules linked in: appletalk ax25 ipx p8023 binfmt_misc rfcomm l2cap bluetooth vmnet vmmon vboxdrv sonypi radeon drm ipv6 speedstep_lib cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative video tc1100_wmi sbs sony_acpi pcc_acpi i2c_ec hotkey dev_acpi button battery container ac asus_acpi fuse ndiswrapper sbp2 scsi_mod lp af_packet joydev usbhid snd_ali5451 snd_ac97_codec snd_ac97_bus tsdev snd_pcm_oss snd_pcm snd_mixer_oss snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device psmouse pcspkr snd pcmcia evdev serio_raw i2c_ali1535 i2c_ali15x3 soundcore parport_pc parport snd_page_alloc i2c_core 8139cp ati_agp agpgart 8139too mii yenta_socket shpchp pci_hotplug rsrc_nonstatic pcmcia_core ext3 jbd ehci_hcd uhci_hcd usbcore ohci1394 ieee1394 ide_generic ide_cd cdrom ide_disk generic alim15x3 thermal processor fan capability commoncap vesafb fbcon tileblit font bitblit softc
Nov 10 19:51:21 abidah kernel: rsor
Nov 10 19:51:21 abidah kernel: [17183415.236000] EIP:    0060:[pg0+950433465/1068893184]    Tainted: P      VLI
Nov 10 19:51:21 abidah kernel: [17183415.236000] EFLAGS: 00010286   (2.6.17-11-generic #2)
Nov 10 19:51:21 abidah kernel: [17183415.236000]  <6>note: wrapndis_wq/0[3145] exited with preempt_count 1
Nov 10 19:51:25 abidah kernel: [17183418.916000] ndiswrapper (wrap_cancel_urb:91): unlink failed: -19



```

---

