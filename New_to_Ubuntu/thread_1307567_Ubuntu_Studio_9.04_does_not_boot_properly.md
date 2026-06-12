---
title: "Ubuntu Studio 9.04 does not boot properly"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by Faced Wrist on 2009-10-31
Hi! 

Now, I am absolutely new to Ubuntu and Linux, please take that into consideration when replying to this thread. 

So, here's my problem:

I just installed Ubuntu Studio 9.04 (Dual boot with Win XP pro). 
I had some trouble getting GRUB to work properly, but somehow i managed to get that working, so thats probably not what's wrong.

GRUB boots XP just fine, but when booting Ubuntu i get a lot of text and then it freezes.
I Cant read all of the text since I'm not as fast as my computer. I honestly dont know what to do. This is whats on my screen:

6000)
[    0.755863] Stack:
[    0.755907]  f67b7f48 c015d1b9 c0130850 f667f0a0 00000001 f66cac00 00000000 000008ff
[    0.755907]  f67b7f58 c01213f1 00000001 c051e740 f67b7f84 c018255c f667f0a0 c0812500
[    0.755907]  f67b4e20 000008ff 00000000 00000000 c078bb80 f66cac00 000008ff f67b7f9c
[    0.755907] Call Trace:
[    0.755907]  [<c015d1b9>] ? tick_handle_periodic+0x19/0x80
[    0.755907]  [<c0310850>] ? finish_task_switch+0x50/0x120
[    0.755907]  [<c01213f1>] ? hpet_interrupt_handler+0x11/0x30
[    0.755907]  [<c018255c>] ? handle_IRQ_event+0x5c/0x120
[    0.755907]  [<c0182f93>] ? thread_edge_irq+0x63/0xd0
[    0.755907]  [<c01831e2>] ? do_irqd+0xc2/0x160
[    0.755907]  [<c0183120>] ? do_irqd+0x0/0x160
[    0.755907]  [<c015164c>] ? kthread+0x3c/0x70
[    0.755907]  [<c0151610>] ? kthread+0x0/0x70
[    0.755907]  [<c0105547>] ? kernel_thread_helper+0x7/0x10
[    0.755907] Code: e8 f5 ff ff 85 c0 75 d9 83 c4 08 5d 5e 5f 5d c3 89 f6 8d bc 27 00 00 00 00 39 05 68  16 79 c0 55 89 e5 74 1d 64 a1 08 20 81 c0 <8b> 40 30 83 e0 03 83 f8 03 0f 94 c0 0f b6 c0 e8 4b 92 fe ff 5d
[    0.755907] EIP: [<c015d141>] tick_periodic+0x11/0x70 SS:ESP 0068:f67b7f28
[    0.755907] ---[ end trace 4eaa2a86a8e2da22 ]---

Is there anyone out there who understand what it means?
Does anyone know what to do from here?

Any help appreciated!

Thanks!

---

### Post by mapes12 on 2009-10-31
Please can you post the output to ```
sudo fdisk -l
```

You may also want to have a read through this and see if you set up the dual boot configuration correctly: [http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

