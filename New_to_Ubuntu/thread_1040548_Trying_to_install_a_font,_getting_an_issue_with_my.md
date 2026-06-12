---
title: "Trying to install a font, getting an issue with my permissions"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by mattbutsko on 2009-01-15
I've had ubuntu for a week and love it so much more than XP. Anyway, I was trying to install a font graphically and I get an error about my permissions. Now, I know in the terminal about sudo and such, but I don't know how to install a font through terminal.

Anyway, is there a graphical way to access root temporarily? I'd prefer to learn the graphical way of doing things THEN learn the terminal, which brings me to my question:

How do I install a font (graphically)?

---

### Post by Michael.Godawski on 2009-01-15
hi,

try to open nautilus with root privileges in terminal:

```
gksudo nautilus
```

---

### Post by albinootje on 2009-01-15
> **mattbutsko said:**
>  How do I install a font (graphically)?

Installing a font in Ubuntu should be as easy as putting the font in ~/.fonts/ directory, and log out of the desktop, and log in again.

There's a pretty nice GUI for font management called Fontmatrix however..
Ubuntu 8.10 (Intrepid) has Fontmatrix in the repositories.
For Ubuntu 8.04.1 you can try this :
[http://www.getdeb.net/app/Fontmatrix](http://www.getdeb.net/app/Fontmatrix)

---

### Post by Sealbhach on 2009-01-15
You can just put a ttf file in a the folder called .fonts in your /home directory. You should be able to use it then.

Try

```
mv mynewfont.ttf ~/.fonts
```

or do it graphically in Nautilus. Because it's going into your own personal folder you won't need root permissions.


.

---

### Post by mattbutsko on 2009-01-15
it worked, thanks. But when I try to unmount a dvd (which I could do before hassle-free) it tells me I'm not root. Kinda annoying. I'm sure if I log off and log back in that'll be fixed, but at the same time, I shouldn't have to. -_-

Edit: Nevermind. I logged out and back in and that didn't work. So now I don't have permission to do a lot after using gksudo.

Also, I've tried multiple font files in the ./fonts folder, but none of them installed. (Yes, they were .ttf's)

---

### Post by albinootje on 2009-01-15
> **mattbutsko said:**
> it worked, thanks. But when I try to unmount a dvd (which I could do before hassle-free) it tells me I'm not root. Kinda annoying. I'm sure if I log off and log back in that'll be fixed, but at the same time, I shouldn't have to. -_-

Edit: Nevermind. I logged out and back in and that didn't work. So now I don't have permission to do a lot after using gksudo.

Try this :
```

sudo eject /dev/cdrom*

```

> 
Also, I've tried multiple font files in the ./fonts folder, but none of them installed. (Yes, they were .ttf's)

Try the Fontmatrix GUI.

---

### Post by Sealbhach on 2009-01-15
> **mattbutsko said:**
> 

Also, I've tried multiple font files in the ./fonts folder, but none of them installed. (Yes, they were .ttf's)

Just check you have the right folder name, its .fonts  not ./fonts and it should be in your /home folder.

You can just go into Nautilus and create one (see attached).

---

