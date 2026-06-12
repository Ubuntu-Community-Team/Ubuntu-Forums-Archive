---
title: "how do change default .wine folder dirrectory?"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by klemperal on 2009-10-31
I would like to change the default .wine folder to wine (without the .) so that I don't risk forgetting to back.  That being said, is there a way to do this so that wine knows to look in my custom directory and won't just create another ".wine" folder?

---

### Post by Vaphell on 2009-10-31
create symbolic link
**ln -s .wine wine**

.wine will be there but wine will be its alias, which you can see and go into

---

