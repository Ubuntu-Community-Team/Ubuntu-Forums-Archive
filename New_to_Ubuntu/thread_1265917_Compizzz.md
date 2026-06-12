---
title: "Compizzz"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by sububtu on 2009-09-14
how to enable compiz??
i had dowloaded compiz and its dependencies..& already installed..
---------
when i tried customize appearance ,frm system menu, it searched for  som drivers & returned an error, that the "desktop effects cannot be enabled"

---

### Post by alphacrucis2 on 2009-09-14
> **sububtu said:**
> how to enable compiz??
i had dowloaded compiz and its dependencies..& already installed..
---------
when i tried customize appearance ,frm system menu, it searched for  som drivers & returned an error, that the "desktop effects cannot be enabled"

You need a driver that supports 3d acceleration. What brand and model graphics card do you have?

---

### Post by sububtu on 2009-09-14
oopss! That graphics card always messingup,,
i had a problem with my graphics card, that it doesnt works well with ubuntu 9.04 and suggests degrading the driver,
im using onboard graphics (intel 965 chipset),,, is that possible to run compiz with onboard graphics ??

---

### Post by v1nsai on 2009-09-14
It should be possible to run compiz, it isn't that demanding on your card to run just the core.  I recommend installing ccsm to control your compiz effects much more easily.  You can get it by running
```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by sububtu on 2009-09-15
there was some problem with graphics, now i corrected those problems,,
one more doubt, i had downloaded some themes which contains some nice docks and gadgets ,but- no dock is displayed yet! why it happend so?

---

### Post by raymondh on 2009-09-15
> **sububtu said:**
> there was some problem with graphics, now i corrected those problems,,
one more doubt, i had downloaded some themes which contains some nice docks and gadgets ,but- no dock is displayed yet! why it happend so?

what is the dock?

If AWN (avant windows navigator), here is the FAQ's

[http://wiki.awn-project.org/FAQ](http://wiki.awn-project.org/FAQ)

---

### Post by Bölvaður on 2009-09-15
> **sububtu said:**
> had downloaded some themes which contains some nice docks and gadgets ,but- no dock is displayed yet! why it happend so?

What theme is that?

Did the theme change correctly (other than the dock did not show up)?



It might be that the dock is not part of the theme, and they just forgot to say that in the description of it.
There are few docs available. You can find them and install from Applications &#8594; Add/Remove and search for '*Dock*'. You might want to change the filter (from the drop down list) to _allow all applications_, not just the ones supported by cannotical.
A popular dock is called AWN (Avant Window Navigator)

---

### Post by sububtu on 2009-09-16
NO NO its,, something like Cairo,..
that was little bit tough for me to install(i guess that the installation might not be done correctly) let me check the AWN dock

---

### Post by v1nsai on 2009-09-16
You have to run a dock before it is displayed.  Just find it in Applications and click the name of the program.

---

### Post by Bölvaður on 2009-09-16
> **sububtu said:**
> NO NO its,, something like Cairo,..
that was little bit tough for me to install(i guess that the installation might not be done correctly) let me check the AWN dock

it is very easy to install.

Look at your top panel.
Applications &#8594; Add/Remove

search for dock (like I suggested before) and click on the box next to Cairo, then click apply changes (or something like that).

Alternatively you can click this [link]("apt:cairo-dock")

---

