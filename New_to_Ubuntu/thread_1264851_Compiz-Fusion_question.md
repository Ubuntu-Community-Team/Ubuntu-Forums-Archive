---
title: "Compiz-Fusion question"
date: 2009-09-12
forum: New to Ubuntu
---

### Post by k33bz on 2009-09-12
I just recently upgraded from Hardy to Jaunty, whew, was a few things to work out. Usplash, running compiz, sound configurations, & wifi.  I think I got everything done I wanted to get done.

However, I remember a function in Hardy's Compiz-Fusion that enabled things to go around the cursor. Different designs or flashes of light following where ever it went. The plugin was called "showmouse" I dont see that option no more. Is it still available, or am I not looking in the right place?

---

### Post by R3fr4cti0n on 2009-09-12
ya, its under accessibility "show mouse"

---

### Post by stderr on 2009-09-12
I'm still running Intrepid here so I can't comment on the CCSM version in Jaunty, but yes, it's called "Show mouse" and normally resides under the Accessibility section.

---

### Post by k33bz on 2009-09-12
Thanks to both of you, however it is not showing up there at all.

I have:
ADD Helper
Magnified
Opacity, brightness and saturation
color fileter
negative
zoom desktop
enhanced zoom desktop
opacify

---

### Post by stderr on 2009-09-12
Since it's in the "Extra" plugins category (see [http://wiki.compiz-fusion.org/Plugins]("http://wiki.compiz-fusion.org/Plugins")), you'll need to install compiz-fusion-plugins-extra

```
sudo apt-get install compiz-fusion-plugins-extra
```

---

### Post by k33bz on 2009-09-12
> **stderr said:**
> Since it's in the "Extra" plugins category (see [http://wiki.compiz-fusion.org/Plugins]("http://wiki.compiz-fusion.org/Plugins")), you'll need to install compiz-fusion-plugins-extra

```
sudo apt-get install compiz-fusion-plugins-extra
```

its already installed, thats what I am not getting. Matter fact it is the only plugin I am not getting.

I am going to try to get it through git.

---

### Post by k33bz on 2009-09-12
Ok, I tried it that way, and something strange happened:

```
keebler@mobile:~$ git clone git://anongit.compiz-fusion.org/fusion/plugins/showmouse showmouse
Initialized empty Git repository in /home/keebler/showmouse/.git/
remote: Counting objects: 75, done.
remote: Compressing objects: 100% (71/71), done.
remote: Total 75 (delta 34), reused 0 (delta 0)
Receiving objects: 100% (75/75), 27.56 KiB, done.
Resolving deltas: 100% (34/34), done.
keebler@mobile:~$ cd showmouse
keebler@mobile:~/showmouse$ make
Makefile:48: *** [ERROR] Compiz not installed.  Stop.
keebler@mobile:~/showmouse$ 

```

Yet I have both compiz and compiz-fusion installed.

---

### Post by stderr on 2009-09-12
*scratches beard* how odd. 

This is all I have installed:

```

ace@ace1:~/scripts$ sudo dpkg -l compiz* | grep ii | grep -v dbgsym
ii  compiz                                     1:0.7.8-0ubuntu4.1                                         OpenGL window and compositing manager
ii  compiz-core                                1:0.7.8-0ubuntu4.1                                         OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.7.8-0ubuntu2                                             Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.7.8-0ubuntu2.2                                           Collection of plugins from OpenCompositing f
ii  compiz-gnome                               1:0.7.8-0ubuntu4.1                                         OpenGL window and compositing manager - GNOM
ii  compiz-plugins                             1:0.7.8-0ubuntu4.1                                         OpenGL window and compositing manager - plug
ii  compiz-wrapper                             1:0.7.8-0ubuntu4.1                                         OpenGL window and compositing manager, wrapp
ii  compizconfig-backend-gconf                 0.7.8-0ubuntu1                                             Settings library for plugins - OpenCompositi
ii  compizconfig-settings-manager              0.7.8-0ubuntu3                                             Compiz configuration settings manager

```
and furthermore, I checked on another of my rigs running Jaunty, which actually has fewer compiz packages installed than the above, and it has the Show mouse plugin appearing in CCSM.

Perhaps try a sudo apt-get install --reinstall compiz-fusion-plugins-extra ?

---

