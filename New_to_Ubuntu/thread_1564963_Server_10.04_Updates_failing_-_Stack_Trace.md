---
title: "Server 10.04 Updates failing - Stack Trace"
date: 2010-08-31
forum: New to Ubuntu
---

### Post by kylea on 2010-08-31
Ubuntu 64bit 10.04 Server

Linux 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:38:40 UTC 2010 x86_64 GNU/Linux


Updates applied via apt-get or Synaptic fail - there is a Kernel timeout error in syslog with a Stack Trace

 INFO: task umount:5344 blocked for more than 120 seconds.
kernel: [ 1321.430143] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
kernel: [ 1321.430146] umount        D 0000000000000002     0  5344   5297 0x00000000
kernel: [ 1321.430150]  ffff88014fe71d98 0000000000000086 0000000000015bc0 0000000000015bc0
kernel: [ 1321.430154]  ffff88013e7603c0 ffff88014fe71fd8 0000000000015bc0 ffff88013e760000
kernel: [ 1321.430157]  0000000000015bc0 ffff88014fe71fd8 0000000000015bc0 ffff88013e7603c0
kernel: [ 1321.430160] Call Trace:
kernel: [ 1321.430169]  [<ffffffff81166d80>] ? bdi_sched_wait+0x0/0x20
kernel: [ 1321.430171]  [<ffffffff81166d8e>] bdi_sched_wait+0xe/0x20
kernel: [ 1321.430177]  [<ffffffff815591df>] __wait_on_bit+0x5f/0x90
kernel: [ 1321.430179]  [<ffffffff81166d80>] ? bdi_sched_wait+0x0/0x20
kernel: [ 1321.430182]  [<ffffffff81559288>] out_of_line_wait_on_bit+0x78/0x90
kernel: [ 1321.430186]  [<ffffffff810850d0>] ? wake_bit_function+0x0/0x40
kernel: [ 1321.430188]  [<ffffffff81166d44>] ? bdi_queue_work+0xa4/0xe0
kernel: [ 1321.430191]  [<ffffffff811680ef>] bdi_sync_writeback+0x6f/0x80
kernel: [ 1321.430194]  [<ffffffff81168120>] sync_inodes_sb+0x20/0x30
kernel: [ 1321.430197]  [<ffffffff8116bc92>] __sync_filesystem+0x82/0x90
kernel: [ 1321.430199]  [<ffffffff8116bd79>] sync_filesystems+0xd9/0x130
kernel: [ 1321.430203]  [<ffffffff81160981>] sys_umount+0xb1/0xd0
kernel: [ 1321.430207]  [<ffffffff810131b2>] system_call_fastpath+0x16/0x1b

---

### Post by andrewthomas on 2010-08-31
What error do you receive in the terminal when using apt-get to update?

---

### Post by kylea on 2010-08-31
Nothing - just hangs there for-ever

If I reboot and run sudo apt-get --configure -a the update will sometimes complete - but mostly just does nothing

---

### Post by kylea on 2010-08-31
I am trying to apply the 2.6.32-24 Kernel update - it is stuck at:

Unpacking .....

---

### Post by kylea on 2010-08-31
INFO: task umount:5344 blocked for more than 120 seconds.

will also be replaced by

INFO: task dpkg:5344 blocked for more than 120 seconds.

and sometimes

INFO: task ureadahead:5344 blocked for more than 120 seconds.

---

### Post by kylea on 2010-08-31
here is some more

