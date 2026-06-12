---
title: "Firefox running slowly"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by corykendall on 2009-11-21
I just installed Karmic Koala on a new machine.  For the first hour or so Firefox was running fine.  Now it spins and takes about 10 seconds to load every page.  I am new to Ubuntu and have no idea how to diagnose what is causing this.  I have confirmed by using my laptop (running windows right next to me) that it is not my internet connection.

Does anyone have any tips?  Or even more general information on how I can diagnose this issue, as I'm new to Ubuntu?

Thanks!

---

### Post by Ericyzfr1 on 2009-11-21
Have you installed any add-ons?

---

### Post by 23dornot23d on 2009-11-21
I have noticed a similar thing in Facebook using chat it gets slower and slower ..... then crashes out ...... no warning .....

..... almost feels like its running out of memory ..... yet I have loads ..... 

Not sure which is best memory monitor to use though to check it out ......... this is a snapshot below ... is 227 Meg normal ..... ?

[IMG]http://i47.tinypic.com/2d7cv86.jpg[/IMG]

---

### Post by corykendall on 2009-11-21
> **Ericyzfr1 said:**
> Have you installed any add-ons?

Firefox add-ons?  No.  I have used apt-get and the Ubuntu Software Center to download plenty of things.

> **23dornot23d said:**
> I have noticed a similar thing in Facebook using chat it gets slower and slower ..... then crashes out ...... no warning .....

..... almost feels like its running out of memory ..... yet I have loads ..... 

Not sure which is best memory monitor to use though to check it out .........

What is/are "loads"?

---

### Post by QIII on 2009-11-21
lovinglinux has a great set of optimizations to look through here:

[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by corykendall on 2009-11-21
It seems now that there is a ~5 second delay after I issue a request across the network.  For example, I just typed

```
sudo apt-get install plt-scheme
```

and the line where it shows the percentage of the package downloaded sat at 0% for about 5 seconds before quickly completing.  It only seems to do this for the first package I am installing.

---

