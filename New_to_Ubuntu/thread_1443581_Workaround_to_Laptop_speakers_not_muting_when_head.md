---
title: "Workaround to Laptop speakers not muting when headphones inserted"
date: 2010-03-31
forum: New to Ubuntu
---

### Post by lotharmat on 2010-03-31
**_[SIZE="4"]Background:[/SIZE]_**

On my laptop; when I plug my headphones into the socket, the sound keeps coming through the front speakers. This is a problem...

Upon looking in alsamixer (from the terminal) I saw that I could set the 'Speaker' volume to zero and this would have the effect of muting the front speakers whilst leaving the headphone level untouched. Muting the 'Speaker' also muted the headphones

**_[SIZE="4"]Solution:[/SIZE]_**
Not too elegant but hey

Create a new Keyboard shortcut (I use win+downarrow) to the following command
```
amixer sset Speaker 0
```
This takes the 'Speaker' volume to zero effectively muting the speakers

Create another shortcut (win+uparrow) but this time swap the 0 for 100

Hope this helps someone.

Ps the 'Speaker' is supposed to have a capital s!

---

### Post by Psumi on 2010-03-31
removing from unaswered

---

