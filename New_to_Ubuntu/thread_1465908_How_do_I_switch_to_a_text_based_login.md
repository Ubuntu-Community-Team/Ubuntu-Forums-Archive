---
title: "How do I switch to a text based login?"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by Sup3r3g0 on 2010-04-29
Something similar to ctrl alt f1 and that kind of login prompt. If I do that will "startx" take me to my regular desktop? Thanks

**Update:**
Here's the solution from the provided link. 
> **komputes said:**
> I had a hard time because I was following guides that were not tested on 9.10. In fact you don't need to mess with GDM's configuration as GRUB2 is the easiest way to get this done. Here are the steps:

1 - Edit the GRUB2 configuration defaults

```
$ sudo gedit /etc/default/grub
```2 - Change the line **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"** to

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash text"
```3 - Save and close the grub file

4 - Update grub so that the changes are propagated to grub's configuration file (to all current and future kernels)

```
$ sudo update-grub
```That it! Simple right? :)

If you ever need to log into gnome, use the **startx** command. If you want GDM to start use the **sudo gdm start** command.

Hope this helps people from wasting hours of trying to disable GDM on 9.10 using older guides that suggest editing gdm.conf, moving gdm.conf, using update-rc.d, rcconf or sysv-rc-conf - none of those worked for me. This was the cleanest/best way I found of doing this.

Cheers!

:guitar:

---

### Post by limey_rick on 2010-04-29
I think you have to start the gnome display manager - if you are using GNOME. 

> sudo /etc/init.d/gdm start 

This will bring up the regular GNOME environment.

---

### Post by Sup3r3g0 on 2010-04-29
Ok, so if I use "startx" and /gdm start I'll get back to a regular Gnome desktop? So how do I get to a textbased login as the default?

---

### Post by limey_rick on 2010-04-29
See comment #38 on this thread:

[http://ubuntuforums.org/showthread.php?t=1305659&page=4](http://ubuntuforums.org/showthread.php?t=1305659&page=4)

---

### Post by Sup3r3g0 on 2010-04-29
Thanks! I quoted what you linked to I ever forget how to do it.

---

