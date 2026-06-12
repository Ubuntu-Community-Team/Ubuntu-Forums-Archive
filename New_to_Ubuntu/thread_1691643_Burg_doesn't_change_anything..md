---
title: "Burg doesn't change anything."
date: 2011-02-20
forum: New to Ubuntu
---

### Post by Mr. ViC on 2011-02-20
Hi.

So today I installed Burg.

I first installed BUC from Synaptic, and then burg-manager from Synaptic again

Followed a little tutorial to get started, did the install on /dev/sda/, message poped up with "Operation sucessful", choosen a theme, double clicked it, restarted and the grub is still the same.

I have Windows and Ubuntu installed here, Ubuntu is the primary one (obviously).

Any ideas guys?

Thanks in advance.

---

### Post by Mr. ViC on 2011-02-20
Bumping.

---

### Post by Mr. ViC on 2011-02-21
One final bump...

---

### Post by slooksterpsv on 2011-02-21
Did you run:

gksudo update-burg

?

---

### Post by Mr. ViC on 2011-02-21
Thanks for your reply.

Ran it, the output is this:

```
/home/purity/.themes/MetalLex/gtk-2.0/panel.rc:319: Unable to locate image file in pixmap_path: "/Shadows/entry-shadow-in.png"
/home/purity/.themes/MetalLex/gtk-2.0/panel.rc:322: Background image options specified without filename
/home/purity/.themes/MetalLex/gtk-2.0/gtkrc:96: Murrine configuration option "gradients" is no longer supported and will be ignored.
```Btw, that "MetalLex" is the theme I am currently using.

Rebooted, and the grub is still the same.

I heard of some incompatibility of Burg with Grub2? But the version I'm using seems to be 1.98.

On my desktop PC, tried to downgrade to the legacy grub, and does not work also, but well, if I get burg to work on my laptop at least, I'm already happy enough.

Thank you.

---

### Post by Mr. ViC on 2011-02-21
Well, sorry for bumping, but it's just to say I finally got it working.

Followed this tutorial, and is working great:

```
http://www.omgubuntu.co.uk/2010/06/get-animated-themed-icon-only-grub-menu-using-burg-now-simple-to-use/
```

Just in case someone ever has the same problem I had.

And even "bought a beer" to the people from Burg Project :P

Thanks guys.

---

