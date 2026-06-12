---
title: "Help with wireless!!!"
date: 2010-09-22
forum: New to Ubuntu
---

### Post by sammyjo on 2010-09-22
Ok so I just installed Ubuntu on my brothers laptop and it is an HP computer. Now it is not recognizing his wireless at all I did the iwconfig and it is saying there is no wireless extensions. Any help on this would be great and just know that I am a total noob so any help in plain english or step by step would be amazing!!! Thanks for everything!

---

### Post by Gone fishing on 2010-09-22
Probably its using a wireless which needs a driver.

Plug it into a wired network then 

System > Administration > Hardware Drivers 

and enable the driver.

---

### Post by zipperback on 2010-09-22
> **sammyjo said:**
>  Now it is not recognizing his wireless at all I did the iwconfig and it is saying there is no wireless extensions.



Open a terminal window like you did when you issued the iwconfig command and tell me what the output of the following says:

```

lspci

```


and also tell me what this one says as well.

```

lsusb

```

Thank you.

zipperback
:popcorn:

---

### Post by sammyjo on 2010-09-23
Hey so I got it working thank you very much for your help guys. I plugged it into the ethernet and it automatically popped up with the drivers. :)

---

### Post by bradleypariah on 2010-09-23
You gotta love that.  :-D

---

### Post by sammyjo on 2010-09-23
Oh yeah talk about pure convenience right there I couldnt be happier lol

---

