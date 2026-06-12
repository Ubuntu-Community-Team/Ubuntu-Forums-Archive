---
title: "2 hp printers sharing one printer seen the other is not"
date: 2008-02-22
forum: Networking &amp; Wireless
---

### Post by ljonesj on 2008-02-22
i have 2 hp printers. the first printer is a old 632c deskjet that the computers can see on the network but one computer cannot use it as there are no vista drivers for the printer. the other printer is a hp 4180 multi function printer i have it setup the same way as the other printer but both my xp and vista machine's cannot find it. i have both of these printers on a ubuntu machine and it can print to either printer as both are hooked up to it any help would be helpful and i have both machines hooked threw a usb hub if that makes a difference

---

### Post by nixscripter on 2008-02-22
> **ljonesj said:**
> i have 2 hp printers. the first printer is a old 632c deskjet that the computers can see on the network but one computer cannot use it as there are no vista drivers for the printer. the other printer is a hp 4180 multi function printer i have it setup the same way as the other printer but both my xp and vista machine's cannot find it. i have both of these printers on a ubuntu machine and it can print to either printer as both are hooked up to it any help would be helpful and i have both machines hooked threw a usb hub if that makes a difference

Let me ensure I've got this right:

```

+--------------+
| 632c deskjet |--+
+--------------+  |  +----------+
                  +--| Ubuntu   |
+--------------+  |  +----------+
| hp 4180 mf   |--+        |
+--------------+        +--------+
                        | Router |-----+
                        +--------+     |
                            |          |
                      +----------+ +--------+
                      | Win XP   | | Vista  |
                      +----------+ +--------+

```

1. The Ubuntu machine can use both printers.
2. The Vista and the XP machine can find the old printer, but the Vista machine can't use it.
3. Neither can find the new printer.

It sounds like Ubuntu is not sharing the second printer. Unfortunately, I don't know how to get the details of the printing system. What does your printer configuration dialog look like (Ubuntu menu -> System -> Administration -> printing)?

---

