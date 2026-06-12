---
title: "Can I make the space wallpaper in Lucid, remain the same and not change?"
date: 2010-07-14
forum: New to Ubuntu
---

### Post by mikodo on 2010-07-14
I really like the Space Wallpaper that comes with the Lucid release. I especially like, the one of the whole planet earth on the black background! I would like the wallpaper to remain at just one scene for as long as I would like. Then change it to another for a while, without it changing to the other space scenes by itself, so quickly.

Is there a way that this can be done?

Thanks,

Mike

---

### Post by Yarui on 2010-07-14
There is a utility in synaptic called wallpaper-tray that rotates wallpapers for you.  I have never used it but I have seen it recommended several times, so it's probably worth checking out.

---

### Post by fooman on 2010-07-14
right-click on desktop > choose: change desktop background...click the add button

in the box that pops up,  browse to: file system > usr > share > backgrounds > cosmos

find the one you like and click open.

edit:  sorry,  i misread and thought you just wanted it to stay at one background.

---

### Post by marshmallow1304 on 2010-07-14
Open up /usr/share/backgrounds/cosmos in nautilus and drag the image you want into the background selection panel.

---

### Post by Zimmer on 2010-07-14
go to usr/share/backgrounds/cosmos

you will need to edit background-1.xml

(as it is owned by root I suggest you start at the Termnal and try gksudo nautilus to open the file browser as root before you start trying to edit the file...)

Change the 
<static>
<duration>1795.0</duration>

entries to a higher figure of your choice...

Or, if you like the earth picture as a permanent background then just add it, now you know where to find it :)

---

### Post by philinux on 2010-07-14
> **marshmallow1304 said:**
> Open up /usr/share/backgrounds/cosmos in nautilus and drag the image you want into the background selection panel.

In that folder should also be the html file that drives it. You can change the delay interval.

---

### Post by mikodo on 2010-07-14
> **marshmallow1304 said:**
> Open up /usr/share/backgrounds/cosmos in nautilus and drag the image you want into the background selection panel.
Brilliant!

Thanks,

Mike

---

### Post by mikodo on 2010-07-14
> **fooman said:**
> right-click on desktop > choose: change desktop background...click the add button

in the box that pops up,  browse to: file system > usr > share > backgrounds > cosmos

find the one you like and click open.

edit:  sorry,  i misread and thought you just wanted it to stay at one background.
No you didn't misread. Thanks for the advice.

Mike

---

### Post by mikodo on 2010-07-14
Thanks everyone; by the way!

Mike:D

---

