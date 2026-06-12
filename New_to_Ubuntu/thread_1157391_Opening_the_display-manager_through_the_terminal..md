---
title: "Opening the display-manager through the terminal."
date: 2009-05-12
forum: New to Ubuntu
---

### Post by Nielsoerbaek on 2009-05-12
** spoiler-alert ** I actually just have to know how i open the diplay managing program through the terminal. 
Explination below.

This is spooky. I tried to connect my monitor to my TV and the result was a little disturbing. I think that i in the process chose the, now not connected, other monitor as my default. I have no panels, but gnome-panel is running, and when i switch between workspaces i can see a flash of the panels going by, as is there on another monitor, or something. I think this could be solved if i only knew how to open the display manager or monitor manager or what it is called thought the terminal. help?!?

Thanks in advance.

---

### Post by OffAxis on 2009-05-12
Try rebooting with only the one monitor hooked up (it should auto detect); CTRL+ALT+Backspace to restart X.

Depending on what version you're running it could be as easy as 

```
sudo displayconfig-gtk
```


If you've got an nvidia card you could try the nvidia tools

```
sudo nvidia-settings
```

you could also try
```
gnome-panel
```

and if you need to adjust settings on your monitor, you could try
```
sudo dpkg-reconfigure xserver-xorg
```
or 
```
xrandr
```

---

### Post by Nielsoerbaek on 2009-05-12
Thanks alot for the reply, but i'm afraid that none of the suggestions worked. I only have one monitor connected now, but neither restarting nor CTRL+ALT+Backspace did anything. sudo displayconfig-gtk gave me a command not found (i have 8.10 by the way). And when i use gnome-panel i just said that a panel is already running.

---

### Post by Nielsoerbaek on 2009-05-12
Hooray!

An a little too quick reply i guess. I restarted and used CTRL+ALT+Backspace again and everything is A.O.K.!

Thanks a million!

---

