---
title: "Edit file advice"
date: 2010-11-27
forum: New to Ubuntu
---

### Post by nnjond on 2010-11-27
Hi,

I need to add 

rootdelay=130 permanently to a file for my os to load, but i can't remember which file or how to edit. 

Can you remind me please?

---

### Post by unknownPoster on 2010-11-28
I'm fairly certain you're going to want to edit the file found at this path:

[FONT=monospace]```

/boot/grub/menu.lst

```

You should open that file with any editor with root permissions. The following would work:

```

sudo vim /boot/grub/menu.lst

```

If you don't have vim or don't know how to use it, you can use any editor of your choice.

You'll probably want to add "[/FONT]rootdelay=130" to the end of the "kernel" line of whichever kernel you are using.

---

### Post by plucky on 2010-11-28
> **nnjond said:**
> Hi,

I need to add 

rootdelay=130 permanently to a file for my os to load, but i can't remember which file or how to edit. 

Can you remind me please?

What version of Ubuntu are you using?

If you are using GRUB2 then the file is **/etc/default/grub**

Good Luck

---

### Post by aeiah on 2010-11-28
edit it with nano if you don't know how to use vim. vim'll be the weirdest thing you've ever tried to use if you dont know what you're doing.

```
sudo nano /etc/default/grub
```

crtl+x to save and exit (hit y to confirm)

then ```
sudo update-grub
```

---

### Post by nnjond on 2010-11-28
Thanks for your help.

/etc/default/grub doesen't resemble the same page I get when I hit "e" at boot, so I'm not sure where to add my edit

---

### Post by plucky on 2010-11-28
> **nnjond said:**
> Thanks for your help.

/etc/default/grub doesen't resemble the same page I get when I hit "e" at boot, so I'm not sure where to add my edit

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash rootdelay=130"
```

Then run ```
sudo update-grub
``` to add it to the grub.cfg file.

See [Grub2 Basics](http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2)

Good Luck

---

