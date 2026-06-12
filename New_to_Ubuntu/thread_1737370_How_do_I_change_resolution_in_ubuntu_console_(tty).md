---
title: "How do I change resolution in ubuntu console (tty)?"
date: 2011-04-23
forum: New to Ubuntu
---

### Post by Nyromith on 2011-04-23
The default resolution is 80x30, and it's a bit difficult to read when a lot of text is displayed because I have a widescreen. How do I change it to a standard 80x25 or 80x24?

Thanks.

---

### Post by ESDEEM on 2011-04-23
Have you tried....
System=>Preferences=>Monitors ( or Display)

---

### Post by Joe of loath on 2011-04-23
Doesn't work in tty

OP, you'll have to do it via GRUB. [https://wiki.archlinux.org/index.php/GRUB2#Setting_the_framebuffer_resolution](https://wiki.archlinux.org/index.php/GRUB2#Setting_the_framebuffer_resolution)

---

### Post by Nyromith on 2011-04-23
Didn't work for me. I modified the '/etc/default/grub' file like it was described in the linked page (and many other pages about grub2, frame buffers, etc...), tried various resolutions, but absolutely no effect. And yes, I ran 'update-grub'.

The change of the resolution occurs after some time during the boot, not immediately  after selecting the OS, so I suspect that grub is not responsible for that.

---

### Post by jmcboots on 2011-05-04
did you run update-grub, or update-grub2.

It makes a difference.

---

