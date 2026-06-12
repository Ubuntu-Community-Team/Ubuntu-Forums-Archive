---
title: "RT2500 usb wifi disabled after resume on Intrepid"
date: 2008-11-27
forum: Networking &amp; Wireless
---

### Post by Joshua66 on 2008-11-27
Hi,
I have a Zonet ZEW2500P usb wifi device plugged into my ubuntu Intrepid box (motherboard: GA-P35-DS3L).  When I boot, it works without issue, but when I resume from suspend, the device is not available.  It shows up in 'lsusb', but not ifconfig, and there are a few errors in dmesg.  The only way I can get it to work is to unplug/replug it.  Any suggestions what may be wrong?

```
desktop:~$ lsusb
Bus 004 Device 007: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter

```

Snippet from dmesg during resume:
```

Nov 26 20:28:56 desktop kernel: [55429.765259] ------------[ cut here ]------------
Nov 26 20:28:56 desktop kernel: [55429.765261] WARNING: at /build/buildd/linux-2.6.27/kernel/power/main.c:176 suspend_test_finish+0x74/0x80()
Nov 26 20:28:56 redstone-desktop kernel: [55429.765263] Modules linked in: af_packet rfcomm bridge stp bnep sco l2cap bluetooth ppdev ipv6 acpi_cpufreq cpufreq_powersave cpufreq_stats cpufreq_conservative cpufreq_userspace cpufreq_ondemand freq_table container video output sbs sbshc pci_slot wmi battery iptable_filter ip_tables x_tables ac lp rt2500usb arc4 ecb crypto_blkcipher snd_hda_intel snd_usb_audio snd_pcm_oss snd_mixer_oss snd_pcm snd_usb_lib snd_seq_dummy rt73usb snd_seq_oss crc_itu_t rt2x00usb snd_seq_midi rt2x00lib snd_seq_midi_event uvcvideo rfkill snd_seq led_class parport_pc compat_ioctl32 snd_rawmidi joydev mac80211 snd_timer evdev serio_raw parport cfg80211 snd_seq_device snd_hwdep psmouse videodev snd v4l1_compat intel_agp nvidia(P) soundcore pcspkr agpgart button iTCO_wdt iTCO_vendor_support snd_page_alloc i2c_core shpchp pci_hotplug ext3 jbd mbcache sr_mod sd_mod cdrom crc_t10dif sg ata_generic pata_acpi usbhid hid pata_jmicron ata_piix libata scsi_mod r8169 dock ehci_hcd uhci_hcd usbcore thermal proce
Nov 26 20:28:56 desktop kernel: sor fan fbcon tileblit font bitblit softcursor fuse
Nov 26 20:28:56 desktop kernel: [55429.765313] Pid: 21155, comm: pm-suspend Tainted: P        W 2.6.27-7-generic #1
Nov 26 20:28:56 desktop kernel: [55429.765315]  [<c037c406>] ? printk+0x1d/0x1f
Nov 26 20:28:56 desktop kernel: [55429.765320]  [<c0131de9>] warn_on_slowpath+0x59/0x90
Nov 26 20:28:56 desktop kernel: [55429.765323]  [<c014d255>] ? sched_clock_cpu+0xd5/0x170
Nov 26 20:28:56 desktop kernel: [55429.765326]  [<c014c0af>] ? down_trylock+0x2f/0x40
Nov 26 20:28:56 desktop kernel: [55429.765328]  [<c01324c2>] ? try_acquire_console_sem+0x12/0x40
Nov 26 20:28:56 desktop kernel: [55429.765331]  [<c024e580>] ? kobject_put+0x20/0x50
Nov 26 20:28:56 desktop kernel: [55429.765334]  [<c015d204>] suspend_test_finish+0x74/0x80
Nov 26 20:28:56 desktop kernel: [55429.765337]  [<c015d2f6>] suspend_devices_and_enter+0xe6/0x190
Nov 26 20:28:56 desktop kernel: [55429.765340]  [<c015d571>] enter_state+0xd1/0x100
Nov 26 20:28:56 desktop kernel: [55429.765341]  [<c015d625>] state_store+0x85/0xd0
Nov 26 20:28:56 desktop kernel: [55429.765343]  [<c015d5a0>] ? state_store+0x0/0xd0
Nov 26 20:28:56 desktop kernel: [55429.765345]  [<c024e444>] kobj_attr_store+0x24/0x30
Nov 26 20:28:56 desktop kernel: [55429.765348]  [<c01ff4c7>] sysfs_write_file+0x97/0x100
Nov 26 20:28:56 desktop kernel: [55429.765350]  [<c01b24c0>] vfs_write+0xa0/0x110
Nov 26 20:28:56 desktop kernel: [55429.765353]  [<c01ff430>] ? sysfs_write_file+0x0/0x100
Nov 26 20:28:56 desktop kernel: [55429.765355]  [<c01b2602>] sys_write+0x42/0x70
Nov 26 20:28:56 desktop kernel: [55429.765357]  [<c0103f7b>] sysenter_do_call+0x12/0x2f
Nov 26 20:28:56 desktop kernel: [55429.765360]  [<c0370000>] ? default_device_exit+0x60/0xb0
Nov 26 20:28:56 desktop kernel: [55429.765363]  =======================
Nov 26 20:28:56 desktop kernel: [55429.765364] ---[ end trace 228ada6cf4949601 ]---
Nov 26 20:28:56 desktop kernel: [55429.765412] PM: Finishing wakeup.
Nov 26 20:28:56 desktop kernel: [55429.765414] Restarting tasks ... done.
Nov 26 20:28:56 desktop anacron[21361]: Anacron 2.3 started on 2008-11-26
Nov 26 20:28:56 desktop anacron[21361]: Will run job `cron.daily' in 5 min.
Nov 26 20:28:56 desktop anacron[21361]: Will run job `cron.weekly' in 10 min.
Nov 26 20:28:56 desktop anacron[21361]: Jobs will be executed sequentially
Nov 26 20:28:58 desktop NetworkManager: <info>  Waking up... 
Nov 26 20:28:58 desktop NetworkManager: <info>  (eth0): now managed 
Nov 26 20:28:58 desktop NetworkManager: <info>  (eth0): device state change: 1 -> 2 
Nov 26 20:28:58 desktop NetworkManager: <info>  (eth0): bringing up device. 
Nov 26 20:28:58 desktop kernel: [55431.216966] r8169: eth0: link down
Nov 26 20:28:58 desktop NetworkManager: <info>  (eth0): preparing device. 
Nov 26 20:28:58 desktop kernel: [55431.217523] ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov 26 20:28:58 desktop NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
Nov 26 20:28:58 desktop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Nov 26 20:28:58 desktop NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889) 
Nov 26 20:28:58 desktop NetworkManager: <info>  (wlan0): now managed 
Nov 26 20:28:58 desktop NetworkManager: <info>  (wlan0): device state change: 1 -> 2 
Nov 26 20:28:58 desktop NetworkManager: <info>  (wlan0): bringing up device. 
Nov 26 20:28:58 desktop NetworkManager: <WARN>  nm_device_hw_bring_up(): (wlan0): device not up after timeout! 
Nov 26 20:28:58 desktop acpid: client connected from 5970[0:0] 
Nov 26 20:28:58 desktop NetworkManager: <info>  (wlan0): deactivating device (reason: 2). 
Nov 26 20:28:58 desktop NetworkManager: <info>  (wlan0): device state change: 2 -> 3 
Nov 26 20:28:58 desktop NetworkManager: <info>  (wlan0): supplicant interface state change: 1 -> 2. 
Nov 26 20:28:58 desktop acpid: client connected from 5970[0:0] 

```

```
desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:7d:e9:0a:84  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:219 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1196 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1196 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:69424 (69.4 KB)  TX bytes:69424 (69.4 KB)

```

---

