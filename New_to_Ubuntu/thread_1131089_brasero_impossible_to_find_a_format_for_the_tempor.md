---
title: "brasero: impossible to find a format for the temporary image."
date: 2009-04-20
forum: New to Ubuntu
---

### Post by egalvan on 2009-04-20
I am trying to make a back-up copy of a  DATA DVD.

This is a Knoppix LiveDVD.

Under Ubuntu 8.04.2 I ran brasero

and got this error

*impossible to find a format for the temporary image.*

see attached screen-shot.

i have been using this install since April-08, and it plays music, encrypted DVD movies, burns iso images... all run fine...

medibuntu restricted extras win32codecs, all installed.

---

### Post by mprince on 2009-04-21
This won't be that helpful to you, but there is a bug filed about this issue.

[https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/236259](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/236259)

---

### Post by cariboo on 2009-04-21
Can you create an iso of the dvd, and then burn it?

```
sudo dd if=/dev/scd0 of=image.iso
```

Jim

---

