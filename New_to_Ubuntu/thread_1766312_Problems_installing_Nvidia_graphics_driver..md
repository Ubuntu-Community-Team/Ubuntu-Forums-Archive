---
title: "Problems installing Nvidia graphics driver."
date: 2011-05-24
forum: New to Ubuntu
---

### Post by v.john.isaac on 2011-05-24
Hey, i recently installed Ubuntu 10.10. And it was fun untill i tried installing the Nvidia driver. After downloading the driver it asked me to reboot the system to complete the installation. I lost my X display. And i switched back to windows 7. So can anyone guide me in total noob lines, to avoid this problem the next time i install the driver. Cos i dont feel like using windows anymore.:confused:

---

### Post by Locke_99GS on 2011-05-24
We need more information.

By what method did you install the nVidia drivers? Did you install them from the Ubuntu repos, or from nVidia's site?

If you still have your Linux install, boot to it and when X fails to load, login at the command line. (If you don't get a command line, hit Ctrl+Alt+F1 to switch to VT1, then login - alternatively, boot to a recovery kernel and select a command line boot) Then give us the output of these four commands:
```

lspci |grep VGA

cat /var/log/Xorg.0.log

dkms status

cat /etc/X11/xorg.conf

```

---

### Post by v.john.isaac on 2011-05-25
Thanks for the reply [Locke_99GS]("http://ubuntuforums.org/member.php?u=543645"). Well  my noob *** freaked out and re installed ubuntu. So i have a dell  XPS 15 L501X with the Nvidia geforece GT420M graphics card. The last time i installed the driver from System>Administration>Additional drivers.  So can u please help install them in the right way this time, cos i understand the process can be a real bitch. Thank u.

---

