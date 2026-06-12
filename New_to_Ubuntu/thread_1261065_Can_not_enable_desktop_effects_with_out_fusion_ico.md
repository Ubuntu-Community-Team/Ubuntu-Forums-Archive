---
title: "Can not enable desktop effects with out fusion icon"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by slughappy1 on 2009-09-08
I made the mistake of clicking on none in Appearance -> Visual Effects, and now if I try and click Normal it says that it can not enable desktop effects. Even though it CAN! It is quite annoying and I can not seem to figure out why it is doing that. 

I have an Intel GM965 btw. I have tried to take it off the blacklist, but it was already commented out. I know that it works. All I need to do is start fusion-icon and everything works. If I don't have fusion-icon running, I have no beautiful eye candy. But there is the problem, I do not want to have to have fusion-icon running.

---

### Post by ashwinhgtx on 2009-09-08
Try a reboot. It fixed the problem when I had it.

---

### Post by slughappy1 on 2009-09-08
Already tried that

---

### Post by CatKiller on 2009-09-08
The most common reason I've seen for effects not being enabled when they *can* be enabled is because the /apps/metacity/general/compositing_manager is set in gconf-editor.

---

