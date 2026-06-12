---
title: "No globe in Google Earth?"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by pointyblue on 2008-12-04
Hi,

I just installed Xubuntu 8.10 on a friend's laptop. Installed Wine, then Google Earth and it seems to run as it should - apart from the fact there's no globe in the viewer window. (It's just a black square.)

Any ideas on how to fix this? Guess I need to install something to make the graphics work...

:confused:

---

### Post by appi2012 on 2008-12-04
Same thing happens to me. Its weird.

---

### Post by oldos2er on 2008-12-04
Which version of Google Earth did you install? The one in Medibuntu or the one from Google?

---

### Post by pointyblue on 2008-12-05
I downloaded the .exe file from Google and installed it with wine.

(I know they have a .bin version for linux too but after making it executable I tried to open it with wine (!) which was obviously wrong, and now wine is set as the default program for .bin and I don't know which program to open it with...)

---

### Post by snova on 2008-12-05
Try the Linux version...

If it's a .bin file, it's just a plain old executable, like any other program you would run. I think it's an installer, but I don't remember.

Either fix the file associations (that will come back to bite you later), or open a terminal and run it from there. If you choose the second option and don't know how, just tell us where the file is located and what it is called, then instructions should be easy to provide.

---

### Post by oldos2er on 2008-12-06
Search for my posts from the past few days; I know I've posted instructions on how to install the *.bin file a couple times recently. Or you could enable the Medibuntu repository and install it using apt-get or Synaptic.

---

### Post by barbedsaber on 2008-12-06
first add the google software repository, follow instructions
[here]("http://www.google.com/linuxrepositories/apt.html")
then, use synaptic to install google earth.
then, you should have the linux version of google earth, but, the problem will still be there, it is a problem that google knows about, and is working on, but a quick work around, is to run it is root. (usually a bad idea, but it does fix the problem)
do this by running
```
sudo googleearth
```

hope that helped.

---

