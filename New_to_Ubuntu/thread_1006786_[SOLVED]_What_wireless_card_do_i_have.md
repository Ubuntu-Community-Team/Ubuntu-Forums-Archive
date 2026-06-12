---
title: "[SOLVED] What wireless card do i have?"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by hoverX on 2008-12-09
how do i figure out what model wireless card has been included in my laptop?

I purchased a DELL XPS1530 and i thought i bought one that came with a Draft-N wireless card.  when i connect to my wireless router i only connect at 54Mb/s.  I ran the hardware testing wizard and it wasn't specific enough.  It told me i either had a abg or abgn wireless card.  Is there any other easy way to determine the model number of my card?

---

### Post by Technoviking on 2008-12-09
Run ```
lspci
``` from a terminal.

Look at the list for something like this
```
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
```

---

### Post by snova on 2008-12-09
The best way I know of is to type 'lspci' into a terminal. It'll be there, along with all your other hardware (or most of it).

---

### Post by nhasian on 2008-12-10
the best way i know of to see what network adaptors you have is

```
lshw -C network
```

---

