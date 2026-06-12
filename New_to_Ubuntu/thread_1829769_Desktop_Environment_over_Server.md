---
title: "Desktop Environment over Server"
date: 2011-08-20
forum: New to Ubuntu
---

### Post by avnd on 2011-08-20
Hello!

I would like to have choice of variety in Desktop Environment for my Ubuntu. Can someone answer 2 questions for me?

1. Can I download Ubuntu (with the default Unity and GNOME environments) and then individually download the required desktop environment and have choice at login? If I do that will my applications menus be cluttered with the applications of both GNOME and the other environment, say, KDE?

2. To avoid the clutter, can I download the Ubuntu server edition, install it and then download whichever desktop environment I want? I mean, this would be nice if (correct me on the following if I'm wrong)
   a. It would actually avoid the clutter of applications
   b (More importantly) Is a Ubuntu Server with a desktop added later REALLY the same as a Desktop install (in the basic innards). Or is my concept something really stupid? (I'm a newbie so I'm not really ashamed ;))

Thanks!

Cheers!

P.S. I did read the arguments against installing a Desktop over a server at [https://help.ubuntu.com/community/ServerGUI]("https://help.ubuntu.com/community/ServerGUI")
But those are for a person intending to use it as a server, aren't they? I'm intending it to use as a Desktop PC. Thanks!

P.S (2) ;) : I would love to know if there is any other alternative to get what I want.

---

### Post by MG&amp;TL on 2011-08-20
Once you've installed the desktop, it's pretty much the same as a default install :)

You might want the minimal .iso, not the server, though:

[https://help.ubuntu.com/community/Installation/MinimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD")

Although I might be wrong.

---

### Post by avnd on 2011-08-22
Thanks for the link, mate. :)

---

### Post by skatinjj on 2011-08-22
I use minimal so I can avoid any clutter and using unnecessary disk space.

---

### Post by nothingspecial on 2011-08-22
If you install the minimal iso and then install one of the {ku,lu,xu,edu,u}buntu-desktop packages then you may as well install the full version because that is what you will get.

If you want to avoid applications you don't want, make sure you only install the desktop environment eg gnome-core or xfce4 etc

---

### Post by zeroseven0183 on 2011-08-22
Or you can probably create two partitions, one for Ubuntu (with Unity) and Kubuntu or any *buntu derivative you like (say Lubuntu or Xubuntu). You can also try them on a virtualized environment. Use Virtualbox for this purpose.

---

### Post by elliotn on 2011-08-22
> **zeroseven0183 said:**
> Or you can probably create two partitions, one for Ubuntu (with Unity) and Kubuntu or any *buntu derivative you like (say Lubuntu or Xubuntu). You can also try them on a virtualized environment. Use Virtualbox for this purpose.

I installed kde on Ubuntu and at login can choose which DE I want. I later removed gnome and unity but kept the gtk apps like brasero and also removed kde apps I don't like

---

### Post by sffvba[e0rt on 2011-08-22
As has been mentioned... If you install Ubuntu you will get Gnome (and if you are installing 11.04 you will get Unity and if you install 11.10 Unity and Gnome-shell).

If you install Kubuntu you will get KDE.

There is no cross-over in the applications for these two distro's by default... You can off course choose to change that afterwards by installing what you please on any of these platforms.


404

PS - In a default Slackware install the recommendation is to install everything available and remove later that which you don't want rather than starting small and growing from there...

---

### Post by cj13579 on 2011-08-22
If you already have your server and want the default ubuntu desktop but without lots of "fluffy" applications (OpenOffice, Evolution etc.) then you can run:

```
sudo apt-get install --without-recommends ubuntu-desktop
```


The traditional lightweight desktop (X) can be got by:

```
sudo apt-get install xubuntu-desktop
```

---

### Post by skatinjj on 2011-08-23
> **nothingspecial said:**
> If you install the minimal iso and then install one of the {ku,lu,xu,edu,u}buntu-desktop packages then you may as well install the full version because that is what you will get.

If you want to avoid applications you don't want, make sure you only install the desktop environment eg gnome-core or xfce4 etc

I don't install a DE during install.  I usually grab fluxbox after a while.

I prefer TTY unless I actually need a DE.  I even use elinks as much as I can.  Everything for me is just so much faster and easier to handle =)

---

### Post by oldos2er on 2011-08-24
> **avnd said:**
> 
   b (More importantly) Is a Ubuntu Server with a desktop added later REALLY the same as a Desktop install (in the basic innards). Or is my concept something really stupid? (I'm a newbie so I'm not really ashamed ;))

P.S. I did read the arguments against installing a Desktop over a server at [https://help.ubuntu.com/community/ServerGUI]("https://help.ubuntu.com/community/ServerGUI")
But those are for a person intending to use it as a server, aren't they? I'm intending it to use as a Desktop PC. Thanks!

P.S (2) ;) : I would love to know if there is any other alternative to get what I want.

Server edition uses a different kernel than the desktop version.

I don't understand why you would install server if you want to install multiple desktop environments...?

---

