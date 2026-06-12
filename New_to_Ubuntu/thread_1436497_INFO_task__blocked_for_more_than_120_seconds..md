---
title: "INFO: task * blocked for more than 120 seconds."
date: 2010-03-22
forum: New to Ubuntu
---

### Post by stoogiebuncho on 2010-03-22
I've been getting random freeze-ups from time to time.  Sometimes I'll go for a few weeks without it happening, sometimes it will happen every day.

When it freezes, the computer becomes completely unresponsive and I have to press Alt+SysRq+R-S-E-I-U-B to get it to reboot.

Here is the kern.log for the latest freeze:
```
Mar 22 17:07:33 Compy kernel: [ 2520.436029] INFO: task i915/1:339 blocked for more than 120 seconds.
Mar 22 17:07:33 Compy kernel: [ 2520.436034] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Mar 22 17:07:33 Compy kernel: [ 2520.436039] i915/1        D c08185c0     0   339      2 0x00000000
Mar 22 17:07:33 Compy kernel: [ 2520.436047]  f659df04 00000046 f696581c c08185c0 f6965a88 c08185c0 a77c63e7 00000205
Mar 22 17:07:33 Compy kernel: [ 2520.436059]  c08185c0 c08185c0 f6965a88 c08185c0 a77c5587 00000205 c08185c0 eebc0000
Mar 22 17:07:33 Compy kernel: [ 2520.436070]  f69657f0 f68ba814 f68ba818 ffffffff f659df30 c0572b76 f69025b0 f68ba81c
Mar 22 17:07:33 Compy kernel: [ 2520.436081] Call Trace:
Mar 22 17:07:33 Compy kernel: [ 2520.436093]  [<c0572b76>] __mutex_lock_slowpath+0xc6/0x130
Mar 22 17:07:33 Compy kernel: [ 2520.436100]  [<c0572a90>] mutex_lock+0x20/0x40
Mar 22 17:07:33 Compy kernel: [ 2520.436129]  [<f83af8fa>] i915_gem_retire_work_handler+0x2a/0x70 [i915]
Mar 22 17:07:33 Compy kernel: [ 2520.436137]  [<c01579de>] run_workqueue+0x6e/0x140
Mar 22 17:07:33 Compy kernel: [ 2520.436159]  [<f83af8d0>] ? i915_gem_retire_work_handler+0x0/0x70 [i915]
Mar 22 17:07:33 Compy kernel: [ 2520.436166]  [<c0157b38>] worker_thread+0x88/0xe0
Mar 22 17:07:33 Compy kernel: [ 2520.436173]  [<c015c180>] ? autoremove_wake_function+0x0/0x40
Mar 22 17:07:33 Compy kernel: [ 2520.436179]  [<c0157ab0>] ? worker_thread+0x0/0xe0
Mar 22 17:07:33 Compy kernel: [ 2520.436185]  [<c015be8c>] kthread+0x7c/0x90
Mar 22 17:07:33 Compy kernel: [ 2520.436190]  [<c015be10>] ? kthread+0x0/0x90
Mar 22 17:07:33 Compy kernel: [ 2520.436196]  [<c0104047>] kernel_thread_helper+0x7/0x10
```

This repeats over and over.

Most of the stuff I've found online says this problem is from the 2.6.26 kernel, but I'm running 2.6.31-20-generic.

I'm at a loss as to what to do next.  If anyone has found a workaround for this problem, I would appreciate it.

---

### Post by stoogiebuncho on 2010-03-22
Doesn't seem like I'm getting much response, so I'll ask an additional question.

Has anyone else been having this problem, or is it just me?

Could this be a hardware problem, or is it more likely to be related to the kernel?

Thanks.

---

### Post by danep on 2010-04-04
I have been getting this error only for the cron task, it started after I rebooted for a kernel update a few weeks ago. It's really bad- whenever the error occurs the system becomes unresponsive to SSH and IMAP requests, but apache still seems to return webpages just fine. It usually lasts 30-60 minutes and goes away on its own. Very weird. I would very much appreciate some help tracing the root of this problem.

---

### Post by computermacgyver on 2010-04-08
You're not alone, stoogiebuncho,
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/429321](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/429321)

I'm having the problem as well. It appears to be connected to an out of date video driver in the kernal. I'm still looking for a good solution now.

I think your issue, danep, is different. Those with the above issue report still being able to login with SSH, etc., (I have yet to confirm this in my case).

---

### Post by computermacgyver on 2010-04-09
The problem hasn't happened to me again since diabling visual effects (Compiz Fusion). I have no steps to reliabily reproduce the problem; so, I am not sure if it is solved or not.

Try to disable visual effects by 
1) right click on the deskop and select "change desktop background"
2) Click the "Visual Effects" tab
3) Change it to none.
This is a per user setting and (as far as I know) has to be changed for each user using the machine.

---

### Post by stoogiebuncho on 2010-04-09
> **computermacgyver said:**
> The problem hasn't happened to me again since diabling visual effects (Compiz Fusion). I have no steps to reliabily reproduce the problem; so, I am not sure if it is solved or not.

Try to disable visual effects by 
1) right click on the deskop and select "change desktop background"
2) Click the "Visual Effects" tab
3) Change it to none.
This is a per user setting and (as far as I know) has to be changed for each user using the machine.

Thanks for the information - I'll keep an eye on that bug report.  From what it describes, it certainly seems rational that disabling visual effect could solve the problems.

