---
title: "Network connection stops working when external drive is used as Time Machine backup"
date: 2018-10-23
forum: Networking &amp; Wireless
---

### Post by jrbeaton2 on 2018-10-23
**TLDR:** When I try to use an external drive on my Ubuntu 18.04 machine as a Time Machine backup destination for my Mac laptop, the backup runs correctly for 3-4 minutes then the (wired) network on the server just stops working.  I need to turn the machine off and back on to restore the network.  Using the drives in other ways (read/write, as Plex server) works fine.

**The gory details:**

I've got a NEXBOX T9 Mini PC Z8300 that I use as a Plex server and file server on my home network.  I just installed 18.04 on it using the "minimal" (something like that) choice. I then installed a few more items:


[LIST]
[*]net-tools
[*]openssh-server
[*]vim
[*]vino
[*]exfat-fuse
[*]exfat-utils
[*]vsftpd
[/LIST]

I've got two external exFAT-formatted drives connected, one for media and one for backup.  I'd like to use the backup drive as a destination for Time Machine on my Mac, so I installed the Samba 4.8.6 from source per the instructions here to get "the support necessary for macOS to 'see' an SMB shared folder as capable of being a network Time Machine share":

[https://kirb.me/2018/03/24/using-samba-as-a-time-machine-network-server.html](https://kirb.me/2018/03/24/using-samba-as-a-time-machine-network-server.html)

The drives and the Samba sharing work fine on the Ubuntu machine for normal reading and writing.  However, when I start a Time Machine backup from my Mac, it connects and the backup runs correctly for 3-4 minutes, then it stops because the wired network on the Ubuntu machine just stops working.

I ran a test on the Ubuntu machine where I tailed syslog and the Samba logs, ran top, and pinged another machine on the local network then started the Time Machine backup.  From the Mac, I also connected to the server via SSH and pinged another machine on the local network.  The backup ran for 3-4 minutes then hung while the ping on the Mac just stopped (because the SSH connection was lost).  On the Ubuntu machine:

1. The ping ran normally until the network stopped working, and it got a "Network host unreachable" (or something similar).
2. The Samba logs showed nothing at all during the whole process.  
3. top showed that the machine went from about 2GB free (out of 4GB) down to about 400KB when the network stopped working.  
4. In syslog, it showed this at about the time the network stopped working:

```
Oct 22 10:48:14 krusty kernel: [  383.643395] r8152 1-3:1.0 enxc44eac7f442d: Rx status -71
Oct 22 10:49:28 krusty kernel: [  457.190461] r8152 1-3:1.0 enxc44eac7f442d: Rx status -71
Oct 22 10:49:32 krusty kernel: [  460.974565] r8152 1-3:1.0 enxc44eac7f442d: Tx status -71
Oct 22 10:49:40 krusty kernel: [  468.972691] ------------[ cut here ]------------
Oct 22 10:49:40 krusty kernel: [  468.972707] NETDEV WATCHDOG: enxc44eac7f442d (r8152): transmit queue 0 timed out
Oct 22 10:49:40 krusty kernel: [  468.972810] WARNING: CPU: 0 PID: 0 at /build/linux-60XibS/linux-4.15.0/net/sched/sch_generic.c:323 dev_watchdog+0x221/0x230
Oct 22 10:49:40 krusty kernel: [  468.972816] Modules linked in: nls_iso8859_1 snd_soc_sst_byt_cht_es8316 axp288_adc axp20x_pek axp288_charger axp288_fuel_gauge industrialio extcon_axp288 gpio_keys input_leds intel_rapl cdc_ether intel_powerclamp coretemp usbnet kvm_intel r8152 mii kvm irqbypass punit_atom_debug crct10dif_pclmul crc32_pclmul ghash_clmulni_intel brcmfmac pcbc brcmutil snd_hdmi_lpe_audio cfg80211 mei_txe mei aesni_intel lpc_ich processor_thermal_device intel_soc_dts_iosf aes_x86_64 crypto_simd glue_helper cryptd intel_cstate snd_intel_sst_acpi snd_intel_sst_core snd_soc_sst_atom_hifi2_platform snd_soc_acpi snd_soc_acpi_intel_match snd_seq_midi snd_seq_midi_event snd_rawmidi snd_soc_es8316 snd_soc_core snd_compress ac97_bus intel_hid dw_dmac snd_pcm_dmaengine dw_dmac_core snd_seq axp20x_i2c sparse_keymap snd_pcm axp20x
Oct 22 10:49:40 krusty kernel: [  468.973124]  snd_seq_device snd_timer snd 8250_dw spi_pxa2xx_platform soundcore pwm_lpss_platform pwm_lpss mac_hid int3400_thermal int3403_thermal int340x_thermal_zone acpi_thermal_rel int3406_thermal intel_int0002_vgpio soc_button_array acpi_pad sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 ses enclosure scsi_transport_sas hid_apple hid_generic usbhid hid uas usb_storage mmc_block i915 i2c_algo_bit drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops drm video sdhci_acpi sdhci
Oct 22 10:49:40 krusty kernel: [  468.973373] CPU: 0 PID: 0 Comm: swapper/0 Not tainted 4.15.0-29-generic #31-Ubuntu
Oct 22 10:49:40 krusty kernel: [  468.973380] Hardware name: N/A CherryTrail/Type2 - Board Product Name, BIOS YT11.6W4x64.D003 05/17/2016
Oct 22 10:49:40 krusty kernel: [  468.973392] RIP: 0010:dev_watchdog+0x221/0x230
Oct 22 10:49:40 krusty kernel: [  468.973400] RSP: 0018:ffff88967fc03e58 EFLAGS: 00010286
Oct 22 10:49:40 krusty kernel: [  468.973412] RAX: 0000000000000000 RBX: 0000000000000000 RCX: 0000000000000006
Oct 22 10:49:40 krusty kernel: [  468.973418] RDX: 0000000000000007 RSI: 0000000000000092 RDI: ffff88967fc16490
Oct 22 10:49:40 krusty kernel: [  468.973427] RBP: ffff88967fc03e88 R08: 0000000000000001 R09: 0000000000000353
Oct 22 10:49:40 krusty kernel: [  468.973433] R10: ffff88967fc03ee0 R11: 0000000000000000 R12: 0000000000000001
Oct 22 10:49:40 krusty kernel: [  468.973440] R13: ffff889675ca9000 R14: ffff889675ca9478 R15: ffff88966fee0a80
Oct 22 10:49:40 krusty kernel: [  468.973452] FS:  0000000000000000(0000) GS:ffff88967fc00000(0000) knlGS:0000000000000000
Oct 22 10:49:40 krusty kernel: [  468.973459] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Oct 22 10:49:40 krusty kernel: [  468.973465] CR2: 00007f3ddd444000 CR3: 000000002360a000 CR4: 00000000001006f0
Oct 22 10:49:40 krusty kernel: [  468.973473] Call Trace:
Oct 22 10:49:40 krusty kernel: [  468.973484]  <IRQ>
Oct 22 10:49:40 krusty kernel: [  468.973507]  ? dev_deactivate_queue.constprop.33+0x60/0x60
Oct 22 10:49:40 krusty kernel: [  468.973524]  call_timer_fn+0x30/0x130
Oct 22 10:49:40 krusty kernel: [  468.973542]  run_timer_softirq+0x3fb/0x450
Oct 22 10:49:40 krusty kernel: [  468.973554]  ? ktime_get+0x43/0xa0
Oct 22 10:49:40 krusty kernel: [  468.973569]  ? lapic_next_deadline+0x26/0x30
Oct 22 10:49:40 krusty kernel: [  468.973588]  __do_softirq+0xdf/0x2b2
Oct 22 10:49:40 krusty kernel: [  468.973605]  irq_exit+0xb6/0xc0
Oct 22 10:49:40 krusty kernel: [  468.973618]  smp_apic_timer_interrupt+0x71/0x130
Oct 22 10:49:40 krusty kernel: [  468.973632]  apic_timer_interrupt+0x84/0x90
Oct 22 10:49:40 krusty kernel: [  468.973638]  </IRQ>
Oct 22 10:49:40 krusty kernel: [  468.973652] RIP: 0010:cpuidle_enter_state+0xa7/0x2f0
Oct 22 10:49:40 krusty kernel: [  468.973658] RSP: 0018:ffffffff9fc03e10 EFLAGS: 00000246 ORIG_RAX: ffffffffffffff11
Oct 22 10:49:40 krusty kernel: [  468.973670] RAX: ffff88967fc22880 RBX: 0000006d30f24e7b RCX: 000000000000001f
Oct 22 10:49:40 krusty kernel: [  468.973676] RDX: 0000006d30f24e7b RSI: fffffff906eb7451 RDI: 0000000000000000
Oct 22 10:49:40 krusty kernel: [  468.973684] RBP: ffffffff9fc03e50 R08: 00000000ffffffff R09: 00000000000007be
Oct 22 10:49:40 krusty kernel: [  468.973691] R10: ffffffff9fc03de0 R11: 00000000000007c0 R12: ffff88967fc2c300
Oct 22 10:49:40 krusty kernel: [  468.973697] R13: 0000000000000003 R14: ffffffff9fd71d58 R15: 0000000000000000
Oct 22 10:49:40 krusty kernel: [  468.973717]  cpuidle_enter+0x17/0x20
Oct 22 10:49:40 krusty kernel: [  468.973733]  call_cpuidle+0x23/0x40
Oct 22 10:49:40 krusty kernel: [  468.973743]  do_idle+0x18c/0x1f0
Oct 22 10:49:40 krusty kernel: [  468.973756]  cpu_startup_entry+0x73/0x80
Oct 22 10:49:40 krusty kernel: [  468.973771]  rest_init+0xae/0xb0
Oct 22 10:49:40 krusty kernel: [  468.973787]  start_kernel+0x4dc/0x4fd
Oct 22 10:49:40 krusty kernel: [  468.973800]  x86_64_start_reservations+0x24/0x26
Oct 22 10:49:40 krusty kernel: [  468.973811]  x86_64_start_kernel+0x74/0x77
Oct 22 10:49:40 krusty kernel: [  468.973826]  secondary_startup_64+0xa5/0xb0
Oct 22 10:49:40 krusty kernel: [  468.973835] Code: 38 00 49 63 4e e8 eb 92 4c 89 ef c6 05 27 36 d9 00 01 e8 03 38 fd ff 89 d9 48 89 c2 4c 89 ee 48 c7 c7 a8 76 99 9f e8 df f3 80 ff <0f> 0b eb c0 90 66 2e 0f 1f 84 00 00 00 00 00 0f 1f 44 00 00 55
Oct 22 10:49:40 krusty kernel: [  468.974062] ---[ end trace fe5c6b5585a5b186 ]---
Oct 22 10:49:40 krusty kernel: [  468.974082] r8152 1-3:1.0 enxc44eac7f442d: Tx timeout
Oct 22 10:49:42 krusty kernel: [  471.053007] r8152 1-3:1.0 enxc44eac7f442d: Tx status -2
Oct 22 10:49:42 krusty kernel: [  471.053216] r8152 1-3:1.0 enxc44eac7f442d: Tx status -2
Oct 22 10:49:42 krusty kernel: [  471.053309] r8152 1-3:1.0 enxc44eac7f442d: Tx status -2
Oct 22 10:49:42 krusty kernel: [  471.053405] r8152 1-3:1.0 enxc44eac7f442d: Tx status -2
Oct 22 10:49:45 krusty kernel: [  473.836707] r8152 1-3:1.0 enxc44eac7f442d: Tx timeout
Oct 22 10:49:50 krusty kernel: [  478.956717] r8152 1-3:1.0 enxc44eac7f442d: Tx timeout
Oct 22 10:49:55 krusty kernel: [  484.076886] r8152 1-3:1.0 enxc44eac7f442d: Tx timeout
Oct 22 10:50:01 krusty kernel: [  489.964723] r8152 1-3:1.0 enxc44eac7f442d: Tx timeout
Oct 22 10:50:06 krusty kernel: [  495.084878] r8152 1-3:1.0 enxc44eac7f442d: Tx timeout
Oct 22 10:50:08 krusty systemd-timesyncd[633]: Timed out waiting for reply from 91.189.91.157:123 (ntp.ubuntu.com).
Oct 22 10:50:12 krusty kernel: [  500.972448] r8152 1-3:1.0 enxc44eac7f442d: Tx timeout
Oct 22 10:50:17 krusty kernel: [  505.836732] r8152 1-3:1.0 enxc44eac7f442d: Tx timeout
Oct 22 10:50:18 krusty systemd-timesyncd[633]: Timed out waiting for reply from 91.189.89.198:123 (ntp.ubuntu.com).
Oct 22 10:50:22 krusty kernel: [  510.956727] r8152 1-3:1.0 enxc44eac7f442d: Tx timeout
Oct 22 10:50:27 krusty kernel: [  516.076873] r8152 1-3:1.0 enxc44eac7f442d: Tx timeout
Oct 22 10:50:28 krusty systemd-timesyncd[633]: Timed out waiting for reply from 91.189.94.4:123 (ntp.ubuntu.com).
Oct 22 10:50:33 krusty kernel: [  521.964758] r8152 1-3:1.0 enxc44eac7f442d: Tx timeout
Oct 22 10:50:38 krusty kernel: [  527.084795] r8152 1-3:1.0 enxc44eac7f442d: Tx timeout
Oct 22 10:50:44 krusty kernel: [  532.972735] r8152 1-3:1.0 enxc44eac7f442d: Tx timeout
Oct 22 10:50:49 krusty kernel: [  537.836749] r8152 1-3:1.0 enxc44eac7f442d: Tx timeout
Oct 22 10:50:54 krusty kernel: [  542.956735] r8152 1-3:1.0 enxc44eac7f442d: Tx timeout
Oct 22 10:50:59 krusty kernel: [  548.076493] r8152 1-3:1.0 enxc44eac7f442d: Tx timeout
Oct 22 10:51:05 krusty kernel: [  553.964361] r8152 1-3:1.0 enxc44eac7f442d: Tx timeout
Oct 22 10:51:10 krusty kernel: [  559.084742] r8152 1-3:1.0 enxc44eac7f442d: Tx timeout
Oct 22 10:51:16 krusty kernel: [  564.976819] r8152 1-3:1.0 enxc44eac7f442d: Tx timeout
Oct 22 10:51:21 krusty kernel: [  569.836751] r8152 1-3:1.0 enxc44eac7f442d: Tx timeout
Oct 22 10:51:26 krusty kernel: [  574.956732] r8152 1-3:1.0 enxc44eac7f442d: Tx timeout
Oct 22 10:51:31 krusty kernel: [  580.076731] r8152 1-3:1.0 enxc44eac7f442d: Tx timeout
Oct 22 10:51:37 krusty kernel: [  585.964740] r8152 1-3:1.0 enxc44eac7f442d: Tx timeout
Oct 22 10:51:42 krusty kernel: [  591.084744] r8152 1-3:1.0 enxc44eac7f442d: Tx timeout
Oct 22 10:51:48 krusty kernel: [  596.972769] r8152 1-3:1.0 enxc44eac7f442d: Tx timeout
Oct 22 10:51:53 krusty kernel: [  601.836336] r8152 1-3:1.0 enxc44eac7f442d: Tx timeout
Oct 22 10:51:58 krusty kernel: [  606.956863] r8152 1-3:1.0 enxc44eac7f442d: Tx timeout
Oct 22 10:52:03 krusty kernel: [  612.077066] r8152 1-3:1.0 enxc44eac7f442d: Tx timeout
Oct 22 10:52:09 krusty kernel: [  617.964739] r8152 1-3:1.0 enxc44eac7f442d: Tx timeout
Oct 22 10:52:14 krusty kernel: [  623.084742] r8152 1-3:1.0 enxc44eac7f442d: Tx timeout
Oct 22 10:52:20 krusty kernel: [  628.972758] r8152 1-3:1.0 enxc44eac7f442d: Tx timeout
Oct 22 10:52:25 krusty kernel: [  633.836835] r8152 1-3:1.0 enxc44eac7f442d: Tx timeout
Oct 22 10:52:30 krusty kernel: [  638.956746] r8152 1-3:1.0 enxc44eac7f442d: Tx timeout
Oct 22 10:52:35 krusty kernel: [  644.076742] r8152 1-3:1.0 enxc44eac7f442d: Tx timeout
Oct 22 10:52:41 krusty kernel: [  649.964759] r8152 1-3:1.0 enxc44eac7f442d: Tx timeout
Oct 22 10:52:42 krusty NetworkManager[744]: <info>  [1540219962.2553] connectivity: (enxc44eac7f442d) timed out
Oct 22 10:52:42 krusty NetworkManager[744]: <info>  [1540219962.2558] manager: NetworkManager state is now CONNECTED_SITE
Oct 22 10:52:42 krusty whoopsie[856]: [10:52:42] offline
Oct 22 10:52:42 krusty dbus-daemon[732]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.15' (uid=0 pid=744 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
Oct 22 10:52:42 krusty systemd[1]: Starting Network Manager Script Dispatcher Service...
Oct 22 10:52:42 krusty dbus-daemon[732]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Oct 22 10:52:42 krusty systemd[1]: Started Network Manager Script Dispatcher Service.
Oct 22 10:52:42 krusty nm-dispatcher: req:1 'connectivity-change': new request (1 scripts)
Oct 22 10:52:42 krusty nm-dispatcher: req:1 'connectivity-change': start running ordered scripts...
Oct 22 10:52:46 krusty kernel: [  655.084741] r8152 1-3:1.0 enxc44eac7f442d: Tx timeout
Oct 22 10:52:52 krusty kernel: [  660.972766] r8152 1-3:1.0 enxc44eac7f442d: Tx timeout
```


The Time Machine share portion of my smb.conf looks like this (per the article above):

```

[TimeMachine]
  comment = Time Machine Backups
  path = /mnt/Backups/TimeMachine
  browseable = yes
  writeable = yes
  create mask = 0600
  directory mask = 0700
  spotlight = yes
  vfs objects = catia fruit streams_xattr
  fruit:aapl = yes
  fruit:time machine = yes

```

The network is managed via Ubuntu's Settings -> Network UI and is set to use a static IP.

In the test I did above, the little Network Manager icon in the upper-right was still there, but had a little "x" on it after a delay of 10-15 minutes.  Using the toggle to turn the network off then back on doesn't change anything.  Turning the machine off then back on restores the network to normal.

A previous time when I wasn't on the machine looking at it, the Time Machine backup failed; and I didn't go to the machine until a few hours had passed.  When I finally looked at it, the Network Manager icon was missing; and the wired network section was completely missing from Settings -> Network.  I ran "reboot" from the command line multiple times, and the wired network (and the section in Settings -> Network) never reappeared.  It did come back after turning the machine off then back on.

So...  

Help!  Does anybody have any idea what's going on here?  I can pretty reliably recreate this, so is there any other information I can provide that would be helpful?

Also...

I previously had Lubuntu (16, I think) installed on this machine with the packaged Samba along with Netatalk and Avahi daemon to allow it to be used with Time Machine, and it did pretty-much the same thing, but I just gave up and never really debugged it.


Thanks!
JRB

---

### Post by TheFu on 2018-10-23
I know ABSOLUTELY NOTHING about Time Machine or Apple stuff. A quick google says that TimeMachine isn't supported on ExFAT file systems, so choosing to use an unsupported file system for important backups seems like a bad idea to me.

exFAT should only be used for devices that cannot be used with any other file system.  Perhaps for cameras.  ExFAT is extremely limited in multiple ways, like file size limitations and the allowed number of files in a directory. There are others. It doesn't allow POSIX permissions which are very important for backups.

If the only method that some storage is to be accessible is via Samba, then using a Linux file system like ext4 is much better to host samba shares.  I find it amazing that samba even allows any file system to be used which doesn't support normal Unix permissions including ACLs and extended attributes.

I saw something about 18.04 not having a specific version of Samba that does something helpful for Time Machine.  I think v4.8.x was the hope, but 4.7.x was the reality.

Hopefully, someone else with specific knowledge will respond and completely invalidate my anti-exFAT bias.

---

### Post by jrbeaton2 on 2018-10-23
Thanks for the reply.

I'm using exFAT on this drive because I'm switching it between Mac, Windows, and Linux systems.  I believe the issue with Time Machine not supporting backups on exFAT drives is only if you're directly plugging an external drive into the Mac and trying to use it that way.  If you try, Time Machine immediately says it won't work and that the drive would need to be formatted.  I'm my case, it actually does start to use it successfully (until the network goes away).

Thanks,
JRB

---

### Post by TheFu on 2018-10-23
NTFS wold be 100x better than exFAT for SSD or spinning disks.

Anyways, I'll step back and look at the network stuff only.  I'm aware of Intel PRO/1000 NICs made at 1 specific plant in Mexico having a problem that certain SIP traffic could lock up the card due to a driver failure. That was about 10 yrs ago.  Looks like you have a Realtek NIC using the r8152 driver.   A little google seemed to confirm that driver has shown issues. I didn't look to hard.  **sudo lshw -C network** would help.

Are you on the latest version?  What version are you on?  Does the changelog between them address the issues you experience?

If you just want this fixed and aren't adverse to spending $25, getting an Intel PRO/1000 NIC will get you only the industry standard and pretty much all the networking issues will go away.  Also, the ASIC on the Intel NICs does more of the work, so you'll have more CPU available.

---

### Post by jrbeaton2 on 2018-10-23
Here's that output:

```
$ sudo lshw -C network
  *-network
       description: Ethernet interface
       physical id: 3
       logical name: enxc44eac7f442d
       serial: c4:4e:ac:7f:44:2d
       size: 100Mbit/s
       capacity: 100Mbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8152 driverversion=v1.09.9 duplex=full ip=192.168.1.27 link=yes multicast=yes port=MII speed=100Mbit/s

```

Incidentally, I ran that command after my network went away (and the wired network section was completely missing from Settings -> Network), and it returned nothing at all.
 
> 
Are you on the latest version? What version are you on? Does the changelog between them address the issues you experience?


```

$ modinfo r8152
filename:       /lib/modules/4.15.0-29-generic/kernel/drivers/net/usb/r8152.ko
version:        **v1.09.9**
license:        GPL
description:    Realtek RTL8152/RTL8153 Based USB Ethernet Adapters
author:         Realtek linux nic maintainers <nic_swsd@realtek.com>
srcversion:     90A533E29C5FE0DC53CA025
alias:          usb:v2357p0601d*dc*dsc*dp*ic02isc06ip00in*
alias:          usb:v2357p0601d*dc*dsc*dp*icFFisc*ip*in*
alias:          usb:v0955p09FFd*dc*dsc*dp*ic02isc06ip00in*
alias:          usb:v0955p09FFd*dc*dsc*dp*icFFisc*ip*in*
alias:          usb:v13B1p0041d*dc*dsc*dp*ic02isc06ip00in*
alias:          usb:v13B1p0041d*dc*dsc*dp*icFFisc*ip*in*
alias:          usb:v17EFp7214d*dc*dsc*dp*ic02isc06ip00in*
alias:          usb:v17EFp7214d*dc*dsc*dp*icFFisc*ip*in*
alias:          usb:v17EFp720Cd*dc*dsc*dp*ic02isc06ip00in*
alias:          usb:v17EFp720Cd*dc*dsc*dp*icFFisc*ip*in*
alias:          usb:v17EFp7205d*dc*dsc*dp*ic02isc06ip00in*
alias:          usb:v17EFp7205d*dc*dsc*dp*icFFisc*ip*in*
alias:          usb:v17EFp3069d*dc*dsc*dp*ic02isc06ip00in*
alias:          usb:v17EFp3069d*dc*dsc*dp*icFFisc*ip*in*
alias:          usb:v17EFp3062d*dc*dsc*dp*ic02isc06ip00in*
alias:          usb:v17EFp3062d*dc*dsc*dp*icFFisc*ip*in*
alias:          usb:v17EFp304Fd*dc*dsc*dp*ic02isc06ip00in*
alias:          usb:v17EFp304Fd*dc*dsc*dp*icFFisc*ip*in*
alias:          usb:v04E8pA101d*dc*dsc*dp*ic02isc06ip00in*
alias:          usb:v04E8pA101d*dc*dsc*dp*icFFisc*ip*in*
alias:          usb:v045Ep07C6d*dc*dsc*dp*ic02isc06ip00in*
alias:          usb:v045Ep07C6d*dc*dsc*dp*icFFisc*ip*in*
alias:          usb:v045Ep07ABd*dc*dsc*dp*ic02isc06ip00in*
alias:          usb:v045Ep07ABd*dc*dsc*dp*icFFisc*ip*in*
alias:          usb:v0BDAp8153d*dc*dsc*dp*ic02isc06ip00in*
alias:          usb:v0BDAp8153d*dc*dsc*dp*icFFisc*ip*in*
alias:          usb:v0BDAp8152d*dc*dsc*dp*ic02isc06ip00in*
alias:          usb:v0BDAp8152d*dc*dsc*dp*icFFisc*ip*in*
alias:          usb:v0BDAp8050d*dc*dsc*dp*ic02isc06ip00in*
alias:          usb:v0BDAp8050d*dc*dsc*dp*icFFisc*ip*in*
depends:        mii
retpoline:      Y
intree:         Y
name:           r8152
vermagic:       4.15.0-29-generic SMP mod_unload
signat:         PKCS#7
signer:
sig_key:
sig_hashalgo:   md4

$ cat /proc/version
Linux version **4.15**.0-29-generic (buildd@lgw01-amd64-057) (gcc version 7.3.0 (Ubuntu 7.3.0-16ubuntu3)) #31-Ubuntu SMP Tue Jul 17 15:39:52 UTC 2018

```

So, I've got v1.09.9.  On Realtek's site, there's a version 2.10.0 for RTL8152B(N) for "LINUX driver for kernel up to 4.15": 

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=55&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=55&Level=5&Conn=4&DownTypeID=3&GetDown=false)

