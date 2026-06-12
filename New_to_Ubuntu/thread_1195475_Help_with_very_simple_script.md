---
title: "Help with very simple script?"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by kamitsukai on 2009-06-23
I was wondering if someone could tell me or even better just post a very simple bash script to launch both Audacious and projectM-pulseaudio at the same time:KS

Thanks in advance!

---

### Post by fugaki on 2009-06-23
find out what the name of the file you execute is called
then make a script, call it whatever

enter the first program, press enter, enter the second program and save it.

run chmod +x filename

then you can run it by going to shell and navigating to the folder it is in and typing:

./filename

---

### Post by prinny42 on 2009-06-23
```

#!/bin/bash

commandtorunprogram1 &
commandtorunprogram2
exit 0

```

---

### Post by anystupidname on 2009-06-23
[removed]

---

### Post by prinny42 on 2009-06-23
The trouble with posts two and four is that, using those methods, the second command wouldn't execute until the first command finished (that is, the program was closed).

---

### Post by anystupidname on 2009-06-24
> **prinny42 said:**
> The trouble with posts two and four is that, using those methods, the second command wouldn't execute until the first command finished (that is, the program was closed).

My bad, prinny42 is correct

---

### Post by kamitsukai on 2009-06-24
Yep it works =] although for some reason audacious always asks for me to select a folder to play instead of using the folder previously selected...

---

### Post by kamitsukai on 2009-06-30
> **kamitsukai said:**
> Yep it works =] although for some reason audacious always asks for me to select a folder to play instead of using the folder previously selected...

Does anyone think they can help with why audacious is always asking for a folder to play when using this script? I could put up with it for a while but now it's just plain annoying;)

---

