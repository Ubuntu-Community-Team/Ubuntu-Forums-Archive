---
title: "Ubuntu keeps rebooting"
date: 2010-06-22
forum: New to Ubuntu
---

### Post by Ububtubobl on 2010-06-22
I have started to get the message
"Install problem. Configuration for Gnome power management has been installed incorrectly. Consult system administrator. " 
Any ideas how to repair this. System continues to reboot even in safe mode.
Thanks

---

### Post by cariboo on 2010-06-22
Open a terminal and try:

```
sudo dpkg-reconfigure gnome-power-manager
```

to see if that solves the problem.

---

### Post by Ububtubobl on 2010-06-24
> **cariboo907 said:**
> Open a terminal and try:

```
sudo dpkg-reconfigure gnome-power-manager
```to see if that solves the problem.



Thanks for the input. I booted from a live cd, opened terminal and entered that command.
No change. Can't get to terminal at boot from hard drive.

---

### Post by Diabolis on 2010-06-24
Can you get to the login screen? If so, press **Ctrl + Alt + F1** that'll give you a terminal (a TTY) from where you can reconfigure/uninstall/install gnome-power-manager.

---

### Post by Ububtubobl on 2010-06-24
> **Diabolis said:**
> Can you get to the login screen? If so, press **Ctrl + Alt + F1** that'll give you a terminal (a TTY) from where you can reconfigure/uninstall/install gnome-power-manager.


Thank you. Terminal now tells me that gnome power manager is not installed. So I tried "sudo install gnome-power-manager". Did not work. Any more suggestions?

---

### Post by Diabolis on 2010-06-24
Its:
```
sudo apt-get install gnome-power-manager
```

---

### Post by Ububtubobl on 2010-06-28
Thanks to all for their help. It.s working once again.  Now I have to figure out how just starting G Parted on live cd can do this.

---

### Post by Rhenthalin on 2010-07-26
Hi, I hate to dig up a dead horse, but I'm having the same error message appear on my distro of Ubunutu 10..... I've tried the commands given earlier. I've tried uninstalling and reinstalling gnome-power-manager and still it gives me this error and insists that I contact myself in order to fix it. Are there any other solutions? or should I just back up what I can and nuke it.

---

