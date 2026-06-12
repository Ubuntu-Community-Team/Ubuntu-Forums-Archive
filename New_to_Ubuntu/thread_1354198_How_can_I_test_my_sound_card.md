---
title: "How can I test my sound card?"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by dizzy1kenobi on 2009-12-13
I have been through the preferences tab and the machine is not muted.

I have no sound in YouTube, VLC, or Audacious.

This happened last nite after my external HD got unplugged while a movie was playing. My PC couldn't find the HD so a did a restart but the shutdown froze and I had to manually turn it off.

I don't know if the 2 things are related but they may be.

---

### Post by lidex on 2009-12-13
Try this command in a terminal:
```
sudo lshw -C sound
```
Find a terminal in Accessories menu.

---

