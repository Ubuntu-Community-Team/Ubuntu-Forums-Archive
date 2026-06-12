---
title: "Ctrl + number key shortcut default function?"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by Confuseling on 2009-06-11
Hi. If I press Ctrl and a number key (1 - 4) something happens to my desktop icons (momentary loading, but apparently otherwise unaffected).

Having trouble googling what this does. (Compiz? I'm 90% sure I didn't set it myself...) Can anyone enlighten me?

---

### Post by nandemonai on 2009-06-13
Odd.. I was under the impression this key combo wasn't in use by default. I actually set Ctrl-1234567890 for tabs in gnome-terminal.

You could take a look in System -> Preferences -> Keyboard Shortcuts

---

### Post by Azrael3000 on 2009-06-13
interesting, happens to me too.
No entry in the Keyboard Shortcuts that would be related to that.

---

### Post by Confuseling on 2009-06-13
Thanks for the responses. I've narrowed it down (I think...) to compiz, insofar as "metacity --replace &" kills it dead.

Still no idea what's happening though...

---

### Post by Azrael3000 on 2009-06-14
I found out what it is I guess. Quite simple indeed :)

In Nautilus if you press Ctrl + 1 you get Icon view, for Ctrl + 2 you get List view and for Ctrl + 3 you get Compact view.
Now my suspicion is, that this also "works" on the desktop. However with the only difference that only Ctrl+1 is enabled. Now if I disable these Shortcuts, the flickering is gone, except for Ctrl+4 which I haven't found out yet what it does.

---

### Post by Confuseling on 2009-06-14
Puzzling that metacity stops it too, though. Perhaps just some unexpected interaction between the two. Not sure it's worth filing a bug over. Cheers!

---

### Post by pavloukos on 2009-11-10
Do you know how could I disable Ctrl+1,2,3?

---

