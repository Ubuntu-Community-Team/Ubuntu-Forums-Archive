---
title: "[SOLVED] Xbox 360 Controller issues"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by HittingSmoke on 2008-12-04
Ok. I went and grabbed a USB Xbox 360 controller today as I was under the impression they worked almost out of the box with Ubuntu but come to find out that's the original Xbox controllers.

I followed [this]("https://help.ubuntu.com/community/Xbox360Controller") guide and it actually made things worse. When I first plugged it in (before using this guide) my 360 Controller would show up under "lsusb" and the light would stay on steady on the Player 1 setting. It still wouldn't show up under jscalibrator or my emulators I'm trying to use it on though.

After running that guide, when I plug in my controller the ring just blinks as if it's trying to connect. The guide indicates that's a problem with the wireless controllers, but I'm using a USB wired controller. Jscalibrator now showed a new controller but it had no response nor did it show the correct amount of buttons for my 360 pad. The guide suggests a reboot so I tried that.

Rebooting with the 360 controller plugged in froze up Ubuntu's boot not far into the third segment of the progress bar and I had to unplug the pad and hard reboot.

After I rebooted and finished the HDD check I plugged back in and ran lsusb again. Now it's just hanging and not reporting anything, even with the pad unplugged. dmesg now reports MUCH more than it did before, and reports three Xbox 360 controllers plugged in. Also, much of the new output from dmesg seems to be input related.

```
[  317.483499] usb 1-6: new full speed USB device using ohci_hcd and address 4
[  317.707960] usb 1-6: configuration #1 chosen from 1 choice
[  317.710964] input: Microsoft Xbox 360 Controller as /devices/pci0000:00/0000:00:0b.0/usb1/1-6/1-6:1.0/input/input8
[  317.732993] input: Microsoft Xbox 360 Controller as /devices/pci0000:00/0000:00:0b.0/usb1/1-6/1-6:1.1/input/input9
[  432.209436] input: Microsoft Xbox 360 Controller as /devices/pci0000:00/0000:00:0b.0/usb1/1-6/1-6:1.2/input/input10
[  432.261420] BUG: unable to handle kernel NULL pointer dereference at virtual address 00000006
[  432.261425] printing eip: f89ffa5c *pde = 00000000 
[  432.261428] Oops: 0000 [#1] SMP 
[  432.261431] Modules linked in: joydev af_packet binfmt_misc ipv6 ppdev cpufreq_powersave cpufreq_conservative cpufreq_userspace cpufreq_stats cpufreq_ondemand freq_table sbs dock video output container sbshc battery iptable_filter ip_tables x_tables aes_i586 dm_crypt dm_mod ac it87 hwmon_vid parport_pc lp parport snd_emu10k1_synth snd_emux_synth snd_seq_virmidi snd_seq_midi_emul snd_emu10k1 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_util_mem snd_hwdep snd_seq_dummy snd_seq_oss xpad snd_seq_midi snd_rawmidi snd_seq_midi_event evdev snd_seq snd_timer snd_seq_device usblp snd emu10k1_gp psmouse usbhid pcspkr serio_raw hid k8temp gameport nvidia(P) soundcore agpgart i2c_nforce2 i2c_core button shpchp pci_hotplug ext3 jbd mbcache usb_storage libusual sg sd_mod sr_mod cdrom ata_generic pata_acpi floppy pata_amd ehci_hcd libata scsi_mod ohci_hcd forcedeth usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  432.261469] 
[  432.261471] Pid: 1555, comm: khubd Tainted: P        (2.6.24-22-generic #1)
[  432.261473] EIP: 0060:[<f89ffa5c>] EFLAGS: 00010286 CPU: 1
[  432.261479] EIP is at xpad_probe+0x23c/0x4b0 [xpad]
[  432.261481] EAX: 00000000 EBX: 00800000 ECX: f7df2100 EDX: 00000004
[  432.261483] ESI: 0000000e EDI: d58a2000 EBP: de4bbc00 ESP: df821cec
[  432.261485]  DS: 007b ES: 007b FS: 00d8 GS: 0000 SS: 0068
[  432.261486] Process khubd (pid: 1555, ti=df820000 task=f7da1140 task.ti=df820000)
[  432.261488] Stack: e2854494 00000041 f89fffbf f7d3e8e4 de4bbc04 da54f41c da54f400 02a01528 
[  432.261492]        e2854480 f8a01528 da54f400 f8a01528 da54f400 f8a01440 de4bbc00 f88a36f9 
[  432.261496]        00000000 da54f41c da54f494 00000000 da54f41c 00000000 f8a01474 f88bc800 
[  432.261500] Call Trace:
[  432.261540]  [<f88a36f9>] usb_probe_interface+0xb9/0x140 [usbcore]
[  432.261577]  [<c0282918>] driver_probe_device+0x88/0x190
[  432.261586]  [<c031a1c5>] klist_next+0x55/0xb0
[  432.261605]  [<c0281c14>] bus_for_each_drv+0x44/0x70
[  432.261627]  [<c0282ae6>] device_attach+0x86/0x90
[  432.261630]  [<c0282a20>] __device_attach+0x0/0x10
[  432.261637]  [<c0281b85>] bus_attach_device+0x45/0x90
[  432.261656]  [<c0280c18>] device_add+0x418/0x510
[  432.261694]  [<f88a1642>] usb_set_configuration+0x392/0x5d0 [usbcore]
[  432.261769]  [<f88a9c26>] generic_probe+0x76/0xb0 [usbcore]
[  432.261808]  [<f88a34b3>] usb_probe_device+0x33/0x40 [usbcore]
[  432.261822]  [<c0282918>] driver_probe_device+0x88/0x190
[  432.261828]  [<c031a1c5>] klist_next+0x55/0xb0
[  432.261846]  [<c0281c14>] bus_for_each_drv+0x44/0x70
[  432.261867]  [<c0282ae6>] device_attach+0x86/0x90
[  432.261870]  [<c0282a20>] __device_attach+0x0/0x10
[  432.261877]  [<c0281b85>] bus_attach_device+0x45/0x90
[  432.261895]  [<c0280c18>] device_add+0x418/0x510
[  432.261934]  [<f889c406>] usb_new_device+0x56/0xa0 [usbcore]
[  432.261967]  [<f889dbb7>] hub_thread+0x687/0xcb0 [usbcore]
[  432.262050]  [<c0140b60>] autoremove_wake_function+0x0/0x40
[  432.262073]  [<f889d530>] hub_thread+0x0/0xcb0 [usbcore]
[  432.262089]  [<c01408a2>] kthread+0x42/0x70
[  432.262091]  [<c0140860>] kthread+0x0/0x70
[  432.262098]  [<c0105667>] kernel_thread_helper+0x7/0x10
[  432.262116]  =======================
[  432.262117] Code: 00 98 f0 0f ab 47 1c 83 c2 01 0f b7 84 12 e0 fe 9f f8 66 85 c0 79 ea 8b 54 24 18 8b 42 04 8b 54 24 20 8b 40 0c 8b 4a 0c 8b 55 00 <0f> b6 70 06 0f b6 40 02 c1 e2 08 c1 e0 0f 09 c2 8b 44 24 20 81 
[  432.262135] EIP: [<f89ffa5c>] xpad_probe+0x23c/0x4b0 [xpad] SS:ESP 0068:df821cec
[  432.262179] ---[ end trace dc6964555daa4bc9 ]---

```

