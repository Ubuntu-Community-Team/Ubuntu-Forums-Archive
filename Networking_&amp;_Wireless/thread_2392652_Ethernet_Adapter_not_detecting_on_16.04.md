---
title: "Ethernet Adapter not detecting on 16.04"
date: 2018-05-23
forum: Networking &amp; Wireless
---

### Post by nrao on 2018-05-23
I have a Ubuntu 16.04 system running the following kernel:
> 4.10.0-28-generic
For some reason, the kernel is unable to load the driver modules required for my Ethernet controller. The lspci output lists only the Wireless card and not my Ethernet controller:
> 00:00.0 Host bridge: Intel Corporation Device 5904 (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Device 5916 (rev 02)
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI (rev 21)
00:17.0 SATA controller: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] (rev 21)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port (rev f1)
00:1f.0 ISA bridge: Intel Corporation Device 9d58 (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Device 9d71 (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
01:00.0 Network controller: Intel Corporation Wireless 3160 (rev 83)


The modules are available in the following path on my machine:
> ls -l /lib/modules/4.10.0-28-generic/kernel/drivers/net/ethernet/realtek
-rw-r--r-- 1 root root  47318 Jul 20  2017 8139cp.ko
-rw-r--r-- 1 root root  64110 Jul 20  2017 8139too.ko
-rw-r--r-- 1 root root  20118 Jul 20  2017 atp.ko
-rw-r--r-- 1 root root 118766 Jul 20  2017 r8169.ko




This problem started today morning when I saw the below logs in the kernel.log:
> May 23 09:24:27 chiphub kernel: [227773.526020] r8169 0000:02:00.0 enp2s0: rtl_counters_cond == 1 (loop: 1000, delay: 10).
May 23 09:25:30 kernel: [227836.525758] r8169 0000:02:00.0 enp2s0: rtl_counters_cond == 1 (loop: 1000, delay: 10).
May 23 09:26:27 kernel: [227893.525154] r8169 0000:02:00.0 enp2s0: rtl_counters_cond == 1 (loop: 1000, delay: 10).
May 23 09:28:27 kernel: [228013.524415] r8169 0000:02:00.0 enp2s0: rtl_counters_cond == 1 (loop: 1000, delay: 10).
May 23 09:28:30 kernel: [228016.524332] r8169 0000:02:00.0 enp2s0: rtl_counters_cond == 1 (loop: 1000, delay: 10).
May 23 09:30:27 kernel: [228133.523508] r8169 0000:02:00.0 enp2s0: rtl_counters_cond == 1 (loop: 1000, delay: 10).
May 23 09:31:30 kernel: [228196.522981] r8169 0000:02:00.0 enp2s0: rtl_counters_cond == 1 (loop: 1000, delay: 10).
May 23 09:32:27 kernel: [228253.522863] r8169 0000:02:00.0 enp2s0: rtl_counters_cond == 1 (loop: 1000, delay: 10).
May 23 09:34:27 kernel: [228373.521750] r8169 0000:02:00.0 enp2s0: rtl_counters_cond == 1 (loop: 1000, delay: 10).
May 23 09:34:30 kernel: [228376.521741] r8169 0000:02:00.0 enp2s0: rtl_counters_cond == 1 (loop: 1000, delay: 10).
May 23 09:34:57 kernel: [228404.405779] NETDEV WATCHDOG: enp2s0 (r8169): transmit queue 0 timed out
May 23 09:34:57 kernel: [228404.405839] ------------[ cut here ]------------
May 23 09:34:57 kernel: [228404.405858] WARNING: CPU: 2 PID: 0 at /build/linux-hwe-k3LMOX/linux-hwe-4.13.0/net/sched/sch_generic.c:316 dev_watchdog+0x225/0x230
May 23 09:34:57 kernel: [228404.405860] Modules linked in: ccm bnep nls_iso8859_1 snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic snd_soc_skl snd_soc_skl_ipc snd_soc_sst_ipc snd_soc_sst_dsp intel_rapl snd_hda_ext_core snd_soc_sst_match x86_pkg_temp_thermal snd_soc_core intel_powerclamp arc4 snd_compress coretemp ac97_bus snd_pcm_dmaengine kvm_intel snd_hda_intel kvm snd_hda_codec snd_hda_core irqbypass snd_hwdep crct10dif_pclmul snd_pcm crc32_pclmul ghash_clmulni_intel snd_seq_midi pcbc snd_seq_midi_event iwlmvm mac80211 snd_rawmidi snd_seq aesni_intel aes_x86_64 crypto_simd glue_helper cryptd snd_seq_device iwlwifi snd_timer intel_cstate intel_rapl_perf snd input_leds soundcore btusb serio_raw cfg80211 topstar_laptop btrtl hci_uart mei_me btbcm mei serdev shpchp intel_pch_thermal btqca sparse_keymap btintel
May 23 09:34:57 chiphub kernel: [228404.405996]  bluetooth ecdh_generic acpi_als acpi_pad mac_hid kfifo_buf intel_lpss_acpi industrialio intel_lpss parport_pc ppdev lp parport autofs4 i915 i2c_algo_bit drm_kms_helper syscopyarea sysfillrect psmouse sysimgblt fb_sys_fops drm r8169 mii ahci libahci video i2c_hid pinctrl_sunrisepoint pinctrl_intel hid
May 23 09:34:57 kernel: [228404.406066] CPU: 2 PID: 0 Comm: swapper/2 Not tainted 4.13.0-38-generic #43~16.04.1-Ubuntu
May 23 09:34:57 kernel: [228404.406069] Hardware name: Default string Default string/Default string, BIOS 5.12 11/25/2017
May 23 09:34:57 kernel: [228404.406074] task: ffff9c55e52daf80 task.stack: ffffafe780d00000
May 23 09:34:57 kernel: [228404.406084] RIP: 0010:dev_watchdog+0x225/0x230
May 23 09:34:57 kernel: [228404.406092] RSP: 0018:ffff9c55eed03e50 EFLAGS: 00010282
May 23 09:34:57 kernel: [228404.406098] RAX: 000000000000003b RBX: 0000000000000000 RCX: 000000000000083f
May 23 09:34:57 kernel: [228404.406101] RDX: 0000000000000000 RSI: 00000000000000f6 RDI: 000000000000083f
May 23 09:34:57 kernel: [228404.406104] RBP: ffff9c55eed03e80 R08: 0000000000000001 R09: 00000000000003d6
May 23 09:34:57 kernel: [228404.406108] R10: 0000000000000000 R11: 00000000000003d6 R12: 0000000000000001
May 23 09:34:57 kernel: [228404.406111] R13: 0000000000000002 R14: ffff9c55e4f8a000 R15: ffff9c55dada5880
May 23 09:34:57 kernel: [228404.406116] FS:  0000000000000000(0000) GS:ffff9c55eed00000(0000) knlGS:0000000000000000
May 23 09:34:57 kernel: [228404.406120] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
May 23 09:34:57 kernel: [228404.406124] CR2: 00007f95480b8000 CR3: 000000011160a002 CR4: 00000000003606e0
May 23 09:34:57 kernel: [228404.406128] Call Trace:
May 23 09:34:57 kernel: [228404.406132]  <IRQ>
May 23 09:34:57 kernel: [228404.406148]  ? qdisc_rcu_free+0x50/0x50
May 23 09:34:57 kernel: [228404.406158]  call_timer_fn+0x37/0x140
May 23 09:34:57 kernel: [228404.406172]  run_timer_softirq+0x1f1/0x460
May 23 09:34:57 kernel: [228404.406180]  ? ktime_get+0x3e/0xa0
May 23 09:34:57 kernel: [228404.406188]  ? lapic_next_deadline+0x26/0x30
May 23 09:34:57 kernel: [228404.406198]  __do_softirq+0xf2/0x287
May 23 09:34:57 kernel: [228404.406209]  irq_exit+0xb6/0xc0
May 23 09:34:57 kernel: [228404.406216]  smp_trace_apic_timer_interrupt+0x74/0xa0
May 23 09:34:57 kernel: [228404.406223]  smp_apic_timer_interrupt+0xe/0x10
May 23 09:34:57 kernel: [228404.406229]  apic_timer_interrupt+0x1af/0x1c0
May 23 09:34:57 kernel: [228404.406234]  </IRQ>
May 23 09:34:57 kernel: [228404.406246] RIP: 0010:cpuidle_enter_state+0x135/0x2f0
May 23 09:34:57 kernel: [228404.406250] RSP: 0018:ffffafe780d03e68 EFLAGS: 00000246 ORIG_RAX: ffffffffffffff10
May 23 09:34:57 kernel: [228404.406258] RAX: 0000000000000000 RBX: 0000000000000008 RCX: 000000000000001f
May 23 09:34:57 kernel: [228404.406263] RDX: 0000000000000000 RSI: 000000002c13bf1e RDI: 0000000000000000
May 23 09:34:57 kernel: [228404.406268] RBP: ffffafe780d03ea0 R08: 000000000001b06b R09: 0000000000000018
May 23 09:34:57 kernel: [228404.406272] R10: ffffafe780d03e38 R11: 000000000000b1cf R12: 0000000000000008
May 23 09:34:57 kernel: [228404.406276] R13: ffff9c55eed2b218 R14: ffffffff99f7a338 R15: 0000cfbb84c7a9a1
May 23 09:34:57 kernel: [228404.406292]  ? cpuidle_enter_state+0x123/0x2f0
May 23 09:34:57 kernel: [228404.406302]  cpuidle_enter+0x17/0x20
May 23 09:34:57 kernel: [228404.406309]  call_cpuidle+0x23/0x40
May 23 09:34:57 kernel: [228404.406315]  do_idle+0x18c/0x1f0
May 23 09:34:57 kernel: [228404.406322]  cpu_startup_entry+0x73/0x80
May 23 09:34:57 kernel: [228404.406331]  start_secondary+0x193/0x1d0
May 23 09:34:57 kernel: [228404.406341]  secondary_startup_64+0x9f/0xa0
May 23 09:34:57 kernel: [228404.406347] Code: 63 8e 60 04 00 00 eb 8f 4c 89 f7 c6 05 7d 8d c0 00 01 e8 af 6a fd ff 89 d9 48 89 c2 4c 89 f6 48 c7 c7 b0 14 d6 99 e8 dc 87 8d ff <0f> ff eb bd 0f 1f 80 00 00 00 00 0f 1f 44 00 00 48 c7 47 08 00
May 23 09:34:57 kernel: [228404.406488] ---[ end trace 882ebacce1292859 ]---


If anyone can help me out with this problem, it would be great! thanks

---

### Post by TheFu on 2018-05-23
Boot from a live-boot flash/DVD Ubuntu 16.04.  Does it work or not?
If not, could the ethernet adaptor have died?

You can try other distros with live boot too, but after 2, if it doesn't work, I'd consider it a dead ethernet.

If it does work with any live-boot distro, then it could be corrupted drivers, incorrect settings, etc.

---

### Post by nrao on 2018-05-23
> **TheFu said:**
> Boot from a live-boot flash/DVD Ubuntu 16.04.  Does it work or not?
If not, could the ethernet adaptor have died?
Its a remote system, so I do not have access to the machine, I only have SSH access which I'm logging in via WiFi.
> 
You can try other distros with live boot too, but after 2, if it doesn't work, I'd consider it a dead ethernet.

Last time the same problem had happened, it was rectified by reinstalling the OS, so i doubt its a dead ethernet.
> 
If it does work with any live-boot distro, then it could be corrupted drivers, incorrect settings, etc.
Is there a way to find out what could be the reason?

Thanks!

---

### Post by rsteinmetz70112 on 2018-05-23
Does "lshw -C network" show the adapter?

---

### Post by TheFu on 2018-05-23
There are remote solutions that allow the OS to be installed.  On most servers it is an $80-$120 option.  Well worth it if there are network issues like this and nobody is competent in the location to be talked through an install enough to get wired ssh access, and nothing else, working.

You could restore from a previously known backup. There are risks doing this.

Looking through all the system logs for reasons why data on disk would become corrupted would be a good idea as well. 

For my professional engagements, we always include a DRAC/IPMI connection that is locked down just to our static IPs. No need to allow the entire world brute-force or trivial hacking access to these interfaces.  IPMI is known to have terrible security, historically. Being paranoid is worth it.

For places getting help for free, they've had to wait until I could get there.  Mom waited 6 weeks, but she was 7 hrs away. I suggested calling a local pro to help. She decided to wait.  Locally, it is usually until the weekend.  

Payment alters my stance about any "emergency" completely. After all, gotta buy that dog food.

---

### Post by nrao on 2018-05-23
> **rsteinmetz70112 said:**
> Does "lshw -C network" show the adapter?

Nope that shows up only my WiFi card:
>   *-network               
       description: Wireless interface
       product: Wireless 3160
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlp1s0
       version: 83
       serial: f4:06:69:d9:7a:e2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.10.0-28-generic firmware=17.608620.0 ip=10.10.1.21 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:df000000-df001fff


---

### Post by chili555 on 2018-05-23
> May 23 09:25:30 kernel: [227836.525758] r8169 0000:02:00.0 enp2s0: rtl_counters_cond == 1 (loop: 1000, delay: 10).
May 23 09:26:27 kernel: [227893.525154] r8169 0000:02:00.0 enp2s0: rtl_counters_cond == 1 (loop: 1000, delay: 10).
May 23 09:28:27 kernel: [228013.524415] r8169 0000:02:00.0 enp2s0: rtl_counters_cond == 1 (loop: 1000, delay: 10).
May 23 09:28:30 kernel: [228016.524332] r8169 0000:02:00.0 enp2s0: rtl_counters_cond == 1 (loop: 1000, delay: 10).
May 23 09:30:27 kernel: [228133.523508] r8169 0000:02:00.0 enp2s0: rtl_counters_cond == 1 (loop: 1000, delay: 10).
May 23 09:31:30 kernel: [228196.522981] r8169 0000:02:00.0 enp2s0: rtl_counters_cond == 1 (loop: 1000, delay: 10).
May 23 09:32:27 kernel: [228253.522863] r8169 0000:02:00.0 enp2s0: rtl_counters_cond == 1 (loop: 1000, delay: 10).
May 23 09:34:27 kernel: [228373.521750] r8169 0000:02:00.0 enp2s0: rtl_counters_cond == 1 (loop: 1000, delay: 10).
May 23 09:34:30 kernel: [228376.521741] r8169 0000:02:00.0 enp2s0: rtl_counters_cond == 1 (loop: 1000, delay: 10).This: [https://patchwork.kernel.org/patch/8388881/](https://patchwork.kernel.org/patch/8388881/) and this: [https://bugzilla.kernel.org/show_bug.cgi?id=107421](https://bugzilla.kernel.org/show_bug.cgi?id=107421) both suggest that the log fills with spam only when the cable is unplugged. I'd assume that it also happens if the cable is bad or the port on the switch is bad. Can you rule these possibilities out?

---

### Post by pdk-knight on 2018-05-24
Same problem. Went through complete recovery procedure, all updates went through and all obsolete stuff deleted.
System booted fine. Next day, nothing. ifconfig shows no ethernet or wireless, nm-connection-editor is totally blank and no network on top bar.
This all started with the auto update around the 20th. Big problem , Very unhappy. 
I'm using 12.04 from the same pc.
This must be happening all over.

---

### Post by pdk-knight on 2018-05-24
Just rebooted and the network is back to normal.
Looks like intermittent problem.
Will check logs

---

### Post by TheFu on 2018-05-24
> **pdk-knight said:**
> Just rebooted and the network is back to normal.
Looks like intermittent problem.
Will check logs

Intermittent problems are almost always hardware issues. Check the ports, cables - both on the NIC and the switch/router.

---

### Post by nrao on 2018-05-29
OK I did a reinstall of the OS, but still the network did not come up.,
as a last resort before junking the motherboard, I opened up the system, unplugged the coin cell battery on the board, plugged it back in and booted the system, everything is working as normal:confused:

I'm not an expert in hardware, but i'm guessing something in the hardware needed a flush inorder to get back to its previous known state, if anyone can explain how/why this issue can occur, I can be better prepared for the next time around.

cheers!

---

### Post by TheFu on 2018-05-29
The act of bumping the computer could have been enough to make a failed connection connect again.  The BIOS battery could impact motherboard stuff, but I've never seen it alter any addon NICs.  Sometimes a BIOS gets corrupted. Usually there is a capacitor which retains the settings for when the battery is replaced. All sorts of bad things can happen with a nearly dead or dead BIOS battery.  I've seen them fail after 1 yr and last 13+ yrs. Most are cheap enough to make that the first thing replaced if the BIOS seems odd at any point.

If this is happening enough that there is an issue like you are posting, I would have setup a remote DRAC/IPMI card or at least installed a $25 Intel PRO/1000 NIC. The hardware has to support the remote protocols, so a real server is required.  Some high-end desktops might include it too.

---

### Post by nrao on 2018-05-29
> **TheFu said:**
> The act of bumping the computer could have been enough to make a failed connection connect again.  The BIOS battery could impact motherboard stuff, but I've never seen it alter any addon NICs.  Sometimes a BIOS gets corrupted. Usually there is a capacitor which retains the settings for when the battery is replaced. All sorts of bad things can happen with a nearly dead or dead BIOS battery.  I've seen them fail after 1 yr and last 13+ yrs. Most are cheap enough to make that the first thing replaced if the BIOS seems odd at any point.

If this is happening enough that there is an issue like you are posting, I would have setup a remote DRAC/IPMI card or at least installed a $25 Intel PRO/1000 NIC. The hardware has to support the remote protocols, so a real server is required.  Some high-end desktops might include it too.

The DRAC/IPMI solution is quite expensive to be honest, and costs almost as much as the PC itself, but more importantly, how do I find out what is the root cause for this, is there any precautions I can take at the OS level to ensure the system does not go into this state again.

---

### Post by TheFu on 2018-05-29
> **nrao said:**
> The DRAC/IPMI solution is quite expensive to be honest, and costs almost as much as the PC itself, but more importantly, how do I find out what is the root cause for this, is there any precautions I can take at the OS level to ensure the system does not go into this state again.

I guess it depends where you are in the world and how much the system is really worth to a business whether it is "expensive" or not.  For me, having to visit a client location once post-install will cost more than having the remote access setup and working.   It doesn't make sense NOT to include that capability.

At a minimum, I would have installed a new Intel PRO/1000, as stated already.  These are important enough to have a spare available, IMHO.
I've seen cracked motherboards impact networking. We switched from the built-in NIC to a card NIC and it was fixed.  A few months later, the HDD controller started acting funny ... that was enough to insist on a warranty replacement. Sometimes the hassle isn't worth it until it is.

I have no idea what the issue could be.  If a business can live without the system for 4 days, then it clearly isn't that important.  After 1 day, I would have said they needed to invoke their DR plan for the system, which would be built based on RTO/RPO information.

---

### Post by pdk-knight on 2018-06-04
This morning Monday June 4 ifconfig showed zero ethernet or wireless.
No network icon.
restarted networking and network-manager and all now working.
Not sure which service made things right, will check next time it happens

---

### Post by pdk-knight on 2018-06-13
Wednesday 13th June
No network icon.
ifconfig showed only the lo information
ifconfig -a showed all physical devices but no assigned addresses.
The network icon was not displayed.
restarted the network-manager and all is now working.
For me the problem is that for some reason the network manger fails to start once in a while.
Peter

---

### Post by nrao on 2018-06-22
The NIC is connected using a straight cable directly to a Cisco Unmanaged switch, could that be causing the device driver to crash? Will using a crossover cable solve the issue i'm wondering.:confused:

---

