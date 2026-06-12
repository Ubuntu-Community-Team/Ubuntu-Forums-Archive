---
title: "Suspend &amp; Hibernate Confusion"
date: 2011-03-28
forum: New to Ubuntu
---

### Post by Mr Stoozer on 2011-03-28
Hello all.
I'm a little confused with Ubuntu 10.10s suspend and hibernate operations and which one i should use (if at all).
I have 3GB Nanya PC2-6400 DDR2-SDRAM SO-DIM (400MHz) installed.
I have no dedicated swap space partition.
When i hit the hibernate option it seems the screen only locks. I've given the system time to write to disk before arousing and once it is, it instantly 'powers' on.  The disks don't spin, speakers & monitor still on, etc. Is this because i have no swap?

When i hit the suspend option, the disks spin down, monitor is off, speakers off (which has now evoked a strange popping noise every time i boot or mute the speakers) and everything seems as it should. However i cannot wake the system via hitting a key or moving the mouse. I have to use the power button. It's my understanding i should be able to wake the system via keys or mouse movement(?).
Finally, (and thanks for reading this far :) ) should i be using these power saving modes at all if i don't have swap space? Is 3GB 400Mz RAM sufficient? My system typically runs on around a 1GB load.
Thanks for any enlightenment!

---

### Post by fabricator4 on 2011-03-28
Hibernate writes the contents of RAM to the swap partition, therefore it won't work if you don't have a swap partition.  Have a look at [the swap FAQ]("https://help.ubuntu.com/community/SwapFaq").

To return from suspend or hibernate you have to push the power button as far as I know.

Chris

---

### Post by Mr Stoozer on 2011-03-29
So i'm ok to carry on using suspend?
How would one go about removing the hibernate option from the menu? (something that should have already been done IMO).

---

### Post by walt.smith1960 on 2011-03-30
Fabricator4 is dead on--no swap partition no hibernate.  As far as powering up via mouse or keyboard, that is a BIOS function.  On my desktop I can go into the BIOS screens and find enable/disable power up from keyboard/mouse/network etc. etc. I believe the keyboard needs a power button. I've not messed with them, just push the button.  Ubuntu boots fast enough that I don't see any real advantage to hibernate; I just use suspend or off.  My desktop machine seems to use about 5 watts-about the same as an incandescent nightlight- while suspended as near as I can measure.

---

### Post by Paqman on 2011-03-30
> **Mr Stoozer said:**
> So i'm ok to carry on using suspend?

Sure, sounds like it's working fine. In my experience waking from suspend only works for PS/2 mice and keyboards, but this may depend on your motherboard.

> 
How would one go about removing the hibernate option from the menu? (something that should have already been done IMO).

Er, good question. From a quick Google it looks like older versions of Gnome could disable this from an entry in gconf, but I don't know if this is still the case, and i'm not on a Linux machine right now.

---

### Post by Mr Stoozer on 2011-04-01
That clears things up a little. Thanks guys.

---

