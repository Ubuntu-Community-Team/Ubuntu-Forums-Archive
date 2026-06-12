---
title: "mt76x0u isn't working since kernel 5.4-54"
date: 2021-01-24
forum: Networking &amp; Wireless
---

### Post by sadayelle on 2021-01-24
I have installed in my computer Ubuntu and Kubuntu 20.04, both are installed in different hard disks, every kernel upgrade after kernel 5.4-54 results in a permanent hang when using a TP-Link Archer T2U, no matter if I connect the dongle after booting the system or from the beginning, so I tried different linux systems, Ubuntu 20.10 with kernel 5.8 it is ok, Manjaro with kernel 5.9 as well, not any issue and working properly, so my doubt it is if this issue is going to be fixed in the next kernel versions or if there is the possibility that 20.04 is going to jump to kernel 5.6 soon, I would like to paste some screenshots with command line outputs, but it's seems impossible because it starts to hang graphically and I never was able to, even if I use other tty. When I try to shutdown and restart freezes. Any help or advice is welcomed, thanks.

---

### Post by jeremy31 on 2021-01-25
Can you boot into 5.4.0-54 and enable proposed repos?  Then in terminal do
```
sudo apt update && sudo apt install linux-generic
```

---

### Post by morrownr on 2021-01-25
jeremy31,

For what it is worth: My adapter based on a MT7612u is still seriously broken on 5.4.0-64-generic. I am still compiling the the patched code you threw up on your github site. It works well.

I have tested with kernels 5.8, 5.9 and 5.10 on other systems and I am not seeing the breakage there so this is specific to 5.4 but I suspect you know that.

---

### Post by sadayelle on 2021-01-25
Hello, thanks for your response, I did what you ask me to do, and the same problem persist, I could observe that in the previous moment when system freezes, Network Manager is stucked in the step "asking for an ip address..."
In my previous post I didn't specify that now I'm on Linux Mint Ulyssa, but since it's based on Ubuntu 20.04 and I was having the same issue in Ubuntu 20.04 I suppossed it's going to be more convinient to check for help here, so here I found something in the kern.log, I hope is going to be useful, thanks in advance.

