---
title: "Ubuntu crashes and does not recover... can you help diagnose problem?"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by TpyKv on 2008-12-10
Hello,

Hope everyone is having a good week! 

I have got my atheros 5007 card working, my Orange internet stick, and VMware Server, all under Intrepid - so I have everything I need once again :)

Only one problem - it crashes, all the time, after about 5 mins use, and I have no idea what is causing it. 

Sometimes the GUI has black horizontal wiggly lines all across the screen... retarting X with ctrl + alt + backspace sorts it out.

Does anyone have any idea what can be causing this, or what I need to do to diagnose the problem?

Any help would be greatly recieved.... I'm so close to Ubuntu perfection :)

Many thanks in advance,

Kevin

---

### Post by Elfy on 2008-12-10
I'd start by looking in the logs - System Admin menu - system logs

It sounds as though it might be gpu related - what grpahics card do you have and are the drivers installed for it.

---

### Post by TpyKv on 2008-12-10
Thanks for the quick reply!

I don't have a graphics card, it's an internal Intel GMA X3100chipset I believe... just did the wiggly line thing again.

I have the logs open, should I post all of them, or -

auth.log,
daemon.log,
debug,
kern.log,
messages,
syslog,
user.log ,
- and/or - xorg.0.log?

---

### Post by Elfy on 2008-12-10
If it just did it run this from a terminal and post that 

```
dmesg |tail -20
cat /var/log/Xorg.0.log |tail
```

Don't post those files please they will be big

---

### Post by TpyKv on 2008-12-10
Those logs are very big....

I managed to get this inbetween two crashes.... seems to be crashing more frequently now...

kevin@vaio:~$ dmesg |tail -20
[   74.596833]  [<c014b79e>] ? ktime_get+0x1e/0x40
[   74.596844]  [<f8c949af>] __lbm_cw_ieee80211_rx+0x19f/0x600 [lbm_cw_mac80211]
[   74.596872]  [<c02eae1c>] ? skb_put+0xc/0xa0
[   74.596882]  [<c014a675>] ? hrtimer_reprogram+0x85/0xc0
[   74.596893]  [<f8d46c83>] ath5k_tasklet_rx+0x2e3/0x550 [ath5k]
[   74.596909]  [<c014a72d>] ? enqueue_hrtimer+0x7d/0x130
[   74.596919]  [<c014e63b>] ? getnstimeofday+0x4b/0x100
[   74.596930]  [<c0137258>] tasklet_action+0x78/0x100
[   74.596939]  [<c0137682>] __do_softirq+0x92/0x120
[   74.596947]  [<c013776d>] do_softirq+0x5d/0x60
[   74.596955]  [<c01378e5>] irq_exit+0x55/0x90
[   74.596962]  [<c0106c1a>] do_IRQ+0x4a/0x80
[   74.596971]  [<c0105003>] common_interrupt+0x23/0x30
[   74.596979]  [<c01700d8>] ? __audit_mq_getsetattr+0x68/0xb0
[   74.596993]  [<f8870800>] ? acpi_idle_enter_bm+0x268/0x2b7 [processor]
[   74.597011]  [<c02dbf7b>] cpuidle_idle_call+0x7b/0xd0
[   74.597020]  [<c010288d>] cpu_idle+0x7d/0x140
[   74.597028]  [<c036ee83>] rest_init+0x53/0x60
[   74.597039]  =======================
[   74.597044] ---[ end trace f843782bab7df5f3 ]---
kevin@vaio:~$ cat /var/log/Xorg.0.log |tail
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
kevin@vaio:~$ 


If any of this makes any sense?

I'll make the tea's

:)

---

### Post by TpyKv on 2008-12-10
Is there anyone else that might have a suggestion? or clue? 

Thanks guys and girls....

---

### Post by TpyKv on 2008-12-10
More error logs, if they are any use?

