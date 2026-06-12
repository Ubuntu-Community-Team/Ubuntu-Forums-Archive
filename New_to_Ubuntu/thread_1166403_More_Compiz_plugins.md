---
title: "More Compiz plugins"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by steigerjb on 2009-05-21
I am new to Compiz. I have Ubuntu 9.04. I wanna get as many plugins as I can but I don't know where or how. I need VERY VERY detailed instructions. Dumb it down. A few of the plugins I've heard/seen that I liked were:

Aquarium
Atlantis
Screensaver
Stackswitch
Freewins
Rubix cube
Snow globe
Photowheel
Snow...theres more but that all I can think of at the moment.

I am sure you know of some more I can get...I'll take those too.

PLEASE PLEASE HELP. I CAN'T FIND HELP ANYWHERE.](*,)](*,)](*,)

---

### Post by durand on 2009-05-21
Open a terminal (Applications > Accessories > Terminal)
```
sudo aptitude install compiz-fusion-plugins-{extra,main,unsupported} compizconfig-settings-manager
```

Then configure it using ccsm from a terminal.

For simpler configuration, use [simple-ccsm]("apt://simple-ccsm"). Then run simple-ccsm from a terminal.

For many others, you will need to compile them yourself which is a longer and more confusing process. Look at this website for more details: [http://mathpages.blogspot.com/2008/06/tips-for-using-compiz-fusion-on-ubuntu.html](http://mathpages.blogspot.com/2008/06/tips-for-using-compiz-fusion-on-ubuntu.html)

---

### Post by lovinglinux on 2009-05-21
> **durand said:**
> Open a terminal (Applications > Accessories > Terminal)
```
sudo aptitude install compiz-fusion-plugins-{extra,main,unsupported} compizconfig-settings-manager
```

This is kind of confusing due to the brackets. I know you mean you should use extra, main or unsupported one at a time, but I think some people might actually try to run the code above as is.

So, it should be like this:

```
sudo aptitude install compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-fusion-plugins-unsupported compizconfig-settings-manager
```

---

### Post by steigerjb on 2009-05-21
> **durand said:**
> Open a terminal (Applications > Accessories > Terminal)
```
sudo aptitude install compiz-fusion-plugins-{extra,main,unsupported} compizconfig-settings-manager
```

Then configure it using ccsm from a terminal.

For simpler configuration, use [simple-ccsm]("apt://simple-ccsm"). Then run simple-ccsm from a terminal.

For many others, you will need to compile them yourself which is a longer and more confusing process. Look at this website for more details: [http://mathpages.blogspot.com/2008/06/tips-for-using-compiz-fusion-on-ubuntu.html](http://mathpages.blogspot.com/2008/06/tips-for-using-compiz-fusion-on-ubuntu.html)

steiger@steiger-ubuntu:~$ sudo aptitude install compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-fusion-plugins-unsupported compizconfig-settings-manager
[sudo] password for joe: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

steiger@steiger-ubuntu:~$ 

ok...nothing happened

---

### Post by lovinglinux on 2009-05-21
[QUOTE=steigerj]ok...nothing happened[/QUOTE]

You already have all of them installed.

---

### Post by steigerjb on 2009-05-21
> **durand said:**
> For many others, you will need to compile them yourself which is a longer and more confusing process. Look at this website for more details: [http://mathpages.blogspot.com/2008/06/tips-for-using-compiz-fusion-on-ubuntu.html](http://mathpages.blogspot.com/2008/06/tips-for-using-compiz-fusion-on-ubuntu.html)

I'll try that this weekend. At least that's some of the plugins on my list.  I'll start with that.

---

### Post by durand on 2009-05-22
> **lovinglinux said:**
> This is kind of confusing due to the brackets. I know you mean you should use extra, main or unsupported one at a time, but I think some people might actually try to run the code above as is.

So, it should be like this:

```
sudo aptitude install compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-fusion-plugins-unsupported compizconfig-settings-manager
```

That does actually work. {} just expands the command to select all those files.

---

### Post by nandemonai on 2009-05-22
> **durand said:**
> That does actually work. {} just expands the command to select all those files.

So it does! Learn something new everyday. Cheers :)

Ok folks, carry on.

---

### Post by lovinglinux on 2009-05-22
> **durand said:**
> That does actually work. {} just expands the command to select all those files.

](*,)](*,)](*,) Now I feel like an idiot. I should stop talking about things I don't know :)

