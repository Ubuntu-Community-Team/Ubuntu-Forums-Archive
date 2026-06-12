---
title: "Wireless Stops Working"
date: 2007-02-10
forum: Networking &amp; Wireless
---

### Post by the7yearplan on 2007-02-10
Just started to use linux and Ubuntu and I got my wireless card to working via ndiswrapper with the windows driver for the broadcom 1390 wlan card that came in my Dell Latitude D620 but from time to time my wireless networking just stops working.  I thought it was a problem with Beryl as everytime I ran Beryl I would lose internet conectivity but after I stopped running Beryl the problem still occurs.  Here is the dmesg output regarding ndiswrapper when the issue occurs:

```
[17179826.664000] irq 7: nobody cared (try booting with the "irqpoll" option)
[17179826.664000]  <c01499a4> __report_bad_irq+0x24/0x80  <c0149a9d> note_interrupt+0x9d/0x270
[17179826.664000]  <f8e60102> ndis_isr+0x52/0xc0 [ndiswrapper]  <c0149448> __do_IRQ+0xf8/0x110
[17179826.664000]  <c0105c89> do_IRQ+0x19/0x30  <c010408a> common_interrupt+0x1a/0x20
[17179826.664000]  <c0149307> handle_IRQ_event+0x17/0x60  <c01493ed> __do_IRQ+0x9d/0x110
[17179826.664000]  <c0105c89> do_IRQ+0x19/0x30  <c010408a> common_interrupt+0x1a/0x20
[17179826.664000]  <c0149307> handle_IRQ_event+0x17/0x60  <c01493ed> 
__do_IRQ+0x9d/0x110
[17179826.664000]  <c0105c89> do_IRQ+0x19/0x30  <c010408a> common_interrupt+0x1a/0x20
[17179826.664000]  <c012782f> __do_softirq+0x5f/0xe0  <c01278e5> do_softirq+0x35/0x40
[17179826.664000]  <c010413c> apic_timer_interrupt+0x1c/0x30  <f88596dd> acpi_processor_idle+0x220/0x3af [processor]
[17179826.664000]  <c0102122> cpu_idle+0x42/0xb0  <c03f27a1> start_kernel+0x321/0x3a0
[17179826.664000]  <c03f2210> unknown_bootoption+0x0/0x270 
[17179826.664000] handlers:
[17179826.664000] [<f8e600b0>] (ndis_isr+0x0/0xc0 [ndiswrapper])
[17179826.664000] Disabling IRQ #7
```

I have restarted with the irqpoll option but the problem still persists.  Any ideas?

---

### Post by spd106 on 2007-02-10
You could try downloading a newer driver.

---

### Post by the7yearplan on 2007-02-10
I'm using the newest driver for my card.  Is there another kernal boot option I could try besides irqpoll that may stop this interruption?

---

### Post by lojic on 2007-02-10
If this was happening before the 2.6.17-11 kernel update than the following thread is probably not related, but if it only happened after that, you may want to check it out.

[http://ubuntuforums.org/showthread.php?t=358004](http://ubuntuforums.org/showthread.php?t=358004)

---

