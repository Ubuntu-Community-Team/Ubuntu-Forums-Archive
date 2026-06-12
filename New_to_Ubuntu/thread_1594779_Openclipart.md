---
title: "Openclipart"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by Inisfad on 2010-10-12
Well, this is the place for absolute beginner talk, and here I am.  I'm running Ubuntu 9.04 and I just downloaded Openclipart from the repositories and......where is it?  I cannot find this indicated anywhere!  :confused:  I have looked in every file, tried to search for it, etc., and just can't understand how to access it.  Can't you open this and browse through the pictures?  I have a headache......Thanks for any help you can give.

---

### Post by yetiman64 on 2010-10-12
Go to System > Administration > Synaptic Package Manager, type openclipart in the search box, highlight the package in the main window, right click it and select Properties > Installed Files. Check in /usr/share/openclipart folder for svg and png folders holding artwork (this path is for Maverick 10.10 - might be the same for you).
A list of all files and their path are in this window. This will give you an idea of what folders to navigate to to use the clipart.

Edit: the openclipart package is a metapackage only (draws in openclipart-png and openclipart-svg), you may have to check these 2 extra packages for the actual artwork, if it's the same in Jaunty

---

### Post by davidmohammed on 2010-10-12
from open-office wordprocessor choose "Tools - Gallery".  For me, all the clip-art from "openclipart" was displayed there.

---

### Post by yetiman64 on 2010-10-12
> **davidmohammed said:**
> from open-office wordprocessor choose "Tools - Gallery".  For me, all the clip-art from "openclipart" was displayed there.

@ davidmohammed, Wow, I didn't realize that was there (should've guessed so though), very handy, thanks :)

---

### Post by Inisfad on 2010-10-12
Wow, thanks. I found it both ways!  So, can I take this one step further (ok, maybe 2...) How do I import one of the clipart graphics into Scribus?  And is there anyway of putting a clipart icon on my desktop (ok, so kind of like windows...) so I can browse through the graphics?  Thanks!

---

### Post by yetiman64 on 2010-10-12
For a link to the main openclipart folder on the Desktop. In a terminal,
```
ln -s /usr/share/openclipart ~/Desktop/openclipart
```If you want a link to the subfolders use the above and alter both the paths in the code above to suit your needs. Note the links on the Desktop will have a lock symbol on them, this is because you are linking to a folder owned by root.

---

### Post by Inisfad on 2010-10-12
Thanks.  I was able to get my clipart into my Scribus card, so I've got my answer for that, as well.  Gee, it only took me about 6 hours to make this birthday card (this is a learning process).  Probably would have been faster just to go to the store......Thanks again

---

### Post by yetiman64 on 2010-10-12
edit: never mind you have marked the thread. cheers

---