Most or none of the lines under the Xbox 360 lines showed up the first time I did this.

Now when I plug in the controller, it blinks once and turns off similar to the way the wireless controllers shut off when the batteries die, but this one is wired.

I also found [this]("http://xbox-linux.cvs.sourceforge.net/xbox-linux/kernel-2.6/drivers/usb/input/") info on an Ubuntu bug report. I have a vague idea of what to do with it based on the first guide I read, but I don't know how to undo what I did before and don't know if it would conflict. The first guide I did seemed to mess some stuff up so I don't want to proceed without some help.

I'd appreciate any help. I hope I've been specific enough but I'm still a fairly big noob when it comes to tweaking Linux. I really want to get to playing some Mario, and my closet full of retro games is useless with an old busted console with no good controllers.

---

### Post by HittingSmoke on 2008-12-04
Ok, another weird update. Now jscalibrator (not sure what started this, I didnt notice it after i rebooted) is reporting a controller with 16 buttons, which if you include the D-pad, adds up to the 360 controller. I cant get it to power up now though and I suspect its because of the 3 controllers already registered on dmesg that wont go away, any way to clear this? rebooting didnt help.

---

### Post by HittingSmoke on 2008-12-04
Ok, as things usually go with problems I'm persistent about, this one has inexplicably fixed itself. After posting this I unplugged the controller, tried and failed at compiling a module I found in the latter half of my OP then rebooted. After rebooting this time, the 3 controllers were cleared from dmesg. I plugged the pad back in and dmegs reported two Xbox 360 controllers. I started up jscalibrator and it also reported two controllers with (surprisingly) 16 buttons. I moved a stick and pressed some buttons and got response so calibrated and booted up ZSNES and ill be damned if I'm not playing Super Mario World with the perfect control scheme.

I'm gonna mark this as solved, but I cant offer a solution other than keep trying crap even if it didn't works last time. It works for me more often than not. I've literally posted every single step I've taken since plugging in the controller.

and P.S. while the controller is working, the Xbox ring is still blinking like it cant connect, so don't let the controller state discourage you if you're trying to get it to work, it **doesn't** mean Ubuntu cant see it.

---

