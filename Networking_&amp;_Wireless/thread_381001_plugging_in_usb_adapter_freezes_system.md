---
title: "plugging in usb adapter freezes system?"
date: 2007-03-10
forum: Networking &amp; Wireless
---

### Post by kacheng on 2007-03-10
Hi.

According to the wiki,
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")
all I need to do to get the dlink dwl-122 adapter working is to install **linux-wlan-ng**.

However, whenever I plug the usb adapter in, the whole system locks up. 

Completely. Frozen screen, no mouse, no keyboard, nothing. The only thing to do is a hard reset.

Anyone have any ideas why this might be?

---

### Post by davidmit on 2007-03-18
Hiya, I have this problem as well. I've read quite a few posts with this problem but found no answers.

kacheng lots of threads recommend adding: noapic irqpoll and acpi=off to the grub menu and some say this helped them so might be worth a go. Didnt work for me though. 

I have a Toshiba A60 Laptop (2.98 celeron, 512mb memory)
running Ubuntu Edgy

When loading I do get a warning about a error that occured with my bios and it recommended trying pnpbios=off which I did but that didnt help either. Whenever I plug in any USB device (USB memory Stick, USB Mouse, Camera) into any USB the system locks up and needs to be hard reset.

Because of this I've no idea how to see the problem as you cant do anything after plugging the USB in. I've turned off legacy USB use in the bios but no help. So I'm as stuck as kacheng. Please, any ideas are very welcome as no USB is rubbish. :0)

---

### Post by vronp on 2007-05-08
Same problem here on Dell Inspiron 9400 running Feisty.

I plug in a Linksys WUSB54G usb adapter and the keyboard locks up.

---

### Post by YetAnotherNoob on 2007-05-29
I also had this problem.  I was told that it was probably a memory problem, which I did not beleive.  I ran dozens of memory tests, and they never failed.  It was so disruptive I gave up and am back on windows.  In a version or two's time I'll try again.

---

