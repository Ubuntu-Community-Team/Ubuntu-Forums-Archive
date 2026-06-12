---
title: "I've broken Thunderbird"
date: 2011-07-21
forum: New to Ubuntu
---

### Post by jermza on 2011-07-21
I've installed and uninstalled Thunderbird a few times.  I first installed TB and Lightning, and it was fine.  Then, I got enticed by a thread about TB5, so I upgraded to that (using Terminal), only to find a few things not working.  I didn't know how to revert to 3.1, so I removed everything from Ubuntu.  I then installed it again, but now Lightning doesn't work.  (See attchments.)

I don't know what to do.

HOw do I completely remove all of it and re-install it again?  I tried doing that via Synaptic, but every time I re-install TB, it remembers my plugins and settings, so it's obviously not removing everything.

---

### Post by oldos2er on 2011-07-21
In Synaptic you need to select 'Completely remove' for all your settings etc. to be removed, or in terminal ```
sudo apt-get purge thunderbird
```
All your mail will be deleted. If you want to save it, first run ```
cp -R .thunderbird/ mail.backup
```

---

