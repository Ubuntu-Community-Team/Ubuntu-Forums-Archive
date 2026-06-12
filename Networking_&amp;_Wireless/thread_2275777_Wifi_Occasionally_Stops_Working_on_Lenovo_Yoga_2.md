---
title: "Wifi Occasionally Stops Working on Lenovo Yoga 2"
date: 2015-04-28
forum: Networking &amp; Wireless
---

### Post by markybooth on 2015-04-28
I recently had some problems with my Lenovo Yoga 2 where the boot manager couldn't find the hard drive. I took it in for repairs and eventually got it back with a working hard drive - turned out it was just a loose cable. However, ever since the wifi has been temperamental. Sometimes working, sometimes not. I suspect this is similarly a loose cable but I'm reluctant to take it back in for repairs (it took five weeks last time and almost didn't get repaired as I bought it in the US and apparently the worldwide warranty for this model doesn't extend to Chile) so I first wanted to check if this could just be a Linux issue as I know there have been some issues with the drivers for this model. I found a wireless script on one of these forums and ran out. Below is the output from when it is not working. If you can take a look at this and let me know if this obviously a hardware issue or if there is something I can change in Ubuntu to make it work then that would be a great help.

Thanks!


    ```
======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

Imaginarium 3.13.0-45-generic x86_64,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Core(TM) i7-4510U CPU @ 2.00GHz
Memory : 7897 MB
Uptime : 11:18:02 up  1:10,  2 users,  load average: 0.12, 0.22, 0.22


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~



lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 006: ID 1bcf:2c43 Sunplus Innovation Technology Inc. 
Bus 002 Device 011: ID 04f3:016f Elan Microelectronics Corp. 
Bus 002 Device 003: ID 2047:0855 Texas Instruments 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

iwlmvm                189813  0 
mac80211              630669  1 iwlmvm
iwlwifi               169932  1 iwlmvm
cfg80211              484040  3 iwlwifi,mac80211,iwlmvm


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
iwlmvm        (2): init_dbg=N | power_scheme=2
iwlwifi      (11): 11n_disable=0 | amsdu_size_8K=0 | antenna_coupling=0 | bt_coex_active=Y | fw_restart=Y | led_mode=0 | nvm_file=(null) | power_level=0 | power_save=N | swcrypto=0 | wd_disable=1
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: disconnected
================o======o========o========o=========o===========o==============o===========
 Interface & ID | Type | Driver | State  | Default | Speed     | Support      | HW Addr   
================o======o========o========o=========o===========o==============o===========
                |      |        |        |         |           |              |           
----------------+------+--------+--------+---------+-----------+--------------+-----------




NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~



Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : en_GB.UTF-8)
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

           - 


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~



blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[iwlmvm]
filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
version:        in-tree:
srcversion:     412FF07DA992AAD938A30BE
depends:        iwlwifi,mac80211,cfg80211
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)

[mac80211]
filename:       /lib/modules/3.13.0-45-generic/kernel/net/mac80211/mac80211.ko
srcversion:     385697223F8285F67C93A06
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
version:        in-tree:
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265-7.ucode
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     B81BA270CF5925E724426BD
depends:        cfg80211
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)

[cfg80211]
filename:       /lib/modules/3.13.0-45-generic/kernel/net/wireless/cfg80211.ko
srcversion:     C2478077E22138832B71659
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x8086:0x08b1 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Not Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Not Default

[/etc/rc.local]
sudo rmmod ideapad_laptop
cat /proc/acpi/wakeup |
    grep '*enabled' |
    cut -f 1 -d ' ' |
    xargs -n 1 -I {} sh -c 'echo Disabling wake up on {}... && echo {} > /proc/acpi/wakeup'
exit 0

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en

[/etc/pm/power.d/wireless] [executable]
#!/bin/sh 
/sbin/iwconfig wlan0 power off



Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-45-generic.efi.signed root=UUID=743cdd6a-1f8e-4916-a8ab-217a5695476f ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.616019] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.616307] audit: initializing netlink socket (disabled)
[    1.947795] iwlwifi 0000:01:00.0: irq 60 for MSI/MSI-X
[    2.080740] iwlwifi 0000:01:00.0: loaded firmware version 22.24.8.0 op_mode iwlmvm
[    2.091133] iwlwifi 0000:01:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[    2.091184] iwlwifi 0000:01:00.0: L1 Disabled - LTR Enabled
[    2.091400] iwlwifi 0000:01:00.0: L1 Disabled - LTR Enabled
[    2.293478] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    3.878284] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    4.146352] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.021566] iwlwifi 0000:01:00.0: L1 Disabled - LTR Enabled
[   14.021786] iwlwifi 0000:01:00.0: L1 Disabled - LTR Enabled
[   14.034328] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.693594] wlan0: authenticate with <MAC ID removed>
[   17.695643] wlan0: direct probe to <MAC ID removed> (try 1/3)
[   17.898733] wlan0: direct probe to <MAC ID removed> (try 2/3)
[   18.102855] wlan0: send auth to <MAC ID removed> (try 3/3)
[   18.145633] wlan0: authenticated
[   18.145987] wlan0: associate with <MAC ID removed> (try 1/3)
[   18.148513] wlan0: RX AssocResp from <MAC ID removed> (capab=0x401 status=0 aid=14)
[   18.150033] wlan0: associated
[   18.150065] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   22.936570] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[   23.094379] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[ 3243.450688] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[ 3243.631802] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[ 3333.371925] iwlwifi 0000:01:00.0: Error sending SCAN_REQUEST_CMD: time out after 2000ms.
[ 3333.371936] iwlwifi 0000:01:00.0: Current CMD queue read_ptr 137 write_ptr 138
[ 3333.389656] WARNING: CPU: 2 PID: 1148 at /build/buildd/linux-3.13.0/drivers/net/wireless/iwlwifi/pcie/trans.c:1010 iwl_trans_pcie_grab_nic_access+0xcb/0xe0 [iwlwifi]()
[ 3333.389663] Modules linked in: hid_multitouch hid_sensor_accel_3d hid_sensor_gyro_3d hid_sensor_als hid_sensor_magn_3d hid_sensor_trigger industrialio_triggered_buffer kfifo_buf industrialio hid_sensor_iio_common hid_sensor_hub uvcvideo videobuf2_vmalloc videobuf2_memops usbhid videobuf2_core hid videodev btusb rfcomm bnep bluetooth snd_hda_codec_hdmi snd_hda_codec_realtek nls_iso8859_1 arc4 iwlmvm mac80211 intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper snd_seq_midi cryptd snd_seq_midi_event snd_rawmidi iwlwifi cfg80211 joydev snd_seq serio_raw snd_hda_intel snd_hda_codec snd_hwdep i915 snd_pcm snd_seq_device snd_page_alloc snd_timer shpchp lpc_ich drm_kms_helper mei_me snd mei drm soundcore i2c_algo_bit video sparse_keymap parport_pc intel_smartconnect ppdev mac_hid lp parport ahci psmouse libahci [last unloaded: ideapad_laptop]
[ 3333.389828]  [<ffffffffa0362eda>] ? iwl_read32+0x1a/0x80 [iwlwifi]
[ 3333.389844]  [<ffffffffa03643ab>] iwl_trans_pcie_grab_nic_access+0xcb/0xe0 [iwlwifi]
[ 3333.389858]  [<ffffffffa0365441>] iwl_trans_pcie_read_mem+0x31/0x130 [iwlwifi]
[ 3333.389875]  [<ffffffffa044fdd7>] iwl_mvm_dump_nic_error_log+0xc7/0x6b0 [iwlmvm]
[ 3333.389941]  [<ffffffffa044cf06>] iwl_mvm_nic_error+0x16/0x30 [iwlmvm]
[ 3333.389956]  [<ffffffffa03625b0>] iwl_trans_pcie_send_hcmd+0x5b0/0x690 [iwlwifi]
[ 3333.389976]  [<ffffffffa044f9be>] iwl_mvm_send_cmd_status+0x4e/0x160 [iwlmvm]
[ 3333.389989]  [<ffffffffa0455c65>] iwl_mvm_scan_request+0x375/0x470 [iwlmvm]
[ 3333.390000]  [<ffffffffa044abef>] iwl_mvm_mac_hw_scan+0x7f/0x90 [iwlmvm]
[ 3333.390131]  [<ffffffff81652489>] netlink_rcv_skb+0xa9/0xc0
[ 3333.390147]  [<ffffffff81651a85>] netlink_unicast+0xd5/0x1b0
[ 3333.390157]  [<ffffffff81651e80>] netlink_sendmsg+0x320/0x770
[ 3333.390267] iwlwifi 0000:01:00.0: Start IWL Error Log Dump:
[ 3333.390282] iwlwifi 0000:01:00.0: Status: 0x00000000, count: -1
[ 3333.390299] iwlwifi 0000:01:00.0: Loaded firmware version: 22.24.8.0
[ 3333.390316] iwlwifi 0000:01:00.0: 0xA037049D | ADVANCED_SYSASSERT          
[ 3333.390330] iwlwifi 0000:01:00.0: 0xFFFFFFFF | uPc
[ 3333.390344] iwlwifi 0000:01:00.0: 0x4FC37798 | branchlink1
[ 3333.390356] iwlwifi 0000:01:00.0: 0xFFFF8802 | branchlink2
[ 3333.390368] iwlwifi 0000:01:00.0: 0x00000010 | interruptlink1
[ 3333.390380] iwlwifi 0000:01:00.0: 0xFFFF8802 | interruptlink2
[ 3333.390391] iwlwifi 0000:01:00.0: 0x4FC377F0 | data1
[ 3333.390402] iwlwifi 0000:01:00.0: 0xFFFF8802 | data2
[ 3333.390414] iwlwifi 0000:01:00.0: 0x4FC377B0 | data3
[ 3333.390426] iwlwifi 0000:01:00.0: 0xFFFF8802 | beacon time
[ 3333.390438] iwlwifi 0000:01:00.0: 0x813709AA | tsf low
[ 3333.390446] iwlwifi 0000:01:00.0: 0xFFFFFFFF | tsf hi
[ 3333.390449] iwlwifi 0000:01:00.0: 0x00000005 | time gp1
[ 3333.390453] iwlwifi 0000:01:00.0: 0x00000000 | time gp2
[ 3333.390456] iwlwifi 0000:01:00.0: 0x4FC377F0 | time gp3
[ 3333.390460] iwlwifi 0000:01:00.0: 0xFFFF8802 | uCode version
[ 3333.390463] iwlwifi 0000:01:00.0: 0xA0372B98 | hw version
[ 3333.390467] iwlwifi 0000:01:00.0: 0xFFFFFFFF | board version
[ 3333.390470] iwlwifi 0000:01:00.0: 0x00000000 | hcmd
[ 3333.390474] iwlwifi 0000:01:00.0: 0xA0372A48 | isr0
[ 3333.390477] iwlwifi 0000:01:00.0: 0xFFFFFFFF | isr1
[ 3333.390481] iwlwifi 0000:01:00.0: 0x4FC377F0 | isr2
[ 3333.390487] iwlwifi 0000:01:00.0: 0xFFFF8802 | isr3
[ 3333.390492] iwlwifi 0000:01:00.0: 0x00000028 | isr4
[ 3333.390497] iwlwifi 0000:01:00.0: 0xFFFFFFFF | isr_pref
[ 3333.390503] iwlwifi 0000:01:00.0: 0x4FC37868 | wait_event
[ 3333.390509] iwlwifi 0000:01:00.0: 0xFFFF8802 | l2p_control
[ 3333.390515] iwlwifi 0000:01:00.0: 0x4FC37808 | l2p_duration
[ 3333.390520] iwlwifi 0000:01:00.0: 0xFFFF8802 | l2p_mhvalid
[ 3333.390526] iwlwifi 0000:01:00.0: 0x4FC37868 | l2p_addr_match
[ 3333.390531] iwlwifi 0000:01:00.0: 0xFFFF8802 | lmpm_pmg_sel
[ 3333.390536] iwlwifi 0000:01:00.0: 0x4FC37818 | timestamp
[ 3333.390542] iwlwifi 0000:01:00.0: 0xFFFF8802 | flow_handler
[ 3333.408307] iwlwifi 0000:01:00.0: Scan failed! status 0x1 ret -110
[ 3335.207858] iwlwifi 0000:01:00.0: Failing on timeout while stopping DMA channel 0 [0x5a5a5a5a]
[ 3337.011537] iwlwifi 0000:01:00.0: Failing on timeout while stopping DMA channel 2 [0x5a5a5a5a]
[ 3338.849349] iwlwifi 0000:01:00.0: Failing on timeout while stopping DMA channel 5 [0x5a5a5a5a]
[ 3340.652536] iwlwifi 0000:01:00.0: Failing on timeout while stopping DMA channel 7 [0x5a5a5a5a]
[ 3342.435813] iwlwifi 0000:01:00.0: L1 Disabled - LTR Disabled
[ 3342.574577] iwlwifi 0000:01:00.0: L1 Disabled - LTR Disabled
[ 3348.379430] iwlwifi 0000:01:00.0: Failed to load firmware chunk!
[ 3348.379442] iwlwifi 0000:01:00.0: Could not load the [0] uCode section
[ 3348.379453] iwlwifi 0000:01:00.0: Failed to start RT ucode: -110
[ 3350.177201] iwlwifi 0000:01:00.0: Failing on timeout while stopping DMA channel 0 [0x5a5a5a5a]
[ 3351.978597] iwlwifi 0000:01:00.0: Failing on timeout while stopping DMA channel 2 [0x5a5a5a5a]
[ 3353.815420] iwlwifi 0000:01:00.0: Failing on timeout while stopping DMA channel 5 [0x5a5a5a5a]
[ 3355.616238] iwlwifi 0000:01:00.0: Failing on timeout while stopping DMA channel 7 [0x5a5a5a5a]
[ 3451.119940] iwlwifi 0000:01:00.0: iwl_trans_send_cmd bad state = 0
[ 3451.119952] iwlwifi 0000:01:00.0: Scan failed! status 0x1 ret -5
[ 3571.196043] iwlwifi 0000:01:00.0: iwl_trans_send_cmd bad state = 0
[ 3571.196055] iwlwifi 0000:01:00.0: Scan failed! status 0x1 ret -5
[ 3691.269698] iwlwifi 0000:01:00.0: iwl_trans_send_cmd bad state = 0
[ 3691.269709] iwlwifi 0000:01:00.0: Scan failed! status 0x1 ret -5
[ 3811.343403] iwlwifi 0000:01:00.0: iwl_trans_send_cmd bad state = 0
[ 3811.343416] iwlwifi 0000:01:00.0: Scan failed! status 0x1 ret -5
[ 3931.416599] iwlwifi 0000:01:00.0: iwl_trans_send_cmd bad state = 0
[ 3931.416604] iwlwifi 0000:01:00.0: Scan failed! status 0x1 ret -5
[ 3976.497969] WARNING: CPU: 0 PID: 725 at /build/buildd/linux-3.13.0/drivers/net/wireless/iwlwifi/mvm/mac-ctxt.c:1092 iwl_mvm_mac_ctxt_changed+0x6e/0x80 [iwlmvm]()
[ 3976.497981] Modules linked in: hid_multitouch hid_sensor_accel_3d hid_sensor_gyro_3d hid_sensor_als hid_sensor_magn_3d hid_sensor_trigger industrialio_triggered_buffer kfifo_buf industrialio hid_sensor_iio_common hid_sensor_hub uvcvideo videobuf2_vmalloc videobuf2_memops usbhid videobuf2_core hid videodev btusb rfcomm bnep bluetooth snd_hda_codec_hdmi snd_hda_codec_realtek nls_iso8859_1 arc4 iwlmvm mac80211 intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper snd_seq_midi cryptd snd_seq_midi_event snd_rawmidi iwlwifi cfg80211 joydev snd_seq serio_raw snd_hda_intel snd_hda_codec snd_hwdep i915 snd_pcm snd_seq_device snd_page_alloc snd_timer shpchp lpc_ich drm_kms_helper mei_me snd mei drm soundcore i2c_algo_bit video sparse_keymap parport_pc intel_smartconnect ppdev mac_hid lp parport ahci psmouse libahci [last unloaded: ideapad_laptop]
[ 3976.498233]  [<ffffffffa044f5ce>] iwl_mvm_mac_ctxt_changed+0x6e/0x80 [iwlmvm]
[ 3976.498248]  [<ffffffffa044b6fb>] iwl_mvm_bss_info_changed+0xcb/0x420 [iwlmvm]
[ 3976.498322]  [<ffffffff8168f904>] __inet_del_ifa+0x154/0x2b0
[ 3976.498331]  [<ffffffff8168fb72>] inet_rtm_deladdr+0x112/0x170
[ 3976.498343]  [<ffffffff81633da5>] rtnetlink_rcv_msg+0x95/0x250
[ 3976.498363]  [<ffffffff81633d10>] ? rtnetlink_rcv+0x30/0x30
[ 3976.498375]  [<ffffffff81652489>] netlink_rcv_skb+0xa9/0xc0
[ 3976.498385]  [<ffffffff81633d08>] rtnetlink_rcv+0x28/0x30
[ 3976.498395]  [<ffffffff81651a85>] netlink_unicast+0xd5/0x1b0
[ 3976.498405]  [<ffffffff81651e80>] netlink_sendmsg+0x320/0x770
[ 3976.498415]  [<ffffffff8164ed24>] ? netlink_rcv_wake+0x44/0x60
[ 3976.498425]  [<ffffffff8164fd82>] ? netlink_recvmsg+0x1a2/0x3a0
[ 3976.498477]  [<ffffffff81628cc5>] ? netdev_run_todo+0x55/0x300
[ 3976.498570] iwlwifi 0000:01:00.0: failed to update MAC <MAC wlan0>
[ 3976.499706] wlan0: deauthenticating from <MAC ID removed> by local choice (reason=3)
[ 3976.499733] iwlwifi 0000:01:00.0: failed to update MAC <MAC wlan0>
[ 3976.499746] iwlwifi 0000:01:00.0: iwl_trans_send_cmd bad state = 0
[ 3976.499753] iwlwifi 0000:01:00.0: failed to update power mode
[ 3976.499838] WARNING: CPU: 3 PID: 1148 at /build/buildd/linux-3.13.0/drivers/net/wireless/iwlwifi/mvm/mac80211.c:1145 iwl_mvm_mac_sta_state+0x27c/0x290 [iwlmvm]()
[ 3976.499842] Modules linked in: hid_multitouch hid_sensor_accel_3d hid_sensor_gyro_3d hid_sensor_als hid_sensor_magn_3d hid_sensor_trigger industrialio_triggered_buffer kfifo_buf industrialio hid_sensor_iio_common hid_sensor_hub uvcvideo videobuf2_vmalloc videobuf2_memops usbhid videobuf2_core hid videodev btusb rfcomm bnep bluetooth snd_hda_codec_hdmi snd_hda_codec_realtek nls_iso8859_1 arc4 iwlmvm mac80211 intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper snd_seq_midi cryptd snd_seq_midi_event snd_rawmidi iwlwifi cfg80211 joydev snd_seq serio_raw snd_hda_intel snd_hda_codec snd_hwdep i915 snd_pcm snd_seq_device snd_page_alloc snd_timer shpchp lpc_ich drm_kms_helper mei_me snd mei drm soundcore i2c_algo_bit video sparse_keymap parport_pc intel_smartconnect ppdev mac_hid lp parport ahci psmouse libahci [last unloaded: ideapad_laptop]
[ 3976.500085]  [<ffffffffa044a98c>] iwl_mvm_mac_sta_state+0x27c/0x290 [iwlmvm]
[ 3976.500575]  [<ffffffff81652489>] netlink_rcv_skb+0xa9/0xc0
[ 3976.500651]  [<ffffffff81651a85>] netlink_unicast+0xd5/0x1b0
[ 3976.500687]  [<ffffffff81651e80>] netlink_sendmsg+0x320/0x770
[ 3976.500854] WARNING: CPU: 3 PID: 1148 at /build/buildd/linux-3.13.0/net/mac80211/sta_info.c:857 __sta_info_destroy+0x1be/0x360 [mac80211]()
[ 3976.500858] Modules linked in: hid_multitouch hid_sensor_accel_3d hid_sensor_gyro_3d hid_sensor_als hid_sensor_magn_3d hid_sensor_trigger industrialio_triggered_buffer kfifo_buf industrialio hid_sensor_iio_common hid_sensor_hub uvcvideo videobuf2_vmalloc videobuf2_memops usbhid videobuf2_core hid videodev btusb rfcomm bnep bluetooth snd_hda_codec_hdmi snd_hda_codec_realtek nls_iso8859_1 arc4 iwlmvm mac80211 intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper snd_seq_midi cryptd snd_seq_midi_event snd_rawmidi iwlwifi cfg80211 joydev snd_seq serio_raw snd_hda_intel snd_hda_codec snd_hwdep i915 snd_pcm snd_seq_device snd_page_alloc snd_timer shpchp lpc_ich drm_kms_helper mei_me snd mei drm soundcore i2c_algo_bit video sparse_keymap parport_pc intel_smartconnect ppdev mac_hid lp parport ahci psmouse libahci [last unloaded: ideapad_laptop]
[ 3976.501416]  [<ffffffff81652489>] netlink_rcv_skb+0xa9/0xc0
[ 3976.501436]  [<ffffffff81651a85>] netlink_unicast+0xd5/0x1b0
[ 3976.501446]  [<ffffffff81651e80>] netlink_sendmsg+0x320/0x770
[ 3976.501605] WARNING: CPU: 3 PID: 1148 at /build/buildd/linux-3.13.0/net/mac80211/sta_info.c:865 __sta_info_destroy+0x265/0x360 [mac80211]()
[ 3976.501609] Modules linked in: hid_multitouch hid_sensor_accel_3d hid_sensor_gyro_3d hid_sensor_als hid_sensor_magn_3d hid_sensor_trigger industrialio_triggered_buffer kfifo_buf industrialio hid_sensor_iio_common hid_sensor_hub uvcvideo videobuf2_vmalloc videobuf2_memops usbhid videobuf2_core hid videodev btusb rfcomm bnep bluetooth snd_hda_codec_hdmi snd_hda_codec_realtek nls_iso8859_1 arc4 iwlmvm mac80211 intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper snd_seq_midi cryptd snd_seq_midi_event snd_rawmidi iwlwifi cfg80211 joydev snd_seq serio_raw snd_hda_intel snd_hda_codec snd_hwdep i915 snd_pcm snd_seq_device snd_page_alloc snd_timer shpchp lpc_ich drm_kms_helper mei_me snd mei drm soundcore i2c_algo_bit video sparse_keymap parport_pc intel_smartconnect ppdev mac_hid lp parport ahci psmouse libahci [last unloaded: ideapad_laptop]
[ 3976.502109]  [<ffffffff81652489>] netlink_rcv_skb+0xa9/0xc0
[ 3976.502130]  [<ffffffff81651a85>] netlink_unicast+0xd5/0x1b0
[ 3976.502141]  [<ffffffff81651e80>] netlink_sendmsg+0x320/0x770
[ 3976.502416] iwlwifi 0000:01:00.0: failed to update MAC <MAC wlan0>
[ 3976.502427] iwlwifi 0000:01:00.0: iwl_trans_send_cmd bad state = 0
[ 3976.502434] iwlwifi 0000:01:00.0: Failed to send BT_CI cmd
[ 3976.502441] iwlwifi 0000:01:00.0: iwl_trans_send_cmd bad state = 0
[ 3976.502447] iwlwifi 0000:01:00.0: Failed to update the ctrl_kill_msk
[ 3976.502458] iwlwifi 0000:01:00.0: failed to update MAC <MAC wlan0>
[ 3976.502488] WARNING: CPU: 3 PID: 1148 at /build/buildd/linux-3.13.0/drivers/net/wireless/iwlwifi/mvm/binding.c:193 iwl_mvm_binding_remove_vif+0x3f/0x50 [iwlmvm]()
[ 3976.502492] Modules linked in: hid_multitouch hid_sensor_accel_3d hid_sensor_gyro_3d hid_sensor_als hid_sensor_magn_3d hid_sensor_trigger industrialio_triggered_buffer kfifo_buf industrialio hid_sensor_iio_common hid_sensor_hub uvcvideo videobuf2_vmalloc videobuf2_memops usbhid videobuf2_core hid videodev btusb rfcomm bnep bluetooth snd_hda_codec_hdmi snd_hda_codec_realtek nls_iso8859_1 arc4 iwlmvm mac80211 intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper snd_seq_midi cryptd snd_seq_midi_event snd_rawmidi iwlwifi cfg80211 joydev snd_seq serio_raw snd_hda_intel snd_hda_codec snd_hwdep i915 snd_pcm snd_seq_device snd_page_alloc snd_timer shpchp lpc_ich drm_kms_helper mei_me snd mei drm soundcore i2c_algo_bit video sparse_keymap parport_pc intel_smartconnect ppdev mac_hid lp parport ahci psmouse libahci [last unloaded: ideapad_laptop]
[ 3976.502713]  [<ffffffffa0452b3f>] iwl_mvm_binding_remove_vif+0x3f/0x50 [iwlmvm]
[ 3976.502729]  [<ffffffffa0449d67>] iwl_mvm_unassign_vif_chanctx+0x57/0x90 [iwlmvm]
[ 3976.503032]  [<ffffffff81652489>] netlink_rcv_skb+0xa9/0xc0
[ 3976.503052]  [<ffffffff81651a85>] netlink_unicast+0xd5/0x1b0
[ 3976.503063]  [<ffffffff81651e80>] netlink_sendmsg+0x320/0x770
[ 3976.552562] iwlwifi 0000:01:00.0: iwl_trans_send_cmd bad state = 0
[ 3976.552567] iwlwifi 0000:01:00.0: Failed to send flush command (-5)
[ 3976.552595] WARNING: CPU: 0 PID: 725 at /build/buildd/linux-3.13.0/drivers/net/wireless/iwlwifi/mvm/mac-ctxt.c:1105 iwl_mvm_mac_ctxt_remove+0x171/0x190 [iwlmvm]()
[ 3976.552598] Modules linked in: hid_multitouch hid_sensor_accel_3d hid_sensor_gyro_3d hid_sensor_als hid_sensor_magn_3d hid_sensor_trigger industrialio_triggered_buffer kfifo_buf industrialio hid_sensor_iio_common hid_sensor_hub uvcvideo videobuf2_vmalloc videobuf2_memops usbhid videobuf2_core hid videodev btusb rfcomm bnep bluetooth snd_hda_codec_hdmi snd_hda_codec_realtek nls_iso8859_1 arc4 iwlmvm mac80211 intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper snd_seq_midi cryptd snd_seq_midi_event snd_rawmidi iwlwifi cfg80211 joydev snd_seq serio_raw snd_hda_intel snd_hda_codec snd_hwdep i915 snd_pcm snd_seq_device snd_page_alloc snd_timer shpchp lpc_ich drm_kms_helper mei_me snd mei drm soundcore i2c_algo_bit video sparse_keymap parport_pc intel_smartconnect ppdev mac_hid lp parport ahci psmouse libahci [last unloaded: ideapad_laptop]
[ 3976.552674]  [<ffffffffa044f751>] iwl_mvm_mac_ctxt_remove+0x171/0x190 [iwlmvm]
[ 3976.552688]  [<ffffffffa044b1a5>] iwl_mvm_mac_remove_interface+0xb5/0x190 [iwlmvm]
[ 3976.552747]  [<ffffffff81633da5>] rtnetlink_rcv_msg+0x95/0x250
[ 3976.552753]  [<ffffffff81633d10>] ? rtnetlink_rcv+0x30/0x30
[ 3976.552756]  [<ffffffff81652489>] netlink_rcv_skb+0xa9/0xc0
[ 3976.552759]  [<ffffffff81633d08>] rtnetlink_rcv+0x28/0x30
[ 3976.552762]  [<ffffffff81651a85>] netlink_unicast+0xd5/0x1b0
[ 3976.552765]  [<ffffffff81651e80>] netlink_sendmsg+0x320/0x770
[ 3976.552767]  [<ffffffff8164ed24>] ? netlink_rcv_wake+0x44/0x60
[ 3976.552770]  [<ffffffff8164fd82>] ? netlink_recvmsg+0x1a2/0x3a0
[ 3976.552802] iwlwifi 0000:01:00.0: iwl_trans_txq_disable bad state = 0
[ 3976.587442] iwlwifi 0000:01:00.0: iwl_trans_txq_disable bad state = 0
[ 3976.622159] iwlwifi 0000:01:00.0: iwl_trans_txq_disable bad state = 0
[ 3976.656827] iwlwifi 0000:01:00.0: iwl_trans_txq_disable bad state = 0
[ 3983.144525] iwlwifi 0000:01:00.0: Refused to change power state, currently in D3

    ======== Done ========

```

