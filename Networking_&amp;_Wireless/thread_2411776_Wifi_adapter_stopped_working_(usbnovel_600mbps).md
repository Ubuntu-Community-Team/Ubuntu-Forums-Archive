---
title: "Wifi adapter stopped working (usbnovel 600mbps)"
date: 2019-02-03
forum: Networking &amp; Wireless
---

### Post by Joseph_Watts on 2019-02-03
os: Ubuntu 18.04 bionic
hw: Lenovo t430
[This]("https://www.amazon.com/gp/product/B06XRG9QDV") is the wireless adapter

This device was previously working just fine (2.4 & 5ghz networks). It stopped working so I went through the process of uninstalling then reinstalling drivers to no avail.

Driver installation was done by following the steps [here.]("https://github.com/abperiasamy/rtl8812AU_8821AU_linux")

iwconfig throws this
```

wlx000f007a7394  unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

lsusb shows
```
Bus 003 Device 004: ID 0bda:a811 Realtek Semiconductor Corp.
```

I've also tried using [this]("https://github.com/gnab/rtl8812au") driver but it also gives the same results.

This is what I see. Selecting the blank line gives options like any other wireless adapter, except when I click to choose a network it doesn't list any as available.
[IMG]https://i.imgur.com/OuSkIJp.png[/IMG]


Thank you for the help in advance. :)

edit: ran ```
apt-get install rtl8812au-dkms
``` but it still doesn't appear to work after rebooting. even though the output of dkms status is ```
rtl8812au, 4.3.14, 4.15.0-45-generic, x86_64: installed
```

---

### Post by solisa on 2019-02-04
I had the same problem after upgrading. It works again after booting with 4.15.0-44.

The iwlwifi module is not working correctly in *-45.

Lenovo x230

lspci -vv -s
```
 03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] (rev 34)
    Subsystem: Intel Corporation Centrino Advanced-N 6205 AGN
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 30
    Region 0: Memory at f1c00000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: [c8] Power Management version 3
        Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Address: 00000000fee00318  Data: 0000
    Capabilities: [e0] Express (v1) Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 unlimited
            ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset+ SlotPowerLimit 0.000W
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+ FLReset-
            MaxPayload 128 bytes, MaxReadReq 128 bytes
        DevSta:    CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr+ TransPend-
        LnkCap:    Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Exit Latency L0s <4us, L1 <32us
            ClockPM+ Surprise- LLActRep- BwNot- ASPMOptComp-
        LnkCtl:    ASPM L1 Enabled; RCB 64 bytes Disabled- CommClk+
            ExtSynch- ClockPM+ AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
    Capabilities: [100 v1] Advanced Error Reporting
        UESta:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UEMsk:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UESvrt:    DLP+ SDES- TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
        CESta:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
        CEMsk:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
        AERCap:    First Error Pointer: 00, GenCap- CGenEn- ChkCap- ChkEn-
    Capabilities: [140 v1] Device Serial Number 60-67-20-ff-ff-43-bc-f6
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi

