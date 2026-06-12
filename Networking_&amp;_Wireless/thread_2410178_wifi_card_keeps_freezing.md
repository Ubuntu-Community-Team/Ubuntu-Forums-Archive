---
title: "wifi card keeps freezing"
date: 2019-01-11
forum: Networking &amp; Wireless
---

### Post by necb on 2019-01-11
I have a Compex WLE600VX as my wifi card and it will periodically stall.  The icon on my system tray shows that it is connected to my router and all other devices on my router work fine and are able to connect to the internet.  I can fix the problem by clicking on my wifi icon and disconnecting and then reconnecting.  I'd like to figure out why this is happening and permanently fix it though.  Dmesg doesn't show anything interesting.  This is my dmesg log when one of these freezes happened.  You can see right at 2236 where I had to manually reconnect in order to get internet.

```
[    3.660722] snd_hda_codec_realtek hdaudioC0D2:    mono: mono_out=0x0
[    3.660723] snd_hda_codec_realtek hdaudioC0D2:    dig-out=0x11/0x1e
[    3.660724] snd_hda_codec_realtek hdaudioC0D2:    inputs:
[    3.660726] snd_hda_codec_realtek hdaudioC0D2:      Front Mic=0x19
[    3.660727] snd_hda_codec_realtek hdaudioC0D2:      Rear Mic=0x18
[    3.660728] snd_hda_codec_realtek hdaudioC0D2:      Line=0x1a
[    3.674961] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[    3.675016] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[    3.675068] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[    3.675121] input: HDA Intel PCH Line Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[    3.675177] input: HDA Intel PCH Line Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[    3.675223] input: HDA Intel PCH Line Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[    3.675256] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[    3.707259] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/pre-cal-pci-0000:03:00.0.bin failed with error -2
[    3.707265] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/cal-pci-0000:03:00.0.bin failed with error -2
[    3.708009] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA988X/hw2.0/firmware-6.bin failed with error -2
[    3.709441] ath10k_pci 0000:03:00.0: qca988x hw2.0 target 0x4100016c chip_id 0x043222ff sub 0000:0000
[    3.709442] ath10k_pci 0000:03:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[    3.709569] ath10k_pci 0000:03:00.0: firmware ver 10.2.4-1.0-00037 api 5 features no-p2p,raw-mode,mfp,allows-mesh-bcast crc32 a4a52adb
[    3.742733] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA988X/hw2.0/board-2.bin failed with error -2
[    3.742858] ath10k_pci 0000:03:00.0: board_file api 1 bmi_id N/A crc32 bebc7c08
[    4.432658] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input12
[    4.432709] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input13
[    4.432755] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input14
[    4.454435] resource sanity check: requesting [mem 0x000c0000-0x000fffff], which spans more than PCI Bus 0000:00 [mem 0x000d0000-0x000d3fff window]
[    4.454550] caller os_map_kernel_space.part.7+0xda/0x120 [nvidia] mapping multiple BARs
[    4.463703] random: crng init done
[    4.463705] random: 7 urandom warning(s) missed due to ratelimiting
[    4.658722] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: errors=remount-ro
[    4.712616] audit: type=1400 audit(1547250461.395:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-oopslash" pid=831 comm="apparmor_parser"
[    4.712881] audit: type=1400 audit(1547250461.395:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/man" pid=830 comm="apparmor_parser"
[    4.712884] audit: type=1400 audit(1547250461.395:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="man_filter" pid=830 comm="apparmor_parser"
[    4.712887] audit: type=1400 audit(1547250461.395:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="man_groff" pid=830 comm="apparmor_parser"
[    4.713669] audit: type=1400 audit(1547250461.395:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-xpdfimport" pid=834 comm="apparmor_parser"
[    4.713980] audit: type=1400 audit(1547250461.395:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/snapd/snap-confine" pid=835 comm="apparmor_parser"
[    4.713990] audit: type=1400 audit(1547250461.395:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/snapd/snap-confine//mount-namespace-capture-helper" pid=835 comm="apparmor_parser"
[    4.714399] audit: type=1400 audit(1547250461.395:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cups-browsed" pid=836 comm="apparmor_parser"
[    4.714564] audit: type=1400 audit(1547250461.395:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=827 comm="apparmor_parser"
[    4.888851] ath10k_pci 0000:03:00.0: htt-ver 2.1 wmi-op 5 htt-op 2 cal otp max-sta 128 raw 0 hwcrypto 1
[    4.971308] ath: EEPROM regdomain: 0x0
[    4.971308] ath: EEPROM indicates default country code should be used
[    4.971309] ath: doing EEPROM country->regdmn map search
[    4.971309] ath: country maps to regdmn code: 0x3a
[    4.971310] ath: Country alpha2 being used: US
[    4.971310] ath: Regpair used: 0x3a
[    4.981204] ath10k_pci 0000:03:00.0 wlp3s0: renamed from wlan0
[    4.985542] Bluetooth: Core ver 2.22
[    4.985552] NET: Registered protocol family 31
[    4.985553] Bluetooth: HCI device and connection manager initialized
[    4.985554] Bluetooth: HCI socket layer initialized
[    4.985555] Bluetooth: L2CAP socket layer initialized
[    4.985561] Bluetooth: SCO socket layer initialized
[    5.095850] usbcore: registered new interface driver btusb
[    5.141952] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    5.141952] Bluetooth: BNEP filters: protocol multicast
[    5.141955] Bluetooth: BNEP socket layer initialized
[    5.308966] Bluetooth: hci0: hardware error 0x37
[    5.517285] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[    6.578663] resource sanity check: requesting [mem 0x000c0000-0x000fffff], which spans more than PCI Bus 0000:00 [mem 0x000d0000-0x000d3fff window]
[    6.578768] caller os_map_kernel_space.part.7+0xda/0x120 [nvidia] mapping multiple BARs
[    6.837431] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[    6.927474] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   10.278702] vboxdrv: Found 8 processor cores
[   10.296221] vboxdrv: TSC mode is Invariant, tentative frequency 3500015405 Hz
[   10.296223] vboxdrv: Successfully loaded version 5.2.18_Ubuntu (interface 0x00290001)
[   10.300643] VBoxNetFlt: Successfully started.
[   10.303385] VBoxNetAdp: Successfully started.
[   10.307388] VBoxPciLinuxInit
[   10.309177] vboxpci: IOMMU not found (not registered)
[   12.214249] wlp3s0: authenticate with 98:de:d0:7d:85:7c
[   12.222220] wlp3s0: send auth to 98:de:d0:7d:85:7c (try 1/3)
[   12.223877] wlp3s0: authenticated
[   12.227992] wlp3s0: associate with 98:de:d0:7d:85:7c (try 1/3)
[   12.229930] wlp3s0: RX AssocResp from 98:de:d0:7d:85:7c (capab=0x11 status=0 aid=1)
[   12.231167] wlp3s0: associated
[   12.241207] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
[   13.426152] Bluetooth: RFCOMM TTY layer initialized
[   13.426156] Bluetooth: RFCOMM socket layer initialized
[   13.426160] Bluetooth: RFCOMM ver 1.11
[   64.544869] systemd: 40 output lines suppressed due to ratelimiting
[   64.549797] systemd[1]: systemd 237 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ +LZ4 +SECCOMP +BLKID +ELFUTILS +KMOD -IDN2 +IDN -PCRE2 default-hierarchy=hybrid)
[   64.568483] systemd[1]: Detected architecture x86-64.
[   65.101182] systemd[1]: Stopping Journal Service...
[   65.101417] systemd-journald[295]: Received SIGTERM from PID 1 (systemd).
[   65.113899] systemd[1]: Stopped Journal Service.
[   65.115403] systemd[1]: Starting Journal Service...
[   65.127755] systemd[1]: Started Journal Service.
[ 1660.980496] WARNING: CPU: 2 PID: 0 at /build/linux-vxxS7y/linux-4.15.0/net/core/dev.c:5645 net_rx_action+0x2cb/0x3a0
[ 1660.980498] Modules linked in: rfcomm ccm pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) bnep btusb btrtl btbcm btintel bluetooth ecdh_generic arc4 joydev input_leds snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_codec_generic intel_rapl wmi_bmof snd_hda_intel snd_hda_codec x86_pkg_temp_thermal intel_powerclamp snd_hda_core snd_hwdep snd_pcm coretemp ath10k_pci snd_seq_midi kvm_intel ath10k_core snd_seq_midi_event ath kvm irqbypass crct10dif_pclmul crc32_pclmul ghash_clmulni_intel snd_rawmidi pcbc mac80211 snd_seq aesni_intel snd_seq_device aes_x86_64 crypto_simd glue_helper cryptd snd_timer intel_cstate mei_me cfg80211 nvidia_uvm(POE) intel_rapl_perf snd mei soundcore ie31200_edac shpchp lpc_ich mac_hid wmi sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 hid_generic
[ 1660.980559]  hid_microsoft usbhid hid nvidia_drm(POE) nvidia_modeset(POE) nvidia(POE) drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops drm ahci ipmi_devintf i2c_i801 libahci ipmi_msghandler video
[ 1660.980577] CPU: 2 PID: 0 Comm: swapper/2 Tainted: P           OE    4.15.0-43-generic #46-Ubuntu
[ 1660.980579] Hardware name:  /DH77EB, BIOS EBH7710H.86A.0101.2013.0516.1649 05/16/2013
[ 1660.980581] RIP: 0010:net_rx_action+0x2cb/0x3a0
[ 1660.980583] RSP: 0018:ffff9549dec83ec8 EFLAGS: 00010293
[ 1660.980585] RAX: 0000000000000043 RBX: 0000000000000040 RCX: ffff9545f3ce0000
[ 1660.980587] RDX: ffff9545f3cb0000 RSI: 00000000fffffe01 RDI: ffffffffc1b04280
[ 1660.980588] RBP: ffff9549dec83f38 R08: 0000000000000002 R09: 0000000000000000
[ 1660.980589] R10: 00000000000023d7 R11: 0000000000000001 R12: 0000000000000000
[ 1660.980591] R13: 00000000ffffffff R14: 0000000000000003 R15: ffff9549c4b37b60
[ 1660.980593] FS:  0000000000000000(0000) GS:ffff9549dec80000(0000) knlGS:0000000000000000
[ 1660.980594] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[ 1660.980596] CR2: 00007f04d69bb000 CR3: 000000021a00a003 CR4: 00000000001606e0
[ 1660.980597] Call Trace:
[ 1660.980599]  <IRQ>
[ 1660.980606]  __do_softirq+0xe4/0x2bb
[ 1660.980611]  irq_exit+0xb8/0xc0
[ 1660.980613]  do_IRQ+0x8a/0xd0
[ 1660.980617]  common_interrupt+0x84/0x84
[ 1660.980618]  </IRQ>
[ 1660.980623] RIP: 0010:cpuidle_enter_state+0xa7/0x2f0
[ 1660.980625] RSP: 0018:ffffb13a4190fe68 EFLAGS: 00000246 ORIG_RAX: ffffffffffffffdd
[ 1660.980627] RAX: ffff9549deca2880 RBX: 00000182ba248aaa RCX: 000000000000001f
[ 1660.980628] RDX: 00000182ba248aaa RSI: fffffffbdb2d8ca2 RDI: 0000000000000000
[ 1660.980629] RBP: ffffb13a4190fea8 R08: 0000000000000334 R09: 00000000000001d1
[ 1660.980631] R10: ffffb13a4190fe38 R11: 0000000000000271 R12: ffff9549decacd00
[ 1660.980632] R13: 0000000000000004 R14: ffffffffb8f71d18 R15: 0000000000000000
[ 1660.980637]  ? cpuidle_enter_state+0x97/0x2f0
[ 1660.980640]  cpuidle_enter+0x17/0x20
[ 1660.980644]  call_cpuidle+0x23/0x40
[ 1660.980647]  do_idle+0x18c/0x1f0
[ 1660.980650]  cpu_startup_entry+0x73/0x80
[ 1660.980653]  start_secondary+0x1ab/0x200
[ 1660.980657]  secondary_startup_64+0xa5/0xb0
[ 1660.980659] Code: 24 08 49 83 c4 18 89 d9 44 89 f2 4c 89 fe e8 7d fc 3a 00 4d 8b 14 24 4d 85 d2 75 e1 4c 8b 65 90 44 89 f0 39 c3 0f 8d 85 fe ff ff <0f> 0b 39 c3 0f 8f 83 fe ff ff 49 8b 47 10 a8 04 75 74 49 83 7f 
[ 1660.980703] ---[ end trace bc4d1486ac0aee32 ]---
[ 2236.033011] wlp3s0: deauthenticating from 98:de:d0:7d:85:7c by local choice (Reason: 3=DEAUTH_LEAVING)
[ 2236.399310] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[ 2237.716517] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[ 2237.811815] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[ 2241.157922] wlp3s0: authenticate with 98:de:d0:7d:85:7c
[ 2241.165525] wlp3s0: send auth to 98:de:d0:7d:85:7c (try 1/3)
[ 2241.167129] wlp3s0: authenticated
[ 2241.167267] wlp3s0: associate with 98:de:d0:7d:85:7c (try 1/3)
[ 2241.168885] wlp3s0: RX AssocResp from 98:de:d0:7d:85:7c (capab=0x11 status=0 aid=1)
[ 2241.170130] wlp3s0: associated
[ 2241.173160] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
[ 4514.607031] wlp3s0: deauthenticating from 98:de:d0:7d:85:7c by local choice (Reason: 3=DEAUTH_LEAVING)
[ 4520.547826] wlp3s0: authenticate with 98:de:d0:7d:85:7c
[ 4520.552391] wlp3s0: send auth to 98:de:d0:7d:85:7c (try 1/3)
[ 4520.554221] wlp3s0: authenticated
[ 4520.562379] wlp3s0: associate with 98:de:d0:7d:85:7c (try 1/3)
[ 4520.563816] wlp3s0: RX AssocResp from 98:de:d0:7d:85:7c (capab=0x11 status=0 aid=1)
[ 4520.565080] wlp3s0: associated

```

Here is lshw -c network results in case anyone needs more details.  I'm on xubuntu 18.04


```
  *-network                 
       description: Wireless interface
       product: QCA986x/988x 802.11ac Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 00
       serial: 04:f0:21:41:af:96
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath10k_pci driverversion=4.15.0-43-generic firmware=10.2.4-1.0-00037 ip=192.168.1.131 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:28 memory:f7200000-f73fffff memory:f7400000-f740ffff
```


How would I go about troubleshooting this?  Is there a wifi hardware specific log I can look at?  Thanks!

---

