---
title: "Cleaning the cache and trash"
date: 2011-03-04
forum: New to Ubuntu
---

### Post by erelsgl on 2011-03-04
I found out that the folders "~/.cache" and "~/.local/share/.Trash" take a lot of disk space. Is it safe to delete their contents?

---

### Post by mcduck on 2011-03-04
Deleting the files in ~/.local/share/Trash would be the same as just right-clicking the trash bin icon and selecting to empty it. So yes, that's safe.

Cleaning the ~/.cache is safe as well, although doesn't make lots of difference in the long run (and probably just slows some things down for a while as programs need to generate the same content again into cache). Of course you might have some cached content that isn't used any more and cleaning the ~/.cache would help getting rid of those and save you a little bit of disk space.

So yes, by all means, empty your trash bin. :D And if deleting stuff from ~/.cache makes sense or not pretty much depends on how large it actually is, if it's in normal limits then deleting stuff doesn't make much sense, if it's grown to insanely large size for some strange reason then cleaning it would be a good action. Hard to say as you didn't mention how much space it's actually taking...

---

### Post by Paddy Landau on 2011-03-04
If you have a modern computer (with a large disk), then you can safely ignore the cache. I have found that Linux has an excellent disk management. I have never cleared my ~/.cache and it contains a mere 86Mb.

I also have a very old computer with a tiny disk, just 14Gb, and I have no problems with its disk space.

However, you can regularly empty your rubbish bin just as the previous poster said. That is probably a good idea.

---

### Post by fooman on 2011-03-04
i use bleachbit to clean things up once in awhile....it has many options to clean,  among which you will find system cache and trash.

bleachbit is in the repos and can be installed from the ubuntu software center or synaptic.

---

### Post by erelsgl on 2011-03-04
Thanks!

My cache grew to above 600 MB, and I wanted to backup my entire home folder, so I thought it would be better to delete it beforehand.

---

### Post by Frogs Hair on 2011-03-04
Another built in  option is to go to Synaptic Package Manager > Settings > Preferences > Files tab and check delete downloaded packages after installation.

---

### Post by Paddy Landau on 2011-03-04
> **Frogs Hair said:**
> Another built in  option is to go to Synaptic Package Manager > Settings > Preferences > Files tab and check delete downloaded packages after installation.
That won't affect the home folder, though.

---

### Post by wojox on 2011-03-04
> **fooman said:**
> i use bleachbit to clean things up once in awhile....it has many options to clean,  among which you will find system cache and trash.

bleachbit is in the repos and can be installed from the ubuntu software center or synaptic.

+1 Bleachbit rocks. On a fresh install I cleaned out 1.2 GB of stuff.

---

