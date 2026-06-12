---
title: "idiot mistake with *"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by SteveNorman on 2009-01-14
so I had a bunch of pics on my desktop I wanted to move to my photos folder.

I typed:```
 mv ~/Desktop *jpg
```

so my desktop has been moved to all my pictures. I get file Desktop does not exist upon cd Desktop

How do I undo this?
How do I shot web?

good lord=;=;

---

### Post by alienexplorers on 2009-01-14
should have typed:
> sudo mv ~/Desktop/*.jpg  ~/pictures

---

### Post by SteveNorman on 2009-01-14
nevermind I fixed it

mv *jpg ~/Desktop worked even tho there where multiple .jpg files

Sorry for the wasted electrons..going back to bed now:oops::oops::oops::oops::oops::oops::oops::oops:

---

### Post by albinootje on 2009-01-14
> **SteveNorman said:**
>  I typed:```
 mv ~/Desktop *jpg
```
How do I undo this?


To undo it :
```

mv *jpg ~/Desktop

```

(Don't use sudo in this case!)

---

### Post by albinootje on 2009-01-14
> **SteveNorman said:**
> nevermind I fixed it

mv *jpg ~/Desktop worked even tho there where multiple .jpg files


I just tried in /tmp the following :
```

mkdir /tmp/test
cd /tmp
mv test *jpg
ls -la *jpg
mv *jpg test

```
In other words, your Desktop directory was moved to a directory called "*jpg", it was not spread over all of your jpg files ;-)

---

### Post by Sealbhach on 2009-01-14
I sometimes find it useful to use "locate" if I'm not sure where I've moved something.

```
locate Desktop
```


.

---

