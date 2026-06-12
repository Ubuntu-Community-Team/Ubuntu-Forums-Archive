---
title: "Wine"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by adsy mac on 2009-09-11
where can i get Wine 1.1.16 as a deb file because i am completely hopeless at trying to use tar files and that.

I could only fine [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html) but it doesnt seem to work :(

---

### Post by dzon65 on 2009-09-11
Have you tried to install wine with synaptics?

---

### Post by adsy mac on 2009-09-11
Dont know what that means...

---

### Post by dzon65 on 2009-09-11
system>(not applications,the other one [my poor english])>synaptics.
Type "wine",enter....you should see it there.Proceed with instructions.Done.If it's done correctly there is a new menu in your main menu.

---

### Post by adsy mac on 2009-09-11
But doesnt that just install the latest version? i dont want that, i want v1.1.16, its older but photoshop run perfect in it.

---

### Post by lovinglinux on 2009-09-11
[wine](apt:wine) [apt-get] 

> [color=#CC0000]**Note:**[/color] when you see [apt-get] after a link on my posts it means that you just need to click it to install the software. This is basically an easy way to perform an installation from the [repositories](http://en.wikipedia.org/wiki/Software_repository) without running the command on a terminal or browsing Synaptic. This is the same as running the command *sudo apt-get install* followed by the name of the program. To learn about installation methods in Ubuntu [click here](https://help.ubuntu.com/9.04/add-applications/C/index.html).

---

### Post by achase79 on 2009-09-11
You have the right website but it is down right now.  I have been having problems connecting tothat site for a few weeks.

---

### Post by adsy mac on 2009-09-11
> **lovinglinux said:**
> [wine]("apt:wine") [apt-get]


I know how to install wine. i just dont know where to find an installation for v1.1.16 (an older version of wine)

i can find a tar.bz2 file but im completely hopeless at using them so i was trying to find deb.

---

### Post by dzon65 on 2009-09-11
I have no idea which version it is but you might give it a try.If photoshop doesn't run well in this version it's very easy to uninstall it through the same synaptics-path.I use gimp instead of photoshop so can't really help you there.But,like I said,try it.

---

### Post by NinjaNumberNine on 2009-09-11
Gimp rulez! :mrgreen:

---

### Post by adsy mac on 2009-09-11
> **dzon65 said:**
> I have no idea which version it is but you might give it a try.If photoshop doesn't run well in this version it's very easy to uninstall it through the same synaptics-path.I use gimp instead of photoshop so can't really help you there.But,like I said,try it.

i tried using GIMP, its good for being free but it just cant do what i want like in PS.

oh when you said go to system then type in wine. i cant see anywhere to type when i click system, all i get is a drop down list showing preferences and administration.

---

### Post by NinjaNumberNine on 2009-09-11
System>Administration>Synaptic Package Manager: Search "Wine" in top right corner. :D

---

### Post by adsy mac on 2009-09-11
> **NinjaNumberNine said:**
> System>Administration>Synaptic Package Manager: Search "Wine" in top right corner. :D

ah got it now haha. but it still only lets me install the latset wine. no good :/

---

### Post by 3rdalbum on 2009-09-11
> **adsy mac said:**
> where can i get Wine 1.1.16 as a deb file because i am completely hopeless at trying to use tar files and that.

Well, if you want to purposely use an older version of some software, then you really should compile from source. It is not hard, you just need to run the ./configure script, install whatever development packages it complains about, and then run the script again, etc. Then run the "make" command and "sudo make install".

---

### Post by NinjaNumberNine on 2009-09-11
> It is not hard, you just need to run the ./configure script, install whatever development packages it complains about, and then run the script again, etc. Then run the "make" command and "sudo make install".
Man, Ive been with linux 3 or 4 yrs now and I still only get 1 out of ahundred tgz packages installed. :D

---

### Post by adsy mac on 2009-09-11
> **3rdalbum said:**
> Well, if you want to purposely use an older version of some software, then you really should compile from source. It is not hard, you just need to run the ./configure script, install whatever development packages it complains about, and then run the script again, etc. Then run the "make" command and "sudo make install".


i dont understand a word you just said :|

---

### Post by CatKiller on 2009-09-11
> **adsy mac said:**
> I could only fine [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html) but it doesnt seem to work :(

What happens?

---

### Post by redbob on 2009-09-11
Months ago I tried to install 1.1.19, but it was so painful, because Wine conflicts too much with gcc, glibc, etc...
Yesterday I successfully installed 1.1.29 just following instructions from Winehq:> [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