### Post by k33bz on 2009-09-12
ok, I tried that, and it still does not show up.```
ii  compiz                                                   1:0.8.2-0ubuntu8.1                                         OpenGL window and compositing manager
ii  compiz-core                                              1:0.8.2-0ubuntu8.1                                         OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                              0.8.2-0ubuntu1.2                                           Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                               0.8.2-0ubuntu2                                             Collection of plugins from OpenCompositing f
ii  compiz-fusion-plugins-unsupported                        0.8.2-1ubuntu1                                             Compiz Fusion plugins - "unsupported" collec
ii  compiz-gnome                                             1:0.8.2-0ubuntu8.1                                         OpenGL window and compositing manager - GNOM
ii  compiz-plugins                                           1:0.8.2-0ubuntu8.1                                         OpenGL window and compositing manager - plug
ii  compiz-plugins-extra                                     0.8.2-0ubuntu1.1                                           Collection of extra plugins from OpenComposi
ii  compiz-plugins-main                                      0.8.2-0ubuntu1.1                                           Collection of plugins from OpenCompositing f
ii  compiz-wrapper                                           1:0.8.2-0ubuntu8.1                                         OpenGL window and compositing manager, wrapp
ii  compizconfig-backend-gconf                               0.8.2-0ubuntu2                                             Settings library for plugins - OpenCompositi
ii  compizconfig-settings-manager                            0.8.2-0ubuntu1                                             Compiz configuration settings manager

```

---

### Post by stderr on 2009-09-12
I grabbed the plugin via git as you did, but there's no source code, and no Makefile, so I don't see how 'make' could work anyway.

It seems like you're meant to copy the files somewhere, although where I'm not sure.

---

### Post by stderr on 2009-09-12
Try  git clone git://anongit.compiz.org/fusion/plugins/showmouse showmouse

---

### Post by k33bz on 2009-09-12
> **stderr said:**
> I grabbed the plugin via git as you did, but there's no source code, and no Makefile, so I don't see how 'make' could work anyway.

It seems like you're meant to copy the files somewhere, although where I'm not sure.

