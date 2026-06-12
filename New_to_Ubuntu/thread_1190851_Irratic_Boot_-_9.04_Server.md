---
title: "Irratic Boot - 9.04 Server"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by Ian-on-the-Trent on 2009-06-18
Hello.

I have an old HP Pavilion laptop (Celeron 900mhz) with a broken screen. I decided to try using it as an energy efficient Home Lan server.

I swapped in a newish 120GB HDD, added RAM (total now 512mb-complete overkill), installed 9.04, upgraded packages, installed Webmin, and away I went. Or so I thought. 

When I reboot I usually need to do it 3 or 4 times as I get a "Operating system not found" message. No GRUB loading message....nada.  Although this may be completely random, I find that if I put the install CD into the drive and recycle the power after the Live CD boots to the first screen, then remove the CD and reboot, GRUB eventually loads.

Very, very strange.  Does anyone have any idea what the heck is going on?  

(When its working it does so like a charm. I'm very impressed.  I have the power plugged into a "Kilometer" and it is showing 12 watts when idle and 19-21watts when its churning away.)

---

### Post by Trebaruna on 2009-06-18
If there's no GRUB message whatsoever I'd suggest the BIOS cannot find the bootloader to begin with. Have you tried fiddling with the settings there? Try changing boot order, hard driver order (likely not applicable on a laptop) or anything related to boot options.

---

### Post by Cheesemill on 2009-06-18
Could well be a failing hard drive.

---

### Post by Ian-on-the-Trent on 2009-06-18
Thanks for replying.

I thought about the HDD dying but there were no issues with the preinstall tests I ran on it. SMART drive is enabled and everything seems cool. The drive is virtually new.

I have changed the boot order with no luck. I can't access the BIOS since it is password encrypted (there is a separate function to allow boot order changes without going into the main BIOS).  Since this was a "if you can get it going you can have it" laptop, the previous owner has long since forgotten the password.

---

### Post by jimmy the saint on 2009-06-18
See if you can attach a monitor to it and see what the screen output is.  I bought a Dell Vostro 200 (a terrible machine in my opinion) that requires the IRQPOLL boot option, and I only discovered that after attaching a monitor to the server.  A helpful "may require irqpoll boot option" or something to that effect message was included in the 30+ minute boot sequence.  With the option, it boots properly every other time (can't figure that out).  Since it is mostly a server, but is also used for playing movies on my tv, I live with it for now, but once I can pick up a suitable front-end machine, I will throw Arch on it and see if that helps.

Edit:  To reset the bios password you should simply be able to remove the cmos battery for a half an hour.  Search google for a repair manual for your laptop and tear down instructions should help you take it apart far enough to access the battery.  Research first as each laptop is different and randomly taking things apart can cause headaches.  I believe the battery on most HP laptops is directly under the keyboard, but once again, each laptop is different.

---

### Post by Ian-on-the-Trent on 2009-06-18
> **jimmy the saint said:**
> See if you can attach a monitor to it and see what the screen output is...A helpful "may require irqpoll boot option" or something to that effect message was included in the 30+ minute boot sequence.  With the option, it boots properly every other time (can't figure that out)...

Edit:  To reset the bios password you should simply be able to remove the cmos battery for a half an hour.  


Yes, a monitor is attached when I work on the server.

Doh...yes, I'll remove the battery and that should clear out the CMOS.  

I've never heard of irqpoll.  I will check it out and report back.

---

### Post by Ian-on-the-Trent on 2009-06-19
*[COLOR="DarkRed"](How do I remove this post?)[/COLOR]*

---

### Post by Ian-on-the-Trent on 2009-06-19
HP Pavilion N5415 Laptop.

As per the suggestion of removing the battery to clear the CMOS and related password lock; well, it ain't so simple after all. 

I've downloaded a service manual and have disassembled the laptop to the motherboard. Surprisingly, the service manual states that problems with CMOS battery requires a motherboard replacement. What's with HP and their security concerns...further reading of the manual has all of these stipulations about resetting the password which only a service centre is permitted to do.

Anyway, I've found the CMOS battery on the underside of the motherboard. However, there is no quick release type clasp, the battery appears to be soldered in place.  A picture of this is shown below. The penny is there for scale.

[IMG]http://www.itsa.ca/pi/CMOS_Battery%20003.jpg[/IMG]

I've got my soldering iron heated up...I was thinking of delicately removing the batteries at the soldered connections (two similar silver blobs at 10 o'clock from the battery). However, I'm asking for suggestions/hindsight for what I am about to do.

---

