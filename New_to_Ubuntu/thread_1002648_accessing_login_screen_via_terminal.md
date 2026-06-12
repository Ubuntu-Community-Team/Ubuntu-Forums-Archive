---
title: "accessing login screen via terminal"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by gzav on 2008-12-05
I've got a big problem:

i tried to install Wine on my xubuntu 8.10 (on a usb stick), but got a crash report and nothing worked. So i uninstalled it but then my xfce panel on top got all messed up. So i decide to logout and remove the xfce config folder. Problem is, when i click on the quit button, it does nothing... 

I can't logout and i can't shut off my comp without pressing the power button. So my question is: can i go to the login screen via a command in the terminal? Or alternatively, is there a way i can boot xubuntu and arrive at the login screen instead of arriving directly on my session?

Thanks a lot for any info!

---

### Post by stefangr1 on 2008-12-05
> **gzav said:**
> I've got a big problem:

i tried to install Wine on my xubuntu 8.10 (on a usb stick), but got a crash report and nothing worked. So i uninstalled it but then my xfce panel on top got all messed up. So i decide to logout and remove the xfce config folder. Problem is, when i click on the quit button, it does nothing... 

I can't logout and i can't shut off my comp without pressing the power button. So my question is: can i go to the login screen via a command in the terminal? Or alternatively, is there a way i can boot xubuntu and arrive at the login screen instead of arriving directly on my session?

Thanks a lot for any info!

I'm not sore what you mean... However, you can always shutdown by going to a terminal Ctrl+Alt+F1 and then type "sudo init 0" to shutdown.

---

### Post by gzav on 2008-12-05
and how do i only log out?

---

### Post by glennric on 2008-12-05
Have you tried Ctrl-Alt-Backspace to zap the xserver?  This should restart the xserver and bring you back to the login screen.  If that doesn't work you could go to a console (with Ctrl-Alt-F1) and type
```
sudo /etc/init.d/gdm restart
```

---

