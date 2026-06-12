---
title: "All text boot"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by mvalviar on 2010-04-25
How do I enable all text boot and login and a shell and present bash on login and if I want start x I type startx? 

I read a thread but starting means typing sudo gdm-bin startx if you don't apps on gnome that needs root privileges needs to be started off a shell instead of presenting a authentication prompt. This is a bit inconvenient. 

Is there a way to get an all text verbose boot, a shell on login and start x with '$ startx' and gnome will just work normally?

---

### Post by -humanaut- on 2010-04-25
Are you running Lucid? If you just let it sit at the TTY1 console it will go to a graphical boot. (Im guessing your using a nvidia card?) An update today seemed to bring back the 16-color display for me. (kubuntu lucid)

---

### Post by nothingspecial on 2010-04-25
You need to edit /etc/default/grub 

So that the 9th line (including lines with nothing written) reads

GRUB_CMDLINE_LINUX_DEFAULT="text"

text instead of quiet splash (or whatever it says)

then ```
sudo update grub
```

You will probably have to edit your xinitrc to have startx work.

Or you could type ```
sudo service gdm start
```

I would not recommend starting X as root though.

---

