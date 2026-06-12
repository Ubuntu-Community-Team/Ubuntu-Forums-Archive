---
title: "Natty Switches my Themes..."
date: 2011-08-13
forum: New to Ubuntu
---

### Post by 2CV67 on 2011-08-13
For the last couple of days, Natty has been playing tricks on me.

Instead of my usual "Clearlooks" theme, it seeems to please itself which theme to use.
Though when I look in "Appearance" it still highlights Clearlooks.

Trying to select something else, then "Clearlooks" again doesn't always work either.
See attached screenshot where I have selected Clearlooks but got a dark blue window border.

[IMG]http://i838.photobucket.com/albums/zz309/2CV67/appearances.jpg[/IMG]

Any ideas?

Thanks!

---

### Post by snip3r8 on 2011-08-13
Interesting ,I also had problems with natty and the appearance manager ,except in my case the appearence manager took up 100% CPU...Its the reason I switched to KDE

Anyhow you could try using commands to set the theme 

to get the current theme
```

sudo -u yourUserName gconftool-2 --get  /desktop/gnome/interface/gtk_theme

```

to set a new theme
```

sudo -u yourUserName gconftool-2 --set --type string --set /desktop/gnome/interface/gtk_theme Clearlooks

```

---

