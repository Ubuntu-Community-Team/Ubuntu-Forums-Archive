---
title: "How to open Downloads that require Vista OS"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by nephilus on 2009-02-23
I have an ubuntu/vista dual boot and I was wondering how you can open Downloads that require a vista OS. the download I'm trying to open is called 360Desktop. and i don't mean anything like beryl etc. I already have it!

---

### Post by Therion on 2009-02-23
You open them with Vista.

---

### Post by yeats on 2009-02-23
Yes - that program only runs on Windows (according to the website).  Since Ubuntu has such cool tools that have similar functions, that leads me to ask, what are you trying to do? :-)

---

### Post by donkyhotay on 2009-02-23
Windows programs can't run on linux except with wine, and from what I know of that program I *seriously* doubt it will run with wine.

---

### Post by sandyd on 2009-02-23
i really don't care what hes trying to do....

but.....


in the terminal, navigate to the place where you downloaded the file (Desktop i assume)

with this
```

cd Desktop

```then type this in (line by line)
```

mkdir 360desktop
mv *.exe 360desktop
sudo apt-get install cabextract
cabextract *

```works, i tried it myself

p.s.: [donkyhotay]("http://ubuntuforums.org/member.php?u=205262") is right, this will NOT install. this will only extract the files that were in the archive for you

EXIT: Yikes! it runs and crashes my Xserver.

Urk! silly me

---

