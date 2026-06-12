---
title: "Separate Desktop Environments, Gnome and KDE."
date: 2010-07-03
forum: New to Ubuntu
---

### Post by gallifrey on 2010-07-03
Hello,
        I have just installed Ubuntu 10.04, and I am currently running the gnome desktop. My partner however, prefers KDE. I know that you can download the KDE files via synaptic, but can someone tell me what I should do afterwards?? 

Basically, I want to set it up so that we can choose between KDE and Gnome at Login, and share the same /home partition. Also, I am apprehensive about the applications from one DE infringing on the other, as I have no doubt my partner will install a load of trash...

Anyway, any advice would, as always, be greatly appreciated!

Thank you.

---

### Post by warfacegod on 2010-07-03
```
sudo apt-get install kubuntu-desktop
```

Will get you everything you need. When your at the loggin screen (enter username and password first), click Session at the bottom and it will give you several options, including Gnome and KDE. Select KDE and then click Loggin.

---

### Post by gallifrey on 2010-07-03
> **warfacegod said:**
> ```
sudo apt-get install kubuntu-desktop
```Will get you everything you need. When your at the loggin screen (enter username and password first), click Session at the bottom and it will give you several options, including Gnome and KDE. Select KDE and then click Loggin.


Thank you kindly! If apps are installed in KDE, will they infringe on my Gnome setup at all? Or will the individual DEs stick to their own apps and settings?

---

### Post by wojox on 2010-07-03
> **gallifrey said:**
> Thank you kindly! If apps are installed in KDE, will they infringe on my Gnome setup at all? Or will the individual DEs stick to their own apps and settings?

Sure, but you can keep them separate with [Gnome Menu Extended]("http://linux.softpedia.com/progDownload/Gnome-Menu-Extended-Download-34178.html")

---

### Post by warfacegod on 2010-07-03
> **gallifrey said:**
> Thank you kindly! If apps are installed in KDE, will they infringe on my Gnome setup at all? Or will the individual DEs stick to their own apps and settings?

The settings will stay separate. You will, however, have a mixed Menu. Easily remedied by right clicking the Menu Bar and selecting Edit Menus. At least in Gnome it is, I have no idea if KDE works the same way.

---

### Post by KdotJ on 2010-07-03
You can also install the kde-minimal package. This will basically just install KDE and will cut out a lot of the junk that kubuntu-desktop will install. kde-minimal will also give you the choice between gnome and KDE at login

---

### Post by Nick_Jinn on 2010-07-03
I am interested in doing the same thing, only I want Enlightenment and Gnome. How do I do that one?

Also, does anyone know how to set up Enlightened Gnome? Where you have features of both Gnome and Enlightenment at the same time?

---

### Post by bodhi.zazen on 2010-07-03
> **Nick_Jinn said:**
> I am interested in doing the same thing, only I want Enlightenment and Gnome. How do I do that one?

Also, does anyone know how to set up Enlightened Gnome? Where you have features of both Gnome and Enlightenment at the same time?

you simply install whatever window manager or DE you wish and select it from the log in menu.

Post install customization, if any, themes / etc are up to you and vary be window manager.

---

### Post by lkjoel on 2010-07-03
> **gallifrey said:**
> Thank you kindly! If apps are installed in KDE, will they infringe on my Gnome setup at all? Or will the individual DEs stick to their own apps and settings?
All the apps from KDE will be available to GNOME, and vice-versa.
NOTE: Gnome can run KDE apps, and vice-versa.

---

### Post by warfacegod on 2010-07-03
> **Nick_Jinn said:**
> I am interested in doing the same thing, only I want Enlightenment and Gnome. How do I do that one?

Also, does anyone know how to set up Enlightened Gnome? Where you have features of both Gnome and Enlightenment at the same time?

Looks like:```
sudoa apt-get install e16
``` should get you started. The e16menuedit2 and e16keyedit packages might be useful.

---

### Post by gallifrey on 2010-07-03
would it be "cleaner" from a configuration point of view to install KDE on a seperate / partition and just share the /home partition?? i have my Gnome set up just the way I like it, and really don't want to screw it up, but my other half does need her KDE. I know it would mean separate booting, but that's okay.

Ultimately, i will remedy the situation by buying her a comp of her own to fiddle with, but for now, I have to compromise somehow.

---

### Post by wojox on 2010-07-03
> **gallifrey said:**
> would it be "cleaner" from a configuration point of view to install KDE on a seperate / partition and just share the /home partition?? i have my Gnome set up just the way I like it, and really don't want to screw it up, but my other half does need her KDE. I know it would mean separate booting, but that's okay.

Ultimately, i will remedy the situation by buying her a comp of her own to fiddle with, but for now, I have to compromise somehow.

Sure if you have the space you could do it that way as well. It's just kind of redundant because you installing the base system twice and then two separate desktops. 

It can be done though. :D

---

### Post by Nick_Jinn on 2010-07-03
Also, you would have to reboot instead of just log out, wouldnt you?

---

### Post by warfacegod on 2010-07-03
> **Nick_Jinn said:**
> Also, you would have to reboot instead of just log out, wouldnt you?

I don't think so. I've never dealt with Enlightenment but, if it's like KDE or Gnome, a Log out should be sufficient.

---

### Post by gallifrey on 2010-07-03
I am just fussy when it comes to my computer. She's my pride and joy :D 

I'm a Gnome user, and I have always been careful to keep KDE/Qt apps and libs out of my system. Feels wrong to mix them in, somehow. 

Well, i guess I shall just have to bite the bullet, and tolerate it temporarily. :popcorn:

---

### Post by warfacegod on 2010-07-03
> **gallifrey said:**
> I am just fussy when it comes to my computer. She's my pride and joy :D 

I'm a Gnome user, and I have always been careful to keep KDE/Qt apps and libs out of my system. Feels wrong to mix them in, somehow. 

Well, i guess I shall just have to bite the bullet, and tolerate it temporarily. :popcorn:

At whatever point you get to have your computer back to the way you like it, use Synaptic to remove any references to KDE and QT. If afterward you find that something is broken you can reinstall the ubuntu-desktop package and everything should be right as rain again. This is something of an over simplification but I don't foresee any major complications anyway. The KDE and Gnome packages tend to keep to themselves.

---

