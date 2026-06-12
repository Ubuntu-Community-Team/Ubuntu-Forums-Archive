---
title: "Help... I Cant install anything."
date: 2009-08-18
forum: New to Ubuntu
---

### Post by Zlap on 2009-08-18
[CENTER][FONT=Comic Sans MS]Hey everyone, This is my first post and i would like it to start off, WTF. Ubuntu is so awesome, and i think it is only awesome because of 1 of 2 things. 1. Well The OS, is just 98% perfect, and when something comes between the 2% you guys fix it as a community, and really arn't much haters on here so cool, The ubuntu community to me is like a small village where everyone knows everyone else, and if something goes down it doesn't need saying for the whole town to pich in. 

Anyways time to stop being so amazed at this OS's awesomeness. 

I have a error that i think must be simple to fix and i really was a PRO at Windows so now im starting fresh as a newbie again *WAHHH* so ill post the image below and i would perfer if you guys sort of wrote a small tut or even a simple to do.

Here is the image link =) thanks guys.


[IMG]http://img7.imageshack.us/img7/1019/screenshotbsz.png
[/FONT][/CENTER]

---

### Post by Zlap on 2009-08-18
Sorry about size of image....

---

### Post by Nburnes on 2009-08-18
Go to Applications > Accesories > Terminal

Then type 

```
sudo dpkg --configure -a
```

---

### Post by Zlap on 2009-08-18
I tryed that before i guess i mistyped it the first time, anyways as i thought i got another error lolz.

It says:
 " You have 1 broken package on your system. Use the "broken" filter to locate it"

any ideas where that is located i searched but met with no success. 


Thanks for your quick reply.

---

### Post by Nburnes on 2009-08-18
What happens when you type 

```
sudo apt-get check
```

---

### Post by zeroseven0183 on 2009-08-18
Looks like you're trying to install **Sun Java 6 Runtime**.

Have you tried installing it using the Terminal? Here's the command:
```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

Reference: [http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html)


And yes, the image is too big. You can always post it as thumbnail first here in the forums.

---

### Post by Zlap on 2009-08-18
found something on the internet known as a Google weird as hell but it magically told me what to do lolz. FIXED  how do i mark this post as SOLVED?:lolflag::guitar:

---

### Post by arochester on 2009-08-18
Go to Applications > Accessories > Terminal

Then type

> sudo apt-get -f install

---

### Post by Zlap on 2009-08-18
ty ill put that in a txt. SAVED thanks for the info might come in handy next time i need to reinstall OS.

---

