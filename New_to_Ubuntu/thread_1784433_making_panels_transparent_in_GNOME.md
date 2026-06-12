---
title: "making panels transparent in GNOME"
date: 2011-06-16
forum: New to Ubuntu
---

### Post by fremantle on 2011-06-16
this is the classic gnome im talking about. im trying to make my panels and menus transparent. so far ive only succeeded making the entire panel transparent.

im using the atolm theme. i went into the gnome-panel.rc and just changed bg [NORMAL] to #transparent, which worked. but now when i click a menu the drop down is NOT transparent. how can i make it transparent too?

---

### Post by nzjethro on 2011-06-16
Dropdown menus can be made transparent in Compiz. Go to "Opacity, Brightness and Saturation", select "New", can't remeber offhand what the Windows Value should be, maybe something like "DropdownMenu", and select your level of opacity.

---

### Post by fremantle on 2011-06-16
under which section? the opacity related things are 
opacitymathces and opacityvalues

---

### Post by nzjethro on 2011-06-17
There should be a section called "Opacity, Brightness, and Saturation".

It may be an extra plugin, or unsupported. Hunt around, maybe try
```
sudo add-apt-repository ppa:compiz/ppa
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install compiz*
```
This will download all compiz plugins, including Opacity.

---

### Post by fremantle on 2011-06-17
> **nzjethro said:**
> There should be a section called "Opacity, Brightness, and Saturation".

It may be an extra plugin, or unsupported. Hunt around, maybe try
```
sudo add-apt-repository ppa:compiz/ppa
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install compiz*
```
This will download all compiz plugins, including Opacity.

you should see this

---

### Post by nzjethro on 2011-06-17
Ah, try adding "DropdownMenu" in the spaces for opacitymatches and opacityvalues. My compiz looks different - I have a separate category for "Opacity, Brightness, and Saturation" as this screenshot shows. Sorry I can't be more help, your guess is as good as mine.
:D

---