I use Gnome-Do Docky so I'm hesitant to disable compiz since I would lose that functionality, and right now my computer has only been freezing once a week or less.  If it becomes more frequent I'll probably give it a try, though.

---

### Post by tarvid on 2010-08-13
Happening to me too. On a server. No X.

Home workstation instable since processor upgrade. Switching from compiz to metacity and firefox to chromium helped.

These are kernel bugs and the only thing I can find in common is load. Recent kernels would rather quit than fight.

---

### Post by kbron on 2010-08-13
Hi guys.

Just wanted to let you know this issue is not exclusive to Ubuntu. I have a CentOS 5.5 suffering from the same problem, to the point that I had to totally disable Xorg in order for the box to keep running more than 10 minutes (I'm booting in runlevel 3)

It seems to be driver for Intel's i915 video card. 
(some more info: I know there's a video card that Intel totally dropped the support for Linux, but I don't remember which one was it, nor where I read it .... -- sorry, too lazy to google --) 

BTW, it's not the first time I've seen this! Some years ago I had exactly the same issue with an ATI card.

---

### Post by kbron on 2010-08-14
One last thing I almost forgot to mention:

I can confirm that in  Ubuntu you can SSH the box and do some forensics such as /var/log  analysis and of course dmesg analysis. As a matter of fact, dmesg is the  only "log" (so to speak) I've been able to find that really blames the  crash to i915 -- which I'm pretty sure it's the cause of this nightmare,  by the way. When done you can safely shutdown/reboot the box.

Bad news for CentOS: this issue causes a kernel crash that not even a "**R**aising **S**kinny **E**lephants **I**s **U**tterly **B**oring" sequence will be able to help you :(  
(solution: just a good old cold boot to get the box alive again)

---

### Post by stoogiebuncho on 2010-08-18
Since moving to Ubuntu 10.04 I have not had this problem.  Maybe it's just a fluke, but I'm not complaining.

---

### Post by aeiah on 2010-11-16
i have it with 10.04 server, 2.6.32-21 running as a HyperV guest. ARGHH.

investigating now :(

---

### Post by mglat on 2010-11-17
I am experiencing the same problems with Ubuntu 10.04-server and kernel 2.6.32-25-server via MS Hyper-V. Any suggestions so far?

---

### Post by andrex593 on 2010-12-03
I also have this problem, in Maverick with kernel 2.6.35.23.25 and Nvidia video driver, all up to date.  It started a few weeks ago after a kernel upgrade IIRC.  I've seen it get triggered twice when I ran relatively disk-intensive commands, like 'find -type d -print0 | xargs -0 chmod u+s' or 'cvs up' on a Drupal repository.  This has the feel of a hardware problem, but SMART on my /home drive shows good health and no errors.

---

### Post by 0xCAFEFACE on 2010-12-06
This has just happened to me also under Ubuntu server 10.04.1LTS running under Hyper-V.

Kernel: 2.6.32-26-generic-pae

It looks like it's related to the scheduling processes crashing.

kern.log :
```

Nov 30 06:51:27 host kernel: [681414.858508] Btrfs loaded
Dec  4 19:06:54 host kernel: [1071141.810134] BUG: scheduling while atomic: swapper/0/0x10000100
Dec  4 19:06:54 host kernel: [1071141.813736] Modules linked in: btrfs zlib_deflate crc32c libcrc32c ufs qnx4 hfsplus hfs minix ntfs vfat msdos fat jfs xfs exportfs reiserfs lp fbcon tileblit font bitblit softcursor psmouse serio_raw parport i2c_piix4 vga16fb vgastate hv_netvsc(C) hv_blkvsc(C) hv_storvsc(C) floppy hv_vmbus(C)
Dec  4 19:06:54 host kernel: [1071141.813754] 
Dec  4 19:06:54 host kernel: [1071141.813757] Pid: 0, comm: swapper Tainted: G         C (2.6.32-24-generic-pae #43-Ubuntu) Virtual Machine
Dec  4 19:06:54 host kernel: [1071141.813759] EIP: 0060:[<c012ffea>] EFLAGS: 00000246 CPU: 0
Dec  4 19:06:54 host kernel: [1071141.813764] EIP is at native_safe_halt+0xa/0x10
Dec  4 19:06:54 host kernel: [1071141.813766] EAX: c0790000 EBX: c07e0a64 ECX: c1a04a60 EDX: 00000000
Dec  4 19:06:54 host kernel: [1071141.813767] ESI: 00000000 EDI: c079d000 EBP: c0791f7c ESP: c0791f7c
Dec  4 19:06:54 host kernel: [1071141.813769]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Dec  4 19:06:54 host kernel: [1071141.813770] CR0: 8005003b CR2: b77c46d0 CR3: 36534000 CR4: 000006f0
Dec  4 19:06:54 host kernel: [1071141.813774] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
Dec  4 19:06:54 host kernel: [1071141.813775] DR6: ffff0ff0 DR7: 00000400
Dec  4 19:06:54 host kernel: [1071141.813777] Call Trace:
Dec  4 19:06:54 host kernel: [1071141.813782]  [<c0110c10>] default_idle+0x40/0x90
Dec  4 19:06:54 host kernel: [1071141.813785]  [<c0108634>] cpu_idle+0x94/0xd0
Dec  4 19:06:54 host kernel: [1071141.813789]  [<c059f368>] rest_init+0x58/0x60
Dec  4 19:06:54 host kernel: [1071141.813792]  [<c07e48fd>] start_kernel+0x351/0x357
Dec  4 19:06:54 host kernel: [1071141.813794]  [<c07e43d8>] ? unknown_bootoption+0x0/0x19e
Dec  4 19:06:54 host kernel: [1071141.813797]  [<c07e40bb>] i386_start_kernel+0xaa/0xb1
Dec  4 19:06:54 host kernel: [1071141.816182] BUG: scheduling while atomic: swapper/0/0x10000100
Dec  4 19:06:54 host kernel: [1071141.819838] Modules linked in: btrfs zlib_deflate crc32c libcrc32c ufs qnx4 hfsplus hfs minix ntfs vfat msdos fat jfs xfs exportfs reiserfs lp fbcon tileblit font bitblit softcursor psmouse serio_raw parport i2c_piix4 vga16fb vgastate hv_netvsc(C) hv_blkvsc(C) hv_storvsc(C) floppy hv_vmbus(C)
Dec  4 19:06:54 host kernel: [1071141.819882] 
Dec  4 19:06:54 host kernel: [1071141.819885] Pid: 0, comm: swapper Tainted: G         C (2.6.32-24-generic-pae #43-Ubuntu) Virtual Machine
Dec  4 19:06:54 host kernel: [1071141.819887] EIP: 0060:[<c012ffea>] EFLAGS: 00000246 CPU: 0
Dec  4 19:06:54 host kernel: [1071141.819890] EIP is at native_safe_halt+0xa/0x10
Dec  4 19:06:54 host kernel: [1071141.819892] EAX: c0790000 EBX: c07e0a64 ECX: c1a04a60 EDX: 00000000
Dec  4 19:06:54 host kernel: [1071141.819909] ESI: 00000000 EDI: c079d000 EBP: c0791f7c ESP: c0791f7c
Dec  4 19:06:54 host kernel: [1071141.819911]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Dec  4 19:06:54 host kernel: [1071141.819913] CR0: 8005003b CR2: b77c46d0 CR3: 36a19000 CR4: 000006f0
Dec  4 19:06:54 host kernel: [1071141.819916] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
Dec  4 19:06:54 host kernel: [1071141.819917] DR6: ffff0ff0 DR7: 00000400
Dec  4 19:06:54 host kernel: [1071141.819918] Call Trace:
Dec  4 19:06:54 host kernel: [1071141.819922]  [<c0110c10>] default_idle+0x40/0x90
Dec  4 19:06:54 host kernel: [1071141.819925]  [<c0108634>] cpu_idle+0x94/0xd0
Dec  4 19:06:54 host kernel: [1071141.819927]  [<c059f368>] rest_init+0x58/0x60
Dec  4 19:06:54 host kernel: [1071141.819930]  [<c07e48fd>] start_kernel+0x351/0x357
Dec  4 19:06:54 host kernel: [1071141.819932]  [<c07e43d8>] ? unknown_bootoption+0x0/0x19e
Dec  4 19:06:54 host kernel: [1071141.819934]  [<c07e40bb>] i386_start_kernel+0xaa/0xb1

```

---

### Post by bakinsoda on 2011-01-19
I too have been having this issue since mid-late December.  At first it happened about 1x a week, now it is happening daily.  At first my hunch was that the disk is bad; one of my tables in mysql became corrupted after so many resets.  Could this be it?  Have you guys resolved this yet?  What have you tried and what threads are you following?

Here is an excerpt from my kern.log:
```

Jan 18 22:48:10 vqnguyen-server2 kernel: [23507.540509] lo: Disabled Privacy Ext
ensions
Jan 18 22:49:25 vqnguyen-server2 kernel: [23581.767565] lo: Disabled Privacy Ext
ensions
Jan 18 22:49:37 vqnguyen-server2 kernel: [23593.861591] lo: Disabled Privacy Ext
ensions
Jan 19 02:32:23 vqnguyen-server2 kernel: [36960.552119] INFO: task mysqld:1938 b
locked for more than 120 seconds.
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552224] "echo 0 > /proc/sys/kern
el/hung_task_timeout_secs" disables this message.
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552331] mysqld        D 0003df5a     0  1938      1 0x00000000
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552346]  e395ff38 00000086 fffb2858 0003df5a 00000000 c088b4c0 e3939c24 c088b4c0
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552364]  d310e6d5 0000216f c088b4c0 c088b4c0 e3939c24 c088b4c0 c088b4c0 f65c6800
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552381]  d30ed65e 0000216f e3939980 e3939980 e395ff6c f65c6838 e395ff64 c05b3a45
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552398] Call Trace:
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552420]  [<c05b3a45>] rwsem_down_failed_common+0x75/0x1a0
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552430]  [<c05b3b8d>] rwsem_down_write_failed+0x1d/0x30
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552440]  [<c05b3c26>] call_rwsem_down_write_failed+0x6/0x10
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552450]  [<c05b3144>] ? down_write+0x24/0x30
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552464]  [<c01f6166>] sys_mremap+0x26/0x60
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552475]  [<c01097ac>] syscall_call+0x7/0xb
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552491] INFO: task mysqld:1997 blocked for more than 120 seconds.
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552577] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552683] mysqld        D 000acd4a     0  1997      1 0x00000000
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552696]  f6595f18 00000086 f771a878 000acd4a 00000000 c088b4c0 f6fc82a4 c088b4c0
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552712]  2e669727 0000217a c088b4c0 c088b4c0 f6fc82a4 c088b4c0 c088b4c0 f65c6800
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552728]  2e6635af 0000217a f6fc8000 f6fc8000 f6595f4c f65c6838 f6595f44 c05b3a45
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552744] Call Trace:
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552755]  [<c05b3a45>] rwsem_down_failed_common+0x75/0x1a0
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552766]  [<c01f0567>] ? handle_mm_fault+0x397/0x4a0
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552776]  [<c05b3bbd>] rwsem_down_read_failed+0x1d/0x30
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552787]  [<c05b3c17>] call_rwsem_down_read_failed+0x7/0x10
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552796]  [<c05b316c>] ? down_read+0x1c/0x20
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552806]  [<c05b64c5>] do_page_fault+0x395/0x3a0
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552815]  [<c05b6130>] ? do_page_fault+0x0/0x3a0
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552823]  [<c05b40f3>] error_code+0x73/0x80
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552240] INFO: task cron:3130 blocked for more than 120 seconds.
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552342] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552449] cron          D 0001c590     0  3130    732 0x00000000
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552464]  f563de1c 00000086 00000000 0001c590 00000000 c088b4c0 f5644264 c088b4c0
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552482]  ff4b58f1 00002209 c088b4c0 c088b4c0 f5644264 c088b4c0 c088b4c0 c2c02000
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552499]  ff3c2b24 00002209 f5643fc0 c1e094c0 f5643fc0 f563de68 f563de2c c05b207a
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552516] Call Trace:
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552540]  [<c05b207a>] io_schedule+0x3a/0x60
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552552]  [<c01d316d>] sync_page+0x3d/0x50
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552562]  [<c05b26c7>] __wait_on_bit_lock+0x47/0x90
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552573]  [<c01e3d3f>] ? vma_prio_tree_remove+0x7f/0xf0
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552581]  [<c01d3130>] ? sync_page+0x0/0x50
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552590]  [<c01d30fe>] __lock_page+0x7e/0x90
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552601]  [<c016ff60>] ? wake_bit_function+0x0/0x50
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552612]  [<c01d52fa>] filemap_fault+0x39a/0x410
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552623]  [<c01eee7c>] __do_fault+0x4c/0x520
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552632]  [<c01f2820>] ? __vma_link_file+0x40/0x70
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552641]  [<c01f2ea4>] ? vma_link+0x84/0xa0
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552651]  [<c01f0368>] handle_mm_fault+0x198/0x4a0
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552663]  [<c028f4e0>] ? ext4_file_mmap+0x0/0x50
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552674]  [<c01f4cbc>] ? do_mmap_pgoff+0x25c/0x300
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552688]  [<c05b623d>] do_page_fault+0x10d/0x3a0
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552699]  [<c01e7c1b>] ? sys_mmap_pgoff+0x12b/0x240
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552708]  [<c05b6130>] ? do_page_fault+0x0/0x3a0
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552717]  [<c05b40f3>] error_code+0x73/0x80
Jan 19 05:16:24 vqnguyen-server2 kernel: [46800.556099] INFO: task mysqld:1997 blocked for more than 120 seconds.
Jan 19 05:16:24 vqnguyen-server2 kernel: [46800.556194] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 19 05:16:24 vqnguyen-server2 kernel: [46800.556300] mysqld        D 0000c059     0  1997      1 0x00000000


```

---

### Post by bakinsoda on 2011-01-19
I too have been having this issue since mid-late December on my Ubuntu 10.04 server (2.6.32-27-generic-pae; P4 laptop).  At first it happened about 1x a week, now it is happening daily.  At first my hunch was that the disk is bad; one of my tables in mysql became corrupted after so many resets.  Could this be it?  Have you guys resolved this yet?  What have you tried and what threads are you following?

Here is an excerpt from my kern.log:
```

Jan 18 22:48:10 vqnguyen-server2 kernel: [23507.540509] lo: Disabled Privacy Ext
ensions
Jan 18 22:49:25 vqnguyen-server2 kernel: [23581.767565] lo: Disabled Privacy Ext
ensions
Jan 18 22:49:37 vqnguyen-server2 kernel: [23593.861591] lo: Disabled Privacy Ext
ensions
Jan 19 02:32:23 vqnguyen-server2 kernel: [36960.552119] INFO: task mysqld:1938 b
locked for more than 120 seconds.
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552224] "echo 0 > /proc/sys/kern
el/hung_task_timeout_secs" disables this message.
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552331] mysqld        D 0003df5a     0  1938      1 0x00000000
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552346]  e395ff38 00000086 fffb2858 0003df5a 00000000 c088b4c0 e3939c24 c088b4c0
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552364]  d310e6d5 0000216f c088b4c0 c088b4c0 e3939c24 c088b4c0 c088b4c0 f65c6800
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552381]  d30ed65e 0000216f e3939980 e3939980 e395ff6c f65c6838 e395ff64 c05b3a45
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552398] Call Trace:
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552420]  [<c05b3a45>] rwsem_down_failed_common+0x75/0x1a0
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552430]  [<c05b3b8d>] rwsem_down_write_failed+0x1d/0x30
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552440]  [<c05b3c26>] call_rwsem_down_write_failed+0x6/0x10
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552450]  [<c05b3144>] ? down_write+0x24/0x30
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552464]  [<c01f6166>] sys_mremap+0x26/0x60
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552475]  [<c01097ac>] syscall_call+0x7/0xb
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552491] INFO: task mysqld:1997 blocked for more than 120 seconds.
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552577] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552683] mysqld        D 000acd4a     0  1997      1 0x00000000
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552696]  f6595f18 00000086 f771a878 000acd4a 00000000 c088b4c0 f6fc82a4 c088b4c0
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552712]  2e669727 0000217a c088b4c0 c088b4c0 f6fc82a4 c088b4c0 c088b4c0 f65c6800
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552728]  2e6635af 0000217a f6fc8000 f6fc8000 f6595f4c f65c6838 f6595f44 c05b3a45
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552744] Call Trace:
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552755]  [<c05b3a45>] rwsem_down_failed_common+0x75/0x1a0
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552766]  [<c01f0567>] ? handle_mm_fault+0x397/0x4a0
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552776]  [<c05b3bbd>] rwsem_down_read_failed+0x1d/0x30
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552787]  [<c05b3c17>] call_rwsem_down_read_failed+0x7/0x10
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552796]  [<c05b316c>] ? down_read+0x1c/0x20
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552806]  [<c05b64c5>] do_page_fault+0x395/0x3a0
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552815]  [<c05b6130>] ? do_page_fault+0x0/0x3a0
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552823]  [<c05b40f3>] error_code+0x73/0x80
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552240] INFO: task cron:3130 blocked for more than 120 seconds.
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552342] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552449] cron          D 0001c590     0  3130    732 0x00000000
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552464]  f563de1c 00000086 00000000 0001c590 00000000 c088b4c0 f5644264 c088b4c0
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552482]  ff4b58f1 00002209 c088b4c0 c088b4c0 f5644264 c088b4c0 c088b4c0 c2c02000
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552499]  ff3c2b24 00002209 f5643fc0 c1e094c0 f5643fc0 f563de68 f563de2c c05b207a
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552516] Call Trace:
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552540]  [<c05b207a>] io_schedule+0x3a/0x60
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552552]  [<c01d316d>] sync_page+0x3d/0x50
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552562]  [<c05b26c7>] __wait_on_bit_lock+0x47/0x90
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552573]  [<c01e3d3f>] ? vma_prio_tree_remove+0x7f/0xf0
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552581]  [<c01d3130>] ? sync_page+0x0/0x50
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552590]  [<c01d30fe>] __lock_page+0x7e/0x90
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552601]  [<c016ff60>] ? wake_bit_function+0x0/0x50
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552612]  [<c01d52fa>] filemap_fault+0x39a/0x410
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552623]  [<c01eee7c>] __do_fault+0x4c/0x520
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552632]  [<c01f2820>] ? __vma_link_file+0x40/0x70
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552641]  [<c01f2ea4>] ? vma_link+0x84/0xa0
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552651]  [<c01f0368>] handle_mm_fault+0x198/0x4a0
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552663]  [<c028f4e0>] ? ext4_file_mmap+0x0/0x50
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552674]  [<c01f4cbc>] ? do_mmap_pgoff+0x25c/0x300
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552688]  [<c05b623d>] do_page_fault+0x10d/0x3a0
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552699]  [<c01e7c1b>] ? sys_mmap_pgoff+0x12b/0x240
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552708]  [<c05b6130>] ? do_page_fault+0x0/0x3a0
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552717]  [<c05b40f3>] error_code+0x73/0x80
Jan 19 05:16:24 vqnguyen-server2 kernel: [46800.556099] INFO: task mysqld:1997 blocked for more than 120 seconds.
Jan 19 05:16:24 vqnguyen-server2 kernel: [46800.556194] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 19 05:16:24 vqnguyen-server2 kernel: [46800.556300] mysqld        D 0000c059     0  1997      1 0x00000000


```

---

### Post by bakinsoda on 2011-01-19
I too have been having this issue since mid-late December on my Ubuntu 10.04 server (2.6.32-27-generic-pae; P4 laptop).  At first it happened about 1x a week, now it is happening daily.  At first my hunch was that the disk is bad; one of my tables in mysql became corrupted after so many resets.  Could this be it?  Have you guys resolved this yet?  What have you tried and what threads are you following?

Here is an excerpt from my kern.log:
```

Jan 18 22:48:10 vqnguyen-server2 kernel: [23507.540509] lo: Disabled Privacy Ext
ensions
Jan 18 22:49:25 vqnguyen-server2 kernel: [23581.767565] lo: Disabled Privacy Ext
ensions
Jan 18 22:49:37 vqnguyen-server2 kernel: [23593.861591] lo: Disabled Privacy Ext
ensions
Jan 19 02:32:23 vqnguyen-server2 kernel: [36960.552119] INFO: task mysqld:1938 b
locked for more than 120 seconds.
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552224] "echo 0 > /proc/sys/kern
el/hung_task_timeout_secs" disables this message.
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552331] mysqld        D 0003df5a     0  1938      1 0x00000000
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552346]  e395ff38 00000086 fffb2858 0003df5a 00000000 c088b4c0 e3939c24 c088b4c0
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552364]  d310e6d5 0000216f c088b4c0 c088b4c0 e3939c24 c088b4c0 c088b4c0 f65c6800
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552381]  d30ed65e 0000216f e3939980 e3939980 e395ff6c f65c6838 e395ff64 c05b3a45
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552398] Call Trace:
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552420]  [<c05b3a45>] rwsem_down_failed_common+0x75/0x1a0
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552430]  [<c05b3b8d>] rwsem_down_write_failed+0x1d/0x30
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552440]  [<c05b3c26>] call_rwsem_down_write_failed+0x6/0x10
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552450]  [<c05b3144>] ? down_write+0x24/0x30
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552464]  [<c01f6166>] sys_mremap+0x26/0x60
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552475]  [<c01097ac>] syscall_call+0x7/0xb
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552491] INFO: task mysqld:1997 blocked for more than 120 seconds.
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552577] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552683] mysqld        D 000acd4a     0  1997      1 0x00000000
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552696]  f6595f18 00000086 f771a878 000acd4a 00000000 c088b4c0 f6fc82a4 c088b4c0
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552712]  2e669727 0000217a c088b4c0 c088b4c0 f6fc82a4 c088b4c0 c088b4c0 f65c6800
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552728]  2e6635af 0000217a f6fc8000 f6fc8000 f6595f4c f65c6838 f6595f44 c05b3a45
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552744] Call Trace:
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552755]  [<c05b3a45>] rwsem_down_failed_common+0x75/0x1a0
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552766]  [<c01f0567>] ? handle_mm_fault+0x397/0x4a0
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552776]  [<c05b3bbd>] rwsem_down_read_failed+0x1d/0x30
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552787]  [<c05b3c17>] call_rwsem_down_read_failed+0x7/0x10
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552796]  [<c05b316c>] ? down_read+0x1c/0x20
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552806]  [<c05b64c5>] do_page_fault+0x395/0x3a0
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552815]  [<c05b6130>] ? do_page_fault+0x0/0x3a0
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552823]  [<c05b40f3>] error_code+0x73/0x80
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552240] INFO: task cron:3130 blocked for more than 120 seconds.
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552342] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552449] cron          D 0001c590     0  3130    732 0x00000000
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552464]  f563de1c 00000086 00000000 0001c590 00000000 c088b4c0 f5644264 c088b4c0
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552482]  ff4b58f1 00002209 c088b4c0 c088b4c0 f5644264 c088b4c0 c088b4c0 c2c02000
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552499]  ff3c2b24 00002209 f5643fc0 c1e094c0 f5643fc0 f563de68 f563de2c c05b207a
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552516] Call Trace:
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552540]  [<c05b207a>] io_schedule+0x3a/0x60
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552552]  [<c01d316d>] sync_page+0x3d/0x50
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552562]  [<c05b26c7>] __wait_on_bit_lock+0x47/0x90
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552573]  [<c01e3d3f>] ? vma_prio_tree_remove+0x7f/0xf0
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552581]  [<c01d3130>] ? sync_page+0x0/0x50
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552590]  [<c01d30fe>] __lock_page+0x7e/0x90
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552601]  [<c016ff60>] ? wake_bit_function+0x0/0x50
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552612]  [<c01d52fa>] filemap_fault+0x39a/0x410
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552623]  [<c01eee7c>] __do_fault+0x4c/0x520
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552632]  [<c01f2820>] ? __vma_link_file+0x40/0x70
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552641]  [<c01f2ea4>] ? vma_link+0x84/0xa0
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552651]  [<c01f0368>] handle_mm_fault+0x198/0x4a0
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552663]  [<c028f4e0>] ? ext4_file_mmap+0x0/0x50
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552674]  [<c01f4cbc>] ? do_mmap_pgoff+0x25c/0x300
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552688]  [<c05b623d>] do_page_fault+0x10d/0x3a0
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552699]  [<c01e7c1b>] ? sys_mmap_pgoff+0x12b/0x240
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552708]  [<c05b6130>] ? do_page_fault+0x0/0x3a0
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552717]  [<c05b40f3>] error_code+0x73/0x80
Jan 19 05:16:24 vqnguyen-server2 kernel: [46800.556099] INFO: task mysqld:1997 blocked for more than 120 seconds.
Jan 19 05:16:24 vqnguyen-server2 kernel: [46800.556194] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 19 05:16:24 vqnguyen-server2 kernel: [46800.556300] mysqld        D 0000c059     0  1997      1 0x00000000


```

---

### Post by bakinsoda on 2011-01-19
I too have been having this issue since mid-late December on my Ubuntu 10.04 server (2.6.32-27-generic-pae; P4 laptop).  At first it happened about 1x a week, now it is happening daily.  At first my hunch was that the disk is bad; one of my tables in mysql became corrupted after so many resets.  Could this be it?  Have you guys resolved this yet?  What have you tried and what threads are you following?

Here is an excerpt from my kern.log:
```

Jan 18 22:48:10 vqnguyen-server2 kernel: [23507.540509] lo: Disabled Privacy Ext
ensions
Jan 18 22:49:25 vqnguyen-server2 kernel: [23581.767565] lo: Disabled Privacy Ext
ensions
Jan 18 22:49:37 vqnguyen-server2 kernel: [23593.861591] lo: Disabled Privacy Ext
ensions
Jan 19 02:32:23 vqnguyen-server2 kernel: [36960.552119] INFO: task mysqld:1938 b
locked for more than 120 seconds.
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552224] "echo 0 > /proc/sys/kern
el/hung_task_timeout_secs" disables this message.
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552331] mysqld        D 0003df5a     0  1938      1 0x00000000
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552346]  e395ff38 00000086 fffb2858 0003df5a 00000000 c088b4c0 e3939c24 c088b4c0
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552364]  d310e6d5 0000216f c088b4c0 c088b4c0 e3939c24 c088b4c0 c088b4c0 f65c6800
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552381]  d30ed65e 0000216f e3939980 e3939980 e395ff6c f65c6838 e395ff64 c05b3a45
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552398] Call Trace:
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552420]  [<c05b3a45>] rwsem_down_failed_common+0x75/0x1a0
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552430]  [<c05b3b8d>] rwsem_down_write_failed+0x1d/0x30
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552440]  [<c05b3c26>] call_rwsem_down_write_failed+0x6/0x10
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552450]  [<c05b3144>] ? down_write+0x24/0x30
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552464]  [<c01f6166>] sys_mremap+0x26/0x60
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552475]  [<c01097ac>] syscall_call+0x7/0xb
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552491] INFO: task mysqld:1997 blocked for more than 120 seconds.
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552577] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552683] mysqld        D 000acd4a     0  1997      1 0x00000000
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552696]  f6595f18 00000086 f771a878 000acd4a 00000000 c088b4c0 f6fc82a4 c088b4c0
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552712]  2e669727 0000217a c088b4c0 c088b4c0 f6fc82a4 c088b4c0 c088b4c0 f65c6800
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552728]  2e6635af 0000217a f6fc8000 f6fc8000 f6595f4c f65c6838 f6595f44 c05b3a45
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552744] Call Trace:
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552755]  [<c05b3a45>] rwsem_down_failed_common+0x75/0x1a0
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552766]  [<c01f0567>] ? handle_mm_fault+0x397/0x4a0
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552776]  [<c05b3bbd>] rwsem_down_read_failed+0x1d/0x30
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552787]  [<c05b3c17>] call_rwsem_down_read_failed+0x7/0x10
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552796]  [<c05b316c>] ? down_read+0x1c/0x20
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552806]  [<c05b64c5>] do_page_fault+0x395/0x3a0
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552815]  [<c05b6130>] ? do_page_fault+0x0/0x3a0
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552823]  [<c05b40f3>] error_code+0x73/0x80
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552240] INFO: task cron:3130 blocked for more than 120 seconds.
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552342] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552449] cron          D 0001c590     0  3130    732 0x00000000
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552464]  f563de1c 00000086 00000000 0001c590 00000000 c088b4c0 f5644264 c088b4c0
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552482]  ff4b58f1 00002209 c088b4c0 c088b4c0 f5644264 c088b4c0 c088b4c0 c2c02000
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552499]  ff3c2b24 00002209 f5643fc0 c1e094c0 f5643fc0 f563de68 f563de2c c05b207a
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552516] Call Trace:
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552540]  [<c05b207a>] io_schedule+0x3a/0x60
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552552]  [<c01d316d>] sync_page+0x3d/0x50
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552562]  [<c05b26c7>] __wait_on_bit_lock+0x47/0x90
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552573]  [<c01e3d3f>] ? vma_prio_tree_remove+0x7f/0xf0
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552581]  [<c01d3130>] ? sync_page+0x0/0x50
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552590]  [<c01d30fe>] __lock_page+0x7e/0x90
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552601]  [<c016ff60>] ? wake_bit_function+0x0/0x50
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552612]  [<c01d52fa>] filemap_fault+0x39a/0x410
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552623]  [<c01eee7c>] __do_fault+0x4c/0x520
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552632]  [<c01f2820>] ? __vma_link_file+0x40/0x70
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552641]  [<c01f2ea4>] ? vma_link+0x84/0xa0
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552651]  [<c01f0368>] handle_mm_fault+0x198/0x4a0
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552663]  [<c028f4e0>] ? ext4_file_mmap+0x0/0x50
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552674]  [<c01f4cbc>] ? do_mmap_pgoff+0x25c/0x300
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552688]  [<c05b623d>] do_page_fault+0x10d/0x3a0
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552699]  [<c01e7c1b>] ? sys_mmap_pgoff+0x12b/0x240
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552708]  [<c05b6130>] ? do_page_fault+0x0/0x3a0
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552717]  [<c05b40f3>] error_code+0x73/0x80
Jan 19 05:16:24 vqnguyen-server2 kernel: [46800.556099] INFO: task mysqld:1997 blocked for more than 120 seconds.
Jan 19 05:16:24 vqnguyen-server2 kernel: [46800.556194] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 19 05:16:24 vqnguyen-server2 kernel: [46800.556300] mysqld        D 0000c059     0  1997      1 0x00000000


```

---

### Post by bakinsoda on 2011-01-19
I too have been having this issue since mid-late December on my Ubuntu 10.04 server (2.6.32-27-generic-pae; P4 laptop).  At first it happened about 1x a week, now it is happening daily.  At first my hunch was that the disk is bad; one of my tables in mysql became corrupted after so many resets.  Could this be it?  Have you guys resolved this yet?  What have you tried and what threads are you following?

Here is an excerpt from my kern.log:
```

Jan 18 22:48:10 vqnguyen-server2 kernel: [23507.540509] lo: Disabled Privacy Ext
ensions
Jan 18 22:49:25 vqnguyen-server2 kernel: [23581.767565] lo: Disabled Privacy Ext
ensions
Jan 18 22:49:37 vqnguyen-server2 kernel: [23593.861591] lo: Disabled Privacy Ext
ensions
Jan 19 02:32:23 vqnguyen-server2 kernel: [36960.552119] INFO: task mysqld:1938 b
locked for more than 120 seconds.
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552224] "echo 0 > /proc/sys/kern
el/hung_task_timeout_secs" disables this message.
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552331] mysqld        D 0003df5a     0  1938      1 0x00000000
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552346]  e395ff38 00000086 fffb2858 0003df5a 00000000 c088b4c0 e3939c24 c088b4c0
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552364]  d310e6d5 0000216f c088b4c0 c088b4c0 e3939c24 c088b4c0 c088b4c0 f65c6800
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552381]  d30ed65e 0000216f e3939980 e3939980 e395ff6c f65c6838 e395ff64 c05b3a45
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552398] Call Trace:
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552420]  [<c05b3a45>] rwsem_down_failed_common+0x75/0x1a0
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552430]  [<c05b3b8d>] rwsem_down_write_failed+0x1d/0x30
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552440]  [<c05b3c26>] call_rwsem_down_write_failed+0x6/0x10
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552450]  [<c05b3144>] ? down_write+0x24/0x30
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552464]  [<c01f6166>] sys_mremap+0x26/0x60
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552475]  [<c01097ac>] syscall_call+0x7/0xb
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552491] INFO: task mysqld:1997 blocked for more than 120 seconds.
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552577] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552683] mysqld        D 000acd4a     0  1997      1 0x00000000
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552696]  f6595f18 00000086 f771a878 000acd4a 00000000 c088b4c0 f6fc82a4 c088b4c0
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552712]  2e669727 0000217a c088b4c0 c088b4c0 f6fc82a4 c088b4c0 c088b4c0 f65c6800
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552728]  2e6635af 0000217a f6fc8000 f6fc8000 f6595f4c f65c6838 f6595f44 c05b3a45
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552744] Call Trace:
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552755]  [<c05b3a45>] rwsem_down_failed_common+0x75/0x1a0
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552766]  [<c01f0567>] ? handle_mm_fault+0x397/0x4a0
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552776]  [<c05b3bbd>] rwsem_down_read_failed+0x1d/0x30
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552787]  [<c05b3c17>] call_rwsem_down_read_failed+0x7/0x10
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552796]  [<c05b316c>] ? down_read+0x1c/0x20
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552806]  [<c05b64c5>] do_page_fault+0x395/0x3a0
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552815]  [<c05b6130>] ? do_page_fault+0x0/0x3a0
Jan 19 02:33:58 vqnguyen-server2 kernel: [36960.552823]  [<c05b40f3>] error_code+0x73/0x80
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552240] INFO: task cron:3130 blocked for more than 120 seconds.
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552342] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552449] cron          D 0001c590     0  3130    732 0x00000000
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552464]  f563de1c 00000086 00000000 0001c590 00000000 c088b4c0 f5644264 c088b4c0
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552482]  ff4b58f1 00002209 c088b4c0 c088b4c0 f5644264 c088b4c0 c088b4c0 c2c02000
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552499]  ff3c2b24 00002209 f5643fc0 c1e094c0 f5643fc0 f563de68 f563de2c c05b207a
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552516] Call Trace:
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552540]  [<c05b207a>] io_schedule+0x3a/0x60
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552552]  [<c01d316d>] sync_page+0x3d/0x50
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552562]  [<c05b26c7>] __wait_on_bit_lock+0x47/0x90
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552573]  [<c01e3d3f>] ? vma_prio_tree_remove+0x7f/0xf0
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552581]  [<c01d3130>] ? sync_page+0x0/0x50
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552590]  [<c01d30fe>] __lock_page+0x7e/0x90
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552601]  [<c016ff60>] ? wake_bit_function+0x0/0x50
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552612]  [<c01d52fa>] filemap_fault+0x39a/0x410
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552623]  [<c01eee7c>] __do_fault+0x4c/0x520
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552632]  [<c01f2820>] ? __vma_link_file+0x40/0x70
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552641]  [<c01f2ea4>] ? vma_link+0x84/0xa0
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552651]  [<c01f0368>] handle_mm_fault+0x198/0x4a0
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552663]  [<c028f4e0>] ? ext4_file_mmap+0x0/0x50
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552674]  [<c01f4cbc>] ? do_mmap_pgoff+0x25c/0x300
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552688]  [<c05b623d>] do_page_fault+0x10d/0x3a0
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552699]  [<c01e7c1b>] ? sys_mmap_pgoff+0x12b/0x240
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552708]  [<c05b6130>] ? do_page_fault+0x0/0x3a0
Jan 19 02:42:23 vqnguyen-server2 kernel: [37560.552717]  [<c05b40f3>] error_code+0x73/0x80
Jan 19 05:16:24 vqnguyen-server2 kernel: [46800.556099] INFO: task mysqld:1997 blocked for more than 120 seconds.
Jan 19 05:16:24 vqnguyen-server2 kernel: [46800.556194] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 19 05:16:24 vqnguyen-server2 kernel: [46800.556300] mysqld        D 0000c059     0  1997      1 0x00000000


```

---

### Post by DimensionSlider on 2012-03-19
Same problem since i`ve switched from Legacy Network Adapter to Network Adapter hv_netsvc. I`m running Hyper-V VPS on Ubuntu 11.10.

Happens every day.

---

### Post by edubidu on 2012-04-18
Same problem with ubuntu zfs issues and newest kernel 3.0.0-17 INFO: task zfs:5127 blocked for more than 120 seconds

---

### Post by oldos2er on 2012-04-18
Closed. Please start a new thread.

---

