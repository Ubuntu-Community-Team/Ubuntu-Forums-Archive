---
title: "ibus with openbox"
date: 2010-08-03
forum: New to Ubuntu
---

### Post by a.sarkar on 2010-08-03
Dear All,

I am trying to make ibus work with openbox (in lucid lynx) for Bengali  support.
(an Indian language). Installed the following packages
```

ibus ibus-gtk ibus-m17n ibus-table	libibus1 libusb-0.1-4 libusb-1.0-0 libusbmuxd1 python-ibus language-selector

```
Typed "gnome-language-selector" in the terminal to add support of bengali language. 
Also selected "ibus" for "Keyboard input method system".
Then typed "ibus-daemon" in the terminal which brought the icon in my system tray.

Right clicked on the ibus icon > Preferences > Input Method > "Select an input method" >
But it only shows "Other > Latex" and "Other > Compose" entries. No entry to add Bengali
language.

For gnome, in another machine, "Select in input method" showed all languages. 

Now my question is am I missing any packages? I thought ibus-m17n was the right package for this.

---

### Post by a.sarkar on 2010-08-03
Solved it. Thanks to [[COLOR="Blue"]this[/COLOR]]("http://jbakshi.50webs.com/Linux_tutorial/Bangla/ibus-bangla.html") post

One has to install the following packages for various language support.

```
sudo apt-get install libm17n-0 m17n-lib-bin m17n-db m17n-contrib
```

Then the "Select an input method" gets filled up with various options.

To start it automatically, put the following line in my autostart script.

```
ibus-daemon -rd &
```

Done.

---

