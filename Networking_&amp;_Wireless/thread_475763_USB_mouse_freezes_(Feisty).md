---
title: "USB mouse freezes (Feisty)"
date: 2007-06-16
forum: Networking &amp; Wireless
---

### Post by Kim Ming Yap on 2007-06-16
In short:

1) Motherboard (winfast) has built-in usb keyboard / mouse (driver - i think). If i disable both and edgy boots - no problem. I think Ubuntu uses its own driver for both

2) if i enable the usb keyboard / mouse on the motherboard (i need to enable it if i want to move my cursor in grubs to select the O.S of my choice .. else the cursor wont move. At this stage the ubuntu usb mouse / keyboard driver not loaded yet). Once i have selected my choice of O.S in grubs and boot that O.S. (example edgy again), on and off the mouse and keyboard freezes in gnome.

Please advice.

Ubuntu 6.10.
AMD 64x2

---

### Post by empthollow on 2007-06-16
i had a problems w/ my toshiba laptop for a long time with randomly losing my usb mouse.  for me it worked w/o fglrx driver.  i finally found the solution on [www.linux-laptop.net](www.linux-laptop.net) .  i needed to add "irqpoll" and "noapic" to my kernel options at boot. this can be done in /boot/grub/menu.lst.  hope that helps, i've found no other solution in these forums or anywhere else. good luck.

---

### Post by Kim Ming Yap on 2007-06-16
Thanks. Mind if you could give me the exact statements?

I am new to linux.

Thanks.

---

### Post by empthollow on 2007-06-17
the easiest way is to chng the /boot/grub/menu.lst
on the line where you see 
```
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=8f487494-dea3-425e-9d51-439f0848b3d8 ro quiet splash 
```
add ```
noapic irqpoll
```
mine looks like this but don't copy and paste it because the uuid may be different
```
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=8f487494-dea3-425e-9d51-439f0848b3d8 ro quiet splash noapic irqpoll
```

---

### Post by rrjohnboy on 2008-02-19
may be way off base here, but I was having problems with USB mouse. It would randomely stop after between 5 - 20 mins & I would have to reboot. The solution for me was that I had installed the standard live CD which was geared more towards AMD chipsets. I downloaded the alternative Intel installation CD & it now works perfectly, just like when I was running it on my old AMD board. Hope it helps.

---

