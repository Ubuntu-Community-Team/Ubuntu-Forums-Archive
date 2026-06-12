---
title: "Dell 9400/e1705 Broadcom wireless SOLVED"
date: 2006-11-17
forum: Networking &amp; Wireless
---

### Post by casley on 2006-11-17
I've just bought a Dell E1705 (9400) with the Broadcom 43xx wireless. Everything worked except the wireless. I searched every Howto - ndiswrapper, fwcutter, build nsdiwrapper etc etc. Nothing worked. ndiswrapper -l showed driver and hardware present but ah no wlan0...

Then an epiphany...

Where is that bcmwl5 driver?... Shouldn't it be in /etc/ndiswrapper? NO! 
Little bastard! If you run ndiswrapper -i bcmwl5.inf it creates/installs into it's own directory /etc/ndiswrapper/bcmwl5/ 

So to solve all your Broadcom woes just move bcmwl5.sys (I also moved bcmwl5.inf) to /etc/ndiswrapper

Reboot.

Wireless!!! Woohoo!!

I'll be here all week. Thankyou. Thankyou. Thankyou. Goodnight.

---

### Post by GabrielDunn on 2007-04-20
grendel@grendel-laptop:~$ ndiswrapper -l
bcmwl5 : invalid driver!
grendel@grendel-laptop:~$ 

So what now?  Its the right windows driver....?  

I upgrade to this from Edgy hoping for wireless support...now I still have to dual boot.  I want to kick windows all together...please save me!!!

---

