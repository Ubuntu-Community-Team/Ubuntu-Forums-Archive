---
title: "NIC card not detected"
date: 2008-02-19
forum: Networking &amp; Wireless
---

### Post by timjayko on 2008-02-19
hey might anyone know why  my NIC card isnt being detected, but when I shutdown, and unplug/replug my PSU cord from the mobo, and replug then reboot. it works


abit IB9 mobo
want to say broadcom brand or whatever broad something brand NIC
computer built it not a year ago
intel core2duo cpu
ifconfig -a picked up nothing (before unplug/replug of PSU cord)
just lo0 loop thingamajig

---

### Post by jhetrick62 on 2008-02-19
May look into getting the proper driver for you mobo.  Do you dual-boot this system with a windows flavor also?

Jeff

---

### Post by timjayko on 2008-02-19
yah I dual boot vista with it.. and it works fine in vista.. but vista is only for games (rarely play on pc anymore after ps3 investment)
thanks for the quick reply

---

### Post by jhetrick62 on 2008-02-19
OK, I saw this problem a year or so ago on a Biostar board that I have.  When dual-booting, the NIC card would not release the windows drivers properly without powering down the cpu!!  Doesn't happen on every board as I did dual-boot on other machines also without issues, but I did have one that had your issue and I was running FC4 at the time with Windows 2000.

Sounds like you have the same problem.  Rather than re-booting when you exit windows and grabbing Ubuntu off of Grub, I'll bet if you shutdown when exiting windows every time and then restart and select from Grub, your problem will go away.

Test it,
Jeff

---

### Post by timjayko on 2008-02-19
okay thanks.. its nice to know what exactly was happening..

---

