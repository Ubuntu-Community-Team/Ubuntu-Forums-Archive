---
title: "How to check the differences between 2 files, with a Percentage?"
date: 2010-02-28
forum: New to Ubuntu
---

### Post by frenchn00b on 2010-02-28
Hello, 

diff function permits to check the diff, and display the differences between 2 files.

I would like to check the difference between two files, and display them only if it is in percentage differences larger than 5 percent. Is that possible this thing?

---

### Post by Barriehie on 2010-02-28
> **frenchn00b said:**
> Hello, 

diff function permits to check the diff, and display the differences between 2 files.

I would like to check the difference between two files, and display them only if it is in percentage differences larger than 5 percent. Is that possible this thing?

Might have to be a bit more specific on the differences, size?, number of lines?, actual byte comparison?

---

### Post by frenchn00b on 2010-02-28
> **Barriehie said:**
> Might have to be a bit more specific on the differences, size?, number of lines?, actual byte comparison?

Well it is to wget a webpage every 1hour, and then use diff to check a value of percentage of difference. Well whatever difference may work, I guess, then it is how to set up with try n error procedure, no?

---

### Post by lisati on 2010-02-28
> **frenchn00b said:**
> Well it is to wget a webpage every 1hour, and then use diff to check a value of percentage of difference. Well whatever difference may work, I guess, then it is how to set up with try n error procedure, no?

It's probably do-able. I don't know of any current program that actually does this, but some time back I did have some code which did something similar with strings. (/me scratches head and tries to remember how the code worked)

---

### Post by DaithiF on 2010-02-28
Hi, measuring 'percentage change' is open to interpretation -- how exactly do you measure how different one file is from another.  If you're not looking for a particularly exact measurement, and therefore a rough and ready calculation is ok, then you could do something like:
```

ORIGINAL_LENGTH=$(wc -l originalfile | cut -d' ' -f 1)
NUMDIFFS=$(diff originalfile newfile | grep "^[<|>]" | wc -l)
PERCENTDIFF=$(( $NUMDIFFS *100 / $ORIGINAL_LENGTH))

```

note that this will double count changed lines, as diff output will include a '<' entry for the original line and a '>' for the new equivalent.  Up to you how you want to take it from here to tailor it for your own particular needs.

---

