---
title: "Front USB ports do not see USB flash Drive..."
date: 2009-12-23
forum: New to Ubuntu
---

### Post by Odin888 on 2009-12-23
Hi all. Still plugging along as a newbie with Ubuntu 9.1. For some reason when I plug my flash drive into the USB ports on the front of my tower, the USB is not seen. When I plug the same flash drive into my back USB ports it is recognized...Any help on having my front USBs recognizing my flash drive would just be Ubuntu groovy.

Thanks
Peter

---

### Post by Sef on 2009-12-23
What happens if you plug in other devices too?

---

### Post by Odin888 on 2009-12-24
Same with external hard drive. Nothing seen.

---

### Post by redcarpet on 2009-12-24
I had this prob once and I had a peep into the case and found the ports were not wired up (!)

---

### Post by mgranet on 2009-12-24
> **redcarpet said:**
> I had this prob once and I had a peep into the case and found the ports were not wired up (!)

Seconded.

---

### Post by Odin888 on 2009-12-25
Ports are definitely wired in, and they were used when Windows (gag me) was the OS.

---

### Post by Luminous_Rogue on 2010-01-06
I am having the same problem with my desktop. the USB ports worked fine when i had windows installed on it.

I tried all the ports on my desktop to see if maybe the port was bad but none of them work. I am trying to back up all files onto an external hard drive.

---

### Post by Methuselah on 2010-01-06
Plug it out, plug it back in, and type dmesg in a terminal.
Do you see anything about the USB device?

Also while it is plugged in, execute lsusb in a terminal.
It should list all the USB devices that have been detected.

It could be possible that they are being recognized but not automounted for whatever reason.

---

### Post by Luminous_Rogue on 2010-01-06
I unplugged it and then plugged it back in and still nothing. i typed lsusb and nothing came up. and nothing came up with dmesg.

i am really new at Ubuntu. I have used for only for about a week now... still trying to get it all working.

the computer i installed it on is  about 7 years old.

---

### Post by Spooky257 on 2010-02-21
I'm having the same problem and this is what I'm getting:

[ 2701.972495] usb 4-1: new full speed USB device using uhci_hcd and address 20
[ 2707.388032] usb 4-1: device not accepting address 20, error -71
[ 2707.500029] usb 4-1: new full speed USB device using uhci_hcd and address 21
[ 2712.912217] usb 4-1: device not accepting address 21, error -71
[ 2712.912244] hub 4-0:1.0: unable to enumerate USB device on port 1

Any help would be appreciated.

---

### Post by Odin888 on 2010-02-21
Hi all. Used mount manager from Ubuntu Software Center. Works great now.

---

