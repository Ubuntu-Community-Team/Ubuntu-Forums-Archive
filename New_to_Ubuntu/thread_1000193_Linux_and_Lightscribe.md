---
title: "Linux and Lightscribe"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by timjm25 on 2008-12-02
What is a good program to use to interface with a Lightscribe CD/DVD burner, and to use the lightscribe capabilities?

---

### Post by Tony Flury on 2008-12-02
I would love to know this too - if anyone can help ...

---

### Post by mister_pink on 2008-12-02
This thread seems to have some ideas. Maybe try some of what it says then post there with any issues. I don't have one myself so can't help directly

[http://ubuntuforums.org/showthread.php?t=106197&page=23](http://ubuntuforums.org/showthread.php?t=106197&page=23)

---

### Post by LowSky on 2008-12-02
Lightscribe has the linux version software on their website it based for FEDORA so it will need to be converted to DEB before using, you ewill need an program called alien to do so
[http://www.lightscribe.com/downloadSection/linux/index.aspx](http://www.lightscribe.com/downloadSection/linux/index.aspx)


here is some othe info to look into
[http://www.linux.com/feature/118705](http://www.linux.com/feature/118705)


LACIE and HP also offer software

---

### Post by stchman on 2008-12-02
> **timjm25 said:**
> What is a good program to use to interface with a Lightscribe CD/DVD burner, and to use the lightscribe capabilities?

Here is a nice page on what you want.

[https://help.ubuntu.com/community/LightScribe](https://help.ubuntu.com/community/LightScribe)

---

### Post by reiki on 2008-12-07
Lightscribe Simple Labeler does text only.

To Lightscribe images onto a disk you'll want to use 4L-gui from here:

[http://www.lacie.com/support/drivers/driver.htm?id=10094](http://www.lacie.com/support/drivers/driver.htm?id=10094)

This is an RPM file and you'll want to convert it to a .deb using alien or find someone that has already converted it. Alien is in the repositories and is very easy to use.

I made a template for Inkscape to use with 4L-gui for putting images and text onto a lightscribe disk. Inkscape is in the repositories. The template has a layer with instructions in it.
[http://ubuntuforums.org/showthread.php?t=636450](http://ubuntuforums.org/showthread.php?t=636450)

---

### Post by NoVista on 2008-12-07
DiskWrapper is another one.
[http://sourceforge.net/projects/discwrapper](http://sourceforge.net/projects/discwrapper)

You might also find you need the libstdc++5 package in order for 4L to recognize your Lightscribe burner.

---

