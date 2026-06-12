---
title: "cracking zip with fcrackzip"
date: 2011-04-27
forum: New to Ubuntu
---

### Post by realmoonstruck on 2011-04-27
i am using version 1.0
the password of the zip file is: aa
but i can not crack it with fcrackzip

i am using:  ```
fcrackzip -u -b -l 2-2 z.zip
```
without the -u flag the output is:
```
possible pw found: et ()
possible pw found: hl ()
possible pw found: iG ()
possible pw found: i9 ()
possible pw found: qK ()
possible pw found: wo ()
possible pw found: w5 ()
possible pw found: Go ()
possible pw found: Hn ()
possible pw found: Vj ()
possible pw found: V& ()
possible pw found: Yt ()
possible pw found: ZO ()
possible pw found: 2R ()
possible pw found: 3] ()
possible pw found: 65 ()
possible pw found: 6} ()
possible pw found: !E ()
possible pw found: !L ()
possible pw found: $F ()
possible pw found: ?v ()
possible pw found: {C ()
possible pw found: [i ()
```

am i missing something? what am i doing wrong?

---

### Post by It-Alien on 2011-05-05
I have exactly the same problem. At least we're not alone in the world..

---

### Post by ugmoe2000 on 2011-11-20
By default, fcrackzip will not actually try to unzipping the archive with the passwords it tests. Using the "-u" flag tells fcrackzip to try unzipping the first file in the archive (if multiple files exist) with the tested-password to rule out false-positives. The output you see is basically a list of false-positives.

---

