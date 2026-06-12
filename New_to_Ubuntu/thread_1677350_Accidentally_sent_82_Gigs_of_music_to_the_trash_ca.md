---
title: "Accidentally sent 82 Gigs of music to the trash can"
date: 2011-01-28
forum: New to Ubuntu
---

### Post by asuastrophysics on 2011-01-28
Hey guys, 

While trying to figure out why my computer wasn't sharing music, I accidentally right-clicked the music folder and hit "send to trash" while running nautilus in root mode. 

The trash can says it's empty. I didn't empty it though. How do I access the "root" trash can? I'm guessing that's where it was moved to.

---

### Post by realzippy on 2011-01-28
When deleting something as root,the trash folder gets created under

/root/.local/share/Trash

...but 82 GB?

---

### Post by asuastrophysics on 2011-01-28
I figured it out. There is no way to restore it from the trash can's location. I had to enable the root account, log in, go to the root trash can, hit restore, and then log back out. Fixed it. My music is now back.

I think under Ubuntu Brainstorms, I'm going to suggest that they add an "are you sure?" dialogue box for deleting folders that big. The lesson here is, if you accidentally send a file/folder to the trash can while running the nautilus process as a different user, you must log in as that user and go to the trash can to restore it. 

But I can't figure out why samba isn't sharing files right now. That's what led me to accidentally delete it in the first place. In network, I see my shared folders, but no other computers see them.
^^EDIT: Figured that out as well. Restart fixed it.

---

