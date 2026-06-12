---
title: "Adding USB sata drives"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by Charlie Chick on 2009-03-22
Hello Everybody,

I have an old 160GB sata drive which I would like to use. I have 2 ata drives for which I bought USB caddies and they work without problem. For the Sata drive, I bought a Unitek SATA HDD USB docking station, but when I plug it in the sata drive does not show anywhere. The 4 USB sockets on the front panel show, but not the actual drive. 

It works in Windoze. You have to go to Disk Manager and mount the drive, but after that, it shows and is useable.

Back in Ubuntu - I downloaded Disk Manager but that didn't show it either. I then downloaded Mount Manager and the sata drive shows in that program, but nowhere else, so I still cannot access this disk to use it. Can anybody help, please?

Many thanks,

Charlie

---

### Post by LiamWilson on 2009-03-22
Let's see...

try a ```
dmesg | tail
``` and see if you can see it listed there.

If not, see if ```
dmesg | grep -i sata
``` works.

---

### Post by Charlie Chick on 2009-03-22
> **LiamWilson said:**
> Let's see...

try a ```
dmesg | tail
``` and see if you can see it listed there.

If not, see if ```
dmesg | grep -i sata
``` works.

Yes, it *appears* to show (my technical knowledge is not that good) but I still can't see it in COMPUTER or somewhere where I can open a graphical box and do something with it.

Charlie

---

### Post by LiamWilson on 2009-03-22
What output do you get with each command?

---

### Post by Charlie Chick on 2009-03-22
dmesg | tail gives: 

[ 8223.049681] Write-error on swap-device (8:16:3600)
[ 8223.049696] Write-error on swap-device (8:16:3608)
[ 8234.088061] Write-error on swap-device (8:16:3600)
[ 8234.088076] Write-error on swap-device (8:16:3608)
[ 8247.004215] Write-error on swap-device (8:16:3600)
[ 8247.004230] Write-error on swap-device (8:16:3608)
[ 8247.304289] Write-error on swap-device (8:16:3600)
[ 8247.304301] Write-error on swap-device (8:16:3608)
[ 8256.104292] Write-error on swap-device (8:16:3600)
[ 8256.104306] Write-error on swap-device (8:16:3608)

and dmesg | grep -i sata gives:

[    4.420334] ata3: SATA max UDMA/133 cmd 0xfe00 ctl 0xfe10 bmdma 0xfea0 irq 20
[    4.420339] ata4: SATA max UDMA/133 cmd 0xfe20 ctl 0xfe30 bmdma 0xfea8 irq 20

I don't know what it all means. Sorry.

Charlie

---

### Post by LiamWilson on 2009-03-22
Hmm...Does it say anything like HDA3 or something in Mount Manager?

---

### Post by Charlie Chick on 2009-03-22
> **LiamWilson said:**
> Hmm...Does it say anything like HDA3 or something in Mount Manager?

No, only sda is showing.....

---

### Post by Charlie Chick on 2009-03-22
Ah, stupid me - I had disconnected the unit! I'll re-connect and re-post after Mothers Day lunch which is now upon me.

Charlie

---

### Post by Charlie Chick on 2009-03-22
> **LiamWilson said:**
> Hmm...Does it say anything like HDA3 or something in Mount Manager?

It has now come up as sdf in Mount Manager, but I still can't see it anywhere else! I think that I'm going to take it back to Maplin and buy an ordinary sata caddy for this drive.

---

### Post by Charlie Chick on 2009-03-23
I took the unit back to Maplin and swapped it for a SATA USB caddy. It all works now. Thanks for your help.

Charlie

---

### Post by LiamWilson on 2009-03-23
Glad I could have been of some help!

---

