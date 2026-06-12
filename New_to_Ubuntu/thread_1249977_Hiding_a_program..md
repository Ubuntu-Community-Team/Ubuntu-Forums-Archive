---
title: "Hiding a program."
date: 2009-08-26
forum: New to Ubuntu
---

### Post by osc1882 on 2009-08-26
Hey there. I was wondering if it would be possable to hide a running program while you were away from the computer. Such as skype or a torrent program. Is there a way to leave running but have it not show up, at lest in gui forum. It can show up in other ways I guess. I would just like to find a way to hide a program while someone is away. 

Any ideas?

---

### Post by wojmur on 2009-08-26
I think you could start another X-Windows session from another console (something like Ctl-Alt-F2, login, run startx). I think you can then switch between the X Windows sessions with Ctl-Alt-F7 and Ctl-Alt-F2. But as I say, haven't actually tried it myself :)

---

### Post by inobe on 2009-08-26
maybe create a separate user account then switch over with fast user switch.

---

### Post by blackened on 2009-08-26
Move it to a different virtual desktop, then make sure your Window List Content (right click the Window List separator and hit "Preferences") is set to "Show windows from current workspace". As long as you don't have the workspace switcher in the panel it will be completely hidden.

---

### Post by nothingspecial on 2009-08-26
Use a command line app eg rtorrent.

Use in conjunction with screen

```
sudo apt-get install rtorrent screen
```

[[COLOR="Magenta"]Here[/COLOR]]("http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/") is a nice beginners guide to rtorrent.

Launch a terminal and type ```
screen
```

Launch rtorrent and start your torrenting activities then press Ctrl+A then D

Your rtorrent session will disappear.

When you want to check your progress just type ```
screen -r
``` and your rtorrent session will magically reappear. 

You can do this using ssh from anywhere in the world.

Good isn`t it.

---

### Post by 3rdalbum on 2009-08-26
Go to the menu on the extreme top-right of your screen. Go to "Lock Screen". This makes your screensaver kick in, and it requires a password in order to exit the screensaver.

I'm sure we've all used the old "switch virtual desktops to hide your programs" trick, but it doesn't work very well because there is a chance that it will still be discovered if the other person puts their hand on the mouse.

---

### Post by brunogirin on 2009-08-26
I agree with 3rdalbum: locking your screen when you leave your computer is a good habit to take. You even have a keyboard shortcut to do that: CTRL+ALT+L

---

### Post by osc1882 on 2009-09-01
Well he would like people to be able to use the computer and not know that these programs are running.

---

### Post by clutch| on 2009-09-01
> **blackened said:**
> Move it to a different virtual desktop, then make sure your Window List Content (right click the Window List separator and hit "Preferences") is set to "Show windows from current workspace". As long as you don't have the workspace switcher in the panel it will be completely hidden.

This seems to me like it would be the easiest way.  So long as you don't think anyone is likely to ctl+alt+arrow over to the other workspace.  He's just basically saying to move it to another workspace and the set the preferences so that the switcher doesn't show up in the bottom right, correct?

You trying to hide a keylogger from your girlfriend, or what?:D

---

### Post by Villiam on 2009-09-01
At least if you talk about torrent downloading software, there are softwares which have "minimize to tray" option in Windows. I hope it will work in ubuntu as well and will serve your purpose.

---

### Post by blackened on 2009-09-02
> **clutch| said:**
> This seems to me like it would be the easiest way.  So long as you don't think anyone is likely to ctl+alt+arrow over to the other workspace.  He's just basically saying to move it to another workspace and the set the preferences so that the switcher doesn't show up in the bottom right, correct?

You trying to hide a keylogger from your girlfriend, or what?:D

That is what I meant. You could even go so far as to remove the switcher from the panel and only use the hotkey to cycle between desktops. In the Windows-centric world that we live in most people don't even know VWMs exists, much less how to they work or can be manipulated.

---

