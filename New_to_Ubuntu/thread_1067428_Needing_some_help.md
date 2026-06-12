---
title: "Needing some help"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by Zom-b on 2009-02-11
I have been having a problem with simdock. I was messing around with the settings to see what different changest did, and one of the things I changed caused it to stop working properly, when I open it now it takes up the whole leftside of the screen, and I can't change the settings anymore, so I was wondering if there was a way to reset a program or some help with this paticular issue.

---

### Post by snova on 2009-02-11
Open Places -> Home directory, enable hidden files (Ctrl-H), and remove the .SimDock directory. That should reset its settings.

---

### Post by Zom-b on 2009-02-11
I tried that and, opened it up, same thing.

---

### Post by snova on 2009-02-11
Open Nautilus again, browse to **.gconf/apps/simdock**, and try removing the **%gconf.xml** file.

If that doesn't reset it, I can't imagine where it's storing its settings.

(And, just in case, make sure you exit SimDock first...)

---

### Post by Zom-b on 2009-02-11
hehe, yeah I have been having to xkill or pkill simdock because of the way it's been acting. I removed the %gconf.xml file and that also didn't help, I will try restarting my computer really quick to see if that makes a difference.

---

### Post by Zom-b on 2009-02-11
alright, restarting did the trick, thanks for you help, just need to figure out if I can make simdock look remotely nice lol, do you know any alternatives that are better by chance?

---

### Post by snova on 2009-02-11
> **Zom-b said:**
> do you know any alternatives that are better by chance?

Try AWN (Avant Window Navigator), Cairo Dock, Gnome Do...

---

### Post by Zom-b on 2009-02-11
Yeah, thanks again for helping me out, but the more I am messing with this Simdock, the more I don't like it, it definatly doesn't mesh well with anything, and I can't move it anywhere but where it starts:-?

---

