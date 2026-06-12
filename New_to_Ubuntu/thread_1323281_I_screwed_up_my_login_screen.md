---
title: "I screwed up my login screen"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by Timi47 on 2009-11-11
Ok so installed 9.10 onto my computer and chose the option that stated that I needed to login to my account to decrypt my home folder. Well lastnight I configured the option that allows for
me to bypass the login screen. Unfortunatly this brings up error messages and brings me to a screen with the default background and no navigation features whatsoever except for a terminal I managed to bring up. 

Is there anyway to reach the login screen so I can get into my account and change the settings, o am I going to have to reinstall ubuntu and start all over again?

---

### Post by durand on 2009-11-11
Does the terminal have a login prompt? If so, try the following:

type in your username, press enter, type in your password (nothing shows up on screen when typing), press enter. It should then login.

Then try to restart the login manager with ```
sudo /etc/init.d/gdm restart
```. You should then get your login manager, hopefully.

---

