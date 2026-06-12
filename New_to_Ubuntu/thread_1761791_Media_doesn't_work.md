---
title: "Media doesn't work?"
date: 2011-05-18
forum: New to Ubuntu
---

### Post by jay13 on 2011-05-18
Hi, I'm running Ubuntu 11.04 from a live CD on an XP machine without an internet connection. I can't seem to run any media files, I've tried Divx, h.264, plain mpeg, and even mp3s, but none will play in Banshee or Media Player. I get a message saying the codec was not found. Am I doing something wrong, or do need to update before media files can be played? (This computer doesn't have an internet connection.)

The media files are on a USB hard drive, and I can view files, and read textfiles and images off the drive just fine. The live CD is running off a USB DVD drive, and I ran the Ubuntu auto installer to make changes to my system before the live CD would work. Thanks for any help.

---

### Post by Dngrsone on 2011-05-18
Ubuntu ships in a purely open-source configuration.  In order to view movies, play .mp3 music and such, you have to install the proprietary codecs for that stuff.

You can try adding the restricted extras through a terminal, but I don't know if you need an internet connection for that or not (nor if it will work when running live):

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by mick222 on 2011-05-18
If you install Ubuntu you can then install the Ubuntu -restricted extras , that gives you the codecs you need to play mp3 or wmp files. 
 You could also try a Wubi install inside Windows which is very like an installed system but easy to remove throuh add remove programs.

---

### Post by ivanovnegro on 2011-05-18
I think you need an internet connection for that, if you have one just do this step in the terminal and you will be able to play your media.

---

### Post by jay13 on 2011-05-18
Ah, I see, thanks for all the help! Are there any open source codecs that Ubuntu supports without additional installs, like these? [http://en.wikipedia.org/wiki/List_of_open_source_codecs](http://en.wikipedia.org/wiki/List_of_open_source_codecs)

---

### Post by ivanovnegro on 2011-05-18
Its basically what you saw on Wikipedia.

---