```
Jan 25 15:07:50 xftux-MS-7970 kernel: [    3.907296] usb 1-6: reset high-speed USB device number 2 using xhci_hcd
Jan 25 15:07:50 xftux-MS-7970 kernel: [    4.061186] mt76x0u 1-6:1.0: ASIC revision: 76100002 MAC revision: 76502000
Jan 25 15:07:50 xftux-MS-7970 kernel: [    4.278853] EXT4-fs (sdc1): mounted filesystem with ordered data mode. Opts: (null)
Jan 25 15:07:50 xftux-MS-7970 kernel: [    4.361249] mt76x0u 1-6:1.0: EEPROM ver:02 fae:01
Jan 25 15:07:50 xftux-MS-7970 kernel: [    4.601531] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
Jan 25 15:07:50 xftux-MS-7970 kernel: [    4.601871] usbcore: registered new interface driver mt76x0u
Jan 25 15:07:50 xftux-MS-7970 kernel: [    4.609892] mt76x0u 1-6:1.0 wlx503eaa4a6f3f: renamed from wlan0
Jan 25 15:07:50 xftux-MS-7970 kernel: [   93.442811] kauditd_printk_skb: 14 callbacks suppressed
Jan 25 15:07:50 xftux-MS-7970 kernel: [   93.442812] audit: type=1400 audit(1611587270.373:25): apparmor="DENIED" operation="capable" profile="/usr/sbin/cups-browsed" pid=947 comm="cups-browsed" capability=23  capname="sys_nice"
Jan 25 15:07:50 xftux-MS-7970 kernel: [   93.641469] Generic FE-GE Realtek PHY r8169-400:00: attached PHY driver [Generic FE-GE Realtek PHY] (mii_bus:phy_addr=r8169-400:00, irq=IGNORE)
Jan 25 15:07:50 xftux-MS-7970 kernel: [   93.751967] r8169 0000:04:00.0 enp4s0: Link is Down
Jan 25 15:07:55 xftux-MS-7970 kernel: [   98.782814] wlx503eaa4a6f3f: authenticate with 0c:80:63:f2:c7:9d
Jan 25 15:07:56 xftux-MS-7970 kernel: [   99.611461] wlx503eaa4a6f3f: send auth to 0c:80:63:f2:c7:9d (try 1/3)
Jan 25 15:07:56 xftux-MS-7970 kernel: [   99.612958] wlx503eaa4a6f3f: authenticated
Jan 25 15:07:56 xftux-MS-7970 kernel: [   99.614874] wlx503eaa4a6f3f: associate with 0c:80:63:f2:c7:9d (try 1/3)
Jan 25 15:07:56 xftux-MS-7970 kernel: [   99.629019] wlx503eaa4a6f3f: RX AssocResp from 0c:80:63:f2:c7:9d (capab=0x931 status=0 aid=2)
Jan 25 15:07:56 xftux-MS-7970 kernel: [   99.631935] wlx503eaa4a6f3f: associated
Jan 25 15:07:56 xftux-MS-7970 kernel: [   99.868333] IPv6: ADDRCONF(NETDEV_CHANGE): wlx503eaa4a6f3f: link becomes ready
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741553] INFO: task kworker/u8:1:99 blocked for more than 120 seconds.
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741561]       Not tainted 5.4.0-64-generic #72-Ubuntu
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741563] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741567] kworker/u8:1    D    0    99      2 0x80004000
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741622] Workqueue: phy0 ieee80211_iface_work [mac80211]
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741625] Call Trace:
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741637]  __schedule+0x2e3/0x740
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741643]  schedule+0x42/0xb0
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741648]  schedule_preempt_disabled+0xe/0x10
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741652]  __mutex_lock.isra.0+0x182/0x4f0
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741658]  ? urb_destroy+0x1c/0x40
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741664]  __mutex_lock_slowpath+0x13/0x20
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741668]  mutex_lock+0x2e/0x40
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741678]  mt76x02_ampdu_action+0x60/0x1c0 [mt76x02_lib]
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741707]  drv_ampdu_action+0x75/0x150 [mac80211]
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741740]  ieee80211_agg_tx_operational+0xb7/0x120 [mac80211]
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741771]  ieee80211_process_addba_resp+0x218/0x230 [mac80211]
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741803]  ieee80211_iface_work+0x31b/0x330 [mac80211]
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741810]  process_one_work+0x1eb/0x3b0
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741816]  worker_thread+0x4d/0x400
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741821]  kthread+0x104/0x140
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741825]  ? process_one_work+0x3b0/0x3b0
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741829]  ? kthread_park+0x90/0x90
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741835]  ret_from_fork+0x35/0x40
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741852] INFO: task kworker/1:2:248 blocked for more than 120 seconds.
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741856]       Not tainted 5.4.0-64-generic #72-Ubuntu
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741858] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741861] kworker/1:2     D    0   248      2 0x80004000
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741872] Workqueue: ipv6_addrconf addrconf_dad_work
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741874] Call Trace:
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741879]  __schedule+0x2e3/0x740
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741884]  schedule+0x42/0xb0
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741889]  schedule_preempt_disabled+0xe/0x10
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741893]  __mutex_lock.isra.0+0x182/0x4f0
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741899]  ? __switch_to_asm+0x40/0x70
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741904]  ? __switch_to_asm+0x34/0x70
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741909]  ? __switch_to_asm+0x34/0x70
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741914]  ? __switch_to_asm+0x40/0x70
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741919]  __mutex_lock_slowpath+0x13/0x20
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741923]  mutex_lock+0x2e/0x40
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741928]  rtnl_lock+0x15/0x20
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741933]  addrconf_dad_work+0x3e/0x420
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741937]  ? __schedule+0x2eb/0x740
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741943]  process_one_work+0x1eb/0x3b0
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741948]  worker_thread+0x4d/0x400
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741952]  kthread+0x104/0x140
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741957]  ? process_one_work+0x3b0/0x3b0
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741960]  ? kthread_park+0x90/0x90
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741966]  ret_from_fork+0x35/0x40
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741974] INFO: task avahi-daemon:867 blocked for more than 120 seconds.
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741977]       Not tainted 5.4.0-64-generic #72-Ubuntu
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741979] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741982] avahi-daemon    D    0   867      1 0x00000000
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741985] Call Trace:
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741990]  __schedule+0x2e3/0x740
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741995]  schedule+0x42/0xb0
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.741999]  schedule_preempt_disabled+0xe/0x10
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742003]  __mutex_lock.isra.0+0x182/0x4f0
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742009]  ? __wake_up_common_lock+0x8a/0xc0
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742014]  __mutex_lock_slowpath+0x13/0x20
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742018]  mutex_lock+0x2e/0x40
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742022]  rtnl_lock+0x15/0x20
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742028]  do_ip_setsockopt.isra.0+0x49/0x1590
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742032]  ? sock_def_readable+0x40/0x70
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742036]  ? unix_dgram_sendmsg+0x530/0x710
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742043]  ? sock_sendmsg+0x65/0x70
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742048]  ? __sys_sendto+0x113/0x190
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742056]  ? __cgroup_bpf_run_filter_setsockopt+0xae/0x2d0
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742061]  ip_setsockopt+0x34/0xc0
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742066]  udp_setsockopt+0x1b/0x30
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742070]  sock_common_setsockopt+0x1a/0x20
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742074]  __sys_setsockopt+0xcc/0x180
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742080]  __x64_sys_setsockopt+0x25/0x30
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742086]  do_syscall_64+0x57/0x190
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742092]  entry_SYSCALL_64_after_hwframe+0x44/0xa9
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742096] RIP: 0033:0x7f5a8e1c78ae
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742105] Code: Bad RIP value.
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742108] RSP: 002b:00007ffd10ec3e68 EFLAGS: 00000202 ORIG_RAX: 0000000000000036
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742112] RAX: ffffffffffffffda RBX: 0000000000000001 RCX: 00007f5a8e1c78ae
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742114] RDX: 0000000000000024 RSI: 0000000000000000 RDI: 000000000000000c
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742116] RBP: 000000000000000c R08: 000000000000000c R09: 0000000000000001
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742118] R10: 00007ffd10ec3e74 R11: 0000000000000202 R12: 00007ffd10ec3e74
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742120] R13: 0000558595e4b9f0 R14: 0000558595e47a60 R15: 0000000000000014
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742126] INFO: task NetworkManager:873 blocked for more than 120 seconds.
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742130]       Not tainted 5.4.0-64-generic #72-Ubuntu
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742132] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742135] NetworkManager  D    0   873      1 0x00000000
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742138] Call Trace:
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742143]  __schedule+0x2e3/0x740
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742148]  schedule+0x42/0xb0
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742152]  schedule_preempt_disabled+0xe/0x10
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742156]  __mutex_lock.isra.0+0x182/0x4f0
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742162]  __mutex_lock_slowpath+0x13/0x20
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742166]  mutex_lock+0x2e/0x40
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742175]  mt76x02_bss_info_changed+0x2a/0x120 [mt76x02_lib]
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742203]  ieee80211_ifa_changed+0x118/0x200 [mac80211]
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742209]  notifier_call_chain+0x55/0x80
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742215]  blocking_notifier_call_chain+0x50/0x70
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742219]  __inet_insert_ifa+0x1fd/0x2e0
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742223]  inet_rtm_newaddr+0x3b1/0x480
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742230]  rtnetlink_rcv_msg+0x2c0/0x380
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742234]  ? inet_dump_ifaddr+0x250/0x250
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742238]  ? rtnetlink_rcv_msg+0x2c0/0x380
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742243]  ? __skb_try_recv_datagram+0xf3/0x160
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742248]  ? rtnl_calcit.isra.0+0x100/0x100
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742253]  netlink_rcv_skb+0x50/0x120
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742259]  rtnetlink_rcv+0x15/0x20
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742263]  netlink_unicast+0x187/0x220
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742267]  netlink_sendmsg+0x222/0x3e0
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742274]  sock_sendmsg+0x65/0x70
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742278]  ____sys_sendmsg+0x212/0x280
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742284]  ___sys_sendmsg+0x88/0xd0
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742290]  ? ___sys_recvmsg+0x88/0xc0
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742297]  ? __fget_light+0x57/0x70
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742303]  __sys_sendmsg+0x5c/0xa0
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742309]  __x64_sys_sendmsg+0x1f/0x30
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742315]  do_syscall_64+0x57/0x190
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742321]  entry_SYSCALL_64_after_hwframe+0x44/0xa9
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742324] RIP: 0033:0x7f841d4a812d
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742330] Code: Bad RIP value.
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742332] RSP: 002b:00007ffd883c6ed0 EFLAGS: 00000293 ORIG_RAX: 000000000000002e
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742335] RAX: ffffffffffffffda RBX: 000056290678b880 RCX: 00007f841d4a812d
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742337] RDX: 0000000000000000 RSI: 00007ffd883c6f20 RDI: 000000000000000c
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742339] RBP: 00007ffd883c6f20 R08: 0000000000000000 R09: 0000000000000000
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742341] R10: 0000000000000018 R11: 0000000000000293 R12: 000056290678b880
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742343] R13: 00007ffd883c70a8 R14: 00007ffd883c70a4 R15: 0000000000000000
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742354] INFO: task cups-browsed:947 blocked for more than 120 seconds.
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742357]       Not tainted 5.4.0-64-generic #72-Ubuntu
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742359] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742361] cups-browsed    D    0   947      1 0x00000000
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742364] Call Trace:
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742369]  __schedule+0x2e3/0x740
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742374]  schedule+0x42/0xb0
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742378]  schedule_preempt_disabled+0xe/0x10
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742383]  __mutex_lock.isra.0+0x182/0x4f0
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742388]  ? __netlink_lookup+0xde/0x150
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742393]  __mutex_lock_slowpath+0x13/0x20
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742397]  mutex_lock+0x2e/0x40
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742401]  __netlink_dump_start+0x59/0x200
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742406]  rtnetlink_rcv_msg+0x23a/0x380
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742411]  ? rtnl_fill_ifinfo+0xea0/0xea0
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742416]  ? rtnl_fill_ifinfo+0xea0/0xea0
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742421]  ? rtnl_calcit.isra.0+0x100/0x100
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742425]  netlink_rcv_skb+0x50/0x120
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742430]  rtnetlink_rcv+0x15/0x20
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742434]  netlink_unicast+0x187/0x220
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742439]  netlink_sendmsg+0x222/0x3e0
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742445]  sock_sendmsg+0x65/0x70
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742450]  __sys_sendto+0x113/0x190
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742456]  ? fd_install+0x27/0x30
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742461]  ? __sys_socket+0x9e/0xf0
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742467]  __x64_sys_sendto+0x29/0x30
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742472]  do_syscall_64+0x57/0x190
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742478]  entry_SYSCALL_64_after_hwframe+0x44/0xa9
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742480] RIP: 0033:0x7f511dfb2844
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742485] Code: Bad RIP value.
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742487] RSP: 002b:00007fff403ee7a0 EFLAGS: 00000293 ORIG_RAX: 000000000000002c
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742490] RAX: ffffffffffffffda RBX: 00007fff403ef940 RCX: 00007f511dfb2844
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742492] RDX: 0000000000000014 RSI: 00007fff403ef870 RDI: 000000000000000b
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742494] RBP: 0000000000000000 R08: 00007fff403ef830 R09: 000000000000000c
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742496] R10: 0000000000000000 R11: 0000000000000293 R12: 00007fff403ef830
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742498] R13: 00007fff403ef870 R14: 00007f511e2a3280 R15: 00007fff403ee7e0
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742504] INFO: task ntpd:986 blocked for more than 120 seconds.
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742507]       Not tainted 5.4.0-64-generic #72-Ubuntu
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742509] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742511] ntpd            D    0   986      1 0x00000004
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742514] Call Trace:
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742518]  __schedule+0x2e3/0x740
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742523]  schedule+0x42/0xb0
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742527]  schedule_preempt_disabled+0xe/0x10
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742531]  __mutex_lock.isra.0+0x182/0x4f0
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742536]  ? __netlink_lookup+0xde/0x150
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742541]  __mutex_lock_slowpath+0x13/0x20
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742545]  mutex_lock+0x2e/0x40
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742549]  __netlink_dump_start+0x59/0x200
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742554]  rtnetlink_rcv_msg+0x23a/0x380
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742559]  ? rtnl_fill_ifinfo+0xea0/0xea0
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742564]  ? rtnl_fill_ifinfo+0xea0/0xea0
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742569]  ? rtnl_calcit.isra.0+0x100/0x100
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742573]  netlink_rcv_skb+0x50/0x120
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742578]  rtnetlink_rcv+0x15/0x20
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742582]  netlink_unicast+0x187/0x220
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742586]  netlink_sendmsg+0x222/0x3e0
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742592]  sock_sendmsg+0x65/0x70
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742597]  __sys_sendto+0x113/0x190
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742604]  ? fd_install+0x27/0x30
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742608]  ? __sys_socket+0x9e/0xf0
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742614]  __x64_sys_sendto+0x29/0x30
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742619]  do_syscall_64+0x57/0x190
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742624]  entry_SYSCALL_64_after_hwframe+0x44/0xa9
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742627] RIP: 0033:0x7fa23817b844
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742632] Code: Bad RIP value.
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742634] RSP: 002b:00007ffdf4d1d220 EFLAGS: 00000293 ORIG_RAX: 000000000000002c
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742636] RAX: ffffffffffffffda RBX: 00007ffdf4d1e3c0 RCX: 00007fa23817b844
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742638] RDX: 0000000000000014 RSI: 00007ffdf4d1e2f0 RDI: 0000000000000004
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742640] RBP: 0000000000000000 R08: 00007ffdf4d1e2b0 R09: 000000000000000c
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742642] R10: 0000000000000000 R11: 0000000000000293 R12: 00007ffdf4d1e2b0
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742643] R13: 00007ffdf4d1e2f0 R14: 000000000000007b R15: 00007ffdf4d1d260
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742668] INFO: task pool-flatpak up:1603 blocked for more than 120 seconds.
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742671]       Not tainted 5.4.0-64-generic #72-Ubuntu
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742673] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742676] pool-flatpak up D    0  1603   1428 0x00000000
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742679] Call Trace:
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742684]  __schedule+0x2e3/0x740
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742689]  schedule+0x42/0xb0
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742693]  schedule_preempt_disabled+0xe/0x10
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742697]  __mutex_lock.isra.0+0x182/0x4f0
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742702]  ? __netlink_lookup+0xde/0x150
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742707]  __mutex_lock_slowpath+0x13/0x20
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742711]  mutex_lock+0x2e/0x40
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742715]  __netlink_dump_start+0x59/0x200
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742720]  rtnetlink_rcv_msg+0x23a/0x380
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742724]  ? rtnl_xdp_prog_skb+0x70/0x70
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742729]  ? rtnl_xdp_prog_skb+0x70/0x70
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742734]  ? rtnl_calcit.isra.0+0x100/0x100
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742738]  netlink_rcv_skb+0x50/0x120
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742743]  rtnetlink_rcv+0x15/0x20
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742747]  netlink_unicast+0x187/0x220
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742751]  netlink_sendmsg+0x222/0x3e0
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742757]  sock_sendmsg+0x65/0x70
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742762]  __sys_sendto+0x113/0x190
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742768]  ? handle_mm_fault+0xca/0x200
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742775]  ? do_user_addr_fault+0x216/0x450
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742781]  __x64_sys_sendto+0x29/0x30
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742786]  do_syscall_64+0x57/0x190
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742792]  entry_SYSCALL_64_after_hwframe+0x44/0xa9
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742794] RIP: 0033:0x7f5106c43844
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742799] Code: Bad RIP value.
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742801] RSP: 002b:00007f5101e4a4d0 EFLAGS: 00000293 ORIG_RAX: 000000000000002c
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742804] RAX: ffffffffffffffda RBX: 00007f5101e4b5f0 RCX: 00007f5106c43844
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742805] RDX: 0000000000000014 RSI: 00007f5101e4b5f0 RDI: 0000000000000019
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742807] RBP: 0000000000000000 R08: 00007f5101e4b594 R09: 000000000000000c
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742809] R10: 0000000000000000 R11: 0000000000000293 R12: 00007f5101e4b594
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742811] R13: 00007f5101e4bc30 R14: 00007f5101e4b5b0 R15: 0000000000000019
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742816] INFO: task evolution-calen:1636 blocked for more than 120 seconds.
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742819]       Not tainted 5.4.0-64-generic #72-Ubuntu
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742821] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742823] evolution-calen D    0  1636   1202 0x00000000
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742826] Call Trace:
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742831]  __schedule+0x2e3/0x740
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742837]  ? get_page_from_freelist+0x1dc/0x390
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742842]  schedule+0x42/0xb0
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742846]  schedule_preempt_disabled+0xe/0x10
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742850]  __mutex_lock.isra.0+0x182/0x4f0
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742856]  ? __mod_lruvec_state+0x44/0xf0
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742860]  ? __netlink_lookup+0xde/0x150
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742865]  __mutex_lock_slowpath+0x13/0x20
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742869]  mutex_lock+0x2e/0x40
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742873]  __netlink_dump_start+0x59/0x200
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742878]  rtnetlink_rcv_msg+0x23a/0x380
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742882]  ? rtnl_xdp_prog_skb+0x70/0x70
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742886]  ? rtnl_xdp_prog_skb+0x70/0x70
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742891]  ? rtnl_calcit.isra.0+0x100/0x100
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742896]  netlink_rcv_skb+0x50/0x120
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742901]  rtnetlink_rcv+0x15/0x20
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742904]  netlink_unicast+0x187/0x220
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742909]  netlink_sendmsg+0x222/0x3e0
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742915]  sock_sendmsg+0x65/0x70
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742920]  __sys_sendto+0x113/0x190
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742928]  ? fput+0x13/0x15
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742932]  ? __sys_setsockopt+0x153/0x180
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742938]  __x64_sys_sendto+0x29/0x30
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742943]  do_syscall_64+0x57/0x190
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742948]  entry_SYSCALL_64_after_hwframe+0x44/0xa9
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742950] RIP: 0033:0x7fd9a96e56dc
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742956] Code: Bad RIP value.
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742958] RSP: 002b:00007fd99d340ce0 EFLAGS: 00000246 ORIG_RAX: 000000000000002c
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742960] RAX: ffffffffffffffda RBX: 000056269ec09670 RCX: 00007fd9a96e56dc
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742962] RDX: 0000000000000014 RSI: 00007fd99d340d60 RDI: 000000000000000a
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742964] RBP: 0000000000000000 R08: 0000000000000000 R09: 0000000000000000
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742966] R10: 0000000000004000 R11: 0000000000000246 R12: 0000000000000000
Jan 25 15:10:19 xftux-MS-7970 kernel: [  242.742968] R13: 00007fd99d340d60 R14: 0000000000000014 R15: 00000000062192c4
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.575796] INFO: task kworker/u8:1:99 blocked for more than 241 seconds.
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.575803]       Not tainted 5.4.0-64-generic #72-Ubuntu
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.575806] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.575810] kworker/u8:1    D    0    99      2 0x80004000
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.575865] Workqueue: phy0 ieee80211_iface_work [mac80211]
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.575868] Call Trace:
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.575880]  __schedule+0x2e3/0x740
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.575886]  schedule+0x42/0xb0
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.575890]  schedule_preempt_disabled+0xe/0x10
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.575895]  __mutex_lock.isra.0+0x182/0x4f0
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.575901]  ? urb_destroy+0x1c/0x40
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.575907]  __mutex_lock_slowpath+0x13/0x20
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.575912]  mutex_lock+0x2e/0x40
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.575921]  mt76x02_ampdu_action+0x60/0x1c0 [mt76x02_lib]
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.575951]  drv_ampdu_action+0x75/0x150 [mac80211]
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.575984]  ieee80211_agg_tx_operational+0xb7/0x120 [mac80211]
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.576015]  ieee80211_process_addba_resp+0x218/0x230 [mac80211]
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.576047]  ieee80211_iface_work+0x31b/0x330 [mac80211]
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.576055]  process_one_work+0x1eb/0x3b0
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.576060]  worker_thread+0x4d/0x400
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.576065]  kthread+0x104/0x140
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.576070]  ? process_one_work+0x3b0/0x3b0
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.576073]  ? kthread_park+0x90/0x90
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.576080]  ret_from_fork+0x35/0x40
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.576091] INFO: task kworker/u8:5:220 blocked for more than 120 seconds.
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.576095]       Not tainted 5.4.0-64-generic #72-Ubuntu
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.576098] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.576101] kworker/u8:5    D    0   220      2 0x80004000
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.576142] Workqueue: events_power_efficient reg_check_chans_work [cfg80211]
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.576144] Call Trace:
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.576150]  __schedule+0x2e3/0x740
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.576155]  schedule+0x42/0xb0
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.576160]  schedule_preempt_disabled+0xe/0x10
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.576164]  __mutex_lock.isra.0+0x182/0x4f0
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.576170]  ? __switch_to_asm+0x40/0x70
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.576175]  ? __switch_to_asm+0x34/0x70
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.576180]  ? __switch_to_asm+0x34/0x70
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.576185]  ? __switch_to_asm+0x40/0x70
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.576190]  ? __switch_to_asm+0x40/0x70
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.576195]  __mutex_lock_slowpath+0x13/0x20
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.576199]  mutex_lock+0x2e/0x40
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.576205]  rtnl_lock+0x15/0x20
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.576229]  reg_check_chans_work+0x2f/0x3b0 [cfg80211]
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.576234]  ? __schedule+0x2eb/0x740
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.576256]  ? commit_tail+0xc9/0x110 [drm_kms_helper]
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.576262]  process_one_work+0x1eb/0x3b0
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.576267]  worker_thread+0x4d/0x400
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.576272]  kthread+0x104/0x140
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.576276]  ? process_one_work+0x3b0/0x3b0
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.576279]  ? kthread_park+0x90/0x90
Jan 25 15:12:20 xftux-MS-7970 kernel: [  363.576285]  ret_from_fork+0x35/0x40
Jan 25 15:19:21 xftux-MS-7970 kernel: [  784.819537] usb 1-6: USB disconnect, device number 2
Jan 25 15:19:21 xftux-MS-7970 kernel: [  784.819559] mt76x0u 1-6:1.0: rx urb failed: -71
Jan 25 15:19:21 xftux-MS-7970 kernel: [  784.819595] mt76x0u 1-6:1.0: rx urb failed: -71
Jan 25 15:19:21 xftux-MS-7970 kernel: [  784.819634] mt76x0u 1-6:1.0: rx urb failed: -71
Jan 25 15:19:21 xftux-MS-7970 kernel: [  784.819674] mt76x0u 1-6:1.0: rx urb failed: -71
Jan 25 15:19:21 xftux-MS-7970 kernel: [  784.819714] mt76x0u 1-6:1.0: rx urb failed: -71
Jan 25 15:19:21 xftux-MS-7970 kernel: [  784.819754] mt76x0u 1-6:1.0: rx urb failed: -71
Jan 25 15:19:21 xftux-MS-7970 kernel: [  784.819794] mt76x0u 1-6:1.0: rx urb failed: -71
Jan 25 15:19:21 xftux-MS-7970 kernel: [  784.819834] mt76x0u 1-6:1.0: rx urb failed: -71
Jan 25 15:19:21 xftux-MS-7970 kernel: [  784.819874] mt76x0u 1-6:1.0: rx urb failed: -71
Jan 25 15:19:21 xftux-MS-7970 kernel: [  784.819914] mt76x0u 1-6:1.0: rx urb failed: -71
Jan 25 15:19:21 xftux-MS-7970 kernel: [  784.820230] xhci_hcd 0000:00:14.0: WARN Cannot submit Set TR Deq Ptr
Jan 25 15:19:21 xftux-MS-7970 kernel: [  784.820233] xhci_hcd 0000:00:14.0: A Set TR Deq Ptr command is pending.
```

