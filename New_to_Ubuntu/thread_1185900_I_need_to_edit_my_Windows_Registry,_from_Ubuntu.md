---
title: "I need to edit my Windows Registry, from Ubuntu?"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by JoshAspire on 2009-06-12
I had some major nerd ego going on with my PC, and well-I went too far with the registry. I **disabled my keyboard & mouse** and I was hoping that some fellow Ubuntu hero could suggest me a way to [COLOR=red]edit my Windows registry[/COLOR].
And I'm trying to install a Ubuntu OS on a CD-rom so then I can access the desktop.
(I'm currently on my notebook.)
All love goes out to other folks.
What exactly did I do with the registry? I edited the currentcontrolset. Yep, stupid.
(system restore doesn't show up when I press F8)
..one step closer to fully-ubunutizing.
 
P.S. I know where to go once I get access to it.

---

### Post by albinootje on 2009-06-12
> **JoshAspire said:**
> I went too far with the registry.

Create a customized ubcd on some other machine elsewhere, and use that cdrom to try to fix your MS-Windows installation.
[http://www.ubcd4win.com/howto.htm](http://www.ubcd4win.com/howto.htm)

Good luck! And enjoy Ubuntu! :)

---

### Post by JoshAspire on 2009-06-12
> And I'm trying to install a Ubuntu OS on a CD-rom so then I can access the desktop.
(I'm currently on my notebook.)

Well I just finished an .iso file download on my notebook.
I know there's plenty of guides of getting ubuntu on a cd/dvd but I need to know how to edit my _registry_.

---

### Post by lkraemer on 2009-06-13
Windows automatically makes restore points at times when it
boots up.  Why not try booting into SAFE Mode and try to 
restore the registry to a time and date before it was changed.
It should work if you can get it to boot into Safe Mode.
If it boots into Safe mode and appears to work, I'd try to
boot into Normal mode, then restore the Registry to an earlier
date & time before the modification. And if it won't boot,
keep trying because after x tries it will do it automatically,
so I am told! ( think x is 10 maybe)

lkraemer

---

