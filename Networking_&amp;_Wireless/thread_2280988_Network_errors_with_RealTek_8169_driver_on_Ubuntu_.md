---
title: "Network errors with RealTek 8169 driver on Ubuntu 14.10"
date: 2015-06-03
forum: Networking &amp; Wireless
---

### Post by Eric_Christianson on 2015-06-03
I have two nic's on a box running Ubuntu 14.10. One nic is working fine, the other has errors and doesn't allow a connection.

eth0 works (not sure about wireless)

I am getting errors for the one configured as eth1: (from dmesg)
[169063.529507] r8169 0000:04:00.0 eth1: rtl_chipcmd_cond == 1 (loop: 100, delay: 100).
[169063.539656] r8169 0000:04:00.0 eth1: rtl_eriar_cond == 1 (loop: 100, delay: 100).
[169063.549748] r8169 0000:04:00.0 eth1: rtl_eriar_cond == 1 (loop: 100, delay: 100).
[169063.559845] r8169 0000:04:00.0 eth1: rtl_eriar_cond == 1 (loop: 100, delay: 100).
[169063.569935] r8169 0000:04:00.0 eth1: rtl_eriar_cond == 1 (loop: 100, delay: 100).
[169063.571106] r8169 0000:04:00.0 eth1: rtl_csiar_cond == 1 (loop: 100, delay: 10).
[169063.581302] r8169 0000:04:00.0 eth1: rtl_eriar_cond == 1 (loop: 100, delay: 100).
[169063.591494] r8169 0000:04:00.0 eth1: rtl_eriar_cond == 1 (loop: 100, delay: 100).
[169063.601584] r8169 0000:04:00.0 eth1: rtl_eriar_cond == 1 (loop: 100, delay: 100).
[169063.611676] r8169 0000:04:00.0 eth1: rtl_eriar_cond == 1 (loop: 100, delay: 100).
[169063.621784] r8169 0000:04:00.0 eth1: rtl_eriar_cond == 1 (loop: 100, delay: 100).
[169063.631987] r8169 0000:04:00.0 eth1: rtl_eriar_cond == 1 (loop: 100, delay: 100).
[169063.642207] r8169 0000:04:00.0 eth1: rtl_eriar_cond == 1 (loop: 100, delay: 100).

$ ethtool eth1  (suggests it's working, but it's not)
Settings for eth1:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised pause frame use: Symmetric Receive-only
	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  10baseT/Half 10baseT/Full 
	                                     100baseT/Half 100baseT/Full 
	                                     1000baseT/Half 1000baseT/Full 
	Link partner advertised pause frame use: Symmetric Receive-only
	Link partner advertised auto-negotiation: Yes
	Speed: 1000Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
Cannot get wake-on-lan settings: Operation not permitted
	Current message level: 0x00000033 (51)
			       drv probe ifdown ifup
	Link detected: yes

$ ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 80:ee:73:aa:37:8a  
          inet6 addr: fe80::82ee:73ff:feaa:378a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:17740 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

(tried adding:
auto eth1 inet dhcp, did not work)

$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev bb)
	Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:4070]
	Kernel driver in use: iwlwifi
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
	Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Device [1297:4017]
	Kernel driver in use: r8169
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
	Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Device [1297:4017]
	Kernel driver in use: r8169


Please let me know if I should provide any other information. I have seen similar posts about failures of r8168 and seen kernel mods for that driver. Not sure if that will work here.

~Eric

---

### Post by Eric_Christianson on 2015-06-03
Working on solving this.. 
Downloaded latest driver from RealTek:
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2)

Now the link-light shows on the second nic, but the kernel driver didn't install correctly? Not sure what to do. (eth0 still works, which is why I can post this.)

[186563.773998] INFO: task find:9725 blocked for more than 120 seconds.
[186563.774002]       Tainted: G        W  OE 3.16.0-38-generic #52-Ubuntu
[186563.774002] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[186563.774004] find            D ffff88041fb134c0     0  9725  24100 0x00000004
[186563.774007]  ffff88012170fb28 0000000000000082 ffff8803fdb55180 00000000000134c0
[186563.774009]  ffff88012170ffd8 00000000000134c0 ffff8803fdb55180 ffff8804072e84e0
[186563.774010]  ffff8803f1e5d800 ffff88012170fb50 ffff8804072e85c0 ffff8804072e84e0
[186563.774012] Call Trace:
[186563.774018]  [<ffffffff81788279>] schedule+0x29/0x70
[186563.774023]  [<ffffffff812d2a75>] __fuse_request_send+0xc5/0x290
[186563.774027]  [<ffffffff810b9880>] ? prepare_to_wait_event+0x100/0x100
[186563.774029]  [<ffffffff812d2c52>] fuse_request_send+0x12/0x20
[186563.774031]  [<ffffffff812d8c07>] fuse_lookup_name+0x117/0x200
[186563.774033]  [<ffffffff812d8d2f>] fuse_lookup+0x3f/0x110
[186563.774037]  [<ffffffff811eb60d>] lookup_real+0x1d/0x70
[186563.774039]  [<ffffffff811ec073>] __lookup_hash+0x33/0x40
[186563.774040]  [<ffffffff811f1513>] path_lookupat+0x903/0xd70
[186563.774043]  [<ffffffff810a57c2>] ? default_wake_function+0x12/0x20
[186563.774046]  [<ffffffff810b9195>] ? __wake_up_common+0x55/0x90
[186563.774050]  [<ffffffff811c3865>] ? kmem_cache_alloc+0x35/0x1f0
[186563.774051]  [<ffffffff811f295b>] ? getname_flags+0x4b/0x180
[186563.774053]  [<ffffffff811f19aa>] filename_lookup+0x2a/0xd0
[186563.774054]  [<ffffffff811f3854>] user_path_at_empty+0x54/0xb0
[186563.774056]  [<ffffffff811f38c1>] user_path_at+0x11/0x20
[186563.774058]  [<ffffffff811e6b22>] vfs_fstatat+0x52/0xa0
[186563.774060]  [<ffffffff811e6fbf>] SYSC_newstat+0x1f/0x40
[186563.774063]  [<ffffffff81091c0c>] ? task_work_run+0xbc/0xf0
[186563.774067]  [<ffffffff810131f7>] ? do_notify_resume+0x97/0xb0
[186563.774070]  [<ffffffff8178d3ca>] ? int_signal+0x12/0x17
[186563.774072]  [<ffffffff811e721e>] SyS_newstat+0xe/0x10
[186563.774073]  [<ffffffff8178d10d>] system_call_fastpath+0x1a/0x1f

---

### Post by Eric_Christianson on 2015-06-03
Rebooting after blacklisting r8169 worked.

---

