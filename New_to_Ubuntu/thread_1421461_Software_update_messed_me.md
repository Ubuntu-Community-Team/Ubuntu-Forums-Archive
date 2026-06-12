---
title: "Software update messed me?"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by webmeist on 2010-03-04
Hi all.
Been running Ubuntu 9.1 for a few months now, and ran all software updates when prompted. I think i've installed maybe 6 or 7 updates to the kernel, as when i previously would boot there were that many choices to boot into.
 
Haven't had any problems, yet. But when i installed updates today, when restarted the machine, came up with:
 
Gnu Grup version 1.97~beta 4,
and sh:grub>
where it stops.
 
I type exit and it says no OS found,
and exit again and it goes to the dual boot with Vista
thats been on here since before I installed Ubuntu.
 
Can someone tell me what to type at grub to
get back into Ubuntu so I can either boot into
an older image of the Ubuntu,
and delete the recent upgrade?
 
Thanks so much.
 
webmeist

---

### Post by ptrinder64 on 2010-03-04
Hiya,

I've not personally had this problem, but have Googled it and it appears to be around wubi installs - does that sound right?

The link below suggests a way to fix this - I hope this helps:

[http://www.omaregan.com/?p=583]("http://www.omaregan.com/?p=583")

I would ordinarily provide you with my most recent kernel version number but as I'm at work and on a Windows PC...

Hope you fix it.

---

### Post by philinux on 2010-03-04
@webmeist, if this is a standard dual boot and **not a wubi install** then follow the instructions below, otherwise follow post #2.

Sounds like grub2 is messed up. Follow the instructions in the link.

Ignore the fact it's about windows borking grub. 9.10 uses grub2 so this is the new way to recover from a grub2 mess.

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

---

