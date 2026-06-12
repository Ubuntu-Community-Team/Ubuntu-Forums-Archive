---
title: "ndiswrapper - driver present, hardware not found"
date: 2006-08-31
forum: Networking &amp; Wireless
---

### Post by keiichi42 on 2006-08-31
I'm using ubuntu 6.06 and trying to get my DWL-650 revP to work.  I successfully installed ndiswrapper and the correct XP driver, but using ndiswrapper -l only lists that the driver is present, the hardware is not detected by ndiswrapper.

In device manager the card is detected on the pci bus and listed properly.  Also the non-wireless pc-card I have installed directly below the dwl-650 is recognized and works fine.

Can anyone please help me figure out why the card is not being recognized as installed by ndiswrapper?  I've only installed linux a few days ago so I'm quite new to it, but I understand enough to get around the terminal and synaptic.  Thanks!

---

### Post by Titus A Duxass on 2006-08-31
Try disabling your non-wireless interface (eth0) through BIOS.

---

### Post by keiichi42 on 2006-08-31
eth0 is a wired pcmcia card, I disconnected it, but it doesn't cause any changes in the ndiswrapper output.

I assume it has to say "driver present, hardware present" before you can load the module with modprobe?

---

### Post by keiichi42 on 2006-08-31
Ok so I was searching on google and read that not finding the hardware probably means I have the wrong driver.  I got the exact driver for my revision from d-link's site for my card, so I see no reason why it shouldn't be seeing the card.

I'll try an older version of the driver for my card and report back.

---

### Post by ser1alsn1per on 2006-08-31
hi there i have been tring for ages to get stuff like this working ie putting my rooter to open for easyness but as soon as i put a web key on it and put the wep key in ubuntu it just worked

---

### Post by keiichi42 on 2006-09-01
I'm a little confused by what you mean...

Should I just force the module to load on boot?  If it doesn't see the hardware will it let me put my wep key in and then start working?
Please elaborate!

---

### Post by kdog on 2006-09-01
Could it be, that there is a different driver loaded, that is conflicting with the ndiswrapper?

On my Netgear WG511 v3 china, that was the case and I had to blacklist the prism54 drivers.

Ken

---

### Post by mhimlin on 2006-09-17
I am in the same boat with the same card, dwl-650 rev p.  I tried the win xp, 2000, 98 and ME drivers and ndiswrapper -l has never shown hardware present.  Any luck getting this working?

---

### Post by sanjeevan on 2008-04-28
so no solution to this problem? i downloaded the driver from link on ndiswrapper site.

---

### Post by bagelong on 2008-04-29
I had basically the same issue and finally reverted back to 7.10 and got it working with ndiswrapper.  Not sure what it was, but something in 8.04 would not let the driver and device link up.

---

