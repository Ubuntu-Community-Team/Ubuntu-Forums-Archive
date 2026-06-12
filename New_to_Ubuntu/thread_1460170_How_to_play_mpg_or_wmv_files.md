---
title: "How to play mpg or wmv files?"
date: 2010-04-22
forum: New to Ubuntu
---

### Post by balaraja on 2010-04-22
I went through 

[https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f]("https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f")

and installed w32codecs. 

dpkg shows i have installed the w32codecs package.

balaraja@balaraja-laptop:~$ dpkg -l | grep w32codecs
ii  w32codecs                                 20071007-0medibuntu3                                       Win32 codec binaries

But still I am unable to play mpg or wmv files using Totem Movie player. It says "Could not determine type of stream".  

What am I missing here?

Thanks,
Bala.

---

### Post by dineshs on 2010-04-22
Have you tried vlc or SMplayer?

---

### Post by PRC09 on 2010-04-22
I think you may need to install Totem Xine from Ubuntu Software Center along with the gstreamer plugins.....

---

### Post by balaraja on 2010-04-22
I tried vlc and smplayer. Same problem exists.

---

### Post by CLEARviewF on 2010-04-22
Did you already installed the restricted package for ubuntu:
Every time I make a clean Ubuntu installation one of the first things I do is installing the restricted drivers to play whichever file I want, like mp3, wma, wmv, etc.
Run this in Terminal:

#sudo apt-get install ubuntu-restricted-extras

It is very weird that you cannot solve this installing VLC, VLC plays everything!

Good luck!

---

