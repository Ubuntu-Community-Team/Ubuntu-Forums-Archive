---
title: "Using emerald window decorator with Ubuntu 11.04"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by 6x9 on 2011-04-29
I've just upgraded from 10.10 to 11.04 and I noticed that my emerald themes no longer work. I've tried using 'emerald --replace' and all my window decorations disappeared :(. How do I get emerald to work again?

---

### Post by Light Knight 22 on 2011-04-29
I'm having the same problem. I've trying messing around with Compiz Settings and still no luck. Maybe Unity and Emerald aren't compatible (yet)?

---

### Post by beew on 2011-04-29
Emerald doesn't work in 11.04 because it doesn't work with the new version of Compiz. There is however a work around if you build it from git.
[URL="http://ubuntuforums.org/showthread.php?t=1702253"]
http://ubuntuforums.org/showthread.php?t=1702253[/URL]

---

### Post by Leed on 2011-04-29
Having the same problem, a real pitty, because because the standard window decoration are just not state of the art, not even close, they look cheap, have no transparency, are hard to adjust etc.

Build... hm, no point having a version in the repos that doesn't work... and I really try to avoid using self built stuff, especially if it need tweaking before build. 

Hope Canonical gets a working build into the repos soon. I can't understand why it's not in per default anyway, after all Ubuntu is supposed to be there to impress Linux newcomers... if the windows look worse than in Windows 7 most people won't switch to Linux, because the other system looks "more pretty".

---

### Post by OzzyFrank on 2011-05-20
As beew said, you can recompile Emerald quite easily - I have Emerald running a treat right now. And while I don't really think Emerald themes make Ubuntu more attractive to Windows users (especially since no default install of Ubuntu ever had Emerald in it), you can always add more window border themes by changing the GTK+/Metacity theme currently in use.

Many of these are as awesome of Emerald ones, minus the blur/glow and transparency. If you don't want to bother yourself with compiling Emerald, I would do some Googling on how to change your GTK+/Metacity themes (basically, open System > Preferences > Appearance and drag and drop themes you've downloaded on it - couldn't be simpler!).

---

### Post by OzzyFrank on 2011-05-21
Oh, and I wouldn't sit there waiting for a compatible version of Emerald to magically appear in the repos - Emerald is now a dead project, so that just isn't going to happen (its successor is apparently called Jasper). Your best bet is to compile, which is as easy as following the guide.

---

