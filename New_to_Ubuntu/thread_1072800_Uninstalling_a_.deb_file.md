---
title: "Uninstalling a .deb file"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by sdim on 2009-02-17
Hi,everyone.
Installed a file called _nautilus-play-mplayer_0.1.1-1_all.deb_,which I would like to uninstall.
I give "sudo dpkg -r package_name",but it says it can't do it saying "dpkg - warning: ignoring request to remove nautilus-play-mplayer_0.1.1-1 which isn't installed".

Any ideas?
Thank you.

---

### Post by era86 on 2009-02-17
Have you tried finding it using the Synaptic Package Manager GUI?

---

### Post by Limerick on 2009-02-17
What's the error output?

---

### Post by sdim on 2009-02-17
Yes,but didn't find it by any such name.
Just posted the output error in the first message.
Thank you.

---

### Post by sdim on 2009-02-17
The description said it would play a video file by right-clicking on it,and presenting the option "play with mplayer",which is not there,even though the package was installed correctly.

---

### Post by Kain000 on 2009-02-17
you could try 

```
Sudo aptitude purge nautilus-play-mplayer
```

this will remove all conf files and the installed package or

you could use the remove operand if you wish but this will only leave the config files on you system and you dont need that clutter.

---

### Post by snova on 2009-02-17
> **sdim said:**
> Hi,everyone.
Installed a file called _nautilus-play-mplayer_0.1.1-1_all.deb_,which I would like to uninstall.
I give "sudo dpkg -r package_name",but it says it can't do it saying "dpkg - warning: ignoring request to remove nautilus-play-mplayer_0.1.1-1 which isn't installed".

Any ideas?
Thank you.

As can be inferred from the above post, that is not the package name. It's only **nautilus-play-mplayer**; the rest of the filename is versioning information and architecture.

---

### Post by sdim on 2009-02-17
Many thanks to all of you.
snova,you were right.It only needed the name of the file,not the version number.

---

