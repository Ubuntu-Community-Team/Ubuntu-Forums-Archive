---
title: "System shutdown beep"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by C. M .Hughes on 2009-07-08
Hi all,
I recently tried to configure my usb headset with no success. As an unfortunate consequence I now have a beep on shutdown that I am unable to get rid of. I have tried the following

1. editing the preferences in Sounds
2. adding 

blacklist pcspkr

to

/etc/modprobe.d/blacklist.conf

If anyone has any ideas, I would be most grateful.

---

### Post by VCoolio on 2009-07-08
Blacklisting should have taken care of it I think, but here is another option that was successful for some people:

system > preferences > power management in the tab General under Extras check the box for no sound on errors.

---

### Post by C. M .Hughes on 2009-07-08
Thanks for the suggestion, but sadly it didn't fix the situation. 

Do you have any other ideas? The beep is really annoying!

---

### Post by mano cazalet on 2009-07-08
hmmmm maybe
[HTML]sudo rmmod pcspkr[/HTML]

or if you write alsamixer in terminal, is there any option for PC beep?

---

### Post by C. M .Hughes on 2009-07-08
THANK YOU!

I typed 

gnome-alsamixer

and muted the PC Beep

I still don't have my USB headphones working, but that will wait for another day.

Thanks again.

---

