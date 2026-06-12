---
title: "How to install Studio onto an external HDD"
date: 2010-12-30
forum: New to Ubuntu
---

### Post by RichieB07 on 2010-12-30
So my roommate got curious with my Ubuntu partition and now wants to install Ubuntu Studio, but he wants it on an external.  I have been trying to find a guide to this and just can not, no idea why.

So it is as easy as telling Ubuntu Studio to install to the External when it's plugged in or is there more to it?  I have no idea honestly as I've never tried to install an OS to an external HDD.

Thanks for any help!

---

### Post by cchhrriiss121212 on 2010-12-31
It should be just the same as a regular HD. Some tips:
Disconnect his main HD during installation which will prevent any GRUB confusion, he can use BIOS to select which HD to boot from
Studio uses a text based installer and has no live mode, so try out his hardware with a regular Ubuntu CD first
Studio has no network manager, meaning wireless won't work out of the box

---

### Post by RichieB07 on 2010-12-31
> **cchhrriiss121212 said:**
> It should be just the same as a regular HD. Some tips:
Disconnect his main HD during installation which will prevent any GRUB confusion, he can use BIOS to select which HD to boot from
Studio uses a text based installer and has no live mode, so try out his hardware with a regular Ubuntu CD first
Studio has no network manager, meaning wireless won't work out of the box

We tried the 10.04 CD first, and it worked well, except his built-in wifi doesn't work so he has to use an adaptor.  If there is no network manager, can we just out WINE on there, get the driver for the adaptor, run it, and have the adaptor work?

I know this sounds very noobish, but I've never dealt with Studio before.

---

### Post by cchhrriiss121212 on 2010-12-31
> If there is no network manager, can we just out WINE on there, get the driver for the adaptor, run it, and have the adaptor work?
No, all you need to do is install gnome network manager with a wired connection or manually from the packages on the DVD image. The network manager is left out for a reason, it interrupts audio processes, so if your friend wants to do audio work keep that in mind.

What I would recommend is that you just install regular 10.04, then add the studio meta-package which you will find in software center. Chances are he won't even want all the packages in there, so you can just download them individually, they are all in the repos.

If you tell me what your friend wants to use studio for, I can recommend the best FOSS programs for the job. Some are not all that easy to use.

---

### Post by RichieB07 on 2010-12-31
> **cchhrriiss121212 said:**
> No, all you need to do is install gnome network manager with a wired connection or manually from the packages on the DVD image. The network manager is left out for a reason, it interrupts audio processes, so if your friend wants to do audio work keep that in mind.

What I would recommend is that you just install regular 10.04, then add the studio meta-package which you will find in software center. Chances are he won't even want all the packages in there, so you can just download them individually, they are all in the repos.

If you tell me what your friend wants to use studio for, I can recommend the best FOSS programs for the job. Some are not all that easy to use.

As of right now I've been trying to get his adaptor to work and the OS won't even boot up any more so I'm going to put 10.04 on it and then install what he wants on it.

All I know is that he really just wants to mess around with the stuff.  I have a MIDI keyboard and he wants to hook that up to it to see what it can do, along with maybe the drum programs and such.  It's nothing too serious, just messing with it.

---

