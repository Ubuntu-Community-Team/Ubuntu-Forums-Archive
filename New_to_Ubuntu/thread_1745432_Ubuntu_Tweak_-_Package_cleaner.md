---
title: "Ubuntu Tweak - Package cleaner"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by Baldrick_NZ on 2011-05-01
Just before I embark on a package clean-up, I was wondering how safe is it to clean config and cahce using ubuntu Tweak.

Are there files that I should avoid deleting, or can I trust that Ubuntu Tweak knows which ones are safe to clean up?

I have backed up my files just incase, but really don't want to be troubled with a restore if I don't need to.

Any help would be much appreciated.

---

### Post by K_45 on 2011-05-01
Just run

```
sudo apt-get autoremove
```

which will clean out old packages.

---

### Post by Baldrick_NZ on 2011-05-01
> **K_45 said:**
> Just run

```
sudo apt-get autoremove
```

which will clean out old packages.

Thanks for that. But what about the cache and config?

Tried autoremove, but the clean config and clean cache options are still requiring a clean.

---

### Post by Baldrick_NZ on 2011-05-01
Under cache, it looks as if there are some pretty important system files in there, and when I check synaptic, they are identical to those in the cache.

Would the ones in the cache refer to a previous kernel, or maybe Tweak has added them by mistake?

There areover 100 objects in the cache, and it would be good to clean it out - if it's safe to do so.

Any ideas?

Cheers.

---

### Post by ngubk on 2011-05-01
Yes, ubuntu tweak is convenient to me. but i suggest you use Bleachbit as a Ubuntu Cleaner. I've been using it for over 1 years and it shows no problem

---

### Post by oldos2er on 2011-05-01
*apt-get autoremove* removes packages that were automatically installed to satisfy dependencies for some packages that are no longer needed.

*apt-get clean* clears the cache (/var/cache/apt/archives).

---

### Post by rburkartjo on 2011-05-01
yes bleachbit is a great cleaner app

---

### Post by el_koraco on 2011-05-01
You can clean the cache if you want to, running out of space and such. Config files are filess for applications you had, but uninstalled. If you install them again, they will have the same configuration as they did when you first had them. Don't see a need for removing them.

---

### Post by Frogs Hair on 2011-05-01
In the Synaptic Package Manager select Settings > Preferences > Files . From there you can set to delete packages after installation . This also helps with cleanup .

---

### Post by wilee-nilee on 2011-05-01
I use the tweak to clear everything I can, but I'm a experienced user, never had a problem, and if I did and I can't fix it right away I insert the clone of it takes about 5-10 minutes.

I also do this a auto-install list of your setup, isn't this cool.;)
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

---

### Post by Baldrick_NZ on 2011-05-03
> **oldos2er said:**
> *apt-get autoremove* removes packages that were automatically installed to satisfy dependencies for some packages that are no longer needed.

*apt-get clean* clears the cache (/var/cache/apt/archives).

Sorted. Thanks all for your help, much appreciated!

---

