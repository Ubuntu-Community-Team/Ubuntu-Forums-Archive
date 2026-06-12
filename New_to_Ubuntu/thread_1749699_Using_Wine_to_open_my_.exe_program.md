---
title: "Using Wine to open my .exe program"
date: 2011-05-04
forum: New to Ubuntu
---

### Post by AMar803 on 2011-05-04
i downloaded Wine so that i could open the windows program i downloaded for the lord of the rings online. when i go to my downloads folder and open the download it automatically uses Wine but nothing pops up. do i need to use the terminal? if so what do i need to type in the terminal. i'm not very computer savvy so the most dumbed down directions/ explanation would be greatly appreciated.

---

### Post by jerome1232 on 2011-05-04
First thing to do is check [winehq]("http://www.winehq.org/") to see if your app runs well under wine.

An easy method to install applications under wine is to use Play on Linux, you can download it with Ubuntu Software Center.

If you want to go at it yourself or it's not listed under Play on Linux the first thing I would try is to open a terminal. Type wine then hit space, then open nautilus and browse to your games .exe, drag it into the terminal and let go, then alt tab to your terminal and hit enter, see what happens. See if any notable errors pop up.

---

### Post by scott-ian on 2011-05-04
The software may not work.  Your should not have to, but it can be started from the terminal.  Type "wine [name and location of program]."  For example: "wine Downloads/example.exe."

---

### Post by andymorton on 2011-05-04
Right-click on the installer, choose properties and then tick the box to mark it as executable. Wine should start up then. Although I don't know whether it will be able to run the programe. 

andy :)

---

### Post by jerome1232 on 2011-05-04
Looking at winehq's appdb, it doesn't look to promising.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=13213](http://appdb.winehq.org/objectManager.php?sClass=version&iId=13213)

---

### Post by AMar803 on 2011-05-04
Thanks alot guys. That helped a ton! Way better than me trying to figure it out myself and mess something up. :D

---

