---
title: "[SOLVED] Metacity and Compiz will not work together"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by Mazza558 on 2009-01-02
For some reason, I cannot get metacity window borders and compiz to actually run at the same time. There's a metacity theme that I want to use which has no alternative with emerald. 

- Disabling emerald results in no window borders at all
- Doing metacity --replace followed by compiz --replace just starts emerald up again
- Compiz --replace by itself starts emerald with it.

---

### Post by jerome1232 on 2009-01-02
I'm going to recomend fusion-icon, it's sits in your tray, you can right click it and access compizconfig-settings-manager, you can switch between metacity and compiz window managers, you can switch between emerald and gtk for drawing window decorations.

It's a very nice utility I add it to sessions so it starts up when I log in.

```
sudo apt-get install fusion-icon
```

To run it hit alt+f2 and type "fusion-icon" without the quotes.

---

### Post by mcduck on 2009-01-02
They can't run at the same time,a s they are noth window managers (and would do the same thing). If you want to use Metacity themes with Compiz effects you need to set compiz to use gtk-window-decorator instead of emerald.

Open a terminal and run "gtk-window-decorator --replace" to load the GTK decorator instead of emerald. 

Then go to Compiz Config Settings Manager->Effects->Window-Manager and set the comamnd to "gtk-window-decorator --replace", and Compiz should now load the correct decorator automatically.

(Metacity and Compiz are both window managers, Metacity uses it's own themes but Compiz can run several different window decorators, like emerald and gtk-window-decorator. Different window decorators allow it to use different types of themes)

---

### Post by anjilslaire on 2009-01-02
Metacity and Compiz are 2 separate window managers. They are not supposed to run simultaneously. It's either/or by design.

---

### Post by LowSky on 2009-01-02
you need to turn off emerald, I believe jerome1232 suggestion of fusion icon will give you the optin to turn off emerald, otherwise go to CCSM and change the window manger back to the default, or uninstall emerald.

Personally I hate emerald, it just one extra piece of eye-candy that always ends up abroken mess up my computer..

---

### Post by Mazza558 on 2009-01-02
> **mcduck said:**
> They can't run at the same time,a s they are noth window managers (and would do the same thing). If you want to use Metacity themes with Compiz effects you need to set compiz to use gtk-window-decorator instead of emerald.

Open a terminal and run "gtk-window-decorator --replace" to load the GTK decorator instead of emerald. 

Then go to Compiz Config Settings Manager->Effects->Window-Manager and set the comamnd to "gtk-window-decorator --replace", and Compiz should now load the correct decorator automatically.

(Metacity and Compiz are both window managers, Metacity uses it's own themes but Compiz can run several different window decorators, like emerald and gtk-window-decorator. Different window decorators allow it to use different types of themes)

I'm running the very latest compiz version, so unfortunately can't install compiz-gnome (and therefore can't run gtk-window-decorator). Thanks for this though - I now understand what's going wrong.

As for fusion-icon, I'm using that already but the window decorator shows no metacity option.

---

### Post by Mazza558 on 2009-01-02
Just to clarify: I mean metacity's** window borders** in combination with compiz (e.g how Ubuntu's default desktop effects are set up).

EDIT: I removed the new compiz and went back to Intrepid default, and now I can use metacity's window borders. Thanks for all your help.

---

