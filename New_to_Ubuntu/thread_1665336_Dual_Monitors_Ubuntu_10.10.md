---
title: "Dual Monitors Ubuntu 10.10"
date: 2011-01-12
forum: New to Ubuntu
---

### Post by khubliakhan on 2011-01-12
Hi all,

My system is a 3.2GHz Pentium: 1 GB RAM: 160GB HDD

My monitors are a 19" Belinea and a 22" Belinea.

I installed Ubuntu 10.10 (32-bit) on my system and almost everything went well. The only issue I have is that I cannot configure dual monitors correctly using System > Preferences > Monitors.

No matter what configuration I use the extended desktop on my 22" Belinea is always somewhat garbled. I would appreciate any help.

The output from using **lspci | grep VGA**:

[CENTER]01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AQ [Radeon 9600][/CENTER]

Thanks in advance

---

### Post by khubliakhan on 2011-01-12
OK - finally solved the problem by following the instructions here:

[Dual monitors in maverick]("http://ubuntuforums.org/showthread.php?t=1594087&page=1")

And here:

[10.10 Dual Monitor Setup]("http://ubuntuforums.org/showthread.php?t=1597612")

Its all about trying and testing things - I don't think there is a one stop solution for everyone.

Since my graphics card is an ATI Card I essentially did the following:

[LIST=1]
[*]Install FGLRX via Synaptic Package Manager
[*]In the Terminal window type in sudo ''aticonfig -- initial'' (without quotes)
[*]Restart
[*]Reconfigure Monitors using System > Preferences > Monitors
[/LIST]

The following is also a good guide for Ati Cards:
[URL="http://*************/hub/How-to-Install-FGLRX-in-Ubuntu-1010"]
How to Install FGLRX in Ubuntu 10.10[/URL]

Hope this helps

---

### Post by clhsharky on 2011-01-12
ATI fglrx drivers only suport ATI HDxxxx chips in Maverick,
not the older legacy chips.
> 01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AQ [Radeon 9600]
is a legacy chip.

Please do not install fglrx driver on legacy ATI chip, it will not work correctly if at all.

Sharky

---

### Post by khubliakhan on 2011-01-12
OK so whats the best way to remove it?

Thanks

---

### Post by clhsharky on 2011-01-12
khubliakhan

To flush fglrx instructions here

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20Need%20to%20purge%20-fglrx](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20Need%20to%20purge%20-fglrx)



Sharky

---

