---
title: "dell wireless/ndiswrapper crash"
date: 2006-11-12
forum: Networking &amp; Wireless
---

### Post by Jan Hrbacek on 2006-11-12
Irregularly, my wireless stops to operate. This is dmesg log:

```
[17179712.860000] irq 177: nobody cared (try booting with the "irqpoll" option)
[17179712.860000]  <c01499a4> __report_bad_irq+0x24/0x80  <c0149a9d> note_interrupt+0x9d/0x270
[17179712.860000]  <f8c0e002> ndis_isr+0x52/0xc0 [ndiswrapper]  <c0149448> __do_IRQ+0xf8/0x110
[17179712.860000]  <c0105c89> do_IRQ+0x19/0x30  <c010408a> common_interrupt+0x1a/0x20
[17179712.860000]  <c0149307> handle_IRQ_event+0x17/0x60  <c01493ed> __do_IRQ+0x9d/0x110
[17179712.860000]  <c0105c89> do_IRQ+0x19/0x30  <c010408a> common_interrupt+0x1a/0x20
[17179712.860000]  <c0149307> handle_IRQ_event+0x17/0x60  <c01493ed> __do_IRQ+0x9d/0x110
[17179712.860000]  <c0105c89> do_IRQ+0x19/0x30  <c010408a> common_interrupt+0x1a/0x20
[17179712.860000]  <c02daad9> _spin_unlock_irqrestore+0x9/0x10  <c025ee63> i8042_interrupt+0x1d3/0x220
[17179712.860000]  <c010408a> common_interrupt+0x1a/0x20  <c0149323> handle_IRQ_event+0x33/0x60
[17179712.860000]  <c01493ed> __do_IRQ+0x9d/0x110  <c0105c89> do_IRQ+0x19/0x30
[17179712.860000]  <c010408a> common_interrupt+0x1a/0x20  <c012782f> __do_softirq+0x5f/0xe0
[17179712.860000]  <c01278e5> do_softirq+0x35/0x40  <c0105c8e> do_IRQ+0x1e/0x30
[17179712.860000]  <c010408a> common_interrupt+0x1a/0x20 
[17179712.860000] handlers:
[17179712.860000] [<f8c0dfb0>] (ndis_isr+0x0/0xc0 [ndiswrapper])
[17179712.860000] Disabling IRQ #177
```

I have already added irqpoll option as a boot parameter. It obviously didn't help. 

Any idea?

/boot/grub/menu.lst
```

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash irqpoll
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot


```

---

### Post by dbott67 on 2006-11-12
Do you have an nVidia card with the 'nvidia' driver (as opposed to 'nv' driver)?  Check your /etc/X11/xorg.conf file.  If you have:
```
Section "Device"
    Identifier     "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
    Driver         "**[COLOR="Red"]nvidia[/COLOR]**"
        Option          "RenderAccel"           "true"
EndSection
```

Then check this thread (post #46):
[http://www.ubuntuforums.org/showthread.php?p=1741301#post1741301](http://www.ubuntuforums.org/showthread.php?p=1741301#post1741301)

There appears to be an issue with the proprietary nVidia binary driver and Broadcom wireless apapters.  Change the driver above to "nv" and it should fix the problem (although your video performance may go in the toilet).

-Dave

---

### Post by Jan Hrbacek on 2006-11-13
Yes, I do have nvidia driver. But disabling it and returning to nv driver would really mean that my graphic performance goes to the toilet. 

Is the problem going to be fixed soon?

---

