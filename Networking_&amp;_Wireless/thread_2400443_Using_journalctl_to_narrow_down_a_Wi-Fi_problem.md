---
title: "Using journalctl to narrow down a Wi-Fi problem?"
date: 2018-09-06
forum: Networking &amp; Wireless
---

### Post by blankcat on 2018-09-06
Greetings, I am relatively new to Linux in general, and now I am trying to figure out a problem with my Wi-Fi card. I wanted to narrow down the problem using journalctl, but right now I think I am not getting the whole log needed. 

Is there a way to specify the journal to display messages directly related to the wireless adapter, while it's working, because at some point it just stops randomly. 

I tried looking through the man page, but so far I am failing to understand what parameters I should put in.

---

### Post by westie457 on 2018-09-06
Is ```
journalctl | grep wifi
```any use to you?

---

### Post by blankcat on 2018-09-06
The log puls out data from around 10 days ago until today, but I don't see something, that could show me the problem.

When I run journalctl --follow, I get to see when the interface goes down.
The installation is a fresh xubuntu 18.04 on an old Lenovo T61.

Not sure if I should spam this here, but part of the log (right until the adapter stops), looks like this:
```
: > kernel: wls3:  Failed check-sdata-in-driver check, flags: 0x4
> kernel: WARNING: CPU: 1 PID: 27908 at /build/linux-wuhukg/linux-4.15.0/net/mac80211/driver-ops.h:18 drv_remove_interface+0xfe/0x110 [mac80211]
> kernel: Modules linked in: nls_iso8859_1 pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) ccm rfcomm bnep snd_hda_codec_analog snd_hda_codec_generic snd_hda_intel snd_hda_codec arc4 snd_hda_core snd_hwdep joydev input_leds serio_raw pcmcia kvm_intel iwl3945 snd_pcm iwlegacy kvm irqbypass wmi_bmof thinkpad_acpi yenta_socket pcmcia_rsrc snd_seq_midi snd_seq_midi_event mac80211 nvram pcmcia_core snd_rawmidi btusb btrtl btbcm btintel snd_seq lpc_ich cfg80211 bluetooth snd_seq_device snd_timer shpchp ecdh_generic mei_me mei sch_fq_codel snd mac_hid soundcore coretemp parport_pc ppdev lp parport ip_tables x_tables autofs4 ums_realtek uas usb_storage hid_logitech_hidpp hid_logitech_dj usbhid hid nouveau mxm_wmi i2c_algo_bit ttm drm_kms_helper psmouse syscopyarea sysfillrect sysimgblt fb_sys_fops
> kernel:  drm e1000e ahci libahci ptp pps_core pata_acpi wmi video
> kernel: CPU: 1 PID: 27908 Comm: kworker/1:5 Tainted: G        W  OE    4.15.0-32-generic #35-Ubuntu
> kernel: Hardware name: LENOVO 8889W1T/8889W1T, BIOS 7LETC7WW (2.27 ) 04/08/2010
> kernel: Workqueue: events_freezable ieee80211_restart_work [mac80211]
> kernel: RIP: 0010:drv_remove_interface+0xfe/0x110 [mac80211]
> kernel: RSP: 0018:ffffb91dc37cbc38 EFLAGS: 00010282
> kernel: RAX: 0000000000000000 RBX: ffff992575018cd8 RCX: 0000000000000006
> kernel: RDX: 0000000000000007 RSI: 0000000000000092 RDI: ffff99257bd16490
> kernel: RBP: ffffb91dc37cbc50 R08: 0000000000000001 R09: 00000000000008ff
> kernel: R10: 00000000000003dd R11: 0000000000000000 R12: ffff992575900760
> kernel: R13: ffff992575900ee8 R14: ffff992575900760 R15: ffff992575019380
> kernel: FS:  0000000000000000(0000) GS:ffff99257bd00000(0000) knlGS:0000000000000000
> kernel: CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
> kernel: CR2: 00007fd9c402b1b8 CR3: 000000013415c000 CR4: 00000000000006e0
> kernel: Call Trace:
> kernel:  ieee80211_do_stop+0x4e1/0x7f0 [mac80211]
> kernel:  ? qdisc_reset+0x2b/0x70
> kernel:  ieee80211_stop+0x1a/0x20 [mac80211]
> kernel:  __dev_close_many+0xa5/0x110
> kernel:  dev_close_many+0x8c/0x140
> kernel:  dev_close.part.88+0x4a/0x70
> kernel:  dev_close+0x19/0x20
> kernel:  cfg80211_shutdown_all_interfaces+0x77/0xc0 [cfg80211]
> kernel:  ieee80211_handle_reconfig_failure+0x98/0xb0 [mac80211]
> kernel:  ieee80211_reconfig+0x236/0xfc0 [mac80211]
> kernel:  ieee80211_restart_work+0x9e/0xd0 [mac80211]
> kernel:  process_one_work+0x1de/0x410
> kernel:  worker_thread+0x32/0x410
> kernel:  kthread+0x121/0x140
> kernel:  ? process_one_work+0x410/0x410
> kernel:  ? kthread_create_worker_on_cpu+0x70/0x70
> kernel:  ? do_syscall_64+0x73/0x130
> kernel:  ? SyS_exit_group+0x14/0x20
> kernel:  ret_from_fork+0x35/0x40
> kernel: Code: c0 75 e8 5b 41 5c 41 5d 5d c3 48 8b b3 f8 03 00 00 48 81 c3 18 04 00 00 48 c7 c7 b0 f9 6d c0 48 85 f6 48 0f 44 f3 e8 f2 44 42 f1 <0f> 0b 5b 41 5c 41 5d 5d c3 66 0f 1f 84 00 00 00 00 00 66 66 66 
> kernel: ---[ end trace 92bad855eadc42da ]---
> kernel: WARNING: CPU: 1 PID: 27908 at /build/linux-wuhukg/linux-4.15.0/net/mac80211/driver-ops.c:39 drv_stop+0xed/0x100 [mac80211]
> kernel: Modules linked in: nls_iso8859_1 pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) ccm rfcomm bnep snd_hda_codec_analog snd_hda_codec_generic snd_hda_intel snd_hda_codec arc4 snd_hda_core snd_hwdep joydev input_leds serio_raw pcmcia kvm_intel iwl3945 snd_pcm iwlegacy kvm irqbypass wmi_bmof thinkpad_acpi yenta_socket pcmcia_rsrc snd_seq_midi snd_seq_midi_event mac80211 nvram pcmcia_core snd_rawmidi btusb btrtl btbcm btintel snd_seq lpc_ich cfg80211 bluetooth snd_seq_device snd_timer shpchp ecdh_generic mei_me mei sch_fq_codel snd mac_hid soundcore coretemp parport_pc ppdev lp parport ip_tables x_tables autofs4 ums_realtek uas usb_storage hid_logitech_hidpp hid_logitech_dj usbhid hid nouveau mxm_wmi i2c_algo_bit ttm drm_kms_helper psmouse syscopyarea sysfillrect sysimgblt fb_sys_fops
> kernel:  drm e1000e ahci libahci ptp pps_core pata_acpi wmi video
> kernel: CPU: 1 PID: 27908 Comm: kworker/1:5 Tainted: G        W  OE    4.15.0-32-generic #35-Ubuntu
> kernel: Hardware name: LENOVO 8889W1T/8889W1T, BIOS 7LETC7WW (2.27 ) 04/08/2010
> kernel: Workqueue: events_freezable ieee80211_restart_work [mac80211]
> kernel: RIP: 0010:drv_stop+0xed/0x100 [mac80211]
> kernel: RSP: 0018:ffffb91dc37cbc28 EFLAGS: 00010246
> kernel: RAX: 0000000000000000 RBX: ffff992575900760 RCX: 0000000000000000
> kernel: RDX: ffff9924db2ad600 RSI: 0000000000000286 RDI: ffff992575900760
> kernel: RBP: ffffb91dc37cbc38 R08: 0000000000000000 R09: 0000000000000000
> kernel: R10: ffffb91dc37cbc48 R11: 0000000000000000 R12: ffff992575900ff0
> kernel: R13: ffff992575900ee8 R14: ffff992575900760 R15: ffff992575019380
> kernel: FS:  0000000000000000(0000) GS:ffff99257bd00000(0000) knlGS:0000000000000000
> kernel: CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
> kernel: CR2: 00007fd9c402b1b8 CR3: 000000013415c000 CR4: 00000000000006e0
> kernel: Call Trace:
> kernel:  ieee80211_stop_device+0x43/0x50 [mac80211]
> kernel:  ieee80211_do_stop+0x4cb/0x7f0 [mac80211]
> kernel:  ? qdisc_reset+0x2b/0x70
> kernel:  ieee80211_stop+0x1a/0x20 [mac80211]
> kernel:  __dev_close_many+0xa5/0x110
> kernel:  dev_close_many+0x8c/0x140
> kernel:  dev_close.part.88+0x4a/0x70
> kernel:  dev_close+0x19/0x20
> kernel:  cfg80211_shutdown_all_interfaces+0x77/0xc0 [cfg80211]
> kernel:  ieee80211_handle_reconfig_failure+0x98/0xb0 [mac80211]
> kernel:  ieee80211_reconfig+0x236/0xfc0 [mac80211]
> kernel:  ieee80211_restart_work+0x9e/0xd0 [mac80211]
> kernel:  process_one_work+0x1de/0x410
> kernel:  worker_thread+0x32/0x410
> kernel:  kthread+0x121/0x140
> kernel:  ? process_one_work+0x410/0x410
> kernel:  ? kthread_create_worker_on_cpu+0x70/0x70
> kernel:  ? do_syscall_64+0x73/0x130
> kernel:  ? SyS_exit_group+0x14/0x20
> kernel:  ret_from_fork+0x35/0x40
> kernel: Code: 54 09 00 4d 85 e4 74 1e 49 8b 04 24 49 8b 7c 24 08 49 83 c4 18 48 89 de e8 e1 b7 f9 f1 49 8b 04 24 48 85 c0 75 e6 e9 51 ff ff ff <0f> 0b 5b 41 5c 5d c3 66 90 66 2e 0f 1f 84 00 00 00 00 00 66 66 
> kernel: ---[ end trace 92bad855eadc42db ]---
> whoopsie[1236]: [22:17:35] Cannot reach: [https://daisy.ubuntu.com](https://daisy.ubuntu.com)
> whoopsie[1236]: [22:17:35] offline
> NetworkManager[688]: <warn>  [1534965455.0099] sup-iface[0x5573fd5b8830,wls3]: connection disconnected (reason -3)
> wpa_supplicant[1954]: wls3: CTRL-EVENT-DISCONNECTED bssid=8c:0d:76:04:be:c6 reason=3 locally_generated=1
> NetworkManager[688]: <info>  [1534965455.0148] manager: NetworkManager state is now CONNECTED_SITE
> avahi-daemon[657]: Interface wls3.IPv6 no longer relevant for mDNS.
> NetworkManager[688]: <info>  [1534965455.0328] device (wls3): supplicant interface state: completed -> disabled
> avahi-daemon[657]: Leaving mDNS multicast group on interface wls3.IPv6 with address fe80::65f7:5e56:ac5:942a.
> systemd[1]: Starting Network Manager Script Dispatcher Service...
> avahi-daemon[657]: Interface wls3.IPv4 no longer relevant for mDNS.
> systemd[1]: Started Network Manager Script Dispatcher Service.
> avahi-daemon[657]: Leaving mDNS multicast group on interface wls3.IPv4 with address 192.168.6.101.
> avahi-daemon[657]: Withdrawing address record for fe80::65f7:5e56:ac5:942a on wls3.
> dhclient[26906]: receive_packet failed on wls3: Network is down
```

---

### Post by blankcat on 2018-09-09
> **westie457 said:**
> Is ```
journalctl | grep wifi
```any use to you?

Alright, seems like 20 years wasted on Windows have taken it's toll. I've been through the help pages and experimented a bit, but it seems that I do not get how this thing works and any attempt to put the log into a file, while it's being generated, fails. I want to dump it all, because when I run the command, when it stops I can't see the start in the terminal window. It's being cut somewhere for obvious reasons, not visible to me :D

If somewhere exists something, where I can read more about this, then I would be happy to go there, and then return with a more educated question. Because running in circles is not my thing, and it takes too much time imho.

---

### Post by chili555 on 2018-09-09
You can scroll through the logs using the arrow keys with:```
journalctl | grep wifi | less
```I doubt that 'wifi' is the parameter to search for, however. I might suggest the identity of the wireless interface, perhaps wlp3s0 or some such. Find yours with:```
iwconfig
```Therefore:```
journalctl | grep wlp | less
```Or search for the driver in question; yours is iwl3945:```
journalctl | grep iwl | less
```Get out of 'less' with q.

You could also check:```
cat /var/log/syslog | grep wlp | less
```Your readings, so far, don't yet suggest the cause of the crash.

---

