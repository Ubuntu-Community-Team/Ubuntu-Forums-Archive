---
title: "registry editore"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by kimikrishna on 2009-02-15
is there any regedit in ubuntu ,like in windows ?

---

### Post by Bradtek on 2009-02-15
There is no registry to edit

---

### Post by kavon89 on 2009-02-15
Linux does not use that awful registry system that Windows does.


If you mean Wine's registry (the compatibility layer so you can run Windows applications), just execute this command in the Terminal:

```
wine regedit
```

---

### Post by kimikrishna on 2009-02-16
i dont know more about windows registry thing..

but isnt registry necessary for runing softwares  ?

how do linux manage withut registry entryes ?

---

### Post by durand on 2009-02-16
The registry is just for windows programs. These won't work in ubuntu unless you use some sort of emulation like wine.
```
sudo aptitude install wine
``` in a terminal (Applications > Accessories > Terminal)

In ubuntu, there is some sort of registry called GConf but this is only for specific programs. You can see it by running gconf-editor in a terminal however, there is no point when you're just a beginner to ubuntu.

---

### Post by spcwingo on 2009-02-16
If you mean that you would like to edit system settings (if on Gnome) you can install gconf-editor.

```
sudo apt-get install gconf-editor
```

But, as the others have stated, Ubuntu doesn't have a registry.

---

### Post by djbushido on 2009-02-16
NOTE: if you don't know what you're doing with gconf-editor, don't do it. You run the risk of breaking your system. High risk. As stated, Linux programs don't have a registry. All the registry does in Windows is create entries to regulate how certain programs handle certain instances. Since this is mainly because of copyright (intellectual property) issues, Linux doesn't run into this necessity as it isn't run by a corporation.
So in summary, you don't technically need a registry. If you need to edit the registry for windows programs through wine, use the wine regedit. If you need to change system settings, use gconf-editor, although if you don't know what you want to do, don't turn on gconf-editor.

---

### Post by Perfect Storm on 2009-02-16
I wouldn't call gconf a registry, more like hidden options for the apps you install.

---

