---
title: "deb vs source"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by RichardCL on 2009-03-18
Hi,

When looking for a program that I don't find under the Ubuntu repositories, I'm sometimes faced with .deb or source. I know that I can install both but which one is best?

I'm currently looking at icepodder [http://www.icepodder.com/?page_id=4]("http://www.icepodder.com/?page_id=4") The download offers .deb for all hardware or source.

Having read around a bit, it seems that I may have some performance benefit if I compile the source on my system (quadcore running 64 bit) and thus have a version of the program for my own hardware.

I'm a complete beginner but have managed to make and install from source for my Garmin and Wireless devices. Debian packages seem easier and quicker though if there isn't any point.

Anyone got any thoughts?


Rich

---

### Post by simtaalo on 2009-03-18
debs are easy. building from source isn't necessarily that much harder, but it can be. i don't think you would notice much speed increase.

---

### Post by Roanoke on 2009-03-18
.debs are better in that you don't have to compile them and all dependencies are shown up front. Sources are better because you can configure the package.

---

### Post by Eisenwinter on 2009-03-18
A source installation provides you with far more control.

---

### Post by carml on 2009-03-18
As someone suggested,using a .deb it's generally easier than compiling yourself the source code.During the compilation you can notice some issues due to the lack of libraries also known as not respected dependences.:)

---

### Post by rburkartjo on 2009-03-18
if a deb download for an app is avail i always use and it is easy to install just use the computer janitor

---

### Post by issih on 2009-03-18
Unless there is a need to patch the source or compile using some specific option, I'd say go with a deb 100% of the time. There is just no point as far as I can see, it won't really give you any appreciable speed up in 99.99% of cases.

---

### Post by lykwydchykyn on 2009-03-18
If you decide to go with source, use checkinstall in place of the usual make/make install.  It will generate a deb and you'll be able to easily uninstall it later.

Alternately, you can read up on how to build a proper .deb with devscripts and debbuild, but that's a lot of work if you aren't redistributing the package.

---

### Post by RichardCL on 2009-03-19
> **lykwydchykyn said:**
> Alternately, you can read up on how to build a proper .deb with devscripts and debbuild, but that's a lot of work if you aren't redistributing the package.

Does it make sense to redistribute. For the wireless driver I had to configure from sources that are available for general *nix machines. I could create a .deb and save a lot of effort for a lot of people. How would one make that available? Are people really interested in that or do most people prefer to just do it them selves?

---

### Post by betrunkenaffe on 2009-03-19
> **RichardCL said:**
> Does it make sense to redistribute. For the wireless driver I had to configure from sources that are available for general *nix machines. I could create a .deb and save a lot of effort for a lot of people. How would one make that available? Are people really interested in that or do most people prefer to just do it them selves?

If you've got a solution which will assist people and are willing to share, people will use that over rebuilding it themselves.

---

