---
title: "using - in a commandline"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by NormR2 on 2009-03-18
Is - a special character for bash?
When enterting the following commandline, it is split into parts and I get a page of error messages from bash:

java -cp .. Vista.MyPgm


How can I preserve the full text of this commandline, ie not have bash use the - or the ..?

Thanks,
Norm

---

### Post by carml on 2009-03-18
Maybe there a space not needed,tri java-cp(followByYourSelf).

---

### Post by Eisenwinter on 2009-03-18
You enquote the text.

java "my parameters go here"

---

### Post by NormR2 on 2009-03-18
Thanks, I'll give it a try.

---

