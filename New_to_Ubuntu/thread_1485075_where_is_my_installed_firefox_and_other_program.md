---
title: "where is my installed firefox and other program"
date: 2010-05-16
forum: New to Ubuntu
---

### Post by navets on 2010-05-16
The last time i installed my firefox from the .tar.gz2 files .. and having trouble for installing java .. 

And then i system from karmic koala to lucid lynx and getting the java from the ubuntu softwere centre .

now i want to know where is my usually default firefox or my java and any others programs installed ?? i wanna see the plugins ,, directory and maybe knowing more from my system ..

is there anyway to know where my files located like find target in windows ? i tried properties my firefox .. but only firefox%u

thanks before ..

---

### Post by debianlinux on 2010-05-16
just for example:

/etc/firefox
/usr/bin/firefox
/usr/share/menu/firefox
/usr/share/bug/firefox
/usr/share/firefox
/usr/share/doc/firefox
/usr/lib/firefox
/usr/lib/firefox-3.6.3/firefox
/home/(your account name)/.mozilla/firefox
/home/(your account name 1)/.mozilla/firefox
/home/(your account name 2)/.mozilla/firefox


you may find everything about firefox by typing this command :

sudo find / -iname firefox

hope this will help you a bit

---

### Post by lovinglinux on 2010-05-16
For Firefox see [this](http://firefox-tutorials.blogspot.com/2010/05/profiles.html).

Also typing **about[noparse]:[/noparse]plugins** in the address bar will give you information about plugins. You can also set Firefox to expose the full path of the plugin files, by changing the preference **plugin.expose_full_path** to true. See how to change preferences [here](http://firefox-tutorials.blogspot.com/2010/05/preferences-tweaks.html).

---

