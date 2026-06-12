---
title: "help with windows management"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by shawnpeterson77 on 2009-03-23
Hi, i recently dumped vista, and did a total install of ubuntu 8.10.  i believe i am having either video card issues ( nvidia geforce 7300 le, i have the recommended driver installed...177 something) or monitor issues.  I had to finagle the resolution to be able to actually see the entire desktop.

While this has been mostly resolved, the one issue that I cannot seem to fix is the title bar on the windows.  essentially, if I hover my mouse over the 'minimize, maximize, close out' buttons, the title bar flickers and looses color (it does not go away, but you can nolonger see anything on it).  

I have been in the compize settings manager, and fiddled with basically everything, but nothing seems to change this glitch.

Any suggestions?

Shawn

note:  i tried to take a screenshot of this effect, but the picture shows the window in the correct format. (lol)

---

### Post by kanikilu on 2009-03-23
Out of curiosity, does this occur if you turn the desktop effects (compiz) off? System > Preferences > Appearance > Visual Effects > None.

---

### Post by sandyd on 2009-03-23
thats the easy part.

```

sudo gedit /etc/X11/xorg.conf
```
add this to the botom
```

Section "Extensions"
 Option "Composite" "False"
 EndSection

```

p.s. are you using KDE 4.2?

if you are, add
```

[Compositing]
Enabled=false

```
to your kwinrc file (located in ~/.kde4/share/config/) or (~/.kde/share/config/)

---

### Post by shawnpeterson77 on 2009-03-23
Hmm, it does not seem to be happening with the desktop effects turned off...I of course like the cool effects.  Is there any way to have my cake and eat it too?

carlee, thanks for the response, but I have no idea what you just said.  would I type 'xorg.conf' into the terminal, and then add the said code at the bottom?  If so, what would that do?

---

### Post by mvalviar on 2009-03-23
Try this [http://robwilkerson.org/2008/12/08/fix-title-bar-issues-in-ubuntu-810-intrepid-ibex/]("http://robwilkerson.org/2008/12/08/fix-title-bar-issues-in-ubuntu-810-intrepid-ibex/")

---

### Post by shawnpeterson77 on 2009-03-23
> **mvalviar said:**
> Try this [http://robwilkerson.org/2008/12/08/fix-title-bar-issues-in-ubuntu-810-intrepid-ibex/]("http://robwilkerson.org/2008/12/08/fix-title-bar-issues-in-ubuntu-810-intrepid-ibex/")

This appears to be the exact same problem.  I will try the posted solution and let you know.  Thanks for the help (everyone).

---

### Post by shawnpeterson77 on 2009-03-23
> **shawnpeterson77 said:**
> This appears to be the exact same problem.  I will try the posted solution and let you know.  Thanks for the help (everyone).

Okay, this worked, but I had to use a different instruction guide to accomplish it... [http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

Apparently this issue has come up before.  Anyway, thank you for the help.

---

### Post by sandyd on 2009-03-23
> **shawnpeterson77 said:**
> Hmm, it does not seem to be happening with the desktop effects turned off...I of course like the cool effects.  Is there any way to have my cake and eat it too?

carlee, thanks for the response, but I have no idea what you just said.  would I type 'xorg.conf' into the terminal, and then add the said code at the bottom?  If so, what would that do?
edited post

it will disable desktop effects
which seem to cause some problems with certain video cards

---

