---
title: "community themes"
date: 2010-09-01
forum: New to Ubuntu
---

### Post by thatguy93 on 2010-09-01
i downloaded community themes from here:
[http://www.omgubuntu.co.uk/2010/04/10-things-to-do-after-installing-ubuntu.html](http://www.omgubuntu.co.uk/2010/04/10-things-to-do-after-installing-ubuntu.html)

my question is, where are they, and how do i install them? 
also, how do i change the log on screen?

---

### Post by hhh on 2010-09-01
They are installed to /usr/share/themes (or you can install them to /home/USER_NAME/.themes) but to apply them right-click the desktop>Change Desktop Background>Theme

What do you want to change for the login screen?

-edit- If you downloaded the community themes with apturl, they are already installed.

---

### Post by sikander3786 on 2010-09-01
Just navigate to the downloaded compressed file and open it using Install from Themes tab.

An easier way, if you've got an active internet connection on your PC, go to [http://art.gnome.org/themes](http://art.gnome.org/themes) and download the themes, splash screens, login screens, icons, whatever you want and choose to open with theme manager. They will be installed automatically.

Regards.

---

### Post by thatguy93 on 2010-09-01
none of the stuff i downloaded shows up when i go to "import" in emerald theme manager...

---

### Post by thatguy93 on 2010-09-01
nvm. had to change everything to ".emerald"

---

### Post by thatguy93 on 2010-09-01
wow this sucks. i thought it changed everything, not just the windows...

---

### Post by thatguy93 on 2010-09-01
argh this is lame. i installed a theme, now i cant remove it. i even uninstalled emerald....

---

### Post by hhh on 2010-09-01
[http://packages.ubuntu.com/lucid/community-themes](http://packages.ubuntu.com/lucid/community-themes)

These are not Emerald themes, they are GTK themes. They are installed in /usr/share/themes and /usr/share/icons. Uninstall them with one command in terminal...
```
sudo apt-get purge community-themes breathe-icon-theme human-icon-theme
```

---

