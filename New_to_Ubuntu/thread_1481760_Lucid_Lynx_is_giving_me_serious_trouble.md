---
title: "Lucid Lynx is giving me serious trouble"
date: 2010-05-12
forum: New to Ubuntu
---

### Post by Jonwenger on 2010-05-12
Yesterday, I upgraded to the new version of Ubuntu: 10.04. I have had 9.10 before, so I wanted to try the new release. As soon as I restarted my laptop, the first thing I noticed is that there is only a blurry gray Ubuntu sign, not nice at all as the website promised. Then as I startup, I notice that my cursor has turned into a black X except when I am in firefox. Then it shows the default theme. I could probably manage if it was only these problems, but somehow my window manager is not working. I do not have any frames around windows, meaning: I cannot resize windows, nor do I have the three buttons for closing, maximizing and minimizing. Also, my workspace switcher app seems to be broken. My screenlets do not work either. Anybody have any ideas on this?

Errors/Bugs/Problems:

1. blurry, black and white Xubuntu logo on startup
2. Cursor shows a black X instead of white arrow
3. no frames around windows
4. workspace switcher app broken
5. screenlets don't work

---

### Post by Jonwenger on 2010-05-12
I just noticed that when I click on the small square button in the bottom left, that hides all windows and shows the desktop, says that: ```
Your window manager does not support the show desktop button, or you are not running a window manager.
```

---

### Post by dE_logics on 2010-05-12
metacity --replace

if that doesnt work - 

compiz --replace.

---

### Post by 2hot6ft2 on 2010-05-13
> **Jonwenger said:**
> 
Errors/Bugs/Problems:

1. blurry, black and white Xubuntu logo on startup
2. Cursor shows a black X instead of white arrow
3. no frames around windows
4. workspace switcher app broken
5. screenlets don't work

1. Startup manager can set the screen resolution and color depth
```
sudo apt-get install startupmanager
```
Then it in ubuntu it would be in
System > Administration > Startup Manager
In Xubuntu I don't know, set the resolution in both tabs and the depth in the first one.
I don't remember any promise of resolution, but eh.

2. From ubuntu
> Sebastien Bacher wrote on 2010-04-07:
the issue is mostly cosmetic and higher priority bugs are on the desktop team list for lucid so no, nobody is working on this one, you are welcome to try to fix it though we would welcome extra hands fixing issues
TheeMahn said we were free to do what we want with his work and I'm sure he would approve of sharing it for your benefit here so if you are running 32 bit here's the fix.
> Your file has been saved and can now be downloaded 10 times. It will be deleted after 60 days without download.
[Click here to download file]("http://rapidshare.com/files/386696607/compiz-core_0.8.4-0ubuntu15_i386.deb.html")
MD5: EB4FF7F41FF5AB1FE5FE1720C29F51A2
It's a deb so just download and save then check the MD5SUM with:
```
md5sum compiz-core_0.8.4-0ubuntu15_i386.deb

```
If it's a match double click to install and reload the windows manager or log out and back in and enjoy.

If I was running 64 bit I would compile the 64 bit package but I'm not and Thee is too busy right now.

3. I suspect 2 will take care of that if not change the compiz windows manager.

4. Install restricted driver if using nVidia, enable effects if using ATI
System > Administration > Hardware Drivers
System > Preferences > Appearance > Visual Effects

5. Beats me I don't use them.
:popcorn:

---

### Post by Jonwenger on 2010-05-13
Thank you both very much. For people with the same problems, the problem with the window manager was solved by ```
metacity --replace
``` and the rest by 2hot6ft2.

*Edit* Unfortunately I spoke too early. After I restarted I had to enter the Command: ```
metacity --replace
``` again. Is there anyway to make this permanent? Btw. this also fixes screenlets.

---

