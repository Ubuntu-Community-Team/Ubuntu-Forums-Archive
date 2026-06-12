---
title: "Webcam won't work in mozilla firefox?"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by SUDOwoodo on 2010-05-01
Hi all,
I'm new to Ubuntu, and i have a problem with my webcam.
When i try to go on to ebuddy, and use the webcam feature, my webcam won't work.  so i tried going on omegle to see if my webcam worked, and it didnt.  But when i use a program like aMSN or skype, my webcam works just fine.
any suggestions?
also, i have adobe flash installed, and im using Mozilla firefox.
thanks for your help!

---

### Post by SUDOwoodo on 2010-05-01
bump.

---

### Post by SUDOwoodo on 2010-05-01
bumpity bump bump.

---

### Post by no2498 on 2010-05-02
odd you have skype working
sounds like you need the same thing as you did for skype

this is not it but something like this
preload v4lsov4l2so (your program name)

hope i pointed you the right way

---

### Post by SUDOwoodo on 2010-05-02
> **no2498 said:**
> odd you have skype working
sounds like you need the same thing as you did for skype

this is not it but something like this
preload v4lsov4l2so (your program name)

hope i pointed you the right way
thanks for the help, i found a code that works
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so firefox
```and it does the trick, but only when you run firefox using that code.
do you know if there is a way to make that change permanant?
thanks again.

---

### Post by no2498 on 2010-05-02
only seen it 1 time
you need to make the file
was in a skype ?
sorry i cant help more

but glad you got it working

---

### Post by baligirl on 2010-05-02
[B][FONT=Courier New]Open a terminal and type the following:
[/FONT][/B]
```

**[FONT=Courier New]sudo gedit /usr/local/bin/skype[/FONT]**

```[B][FONT=Courier New]This brings up a (probably blank) editor, copy the following lines into it:
[/FONT][/B]
```

[B][FONT=Courier New]#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype[/FONT][/B]

```**[FONT=Courier New]Save the file and close the editor.  Hopefully you will be all set![/FONT]**

**[FONT=Courier New]best regards,[/FONT]**
[B][FONT=Courier New]Jennie
[/FONT][/B]


[B][FONT=Courier New]
[/FONT][/B]

---

### Post by SUDOwoodo on 2010-05-02
> **baligirl said:**
> [B][FONT=Courier New]Open a terminal and type the following:
[/FONT][/B]
```

**[FONT=Courier New]sudo gedit /usr/local/bin/skype[/FONT]**

```[B][FONT=Courier New]This brings up a (probably blank) editor, copy the following lines into it:
[/FONT][/B]
```

[B][FONT=Courier New]#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype[/FONT][/B]

```**[FONT=Courier New]Save the file and close the editor.  Hopefully you will be all set![/FONT]**

**[FONT=Courier New]best regards,[/FONT]**
[B][FONT=Courier New]Jennie
[/FONT][/B]


[B][FONT=Courier New]
[/FONT][/B]
i tried what you suggested, but still no luck
also, if it helps, i replaced the word skype, with firefox, as thats what im trying to get my webcam to work on... sorry if my post is confusing... but what im trying to accomplish is having my webcam work with flash, without always using the "LD_PRELOAD" code in the terminal.... 
thanks for your help as always!

---

### Post by baligirl on 2010-05-02
Oh, sorry, I didn't read your post close enough!  I don't really have any further advice to offer, except to mention that my /usr/bin directory has both a "firefox" and a "firefox-3.5" file in it.  Not sure which is being used as a default.  Maybe you can try modding things to have "firefox-3.5" (or similar) instead of just "firefox"?

Hope you get it figured out!

Jennie

---

### Post by SUDOwoodo on 2010-05-03
> **baligirl said:**
> Oh, sorry, I didn't read your post close enough!  I don't really have any further advice to offer, except to mention that my /usr/bin directory has both a "firefox" and a "firefox-3.5" file in it.  Not sure which is being used as a default.  Maybe you can try modding things to have "firefox-3.5" (or similar) instead of just "firefox"?

Hope you get it figured out!

Jennie
Thanks for your help.
i replaced firefox with firefox-3.5, and still no luck.
i guess the only way ill have a usable webcam on mozilla is by running the terminal code everytime..
oh well,
thanks for the suggestions everyone!

---

