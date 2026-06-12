---
title: "Sounds problems"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by winjeel on 2009-07-24
I'm running Jaunty Jackalope on a Dell Latitude D520 (purchased in Japan). Everything else is working fine. The sound system works well, I can mute and turn up and down the sound. However, just two exceptions, when I receive mail it goes beep, and when I shut down it goes beep-beep-screech, both loudly, and even if the sound is turned really low or muted. Is there some setting hidden away somewhere that I can use to fix these two exceptions? I made a colleague jump out of her skin the other day when I went to shut down my computer; it is the only annoying thing I can say about Jaunty.


(Just gone to Preferences in Mail and turned off "Play Sound" for when mail arrives, but it still goes "beep")

---

### Post by stoogiebuncho on 2009-07-25
This is a bug in Jaunty that has not been fixed yet.

There's a few things to try.

Some people say that going to System > Preferences > Power Management > General > Extras and unchecking "Use sound to notify in event of an error" fixes it for them.  It did not for me.

Some people say opening up the CompizConfig Settings Manager (if you're using it) and going to General > General Options and unchecking "Audible Bell" does the trick.  This did not work for me either.

What I ended up doing was blacklisting the speaker.  I opened the blacklist file:

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```

scrolled down to the bottom and entered

```
# Blacklist the PC Speaker
blacklist pcspkr
```

Save and restart (it will still beep when you restart, but after that it should quit).

---

### Post by jbrown96 on 2009-07-25
In system-->preferences-->sound there should be an option to disable the system beep. I'm not sure if that will solve the shutdown sound. You may need to switch all your output settings to ALSA. Reboot then run ```
alsamixer
``` and there should be a "beep" channel use the arrows to select it then press m to mute it, esc to exit.

---

### Post by winjeel on 2009-07-25
Thanks. I'm working on something at the moment, and so I'll try it (and maybe the others) later. Thanks again for your time. :D

---

