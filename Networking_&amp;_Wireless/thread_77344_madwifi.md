---
title: "madwifi"
date: 2005-10-16
forum: Networking &amp; Wireless
---

### Post by gdcondor on 2005-10-16
Hi

I'm fighting with my wireless card (netgear 311T) which is supported by madwifi
when i was under hoary the module included in linux-restricted was too old and I managed to get it work installing madwifi from the CVS
but now (breezy) the one contained in linux-restricted seems to be ok but it doesn't work and in dmesg i have (sorry it's a bit long but i don't know which part is interesting...) :

```
[4297668.899000] ath_pci: Unknown symbol ieee80211_ioctl_siwrate
[4297668.899000] ath_pci: Unknown symbol ath_rate_tx_complete
[4297668.899000] ath_pci: Unknown symbol ieee80211_encap
[4297668.900000] ath_pci: Unknown symbol ieee80211_input
[4297668.900000] ath_pci: Unknown symbol ieee80211_ioctl_siwap
[4297668.900000] ath_pci: Unknown symbol ieee80211_ifattach
[4297668.900000] ath_pci: Unknown symbol _ath_hal_attach
[4297668.900000] ath_pci: Unknown symbol if_printf
[4297668.900000] ath_pci: Unknown symbol ieee80211_sysctl_register
[4297668.900000] ath_pci: Unknown symbol ieee80211_ioctl_siwencode
[4297668.900000] ath_pci: Unknown symbol ieee80211_beacon_update
[4297668.900000] ath_pci: Unknown symbol ieee80211_ioctl_setmlme
[4297668.900000] ath_pci: Unknown symbol ieee80211_ioctl_setoptie
[4297668.901000] ath_pci: Unknown symbol ieee80211_ioctl_giwmode
[4297668.901000] ath_pci: Unknown symbol ieee80211_find_rxnode
[4297668.901000] ath_pci: Unknown symbol ath_rate_attach
[4297668.901000] ath_pci: Unknown symbol ether_sprintf
[4297668.901000] ath_pci: Unknown symbol ieee80211_ifdetach
[4297668.901000] ath_pci: Unknown symbol ieee80211_free_node
[4297668.901000] ath_pci: Unknown symbol ieee80211_ioctl_siwsens
[4297668.901000] ath_pci: Unknown symbol ath_rate_newassoc
[4297668.901000] ath_pci: Unknown symbol ath_hal_computetxtime
[4297668.901000] ath_pci: Unknown symbol ieee80211_notify_michael_failure
[4297668.901000] ath_pci: Unknown symbol ieee80211_ioctl_chanlist
[4297668.902000] ath_pci: Unknown symbol ieee80211_ioctl_getparam
[4297668.902000] ath_pci: Unknown symbol ath_rate_dynamic_sysctl_register
[4297668.902000] ath_pci: Unknown symbol ieee80211_dump_pkt
[4297668.902000] ath_pci: Unknown symbol ieee80211_ioctl_giwrate
[4297668.902000] ath_pci: Unknown symbol ath_hal_mhz2ieee
[4297668.902000] ath_pci: Unknown symbol ieee80211_ioctl_siwrts
[4297668.902000] ath_pci: Unknown symbol ieee80211_ioctl_giwname
[4297668.902000] ath_pci: Unknown symbol ath_hal_detach
[4297668.902000] ath_pci: Unknown symbol ieee80211_cipher_none
[4297668.903000] ath_pci: Unknown symbol ieee80211_ioctl_setparam
[4297668.903000] ath_pci: Unknown symbol ieee80211_ioctl_siwpower
[4297668.903000] ath_pci: Unknown symbol ieee80211_ioctl_giwsens
[4297668.903000] ath_pci: Unknown symbol ieee80211_media_change
[4297668.903000] ath_pci: Unknown symbol ieee80211_ioctl_giwfreq
[4297668.903000] ath_pci: Unknown symbol ieee80211_beacon_alloc
[4297668.903000] ath_pci: Unknown symbol ieee80211_ioctl_siwfrag
[4297668.903000] ath_pci: Unknown symbol ieee80211_ioctl_giwap
[4297668.903000] ath_pci: Unknown symbol ieee80211_ioctl_siwfreq
[4297668.903000] ath_pci: Unknown symbol ieee80211_ibss_merge
[4297668.903000] ath_pci: Unknown symbol ieee80211_ioctl_giwpower
[4297668.904000] ath_pci: Unknown symbol ieee80211_mhz2ieee
[4297668.904000] ath_pci: Unknown symbol ath_hal_probe
[4297668.904000] ath_pci: Unknown symbol ieee80211_ioctl_giwrange
[4297668.904000] ath_pci: Unknown symbol ieee80211_ioctl_giwretry
[4297668.904000] ath_pci: Unknown symbol ieee80211_ioctl_giwnickn
[4297668.904000] ath_pci: Unknown symbol ieee80211_ioctl_giwrts
[4297668.904000] ath_pci: Unknown symbol ieee80211_iw_getstats
[4297668.904000] ath_pci: Unknown symbol ieee80211_ioctl_addmac
[4297668.904000] ath_pci: Unknown symbol ath_rate_node_cleanup
[4297668.905000] ath_pci: Unknown symbol ath_rate_detach
[4297668.905000] ath_pci: Unknown symbol ieee80211_ioctl_giwfrag
[4297668.905000] ath_pci: Unknown symbol ieee80211_wme_acnames
[4297668.905000] ath_pci: Unknown symbol ieee80211_vlan_kill_vid
[4297668.905000] ath_pci: Unknown symbol ieee80211_ioctl_giwencode
[4297668.905000] ath_pci: Unknown symbol ieee80211_next_scan
[4297668.905000] ath_pci: Unknown symbol ieee80211_media_init
[4297668.905000] ath_pci: Unknown symbol ieee80211_ioctl_iwsetup
[4297668.905000] ath_pci: Unknown symbol ieee80211_ioctl
[4297668.905000] ath_pci: Unknown symbol ieee80211_ioctl_delmac
[4297668.905000] ath_pci: Unknown symbol ieee80211_classify
[4297668.905000] ath_pci: Unknown symbol ieee80211_media_status
[4297668.906000] ath_pci: Unknown symbol ieee80211_announce
[4297668.906000] ath_pci: Unknown symbol ieee80211_ioctl_setkey
[4297668.906000] ath_pci: Unknown symbol ieee80211_ioctl_iwaplist
[4297668.906000] ath_pci: Unknown symbol ieee80211_ioctl_delkey
[4297668.906000] ath_pci: Unknown symbol ieee80211_ioctl_siwtxpow
[4297668.906000] ath_pci: Unknown symbol ieee80211_chan2ieee
[4297668.906000] ath_pci: Unknown symbol ieee80211_ioctl_siwretry
[4297668.906000] ath_pci: Unknown symbol ieee80211_ioctl_siwnickn
[4297668.906000] ath_pci: Unknown symbol ieee80211_state_name
[4297668.906000] ath_pci: Unknown symbol ath_rate_node_init
[4297668.906000] ath_pci: Unknown symbol ieee80211_ioctl_siwscan
[4297668.907000] ath_pci: Unknown symbol ieee80211_ioctl_siwmode
[4297668.907000] ath_pci: Unknown symbol ieee80211_ioctl_getoptie
[4297668.907000] ath_pci: Unknown symbol ath_rate_findrate
[4297668.907000] ath_pci: Unknown symbol ieee80211_ioctl_giwessid
[4297668.907000] ath_pci: Unknown symbol ath_hal_init_channels
[4297668.907000] ath_pci: Unknown symbol ieee80211_ioctl_giwscan
[4297668.907000] ath_pci: Unknown symbol ieee80211_crypto_encap
[4297668.907000] ath_pci: Unknown symbol ieee80211_vlan_register
[4297668.907000] ath_pci: Unknown symbol ieee80211_ioctl_siwessid
[4297668.907000] ath_pci: Unknown symbol ieee80211_chan2mode
[4297668.907000] ath_pci: Unknown symbol ieee80211_getrssi
[4297668.907000] ath_pci: Unknown symbol ieee80211_pwrsave
[4297668.908000] ath_pci: Unknown symbol ieee80211_find_txnode
[4297668.908000] ath_pci: Unknown symbol ath_rate_newstate
[4297668.908000] ath_pci: Unknown symbol ath_rate_setupxtxdesc
[4297668.908000] ath_pci: Unknown symbol ieee80211_ioctl_giwtxpow
[4297668.908000] ath_pci: Unknown symbol ath_hal_getwirelessmodes
[4297695.316000] ath_hal: module license 'Proprietary' taints kernel.
[4297695.319000] ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
[4297695.363000] wlan: 0.8.6.0 (EXPERIMENTAL)
[4297695.372000] ath_rate_sample: 1.2
[4297695.385000] ath_pci: 0.9.6.0 (EXPERIMENTAL)
[4297695.391000] PCI: Enabling device 0000:07:00.0 (0000 -> 0002)
[4297695.391000] ACPI: PCI Interrupt 0000:07:00.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4297696.143000] Build date: Oct 11 2005
[4297696.143000] Debugging version (IEEE80211)
[4297696.143000] ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[4297696.143000] ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[4297696.143000] ath0: turboG rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[4297696.143000] ath0: H/W encryption support: WEP AES AES_CCM TKIP
[4297696.143000] ath0: mac 7.9 phy 4.5 radio 5.6
[4297696.143000] ath0: Use hw queue 1 for WME_AC_BE traffic
[4297696.143000] ath0: Use hw queue 0 for WME_AC_BK traffic
[4297696.143000] ath0: Use hw queue 2 for WME_AC_VI traffic
[4297696.143000] ath0: Use hw queue 3 for WME_AC_VO traffic
[4297696.143000] ath0: Use hw queue 8 for CAB traffic
[4297696.143000] ath0: Use hw queue 9 for beacons
[4297696.143000] Debugging version (ATH)
[4297696.143000] ath0: Atheros 5212: mem=0x11000000, irq=11
[4297696.585000] Unable to handle kernel paging request at virtual address 0000ffff
[4297696.585000]  printing eip:
[4297696.585000] d143ccf8
[4297696.585000] *pde = 00000000
[4297696.585000] Oops: 0000 [#1]
[4297696.585000] Modules linked in: ath_pci ath_rate_sample wlan ath_hal binfmt_misc rfcomm l2cap bluetooth speedstep_ich speedstep_lib cpufreq_powersave cpufreq_stats cpufreq_userspace cpufreq_ondemand cpufreq_conservative freq_table pcmcia tc1100_wmi video battery container i2c_acpi_ec i2c_core button pcc_acpi sony_acpi ac dev_acpi hotkey ipv6 af_packet floppy pcspkr rtc ohci1394 yenta_socket rsrc_nonstatic pcmcia_core snd_intel8x0 snd_ac97_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd soundcore snd_page_alloc tpm_nsc tpm_atmel tpm hw_random pci_hotplug intel_agp agpgart nls_iso8859_1 vfat fat nls_cp437 ntfs dm_mod tsdev evdev sr_mod sbp2 scsi_mod ieee1394 psmouse mousedev parport_pc lp parport md reiserfs thermal processor fan 3c59x mii uhci_hcd usbcore ide_cd cdrom ide_disk ide_generic piix ide_core unix vesafb capability commoncap vgastate softcursor cfbimgblt cfbfillrect cfbcopyarea fbcon tileblit font bitblit
[4297696.585000] CPU:    0
[4297696.585000] EIP:    0060:[<d143ccf8>]    Tainted: P      VLI
[4297696.585000] EFLAGS: 00010246   (2.6.12-9-686)
[4297696.585000] EIP is at read_ap_result+0x198/0x5b8 [wlan]
[4297696.585000] eax: 0000ffff   ebx: c67f7e84   ecx: 00000000   edx: cd211000
[4297696.585000] esi: cd2110f5   edi: c684f020   ebp: cd2110f5   esp: c67f7d64
[4297696.585000] ds: 007b   es: 007b   ss: 0068
[4297696.585000] Process iwlist (pid: 22982, threadinfo=c67f6000 task=cce17520)
[4297696.585000] Stack: c013e515 cf2c98ec 00000007 cfa1900d cffd32fc 00000000 cb684630 c6850000
[4297696.585000]        c67f7e40 c684f020 00000008 00000020 4352bdba 209d1348 c67f7dcc c011ce06
[4297696.585000]        c67f7dcc 4352bdba 209d1348 3b9aca00 cf2c9848 cf2c988c c67f7dcc c016db71
[4297696.585000] Call Trace:
[4297696.585000]  [<c013e515>] __do_page_cache_readahead+0x60/0x100
[4297696.585000]  [<c011ce06>] current_fs_time+0x4d/0x5b
[4297696.585000]  [<c016db71>] update_atime+0x48/0xbd
[4297696.585000]  [<c013c1a5>] buffered_rmqueue+0x146/0x1bf
[4297696.585000]  [<c013c5eb>] __alloc_pages+0x301/0x3e6
[4297696.585000]  [<d1437e56>] ieee80211_iterate_nodes+0x3b/0x66 [wlan]
[4297696.585000]  [<d143e801>] ieee80211_ioctl_giwscan+0x5c/0xa8 [wlan]
[4297696.585000]  [<d143cb60>] read_ap_result+0x0/0x5b8 [wlan]
[4297696.585000]  [<c023f8d6>] wireless_process_ioctl+0x5c0/0x7e7
[4297696.585000]  [<d145a1ad>] ath_ioctl_giwscan+0x0/0x15 [ath_pci]
[4297696.585000]  [<c0235d18>] dev_ioctl+0x104/0x2c0
[4297696.585000]  [<c022b3c7>] sock_ioctl+0xd1/0x239
[4297696.585000]  [<c01661cd>] do_ioctl+0x6d/0x7a
[4297696.585000]  [<c0166326>] vfs_ioctl+0x65/0x1d4
[4297696.585000]  [<c016651a>] sys_ioctl+0x85/0x93
[4297696.585000]  [<c0102df7>] sysenter_past_esp+0x54/0x75
[4297696.585000] Code: 24 1c 0f 87 ec 02 00 00 8b 84 24 e4 00 00 00 89 50 10 c7 03 00 00 00 00 66 c7 43 02 05 8b 8b 94 24 e8 00 00 00 8b 82 28 01 00 00 <0f> b7 00 69 c0 a0 86 01 00 89 43 04 66 c7 43 08 01 00 8b 8c 24
[4297696.585000]


```

if someone has an idea... i REALLY need my wlan card to work :((

thanks !
-- 
GdCondor

---

### Post by hil on 2006-02-03
That happened to me with my compiled kernel. Madwifi works with the stock kernel but not compiled kernel.

---

### Post by Lambert on 2006-02-03
Basically something is wrong with the driver and it's not installed properly or there are some duplicate files which are being read. Did you upgrade from hoary to breezy via dist-upgrade or fresh install?

You are going to have to uninstall the driver (complete linux-restricted-module package) and reinstall it. Before reinstalling, search for any left over files that didn't get removed and delete those.

---

### Post by hil on 2006-02-06
I installed Breezy , not from upgrade. I downloaded the madwifi-old and installed with the 2.6.12 kernel source. It can work well now. madwifi-ng did not work for me. I got ioctl errors and I created ap for my card.

---

