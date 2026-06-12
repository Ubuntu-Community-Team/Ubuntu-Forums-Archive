---
title: "I just accidentaly turned of the window manager...  HELP!!"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by qwertyuiop96 on 2009-04-15
I recently installed kde in Ubuntu, so I have kde and gnome.  I was playing with kde, and lauched compiz.  Logged out, logged back in, and my emerald theme was in kde!  I quit emerald, and now I have no window manager in KDE.  What is the default so I can launch it?  Please help!

---

### Post by abn91c on 2009-04-15
try ```
kwin --replace
```

---

### Post by HermanAB on 2009-04-15
Well, it is 'kdm' but  don't think that you can simply run it.  You may need to restart X to get things to work right again.

---

### Post by tom66 on 2009-04-15
You should be able to run it without restart. If you run "compiz --replace" it *should* start your default WM.

---

### Post by qwertyuiop96 on 2009-04-15
kwin --replace works, but if I exit the terminal...  everything goes to no window manager again.

---

### Post by abn91c on 2009-04-15
> **qwertyuiop96 said:**
> kwin --replace works, but if I exit the terminal...  everything goes to no window manager again.
run the command again then go to system settings>desktop>desktop effect and disable then

---

### Post by tom66 on 2009-04-16
In a terminal type "compiz --replace &"

No quotes, the final ampersand is important (it lets you close the terminal and keeps it running).

---

### Post by belikralj on 2009-04-16
since "kwin --replace" worked for you just add an & to the end (ie "kwin --replace &") and that should solve the problem of it ending soon as you close the terminal.

---

### Post by qwertyuiop96 on 2009-04-16
I did it a different way- went to autostart apps and added kwin.  That seems to be working for now, and I am very happy with KDE--I prefer blue over brown. ;)

---

### Post by Mulenmar on 2009-04-16
> **qwertyuiop96 said:**
> ... I am very happy with KDE--I prefer blue over brown. ;)

Not to mention the awesome plasmoids! KDE4 's definitely better than it was back when it first came out. I just installed it this morning, an am pleasantly surprised. Much more crystal clear, pretty and all. But even plain Firefox 3 (as opposed to Swiftfox) beats Konqueror as a browser in the speed department 8~( It ain't painful, but it's noticeable.

Oof, that was OT...anyway, glad your problem's solved! :)

---

### Post by qwertyuiop96 on 2009-04-16
> **Mulenmar said:**
> Not to mention the awesome plasmoids! KDE4 's definitely better than it was back when it first came out. I just installed it this morning, an am pleasantly surprised. Much more crystal clear, pretty and all. But even plain Firefox 3 (as opposed to Swiftfox) beats Konqueror as a browser in the speed department 8~( It ain't painful, but it's noticeable.

Konqueror also doesn't support plugins- won't even do flash!!  It seems.  Gmail has to run in Plain html for it.  RRRRg  I just use firefox.

---

