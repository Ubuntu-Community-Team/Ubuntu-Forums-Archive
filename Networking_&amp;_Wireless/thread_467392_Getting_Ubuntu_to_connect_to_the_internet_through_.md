---
title: "Getting Ubuntu to connect to the internet through and XP machine"
date: 2007-06-07
forum: Networking &amp; Wireless
---

### Post by unready%20cincinnatus on 2007-06-07
I only have a wireless internet connection available to me, and my desktop only has an ethernet port, no wireless card.  It's dual-booting XP Pro and Feisty Fawn.  I also have a laptop running XP home.  I've set up a small network so the PC can connect to the internet through the laptop via ethernet cable.  This works perfectly when I boot XP.  Ubuntu, on the other hand, says there is no network connection.  When I boot Ubuntu, the laptop constantly tries to connect and fails, giving a "network cable is unplugged" message.

Any ideas how I can get these two machines to play nice?

---

### Post by dmizer on 2007-06-07
on your desktop (booted to windows) ... what are your settings in: control panel > network connections > tcp/ip > properties 

additionally, when booted to feisty, please post the output of the following command:
```
ifconfig
```

finally, the cable you've used to connect your laptop to your desktop, is it a crossover cable or is it a regular ethernet cable (a crossover cable should say "X" or "cross" or "crossover" or otherwise be designated as such somewhere on the cable itself).  some network adapters are capable of automatically crossing a direct connection when needed, but it may not work the same in ubuntu.

---

### Post by unready%20cincinnatus on 2007-06-09
Hey, thanks for responding.  

Ubuntu has decided all on its own to connect now, so I think I'll be alright.  I appreciate the offer of help, though.

---