kevin@vaio:~$ sudo -s
[sudo] password for kevin: 
root@vaio:~# tail /var/log/messages
Dec 10 14:49:35 vaio kernel: [   64.969342]  [<c01378e5>] irq_exit+0x55/0x90
Dec 10 14:49:35 vaio kernel: [   64.969349]  [<c0106c1a>] do_IRQ+0x4a/0x80
Dec 10 14:49:35 vaio kernel: [   64.969358]  [<c0105003>] common_interrupt+0x23/0x30
Dec 10 14:49:35 vaio kernel: [   64.969367]  [<c01700d8>] ? __audit_mq_getsetattr+0x68/0xb0
Dec 10 14:49:35 vaio kernel: [   64.969380]  [<f8870800>] ? acpi_idle_enter_bm+0x268/0x2b7 [processor]
Dec 10 14:49:35 vaio kernel: [   64.969398]  [<c02dbf7b>] cpuidle_idle_call+0x7b/0xd0
Dec 10 14:49:35 vaio kernel: [   64.969407]  [<c010288d>] cpu_idle+0x7d/0x140
Dec 10 14:49:35 vaio kernel: [   64.969415]  [<c037a711>] start_secondary+0x9d/0xcc
Dec 10 14:49:35 vaio kernel: [   64.969425]  =======================
Dec 10 14:49:35 vaio kernel: [   64.969430] ---[ end trace 2b328a2701b5fdac ]---
root@vaio:~# tail -50 /var/log/messages
Dec 10 14:49:02 vaio kernel: [   32.072677] sky2 eth0: enabling interface
Dec 10 14:49:02 vaio kernel: [   32.352181] NET: Registered protocol family 17
Dec 10 14:49:16 vaio pulseaudio[5602]: ltdl-bind-now.c: Failed to find original dlopen loader.
Dec 10 14:49:16 vaio pulseaudio[5604]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Dec 10 14:49:16 vaio pulseaudio[5604]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Dec 10 14:49:21 vaio kernel: [   50.880631] NET: Registered protocol family 10
Dec 10 14:49:21 vaio kernel: [   50.885578] lo: Disabled Privacy Extensions
Dec 10 14:49:21 vaio kernel: [   50.888730] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 10 14:49:21 vaio kernel: [   50.892259] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec 10 14:49:21 vaio kernel: [   50.892292] hso0: Disabled Privacy Extensions
Dec 10 14:49:21 vaio pulseaudio[5705]: ltdl-bind-now.c: Failed to find original dlopen loader.
Dec 10 14:49:21 vaio pulseaudio[5705]: pid.c: Stale PID file, overwriting.
Dec 10 14:49:21 vaio pulseaudio[5705]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Dec 10 14:49:21 vaio pulseaudio[5705]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Dec 10 14:49:35 vaio kernel: [   64.968801] ------------[ cut here ]------------
Dec 10 14:49:35 vaio kernel: [   64.968817] WARNING: at /build/buildd/linux-backports-modules-2.6.27-2.6.27/debian/build/build-generic/compat-wireless-2.6/net/mac80211/rx.c:2200 __lbm_cw_ieee80211_rx+0x19f/0x600 [lbm_cw_mac80211]()
Dec 10 14:49:35 vaio kernel: [   64.968826] Modules linked in: ipv6 af_packet i915 drm binfmt_misc rfcomm bridge stp bnep sco l2cap bluetooth sonypi ppdev acpi_cpufreq cpufreq_conservative cpufreq_stats cpufreq_ondemand cpufreq_powersave freq_table cpufreq_userspace wmi container sbs sbshc pci_slot iptable_filter ip_tables x_tables sbp2 parport_pc lp parport hso rfkill joydev pcmcia snd_hda_intel snd_pcm_oss snd_mixer_oss arc4 tifm_7xx1 yenta_socket ecb rsrc_nonstatic tifm_core crypto_blkcipher snd_pcm psmouse evdev pcspkr serio_raw ath5k pcmcia_core iTCO_wdt iTCO_vendor_support lbm_cw_mac80211 snd_seq_dummy lbm_cw_cfg80211 led_class snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq sony_laptop snd_timer snd_seq_device video output snd button battery ac shpchp soundcore snd_page_alloc pci_hotplug intel_agp agpgart ext3 jbd mbcache usb_storage libusual sr_mod cdrom ata_generic usbhid hid sd_mod crc_t10dif sg ata_piix ahci pata_acpi libata scsi_mod dock ohci1394 ieee1394 sky2 ehci_hcd uhci_hcd usb
Dec 10 14:49:35 vaio kernel: ore thermal processor fan fbcon tileblit font bitblit softcursor fuse
Dec 10 14:49:35 vaio kernel: [   64.969080] Pid: 0, comm: swapper Not tainted 2.6.27-9-generic #1
Dec 10 14:49:35 vaio kernel: [   64.969087]  [<c037c4b6>] ? printk+0x1d/0x1f
Dec 10 14:49:35 vaio kernel: [   64.969103]  [<c0131de9>] warn_on_slowpath+0x59/0x90
Dec 10 14:49:35 vaio kernel: [   64.969119]  [<c01dc400>] ? bio_free+0x20/0x50
Dec 10 14:49:35 vaio kernel: [   64.969131]  [<c01acb2e>] ? __slab_free+0xe/0xf0
Dec 10 14:49:35 vaio kernel: [   64.969142]  [<c01870c3>] ? mempool_free_slab+0x13/0x20
Dec 10 14:49:35 vaio kernel: [   64.969152]  [<c019275c>] ? clear_bdi_congested+0xc/0x50
Dec 10 14:49:35 vaio kernel: [   64.969161]  [<c01870c3>] ? mempool_free_slab+0x13/0x20
Dec 10 14:49:35 vaio kernel: [   64.969171]  [<c023f2ef>] ? __freed_request+0xaf/0x120
Dec 10 14:49:35 vaio kernel: [   64.969182]  [<c01acb2e>] ? __slab_free+0xe/0xf0
Dec 10 14:49:35 vaio kernel: [   64.969192]  [<c0118e38>] ? read_hpet+0x8/0x20
Dec 10 14:49:35 vaio kernel: [   64.969203]  [<c014e63b>] ? getnstimeofday+0x4b/0x100
Dec 10 14:49:35 vaio kernel: [   64.969214]  [<c0136976>] ? set_normalized_timespec+0x16/0x90
Dec 10 14:49:35 vaio kernel: [   64.969224]  [<c0151c84>] ? clockevents_program_event+0x14/0x150
Dec 10 14:49:35 vaio kernel: [   64.969234]  [<c014b79e>] ? ktime_get+0x1e/0x40
Dec 10 14:49:35 vaio kernel: [   64.969246]  [<f8c609af>] __lbm_cw_ieee80211_rx+0x19f/0x600 [lbm_cw_mac80211]
Dec 10 14:49:35 vaio kernel: [   64.969276]  [<c02eae1c>] ? skb_put+0xc/0xa0
Dec 10 14:49:35 vaio kernel: [   64.969287]  [<c014a675>] ? hrtimer_reprogram+0x85/0xc0
Dec 10 14:49:35 vaio kernel: [   64.969299]  [<f8c8cc83>] ath5k_tasklet_rx+0x2e3/0x550 [ath5k]
Dec 10 14:49:35 vaio kernel: [   64.969317]  [<c0137258>] tasklet_action+0x78/0x100
Dec 10 14:49:35 vaio kernel: [   64.969326]  [<c0137682>] __do_softirq+0x92/0x120
Dec 10 14:49:35 vaio kernel: [   64.969334]  [<c013776d>] do_softirq+0x5d/0x60
Dec 10 14:49:35 vaio kernel: [   64.969342]  [<c01378e5>] irq_exit+0x55/0x90
Dec 10 14:49:35 vaio kernel: [   64.969349]  [<c0106c1a>] do_IRQ+0x4a/0x80
Dec 10 14:49:35 vaio kernel: [   64.969358]  [<c0105003>] common_interrupt+0x23/0x30
Dec 10 14:49:35 vaio kernel: [   64.969367]  [<c01700d8>] ? __audit_mq_getsetattr+0x68/0xb0
Dec 10 14:49:35 vaio kernel: [   64.969380]  [<f8870800>] ? acpi_idle_enter_bm+0x268/0x2b7 [processor]
Dec 10 14:49:35 vaio kernel: [   64.969398]  [<c02dbf7b>] cpuidle_idle_call+0x7b/0xd0
Dec 10 14:49:35 vaio kernel: [   64.969407]  [<c010288d>] cpu_idle+0x7d/0x140
Dec 10 14:49:35 vaio kernel: [   64.969415]  [<c037a711>] start_secondary+0x9d/0xcc
Dec 10 14:49:35 vaio kernel: [   64.969425]  =======================
Dec 10 14:49:35 vaio kernel: [   64.969430] ---[ end trace 2b328a2701b5fdac ]---
root@vaio:~#

---

### Post by TpyKv on 2008-12-16
Bump :lolflag:

---

### Post by emptyoceans on 2009-02-26
My Ubuntu 8.10 Intrepid has started crashing a lot in the last month. Maybe 6 crashes in February alone. I had a 8.04 install disk that i got from ebay in India but immediately upgraded it to 8.10 as soon as I got online. I have a Toshiba Satellite M200. Most of the issues I have had I have been able to recitfy via this forum but I dunno where to even start diagnosing why its crashing. Its just random. It will work for the whole day and then I'm just doing something normal and the screen will just freeze up. I think I will download 8.10 and install again. Any other suggestions/links would be appreciated.

---

