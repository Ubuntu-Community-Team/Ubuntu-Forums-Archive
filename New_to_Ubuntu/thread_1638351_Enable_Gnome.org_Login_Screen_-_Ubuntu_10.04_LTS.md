---
title: "Enable Gnome.org Login Screen - Ubuntu 10.04 LTS"
date: 2010-12-05
forum: New to Ubuntu
---

### Post by Invex09 on 2010-12-05
I'm new to Linux and would like to change the login screen to one found at Gnome.org (the site you're taken to when you click "Get more themes online" from the Appearance Settings). Specifically, I'd like to enable the theme "Login Scan Fusion" found here:

[http://art.gnome.org/themes/gdm_greeter](http://art.gnome.org/themes/gdm_greeter)

I've tried following this totorial:

[http://www.n00bsonubuntu.net/content/how-change-login-screen-ubuntu-1004-lucid-lynx](http://www.n00bsonubuntu.net/content/how-change-login-screen-ubuntu-1004-lucid-lynx)

but all this seems to let me do is change the background of the login page. Is it possible to enable the theme I specified on this Ubuntu build? Thanks in advance for any help. Sorry if something isn't clear, this is all pretty new to me. I'd be happy to give more details though so let me know if you have any questions. Thanks again!

---

### Post by Invex09 on 2010-12-15
After looking around I found out that because Ubuntu now uses GDM2, themes aren't supported as they were in GDM. From what I've found, you can really only change the background of the login screen.

---

### Post by Verbeck on 2010-12-15
gdm now uses gtk themes
to change it, run
```

sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow/
```then logout and select the theme you want.
after that, run
```

sudo rm /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```

---

### Post by Invex09 on 2010-12-15
Thanks for the reply Verbeck. I actually found the tips you mentioned earlier today so I was able to use them to change the login background (and could've changed more obviously as it brought up the whole "Appearance" window). Not as a cool as some of the cool themes people have out there, but it'll have to do. From what I've read, it seems its possible to change your version of GDM back down, but it seems really challenging and as I'm relatively new to Linux, not something I plan on tackling. I'm struggling to get my FTP/Web Server working so I've been cruising around the forums trying to figure that out. Functionality always comes before style haha. Thanks again!

---

