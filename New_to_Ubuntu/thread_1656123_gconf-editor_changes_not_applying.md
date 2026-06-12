---
title: "gconf-editor changes not applying"
date: 2010-12-30
forum: New to Ubuntu
---

### Post by KlytusLord on 2010-12-30
Hello,

I run the gconf-editor using the sudo command in a terminal. When I make changes, they are not applied even after rebooting. When I check the gconf-editor again, the changes are still there, but they are having no effect. Please see the following screenshot.

[[IMG]http://img529.imageshack.us/img529/1356/screenshotsi.th.png[/IMG]](http://img529.imageshack.us/i/screenshotsi.png/)

As you can see in the screenshot, the options for displaying the desktop icons are selected, but the icons are not actually visible on the desktop. My Ubuntu release is 10.10, but this is also happening on my desktop, which is running 9.10

Thanks for any help with this.

---

### Post by Verbeck on 2010-12-30
> **KlytusLord said:**
> 
I run the gconf-editor using the sudo command in a terminal
that could be the problem. you should use it _without sudo_ (else the changes would be saved in /root, which doesn't have anything to do with the normal user)

---

### Post by KlytusLord on 2010-12-30
Thank you so much!

---

### Post by Verbeck on 2010-12-30
you're welcome

dont forget to mark the thread as 'Solved' from **[COLOR=Red]Thread Tools[/COLOR]** at the top

---

### Post by ajgreeny on 2010-12-30
And just in case it messes anything up, you might want to reverse the changes you made in the root gconf-editor.  It may not matter, depending on what they were, but better safe than sorry.

---

