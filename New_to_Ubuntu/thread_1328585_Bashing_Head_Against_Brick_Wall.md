---
title: "Bashing Head Against Brick Wall"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by donjorge22 on 2009-11-16
I installed Ubuntu 9.10 on one of my laptops a couple of weeks ago, wiping it clean of (yuck) Windows Vista.  For the most part, I like Ubuntu is better; HOWEVER, I feel like I've been bashing my head against a brick wall on a number of issues specific to the setup I want/need for my everyday activities.  I've tried at great length investigating solutions for all of the below, but I couldn't get any of the solutions I found to work. Anyway...

I need to have Japanese keyboard input, and I installed the extra language pack; however, the default fonts are not pretty, and a guide to adding new fonts causes every system update to give me a deluge of errors.  I also can't figure out how to change from one IME to the next.

I also have a Trust-5300 tablet that I need for entering Chinese characters whose pronunciation I don't (yet) know; I tried installing a driver for it, but to no avail and lots of errors.

When the system loads up, it comes up with some encryption error and then loads normally - is this peculiar to the latest revision of Ubuntu?

Finally, I've been trying to install Elements (as part of the Compiz package); however, that comes up with a load of "stuff not found" errors.

It's so annoying that there are these problems.  I installed Ubuntu in the first place because I was so fed up of Windows, and because I want to understand computers better.  I love the economy of the Terminal, and the awesomeness of the applets and the functionality in general, and for the things I've been able to fix (soundcard and wifi issues) it's been great.  So, any help greatly appreciated - anything to stay away from Microsoft ;)

P.S. if there's more information needed on these issues, I'll gladly look up what I followed...

---

### Post by itsbrad212 on 2009-11-16
go to System>Prefrences>Language Support to change language (i hope thats what u wanted)

and could u please post the error you get with compiz install?

---

### Post by donjorge22 on 2009-11-16
```
eldon@eldon-laptop:~$ bash ./elementsinstall
bash: ./elementsinstall: No such file or directory
eldon@eldon-laptop:~$ bash ./elementsinstall.sh
bash: ./elementsinstall.sh: No such file or directory
eldon@eldon-laptop:~$ cd ~/Downloads
eldon@eldon-laptop:~/Downloads$ bash ./elementsinstall.sh
[sudo] password for eldon: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz-fusion-bcop is already the newest version.
compiz-dev is already the newest version.
libxcomposite-dev is already the newest version.
libpng12-dev is already the newest version.
libsm-dev is already the newest version.
libxrandr-dev is already the newest version.
libxdamage-dev is already the newest version.
libxinerama-dev is already the newest version.
libstartup-notification0-dev is already the newest version.
libgl1-mesa-dev is already the newest version.
libtool is already the newest version.
libxslt1-dev is already the newest version.
xsltproc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mkdir: cannot create directory `/home/eldon/.elements': File exists
--2009-11-16 21:40:24--  http://www.elementsplugin.com/downloads/elements-most-recent.tar.gz
Resolving www.elementsplugin.com... 74.220.219.113
Connecting to www.elementsplugin.com|74.220.219.113|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 81464 (80K) [application/x-gzip]
Saving to: `/home/eldon/.elements/elements.tar.gz'

100%[======================================>] 81,464      76.8K/s   in 1.0s    

2009-11-16 21:40:25 (76.8 KB/s) - `/home/eldon/.elements/elements.tar.gz' saved [81464/81464]

images/
images/stars1.png
images/snow2.png
images/snow1.png
images/plugin-elements.png
images/fireflies2.svg
images/fireflies1.svg
images/bubbles2.png
images/bubbles1.png
images/autumn2.png
images/autumn1.png
elements.c
elements.xml.in
Makefile
plugin.info
install   : /home/eldon/.compiz/plugins/libelements.soinstall: cannot create regular file `/home/eldon/.compiz/plugins/libelements.so': Permission denied
make: *** [install] Error 1
Checking for Xgl: eldon@eldon-laptop:~/Downloads$ not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

Thar be the bug.  Instructions followed from [http://www.ubuntugeek.com/howto-install-elements-for-compiz-fusion.html](http://www.ubuntugeek.com/howto-install-elements-for-compiz-fusion.html).  Also, everything vanishes before it prints the warnings for a few seconds, leaving just the desktop background.  Installed languages, just can't figure out how to type in Japanese... thanks for quick response :D

---

### Post by itsbrad212 on 2009-11-16
this may be a dumb question but are you in the same directory as the elementsinstall.sh file?

---

### Post by itsbrad212 on 2009-11-16
oh, and i also get the boot error as well. something along the lines of "Couldn't find shell script". as long as my computer worls, im happy

---

### Post by donjorge22 on 2009-11-16
Sure am...

```
eldon@eldon-laptop:~$ cd ~/Downloads
eldon@eldon-laptop:~/Downloads$ bash ./elementsinstall.sh
```

That's where I left it anyway.  Or is there something I'm missing?

---

### Post by itsbrad212 on 2009-11-16
hmm. i tried installing it and i got the same output, but it shows up in ccsm. did u check there? :D

---

### Post by donjorge22 on 2009-11-16
Not seeing it there... what section did you find it under?

---

### Post by itsbrad212 on 2009-11-16
lets see... it was under extras (5th from top) and its called "Elements"

---

### Post by donjorge22 on 2009-11-16
Not seeing it there.  All I gots under Extras is Annotate, Benchmark, Screenshot, Splash and Window Previews :(

---

### Post by itsbrad212 on 2009-11-16
ahh i think i see the problem

```

install   : /home/eldon/.compiz/plugins/libelements.soinstall: cannot create regular file `/home/eldon/.compiz/plugins/libelements.so': Permission denied
make: *** [install] Error 1


```

run:
```

sudo bash ./elementsinstall.sh
```

---

### Post by donjorge22 on 2009-11-16
YAY! Whoops, that was kinda dumb of me.  Kudos to you though, thanks :D :D :D

---

### Post by L14UX_1NS1D3 on 2009-11-16
Did you possibly try running the script as sudo user?

like so:

```
sudo ./dir/script.sh 

```
or
```
cd /dir && sudo ./script.sh

```
or
```
sudo sh script.sh
```

see if that works. 

Your output said something about xgl.

do some googling about elements *and* xgl. You might not be the only one with this problem.

Hope this helps! :D

---

### Post by itsbrad212 on 2009-11-16
> **donjorge22 said:**
> YAY! Whoops, that was kinda dumb of me.  Kudos to you though, thanks :D :D :D

no prob :D

---

### Post by L14UX_1NS1D3 on 2009-11-16
Ooops! Didn't see that that the problem was already solved.

---

