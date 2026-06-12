---
title: "Using Swiftfox, safe to remove Firefox and dependancies?"
date: 2010-03-08
forum: New to Ubuntu
---

### Post by JerichoKru on 2010-03-08
I'm using 3.6 of Swiftfox right now (It loads pages faster than normal FF), and I'd like to remove the normal Firefox.  When doing so, it wants to remove these as well:

```
firefox-3.0
firefox-3.5
firefox-3.5-branding
firefox-3.5-gnome-support
firefox-branding
firefox-gnome-support
ubufox
```

Would it be safe to remove?  Will any of these mess up Swiftfox if removed?


I noticed the ubufox description...what exactly does that do?

---

### Post by MelDJ on 2010-03-08
ubufox is an addon for firefox. i would recommend you leave the normal firefox.

---

### Post by JerichoKru on 2010-03-08
> **MelDJ said:**
> ubufox is an addon for firefox. i would recommend you leave the normal firefox.

I think I'll leave it, since flash doesn't work correctly in swiftfox anyway.

---

### Post by mister_playboy on 2010-03-08
I also use a Firefox 3.6 binary rather than the inbuilt Firefox (3.0 since I'm still on 9.04).  I recommend leaving the packages alone to avoid messing things up.

It took me a long time before I could figure out which of the half dozen or so potential plugin locations my binary FF was looking at so I could get Flash to work.  I ended up just copying libflashplayer.so to each location I found, and it eventually worked!  Everything else (history, extensions, passwords) seems to be shared between your Firefoxes without having to do any work.

---

