---
title: "rythanmbox music player keeps trying to down load"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by blake7 on 2009-05-25
it keeps trying to down load  application/x-ar decoder   and 
Windows Media Audio decoder but can ever find it. is thier somthing i can do 


thank yiou for your help

---

### Post by oOarthurOo on 2009-05-25
Add the medibuntu respository, install w32codecs, assuming it is legal for the area you live in.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by blake7 on 2009-05-25
hi 

thanks for that but it did not work, it still doing the same thing, if you have any other iders i would be greatfull.

cheers and thanks for your time

---

### Post by oOarthurOo on 2009-05-25
What's the filename and extension it is trying to play?

---

### Post by blake7 on 2009-05-25
i dont know it just does it every time i start the program...
i wrote in the frist post what it is trying to do.

thank you for your time

---

### Post by oOarthurOo on 2009-05-25
Start it from the terminal, and post the output here

---

### Post by blake7 on 2009-05-25
sorry but how do i do that

---

### Post by oOarthurOo on 2009-05-25
Open a termina and type: rhythmbox 

Or... 
```
rhythmbox --debug &> rhythmbox-debug.txt
```

That should create a file in your home directory with the debugging output. Paste the output of the first way, then if you're really keen attach the file that's created with the second way.

---

### Post by Viva on 2009-05-25
Are you able to play all music files in rythmbox?

---

