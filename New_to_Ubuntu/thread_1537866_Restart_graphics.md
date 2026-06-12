---
title: "Restart graphics"
date: 2010-07-24
forum: New to Ubuntu
---

### Post by yc2 on 2010-07-24
Hello,

Two questions about restarting the graphics, please:

1. I think I know that the new command for graphics restart is
rightAlt + sysRq + k
I press the sequence as three individual keys (not like a chord) but the sysRq only opens the print screen dialogue. (Which otherwise can be opened from the prt sc key in a normal way)

I think the problem has to do with my HP-laptop requiring the function key to be pressed to get "sys sq" from the delete-key. (Without the function key it does not work either)
(My right alt is the "alt gr")

2. Are these two commands the same?
sudo /etc/init.d/gdm start
sudo startx


I run Lucid/Gnome.

Thanks

---

### Post by hhh on 2010-07-24
re: question one, see this...
[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Ctrl-Alt-Backspace%20disabled%20by%20default%20in%20Xorg,%20configured%20via%20XKB](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Ctrl-Alt-Backspace%20disabled%20by%20default%20in%20Xorg,%20configured%20via%20XKB)

---

### Post by yc2 on 2010-07-24
Thanks hhh,

The problem in question one is solved by following the procedure in the link you posted, going back to ctrl/alt/backspace.

---

### Post by hhh on 2010-07-24
No problem. re: question 2, I almost positive they're not exactly the same. gdm is the Gnome Display Manager...
[http://en.wikipedia.org/wiki/GNOME_Display_Manager](http://en.wikipedia.org/wiki/GNOME_Display_Manager)
...while x is xinit...
[http://en.wikipedia.org/wiki/Startx](http://en.wikipedia.org/wiki/Startx)
HTH

---

### Post by yc2 on 2010-07-25
I think you are right, but I am still not absolutely clear about the difference.

I guess, after installing graphics on a server you would have to use startx?
```
sudo apt-get install ubuntu-desktop
sudo startx

```

But if you just want to restart graphics you can do
```
sudo /etc/init.d/gdm restart

```

maybe ;)

The display manager seems to be a rather important part of the graphics system "X"

---