```

from the bad kernel log

```
Feb 04 12:37:40 x230 systemd[1]: Starting Network Manager Script Dispatcher Service...
Feb 04 12:37:40 x230 dbus-daemon[1198]: [session uid=121 pid=1198]  Activating service name='ca.desrt.dconf' requested by ':1.13' (uid=121  pid=
Feb 04 12:37:40 x230 dbus-daemon[1198]: [session uid=121 pid=1198] Successfully activated service 'ca.desrt.dconf'
Feb 04 12:37:40 x230 dbus-daemon[998]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Feb 04 12:37:40 x230 systemd[1]: Started Network Manager Script Dispatcher Service.
Feb 04 12:37:40 x230 nm-dispatcher[2585]: req:1 'down' [wlp3s0]: new request (2 scripts)
Feb 04 12:37:40 x230 nm-dispatcher[2585]: req:1 'down' [wlp3s0]: start running ordered scripts...
Feb 04 12:37:40 x230 nm-dispatcher[2585]: req:2 'connectivity-change': new request (2 scripts)
Feb 04 12:37:41 x230 gnome-shell[1212]: An active wireless connection, in infrastructure mode, involves no access point?
Feb 04 12:37:41 x230 gnome-shell[1719]: An active wireless connection, in infrastructure mode, involves no access point?
Feb 04 12:37:41 x230 gnome-shell[1212]: An active wireless connection, in infrastructure mode, involves no access point?
Feb 04 12:37:41 x230 gnome-shell[1719]: An active wireless connection, in infrastructure mode, involves no access point?
Feb 04 12:37:41 x230 gnome-shell[1212]: An active wireless connection, in infrastructure mode, involves no access point?
Feb 04 12:37:41 x230 gnome-shell[1212]: An active wireless connection, in infrastructure mode, involves no access point?
Feb 04 12:37:41 x230 gnome-shell[1719]: An active wireless connection, in infrastructure mode, involves no access point?
Feb 04 12:37:41 x230 gnome-shell[1212]: An active wireless connection, in infrastructure mode, involves no access point?
Feb 04 12:37:41 x230 gnome-shell[1719]: An active wireless connection, in infrastructure mode, involves no access point?
Feb 04 12:37:41 x230 gnome-shell[1719]: An active wireless connection, in infrastructure mode, involves no access point?
Feb 04 12:37:41 x230 gnome-shell[1212]: An active wireless connection, in infrastructure mode, involves no access point?
Feb 04 12:37:41 x230 gnome-shell[1212]: An active wireless connection, in infrastructure mode, involves no access point?
Feb 04 12:37:41 x230 gnome-shell[1719]: An active wireless connection, in infrastructure mode, involves no access point?
Feb 04 12:37:41 x230 gnome-shell[1719]: An active wireless connection, in infrastructure mode, involves no access point?
Feb 04 12:37:42 x230 NetworkManager[1051]: <info>   [1549280262.9976] device (wlp3s0): set-hw-addr: set MAC address to  BA:47:47:C9:22:D6 (scann
Feb 04 12:37:42 x230 kernel: iwlwifi 0000:03:00.0: Error sending REPLY_SCAN_ABORT_CMD: time out after 2000ms.
Feb 04 12:37:43 x230 kernel: iwlwifi 0000:03:00.0: Current CMD queue read_ptr 98 write_ptr 99
Feb 04 12:37:43 x230 kernel: iwlwifi 0000:03:00.0: Loaded firmware version: 18.168.6.1
Feb 04 12:37:43 x230 kernel: iwlwifi 0000:03:00.0: 0x00000000 | OK                          
Feb 04 12:37:43 x230 kernel: iwlwifi 0000:03:00.0: 0x00000000 | uPc
Feb 04 12:37:43 x230 kernel: iwlwifi 0000:03:00.0: 0x00000000 | branchlink1
Feb 04 12:37:43 x230 kernel: iwlwifi 0000:03:00.0: 0x00000000 | branchlink2
Feb 04 12:37:43 x230 kernel: iwlwifi 0000:03:00.0: 0x00000000 | interruptlink1
Feb 04 12:37:43 x230 kernel: iwlwifi 0000:03:00.0: 0x00000000 | interruptlink2
Feb 04 12:37:43 x230 kernel: iwlwifi 0000:03:00.0: 0x00000000 | data1
Feb 04 12:37:43 x230 kernel: iwlwifi 0000:03:00.0: 0x00000000 | data2
Feb 04 12:37:43 x230 kernel: iwlwifi 0000:03:00.0: 0x00000000 | line
Feb 04 12:37:43 x230 kernel: iwlwifi 0000:03:00.0: 0x00000000 | beacon time
Feb 04 12:37:43 x230 kernel: iwlwifi 0000:03:00.0: 0x00000000 | tsf low
Feb 04 12:37:43 x230 kernel: iwlwifi 0000:03:00.0: 0x00000000 | tsf hi
Feb 04 12:37:43 x230 kernel: iwlwifi 0000:03:00.0: 0x00000000 | time gp1
Feb 04 12:37:43 x230 kernel: iwlwifi 0000:03:00.0: 0x00000000 | time gp2
Feb 04 12:37:43 x230 kernel: iwlwifi 0000:03:00.0: 0x00000000 | time gp3
Feb 04 12:37:43 x230 kernel: iwlwifi 0000:03:00.0: 0x00000000 | uCode version
Feb 04 12:37:43 x230 kernel: iwlwifi 0000:03:00.0: 0x00000000 | hw version
Feb 04 12:37:43 x230 kernel: iwlwifi 0000:03:00.0: 0x00000000 | board version
Feb 04 12:37:43 x230 kernel: iwlwifi 0000:03:00.0: 0x00000000 | hcmd
Feb 04 12:37:43 x230 kernel: iwlwifi 0000:03:00.0: 0x00000000 | isr0
Feb 04 12:37:43 x230 kernel: iwlwifi 0000:03:00.0: 0x00000000 | isr1
Feb 04 12:37:43 x230 kernel: iwlwifi 0000:03:00.0: 0x00000000 | isr2
Feb 04 12:37:43 x230 kernel: iwlwifi 0000:03:00.0: 0x00000000 | isr3
Feb 04 12:37:43 x230 kernel: iwlwifi 0000:03:00.0: 0x00000000 | isr4
Feb 04 12:37:43 x230 kernel: iwlwifi 0000:03:00.0: 0x00000000 | isr_pref
Feb 04 12:37:43 x230 kernel: iwlwifi 0000:03:00.0: 0x00000000 | wait_event
Feb 04 12:37:43 x230 kernel: iwlwifi 0000:03:00.0: 0x00000000 | l2p_control
Feb 04 12:37:43 x230 kernel: iwlwifi 0000:03:00.0: 0x00000000 | l2p_duration
Feb 04 12:37:43 x230 kernel: iwlwifi 0000:03:00.0: 0x00000000 | l2p_mhvalid
Feb 04 12:37:43 x230 kernel: iwlwifi 0000:03:00.0: 0x00000000 | l2p_addr_match
Feb 04 12:37:43 x230 kernel: iwlwifi 0000:03:00.0: 0x00000000 | lmpm_pmg_sel
Feb 04 12:37:43 x230 kernel: iwlwifi 0000:03:00.0: 0x00000000 | timestamp
Feb 04 12:37:43 x230 kernel: iwlwifi 0000:03:00.0: 0x00000000 | flow_handler
Feb 04 12:37:43 x230 kernel: iwlwifi 0000:03:00.0: Start IWL Event Log Dump: nothing in log
Feb 04 12:37:43 x230 kernel: iwlwifi 0000:03:00.0: Command REPLY_RXON failed: FW Error
Feb 04 12:37:43 x230 kernel: iwlwifi 0000:03:00.0: Error clearing ASSOC_MSK on BSS (-5)
Feb 04 12:37:43 x230 kernel: ieee80211 phy0: Hardware restart was requested
Feb 04 12:37:43 x230 kernel: iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
Feb 04 12:37:43 x230 kernel: iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
Feb 04 12:37:43 x230 kernel: IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
Feb 04 12:37:43 x230 avahi-daemon[963]: Interface wlp3s0.IPv6 no longer relevant for mDNS.
Feb 04 12:37:43 x230 avahi-daemon[963]: Withdrawing address record for 192.168.178.23 on wlp3s0.
Feb 04 12:37:43 x230 avahi-daemon[963]: Leaving mDNS multicast group on interface wlp3s0.IPv4 with address 192.168.178.23.
Feb 04 12:37:43 x230 avahi-daemon[963]: Interface wlp3s0.IPv4 no longer relevant for mDNS.
Feb 04 12:37:43 x230 NetworkManager[1051]: <info>   [1549280263.4284] device (wlp3s0): supplicant interface state: scanning  -> disabled
Feb 04 12:37:43 x230 kernel: iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
Feb 04 12:37:43 x230 gsd-sharing[1840]: Failed to StopUnit service:  GDBus.Error:org.freedesktop.systemd1.NoSuchUnit: Unit  gnome-user-share-web
Feb 04 12:37:43 x230 gsd-sharing[1840]: Failed to StopUnit service:  GDBus.Error:org.freedesktop.systemd1.NoSuchUnit: Unit rygel.service not  lo
Feb 04 12:37:43 x230 gsd-sharing[1840]: Failed to StopUnit service:  GDBus.Error:org.freedesktop.systemd1.NoSuchUnit: Unit  gnome-remote-desktop
Feb 04 12:37:43 x230 gsd-sharing[1840]: Failed to StopUnit service:  GDBus.Error:org.freedesktop.systemd1.NoSuchUnit: Unit  vino-server.service 
Feb 04 12:37:48 x230 kernel: iwlwifi 0000:03:00.0: Failed to load firmware chunk!
Feb 04 12:37:48 x230 kernel: iwlwifi 0000:03:00.0: iwlwifi transaction failed, dumping registers
Feb 04 12:37:48 x230 kernel: iwlwifi 0000:03:00.0: iwlwifi device config registers:
Feb 04 12:37:48 x230 kernel: iwlwifi 0000:03:00.0: 00000000: 00858086  00100406 02800034 00000010 f1c00004 00000000 00000000 00000000
Feb 04 12:37:48 x230 kernel: iwlwifi 0000:03:00.0: 00000020: 00000000  00000000 00000000 13118086 00000000 000000c8 00000000 00000107
Feb 04 12:37:48 x230 kernel: iwlwifi 0000:03:00.0: iwlwifi device memory mapped registers:
Feb 04 12:37:48 x230 kernel: iwlwifi 0000:03:00.0: 00000000: 00488700  00000040 08000000 00000000 00000001 00000000 00000030 00000000
Feb 04 12:37:48 x230 kernel: iwlwifi 0000:03:00.0: 00000020: 00000001  080403c5 000000b0 00000000 90000001 00030001 80008040 00080046
Feb 04 12:37:48 x230 kernel: iwlwifi 0000:03:00.0: iwlwifi device AER capability structure:
Feb 04 12:37:48 x230 kernel: iwlwifi 0000:03:00.0: 00000000: 14010001  00000000 00000000 00062011 00000000 00002000 00000000 00000000
Feb 04 12:37:48 x230 kernel: iwlwifi 0000:03:00.0: 00000020: 00000000 00000000 00000000
Feb 04 12:37:48 x230 kernel: iwlwifi 0000:03:00.0: iwlwifi parent port (0000:00:1c.1) config registers:
Feb 04 12:37:48 x230 kernel: iwlwifi 0000:00:1c.1: 00000000: 1e128086  00100007 060400c4 00810010 00000000 00000000 00030300 200000f0
Feb 04 12:37:48 x230 kernel: iwlwifi 0000:00:1c.1: 00000020: f1c0f1c0  0001fff1 00000000 00000000 00000000 00000040 00000000 00000207
Feb 04 12:37:48 x230 kernel: iwlwifi 0000:03:00.0: Could not load the [0] uCode section
Feb 04 12:37:48 x230 kernel: iwlwifi 0000:03:00.0: Failed to run INIT ucode: -110
Feb 04 12:37:48 x230 kernel: iwlwifi 0000:03:00.0: Unable to initialize device.
Feb 04 12:37:48 x230 kernel: ------------[ cut here ]------------
Feb 04 12:37:48 x230 kernel: Hardware became unavailable during restart.
Feb 04 12:37:48 x230 kernel: WARNING: CPU: 2 PID: 36 at  /build/linux-uQJ2um/linux-4.15.0/net/mac80211/util.c:1863  ieee80211_reconfig+0x22c/0xf
Feb 04 12:37:48 x230 kernel: Modules linked in: ccm cmac bnep btusb  btrtl btbcm btintel bluetooth ecdh_generic intel_rapl snd_hda_codec_hdmi  x
Feb 04 12:37:48 x230 kernel:  nf_conntrack_broadcast nf_nat_ftp nf_nat  nf_conntrack_ftp nf_conntrack libcrc32c sch_fq_codel sunrpc iptable_fil
Feb 04 12:37:48 x230 kernel: CPU: 2 PID: 36 Comm: kworker/2:1 Not tainted 4.15.0-45-generic #48-Ubuntu
Feb 04 12:37:48 x230 kernel: Hardware name: LENOVO 2325BP9/2325BP9, BIOS G2ETB0WW (2.70 ) 09/25/2017
Feb 04 12:37:48 x230 kernel: Workqueue: events_freezable ieee80211_restart_work [mac80211]
Feb 04 12:37:48 x230 kernel: RIP: 0010:ieee80211_reconfig+0x22c/0xfc0 [mac80211]
Feb 04 12:37:48 x230 kernel: RSP: 0018:ffffa3dcc0e07e00 EFLAGS: 00010286
Feb 04 12:37:48 x230 kernel: RAX: 0000000000000000 RBX: ffff8bc50a5d0760 RCX: 0000000000000006
Feb 04 12:37:48 x230 kernel: RDX: 0000000000000007 RSI: 0000000000000082 RDI: ffff8bc51e296490
Feb 04 12:37:48 x230 kernel: RBP: ffffa3dcc0e07e48 R08: 0000000000000001 R09: 00000000000003b3
Feb 04 12:37:48 x230 kernel: R10: fffff1bf86fbb640 R11: 0000000000000000 R12: ffff8bc50a5d13a0
Feb 04 12:37:48 x230 kernel: R13: ffff8bc50a5d0760 R14: ffff8bc50a5d0f90 R15: 00000000ffffff92
Feb 04 12:37:48 x230 kernel: FS:  0000000000000000(0000) GS:ffff8bc51e280000(0000) knlGS:0000000000000000
Feb 04 12:37:48 x230 kernel: CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Feb 04 12:37:48 x230 kernel: CR2: 00007fdcfeb2e000 CR3: 0000000062c0a006 CR4: 00000000001606e0
Feb 04 12:37:48 x230 kernel: Call Trace:
Feb 04 12:37:48 x230 kernel:  ieee80211_restart_work+0x9e/0xd0 [mac80211]
Feb 04 12:37:48 x230 kernel:  process_one_work+0x1de/0x410
Feb 04 12:37:48 x230 kernel:  worker_thread+0x32/0x410
Feb 04 12:37:48 x230 kernel:  kthread+0x121/0x140
Feb 04 12:37:48 x230 kernel:  ? process_one_work+0x410/0x410
Feb 04 12:37:48 x230 kernel:  ? kthread_create_worker_on_cpu+0x70/0x70
Feb 04 12:37:48 x230 kernel:  ret_from_fork+0x35/0x40
Feb 04 12:37:48 x230 kernel: Code: 00 c6 45 d6 00 c6 83 94 04 00 00 00  48 89 df e8 bb b6 fc ff 85 c0 41 89 c7 0f 84 50 01 00 00 48 c7 c7 58 b3
Feb 04 12:37:48 x230 kernel: ---[ end trace 075e06daef46bd11 ]---
Feb 04 12:37:48 x230 kernel: ------------[ cut here ]------------
Feb 04 12:37:48 x230 kernel: wlp3s0:  Failed check-sdata-in-driver check, flags: 0x0
Feb 04 12:37:48 x230 kernel: WARNING: CPU: 2 PID: 36 at  /build/linux-uQJ2um/linux-4.15.0/net/mac80211/driver-ops.h:18  drv_remove_interface+0xf
Feb 04 12:37:48 x230 kernel: Modules linked in: ccm cmac bnep btusb  btrtl btbcm btintel bluetooth ecdh_generic intel_rapl snd_hda_codec_hdmi  x
Feb 04 12:37:48 x230 kernel:  nf_conntrack_broadcast nf_nat_ftp nf_nat  nf_conntrack_ftp nf_conntrack libcrc32c sch_fq_codel sunrpc iptable_fil
Feb 04 12:37:48 x230 kernel: CPU: 2 PID: 36 Comm: kworker/2:1 Tainted: G        W        4.15.0-45-generic #48-Ubuntu
Feb 04 12:37:48 x230 kernel: Hardware name: LENOVO 2325BP9/2325BP9, BIOS G2ETB0WW (2.70 ) 09/25/2017
Feb 04 12:37:48 x230 kernel: Workqueue: events_freezable ieee80211_restart_work [mac80211]
Feb 04 12:37:48 x230 kernel: RIP: 0010:drv_remove_interface+0xfe/0x110 [mac80211]
Feb 04 12:37:48 x230 kernel: RSP: 0018:ffffa3dcc0e07c38 EFLAGS: 00010282
Feb 04 12:37:48 x230 kernel: RAX: 0000000000000000 RBX: ffff8bc509728cd8 RCX: 0000000000000006
Feb 04 12:37:48 x230 kernel: RDX: 0000000000000007 RSI: 0000000000000092 RDI: ffff8bc51e296490
Feb 04 12:37:48 x230 kernel: RBP: ffffa3dcc0e07c50 R08: 0000000000000001 R09: 00000000000003cf
Feb 04 12:37:48 x230 kernel: R10: 0000000000000000 R11: 0000000000000000 R12: ffff8bc50a5d0760
Feb 04 12:37:48 x230 kernel: R13: ffff8bc50a5d0ee8 R14: ffff8bc50a5d0760 R15: ffff8bc509729380
Feb 04 12:37:48 x230 kernel: FS:  0000000000000000(0000) GS:ffff8bc51e280000(0000) knlGS:0000000000000000
Feb 04 12:37:48 x230 kernel: CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Feb 04 12:37:48 x230 kernel: CR2: 00007fdcfeb2e000 CR3: 0000000062c0a006 CR4: 00000000001606e0
Feb 04 12:37:48 x230 kernel: Call Trace:
Feb 04 12:37:48 x230 kernel:  ieee80211_do_stop+0x4e1/0x7f0 [mac80211]
Feb 04 12:37:48 x230 kernel:  ? qdisc_reset+0x2b/0x70
Feb 04 12:37:48 x230 kernel:  ieee80211_stop+0x1a/0x20 [mac80211]
Feb 04 12:37:48 x230 kernel:  __dev_close_many+0xa5/0x110
Feb 04 12:37:48 x230 kernel:  dev_close_many+0x8c/0x140
Feb 04 12:37:48 x230 kernel:  dev_close.part.88+0x4a/0x70
Feb 04 12:37:48 x230 kernel:  dev_close+0x19/0x20
Feb 04 12:37:48 x230 kernel:  cfg80211_shutdown_all_interfaces+0x77/0xc0 [cfg80211]
Feb 04 12:37:48 x230 kernel:  ieee80211_handle_reconfig_failure+0x98/0xb0 [mac80211]
Feb 04 12:37:48 x230 kernel:  ieee80211_reconfig+0x236/0xfc0 [mac80211]
Feb 04 12:37:48 x230 kernel:  ieee80211_restart_work+0x9e/0xd0 [mac80211]
Feb 04 12:37:48 x230 kernel:  process_one_work+0x1de/0x410
Feb 04 12:37:48 x230 kernel:  worker_thread+0x32/0x410
Feb 04 12:37:48 x230 kernel:  kthread+0x121/0x140
Feb 04 12:37:48 x230 kernel:  ? process_one_work+0x410/0x410
Feb 04 12:37:48 x230 kernel:  ? kthread_create_worker_on_cpu+0x70/0x70
Feb 04 12:37:48 x230 kernel:  ret_from_fork+0x35/0x40
Feb 04 12:37:48 x230 kernel: Code: c0 75 e8 5b 41 5c 41 5d 5d c3 48 8b  b3 f8 03 00 00 48 81 c3 18 04 00 00 48 c7 c7 b0 89 87 c0 48 85 f6 48 0f
Feb 04 12:37:48 x230 kernel: ---[ end trace 075e06daef46bd12 ]---
Feb 04 12:37:48 x230 kernel: WARNING: CPU: 2 PID: 36 at  /build/linux-uQJ2um/linux-4.15.0/net/mac80211/driver-ops.c:39  drv_stop+0xed/0x100 [mac
Feb 04 12:37:48 x230 kernel: Modules linked in: ccm cmac bnep btusb  btrtl btbcm btintel bluetooth ecdh_generic intel_rapl snd_hda_codec_hdmi  x
Feb 04 12:37:48 x230 kernel:  nf_conntrack_broadcast nf_nat_ftp nf_nat  nf_conntrack_ftp nf_conntrack libcrc32c sch_fq_codel sunrpc iptable_fil
Feb 04 12:37:48 x230 kernel: CPU: 2 PID: 36 Comm: kworker/2:1 Tainted: G        W        4.15.0-45-generic #48-Ubuntu
Feb 04 12:37:48 x230 kernel: Hardware name: LENOVO 2325BP9/2325BP9, BIOS G2ETB0WW (2.70 ) 09/25/2017
Feb 04 12:37:48 x230 kernel: Workqueue: events_freezable ieee80211_restart_work [mac80211]
Feb 04 12:37:48 x230 kernel: RIP: 0010:drv_stop+0xed/0x100 [mac80211]
Feb 04 12:37:48 x230 kernel: RSP: 0018:ffffa3dcc0e07c28 EFLAGS: 00010246
Feb 04 12:37:48 x230 kernel: RAX: 0000000000000000 RBX: ffff8bc50a5d0760 RCX: 0000000000000000
Feb 04 12:37:48 x230 kernel: RDX: ffff8bc514b9c440 RSI: 0000000000000286 RDI: ffff8bc50a5d0760
Feb 04 12:37:48 x230 kernel: RBP: ffffa3dcc0e07c38 R08: 0000000000000000 R09: 0000000000000000
Feb 04 12:37:48 x230 kernel: R10: ffffa3dcc0e07c48 R11: 0000000000000000 R12: ffff8bc50a5d0ff0
Feb 04 12:37:48 x230 kernel: R13: ffff8bc50a5d0ee8 R14: ffff8bc50a5d0760 R15: ffff8bc509729380
Feb 04 12:37:48 x230 kernel: FS:  0000000000000000(0000) GS:ffff8bc51e280000(0000) knlGS:0000000000000000
Feb 04 12:37:48 x230 kernel: CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Feb 04 12:37:48 x230 kernel: CR2: 00007fdcfeb2e000 CR3: 0000000062c0a006 CR4: 00000000001606e0
Feb 04 12:37:48 x230 kernel: Call Trace:
Feb 04 12:37:48 x230 kernel:  ieee80211_stop_device+0x43/0x50 [mac80211]
Feb 04 12:37:48 x230 kernel:  ieee80211_do_stop+0x4cb/0x7f0 [mac80211]
Feb 04 12:37:48 x230 kernel:  ? qdisc_reset+0x2b/0x70
Feb 04 12:37:48 x230 kernel:  ieee80211_stop+0x1a/0x20 [mac80211]
Feb 04 12:37:48 x230 kernel:  __dev_close_many+0xa5/0x110
Feb 04 12:37:48 x230 kernel:  dev_close_many+0x8c/0x140
Feb 04 12:37:48 x230 kernel:  dev_close.part.88+0x4a/0x70
Feb 04 12:37:48 x230 kernel:  dev_close+0x19/0x20
Feb 04 12:37:48 x230 kernel:  cfg80211_shutdown_all_interfaces+0x77/0xc0 [cfg80211]
Feb 04 12:37:48 x230 kernel:  ieee80211_handle_reconfig_failure+0x98/0xb0 [mac80211]
Feb 04 12:37:48 x230 kernel:  ieee80211_reconfig+0x236/0xfc0 [mac80211]
Feb 04 12:37:48 x230 kernel:  ieee80211_restart_work+0x9e/0xd0 [mac80211]
Feb 04 12:37:48 x230 kernel:  process_one_work+0x1de/0x410
Feb 04 12:37:48 x230 kernel:  worker_thread+0x32/0x410
Feb 04 12:37:48 x230 kernel:  kthread+0x121/0x140
Feb 04 12:37:48 x230 kernel:  ? process_one_work+0x410/0x410
Feb 04 12:37:48 x230 kernel:  ? kthread_create_worker_on_cpu+0x70/0x70
Feb 04 12:37:48 x230 kernel:  ret_from_fork+0x35/0x40
Feb 04 12:37:48 x230 kernel: Code: 54 09 00 4d 85 e4 74 1e 49 8b 04 24  49 8b 7c 24 08 49 83 c4 18 48 89 de e8 e1 27 e0 f1 49 8b 04 24 48 85 c0
Feb 04 12:37:48 x230 kernel: ---[ end trace 075e06daef46bd13 ]---
Feb 04 12:37:48 x230 wpa_supplicant[1052]: wlp3s0: CTRL-EVENT-SCAN-FAILED ret=-100 retry=1
Feb 04 12:37:48 x230 wpa_supplicant[1052]: wlp3s0: CTRL-EVENT-SCAN-FAILED ret=-100 retry=1
Feb 04 12:37:48 x230 nm-dispatcher[2585]: req:2 'connectivity-change': start running ordered scripts...
Feb 04 12:37:49 x230 gnome-software[2392]: failed to call  gs_plugin_add_featured on snap: lookup api.snapcraft.io on  127.0.0.53:53: server mis
Feb 04 12:37:49 x230 gnome-software[2392]: failed to call  gs_plugin_add_popular on snap: lookup api.snapcraft.io on 127.0.0.53:53:  server misb
Feb 04 12:37:49 x230 gnome-software[2392]: failed to call  gs_plugin_add_category_apps on snap: lookup api.snapcraft.io on  127.0.0.53:53: serve
Feb 04 12:37:49 x230 gnome-software[2392]: hiding category productivity  featured applications: found only 0 to show, need at least 9
Feb 04 12:37:49 x230 gnome-software[2392]: failed to call  gs_plugin_add_category_apps on snap: lookup api.snapcraft.io on  127.0.0.53:53: serve
Feb 04 12:37:50 x230 PackageKit[1303]: resolve transaction /226_cabccace from uid 1000 finished with success after 406ms
Feb 04 12:37:50 x230 PackageKit[1303]: resolve transaction /227_cbaecdea from uid 1000 finished with success after 411ms
Feb 04 12:37:50 x230 gnome-software[2392]: hiding category graphics featured applications: found only 1 to show, need at least 9
Feb 04 12:37:51 x230 PackageKit[1303]: resolve transaction /228_babddaeb from uid 1000 finished with success after 415ms
Feb 04 12:37:51 x230 gnome-software[2392]: Only 8 apps for popular list, hiding
Feb 04 12:38:09 x230 wpa_supplicant[1052]: wlp3s0: CTRL-EVENT-SCAN-FAILED ret=-100
Feb 04 12:38:42 x230 wpa_supplicant[1052]: wlp3s0: CTRL-EVENT-SCAN-FAILED ret=-100
Feb 04 12:39:25 x230 NetworkManager[1051]: <info>  [1549280365.3283] manager: rfkill: WiFi hardware radio set disabled
Feb 04 12:39:25 x230 wpa_supplicant[1052]: rfkill: WLAN soft blocked
Feb 04 12:39:25 x230 NetworkManager[1051]: <info>   [1549280365.3285] device (wlp3s0): state change: disconnected ->  unavailable (reason 'none'
Feb 04 12:39:25 x230 NetworkManager[1051]: <info>   [1549280365.3302] audit: op="radio-control" arg="wireless-enabled:0"  pid=1719 uid=1000 resu
Feb 04 12:39:25 x230 NetworkManager[1051]: <info>   [1549280365.3334] manager: rfkill: WiFi now disabled by radio  killswitch
Feb 04 12:39:25 x230 wpa_supplicant[1052]: nl80211: deinit ifname=wlp3s0 disabled_11b_rates=0
Feb 04 12:39:36 x230 NetworkManager[1051]: <info>  [1549280376.1139] manager: rfkill: WiFi hardware radio set enabled
Feb 04 12:39:36 x230 kernel: iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
Feb 04 12:39:36 x230 kernel: iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
Feb 04 12:39:36 x230 kernel: IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
Feb 04 12:39:36 x230 NetworkManager[1051]: <info>   [1549280376.5163] audit: op="radio-control" arg="wireless-enabled:1"  pid=1719 uid=1000 resu
Feb 04 12:39:36 x230 NetworkManager[1051]: <info>  [1549280376.5169] manager: rfkill: WiFi now enabled by radio killswitch
Feb 04 12:39:36 x230 wpa_supplicant[1052]: dbus:  fill_dict_with_properties dbus_interface=fi.w1.wpa_supplicant1.Interface  dbus_property=Statio
Feb 04 12:39:36 x230 wpa_supplicant[1052]: dbus: wpa_dbus_get_object_properties: failed to get object properties: (none) none
Feb 04 12:39:36 x230 wpa_supplicant[1052]: dbus: Failed to construct signal
Feb 04 12:39:36 x230 wpa_supplicant[1052]: dbus:  fill_dict_with_properties dbus_interface=fi.w1.wpa_supplicant1.Interface  dbus_property=Statio
Feb 04 12:39:36 x230 NetworkManager[1051]: <info>   [1549280376.5798] device (wlp3s0): supplicant interface state: starting  -> ready
Feb 04 12:39:36 x230 NetworkManager[1051]: <info>   [1549280376.5798] device (wlp3s0): state change: unavailable ->  disconnected (reason 'suppl
Feb 04 12:39:36 x230 kernel: IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
Feb 04 12:39:39 x230 NetworkManager[1051]: <info>  [1549280379.7378] policy: auto-activating connection 'UPCAD77541'
Feb 04 12:39:39 x230 NetworkManager[1051]: <info>   [1549280379.7388] device (wlp3s0): Activation: starting connection  'UPCAD77541' (8a391770-0
Feb 04 12:39:39 x230 NetworkManager[1051]: <info>   [1549280379.7390] device (wlp3s0): state change: disconnected ->  prepare (reason 'none', sy
Feb 04 12:39:39 x230 NetworkManager[1051]: <info>  [1549280379.7392] manager: NetworkManager state is now CONNECTING
Feb 04 12:39:39 x230 NetworkManager[1051]: <info>   [1549280379.7527] device (wlp3s0): set-hw-addr: set-cloned MAC address  to 5A:5F:6F:16:AA:11
Feb 04 12:39:39 x230 kernel: iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
Feb 04 12:39:40 x230 kernel: iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
Feb 04 12:39:40 x230 kernel: IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
Feb 04 12:39:40 x230 NetworkManager[1051]: <info>   [1549280380.1601] device (wlp3s0): supplicant interface state: ready  -> disabled
Feb 04 12:39:40 x230 NetworkManager[1051]: <info>   [1549280380.1607] device (wlp3s0): state change: prepare -> config  (reason 'none', sys-ifac
Feb 04 12:39:40 x230 NetworkManager[1051]: <info>   [1549280380.1610] device (wlp3s0): Activation: (wifi) access point  'UPCAD77541' has securit
Feb 04 12:39:40 x230 NetworkManager[1051]: <info>   [1549280380.1610] device (wlp3s0): state change: config -> need-auth  (reason 'none', sys-if
Feb 04 12:39:40 x230 NetworkManager[1051]: <info>   [1549280380.1612] sup-iface[0x557d5def2500,wlp3s0]: wps: type pbc  start...
Feb 04 12:39:40 x230 NetworkManager[1051]: <info>   [1549280380.1657] device (wlp3s0): state change: need-auth ->  prepare (reason 'none', sys-i
Feb 04 12:39:40 x230 NetworkManager[1051]: <info>   [1549280380.1662] device (wlp3s0): state change: prepare -> config  (reason 'none', sys-ifac
Feb 04 12:39:40 x230 NetworkManager[1051]: <info>   [1549280380.1664] device (wlp3s0): Activation: (wifi) connection  'UPCAD77541' has security,
Feb 04 12:39:40 x230 NetworkManager[1051]: <info>  [1549280380.1665] Config: added 'ssid' value 'XXXX'
Feb 04 12:39:40 x230 NetworkManager[1051]: <info>  [1549280380.1665] Config: added 'scan_ssid' value '1'
Feb 04 12:39:40 x230 NetworkManager[1051]: <info>  [1549280380.1665] Config: added 'bgscan' value 'simple:30:-80:86400'
lines 5898-5934
Feb 04 12:39:25 x230 wpa_supplicant[1052]: rfkill: WLAN soft blocked
Feb 04 12:39:25 x230 NetworkManager[1051]: <info>   [1549280365.3285] device (wlp3s0): state change: disconnected ->  unavailable (reason 'none'
Feb 04 12:39:25 x230 NetworkManager[1051]: <info>   [1549280365.3302] audit: op="radio-control" arg="wireless-enabled:0"  pid=1719 uid=1000 resu
Feb 04 12:39:25 x230 NetworkManager[1051]: <info>   [1549280365.3334] manager: rfkill: WiFi now disabled by radio  killswitch
Feb 04 12:39:25 x230 wpa_supplicant[1052]: nl80211: deinit ifname=wlp3s0 disabled_11b_rates=0
Feb 04 12:39:36 x230 NetworkManager[1051]: <info>  [1549280376.1139] manager: rfkill: WiFi hardware radio set enabled
Feb 04 12:39:36 x230 kernel: iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
Feb 04 12:39:36 x230 kernel: iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
Feb 04 12:39:36 x230 kernel: IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
Feb 04 12:39:36 x230 NetworkManager[1051]: <info>   [1549280376.5163] audit: op="radio-control" arg="wireless-enabled:1"  pid=1719 uid=1000 resu
Feb 04 12:39:36 x230 NetworkManager[1051]: <info>  [1549280376.5169] manager: rfkill: WiFi now enabled by radio killswitch
Feb 04 12:39:36 x230 wpa_supplicant[1052]: dbus:  fill_dict_with_properties dbus_interface=fi.w1.wpa_supplicant1.Interface  dbus_property=Statio
Feb 04 12:39:36 x230 wpa_supplicant[1052]: dbus: wpa_dbus_get_object_properties: failed to get object properties: (none) none
Feb 04 12:39:36 x230 wpa_supplicant[1052]: dbus: Failed to construct signal
Feb 04 12:39:36 x230 wpa_supplicant[1052]: dbus:  fill_dict_with_properties dbus_interface=fi.w1.wpa_supplicant1.Interface  dbus_property=Statio
Feb 04 12:39:36 x230 NetworkManager[1051]: <info>   [1549280376.5798] device (wlp3s0): supplicant interface state: starting  -> ready
Feb 04 12:39:36 x230 NetworkManager[1051]: <info>   [1549280376.5798] device (wlp3s0): state change: unavailable ->  disconnected (reason 'suppl
Feb 04 12:39:36 x230 kernel: IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
Feb 04 12:39:39 x230 NetworkManager[1051]: <info>  [1549280379.7378] policy: auto-activating connection 'UPCAD77541'
Feb 04 12:39:39 x230 NetworkManager[1051]: <info>   [1549280379.7388] device (wlp3s0): Activation: starting connection  'UPCAD77541' (8a391770-0
Feb 04 12:39:39 x230 NetworkManager[1051]: <info>   [1549280379.7390] device (wlp3s0): state change: disconnected ->  prepare (reason 'none', sy
Feb 04 12:39:39 x230 NetworkManager[1051]: <info>  [1549280379.7392] manager: NetworkManager state is now CONNECTING
Feb 04 12:39:39 x230 NetworkManager[1051]: <info>   [1549280379.7527] device (wlp3s0): set-hw-addr: set-cloned MAC address  to 5A:5F:6F:16:AA:11
Feb 04 12:39:39 x230 kernel: iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
Feb 04 12:39:40 x230 kernel: iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
Feb 04 12:39:40 x230 kernel: IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
Feb 04 12:39:40 x230 NetworkManager[1051]: <info>   [1549280380.1601] device (wlp3s0): supplicant interface state: ready  -> disabled
Feb 04 12:39:40 x230 NetworkManager[1051]: <info>   [1549280380.1607] device (wlp3s0): state change: prepare -> config  (reason 'none', sys-ifac
Feb 04 12:39:40 x230 NetworkManager[1051]: <info>   [1549280380.1610] device (wlp3s0): Activation: (wifi) access point  'UPCAD77541' has securit
Feb 04 12:39:40 x230 NetworkManager[1051]: <info>   [1549280380.1610] device (wlp3s0): state change: config -> need-auth  (reason 'none', sys-if
Feb 04 12:39:40 x230 NetworkManager[1051]: <info>   [1549280380.1612] sup-iface[0x557d5def2500,wlp3s0]: wps: type pbc  start...
Feb 04 12:39:40 x230 NetworkManager[1051]: <info>   [1549280380.1657] device (wlp3s0): state change: need-auth ->  prepare (reason 'none', sys-i
Feb 04 12:39:40 x230 NetworkManager[1051]: <info>   [1549280380.1662] device (wlp3s0): state change: prepare -> config  (reason 'none', sys-ifac
Feb 04 12:39:40 x230 NetworkManager[1051]: <info>   [1549280380.1664] device (wlp3s0): Activation: (wifi) connection  'UPCAD77541' has security,
Feb 04 12:39:40 x230 NetworkManager[1051]: <info>  [1549280380.1665] Config: added 'ssid' value 'XXX'
```

---

