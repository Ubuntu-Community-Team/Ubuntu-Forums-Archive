---
title: "MP3 nightmare....."
date: 2009-08-09
forum: New to Ubuntu
---

### Post by James Danger Mouse on 2009-08-09
[COLOR=black][FONT=Verdana]Hey folks this is my 1st post on this forum so please be patient I'll do my best to keep up....[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Verdana]I have installed 8.04 on a new machine that doesn't have internet access and so I need to download the plugins for Rythembox music player from somewhere then I need to install them some how is there a quick fix guide out there I'm gonna have a look at the pdf that was posted in the sticky by technoviking hopefully my answers lie there, other then that I'm not sure where to start..... I read the forum a few times but there are steps missing or things I'm not doing properly could some one please lay it out there for me in step by step form...[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Verdana]Also I was wondering would it be easier to get mp3's going on the new version of ubuntu?[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]If so I can download it and start from there remember I don’t have internet access on the ubuntu machine so until I get internet working on my machine I know I'm going to have to battle..... [/FONT][/COLOR]
 
 
 
[COLOR=black][FONT=Verdana]My thanks in advance to who ever has some advice for me.[/FONT][/COLOR]

---

### Post by MelDJ on 2009-08-09
mp3 plugins cant be put straight into ubuntu as its a copyright infrigment:guitar:

---

### Post by MelDJ on 2009-08-09
u could get the .deb installer for banshee and install it into ubuntu

---

### Post by golusweet on 2009-08-09
Try this package

[http://packages.medibuntu.org/pool/free/f/ffmpeg/ffmpeg_0.cvs20070307-5ubuntu7.3+medibuntu1_i386.deb](http://packages.medibuntu.org/pool/free/f/ffmpeg/ffmpeg_0.cvs20070307-5ubuntu7.3+medibuntu1_i386.deb)

Here are list of other packages for hardy

[http://packages.medibuntu.org/hardy/index.html](http://packages.medibuntu.org/hardy/index.html)

---

### Post by furuno on 2009-08-09
This is what I'm doing when I didn't have internet access back then :

1. Type this command on your Ubuntu :
```
aptitude search ~i > ~/packagelist.txt
```
2. Go to your home directory and copy the packagelist.txt file to your flash disk (or whatever...)
3. Go to the place where you can connect to internet...
4. Open up [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
5. Search for the package you'll need to install e.g. gstreamer0.10-ffmpeg also choose you correct Ubuntu version (8.04 is hardy heron in your case).
6. You'll be given a list of required packages and download link below the list. Before you download that packages, cross-check the required packages (the on with red circle) with your packagelist.txt, if it isn't listed in the packagelist.txt file, the you will need to download it too. Then you'll of course will need to download the package itself (from the link at the bottom of package list page).
7. Rinse and repeat for all of the packages you'll need.
8. When you're back home, put all of those packages in a single folder, e.g. in Packages folder in you home directory.
9. Type this command :
```
cd ~/Packages
sudo dpkg -i --force-depends *.deb
```
10. Then this :
```
sudo dpkg --configure --pending
```
11. If nothing goes wrong that all of those packages should be installed now.

Remember :
You'll need to have all of the dependecies for EVERY package you want. Example :
You want package A, but package A depens on package B, and B depends on C.
Then you'll need to download A, B, and C.

Well, it is kinda troublesome, but 3 hours should be more than enough :popcorn:

Anyway, you will want to install all pacakges with gstreamer in their names, just in case... Good luck!

---

### Post by Terl on 2009-08-09
For MP3 support and even to get flash and jave runtime ans microsoft fonts among other restriced codecs do: ```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by furuno on 2009-08-09
Umm... the problem is, he does not have an internet connection, so I think apt-get is out of the question here...

---

### Post by oldos2er on 2009-08-09
Try either Keryx ([http://keryxproject.org/](http://keryxproject.org/)) or AptonCD ([http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)).

---

### Post by Bartender on 2009-08-09
You're probably used to Windows, where you could take a thumb drive someplace and get everything in one .exe.
It's not like that in Linux.  Speaking from experience, you will find it much easier to take your PC to a broadband connection than trying to get the packages you need onto a disconnected PC.
I'm typing this message with a laptop, sitting in the car, outside a store that's throwing out an unencrypted wifi connection.  At home we have dial-up, which is *almost* the same thing as no internet at all when you're using Linux.

---

