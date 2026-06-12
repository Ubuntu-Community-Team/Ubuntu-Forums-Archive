---
title: "Problem with acerhk after kernel upgrade"
date: 2007-05-31
forum: Networking &amp; Wireless
---

### Post by charshep on 2007-05-31
After upgrading from 2.6.20-15 to 2.6.20-16 i'm no longer able to modprobe the acerhk module. I've just switched from Gentoo to Ubuntu Feisty 7.04 so I'm not sure of the best way to fix this but I would have thought that a manual recompile of the driver would be unnecessary since it wasn't required after the original Ubuntu installation.

Here's the output from dmesg:


[  156.652000] acerhk: Could not find model string, will assume type 200 series
[  156.652000] BUG: unable to handle kernel paging request at virtual address 00
009610
[  156.652000]  printing eip:
[  156.652000] c00f0000
[  156.652000] *pde = 00000000
[  156.652000] Oops: 0002 [#1]
[  156.652000] SMP 
[  156.652000] Modules linked in: acerhk ipv6 ppdev i915 drm speedstep_centrino 
cpufreq_powersave cpufreq_userspace cpufreq_ondemand cpufreq_conservative cpufre
q_stats freq_table pcc_acpi sony_acpi dev_acpi tc1100_wmi button dock ac sbs bat
tery video container i2c_ec i2c_core asus_acpi backlight sbp2 lp fuse snd_intel8
x0 snd_ac97_codec wlan_wep pcmcia ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd
_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_t
imer snd_seq_device wbsd joydev mmc_core snd soundcore wlan_scan_sta irda crc_cc
itt parport_pc parport pcspkr yenta_socket rsrc_nonstatic pcmcia_core ath_rate_s
ample ath_pci wlan snd_page_alloc ath_hal(P) psmouse serio_raw iTCO_wdt iTCO_ven
dor_support af_packet shpchp pci_hotplug intel_agp agpgart tsdev evdev ext3 jbd 
mbcache ide_cd cdrom ide_disk 8139too ata_generic libata scsi_mod piix 8139cp mi
i ohci1394 ieee1394 generic ehci_hcd uhci_hcd usbcore thermal processor fan fbco
n tileblit font bitblit softcursor vesafb capability commoncap
[  156.652000] CPU:    0
[  156.652000] EIP:    0060:[<c00f0000>]    Tainted: P      VLI
[  156.652000] EFLAGS: 00210086   (2.6.20-16-generic #2)
[  156.652000] EIP is at 0xc00f0000
[  156.652000] eax: 00009610   ebx: 0000051c   ecx: 0000001f   edx: c013aae8
[  156.652000] esi: dfdfbc80   edi: def72a90   ebp: dfe84400   esp: d9a39e6c
[  156.652000] ds: 007b   es: 007b   ss: 0068
[  156.652000] Process modprobe (pid: 5219, ti=d9a38000 task=def76560 task.ti=d9
a38000)
[  156.652000] Stack: dfdf609b d9a39eb0 dfdfc3df dfdfbc80 0000001f d9a39e94 0000
0000 d9a39eb0 
[  156.652000]        00000000 c00f0000 00000000 dfdfbc80 dfdfc3df 0000001f dfdc
d93d d9a39eb0 
[  156.652000]        def72a90 00009610 0000051c 0000001f c013aae8 def72a90 dfdf
bc80 dfdfbc80 
[  156.652000] Call Trace:
[  156.652000]  [<dfdf609b>] call_bios_52x+0x4b/0x80 [acerhk]
[  156.652000]  [<dfdcd93d>] acerhk_init+0x8fd/0x1bd2 [acerhk]
[  156.652000]  [<c013aae8>] kthread_stop+0x68/0x70
[  156.652000]  [<c014422d>] sys_init_module+0x15d/0x1ba0
[  156.652000]  [<c0107a5d>] sys_mmap2+0xcd/0xd0
[  156.652000]  [<c01031f0>] sysenter_past_esp+0x69/0xa9
[  156.652000]  =======================
[  156.652000] Code: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
 ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ee <00> 00 00
 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 
[  156.652000] EIP: [<c00f0000>] 0xc00f0000 SS:ESP 0068:d9a39e6c
[  156.652000]  <6>eth0: link up, 100Mbps, full-duplex, lpa 0x45E1

---

### Post by charshep on 2007-05-31
Wow was I barking up the wrong tree. If you have certain models of laptops (powerpro 5:14 from powernotebooks in my case) you sometimes need to add some extra parameters to modprobe.:

sudo modprobe acerhk poll=0 force_series=290

And then you need to do this to actually enable the led switch:

echo "on" > /proc/driver/acerhk/wirelessled 

The thing is you often don't need to do this even after shutting down the machine, as long as it remains plugged in. I hadn't unplugged it in ages and forgotten all about these steps.

---