Is that the correct driver?  Would you recommend updating?  I can't find a changelog for the driver.

> If you just want this fixed and aren't adverse to spending $25, getting an Intel PRO/1000 NIC will get you only the industry standard...

This is just a little mini PC, so replacing the network card like that isn't really possible.

---

### Post by TheFu on 2018-10-23
The lshw output is missing the most important date.  The configuration line should be longer with the driver AND version. 

With 100base-tx, you might want to force that speed. Don't use autonegotiation. I remember that 10/100 NICs didn't always handle autonegotiation correctly and had to be forced to a specific speed. There were lots of issues with different NICs and different switch/router ports.  But I haven't used 10/100 networking since around 2006, so maybe things are fine now?

I asked the questions to lead you down a path that would hopefully provide answers.  The source code for the driver is here: [https://github.com/torvalds/linux/blob/master/drivers/net/usb/r8152.c](https://github.com/torvalds/linux/blob/master/drivers/net/usb/r8152.c) with the change description for each commit.

---

### Post by jrbeaton2 on 2018-10-23
I've updated the lshw output above (it was a bad cut-and-paste job).  This was the full last line:

```
configuration: autonegotiation=on broadcast=yes driver=r8152 driverversion=v1.09.9 duplex=full ip=192.168.1.27 link=yes multicast=yes port=MII speed=100Mbit/s
```

I don't really know anything about drivers.  Are you suggesting that I pull the latest driver code from Github kernel repo and compile that?  That code appears to make it identify itself as "v1.09.9",  same as I've got.

```

/* Information for net-next */
#define NETNEXT_VERSION		"09"


/* Information for net */
#define NET_VERSION		"9"


#define DRIVER_VERSION		"v1." NETNEXT_VERSION "." NET_VERSION

```

Is that better than downloading the 2.10.0 driver code from the Realtek site?

---

### Post by TheFu on 2018-10-24
Sorry, I cannot say which is better.

If it were me, I'd try these things:
* disable autonegotiation. Force 100 base-tx - ethtool will allow that, if options to the driver don't.

If that doesn't solve it, 
* disable/unplug the current NIC and replace it. 

Over the years, I've learned that having to manually install drivers to make something work isn't worth the hassle, since it becomes something that has to be redone over and over and over every time there is a new kernel. The same with devices like printers and scanners.  If the support isn't easy and built-in, I return the device or sell it and get one that does work easily.

But stubborn people can do amazing things, like make an OS, get commands for it working, create a driver subsystem that allows millions of different configurations. It is up to you.

---

