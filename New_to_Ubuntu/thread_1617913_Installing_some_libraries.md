---
title: "Installing some libraries"
date: 2010-11-09
forum: New to Ubuntu
---

### Post by Armeleon on 2010-11-09
I am trying to run a nice little program in Ubuntu. Unfortunately, I ran  across this issue: "your system will need these libraries installed:

* GTK+ 2+
* SDL 1.2+
* SDL_image

And some kind of OpenGL implementation, so:

* libgl
* libglu"

Any ideas on how and where to get them?

---

### Post by wog on 2010-11-09
> **Armeleon said:**
> I am trying to run a nice little program in Ubuntu. Unfortunately, I ran  across this issue: "your system will need these libraries installed:

* GTK+ 2+
* SDL 1.2+
* SDL_image

And some kind of OpenGL implementation, so:

* libgl
* libglu"

Any ideas on how and where to get them?

You can search apt-get for them in the terminal window and see if they're there.
```
apt-cache search "keywords of your choice"
```

Just use libgl and libglu separately as keywords and that'll give you some options. Once you know what you want to install, you do this:
```
sudo apt-get install package_of_your_choice
```

Of course, if GUI is more your style, you can use: 
System >> Administration >> Synaptic Package Manager

Use the search area and type in each of those and check them off (they might both come up during the same search) for installation.

That's what I know, anyway.

Good luck!

---

### Post by Armeleon on 2010-11-10
Great info. Thanks. Let me run this by you guys, and let me know if I have misunderstood anything. (The package names are not exactly the same, which is why I question whether I have the entire package or only a part if it is even a part of the right package)

* GTK+ 2+     -- installed **'libgtk2.0-0**'
* SDL 1.2+     -- installed **'libsdl1.2debian-all'**
* SDL_image  -- installed** 'libsdl-image1.2'**

* libgl
* libglu             -- installed **'libglu1-mesa'**

The biggest reason why I ask is because of the no-such-file error I still get when trying to run the file. 'error while loading shared libraries: libSDL_ttf-2.0.so.0'

---

### Post by oldos2er on 2010-11-10
apt-cache search libsdl ttf
libsdl-ttf2.0-0 - ttf library for Simple DirectMedia Layer with FreeType 2 support
libsdl-ttf2.0-dev - development files for SDL ttf library (version 2.0)

Hope that helps.

---

