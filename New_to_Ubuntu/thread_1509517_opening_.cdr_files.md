---
title: "opening .cdr files"
date: 2010-06-14
forum: New to Ubuntu
---

### Post by beanco on 2010-06-14
What program can I use to open .cdr files ?

I am on Karmic.

Thanks

robi

---

### Post by VernonA on 2010-06-14
There's more than one type of file which uses the .CDR extension. Do you have any idea what sort of file it is?
--Vernon

---

### Post by beanco on 2010-06-14
> **VernonA said:**
> There's more than one type of file which uses the .CDR extension. Do you have any idea what sort of file it is?
--Vernon


All I know is that it is a logo for the school I teach at. The guy who created said sg along the lines of having used *illustrator* to make it.

Robi

---

### Post by wednesday allfather on 2010-06-14
CDR is Corel.  Closed source, proprietary format.  afaik you cannot convert those images unless you have Corel.

As much as I dislike Adobe, Corel seems to be worse.  

Sorry

---

### Post by wesleybishop on 2010-06-14
sounds like you have a similar issue [http://ubuntuforums.org/showthread.php?t=93967](http://ubuntuforums.org/showthread.php?t=93967)

---

### Post by beanco on 2010-06-14
> **wesleybishop said:**
> sounds like you have a similar issue [http://ubuntuforums.org/showthread.php?t=93967](http://ubuntuforums.org/showthread.php?t=93967)

Well I could not get sk1 to install, rather, U followed the link in the other thread, downloaded clicked, it said installed but I cannot get it to open .

I can asked the guy tomorrow to save the file in Corel Draw as a jpg and then work with that, but i really wanted to be able to open up .cdr files....

robi

---

### Post by VernonA on 2010-06-15
According to the SK1 website (see [here]("http://www.sk1project.org/modules.php?name=Products&product=uniconvertor")), they provide the CDR converter in a library, which they say is used by both Inkscape and Scribus to allow them to import CorelDraw files. Have you tried installing Inkscape to see if it can read your file and save it as an SVG?

---

### Post by beanco on 2010-06-15
> **VernonA said:**
> According to the SK1 website (see [here]("http://www.sk1project.org/modules.php?name=Products&product=uniconvertor")), they provide the CDR converter in a library, which they say is used by both Inkscape and Scribus to allow them to import CorelDraw files. Have you tried installing Inkscape to see if it can read your file and save it as an SVG?


VernonA,

I could not get it installed for some reason. Can I get it from the command line?

RObi

---

### Post by Chesamo on 2010-06-15
```
sudo aptitude install inkscape
```

---

### Post by beanco on 2010-06-15
> **Chesamo said:**
> ```
sudo aptitude install inkscape
```

thanks

---

### Post by VernonA on 2010-06-15
If this works, don't forget to post back here and let us know. (If it doesn't work I guess you'll be back pretty fast!)
--Vernon
PS There's no need to keep re-quoting our replies back to us:p

---

### Post by beanco on 2010-06-16
Got it installed but could not open the .cdr file. I will mess around with it tonight after work.


And sorry about all the quotes.

robi

---

### Post by VernonA on 2010-06-17
I installed Inkscape on my machine, and it does seem to suggest it can open CorelDraw files. I didn't have .CDR file to hand, so couldn't actually prove it. Do you want to attach your file to the thread?
--Vernon

---

### Post by beanco on 2010-06-17
Here you go

robi

edited to add.... i cannot upload .crd files!

---

### Post by beanco on 2010-06-18
It appears that the forums do not allow .crd files as attachments.

I actually have the file now as a jpd .... now I just have to learn how use either  inkscape or gimp.

look at the attached file, I want to take the Logo and make it as and arc rather than have it straight....

This is the only step of an over all larger project that I cannot figure out yet.....

---

### Post by mandza on 2012-03-20
i just install inkscape but i still can not open .cdr files
i use ubuntu 11.10

---

### Post by Jerry N on 2012-03-20
Coreldraw bitmap files (.cdr) are on the list of files that Xnview will open.  Xnview is a Windows program but will run in Wine, at least I run it in Crossover.  There is an old linux version of Xnview that I found to be worthless although it can still be downloaded from the Xnview website and there is a new multiplatform version of Xnview (Xnview MP) in testing that runs in Linux but I know nothing about it's format compatibility.

Jerry

---

### Post by loftyboyt on 2012-10-03
so can i export to extention cdr? 
beacause every body is in used coreldraw in my country!

---

### Post by cway00 on 2012-10-03
Check this website for more information on how to install Inscape and Uniconverter including a Corel Viewer from this link on Ubuntu 

```

http://sk1project.org/index.php

```

---

