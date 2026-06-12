---
title: "How do I install Project Diaspora?"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by Cloud Wolf on 2009-02-19
I desperately need help knowing how to install this! I have looked at the site, but it offers no guidance.
Could someone put together a step-by-step guide on how to install it and which files are needed?

---

### Post by Cloud Wolf on 2009-02-21
Bump.

---

### Post by carml on 2009-02-21
Which is the site?If you tell me which it is,I read it and try to drive you step by step. :-)

---

### Post by carml on 2009-02-21
It is this one [http://sourceforge.net/projects/pdiaspora?](http://sourceforge.net/projects/pdiaspora?)

---

### Post by Cloud Wolf on 2009-02-21
No, it is this site,
[http://www.nighsoft.net](http://www.nighsoft.net)

---

### Post by carml on 2009-02-21
Ok that's a beta version,so it could have some issue.Now I'm downloading that to see what it requires,I'll take a look
at [http://sourceforge.net/projects/pdiaspora?](http://sourceforge.net/projects/pdiaspora?) also, hang on a while. :-)

---

### Post by carml on 2009-02-21
Ok first of all go to System->Administration->Synaptic package manager and look for "libsdl".Probably you'll get a result similar to the one in the picture below.If you that we're ok,and we can go on.;)

---

### Post by Cloud Wolf on 2009-02-21
yep. continue

---

### Post by carml on 2009-02-21
Ok man,go again to System->Administration->Synaptic package manager and look for " build-essential" select the square near the name right-click and select "mark for installation".Or you can also go to Applications-Accessories-Terminal and type "sudo apt-get install build-essential",then you're being prompted for your password,don't care if you don't see what you type,that's a security setting.:)

---

### Post by Cloud Wolf on 2009-02-21
For some reason I have already got that installed. Continue.

---

### Post by carml on 2009-02-21
Ok, check if also the following are installed :
libsdl_ttf
libsdl_image
libsdl_gfx
libcurl.

---

### Post by Cloud Wolf on 2009-02-21
All installed :)

---

### Post by carml on 2009-02-21
Ah ok,I was waiting,but you disconnected,so I went to do something else.Now you have to extract the NameofGameFile.zip somewhere,preferably on your home folder or on the desktop.

---

### Post by Cloud Wolf on 2009-02-21
what? what zip file, from where?

---

### Post by carml on 2009-02-24
The one named: pdiaspora_client-beta-1.2.5.tar.gz

---

### Post by Cloud Wolf on 2009-02-24
thats done :)
go. put more in each step if you can

---

### Post by carml on 2009-02-24
> **carml said:**
> Ah ok,I was waiting,but you disconnected,so I went to do something else.Now you have to extract the NameofGameFile.zip somewhere,preferably on your home folder or on the desktop.
Sorry I assumed it was a .zip file,now decompress the file onto a directory placed on your home directory or onto the desktop.

---

### Post by Cloud Wolf on 2009-02-24
already done

---

### Post by carml on 2009-02-24
Ok should there be something like :make,configure,etc.
You should go to Applications->Accessories->Terminal and type
cd /exact/path/of/the/directory to go to the directory where you decompressed the file, then type " sudo make " and insert your password,then after you see "yourname@ubuntu:&#65279;~$ " type " sudo make install".
It should generate the executable and all the necessaries directories and files. :)

---

### Post by Cloud Wolf on 2009-02-24
just comes up with

jacob@UBUNTU-VAIO1:~/Desktop/pdiaspora_client-beta-1.2.5/src$ sudo make install
make: *** No rule to make target `install'. Stop.

---

### Post by Cloud Wolf on 2009-02-24
also with the sudo make, it comes up with

jacob@UBUNTU-VAIO1:~/Desktop/pdiaspora_client-beta-1.2.5/src$ sudo make
g++ -c `sdl-config --cflags` main.c -o main.o
In file included from main.c:12:
main.h:21:35: error: SDL/SDL_gfxPrimitives.h: No such file or directory
main.h:65:23: error: curl/curl.h: No such file or directory
make: *** [main.o] Error 1

---

### Post by carml on 2009-02-24
Wrong,bad answer .Check the directory for a file called make.
P.s. the command " sudo make " what gave you?

---

### Post by carml on 2009-02-24
Ok, maybe installing " libsdl1.2-dev" will solve that problems,i.e. the ones gave by sudo make.
Let me know

---

### Post by Cloud Wolf on 2009-02-24
I already have that. I dont know what is wrong. the make file your on about is in the file called src and is called "makefile"

---

### Post by carml on 2009-02-24
Please could you access to Syaptic,look for "libsdl" ,take a screenshot and post it?

---

### Post by Cloud Wolf on 2009-02-24
here

---

### Post by carml on 2009-02-24
I tried to download and install the software,it didn't compile,I can only suggest you to look for a previous version or to make a search on google.
I'm sorry:(:confused:

---

### Post by carml on 2009-02-24
The only solution I find is to donload the version for Windows and try to execute that using the package called Wine,this my extrema ratio,do this until the developers release a working version.

---

### Post by Darkcon on 2009-09-24
heya cloud, what i did to install pdias on ubuntu is download pdias then in this order

download SDL from [http://www.libsdl.org/download-1.2.php](http://www.libsdl.org/download-1.2.php)              - SDL itself
then download [http://www.libsdl.org/projects/SDL_image/](http://www.libsdl.org/projects/SDL_image/)            - SDL_image
download [http://www.libsdl.org/projects/SDL_ttf/](http://www.libsdl.org/projects/SDL_ttf/)               - SDL_tff
[http://www.ferzkopp.net/joomla/content/view/19/14/](http://www.ferzkopp.net/joomla/content/view/19/14/)         -         SDL_gfx
[http://curl.haxx.se/download.html](http://curl.haxx.se/download.html)            - curl

then went to synaptics manager, type curl into the quick search, and installed everything with the name curl in it

sudo -i to make it root terminal
extract each file you downloaded, goto each directory and
type ./configure 
then
make
then 
make install

make sure you do it for each of the files you downloaded, 

then follow the pdias readme on how to compile the game

---

### Post by hidinginthemountains on 2009-12-17
Sort of a newb question from me then (I don't compile my own stuff often, and when I do I'm pretty much just following someone-else-helpfull's paint by numbers), if I install the "official versions" of SDL as you suggest, will that affect the packages I already have installed through synaptic in any way? (...particularly in any negative way?)

---

