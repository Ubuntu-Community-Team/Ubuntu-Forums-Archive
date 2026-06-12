---
title: "Browsing directories with blank spaces in console"
date: 2010-01-14
forum: New to Ubuntu
---

### Post by am65 on 2010-01-14
I have a directory with name "Ubuntu One". I would like to view its contents from the console. That is:

>cd Ubuntu One

I have tried also

>cd Ubuntu%20One

but is is not working. How can I change to this folder in a console?

Thanks

---

### Post by lisati on 2010-01-14
Putting "\" before the space sometimes helps. Try: ```
cd Ubuntu\ One
```

---

### Post by marshmallow1304 on 2010-01-14
> **lisati said:**
> Putting "\" before the space sometimes helps. Try: ```
cd Ubuntu\ One
```
This.

Or put quotes around it
```
cd "Ubuntu One"
```


Tab completion makes it a lot easier.

---

### Post by am65 on 2010-01-14
Thanks for your help.

---

### Post by bodhi.zazen on 2010-01-14
I see this is solved, but perhaps the easiest way, with the least typing, is to use tab completion.

```
cd Ubun<tab>
```

---

