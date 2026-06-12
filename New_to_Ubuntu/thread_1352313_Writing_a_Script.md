---
title: "Writing a Script"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by wizofozz on 2009-12-11
I am attempting to write a script that will download some files that are in a date format say like 20020904.jpg. How would I make it so it would download a whole month and then move onto the next month? Any help is truly appreciated.

Thank You

---

### Post by StOoZ on 2009-12-11
regular expression on the two digits of the month?

---

### Post by northern lights on 2009-12-11
```
cd /folder/where/the/pics/are
ls -a | grep 200209*
```

I don't really get what you mean by moving the pictures "onto the next month" after downloading, please elaborate, if the above isn't helpful [enough].

---

### Post by StOoZ on 2009-12-30
<removed by me>

---

