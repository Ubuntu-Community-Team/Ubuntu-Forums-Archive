---
title: "viewing -duration"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by nandagopal on 2009-09-06
How do I view the duration of an mp3 file in the terminal,
ls -l does not give the duration.
it only gives the time in which it was last modified ,  i want  to view all the properties that we see in the nautilus browser when we right click and select properties ,in the terminal

can somebody please enlighten me on this.

---

### Post by pedro3005 on 2009-09-06
Use "libimage-exiftool-perl", it's on the repositories. Run:
```

sudo apt-get install libimage-exiftool-perl

```
Then:
```

exiftool file.mp3

```
For more information on it:
```

man exiftool

```

---

### Post by nandagopal on 2009-09-06
Thanks a ton man.
It works perfectly.
i am able to pipe this command to grep and get what i want ,
thanks a lot once again

---

