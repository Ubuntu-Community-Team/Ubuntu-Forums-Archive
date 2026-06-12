---
title: "Missing Operating System?"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by Legeril on 2010-10-24
I am currently running on my Live USB, I have installed 10.04 twice now since the move to Ubuntu and am about to install for a 3rd time. 

Basically I close down my laptop and everything is running fine, but when I turn it back on I get "Missing Operating System" flashing at me, what is happening to my installations? I'm assuming it's not a virus or anything, is it some failure in the way I am installing Ubuntu?

Help and advice greatly needed, I love Ubuntu but the fact that this has happened twice in a month is starting to get irritating...

---

### Post by arochester on 2010-10-24
Have you changed the BIOS to boot from USB first, or have  you just changed the boot order? The first is a permanent fix, but the second is temporary.

---

### Post by Verbeck on 2010-10-24
try this : check the boot priority in bios and move the harddisk to the top if you have to. or remove any cd/flash drive from the laptop, then start up

---

### Post by Legeril on 2010-10-24
I should clarify, I'm having this problem on my laptop hardware. I'm not trying to install Linux on a USB, I'm just running from Live USB to access these forums. As Grub won't load my OS, I'm not dual boot or anything either Ubuntu is my only installation.

I should also note from my USB I can access the partition with everything looking to be intact, so I can't work out what the problem is.. =/

---

### Post by Legeril on 2010-10-24
> **Verbeck said:**
> try this : check the boot priority in bios and move the harddisk to the top if you have to. or remove any cd/flash drive from the laptop, then start up

I feel like an idiot, I had a blank USB Drive in a port and it was first in the boot order. 

Wow am I embarrassed :(

*Thread being marked as solved, thanks guys

---

