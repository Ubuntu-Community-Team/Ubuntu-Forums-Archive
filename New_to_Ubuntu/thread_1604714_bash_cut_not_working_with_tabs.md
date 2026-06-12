---
title: "bash: cut not working with tabs"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by honeybear on 2010-10-24
Hi, it seems that there is an issue with tab under cut app. I have this non-working code:

```
cat myfile.txt | cut -d'\t' -f1

```

---

### Post by schryer on 2010-10-24
The default delimiter is tab so try:
```
cat myfile.txt | cut -f1
```

---

### Post by Chesamo on 2010-10-24
As schryer mentioned, tab is the default delimiter, so there's no need to specify it manually.

Alternately, I believe cut's syntax is usually ```
cut -d<SP>'<symbol>'
```I'm not at liberty to experiment right now, though.

---

### Post by amauk on 2010-10-24
As above, cut's default delimiter is tab

If you really want to specify the delimiter to a tab, you can using something like this```
cut -d "$(echo -e "\t")" -f2
```

I've had to do this a few times when working with text files where the delimiter was user-specified and unknown ahead of time

Something akin to```
DELIMIT="\t"
echo -e "foo\tbar\tbaz" | cut -d "$(echo -e "$DELIMIT")" -f2
```

---

### Post by honeybear on 2010-10-24
thank you so much !!

---

