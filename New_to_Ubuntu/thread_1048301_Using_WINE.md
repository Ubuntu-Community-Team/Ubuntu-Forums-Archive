---
title: "Using WINE"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by John Hale on 2009-01-23
How do I find and run windows exe files and installed programs using Wine please I think I installed it correctly

Thanks

John

---

### Post by taurus on 2009-01-23
Of course, you need to download it, windows app, first unless you have it on a CD/DVD.  Then, you run it from a terminal using wine.  Make sure you are in the directory where that program is, just run

```
wine filename.exe
```

---

### Post by empty_spaces on 2009-01-23
in the terminal, you need to change to the folder containing the exe file, and then type **wine file.exe** where file.exe is your exe file.
Or you should also be able to right-click on the exe and select "Open with Wine Windows Program Loader".

---

### Post by superprash2003 on 2009-01-23
you may have to give full link like wine /path/to/filename.exe

---

### Post by John Hale on 2009-01-23
I'd like to install packages like autocad and nero into ubuntu as windows is so unstable now I can't connect to the web using it and exploer keeps popping up error messages and reloading etc

---

### Post by taurus on 2009-01-23
There is a version of nero for linux, nerolinux.  However, there are plenty of nice burning apps for Linux though.

p.s.  Just so you so you won't be surprised later.  Not every windows app will run or install with wine.  Wine is not the silver bullet.

---

### Post by stchman on 2009-01-23
> **John Hale said:**
> I'd like to install packages like autocad and nero into ubuntu as windows is so unstable now I can't connect to the web using it and exploer keeps popping up error messages and reloading etc

You can install K3b which is a really great CD/DVD burning program with lots of great features.

Hardy or later install.
```
sudo apt-get -y install k3b libk3b2-extracodecs
```2

Nero also makes a Linux version in either RPM or DEB packages in 32 and 64 bit.

[http://www.nero.com/enu/linux3.html](http://www.nero.com/enu/linux3.html)

I cannot help you with the autocad stuff.

---

### Post by gyaneshwar on 2009-01-23
On the [http://appdb.winehq.org/](http://appdb.winehq.org/) you can get a list of application currently supported with wine.

To have fully supported heavy programs like autocad I suggest you to use some virtual machine program like Virtualbox or similar to use windows under the Ubuntu.

---

### Post by Tibuda on 2009-01-23
> **John Hale said:**
> How do I find and run windows exe files and installed programs using Wine please I think I installed it correctly

Thanks

John
Wine applications see /home/USER/.wine as c:\ drive, so you can find most programs there.

---

### Post by sum janus on 2009-01-23
Doesn't Brasero come on Hardy preinstalled?  If not... how did it get onto my box!

---

### Post by John Hale on 2009-01-23
brasero won't copy my dvd's for some reason and I have to boot into windows to use nero

---

