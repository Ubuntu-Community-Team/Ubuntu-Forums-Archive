---
title: "Ubuntu menu bar help"
date: 2011-02-08
forum: New to Ubuntu
---

### Post by hunter99507 on 2011-02-08
I am running ubuntu 10.04 and i have a question.  Often the menu bar on all programs dissapears.  The menu bar that is on every application (Close app, minimize, and maximize)  Sometimes when ubuntu boots up it shows, and other times it doesnt.  How can i fix this problem?  I know i can restart gnome, but how can i do a perminit fix?  Thanks

---

### Post by wojox on 2011-02-08
If your using compiz or kwin disable it and try.

---

### Post by Tiberion on 2011-02-08
well i am not sure why it is disappearing but to bring it back open terminal and try killall gnome-panel at least this might get your panel back

---

### Post by hunter99507 on 2011-02-08
How do I disable it?

---

### Post by Tiberion on 2011-02-08
you can uninstall it by in terminal sudo apt-get autoremove compiz or open synaptic and search for compiz

---

### Post by hunter99507 on 2011-02-08
[IMG]file:///tmp/moz-screenshot-2.jpg[/IMG]The kill gnome didnt work. Here is a screenshot of calculator to show my issue.

[IMG]file:///tmp/moz-screenshot.jpg[/IMG][IMG]file:///tmp/moz-screenshot-1.jpg[/IMG]

---

### Post by Tiberion on 2011-02-08
I haven't come across that.  I noticed the apple in the top left corner.  I haven't seen that in Ubuntu on a tool bar.  I misunderstood your original post sorry.

---

### Post by Tiberion on 2011-02-08
Try this 

[http://www.pendrivelinux.com/ubuntu-desktop-effects-fixing-the-missing-titlebar/](http://www.pendrivelinux.com/ubuntu-desktop-effects-fixing-the-missing-titlebar/)

according to the text this will fix the compiz bug.

---

### Post by wojox on 2011-02-08
> **hunter99507 said:**
> How do I disable it?

Go to System > Preferences > Appearance > Visual Effect > None

---

### Post by hunter99507 on 2011-02-08
I am not sure if any of those suggestions work because i just restarted ubuntu and now it works fine.  Ill make sure and try these suggestions next time this issue happens

---

### Post by Tiberion on 2011-02-08
I agree with wojox that this is a compiz issue and it will repeat hopefully one of our suggestions will help.  Good Luck!!


If you are satisfied please mark this thread as solved

---

### Post by wojox on 2011-02-08
If you have compiz installed, install compizconfig-settings-manager and turn on Window Decorations.

---