went with this how-to [http://gourgi.wordpress.com/2008/02/08/how-to-install-showmouse-plugin-compiz-fusion/]("http://gourgi.wordpress.com/2008/02/08/how-to-install-showmouse-plugin-compiz-fusion/")

> **stderr said:**
> Try git clone git://anongit.compiz.org/fusion/plugins/showmouse showmouse

that was already done :(

---

### Post by corncob on 2009-09-12
> **R3fr4cti0n said:**
> ya, its under accessibility "show mouse"

I have show-mouse.  I checked it but I don't see anything different.  Maybe I have to reboot?

---

### Post by stderr on 2009-09-12
> **k33bz said:**
> went with this how-to [http://gourgi.wordpress.com/2008/02/08/how-to-install-showmouse-plugin-compiz-fusion/]("http://gourgi.wordpress.com/2008/02/08/how-to-install-showmouse-plugin-compiz-fusion/")
Yeah that looks out of date, the URL I posted is from the compiz git site @ [http://git.compiz.org/]("http://git.compiz.org/"), and that *does* include source code and a Makefile ;)

corncob: No, you don't need to reboot with compiz effects. However, I'm struggling to get it working either hehe

---

### Post by k33bz on 2009-09-12
> **stderr said:**
> Yeah that looks out of date, the URL I posted is from the compiz git site @ [http://git.compiz.org/]("http://git.compiz.org/"), and that *does* include source code and a Makefile ;)

corncob: No, you don't need to reboot with compiz effects. However, I'm struggling to get it working either hehe

oh wow, neither one of ya'll can get ya'lls to work, does that mean the reason I dont have it listed is because it is no good no more?

make sure ya'll have mouse polling enabled, only way it will work


So after I got the file through git, what do I do with it? or should it be placed in a certain directory?

---

### Post by stderr on 2009-09-12
Still no joy this end... man I'm getting confused now!

You'll have to run make and then probably sudo make install (not sure if you need the sudo).

---

### Post by stderr on 2009-09-12
Ah, you may also need to grab the mouse poll plugin from git first, because it's included in the source. Give me a sec, I'll try to compile this plugin my end...

edit: This is nasty. You also need compiz-fusion-bcop installed, and you need to comment out some of the lines in Makefile, and I'm still not having much luck getting this to compile. 

```
ace@ace1:~/scripts/showmouse-compiz$ make
convert   : showmouse.xml.in -> build/showmouse.xml
bcop'ing  : build/showmouse.xml -> build/showmouse_options.h
bcop'ing  : build/showmouse.xml -> build/showmouse_options.c
make: *** No rule to make target `build/showmouse.lo', needed by `c-build-objs'. Stop.

```

---

### Post by k33bz on 2009-09-12
after downloading the source code I still get same message of not having compiz installed.
```
keebler@mobile:~/Desktop$ cd showmouse*
keebler@mobile:~/Desktop/showmouse-2b8f3033fefcfca448d895bb7e3e908d8b53e2a3$ make
Makefile:48: *** [ERROR] Compiz not installed.  Stop.

```

that is also after installing compiz-fusion-bcop

---

### Post by stderr on 2009-09-12
Yeah, you need compiz-dev. Still not there yet though, having trouble integrating the mousepoll source

---

### Post by stderr on 2009-09-12
Ok it's compiled now, I just confused the makefile with too many .cpps. How are you getting on?

So if memory serves, you need to do something like this:

```

sudo apt-get install compiz-dev compiz-fusion-bcop 
git clone git://anongit.compiz.org/fusion/plugins/showmouse showmouse
cd showmouse
make

```

```

ace@ace1:~/scripts/showmouse-compiz$ make
convert   : showmouse.xml.in -> build/showmouse.xml
schema    : build/showmouse.xml -> build/compiz-showmouse.schema
linking   : build/libshowmouse.la

```


When it's compiled and linked successfully, it looks like you have to copy:

build/compiz-showmouse.schema -> /usr/share/gconf/schemas/compiz-showmouse.schema
build/libshowmouse.la -> /usr/lib/compiz/libshowmouse.la
build/showmouse.xml -> /usr/share/compiz/showmouse.xml

... and hope that did the trick

---

### Post by k33bz on 2009-09-12
> **stderr said:**
> Ok it's compiled now, I just confused the makefile with too many .cpps. How are you getting on?

```

ace@ace1:~/scripts/showmouse-compiz$ make
convert   : showmouse.xml.in -> build/showmouse.xml
schema    : build/showmouse.xml -> build/compiz-showmouse.schema
linking   : build/libshowmouse.la

```


When it's compiled and linked successfully, it looks like you have to copy:

build/compiz-showmouse.schema -> /usr/share/gconf/schemas/compiz-showmouse.schema
build/libshowmouse.la -> /usr/lib/compiz/libshowmouse.la
build/showmouse.xml -> /usr/share/compiz/showmouse.xml

... and hope that did the trick

installing compiz-dev right now. What is the link for the download of showmouse, I think I keep trying to download the wrong one on top of this, lol

---

### Post by stderr on 2009-09-12
Hehe, don't worry, I entirely confused the issue myself by sticking the (I think unnecessary) mousepoll source all over the shop!

I appended the procedure as I recall it in the previous post

---

### Post by k33bz on 2009-09-12
> **stderr said:**
> Hehe, don't worry, I entirely confused the issue myself by sticking the (I think unnecessary) mousepoll source all over the shop!

I appended the procedure as I recall it in the previous post

yup, that did the trick, thanks :)

---

### Post by stderr on 2009-09-12
Let me know if the plugin works :) If it does, I'll copy the compiled files over myself, seen as my copy in compiz-fusion-plugins-extra apeears to be less-than-useful...

---

### Post by k33bz on 2009-09-12
> **stderr said:**
> Let me know if the plugin works :) If it does, I'll copy the compiled files over myself, seen as my copy in compiz-fusion-plugins-extra apeears to be less-than-useful...

unfortunately it dont work :(

---

### Post by stderr on 2009-09-12
LOL what an anticlimax! Did you even get the CCSM menu entry (I imagine you'd need to either restart compiz or reboot)?

---

### Post by k33bz on 2009-09-12
> **stderr said:**
> LOL what an anticlimax! Did you even get the CCSM menu entry (I imagine you'd need to either restart compiz or reboot)?

ya I got the entry, did not need to restart though

---

### Post by CatKiller on 2009-09-12
> **corncob said:**
> I have show-mouse.  I checked it but I don't see anything different.  Maybe I have to reboot?

You need to actually turn it on. Do whatever you've got set as the Initiate key combination. I think the default is Super-K.

---

### Post by k33bz on 2009-09-13
> **CatKiller said:**
> You need to actually turn it on. Do whatever you've got set as the Initiate key combination. I think the default is Super-K.

ya, I did that. And it is <Super> K

---

### Post by stderr on 2009-09-14
At least we have an explanation now as to why it wasn't included in the compiz-fusion-plugins-extra package you've got :) 

Mind you, the source code is relatively short and neat; I'm half-tempted to have a look at it myself...

---

### Post by k33bz on 2009-09-14
> **stderr said:**
> At least we have an explanation now as to why it wasn't included in the compiz-fusion-plugins-extra package you've got :) 

Mind you, the source code is relatively short and neat; I'm half-tempted to have a look at it myself...

let me know if you get it to work, 

I'm not good with programming, so ya, lol

---

