---
title: "Xubuntu boots into Busybox"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by LinuxFox on 2009-04-08
I have a problem with my mother's computer.  When I tried to boot into Xubuntu, it took me to busybox, no matter what kernel I choose (pressing ESC before starting).  Before that, the computer was shut down, and now I'm stuck at this screen.

Is there any way to start Xubuntu, and not busybox?  Is there a command I need to type.  Some help please.  If it helps, I installed it via Wubi, so she can switch between that and Windows.

---

### Post by Jose Catre-Vandis on 2009-04-08
Try editing the kernel line in grub when you boot up to remove "quiet" and "splash", you should then be able to see where things are breaking down.

---

### Post by LinuxFox on 2009-04-08
> **Jose Catre-Vandis said:**
> Try editing the kernel line in grub when you boot up to remove "quiet" and "splash", you should then be able to see where things are breaking down.Thanks, I did that and I got a message telling me to boot into Windows, run "chkdsk /r", restart into Windows, and then restart to resume installation.

Why would I need to resume installation if it's installed?  Would doing this fix my problem?

EDIT: I just did the said instructions, and now it's working like it should.

---

