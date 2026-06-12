---
title: "Heads-Up: newest Gutsy kernel (2.6.22-14.47) and nfs4"
date: 2007-12-19
forum: Networking &amp; Wireless
---

### Post by bouchecl on 2007-12-19
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/bugs/148600](https://bugs.launchpad.net/bugs/148600) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi all, 

I had problems this morning booting my Gutsy workstation after the most recent kernel update (2.6.22-14.47-generic, released on 12/18/2007). After a bit of testing and the obligatory hunt for logfiles, I've noticed a kernel oops while trying to load the NFS shares, as seen in this snippet taken from /var/log/kern.log:

 ```
Dec 19 09:17:27 apollon kernel: [   24.824000] bridge-eth0: enabling the bridge
Dec 19 09:17:27 apollon kernel: [   24.824000] bridge-eth0: up
Dec 19 09:17:27 apollon kernel: [   24.824000] bridge-eth0: already up
Dec 19 09:17:27 apollon kernel: [   24.824000] bridge-eth0: attached
Dec 19 09:17:30 apollon kernel: [   27.800000] NET: Registered protocol family 17
Dec 19 09:17:34 apollon kernel: [   31.980000] BUG: unable to handle kernel NULL pointer dereference at virtual address 00000038
Dec 19 09:17:34 apollon kernel: [   31.980000]  printing eip:
Dec 19 09:17:34 apollon kernel: [   31.980000] f8c3a040
Dec 19 09:17:34 apollon kernel: [   31.980000] *pde = 00000000
Dec 19 09:17:34 apollon kernel: [   31.980000] Oops: 0000 [#1]
Dec 19 09:17:34 apollon kernel: [   31.980000] SMP 
Dec 19 09:17:34 apollon kernel: [   31.980000] Modules linked in: af_packet vmnet(P) vmblock(P) vmmon(P) ppdev ipv6 cpufreq_userspace cpufreq_powersave cpufreq_stats cpufreq_ondemand freq_table cpufreq_conservative sbs ac dock video container button battery nfs lockd sunrpc parport_pc lp parport snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device nvidia(P) xpad snd k8temp serio_raw agpgart i2c_nforce2 pcspkr psmouse soundcore snd_page_alloc shpchp pci_hotplug i2c_core evdev ext3 jbd mbcache sg sr_mod sd_mod cdrom usbhid hid sata_nv amd74xx ide_core ata_generic forcedeth libata scsi_mod ehci_hcd ohci_hcd usbcore thermal processor fan fuse apparmor commoncap
Dec 19 09:17:34 apollon kernel: [   31.980000] CPU:    0
Dec 19 09:17:34 apollon kernel: [   31.980000] EIP:    0060:[<f8c3a040>]    Tainted: P       VLI
Dec 19 09:17:34 apollon kernel: [   31.980000] EFLAGS: 00010206   (2.6.22-14-generic #1)
Dec 19 09:17:34 apollon kernel: [   31.980000] EIP is at nfs_fhget+0xd0/0x3e0 [nfs]
Dec 19 09:17:34 apollon kernel: [   31.980000] eax: 00000000   ebx: 00000000   ecx: f72f0674   edx: 00004180
Dec 19 09:17:34 apollon kernel: [   31.980000] esi: f72f0600   edi: f6b49bd4   ebp: f6b17128   esp: f6b49b88
Dec 19 09:17:34 apollon kernel: [   31.980000] ds: 007b   es: 007b   fs: 00d8  gs: 0033  ss: 0068
Dec 19 09:17:34 apollon kernel: [   31.980000] Process mount.nfs4 (pid: 6094, ti=f6b48000 task=f717c530 task.ti=f6b48000)
Dec 19 09:17:34 apollon kernel: [   31.980000] Stack: f8c39f10 f6b49bac 00000020 c0133462 c03d9de0 f6b17000 fffefa43 c02bd89d 
Dec 19 09:17:34 apollon kernel: [   31.980000]        00000282 f6b49c66 f6b49bd4 f6b49bd4 f72f0600 f6b49c64 f6b49d1e f8c388d7 
Dec 19 09:17:34 apollon kernel: [   31.980000]        f717c6f0 c1f07000 f72f0200 00000002 00000000 00000000 00000000 00000000 
```

The workstation works fine when NFS shares are not loaded. The bug has been reported by another person on Launchpad ([https://bugs.launchpad.net/bugs/148600](https://bugs.launchpad.net/bugs/148600)). My advice would be to wait a bit before installing the newest kernel package.

---

### Post by bouchecl on 2007-12-19
The problem is discussed in another thread: [http://ubuntuforums.org/showthread.php?p=3979308](http://ubuntuforums.org/showthread.php?p=3979308)

---

