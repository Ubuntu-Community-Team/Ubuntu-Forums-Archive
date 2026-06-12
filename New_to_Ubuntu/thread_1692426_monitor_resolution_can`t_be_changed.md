---
title: "monitor resolution can`t be changed"
date: 2011-02-21
forum: New to Ubuntu
---

### Post by vik.gelin on 2011-02-21
i am facing problem with monitor resolution.currently it is 600x400 and there is one more option in the display menu of preferences and that is is of 600x350.i am not able to see any window completely and facing problems.recently i changed my motherboard and i have "P4M800-M7 V:1.0 " BY ELITE GROUP. previously i had a gigabyte motherboard.plz help. is there is a way out to increase the resolution

---

### Post by cariboo on 2011-02-21
Check synaptic to see if you have unichrome/opencrome installed, if you do, you may need to create an /etc/X11/xorg.conf file. To do so press Ctrl-Alt-F1, once atthe console type:

```
sudo /etc/init.d/gdm stop
```

the above command will stop the gnome desktop manager. Next type:

```
Xorg -configure
```

this will create an xorg.conf file in your home directory, copy the new xorg.conf file to /etc/X11:

```
cp xorg* /etc/X11/xorg.conf
```

Restart gdm:

```
sudo /etc/init.d/gdm start
```

you should be taken back to your desktop, where you should be able to adjust your resolution.

---

