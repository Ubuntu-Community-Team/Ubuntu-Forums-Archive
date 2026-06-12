---
title: "Youtube video not playing in Firefox"
date: 2010-11-12
forum: New to Ubuntu
---

### Post by raamee on 2010-11-12
Hey guys, 

        Previously i can view youtube videos flawlessly in firefox. But then, i updated firefox to the latest and i cant see video in youtube, only i can hear is audio. But in other browsers such as in chrome its working fine. I have this problem only in firefox. I have attached the screenshot.

[B][COLOR="Red"]
System_Info:[/COLOR][/B]

Ubuntu 10.04

Firefox - 3.6.12

Latest adobe flash player. If any other details needed, please ask.

---

### Post by stoogiebuncho on 2010-11-12
This has been happening to me occasionally as well.  Restarting firefox seems to fix it.  It's annoying.

Sorry I don't have an actual fix for you.

---

### Post by Hippytaff on 2010-11-12
have you tried
```

sudo apt-get update && sudo apt-get upgrade

```
Can't guarantee it'll work but it s always worth a try :-)

---

### Post by bilalsana on 2010-11-13
i am having exactly the same problem! flash videos play well on other websites like vimeo or facebook! but on youtube there is sound with a grey picture!!

---

### Post by ssulaco on 2010-11-13
Here is some tweaks to try...
[http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)
[http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html)
This may or may not work since the issue seems to be with youtube only

---

### Post by bilalsana on 2010-11-28
i am having the same problem, tried purging all firefox plugins and reinstalling...even tried reinstalling firefox! flash works fine on opera and chrome as well as almost all other sites except youtube! even some embedded youtube content plays fine!!

---

### Post by WienerWuerstel on 2010-11-28
The Problem is solved when you start Firefox in a Terminal with this Command:

export XLIB_SKIP_ARGB_VISUALS=1 && firefox

---

### Post by bilalsana on 2010-11-28
thx WienerWuerstel
tat solves it for me! but wats the permanent solution? and where does the problem lie?

---

### Post by WienerWuerstel on 2010-11-28
The Problem lies in RGBA and you can find the Solution [here]("http://www.webupd8.org/2010/05/enable-rgba-transparency-in-ubuntu-910.html").

---

### Post by myolbug on 2010-12-01
> **WienerWuerstel said:**
> The Problem lies in RGBA and you can find the Solution [here]("http://www.webupd8.org/2010/05/enable-rgba-transparency-in-ubuntu-910.html").

I couldn't find it. Could you elaborate?

---

### Post by myolbug on 2010-12-09
Anyone got this?

---

### Post by bilalsana on 2010-12-09
this is what is supposed to help:

paste this in a terminal:

$gedit ~/.profile &

-and in the .profile file, paste this:

export GTK_MODULES=rgba
export GTK_RGBA_APPS=allbut:firefox-bin:gnome-mplayer:totem:soffice

You can add some more applications to the "GTK_RGBA_APPS" line - the applications you add there will be blacklisted and RGBA support won't be used for them.

---

### Post by bilalsana on 2010-12-09
P.S.
it didnt help me!

---