---

### Post by jeremy31 on 2021-01-25
While in a kernel with working wifi do ```
sudo apt install git dkms
git clone https://github.com/jeremyb31/mt76.git
```
Then boot into the newest non working kernel
```
sudo dkms add ./mt76
sudo dkms install mt76-5.4/1
```

Reboot

> **morrownr said:**
> jeremy31,

For what it is worth: My adapter based on a MT7612u is still seriously broken on 5.4.0-64-generic. I am still compiling the the patched code you threw up on your github site. It works well.

I have tested with kernels 5.8, 5.9 and 5.10 on other systems and I am not seeing the breakage there so this is specific to 5.4 but I suspect you know that.

Yes, back in December the Ubuntu kernel brought in a commit from the upstream 5.4 LTS that caused the issue.  The bug report I was working on is [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1906770](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1906770)  The fix the Ubuntu proposed kernel has is also from upstream [https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/commit/drivers?h=v5.10&id=05d6c8cfdbd6cefac6b373bad72775fcc4193c80](https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/commit/drivers?h=v5.10&id=05d6c8cfdbd6cefac6b373bad72775fcc4193c80)

---

### Post by sadayelle on 2021-01-26
Solved!! It works pretty well on Linux Mint too, once again thank you so much jeremy31 for your help. :)

---

