---
title: "Banshee Question/Issue"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by mtangoo on 2011-05-05
I regard RB as great media player and Ubuntu is dropping it...sad. Anyway, Banshee is great too but I have issues with it if I manage to fix I will shift to them as default player (though I will keep my RB).
1. How do I watch more than one folder. In RB is as easy as invoking gconf-edit and add it
2. How do I stop banshee from "organizing" my media by moving them in different folder? I want my folders to remain intact with their media and I don't like banshee telling me where to put them!
3. Can I scan downloaded media from GPodder so that it will not re-download my thousands of podcasts that are already there? (Even RB failed here)

Thanks!:P

---

### Post by mtangoo on 2011-05-07
Any help?

---

### Post by Paqman on 2011-05-07
You don't *have* to use Banshee. Rhythmbox is still in the repos, you can install it in a couple of clicks.

---

### Post by Elfy on 2011-05-07
1 - use symlinks. ```
ln -s /path/to/real/file /path/to/non-existant/file
```

Alternatively use some other media player that allows multiple libraries.

2 - I don't use banshee (mostly because of the media library issue, but I thought there was an option for this.

3 - no idea - try searching the forum, I'd not use the forum search facility which is lacking. Try a custom search engine like [googlbuntu]("http://www.googlubuntu.com/")

---

### Post by mtangoo on 2011-05-07
Thanks for reply. Can I symlink the whole folder? How symlinking work? Trick the player?
I think I will have keep RB though I cannot find how to migrate my podcasts too!

---

