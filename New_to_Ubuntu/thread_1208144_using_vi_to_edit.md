---
title: "using vi to edit"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by sctb082552 on 2009-07-08
I am following the setup guide for a lamp server. I am at the part where they want me to edit a file using the "[COLOR="Red"]sudo vi /etc/network/interfaces[/COLOR]"  now the deal is this. I am able to ad the lines necessary to modify and change the the interfaces configuration file. The problem is, [COLOR="Red"]HOW DO YOU SAVE AND EXIT[/COLOR] back to the terminal? all I am able to do is restart my computer then it tells me there is a swp or duplicate file.

Thanks for any help.

confused in texas:confused::confused::confused:

---

### Post by amauk on 2009-07-08
```
:wq
```

---

### Post by aysiu on 2009-07-08
This is why I use nano instead of vi.

---

### Post by amauk on 2009-07-08
> **aysiu said:**
> This is why I use nano instead of vi.Aaagghh, heretic !!!

:p

---

### Post by lavinog on 2009-07-08
haha, I saw the word vi in the absolute beginners section and thought...oh no.

For future reference, you may find substituting nano for vi to be easier. vi is powerful but not really friendly to new users. nano tends to act more like a simple text editor.
use ctrl-x to exit (if there were changes it will ask if you want to save)

---

### Post by sctb082552 on 2009-07-08
Thanks for the replys, the first replys were I'd say confusing but you followed up with all the questions my mind created answered.

Thanks again.

Some of the step by step guides to doing things in ubuntu are great but they fall short when they start you in a process and do not tell you how to exit or complete the command. I wish they would remember when writing these guides that it is a beginner that is reading it.:lolflag:

---

### Post by sctb082552 on 2009-07-08
thanks lavinog, your reply was very informative.

---

