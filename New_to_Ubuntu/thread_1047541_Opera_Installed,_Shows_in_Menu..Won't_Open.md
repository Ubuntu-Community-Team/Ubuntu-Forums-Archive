---
title: "Opera Installed, Shows in Menu..Won't Open"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by ~zoey~ on 2009-01-22
I'm running ubuntu intrepid, Linux-desktop 2.6.27-9-generic #1 SMP  UTC 2008 i686 GNU/Linux.
I got Opera installed after quite a few tries.  I downloaded it twice from the Opera website using their installer, only to have it come up that there was no package available to install, so I think that I have two Opera .deb packages somewhere on my system.
I downloaded a tar package also from the Opera website and got that installed using ./install.sh. It shows up in the menu, but clicking on the icon doesn't accomplish anything, nor does ./opera using the command line.
What should my next step be?

Thanks, zoey

---

### Post by Bölvaður on 2009-01-22
System &#8594; Administration &#8594; Software sources
Mark all except perhaps source code, but marking scoure code isn't dangerous.

+Add

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) [COLOR="Red"]hardy[/COLOR] partner



note that this is probably not hardy for you, but rather gusty (8.04) or intrepid (8.10). so if you have ubuntu 8.10 then this line would be:

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

then go to synaptic and install :)

---

### Post by ~zoey~ on 2009-01-22
> **Bölvaður said:**
> System &#8594; Administration &#8594; Software sources
Mark all except perhaps source code, but marking scoure code isn't dangerous.

+Add

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) [COLOR="Red"]hardy[/COLOR] partner



note that this is probably not hardy for you, but rather gusty (8.04) or intrepid (8.10). so if you have ubuntu 8.10 then this line would be:

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

then go to synaptic and install :)

I did that, but opera didn't show up in synaptic.  I tried sudo apt-get install opera and got "package opera has no installation candidate"

It is installed, but won't run.  I am probably missing a link somewhere, but I haven't a clue as to how to fix the problem.

Thanks, zoey

---

### Post by RomeReactor on 2009-01-22
Hi. Try running Opera from the terminal:
```
opera
```
and post any errors you get there. If nothing happens, try:
```
which opera
```
It should tell you the location of the executable if it's in the system's path.

---

### Post by ~zoey~ on 2009-01-22
> **RomeReactor said:**
> Hi. Try running Opera from the terminal:
```
opera
```
and post any errors you get there. If nothing happens, try:
```
which opera
```
It should tell you the location of the executable if it's in the system's path.

command opera gives me;
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/opera/9.63/opera: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory

which opera gives me; /usr/bin/opera

Thanks, zoey

---

### Post by RomeReactor on 2009-01-22
Try installing libqt3-mt:
```
sudo aptitude install libqt3-mt
```

---

### Post by gjoellee on 2009-01-22
Try install a DEB file: [http://www.opera.com/](http://www.opera.com/) and click on the "Download" button. Then select your version of Ubuntu

---

### Post by ~zoey~ on 2009-01-22
> **RomeReactor said:**
> Try installing libqt3-mt:
```
sudo aptitude install libqt3-mt
```

Thank You, Thank You, RomeReactor that did it!!!

zoey

---

