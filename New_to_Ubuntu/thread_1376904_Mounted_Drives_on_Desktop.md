---
title: "Mounted Drives on Desktop"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by ovid9 on 2010-01-09
Ok, so I finally am getting around to get my various drives all partitioned correctly and such.    I'm using Hardy 8.04.  

My main drive is a 640gig WD caviar green.  It is now in 3 paritions.  

The first partition is used by both users.
The 2nd partition is used just by me (admin/root main user).
The 3rd partition holds music shared by both users.

Permissions are all setup correctly for the various users, but how do I get partition 2 to not show up on the desktop when user #2 is logged in?

They can't use it, it doesn't need to be cluttering up space.  

There's probably some simple way to do this I just haven't found, but...any ideas?

---

### Post by marco123 on 2010-01-09
Press Alt+F2 and type:

> gconf-editor

Go to Apps>Nautilus>Desktop and uncheck "Volumes Visible"

---

### Post by ovid9 on 2010-01-09
And it was simple.  Wow, there's so much cool stuff built into Ubuntu that I don't know ANYTHING about.  

Thank you so much!  Less desktop clutter woo hoo! :)

---

### Post by marco123 on 2010-01-09
> **ovid9 said:**
> And it was simple.  Wow, there's so much cool stuff built into Ubuntu that I don't know ANYTHING about.  

Thank you so much!  Less desktop clutter woo hoo! :)

No problem.  Enjoy Ubuntu!:D

---

