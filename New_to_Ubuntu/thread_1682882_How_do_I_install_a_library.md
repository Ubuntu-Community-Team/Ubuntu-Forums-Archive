---
title: "How do I install a library?"
date: 2011-02-06
forum: New to Ubuntu
---

### Post by Captain Man on 2011-02-06
Hello everyone, sorry to trouble you again. I've looked around but I cannot find how to do this, how do I get a library? I'm trying to run Dwarf Fortress for linux and the windows version under wine runs way to slow so I thought the linux version may be better. The Readme says I need these libraries,
> In addition to the hardware requirements (which will be the same as the other
platforms) your system will need these libraries installed:

* GTK+ 2+
* SDL 1.2+
* SDL_image

And some kind of OpenGL implementation, so:

* libgl
* libglu

I don't know how to do this, I assume it's some terminal command or possibly something from the software center, I do not know, so any help is appreciated! Thanks!

---

### Post by Rocket2DMn on 2011-02-06
All these library packages should be available in the repositories - you may already have them installed (esp. the gtk ones) since they are pretty common libs.  Have you tried installing and playing the linux version?  I don't see Dwarf Fortress in the repos, so you will have to install that separately.

---

### Post by Captain Man on 2011-02-06
Yes, I have tried playing the linux version. When double clicking it I have two options, run or run in command line and neither work. I also made sure the executable thing was checked off in the properties.

How can I check to see if I have those libraries? I haven't put anything on this compy other than Chromium yet so unless the libs came default I probably don't have them.

---

### Post by Rocket2DMn on 2011-02-06
OK, I downloadd DF in an Ubuntu 10.10 VM, and this is what i had to do after downloading the app.
```
tar xjvf df_31_18_linux.tar.bz2
cd df_linux
chmod +x df
sudo apt-get install libsdl-image-1.2 libsdl-ttf2.0-0
```
You should then be able to execute the df application.
```
./df
```

---

### Post by Captain Man on 2011-02-08
Okay, I already extracted the archive to the home folder so I skipped the first line, I'm guessing that's what it was for. I run the second two but the forth one gives me issues...

```
jackson@jackson-laptop:~/df_linux$ sudo apt-get install libsdl-image-1.2 libsdl-ttf2.0-0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libsdl-image-1.2
E: Couldn't find any package by regex 'libsdl-image-1.2'

```

Help? Thanks for the responses Rocket2dmn!

---

### Post by Paqman on 2011-02-08
Both those libs are in the Universe repo. Make sure you've got that enabled in your software sources and try again.

---

### Post by Captain Man on 2011-02-08
Okay, I've fixed it. I went into Synaptic Package Manager, which I think is my version's version of Software Sources, and checked off libgtk or something, one of them, I don't remember which, and now the Linux version runs, thanks for the help everyone, I love that these forums are so helpful.

---

