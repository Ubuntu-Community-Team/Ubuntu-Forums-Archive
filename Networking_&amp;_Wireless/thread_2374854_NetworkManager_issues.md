---
title: "NetworkManager issues"
date: 2017-10-19
forum: Networking &amp; Wireless
---

### Post by gk3334 on 2017-10-19
I just installed Ubuntu 17.10.
Every time I try to disconnect from WiFi,
    one: It doesn&#8217;t show that I&#8217;m disconnected.
    two: I can&#8217;t reconnect to Wifi.
    three: When I try to reboot, it freezes on me.
four: When I try to use sudo, it freezes.
Please help.

---

### Post by ynota on 2017-10-19
I think you may mean Ubuntu 17.10... :) Are you able to drop out to a TTY with Ctl + Alt + F2? If so you can try the  'dmesg' command for clues to the cause of the screen freeze.

---

### Post by Bucky Ball on 2017-10-19
Welcome. What is make, model, specs of your machine and have you installed a wireless driver or graphics driver?

Boot the machine and if you can get online and before it crashes, open a terminal and input these two commands one at a time.

```
sudo lshw -C network
sudo lshw -C video
```

Post the output of each here separately and please use [code] tags (see my signature if you don't know how). ;)

(*Note: Not sure that 17.10 has even been released quite yet, but even if it has, you may experience some teething issues and instability. A better place to start with Ubuntu is with a stable, long-term support release that has been out for awhile and had bugs squashed (with the caveat that if your machine is very new (last six months) you may need the newest release for the latest drivers it contains. The current LTS release (supported for five years until 2021) is 16.04 LTS. 

Interim releases, like 17.10, are supported for nine months.)

---

### Post by gk3334 on 2017-10-20
Output of lshw -C network
```

 *-network                 
       description: Wireless interface
       product: QCA9377 802.11ac Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 31
       serial: 94:e9:79:92:de:81
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath10k_pci driverversion=4.13.0-16-generic firmware=WLAN.TF.1.0-00267-1 ip=172.20.10.2 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:131 memory:b1000000-b11fffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.1
       bus info: pci@0000:03:00.1
       logical name: enp3s0f1
       version: 12
       serial: 
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8411-2_0.0.1 07/08/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:127 ioport:3000(size=256) memory:b1204000-b1204fff memory:b1200000-b1203fff


```

Output of lshw -C video
```

 *-display                 
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:129 memory:b0000000-b0ffffff memory:a0000000-afffffff ioport:4000(size=64) memory:c0000-dffff


```

---

### Post by gk3334 on 2017-10-20
Here is the output of (dmesg | tail -n 160) after trying to disconnect from WiFi
```

[   28.483414] NET: Registered protocol family 5
[   28.943417] pcieport 0000:00:1d.2: AER: Multiple Corrected error received: id=00ea
[   28.943441] pcieport 0000:00:1d.2: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00ea(Receiver ID)
[   28.943450] pcieport 0000:00:1d.2:   device [8086:9d1a] error status/mask=00000001/00002000
[   28.943459] pcieport 0000:00:1d.2:    [ 0] Receiver Error         (First)
[   28.943471] pcieport 0000:00:1d.2: AER: Corrected error received: id=00ea
[   28.943485] pcieport 0000:00:1d.2: can't find device of ID00ea
[   28.977968] pcieport 0000:00:1d.2: AER: Multiple Corrected error received: id=00ea
[   28.977975] pcieport 0000:00:1d.2: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00ea(Receiver ID)
[   28.977977] pcieport 0000:00:1d.2:   device [8086:9d1a] error status/mask=00002041/00002000
[   28.977978] pcieport 0000:00:1d.2:    [ 0] Receiver Error         (First)
[   28.977979] pcieport 0000:00:1d.2:    [ 6] Bad TLP               
[   29.604790] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   34.138318] r8169 0000:03:00.1 enp3s0f1: link down
[   34.138444] IPv6: ADDRCONF(NETDEV_UP): enp3s0f1: link is not ready
[  271.009598] Bluetooth: RFCOMM TTY layer initialized
[  271.009604] Bluetooth: RFCOMM socket layer initialized
[  271.009608] Bluetooth: RFCOMM ver 1.11
[  274.847643] rfkill: input handler disabled
[  317.489729] pcieport 0000:00:1d.2: AER: Multiple Corrected error received: id=00ea
[  317.489742] pcieport 0000:00:1d.2: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00ea(Receiver ID)
[  317.489746] pcieport 0000:00:1d.2:   device [8086:9d1a] error status/mask=00000001/00002000
[  317.489749] pcieport 0000:00:1d.2:    [ 0] Receiver Error         (First)
[  317.526093] pcieport 0000:00:1d.2: AER: Multiple Corrected error received: id=00ea
[  317.526109] pcieport 0000:00:1d.2: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00ea(Receiver ID)
[  317.526113] pcieport 0000:00:1d.2:   device [8086:9d1a] error status/mask=00000001/00002000
[  317.526118] pcieport 0000:00:1d.2:    [ 0] Receiver Error         (First)
[  318.149863] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[  318.330327] r8169 0000:03:00.1 enp3s0f1: link down
[  318.330457] IPv6: ADDRCONF(NETDEV_UP): enp3s0f1: link is not ready
[  318.784514] pcieport 0000:00:1d.2: AER: Multiple Corrected error received: id=00ea
[  318.784528] pcieport 0000:00:1d.2: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00ea(Receiver ID)
[  318.784532] pcieport 0000:00:1d.2:   device [8086:9d1a] error status/mask=00000001/00002000
[  318.784537] pcieport 0000:00:1d.2:    [ 0] Receiver Error         (First)
[  318.822148] pcieport 0000:00:1d.2: AER: Multiple Corrected error received: id=00ea
[  318.822168] pcieport 0000:00:1d.2: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00ea(Receiver ID)
[  318.822174] pcieport 0000:00:1d.2:   device [8086:9d1a] error status/mask=00002041/00002000
[  318.822180] pcieport 0000:00:1d.2:    [ 0] Receiver Error         (First)
[  318.822185] pcieport 0000:00:1d.2:    [ 6] Bad TLP               
[  319.446048] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[  326.212331] wlp2s0: authenticate with 
[  326.252716] wlp2s0: send auth to  (try 1/3)
[  326.254548] wlp2s0: authenticated
[  326.256131] wlp2s0: associate with  (try 1/3)
[  326.260194] wlp2s0: RX AssocResp from  (capab=0x411 status=0 aid=1)
[  326.262761] wlp2s0: associated
[  326.262877] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
[  326.674266] kauditd_printk_skb: 8 callbacks suppressed
[  326.674268] audit: type=1400 audit(1508516602.120:20): apparmor="DENIED" operation="open" profile="/sbin/dhclient" name="/var/lib/wicd/dhclient.conf" pid=1927 comm="dhclient" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
[  484.444023] INFO: task kworker/u8:0:5 blocked for more than 120 seconds.
[  484.444029]       Not tainted 4.13.0-16-generic #19-Ubuntu
[  484.444031] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  484.444035] kworker/u8:0    D    0     5      2 0x00000000
[  484.444115] Workqueue: phy0 ieee80211_ba_session_work [mac80211]
[  484.444120] Call Trace:
[  484.444139]  __schedule+0x28b/0x890
[  484.444149]  schedule+0x36/0x80
[  484.444158]  schedule_preempt_disabled+0xe/0x10
[  484.444167]  __mutex_lock.isra.2+0x190/0x4e0
[  484.444179]  __mutex_lock_slowpath+0x13/0x20
[  484.444187]  ? __mutex_lock_slowpath+0x13/0x20
[  484.444195]  mutex_lock+0x2f/0x40
[  484.444249]  __ieee80211_start_rx_ba_session+0x1b7/0x5a0 [mac80211]
[  484.444257]  ? dequeue_entity+0xed/0x4b0
[  484.444305]  ieee80211_ba_session_work+0x164/0x250 [mac80211]
[  484.444316]  process_one_work+0x1e7/0x410
[  484.444323]  worker_thread+0x4a/0x410
[  484.444330]  kthread+0x125/0x140
[  484.444337]  ? process_one_work+0x410/0x410
[  484.444342]  ? kthread_create_on_node+0x70/0x70
[  484.444350]  ret_from_fork+0x25/0x30
[  605.162925] INFO: task kworker/u8:0:5 blocked for more than 120 seconds.
[  605.162932]       Not tainted 4.13.0-16-generic #19-Ubuntu
[  605.162934] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  605.162938] kworker/u8:0    D    0     5      2 0x00000000
[  605.163017] Workqueue: phy0 ieee80211_ba_session_work [mac80211]
[  605.163022] Call Trace:
[  605.163041]  __schedule+0x28b/0x890
[  605.163050]  schedule+0x36/0x80
[  605.163060]  schedule_preempt_disabled+0xe/0x10
[  605.163069]  __mutex_lock.isra.2+0x190/0x4e0
[  605.163081]  __mutex_lock_slowpath+0x13/0x20
[  605.163089]  ? __mutex_lock_slowpath+0x13/0x20
[  605.163098]  mutex_lock+0x2f/0x40
[  605.163152]  __ieee80211_start_rx_ba_session+0x1b7/0x5a0 [mac80211]
[  605.163159]  ? dequeue_entity+0xed/0x4b0
[  605.163209]  ieee80211_ba_session_work+0x164/0x250 [mac80211]
[  605.163219]  process_one_work+0x1e7/0x410
[  605.163227]  worker_thread+0x4a/0x410
[  605.163234]  kthread+0x125/0x140
[  605.163241]  ? process_one_work+0x410/0x410
[  605.163246]  ? kthread_create_on_node+0x70/0x70
[  605.163254]  ret_from_fork+0x25/0x30
[  725.902083] INFO: task kworker/u8:0:5 blocked for more than 120 seconds.
[  725.902090]       Not tainted 4.13.0-16-generic #19-Ubuntu
[  725.902092] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  725.902096] kworker/u8:0    D    0     5      2 0x00000000
[  725.902184] Workqueue: phy0 ieee80211_ba_session_work [mac80211]
[  725.902190] Call Trace:
[  725.902209]  __schedule+0x28b/0x890
[  725.902219]  schedule+0x36/0x80
[  725.902228]  schedule_preempt_disabled+0xe/0x10
[  725.902238]  __mutex_lock.isra.2+0x190/0x4e0
[  725.902250]  __mutex_lock_slowpath+0x13/0x20
[  725.902259]  ? __mutex_lock_slowpath+0x13/0x20
[  725.902267]  mutex_lock+0x2f/0x40
[  725.902324]  __ieee80211_start_rx_ba_session+0x1b7/0x5a0 [mac80211]
[  725.902333]  ? dequeue_entity+0xed/0x4b0
[  725.902384]  ieee80211_ba_session_work+0x164/0x250 [mac80211]
[  725.902395]  process_one_work+0x1e7/0x410
[  725.902403]  worker_thread+0x4a/0x410
[  725.902410]  kthread+0x125/0x140
[  725.902417]  ? process_one_work+0x410/0x410
[  725.902423]  ? kthread_create_on_node+0x70/0x70
[  725.902430]  ret_from_fork+0x25/0x30
[  846.795652] INFO: task kworker/u8:0:5 blocked for more than 120 seconds.
[  846.795660]       Not tainted 4.13.0-16-generic #19-Ubuntu
[  846.795662] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  846.795666] kworker/u8:0    D    0     5      2 0x00000000
[  846.795738] Workqueue: phy0 ieee80211_ba_session_work [mac80211]
[  846.795743] Call Trace:
[  846.795762]  __schedule+0x28b/0x890
[  846.795772]  schedule+0x36/0x80
[  846.795781]  schedule_preempt_disabled+0xe/0x10
[  846.795790]  __mutex_lock.isra.2+0x190/0x4e0
[  846.795802]  __mutex_lock_slowpath+0x13/0x20
[  846.795811]  ? __mutex_lock_slowpath+0x13/0x20
[  846.795819]  mutex_lock+0x2f/0x40
[  846.795869]  __ieee80211_start_rx_ba_session+0x1b7/0x5a0 [mac80211]
[  846.795876]  ? dequeue_entity+0xed/0x4b0
[  846.795922]  ieee80211_ba_session_work+0x164/0x250 [mac80211]
[  846.795932]  process_one_work+0x1e7/0x410
[  846.795940]  worker_thread+0x4a/0x410
[  846.795946]  kthread+0x125/0x140
[  846.795954]  ? process_one_work+0x410/0x410
[  846.795959]  ? kthread_create_on_node+0x70/0x70
[  846.795966]  ret_from_fork+0x25/0x30
[  887.826613] wlp2s0: deauthenticating from by local choice (Reason: 3=DEAUTH_LEAVING)
[  967.667027] INFO: task kworker/u8:0:5 blocked for more than 120 seconds.
[  967.667034]       Not tainted 4.13.0-16-generic #19-Ubuntu
[  967.667036] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  967.667040] kworker/u8:0    D    0     5      2 0x00000000
[  967.667121] Workqueue: phy0 ieee80211_ba_session_work [mac80211]
[  967.667126] Call Trace:
[  967.667146]  __schedule+0x28b/0x890
[  967.667156]  schedule+0x36/0x80
[  967.667165]  schedule_preempt_disabled+0xe/0x10
[  967.667174]  __mutex_lock.isra.2+0x190/0x4e0
[  967.667187]  __mutex_lock_slowpath+0x13/0x20
[  967.667195]  ? __mutex_lock_slowpath+0x13/0x20
[  967.667204]  mutex_lock+0x2f/0x40
[  967.667258]  __ieee80211_start_rx_ba_session+0x1b7/0x5a0 [mac80211]
[  967.667266]  ? dequeue_entity+0xed/0x4b0
[  967.667315]  ieee80211_ba_session_work+0x164/0x250 [mac80211]
[  967.667327]  process_one_work+0x1e7/0x410
[  967.667335]  worker_thread+0x4a/0x410
[  967.667341]  kthread+0x125/0x140
[  967.667349]  ? process_one_work+0x410/0x410
[  967.667354]  ? kthread_create_on_node+0x70/0x70
[  967.667362]  ret_from_fork+0x25/0x30

```

---

