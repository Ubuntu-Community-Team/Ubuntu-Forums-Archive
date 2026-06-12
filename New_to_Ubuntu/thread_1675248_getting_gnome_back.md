---
title: "getting gnome back"
date: 2011-01-25
forum: New to Ubuntu
---

### Post by ajaykumarb on 2011-01-25
I have set gnome-shell as default using the following command.

ln -s ~/gnome-shell/install/share/applications/gnome-shell.desktop ~/.local/share/applications/gnome-shell.desktop
gconftool-2 -s /desktop/gnome/session/required_components/windowmanager "gnome-shell" -t string

Can anyone help how to make old gnome as the default.

Thank you
Ajay

---

### Post by sirrod on 2011-01-25
I had luck deleting the link in the .local directory. So...

```
rm ~/.local/share/applications/gnome-shell.desktop
```

Then, since the gconftool-2 command required "gnome-shell" as the window manager, I just ran it again and replaced "gnome-shell" with "compiz" or "gnome-wm" or whatever window manager you want. So...

```
gconftool-2 -s /desktop/gnome/session/required_components/windowmanager "compiz" -t string
```

or...

```
gconftool-2 -s /desktop/gnome/session/required_components/windowmanager "gnome-wm" -t string
```

Now, when you restart, you should be back to regular gnome-desktop. I was a little unsure of this myself a couple days ago, but I messed with it enough to get back to something usable again. I'm still using gnome-shell some of the time, but I need to go back and forth depending on what I'm doing.

---

### Post by Bucky Ball on 2011-01-25
When you boot to the login screen is there no option in 'Sessions' to boot to a gnome desktop (or any other desktop environment you have installed for that matter)?

---

### Post by sirrod on 2011-01-25
There *are* those options, but the fact that a link was placed in the .local directory for startup and the required window manager was set to gnome-shell means that gnome-shell will be loaded no matter the selection on the login screen.

---

