---
title: "emerald and compiz?"
date: 2009-08-07
forum: New to Ubuntu
---

### Post by Kaymeerah on 2009-08-07
I decided to customize a theme with emerald, then read on the forums that i had to run "emerald --replace", that did nothing.. infact it disabled my desktop effects and left the old theme be, it also messed up X server, and the Nvidia drivers got messed up as a consequence, i decided to completely remove metacity, nvidia drivers and xserver, and reinstall them. This did not work either, i still get "Desktop effects could not be enabled", i tried running metacity --replace, still nothing, glxinfo says nothing than normal after the nvidia reinstall, compiz --replace doesnt work either and i pretty much ran out of ideas. u got some ideas?

Ubuntu 9.04 jaunty 64 bit

---

### Post by sdlynx on 2009-08-07
install "fusion-icon", then run that.  It will add a little cube icon to your system tray. Right click it and change your window decorator to emerald.

---

### Post by Kaymeerah on 2009-08-08
didnt work

---

### Post by Kaymeerah on 2009-08-08
okay if anyone else got the same problem as me, remove metacity COMPLETELY

CTRL + ALT F1 and then

```
sudo apt-get remove metacity
```

should be able to enable desktop effects

now after this, make ur theme with emerald, and goto compizconfig -> effects -> window decoration -> /usr/bin/emerald

then ALT + F2 and type

```
emerald --replace
```

should be enough

RESULT at my comp: [img]http://i25.tinypic.com/2v7yp2x.png

---

### Post by sdlynx on 2009-08-08
I don't suggest removing metacity.  If compiz crashes, you'll have no window borders.

---

### Post by coldReactive on 2009-08-08
> **sdlynx said:**
> I don't suggest removing metacity.  If compiz crashes, you'll have no window borders.

+1 on this.

---

### Post by Kaymeerah on 2009-08-09
hmm well u can always boot into recovery root console and type apt-get install metacity tho, besides ive never seen compiz crashing

---

### Post by steveneddy on 2009-08-09
> **Kaymeerah said:**
> hmm well u can always boot into recovery root console and type apt-get install metacity tho, besides ive never seen compiz crashing

The correct command is

```
emerald --replace
```

It is not recommended that you uninstall Metacity.

Look - try compiz-check to determine what exactly the issue is.

It isn't 
Emerald specific but you could use this application to make sure that all of the elements are available to you for the running of compiz and emerald.

Also look here for any help:

[http://ubuntuguide.org/wiki/Ubuntu:Jaunty#Eye_Candy_Applications](http://ubuntuguide.org/wiki/Ubuntu:Jaunty#Eye_Candy_Applications)

---

### Post by sdlynx on 2009-08-10
compiz crashes for me every once in a while, sometimes when I'm doing two different actions with compiz at the same time that isn't supposed to happen (ie super + tabbing while trying to unfold the cube).

its easy to tell because if using emerald your window borders change to metacity and your workspaces change to the default two compiz-less ones

---

