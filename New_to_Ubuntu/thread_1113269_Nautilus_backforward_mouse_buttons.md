---
title: "Nautilus back/forward mouse buttons"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by tracerbullet on 2009-04-01
Yes yes it's the age-old conundrum: Why won't back and forward work in Nautilus when it works just fine in Firefox?

Call me stupid and all that, but I couldn't find a fix for this.

Obviously (or maybe it's not that obvious...) I would prefer to do this in a way that modifies Nautilus, since my mouse works as intended everywhere else (read: Firefox). But if this is absolutely not possible, I will settle for something less elegant.

---

### Post by Yashiro on 2009-04-01
Because the Nautilus coders wont make it work.

You can work round it by using *xbindkeys* or something similar that maps Alt+Left and Alt+Right to your thumb buttons.

---

### Post by LowSky on 2009-04-01
> **Yashiro said:**
> 
You can work round it by using *xbindkeys* or something similar that maps Alt+Left and Alt+Right to your thumb buttons.

This would work, but might interfere with other applications that may be running at the time.

---

### Post by tracerbullet on 2009-04-01
> **Yashiro said:**
> Because the Nautilus coders wont make it work.
But is this not something we (the community) can/did add? Is that not the entire point of stuff being free(aif)?

> **LowSky said:**
> This would work, but might interfere with other applications that may be running at the time.

My thinking exactly. I know there are solutions that will have the effect I want, but I might end up creating more problems than I solve.

---

### Post by tracerbullet on 2009-04-02
Still searching for a solution to this.

---

### Post by tracerbullet on 2009-04-02
Oh and... Nautilus doesn't have built in ftp?! Surely someone must have added this by now? :?

---

### Post by Yashiro on 2009-04-02
File > Connect to Server

Add it to your bookmarks when you're logged in.
You can use it like a normal folder from now on.

Or just type the address into the location line.

---

### Post by tracerbullet on 2009-04-05
> **Yashiro said:**
> File > Connect to Server

Add it to your bookmarks when you're logged in.
You can use it like a normal folder from now on.

Or just type the address into the location line.

Ah, I found the problem. Nautilus doesn't comply unless I tack on an extra ```
ftp://
``` Firefox usually does that for me. :D

Still looking for a solution to the mouse problem though.

---

### Post by tracerbullet on 2009-04-20
Bah, the thread seems to have drowned.

I'm still looking though... :(

---

### Post by inunu on 2009-04-20
I used btnx to sort out the back forward in Nautilus.

---

### Post by LowSky on 2009-04-20
[http://live.gnome.org/Nautilus/WhosWho](http://live.gnome.org/Nautilus/WhosWho)

why not ask on of those guys why frward/back isn't availible.

You know what I think is funny, humans are so lazy they rather use their thumb, rather than move their wrist to move mouse an inch or so.

---

### Post by f0ku5 on 2009-04-21
The GNOME guys already have a bug and patch available:

[http://bugzilla.gnome.org/show_bug.cgi?id=314800](http://bugzilla.gnome.org/show_bug.cgi?id=314800)

---

### Post by tracerbullet on 2009-04-30
> **f0ku5 said:**
> The GNOME guys already have a bug and patch available:

[http://bugzilla.gnome.org/show_bug.cgi?id=314800](http://bugzilla.gnome.org/show_bug.cgi?id=314800)

From what I can tell this has been committed to the next release? Then I suppose it's just a matter of time before this fix hits my desktop. :D

At this point I'm just going to butter on a little more patience, as I don't feel like cracking open the guts of my OS and potentially break everything. :lolflag:

---

