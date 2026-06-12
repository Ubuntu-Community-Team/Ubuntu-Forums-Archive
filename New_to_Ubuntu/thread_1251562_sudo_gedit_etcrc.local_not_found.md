---
title: "sudo gedit /etc/rc.local not found"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by Knepp on 2009-08-27
Im trying to use the command "sudo gedit /etc/rc.local" in Terminal but I'm "sudo gedit: command not found. What do I need to do to fix this? 

   ... I need to fix this so I can follow this tut [http://ubuntuforums.org/showthread.php?t=508145&highlight=xbox+360](http://ubuntuforums.org/showthread.php?t=508145&highlight=xbox+360)
Thnx!

---

### Post by credobyte on 2009-08-27
KDE ( Kubuntu ):
```
sudo kate /etc/rc.local
```Gnome ( Ubuntu ):
```
sudo gedit /etc/rc.local
```

Solution, no matter which UI you are using:
```
sudo apt-get install gedit && sudo gedit /etc/rc.local
```

---

### Post by drs305 on 2009-08-27
And please use "gksudo" or "gksu" if using graphical apps.

See the Graphical Sudo section:
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by Knepp on 2009-08-27
Oh I see thanks!

---

