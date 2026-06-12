---
title: "terminal, copy and pasting?"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by coops351 on 2009-03-28
how do you use the copy and paste commands in the terminal, because this is really starting to annoy me. i can't copy 1 folder into another 1, so i was wondering if the terminal can do this instead

if anyone can help me, and tell me what commands i need to use it would be most appreciated

cheers luke

---

### Post by bruno9779 on 2009-03-28
mv command does it.

If you can't handle the folder in a GUI way, it is most likely a permission problem.

here goes a link to command tutorials

[http://beginnerlinuxtutorial.com/help-tutorials/basic-linux-commands/](http://beginnerlinuxtutorial.com/help-tutorials/basic-linux-commands/)

alternatively you can open a terminal and type:

sudo nautilus

this starts nautilus with root privileges

---

### Post by fixitdude on 2009-03-28
kfmclient openProfile filemanagement

I love that thing, it seems like they decided to make things hard and take that out as a default way to do file stuff, make a icon for it on your desktop/toolbar or something. I don't understand this lame behavior by ubuntu developers and I'm getting tired of it being a problem every time you do a full upgrade. I understand the geeks wanting to do keyboard crap so they feel empowered, but as a high and low level programmer and a total geek, I would rather let the technology do the work so I don't have to, isn't that the point of all this?

As for terminal, the "cp" command has a lot of options to copy recursively or "archive" mode.

man cp

And when you said copy/paste in terminal it's a center click on the mouse that pastes ONE OF the clipboards. You figure it out by messing with it.

---

### Post by mvalviar on 2009-03-28
On a side note its ```
gksudo nautilus
``` to open a file browser with root access. Use it with care. Close it immediately afterwards.

---

### Post by bruno9779 on 2009-03-28
> **mvalviar said:**
> On a side note its ```
gksudo nautilus
``` to open a file browser with root access. Use it with care. Close it immediately afterwards.

You are right... shame on me

---

