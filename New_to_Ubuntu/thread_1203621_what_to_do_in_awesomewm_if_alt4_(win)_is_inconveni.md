---
title: "what to do in awesomewm if alt4 (win) is inconvenient"
date: 2009-07-03
forum: New to Ubuntu
---

### Post by tacitdynamite on 2009-07-03
hello all, 
i just got my first linux variety (jaunty) after a few years of using cygwin in windows xp.  i've installed awesome window manager 3.2, and i've discovered that it uses the alt4 (windows) button for all of the default mod keys. this is unacceptable for me because on my toshiba laptop some dufus made the windows key a tiny key in the upper right corner of the keyboard.  is there any way to change the default mod key in awesome wm?

thanks!

---

### Post by kk0sse54 on 2009-07-19
This is a little old but still deserves a reply...

First you need to make sure you copy over the default config file to ~/.config/awesome

```

mkdir -p ~/.config/awesome
cp /etc/xdg/awesome/rc.lua ~/.config/awesome
```

I don't use ubuntu but you might need to change the permissions of the ~/.config/awesome/rc.lua to make it writable. Either "chown <user> ~/.config/awesome/rc.lua" or the chmod command will work. Type man chown or man chmod to find out more about them. But once you've got the file copied over you need to edit your rc.lua

```
gedit ~/.config/awesome/rc.lua
```

scroll down until you find the variable modkey = "Mod4" and just change it to the key you would like. For example Mod1 is "Alt". Be aware though that it recommends you changing keys by remapping Mod4 using something like xmodmap.

---

### Post by tacitdynamite on 2009-07-20
Thanks for your careful answer to my question! You helped me a lot.

---

