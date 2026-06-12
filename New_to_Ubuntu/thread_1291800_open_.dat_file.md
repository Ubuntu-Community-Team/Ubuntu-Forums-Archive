---
title: "open .dat file"
date: 2009-10-15
forum: New to Ubuntu
---

### Post by Duke Togo on 2009-10-15
hi
I had a google on this but could not find an answer
I want to open a .dat file (just a data file for simple text editing not video)
what do I need in order to do this?
is there a piece of software that can do this?
thanks in advance

---

### Post by RichardLinx on 2009-10-15
> .dat files are windows-scripts, which you cannot run on Linux.
You might have to install windows in a virtual machine and edit the file there, it might also be possible through wine. I'm not very familiar with .dat, sorry.

You can download the latest version of Wine from here: [http://www.winehq.org/download](http://www.winehq.org/download)
(The Ubuntu .deb file)

And you can get virtualbox by typing in a terminal:
```
sudo apt-get install virtualbox-ose
```
Or visit the virtualbox website and download the binary from there.
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by Duke Togo on 2009-10-15
Richardlinx

Thanks for the help but unfortunately I already have a windows xp partition but the cd on my laptop is broken so there is no way I can use virtual box
The xp partition is a japanese version so doing most things on it, unless very simple, are almost impossible (my japanese is limited)
any other ideas
I was running wine too but it won`t open this file

---

### Post by RichardLinx on 2009-10-15
Wine is a tool for loading up Windows programs. So you would need to try installing a windows program for opening/editing .dat files in Wine.

Also, I'm not 100% sure about the contents of a .dat file but I did some quick research and learned that they're a type of text file. So you might be able to open it up in most text editors. Try opening it in gedit on Ubuntu. (Gedit is the default text editor in Ubuntu). You could also try opening it up in Notepad or Wordpad in Wine.

I haven't got wine installed but if I remember correctly it comes with Notepad or Wordpad installed.

---

### Post by mcduck on 2009-10-15
> **Duke Togo said:**
> hi
I had a google on this but could not find an answer
I want to open a .dat file (just a data file for simple text editing not video)
what do I need in order to do this?
is there a piece of software that can do this?
thanks in advance

.dat is just a generic name for any data file, so you need to tell what program made that file and what kind of data it contains.

Nobody will be able to tell you what program to use to open that kind of file simply based on the file name, it can contain any data in any format.

---

### Post by 3rdalbum on 2009-10-15
If it's just a text file, then try looking at it using "less":

```
less myfile.dat
```

If it's just gobbledegook, then it's got binary data in it and any editing you do to it will probably stop it from working in whatever program it's for.

The ".dat" extension means precisely nothing. If you know what program on Windows was used to open or create this file, then tell us and there might be a way to open it on Linux.

---

### Post by mcduck on 2009-10-15
You can also try to check what type the file's contents are with the "file"-command.

```
file somefile.dat
```

---

### Post by Duke Togo on 2009-10-20
thanks everyone
gedit wouldn`t do it but notepad in wine did
it was binary so I left well alone
solved

---

### Post by BikeHelmet on 2009-10-20
.dat is one of the more overused extensions. I've seen media players uses it, game saves, other game assets, etc.

But... it looks like you already have your answer. :)

---

