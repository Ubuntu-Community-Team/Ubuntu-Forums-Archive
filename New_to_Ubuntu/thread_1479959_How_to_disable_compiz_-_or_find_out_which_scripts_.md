---
title: "How to disable compiz - or find out which scripts starts it"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by karatedog on 2010-05-11
I'm a GNOME user on the average (with Compiz + Emerald), but I recently turned to KDE. And my problem is that I cannot turn Compiz off.

I was a n00b when I set up Compiz, so I must have done it the ugliest way possible (which means I don't have the faintest idea where I put it). I tried every GUI tool available, then turned to console. All my searching was pointless, so the quiestion goes out for the experienced: How can I find out in which startup script I start Compiz?

I've tried KDE's composite settings, which is set to KWin, but still Compiz starts at login time (when those nice KDE system icons appear the Compiz Fusion logo covers them).

If I start KDE with another user, Compiz won't start so this script must be tied to the user session.
I have issued a full scale grep to my home/user folder, looking for "compiz" but no result. I took measures not to forget the directories that start with "."

Any idea where to look?

---

### Post by philinux on 2010-05-11
Why not just remove compiz.

Or 

```
metactity --replace
```

---

### Post by ankspo71 on 2010-05-11
Hi,
Do you have any start up application entries listed in: 
System Settings > Advanced (tab) > Autostart ?

The command to start compiz is
```
compiz --replace
```
Maybe you combined that command with another startup script?
Hope this helps.

---

### Post by howefield on 2010-05-11
Too many "t"s in there ;)

---

### Post by Zalbor on 2010-05-11
"metacity --replace" in kde either won't do anything or will "break" things. Try
```
kwin --replace
```

---

### Post by ankspo71 on 2010-05-11
I just remembered something.... Did you install fusion-icon?

If you did, it provides a way turn off compiz in your System Tray, and it might explain why you can't find a startup script for compiz somewhere.

---

### Post by karatedog on 2010-05-11
> **Zalbor said:**
> "metacity --replace" in kde either won't do anything or will "break" things. Try
```
kwin --replace
```

Thanks, that will surely work, however I think this is also an ugly solution. First Kwin starts, then my "compiz --replace" kicks in, then - at the end - another script does the "kwin --replace" job. That's why I was looking for the initial script that mixes up a clean startup.

---

### Post by karatedog on 2010-05-11
> **ankspo71 said:**
> I just remembered something.... Did you install fusion-icon?

If you did, it provides a way turn off compiz in your System Tray, and it might explain why you can't find a startup script for compiz somewhere.

No, it is not installed.

---

### Post by karatedog on 2010-05-11
After a lot of digging I found it.

/etc/X11/Xsession.d/25enable-compiz:
```
if [ -e $HOME/.kde/share/config/compizasWM ] && [ -e /usr/bin/compiz ] ; then
        export KDEWM="/usr/bin/compiz"
fi
```

Renaming the 'compizasWM' file solved the problem.

---

