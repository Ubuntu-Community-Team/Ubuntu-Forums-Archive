---
title: "can't change custom theme"
date: 2009-09-01
forum: New to Ubuntu
---

### Post by Xenomorph05 on 2009-09-01
I don't know why but i can not change parts of the Ubuntu theme. I tried to use rm -rf .gnome .gnome2 .gconf .gconfd .metacity but it didnt fix the problem. It looks like this: [http://img84.imageshack.us/img84/6624/helpf.png](http://img84.imageshack.us/img84/6624/helpf.png)

The black isn't suppose to be there at all! If this is a repost I'm sorry but I don't know how to find out how to fix it.

I was adding themes and playing with Compiz and emerald but even after removing them it's still like this.

---

### Post by Giant Speck on 2009-09-01
Have you tried going in and looking at the color settings?

System > Preferences > Appearance > Customize > Colors

[[IMG]http://i279.photobucket.com/albums/kk122/SpecKtacle/th_Screenshot-14.png[/IMG]](http://i279.photobucket.com/albums/kk122/SpecKtacle/Screenshot-14.png)

Also, please don't take this to sound condescending, but did you restart your computer (or at least logout and back in) after deleting those folders?

---

### Post by Xenomorph05 on 2009-09-01
I did a log out and log in which is why it looks funny. Its not so much the color that is messed up but the actually buttons and panels are stuck in the previous theme for some reason.

---

### Post by Xenomorph05 on 2009-09-02
I should mention that in the Change desktop background/theme/customize/controls that they are all the same! It looks like each different control color and design was replaced by the exact same one.

---

### Post by Xenomorph05 on 2009-09-02
It seems that every theme I pick in the Appearance Preferences are all bugged out or over written somehow. Is there a way to replace them or will I have to resort to a fresh install? I don't have a system back up installed...

---

### Post by Xenomorph05 on 2009-09-02
Alright then I managed to solve my own problem! I don't know why it happened in the fist place but here is how I solved it: sudo rm -rf /usr/share/themes/name_of_folder and removed the themes I added.

---