---

### Post by RobGoss on 2015-04-28
Are you using a Wifi connection? And if so make sure your wireless router is working as it should be sometImes your IP address is interrupted and may cause outages.

---

### Post by jeremy31 on 2015-04-29
I would remove the wifi card and reinsert it as it should have showed up in the script result from the ```
lspci
``` command

---

### Post by michi1983 on 2015-04-29
> **jeremy31 said:**
> I would remove the wifi card and reinsert it as it should have showed up in the script result from the ```
lspci
``` command

I might miss something here but I think the TO can't just remove and reinsert any kind of wifi card. The wifi is built-in in the Yoga 2 I think. But it's weired because it doesn't show up at all in the script.

---

### Post by jeremy31 on 2015-04-29
The bottom cover or a panel may have to be removed to access the wifi card and after that, only one or two screws hold the card in the slot.

A youtube video says there are 11 screws to remove from the bottom panel

---

### Post by michi1983 on 2015-04-29
> **jeremy31 said:**
> The bottom cover or a panel may have to be removed to access the wifi card and after that, only one or two screws hold the card in the slot.

Ah okay, you really meant that ;) I thought of that this is the only way to do it but was not sure if you really want to give that kind of advice ;)

---

### Post by markybooth on 2015-04-29
Yeah, I figured that all those empty responses weren't a good sign. Guess I'll just have to have a go at opening it up and seeing if a bit of screw tightening helps. Thanks for the tips.

---

### Post by wildmanne39 on 2015-04-29
The repair person probably left the wireless card loose.

---

