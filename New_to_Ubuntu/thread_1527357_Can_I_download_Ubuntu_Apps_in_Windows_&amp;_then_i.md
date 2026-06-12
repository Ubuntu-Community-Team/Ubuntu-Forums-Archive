---
title: "Can I download Ubuntu Apps in Windows &amp; then install them in Ubuntu?"
date: 2010-07-09
forum: New to Ubuntu
---

### Post by t4nv1r on 2010-07-09
So i want to Download K3B in my ubuntu 9.04. but the total file is 200MB. my net speed is super slow, only 12KB/s . So i can i download K3B in Windows in my dad's office which has a fast internet connection and then copy that to ubuntu & install it here?

---

### Post by nothingspecial on 2010-07-09
Yes but you will need to download any dependencies too.

---

### Post by Paqman on 2010-07-09
> **nothingspecial said:**
> Yes but you will need to download any dependencies too.

Which means that in practical terms it's likely to be a huge pain to do.

K3B shouldn't be 200MB unless you're running Gnome and it's pulling in tons of KDE dependencies. Picking a Gnome app will result in a much smaller download and faster start times.

---

### Post by t4nv1r on 2010-07-09
Where can i Download the dependencies from?

---

### Post by t4nv1r on 2010-07-09
> **Paqman said:**
> Which means that in practical terms it's likely to be a huge pain to do.

K3B shouldn't be 200MB unless you're running Gnome and it's pulling in tons of KDE dependencies. Picking a Gnome app will result in a much smaller download and faster start times.
yup im running Gnome. i mean the app is only 12MB but all da dependencies total it to 200MB. the default DVD burner in ubunu 9.04 is so slow. thats why i wanted to use K3B. so is there any good gnome-based DVD burners ?

---

### Post by philinux on 2010-07-09
Give gnomebaker a go. I prefer k3b myself but try it anyway.

---

### Post by nothingspecial on 2010-07-09
To get a list of dependencies you type

```
apt-cache showpkg k3b
```

You download them from here

[http://packages.ubuntu.com/lucid/](http://packages.ubuntu.com/lucid/)

Paqman is right, this will be a royal pain in the butt, but if you do go ahead, you wont know what order to install them in, so put them all in one place, and type ```
sudo dpkg -i *.deb
```

And (hopefully) dpkg will sort it out for you.

I`d try something else though.

---

### Post by robert shearer on 2010-07-09
Use Keryx and it will take care of all the dependencies for you ;)

[http://keryxproject.org/](http://keryxproject.org/)


> Keryx is a portable, cross-platform package manager for APT-based (Ubuntu, Debian) systems. It provides a graphical interface for gathering updates, packages, and dependencies for offline computers. Keryx is free and open source. 

---

### Post by Bachstelze on 2010-07-09
Download the Kubuntu Alternate CD. It has everything you need to install K3B from the CD.

---

### Post by Paqman on 2010-07-09
> **Bachstelze said:**
> Download the Kubuntu Alternate CD. It has everything you need to install K3B from the CD.

Er, it'll also be 700MB instead of 200MB! 

I'd definitely try the Gnome alternatives first. You might find that switching to a different app doesn't really make it any quicker than Brasero, so if K3B isn't going to be much quicker then it might not be worth the hassle.

---

### Post by cong06 on 2010-07-09
> **robert shearer said:**
> Use Keryx and it will take care of all the dependencies for you ;)

[http://keryxproject.org/](http://keryxproject.org/)

I would also recommend you try keryx.

---

### Post by d3v1150m471c on 2010-07-09
imgburn works in wine btw

---

