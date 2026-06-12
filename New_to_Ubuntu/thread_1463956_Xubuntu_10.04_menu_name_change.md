---
title: "Xubuntu 10.04 menu name change"
date: 2010-04-27
forum: New to Ubuntu
---

### Post by mesmith on 2010-04-27
I want to do something that ought to be fairly simple, but doesn't appear to be.  I want to change the name of a program that appears in my Applications/Office menu structure from "OpenOffice.org Word Processor" to "OO Word Processor."  No big deal, but it seems very complicated.  Any help?

---

### Post by -humanaut- on 2010-04-27
It's honestly more difficult then it should be you'll have to create a applications.gtkrc-2.0 and make your own menu's list I can help you create it if you want?

---

### Post by anewguy on 2010-04-27
I don't know how different xubuntu is from regular Ubuntu, but with regular Ubuntu you can just select the main menu editor, go to the item, click properties and change the name - simple.  *IF* xubuntu has a main menu editor somewhere I would think it would be equaly as easy.

Dave ;)

---

### Post by mesmith on 2010-04-27
Everything I've seen says it's a bitch in Xubuntu.  I'll learn to love what I have.

Thanks,

---

### Post by rayraven on 2010-04-27
> **mesmith said:**
> Everything I've seen says it's a bitch in Xubuntu.  I'll learn to love what I have.

Thanks,

It's not really so complicated. But, it involves some manual work.

Go to the folder:
```
/usr/share/applications
```

Find the app you want to rename, and open the file in mousepad.
Find an entry that says "Name" and change the text to what you want.

I haven't really used Xfce recently, so i don;t remember if it takes effect immediately. But a re-login should definitely make it take effect.

Do note that upgrades to the app will change the names back to what is in the package.

Xfce 4.6 moved to a new menu library, so there's no menu editor for it. Xfce 4.8 should come with one, i think.

---

### Post by mesmith on 2010-04-27
Thanks.  That does look simple.  Can live with a redo after updates.  Merci.

---

