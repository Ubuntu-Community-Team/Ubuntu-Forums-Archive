---
title: "I need to get rid of this error message, can you help?"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by Chris Edgell on 2010-02-05
I had noticed this error message when I went to synaptic.  But now I got the same message when I went to install the 3 new updates.  

Can anyone tell me what exactly to run and where?

---

### Post by oldos2er on 2010-02-05
Open a terminal (Applications, Accessories, Terminal) and run ```
sudo dpkg --configure -a
```

---

### Post by Chris Edgell on 2010-02-06
Thank you so much...that did the trick.

---

### Post by oldos2er on 2010-02-06
You're welcome.

---

