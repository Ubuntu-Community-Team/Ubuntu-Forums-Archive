---
title: "Looking for a linmodem recommendation"
date: 2007-03-15
forum: Networking &amp; Wireless
---

### Post by TimP on 2007-03-15
I'm looking to buy a relatively cheap (under $20) PCI software modem for my Linux box. I'm primarily looking to use it for dialing into the Linux box remotely so transfer speeds aren't exactly crucial since I will just be using it as a remote text console. I've been reading guides, FAQs, HOWTOs, forums, etc. for most of the day but haven't found a single recommended chipset. Ideally it would be great if I could just plug it in and have it work like my Intel Gigabit NIC since I'd rather not have to manually recompile kernel modules for updates. I'm using Ubuntu 5.10 on a stable box, but will be upgrading to 6.06 or 7.04 once 7.04 is out and 5.10 is out of support.

From what I've read, here's generally what I've seen:

Motorola chipset: I've heard nothing but bad things. Offered an archaic binary driver years ago.
Conexant chipset: used to be the best, but less popular because the full driver costs money ($20)
Intel chipset: doesn't seem to be in a lot of modems, but seems to have an Intel supported open source driver (like their network cards and video cards)

I'm looking to buy it on Newegg, so if anyone has a particularly good modem they've used from there, I'd appreciate a link.

Thanks!
Tim

---

### Post by Mr. C. on 2007-03-16
Hmmm... spending this much time and effort for a $20 modem, when speed doesn't matter?

Just find a name that's supported; for your application, one is as good as the next.

I know I must have a couple of winmodem's laying around unused, probably Conexant, one US robotics I think (its been too long).  If I do still have them, you can have them for shipping cost from CA.

MrC

---

### Post by TimP on 2007-03-16
> **Mr. C. said:**
> Just find a name that's supported; for your application, one is as good as the next.

Unfortunately that's my problem. I can't find any information about current modems that can be used on current Linux distros. Most of the documentation refers to old distros (4+ years old) and modems that are no longer produced. Initially I thought, "since the volume of documentation declined, surely this must be trivially easy now", but on the contrary when I go looking I find quite a bit of linmodem/Ubuntu headaches.

I figured since I have the ability to choose a best fit modem before buying instead of being stuck with a hard to configure modem, I was hoping I could get some opinions on what works the best with the least configuration hassle. Ideally something that "just works" with a reboot and doesn't require compiling new kernel modules for every kernel upgrade would be the best.

---

### Post by digitalgecko on 2007-03-16
Software modems are alot of trouble. I finally bought a serial modem from office depot (their brand) for $49 and it works right out of the box.

:guitar:

---

### Post by Mr. C. on 2007-03-16
I agree with the previous poster.  WinModems, emulated via Linmodem in Linux have compatibility issues, are slower, more painful, and less reliable.

Unless you are a masochist, get an standard V.92 controller based modem and call it a day.

MrC

---

### Post by TimP on 2007-03-16
I suppose the next question is, does anyone know where you can buy a decent PCI hardware modem? I only have one serial port on my machine and I'd prefer to leave it available since I have multiple unused PCI slots.

Thanks!

---

### Post by Sepero on 2007-08-10
I know this thread is kinda old.
Generally the slmodems appear to be relatively good and easy.

---

