---
title: "how do i find all the files NOT ending in mp3 on /foo/ and its subdirectories?"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by hanzj on 2009-09-02
[COLOR=#204A87]**[SIZE=3] [/SIZE]**[/COLOR]how do i find all the files NOT ending in mp3 on /foo/ and its subdirectories?

---

### Post by hanzj on 2009-09-02
Please also show me how to do this in Nautilus (after pressing Ctrl+F, or Go/[Search for Files]).

---

### Post by falconindy on 2009-09-02
Don't know how to do it in Nautilus, but the command line results would obtained with:
```
find /foo/ | grep -v .mp3$
```
Command line is better in this case because you could easily do something like....
```
for f in `find /foo/ | grep -v .mp3$`; do
    mv $f /other/directory/ #or delete, or copy, or whatever...
done
```

---

### Post by modmadmike on 2009-09-02
> **falconindy said:**
> Don't know how to do it in Nautilus, but the command line results would obtained with:
```
find /foo/ | grep -v .mp3$
```
Command line is better in this case because you could easily do something like....
```
for f in `find /foo/ | grep -v .mp3$`; do
    mv $f /other/directory/ #or delete, or copy, or whatever...
done
```

locate is much faster:
```
locate /foo/ | grep -v .mp3
```

---

### Post by slakkie on 2009-09-02
> **falconindy said:**
> Don't know how to do it in Nautilus, but the command line results would obtained with:
```
find /foo/ | grep -v .mp3$
```
Command line is better in this case because you could easily do something like....
```
for f in `find /foo/ | grep -v .mp3$`; do
    mv $f /other/directory/ #or delete, or copy, or whatever...
done
```

Alternativly

```

# Same thing but without grep
find /foo ! -iname \*.mp3 

# mv without for-loop
find /foo ! -iname \*.mp3 -exec mv {} /bar +

```

---

