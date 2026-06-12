---
title: "Editing GRUB"
date: 2010-02-12
forum: New to Ubuntu
---

### Post by QazLeo on 2010-02-12
I wanted to edit the grub menu.
But nothing shown in gedit when i typed the command in terminal:
sudo gedit /boot/grub/menu.lst

---

### Post by Satoru-san on 2010-02-12
you need to edit [I]/etc/default/grub instead.

[/I]```
gksudo gedit /etc/defualt/grub
sudo update-grub
```

---

### Post by mcduck on 2010-02-12
If you are using Ubuntu 9.10 that file doesnt exist any more.

Basic Grub configuration is done in /etc/default/grub, and more detailed stuff about menu entries etc. are in /etc/grub.d/ directory.

---

### Post by stoogiebuncho on 2010-02-12
As mcduck said, there are now two locations to edit the grub menu.  /etc/default/grub (for configuration options), and /etc/grub.d/ (to add custom boot options).

This post explains very clearly how Grub 2 works and where all the configuration files are.  It's very well written and easy to understand.
[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

EDIT: Or if you could be a bit more specific about what you want to change in your grub menu, we may be able to help you here.

---

