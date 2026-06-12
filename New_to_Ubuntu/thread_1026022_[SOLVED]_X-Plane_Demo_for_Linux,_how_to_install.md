---
title: "[SOLVED] X-Plane Demo for Linux, how to install?"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by Joao Paz on 2008-12-30
Greetings,

I'm searching for some help on how to install the X-Plane (flight simulator) demo in Ubuntu. I saw that they have a demo for Linux at
[http://www.x-plane.com/demo.html](http://www.x-plane.com/demo.html)

Downloaded it, extracted it, but then nothing happened...
I did some search and found something about Synaptics and libopenal being required to run the installer. So I installed 
libopenal-dev
libopenal1
libopenal1-dbg

Tried to double-click the installer again but still nothing happened.

So...
a) May I leave these libeopenal* installed or should I remove them again?
b) Any ideas on how to make it work?

I know this all may sound too dumb to you Gents, but it has been only a week or so with Ubuntu, here ... but I'm looooooving it! :P

Thanks for your patience!
Joao

---

### Post by taurus on 2008-12-30
Why don't you just run it from a terminal and see what happens?

Applications -> Accessories -> Terminal
```
cd ~/Desktop
./"X-Plane Demo Installer Linux"
```
Assuming that you unzipped it in your ~/Desktop.

---

### Post by Joao Paz on 2008-12-30
Hum...
Didn't work but maybe it was worth it nonetheless.

> ./X-Plane Demo Installer Linux: error while loading shared libraries: libopenal.so.0: cannot open shared object file: No such file or directory


Perhaps I need that libenopenal.so.0 ?
Thank you Taurus!

---

### Post by eBoxNet on 2008-12-30
When you are not getting any message from your application always try to run it thought terminal,that way you getting really useful messages from your system about the application you are trying to run.

;)

---

### Post by eBoxNet on 2008-12-30
If you are using Intrepid, try this to fix your problem

```
sudo ln -s /usr/lib/libopenal.so.1 /usr/lib/libopenal.so.0
```

---

### Post by spydon on 2008-12-30
Hmm you should already have that file I think.
You could try to do
```
sudo chmod +x "X-Plane Demo Installer Linux"
```
and if you want to(a bit risky)
```
sudo ./"X-Plane Demo Installer Linux"
```

---

### Post by Joao Paz on 2008-12-30
Thank you, all

While I was here I downloaded this...
[http://packages.ubuntu.com/dapper/i386/libopenal0/download](http://packages.ubuntu.com/dapper/i386/libopenal0/download)
...and installed it with the default GDebi Package Installer

That seems to have done the trick :)

But, boy, I hope I'm not messing my Ubuntu in any way! ;)

---

### Post by eBoxNet on 2008-12-30
this is a kind of bug in ubuntu 8.10 don't worry you didn't mess with your OS

---

### Post by Joao Paz on 2008-12-30
> **eBoxNet said:**
> this is a kind of bug in ubuntu 8.10 don't worry you didn't mess with your OS

Thanks again 8-)

---

