---
title: "delete desktop icon"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by atheosun on 2010-05-28
Hey guys,

I somehow copied the "system reserved" icon on to my desktop and now cannot delete it.

Could some kind person show me how to do it? :confused:

Many thanks,

John

---

### Post by RiceMonster on 2010-05-28
I'm guessing you mounted part of your windows file system. Try right click > umount and see what happens.

---

### Post by atheosun on 2010-05-28
Wow fast response RiceMonster. Kudos!

I just got rid of it by typing:

gconf-editor

then browsing to:

apps \ nautilus \ desktop

and i unchecked volumes_visible


Your way probably was quicker and if it happens again i will be sure to try it.:P

Edit: just tried to unmount it there and it worked a treat. Cheers!

---