ug 31 23:22:45 itvss1 kernel: [ 2281.420086] dpkg          D 0000000000000000     0 24196  24133 0x00000000
Aug 31 23:22:45 itvss1 kernel: [ 2281.420090]  ffff880168c87db8 0000000000000082 0000000000015bc0 0000000000015bc0
Aug 31 23:22:45 itvss1 kernel: [ 2281.420094]  ffff88021a7931a0 ffff880168c87fd8 0000000000015bc0 ffff88021a792de0
Aug 31 23:22:45 itvss1 kernel: [ 2281.420097]  0000000000015bc0 ffff880168c87fd8 0000000000015bc0 ffff88021a7931a0
Aug 31 23:22:45 itvss1 kernel: [ 2281.420100] Call Trace:
Aug 31 23:22:45 itvss1 kernel: [ 2281.420109]  [<ffffffff81166d80>] ? bdi_sched_wait+0x0/0x20
Aug 31 23:22:45 itvss1 kernel: [ 2281.420112]  [<ffffffff81166d8e>] bdi_sched_wait+0xe/0x20
Aug 31 23:22:45 itvss1 kernel: [ 2281.420117]  [<ffffffff815591df>] __wait_on_bit+0x5f/0x90
Aug 31 23:22:45 itvss1 kernel: [ 2281.420119]  [<ffffffff81166d80>] ? bdi_sched_wait+0x0/0x20
Aug 31 23:22:45 itvss1 kernel: [ 2281.420122]  [<ffffffff81559288>] out_of_line_wait_on_bit+0x78/0x90
Aug 31 23:22:45 itvss1 kernel: [ 2281.420126]  [<ffffffff810850d0>] ? wake_bit_function+0x0/0x40
Aug 31 23:22:45 itvss1 kernel: [ 2281.420129]  [<ffffffff81166d44>] ? bdi_queue_work+0xa4/0xe0
Aug 31 23:22:45 itvss1 kernel: [ 2281.420131]  [<ffffffff811680ef>] bdi_sync_writeback+0x6f/0x80
Aug 31 23:22:45 itvss1 kernel: [ 2281.420134]  [<ffffffff81168120>] sync_inodes_sb+0x20/0x30
Aug 31 23:22:45 itvss1 kernel: [ 2281.420137]  [<ffffffff8116bc92>] __sync_filesystem+0x82/0x90
Aug 31 23:22:45 itvss1 kernel: [ 2281.420140]  [<ffffffff8116bd79>] sync_filesystems+0xd9/0x130
Aug 31 23:22:45 itvss1 kernel: [ 2281.420142]  [<ffffffff8116be31>] sys_sync+0x21/0x40
Aug 31 23:22:45 itvss1 kernel: [ 2281.420146]  [<ffffffff810131b2>] system_call_fastpath+0x16/0x1b
Aug 31 23:24:45 itvss1 kernel: [ 2401.422564] INFO: task dpkg:24196 blocked for more than 120 seconds.
Aug 31 23:24:45 itvss1 kernel: [ 2401.422568] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Aug 31 23:24:45 itvss1 kernel: [ 2401.422570] dpkg          D 0000000000000000     0 24196  24133 0x00000000
Aug 31 23:24:45 itvss1 kernel: [ 2401.422574]  ffff880168c87db8 0000000000000082 0000000000015bc0 0000000000015bc0
Aug 31 23:24:45 itvss1 kernel: [ 2401.422578]  ffff88021a7931a0 ffff880168c87fd8 0000000000015bc0 ffff88021a792de0
Aug 31 23:24:45 itvss1 kernel: [ 2401.422581]  0000000000015bc0 ffff880168c87fd8 0000000000015bc0 ffff88021a7931a0
Aug 31 23:24:45 itvss1 kernel: [ 2401.422584] Call Trace:
Aug 31 23:24:45 itvss1 kernel: [ 2401.422593]  [<ffffffff81166d80>] ? bdi_sched_wait+0x0/0x20
Aug 31 23:24:45 itvss1 kernel: [ 2401.422596]  [<ffffffff81166d8e>] bdi_sched_wait+0xe/0x20
Aug 31 23:24:45 itvss1 kernel: [ 2401.422601]  [<ffffffff815591df>] __wait_on_bit+0x5f/0x90
Aug 31 23:24:45 itvss1 kernel: [ 2401.422603]  [<ffffffff81166d80>] ? bdi_sched_wait+0x0/0x20
Aug 31 23:24:45 itvss1 kernel: [ 2401.422606]  [<ffffffff81559288>] out_of_line_wait_on_bit+0x78/0x90
Aug 31 23:24:45 itvss1 kernel: [ 2401.422610]  [<ffffffff810850d0>] ? wake_bit_function+0x0/0x40
Aug 31 23:24:45 itvss1 kernel: [ 2401.422613]  [<ffffffff81166d44>] ? bdi_queue_work+0xa4/0xe0
Aug 31 23:24:45 itvss1 kernel: [ 2401.422616]  [<ffffffff811680ef>] bdi_sync_writeback+0x6f/0x80
Aug 31 23:24:45 itvss1 kernel: [ 2401.422618]  [<ffffffff81168120>] sync_inodes_sb+0x20/0x30
Aug 31 23:24:45 itvss1 kernel: [ 2401.422621]  [<ffffffff8116bc92>] __sync_filesystem+0x82/0x90
Aug 31 23:24:45 itvss1 kernel: [ 2401.422624]  [<ffffffff8116bd79>] sync_filesystems+0xd9/0x130
Aug 31 23:24:45 itvss1 kernel: [ 2401.422626]  [<ffffffff8116be31>] sys_sync+0x21/0x40
Aug 31 23:24:45 itvss1 kernel: [ 2401.422631]  [<ffffffff810131b2>] system_call_fastpath+0x16/0x1b

---

### Post by kylea on 2010-09-01
I have created a bug report

[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/628047](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/628047)

---

