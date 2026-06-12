---
title: "Appearance Preference Screen Pops Up On Every Reboot And Login"
date: 2010-08-02
forum: New to Ubuntu
---

### Post by giddyup306 on 2010-08-02
Not sure what I did to get it to do this, but I can't find a solution anywhere.  This is annoying!  Thanks in advance,

---

### Post by SpockVulcan on 2010-08-02
Dig around in the startup applications thats where i think the issue is. There will be something about appearance preferences there probably. :D

---

### Post by Brushstroke on 2010-08-02
Open a Terminal, and type this:

> sudo unlink [COLOR=#000000]**/**[/COLOR]usr[COLOR=#000000]**/**[/COLOR]share[COLOR=#000000]**/**[/COLOR]gdm[COLOR=#000000]**/**[/COLOR]autostart[COLOR=#000000]**/**[/COLOR]LoginWindow[COLOR=#000000]**/**[/COLOR]gnome-appearance-properties.desktopThat should prevent it from coming up each time at the login screen. And if you ever need it *back *on the login screen, open a Terminal and type this:

> sudo cp [COLOR=#000000]**/**[/COLOR]usr[COLOR=#000000]**/**[/COLOR]share[COLOR=#000000]**/**[/COLOR]applications[COLOR=#000000]**/**[/COLOR]gnome-appearance-properties.desktop [COLOR=#000000]**/**[/COLOR]usr[COLOR=#000000]**/**[/COLOR]share[COLOR=#000000]**/**[/COLOR]gdm[COLOR=#000000]**/**[/COLOR]autostart[COLOR=#000000]**/**[/COLOR]LoginWindow:)

---

### Post by giddyup306 on 2010-08-03
> **Brushstroke said:**
> Open a Terminal, and type this:

That should prevent it from coming up each time at the login screen. And if you ever need it *back *on the login screen, open a Terminal and type this:

:)

Thanks!  That did the trick!  You have no idea how annoying that was...

---

### Post by Krabby.Linux on 2010-08-03
Im Sure that this was you linking the Appearance screen on startup. You usually do this while playing around with Plymouth Themes Styles Login Screens Splash Screens etc :)

---

