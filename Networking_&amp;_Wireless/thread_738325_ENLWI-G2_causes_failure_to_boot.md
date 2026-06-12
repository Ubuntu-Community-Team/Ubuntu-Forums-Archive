---
title: "ENLWI-G2 causes failure to boot"
date: 2008-03-28
forum: Networking &amp; Wireless
---

### Post by marconix on 2008-03-28
I just installed Ubuntu 7.10 on an old Dell computer (P4 2.4 GHz, 512MB RAM), but not without having to take out my PCI wireless card (ENLWI-G2). When the card is seated, the Live CD loads the screen with the orange progress bar and then stalls near the end (waited 5 minutes, and the CD even stopped spinning). When the card is taken out, installation runs smoothly. 

When I put the card back in, the Ubuntu stalls in a blank screen after the GRUB loader. After taking the card out, Ubuntu loads and runs without complications.

As a longtime windows user, I have almost no experience with Ubuntu. Any help would be much appreciated.

---

### Post by dstew on 2008-03-28
Some thoughts...

Does your computer have another PCI card or built-in device that might be interfering? Does it have, for example, built-in ethernet? If so, try disabling it in BIOS if you can, and see if you can boot.

Also, you can try kernel options. My guess is that you are having an interrupt confict. You can try adding **noapic** and **nolapic** to the kernel line in grub's /boot/grub/menu.lst file. That shuts off the Advanced Programmable Interrupt controller, and forces the system to use the plain old interrupts. It might be a hair slower, but it might work better. Anyway, it is just a guess.

Can you put the wireless card in a different slot? Sometimes, that can make a difference. Does the card work in another computer? Maybe the card is damaged.

---

### Post by marconix on 2008-03-29
Thanks for the tips.
I tried turning off the onboard NIC, switching the card's PCI slot and adding noapic and nolapic to the kernel line, but it still doesn't boot up with the card. Once when I removed "Quiet" from the bootloader, it displayed the words Unidentified Handle 10, Ignoring,  and proceeded to boot; I could not find the card on the list of adapters in Networking. Since then the message has not shown up, nor have I been able to boot.
The card was previously working under Windows.
Is there anything else I can do?

---

### Post by dstew on 2008-03-29
I would only be guessing at this point. I would try the kernel option **acpi=off** before giving up. Another thing might be to look at the system log after a failed boot with the card in place. It is stored in the directory /var/log. The previous system log is named syslog.0, so the command to examine it would be```
more /var/log/syslog.0
```There might be a clue in there as to why it is not happy with the card.

---

