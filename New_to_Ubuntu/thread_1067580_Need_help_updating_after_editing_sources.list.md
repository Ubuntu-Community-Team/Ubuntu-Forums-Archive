---
title: "Need help updating after editing sources.list"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by MrTumour on 2009-02-12
I want to install xmms. I found the site where it was stored and added the the relevant lines to my sources.list. I am at a loss of what do next, i've tried updating but it won't do anything.

---

### Post by lswest on 2009-02-12
```
sudo apt-get update
sudo apt-get install xmms
```

Not sure if xmms is still in active development, xmms2 is in the ubuntu repositories (admittedly, I've never spent any time trying to get it to work, so I have no idea if it's better or worse than xmms).

---

### Post by MrTumour on 2009-02-12
From what I understand they removed xmms from the repos because xmms2 is supposed to be better. I can't get xmms2 to work so I decided to get xmms. If xmms isn't the repos will sudo apt get work?

Edit: Thanks it worked.

---

### Post by lswest on 2009-02-12
No problem, glad it works.  Yeah, not sure about xmms2, I use Banshee on my Ubuntu system and XMMS on my ArchLinux laptop system, but that's still in the arch repos.

---

