---
title: "gtk 2.x theme"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by iam_newhere on 2009-05-02
how do i make synaptic package manager and firestarter to use gtk2.x theme that is downloaded from gnomelook.org?

everything works when i applied the theme except for these two.

thanks!

---

### Post by LinuxGuy1234 on 2009-05-02
Take a chance and upgrade to 8.10; even better is 9.04 after you go to 8.10. Intergation is fine in 8.10...

---

### Post by m_duck on 2009-05-02
It depends on the theme. Initally installed themes will be fine as they are installed in /usr/share/something and so are global, but subsequently installed themes probably won't work with programs run as root, ie synaptic, as the theme is installed to the home folder, ~/.themes.

I tend to make a couple of symlinks to my users ~/.themes and ~/.icons. Fire up a terminal and type:```
sudo ln -s /home/yourusername/.themes /root/.themes
sudo ln -s /home/yourusername/.icons /root/.icons
```That just makes any programs run as root user look in roots home directory for the theme, which will in turn look in your home directory for any of your installed themes.

I hope that makes sense!

---

