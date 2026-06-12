---
title: "Installing an application"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by nayeret43 on 2009-01-03
I just downloaded Assault Cube (the game), and it opened up in a tar.bz2 file.

I am a Linux newbie here by the way.

How do I install the program? There is no "next next finish" that I see.  So, how do you install a program in Linux?

Thanks!

---

### Post by Titan8990 on 2009-01-03
Install in from System -> Administration -> Synaptic Package Manager.

Only download tar.gz when there isn't and existing package in synaptic or you are in need of a newer version.

---

### Post by nayeret43 on 2009-01-03
> **Titan8990 said:**
> Install in from System -> Administration -> Synaptic Package Manager.

Only download tar.gz when there isn't and existing package in synaptic or you are in need of a newer version.



I tried that.  It didn't work.  I didn't download an application.  I downloaded a game.  When I typed in "Assault Cube" all it showed was some screen saver I think that had nothing to do with what I downloaded.

Is there perhaps another option?

---

### Post by ptn107 on 2009-01-03
I'm downloading the game right now and I'll post the installation instructions if I figure it out.

---

### Post by ithanium on 2009-01-03
download the game from here:
[http://www.getdeb.net/app.php?name=AssaultCube]("http://www.getdeb.net/app.php?name=AssaultCube")
it's easyer to install

---

### Post by ptn107 on 2009-01-03
ithanium's suggestion will work.

I also figured out how to run the game from the file you downloaded by *following the included instructions*.  The 'readme.html' says that libSDL 1.2, libSDL_image, and OpenAL are required to run the game.  On my Debian machine all I needed to do was install them by running
```
sudo apt-get install libsdl1.2debian libsdl-image1.2 libopenal1
``` from the command line (Applications -> Accessories -> Terminal).  These packages are the same in Ubuntu 8.10 as well.

Double-clicking the 'assaultcube.sh' file in the game folder then ran the game with no hitches.

---

### Post by oldos2er on 2009-01-03
> **nayeret43 said:**
> I just downloaded Assault Cube (the game), and it opened up in a tar.bz2 file.

I am a Linux newbie here by the way.

How do I install the program? There is no "next next finish" that I see.  So, how do you install a program in Linux?


 Assault Cube is in the repositories. Open a terminal and type "sudo aptitude install assaultcube".

---