I thought it was like when people put <programname> in the command.

I'm so sorry.

---

### Post by durand on 2009-05-22
:)

---

### Post by durand on 2009-05-22
> **steigerjb said:**
> steiger@steiger-ubuntu:~$ sudo aptitude install compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-fusion-plugins-unsupported compizconfig-settings-manager
[sudo] password for joe: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

steiger@steiger-ubuntu:~$ 

ok...nothing happened

Nothing's supposed to happen until you configure it! Press Alt+F2 and run **simple-ccsm** and change the settings. For more detailed configuration, run **ccsm**.

---

### Post by steigerjb on 2009-05-22
joe@joe-ubuntu:~$ mkdir compiz
mkdir: cannot create directory `compiz': File exists
joe@joe-ubuntu:~$ mkdir compiz
mkdir: cannot create directory `compiz': File exists
joe@joe-ubuntu:~$ cd ~/compiz
joe@joe-ubuntu:~/compiz$ git clone git://anongit.compiz-fusion.org/users/wodor/anaglyph
fatal: destination directory 'anaglyph' already exists.
joe@joe-ubuntu:~/compiz$ mkdir compiz
joe@joe-ubuntu:~/compiz$ cd compiz
joe@joe-ubuntu:~/compiz/compiz$ git clone git://anongit.compiz-fusion.org/users/wodor/anaglyph
Initialized empty Git repository in /home/joe/compiz/compiz/anaglyph/.git/
remote: Counting objects: 121, done.
remote: Compressing objects: 100% (117/117), done.
remote: Total 121 (delta 60), reused 0 (delta 0)
Receiving objects: 100% (121/121), 25.88 KiB, done.
Resolving deltas: 100% (60/60), done.
joe@joe-ubuntu:~/compiz/compiz$ git clone git://anongit.compiz-fusion.org/fusion/plugins/atlantis
Initialized empty Git repository in /home/joe/compiz/compiz/atlantis/.git/
remote: Counting objects: 869, done.
remote: Compressing objects: 100% (865/865), done.
remote: Total 869 (delta 596), reused 0 (delta 0)
Receiving objects: 100% (869/869), 2.92 MiB | 185 KiB/s, done.
Resolving deltas: 100% (596/596), done.
joe@joe-ubuntu:~/compiz/compiz$ git clone git://anongit.compiz-fusion.org/users/metastability/atlantis2
Initialized empty Git repository in /home/joe/compiz/compiz/atlantis2/.git/
remote: Counting objects: 869, done.
remote: Compressing objects: 100% (865/865), done.
remote: Total 869 (delta 596), reused 0 (delta 0)
Receiving objects: 100% (869/869), 2.92 MiB | 184 KiB/s, done.
Resolving deltas: 100% (596/596), done.
joe@joe-ubuntu:~/compiz/compiz$ git clone git://anongit.compiz-fusion.org/users/smspillaz/fireflies
Initialized empty Git repository in /home/joe/compiz/compiz/fireflies/.git/
fatal: The remote end hung up unexpectedly
joe@joe-ubuntu:~/compiz/compiz$ git clone git://anongit.compiz-fusion.org/users/warlock/freewins
Initialized empty Git repository in /home/joe/compiz/compiz/freewins/.git/
remote: Counting objects: 1190, done.
remote: Compressing objects: 100% (1186/1186), done.
remote: Total 1190 (delta 826), reused 0 (delta 0)
Receiving objects: 100% (1190/1190), 274.40 KiB | 125 KiB/s, done.
Resolving deltas: 100% (826/826), done.
joe@joe-ubuntu:~/compiz/compiz$ git clone git://anongit.compiz-fusion.org/users/b0le/photowheel
Initialized empty Git repository in /home/joe/compiz/compiz/photowheel/.git/
remote: Counting objects: 44, done.
remote: Compressing objects: 100% (41/41), done.
remote: Total 44 (delta 22), reused 0 (delta 0)
Receiving objects: 100% (44/44), 13.37 KiB, done.
Resolving deltas: 100% (22/22), done.
joe@joe-ubuntu:~/compiz/compiz$ git clone git://anongit.compiz-fusion.org/users/pafy/screensaver
Initialized empty Git repository in /home/joe/compiz/compiz/screensaver/.git/
remote: Counting objects: 176, done.
remote: Compressing objects: 100% (172/172), done.
remote: Total 176 (delta 102), reused 0 (delta 0)
Receiving objects: 100% (176/176), 44.75 KiB, done.
Resolving deltas: 100% (102/102), done.
joe@joe-ubuntu:~/compiz/compiz$ git clone git://anongit.compiz-fusion.org/fusion/plugins/snow
Initialized empty Git repository in /home/joe/compiz/compiz/snow/.git/
remote: Counting objects: 123, done.
remote: Compressing objects: 100% (119/119), done.
remote: Total 123 (delta 61), reused 0 (delta 0)
Receiving objects: 100% (123/123), 32.38 KiB, done.
Resolving deltas: 100% (61/61), done.
joe@joe-ubuntu:~/compiz/compiz$ git clone git://anongit.compiz-fusion.org/users/metastability/snowglobe
Initialized empty Git repository in /home/joe/compiz/compiz/snowglobe/.git/
remote: Counting objects: 99, done.
remote: Compressing objects: 100% (96/96), done.
remote: Total 99 (delta 58), reused 0 (delta 0)
Receiving objects: 100% (99/99), 154.58 KiB | 139 KiB/s, done.
Resolving deltas: 100% (58/58), done.
joe@joe-ubuntu:~/compiz/compiz$ git clone git://anongit.compiz-fusion.org/users/smspillaz/stars
Initialized empty Git repository in /home/joe/compiz/compiz/stars/.git/
fatal: The remote end hung up unexpectedly
joe@joe-ubuntu:~/compiz/compiz$ git clone git://anongit.compiz-fusion.org/fusion/plugins/tile
Initialized empty Git repository in /home/joe/compiz/compiz/tile/.git/
fatal: The remote end hung up unexpectedly
joe@joe-ubuntu:~/compiz/compiz$ git clone git://anongit.compiz-fusion.org/fusion/plugins/wallpaper
Initialized empty Git repository in /home/joe/compiz/compiz/wallpaper/.git/
remote: Counting objects: 252, done.
remote: Compressing objects: 100% (248/248), done.
remote: Total 252 (delta 126), reused 0 (delta 0)
Receiving objects: 100% (252/252), 48.41 KiB, done.
Resolving deltas: 100% (126/126), done.
joe@joe-ubuntu:~/compiz/compiz$ 
joe@joe-ubuntu:~/compiz/compiz$ cd anaglyph
joe@joe-ubuntu:~/compiz/compiz/anaglyph$ make
convert   : anaglyph.xml.in -> build/anaglyph.xml
bcop'ing  : build/anaglyph.xml -> build/anaglyph_options.h
bcop'ing  : build/anaglyph.xml -> build/anaglyph_options.c
schema    : build/anaglyph.xml -> build/compiz-anaglyph.schema
compiling : anaglyph.c -> build/anaglyph.lo
compiling : build/anaglyph_options.c -> build/anaglyph_options.lo
linking   : build/libanaglyph.la
joe@joe-ubuntu:~/compiz/compiz/anaglyph$ make install
install   : /home/joe/.compiz/plugins/libanaglyph.so
install   : /home/joe/.compiz/metadata/anaglyph.xml
install   : build/compiz-anaglyph.schema
joe@joe-ubuntu:~/compiz/compiz/anaglyph$ cd
joe@joe-ubuntu:~$ cd compiz/atlantis
joe@joe-ubuntu:~/compiz/atlantis$ make
convert   : atlantis.xml.in -> build/atlantis.xml
bcop'ing  : build/atlantis.xml -> build/atlantis_options.h
bcop'ing  : build/atlantis.xml -> build/atlantis_options.c
schema    : build/atlantis.xml -> build/compiz-atlantis.schema
compiling : fish.c -> build/fish.lo
compiling : float.c -> build/float.lo
compiling : bfish.c -> build/bfish.lo
compiling : bubble.c -> build/bubble.lo
compiling : dolphin.c -> build/dolphin.lo
compiling : fish2.c -> build/fish2.lo
compiling : scuttle.c -> build/scuttle.lo
compiling : atlantis.c -> build/atlantis.lo
compiling : chromis.c -> build/chromis.lo
compiling : swim.c -> build/swim.lo
compiling : shark.c -> build/shark.lo
compiling : coral.c -> build/coral.lo
compiling : util.c -> build/util.lo
compiling : water.c -> build/water.lo
compiling : crab.c -> build/crab.lo
compiling : whale.c -> build/whale.lo
compiling : coral2.c -> build/coral2.lo
compiling : build/atlantis_options.c -> build/atlantis_options.lo
linking   : build/libatlantis.la
joe@joe-ubuntu:~/compiz/atlantis$ make install
install   : /home/joe/.compiz/plugins/libatlantis.so
install   : /home/joe/.compiz/metadata/atlantis.xml
install   : build/compiz-atlantis.schema
joe@joe-ubuntu:~/compiz/atlantis$ cd
joe@joe-ubuntu:~$ cd compiz/atlantis2
joe@joe-ubuntu:~/compiz/atlantis2$ make
convert   : atlantis.xml.in -> build/atlantis.xml
bcop'ing  : build/atlantis.xml -> build/atlantis_options.h
bcop'ing  : build/atlantis.xml -> build/atlantis_options.c
schema    : build/atlantis.xml -> build/compiz-atlantis.schema
compiling : fish.c -> build/fish.lo
compiling : float.c -> build/float.lo
compiling : bfish.c -> build/bfish.lo
compiling : bubble.c -> build/bubble.lo
compiling : dolphin.c -> build/dolphin.lo
compiling : fish2.c -> build/fish2.lo
compiling : scuttle.c -> build/scuttle.lo
compiling : atlantis.c -> build/atlantis.lo
compiling : chromis.c -> build/chromis.lo
compiling : swim.c -> build/swim.lo
compiling : shark.c -> build/shark.lo
compiling : coral.c -> build/coral.lo
compiling : util.c -> build/util.lo
compiling : water.c -> build/water.lo
compiling : crab.c -> build/crab.lo
compiling : whale.c -> build/whale.lo
compiling : coral2.c -> build/coral2.lo
compiling : build/atlantis_options.c -> build/atlantis_options.lo
linking   : build/libatlantis.la
joe@joe-ubuntu:~/compiz/atlantis2$ make install
install   : /home/joe/.compiz/plugins/libatlantis.so
install   : /home/joe/.compiz/metadata/atlantis.xml
install   : build/compiz-atlantis.schema
joe@joe-ubuntu:~/compiz/atlantis2$ cd
joe@joe-ubuntu:~$ cd compiz/fireflies
bash: cd: compiz/fireflies: No such file or directory
joe@joe-ubuntu:~$ make
make: *** No targets specified and no makefile found.  Stop.
joe@joe-ubuntu:~$ make install
make: *** No rule to make target `install'.  Stop.
joe@joe-ubuntu:~$ cd
joe@joe-ubuntu:~$ cd compiz/freewins
joe@joe-ubuntu:~/compiz/freewins$ make
Makefile:58: *** [ERROR] No package 'cairo-xlib' found.  Stop.
joe@joe-ubuntu:~/compiz/freewins$ make install
Makefile:58: *** [ERROR] No package 'cairo-xlib' found.  Stop.
joe@joe-ubuntu:~/compiz/freewins$ cd
joe@joe-ubuntu:~$ cd compiz/photowheel
joe@joe-ubuntu:~/compiz/photowheel$ make
bcop'ing  : build/photo.xml -> build/photo_options.h
bcop'ing  : build/photo.xml -> build/photo_options.c
schema    : build/photo.xml -> build/compiz-photo.schema
compiling : photo.c -> build/photo.lo
compiling : build/photo_options.c -> build/photo_options.lo
linking   : build/libphoto.la
joe@joe-ubuntu:~/compiz/photowheel$ make install
install   : /home/joe/.compiz/plugins/libphoto.so
install   : /home/joe/.compiz/metadata/photo.xml
install   : build/compiz-photo.schema
joe@joe-ubuntu:~/compiz/photowheel$ cd
joe@joe-ubuntu:~$ cd compiz/screensaver
joe@joe-ubuntu:~/compiz/screensaver$ make
convert   : screensaver.xml.in -> build/screensaver.xml
bcop'ing  : build/screensaver.xml -> build/screensaver_options.h
bcop'ing  : build/screensaver.xml -> build/screensaver_options.c
schema    : build/screensaver.xml -> build/compiz-screensaver.schema
compiling : effect.cpp -> build/effect.lo
compiling : vector.cpp -> build/vector.lo
compiling : rotatingcube.cpp -> build/rotatingcube.lo
compiling : wrapper.cpp -> build/wrapper.lo
compiling : screensaver.cpp -> build/screensaver.lo
compiling : matrix.cpp -> build/matrix.lo
compiling : flyingwindows.cpp -> build/flyingwindows.lo
compiling : build/screensaver_options.c -> build/screensaver_options.lo
linking   : build/libscreensaver.la
joe@joe-ubuntu:~/compiz/screensaver$ make install
install   : /home/joe/.compiz/plugins/libscreensaver.so
install   : /home/joe/.compiz/metadata/screensaver.xml
install   : build/compiz-screensaver.schema
joe@joe-ubuntu:~/compiz/screensaver$ cd
joe@joe-ubuntu:~$ cd compiz/snow
joe@joe-ubuntu:~/compiz/snow$ make
convert   : snow.xml.in -> build/snow.xml
bcop'ing  : build/snow.xml -> build/snow_options.h
bcop'ing  : build/snow.xml -> build/snow_options.c
schema    : build/snow.xml -> build/compiz-snow.schema
compiling : snow.c -> build/snow.lo
compiling : build/snow_options.c -> build/snow_options.lo
linking   : build/libsnow.la
joe@joe-ubuntu:~/compiz/snow$ make install
install   : /home/joe/.compiz/plugins/libsnow.so
install   : /home/joe/.compiz/metadata/snow.xml
install   : build/compiz-snow.schema
install   : /home/joe/.compiz/images/snowflake.png
joe@joe-ubuntu:~/compiz/snow$ cd
joe@joe-ubuntu:~$ cd compiz/snowglobe
joe@joe-ubuntu:~/compiz/snowglobe$ make
convert   : snowglobe.xml.in -> build/snowglobe.xml
bcop'ing  : build/snowglobe.xml -> build/snowglobe_options.h
bcop'ing  : build/snowglobe.xml -> build/snowglobe_options.c
schema    : build/snowglobe.xml -> build/compiz-snowglobe.schema
compiling : movement.c -> build/movement.lo
compiling : snowglobe.c -> build/snowglobe.lo
compiling : snowman.c -> build/snowman.lo
compiling : water.c -> build/water.lo
compiling : snowflake.c -> build/snowflake.lo
compiling : build/snowglobe_options.c -> build/snowglobe_options.lo
linking   : build/libsnowglobe.la
joe@joe-ubuntu:~/compiz/snowglobe$ make install
install   : /home/joe/.compiz/plugins/libsnowglobe.so
install   : /home/joe/.compiz/metadata/snowglobe.xml
install   : build/compiz-snowglobe.schema
joe@joe-ubuntu:~/compiz/snowglobe$ cd
joe@joe-ubuntu:~$ cd compiz/stars
bash: cd: compiz/stars: No such file or directory
joe@joe-ubuntu:~$ make
make: *** No targets specified and no makefile found.  Stop.
joe@joe-ubuntu:~$ make install
make: *** No rule to make target `install'.  Stop.
joe@joe-ubuntu:~$ cd
joe@joe-ubuntu:~$ cd compiz/tile
bash: cd: compiz/tile: No such file or directory
joe@joe-ubuntu:~$ make
make: *** No targets specified and no makefile found.  Stop.
joe@joe-ubuntu:~$ make install
make: *** No rule to make target `install'.  Stop.
joe@joe-ubuntu:~$ cd
joe@joe-ubuntu:~$ cd compiz/wallpaper
joe@joe-ubuntu:~/compiz/wallpaper$ make
convert   : wallpaper.xml.in -> build/wallpaper.xml
bcop'ing  : build/wallpaper.xml -> build/wallpaper_options.h
bcop'ing  : build/wallpaper.xml -> build/wallpaper_options.c
schema    : build/wallpaper.xml -> build/compiz-wallpaper.schema
compiling : wallpaper.c -> build/wallpaper.lo
compiling : build/wallpaper_options.c -> build/wallpaper_options.lo
linking   : build/libwallpaper.la
joe@joe-ubuntu:~/compiz/wallpaper$ make install
install   : /home/joe/.compiz/plugins/libwallpaper.so
install   : /home/joe/.compiz/metadata/wallpaper.xml
install   : build/compiz-wallpaper.schema
joe@joe-ubuntu:~/compiz/wallpaper$

---

### Post by durand on 2009-05-22
First of all, don't just blindly run commands. If you see an error, don't run the next command until you've worked out what went wrong! Next, use code tags to enclose your pasted output.

It looks like most of the plugins compiled properly apart from freewins, fireflies, tiles and stars. Freewins requires some cairo-xlib program. I have no idea how to find that.. stars wasn't in the git repository so it wasn't downloaded so it couldn't be compiled and installed. Same with fireflies and tiles. You need to find out why that is. Look in the compiz folder in your home directory. It could be that they've been renamed to something else.

---

### Post by steigerjb on 2009-05-22
> **durand said:**
> First of all, don't just blindly run commands. If you see an error, don't run the next command until you've worked out what went wrong! Next, use code tags to enclose your pasted output.

I went to that website and ran the script, probably did it wrong though, I just copied the whole thing into the terminal.

> **durand said:**
> It looks like most of the plugins compiled properly apart from freewins, fireflies, tiles and stars. Freewins requires some cairo-xlib program. I have no idea how to find that.. stars wasn't in the git repository so it wasn't downloaded so it couldn't be compiled and installed. Same with fireflies and tiles. You need to find out why that is. Look in the compiz folder in your home directory. It could be that they've been renamed to something else.

Yeah, they show but I can't seem to be able to get them running.

---

### Post by steigerjb on 2009-05-22
well photowheel works...next...

ugh screensaver worked for a sec there

---

### Post by steigerjb on 2009-05-23
Ok guys the ones so far seem to work. the simple ccsm was messing it up at first.

I am shortening my list. Only ones left I wanna get are: 

Stackswitch
Freewins
Rubix cube

if you know how get them...help me plz:confused:

---

### Post by joshyfluff on 2009-12-15
I seem to be getting 
Makefile:48: *** [ERROR] Compiz not installed. Stop.
Does this mean that I have to install compiz from GIT? I already have it installed from a fresh install ; ;
EDIT
I fixed it ^^

---

### Post by thefatmoop on 2009-12-16
not sure if this was posted already but this site is good.
[http://mathpages.blogspot.com/2008/06/tips-for-using-compiz-fusion-on-ubuntu.html]("http://mathpages.blogspot.com/2008/06/tips-for-using-compiz-fusion-on-ubuntu.html")

```
compiz-bcop
```

is now 
```
compiz-fusion-bcop
```

To the guy who posted his huge error message: Do you see other people doing that? do you think anyone is going to read over your 1000lines of fail?

---

### Post by steigerjb on 2010-01-20
> **steigerjb said:**
> I am new to Compiz. I have Ubuntu 9.04. I wanna get as many plugins as I can but I don't know where or how. I need VERY VERY detailed instructions. Dumb it down. A few of the plugins I've heard/seen that I liked were:

Aquarium
Atlantis
Screensaver
Stackswitch
Freewins
Rubix cube
Snow globe
Photowheel
Snow...theres more but that all I can think of at the moment.

I am sure you know of some more I can get...I'll take those too.

PLEASE PLEASE HELP. I CAN'T FIND HELP ANYWHERE.](*,)](*,)](*,)

bravo gotbletu!:
[http://www.youtube.com/watch?v=b616WSM-uYw](http://www.youtube.com/watch?v=b616WSM-uYw)

thanks a bunch! way easy way! party time with Compiz :guitar:

---

### Post by durand on 2010-01-20
> **steigerjb said:**
> bravo gotbletu!:
[http://www.youtube.com/watch?v=b616WSM-uYw](http://www.youtube.com/watch?v=b616WSM-uYw)

thanks a bunch! way easy way! party time with Compiz :guitar:

Wow, thanks for that link!

BTW, steiger, sorry for not responding to your posts. I think I missed the email when you replied so I never bothered to check back :(

---

### Post by steigerjb on 2010-01-20
> **durand said:**
> BTW, steiger, sorry for not responding to your posts. I think I missed the email when you replied so I never bothered to check back :(

no problem

---

